<template>
	<div class="new-tab">		
		<favorite-section
			v-for="bookmark in bookmarks"
			:key="bookmark.id"
			:title="bookmark.title"
			:children="bookmark.children"/>
	</div>
</template>


<script>
import BookmarkService from './bookmarks/BookmarksService.vue'
import FavoriteSection from './favorites/FavoriteSection.vue'

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
h3 {
	margin: 40px 0 0;
}
ul {
	list-style-type: none;
	padding: 0;
}
li {
	display: inline-block;
	margin: 0 10px;
}
a {
	color: #42b983;
}
</style>
