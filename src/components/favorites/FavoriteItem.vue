<template>
	<a 
		class="fav-item"
		:href="url">

		<img :src="'chrome://favicon/' + url">
		{{ title }}
	</a>
</template>

<script>
export default {
	props: {
		title: String,
		url: String
	}
}
</script>

<style scoped>
a {
	display: block;
}
</style>