<template>
	<div class="favorite-list">
		<favorite-section
			v-for="bookmark in bookmarks"
			:key="bookmark.id"
			:title="bookmark.title"
			:children="bookmark.children"/>
	</div>
</template>


<script>
import { EventBus } from '../../main'
import BookmarkService from '../bookmarks/BookmarksService.vue'
import FavoriteSection from './FavoriteSection.vue'

export default {
	components: { FavoriteSection },
	name: 'NewTab',

	data: () => { 
		return {
			bookmarks: []
		}
	},

	created: function() {
		BookmarkService.all("1").then(b => { this.bookmarks = b })
		EventBus.$on('arrow-navigation', key => this.arrowNavigation(key))
	},

	methods: {
		arrowNavigation(key) {
			const activeElement = document.activeElement

			if (activeElement.className != 'fav-item') {
				this.arrowNavigateFirstItem()
				return
			}

			switch(key) {
				case 'ArrowUp':
					this.arrowNavigateUp(activeElement)
					break
				case 'ArrowDown':
					this.arrowNavigateDown(activeElement)
					break
				case 'ArrowLeft':
					this.arrowNavigateLeft(activeElement)
					break
				case 'ArrowRight':
					this.arrowNavigateRight(activeElement)
			}
		},

		// Navigates to the first available fav item
		arrowNavigateFirstItem() {
			document
				.querySelector('.favorite-list .fav-section')
				.querySelector('.fav-list .fav-item')
				.focus()
		},
		
		arrowNavigateUp(activeElement) {
			const previousSibling = activeElement.previousSibling
			if(previousSibling) previousSibling.focus()
		},
		arrowNavigateDown(activeElement) {
			activeElement
				.nextSibling
				.focus()
		},
		arrowNavigateLeft(activeElement) {
			console.log(activeElement)
			console.log('left')
		},
		arrowNavigateRight(activeElement) {
			console.log(activeElement)
			console.log('right')
		},

		enrichedItem(el, columns=1) {
			const parentEl = el.closest('.fav-list')
			const itemArray = Array.from(parentEl.children)
			const index = itemArray.findIndex(e => e == el)

			return {
				el,
				parentEl,
				index,
				listLength: itemArray.length,
				column: Math.ceil((index + 1) / columns),
				lastInColumn: ((index + 1) % columns == 0) || ((index + 1) == itemArray.length)
			}
		},
	}
}
</script>


<style scoped>

</style>
