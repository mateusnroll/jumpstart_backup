<template>
	<div class="new-tab">
		<div class="logo-container">
			<img 
				class="small-logo"
				src="assets/logo-small.svg"
				width=32 height=40 />
		</div>

		<search-box/>
		<favorite-list/>
	</div>
</template>


<script>
import FavoriteList from './favorites/FavoriteList.vue'
import SearchBox from './search/SearchBox.vue'

export default {
	components: { FavoriteList, SearchBox },
	name: 'NewTab'
}
</script>


<style scoped>
.new-tab {
	padding-top: 3rem;
}

.logo-container {
	width: 100%;
	text-align: center;
}
</style>
