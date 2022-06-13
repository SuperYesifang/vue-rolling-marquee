<template>
	<div id="app">
		<Main class="rolling-marquee" direction="45deg" :shadow="true" :prompt="true">
			<div class="lyc">Hello World</div>
		</Main>
		<Main class="rolling-marquee prompt" direction="left" :shadow="true" :prompt="true">
			<div class="lyc">Hello World</div>
		</Main>
		<Main class="rolling-marquee prompt" direction="45deg" :shadow="true" :prompt="true">
			<div class="lyc">Hello World</div>
		</Main>
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
		width: calc(100% - 500px);
		height: 50px;
		border: 1px solid #000;
	}
	.prompt {
		width: 80px;
	}
	.lyc {
		white-space: nowrap;
	}
</style>
