<template>
	<div class="new-tab">
		<div class="logo-container">
			<img 
				class="small-logo"
				src="assets/logo-small.svg"
				width=32 height=40 />
		</div>

		<search-box
			@query-update="queryUpdate"/>
		
		<favorite-list
			v-show="!hasActiveQuery"/>

		<search-list
			v-show="hasActiveQuery"
			:query="searchQuery"/>
	</div>
</template>


<script>
import FavoriteList from './favorites/FavoriteList.vue'
import SearchBox from './search/SearchBox.vue'
import SearchList from './search/SearchList.vue'

export default {
	components: { FavoriteList, SearchBox, SearchList },
	name: 'NewTab',

	data: function() {
		return {
			searchQuery: ''
		}
	},

	methods: {
		queryUpdate(query) {
			this.searchQuery = query
		}
	},

	computed: {
		hasActiveQuery: function() {
			return this.searchQuery.length > 0
		}
	}
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
