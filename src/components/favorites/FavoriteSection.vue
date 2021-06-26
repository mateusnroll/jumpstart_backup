<template>
	<div class="fav-section">
		<h2 class="section-title">{{ title }}</h2>
		
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
.fav-section {
	margin-top: 5rem;
}

.section-title {
	font-size: 2rem;
	margin: 0 0 .5rem .5rem;
}

.fav-list {
	column-count: 2;
}
</style>