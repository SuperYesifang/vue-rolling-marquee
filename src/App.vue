<template>
	<div id="app">
		<Main class="rolling-marquee" direction="left" :shadow="true">Hello World</Main>
	</div>
</template>

<script>
	import Main from "./components/Main.vue";
	export default {
		components: { Main },
		name: "app",
		data() {
			return {};
		}
	};
</script>

<style>
	.rolling-marquee {
		margin: 100px auto;
		width: 150px;
		height: 50px;
		border: 1px solid #000;
	}
</style>
