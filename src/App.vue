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
		<button @click="generate()">生成</button><button @click="tts()">読み上げ</button>
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
				name: 'ミサトさん',
				a: 'シンジくん！\nシンジくん！？\n聞いてる？\nこれが大人のキスよ\nわかったの！？\nいい！？\nエヴァーに乗りなさい\nうるさい！\n死になさい！\nサードチルドレンのあなたは'
			}, {
				name: 'しんじ君',
				a: 'こんなのってないよ…\n動け！\n動いてよぉ！！\nあんまりだよ…\n嫌だよぉ！\nなんで僕が\n笑えば…いいと思うよ…\n酷いよぉ…\nだって\nミサトさんが\nどうしよう…\nねえ！\n無理だよ…\nわからないよぉ！\n僕には'
			}, {
				name: '冨岡義勇',
				a: '生殺与奪の\n権を\n他人に\n握らせるな！\n みじめったらしく\nうずくまるのは\nやめろ！ \nそんなことが\n通用する\nなら \nお前の\n家族は\n殺されて\nいない！ \n奪うか\n奪われるかの\n時に\n主導権を\n握れない\n弱者が\n妹を治す？\n仇を見つける？\n笑止千万！！\n弱者には\n何の権利も\n選択肢もない\n悉く\n強者に\nねじ伏せられる\nのみ！！\n妹を\n治す方法は\n鬼なら\n知っているかもしれない\nだが\n鬼共が\nお前の\n意思や\n願いを\n尊重してくれると\n思うなよ\n当然\n俺も\nお前を\n尊重しない\nそれが現実だ！！！'
			}, {
				name: 'アマゾンの奥地へ向かった探検隊',
				a: '何かしら\n理由が\nあると\n皆が\n目指し\n始める\nアマゾンの\n奥地には\n一体何が\nあるのか？\nその謎を\n解明するため、\n我々調査隊は\nアマゾンの\n奥地へと\n向かった――。'
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
		},
		tts () {
			const msg = new SpeechSynthesisUtterance();
			msg.text = this.result;
			window.speechSynthesis.speak(msg);
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
