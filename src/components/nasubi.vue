<script setup lang="ts">
import { ref,reactive, computed, watch, watchEffect } from "vue";

defineProps({
	msg: String,
});
console.log("nasubi");
let msgs = "<h2>楽しいなー</h2>";
const link = "https://www.youtube.com/";
let isActive = true; //簡単に変更可能
let isBack = false;
// letは再代入可能const不可
const error = true;

let stock = 10;

let stockMsg = "";
if (stock > 5) {
	stockMsg = "在庫あり";
} else if (stock > 0) {
	stockMsg = "残りわずか";
} else {
	stockMsg = "在庫なし";
}


let fruits = ["apple", "banana", "cherry"];
const users = [
	{ id: 1, name: "mini nasu", email: "nasu@gmail.com", admin: true },
	{ id: 2, name: "Jane Doe", email: "jane@example.com", admin: false },
	{ id: 3, name: "Kevin MacDonald", email: "kevin@test.com", admin: false },
];

const click_button = (event:any) => {
	console.log("5man-yen");
	event.target.style.backgroundColor = "red";
};

const send = () => {
	console.log("send");
};

const count = ref(0);

const count2 = ref(0);
const addCount = () => {
	count2.value++;
};

const state = reactive({
	count: 0,
});
// reactiveでのカウント

const message = ref("Hello World");
const clickButton = () => {
	console.log(message.value);
};

const user = reactive({
	firstName: 'nasubi',
	lastName: 'nasu',
})

const fullName = computed(() => `${user.firstName} ${user.lastName}`);
// 定義された変数を加工する＃script内で使うときはvalueが必要
// computedはなんかむずめかもー

watch(count, (count, previousCount) => {
	console.log('count:', count);
	console.log('previousCount:', previousCount);
})

watch(() => state.count, (count, previousCount) => {
	console.log('count:', count);
	console.log('previousCount:', previousCount);
},
	//{ immediate: true }//これをつけるとページを開いたときにも実行される
);
// watchでrefやreactiveの変化を監視するｗｗ
watchEffect(() => console.log(count.value));
// `${count.value}/${count2.value}`)このように複数の関数を表示する
</script>

<template>
	-------------------------------------
	<h1>{{ msg }}</h1>
	<p v-text="msgs"></p>
	<p v-html="msgs"></p>

	<a :href="link" target="_blank">ようつべに飛ぶ</a>

	<!-- v-bindは:で省略できてplayerの行動によって動作を変えることが出来る -->
	<p class="size" :class="{ red: isActive }">v-bindの設定方法の確認1</p>
	<!-- クラスも動的にできる -->
	<p :class="[{ yellowGreen: isActive }, { back: isBack }]">
		v-bindの設定方法の確認2
	</p>
	<!-- 配列を使えてその中にオブジェクトを使う方法もある -->
	<!-- styleは使わない -->
	<div v-if="error">エラーないよ</div>
	<div v-else>err0r!!!!</div>

	<div v-if="stock > 5">
		在庫あり
		<div class="small">注釈:到着まで５年かかります</div>
	</div>
	<div v-else-if="stock > 0">残りわずか</div>
	<div v-else="(stock = 0)">在庫なし</div>
	<div>在庫は{{ stock }}</div>
	<br />

	<div v-for="x in fruits" :key="x">{{ x }}</div>
	<ul>
		<li v-for="user in users" :key="user.id">
			{{ user.id }}:{{ user.name }}({{ user.email }})
		</li>
	</ul>
	<!-- forの中にifを入れることで表示させるさせないを判断できる -->

	<button @click="click_button">ここをクリックすると５万円！！</button>
	<!-- v-on:click は@clickと省略できる -->
	<!-- @click="click_button,nasu('nasubi')"のように２つ関数を起動できる -->

	<form @submit.prevent="send">
		<!-- イベント修飾子 -->
		<button @keyup.enter="submit">送信</button>
		<!-- キー修飾子 -->
	</form>

	<button type="button" @click="count++">count is: {{ count }}</button>
	<!-- 定義だけjs -->
	<button type="button" @click="addCount">{{ count2 }}回押したね</button>
	<!-- 計算もjs -->
	<button type="button" @click="state.count++">
		count is: {{ state.count }}
	</button>
	<!-- reactiveﾊﾞｰｼﾞｮﾝ -->

	<p>{{ message }}</p>
	<input v-model.lazy="message" />
	<!-- lazy:入力されるまで反映されないtrim:前後の空白をなくす -->
	<!-- 数値を入力するにはtype=number -->
	<div><button @click="clickButton">Click</button></div>
	<!-- typeofは関数の型を確認 -->

	<p>fullName:{{ fullName }}</p>

	<br />
</template>

<style scoped>
.red {
	color: rgb(226, 95, 95);
	font-weight: 900;
}

.size {
	font-size: 20px;
}

.back {
	background-color: aqua;
}

.yellowGreen {
	color: yellowgreen;
}

.small {
	font-size: 10px;
}
</style> 