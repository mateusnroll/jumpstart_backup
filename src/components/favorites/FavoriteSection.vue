<template>
	<div class="fav-section">
		<h2>{{ title }}</h2>
		
		<div class="fav-list">
			<favorite-item
				v-for="bookmark in children" 
				:key="bookmark.id"
				:title="bookmark.title"
				:url="bookmark.url"/>
		</div>
	</div>
</template>


<script>
import FavoriteItem from './FavoriteItem.vue'

export default {
	components: { FavoriteItem },
	props: {
		title: String,
		children: Array
	}
}
</script>


<style scoped>
.fav-list {
	column-count: 2;
}

</style>