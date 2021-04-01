<template>
	<div class="main">
		テンプレート: <select @change="randoms = $event.target.value">
			<option value="" selected>選択されてません</option>
			<option v-for="template in templates" :value="template.a" :key="template.name">{{template.name}}</option>
		</select><br>
		回数<input type="number" v-model="count" @input="generate()"> <br>
		ランダムにする候補: <br>
		<textarea v-model="randoms" cols="30" rows="10"></textarea><br>
		結果:<br>
		<textarea v-model="result" cols="30" rows="10"></textarea><br>
		<button @click="generate()">生成</button>
		<details>
			<summary>プライバシーポリシー</summary>
			このサイトは Google アナリティクスを使用しています
		</details>
	</div>
</template>

<script>
export default {
	name: 'App',
	components: { },
	data: () => ({
		randoms: "",
		count: 40,
		result: "",
		templates: [
			{
				name: 'エヴァンゲリオン',
				a: 'シンジくん！\nシンジくん！？\n聞いてる？\nこれが大人のキスよ\nわかったの！？\nいい！？\nエヴァーに乗りなさい\nうるさい！\n死になさい！\nサードチルドレンのあなたは'
			}, {
				name: 'ピエンｗ',
				a: 'ﾋﾟ\nｴ\nﾝ\n🥺\nw'
			}
		]
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
