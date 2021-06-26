<template>
	<div class="search-container">

		<div class="search-box">
			<img
				class="icon-search"
				src="assets/icons/icon-search.svg"/>

			<input 
				class="search-input"
				type="text">
		</div>
		
	</div>
</template>

<script>
export default {
	props: { }
}
</script>

<style scoped>
.search-container {
	width: 100%;
	margin-top: 3.5rem;
	margin-bottom: 5rem;
	display: flex;
	justify-content: center;
}

.search-box {
	--angle: 0deg;

	display: flex;
	width: 100%;
	max-width: 30rem;
	padding: 1rem;

	background-color: #262729;

	border-radius: 8px;

	animation: 10s rotate linear infinite;
}

.icon-search {
	flex-shrink: 0;
	margin-right: .5rem;

	/* icon-color: 737680 */
	filter: invert(51%) sepia(6%) saturate(588%) hue-rotate(189deg) brightness(88%) contrast(86%); 
}

.search-input {
	flex-grow: 1;

	/* background-color: transparent; */
	border: none;
	outline: none;
}
</style>