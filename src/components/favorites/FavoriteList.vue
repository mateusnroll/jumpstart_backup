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
		BookmarkService.all("1").then(b => {
			console.log(b)
			this.bookmarks = b
		})
	}
}
</script>


<style scoped>

</style>
