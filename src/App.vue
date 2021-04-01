<template>
	<div class="main">
		Count<input type="number" v-model="count" @input="generate()"> <br>
		randoms: <br>
		<textarea v-model="randoms" cols="30" rows="10"></textarea><br>
		result:<br>
		<textarea v-model="result" cols="30" rows="10"></textarea>
	</div>
</template>

<script>
export default {
	name: 'App',
	components: { },
	data: () => ({
		randoms: "",
		count: 10,
		result: ""
	}),
	watch: {
		randoms () {
			this.generate();
		}
	},
	methods: {
		generate () {
			this.result = '';
			const randoms = this.randoms.split('\n');
			for (let i=0; i<this.count; i++) {
				this.result += randoms[Math.floor(Math.random() * randoms.length)]
			}
		}
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
