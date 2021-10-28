<template>
	<div id="app">
		<Main class="rolling-marquee">Hello World</Main>
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
		border: 1px solid #000;
		height: 60px;
	}
</style>
