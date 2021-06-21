<template>
	<div id="app">
		<NewTab />
	</div>
</template>

<script>
import NewTab from './components/NewTab.vue'

export default {
	name: 'App',
	components: {
		NewTab
	}
}
</script>

<style>
#app {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
	text-align: center;
	color: #2c3e50;
	margin-top: 60px;
}
</style>
