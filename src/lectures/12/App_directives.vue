<template>
	<div>
		<p>{{ msg }}</p>
		<p v-text="msg"></p>
		<p v-html="htmlStr"></p>
		<p v-text="htmlStr"></p>
		<p v-once>{{ msg }} !!!!</p>
	</div>
</template>

<script>
import { ref } from 'vue';

export default {
	setup() {
		/**
		 * v-text는 html 태그 안에 textContent를 채운다.
		 * v-html은 innerHTML과 비슷하게 태그를 인식한다.
		 * v-once 엘리먼트와 컴포넌트를 한번(once)만 렌더링한다. 이후에 재렌더링 할 때
		 * 엘리먼트/컴포넌트 및 모든 하위 엘리먼트는 정적 컨텐츠로 처리되고 건너뛴다.
		 * 업데이트 성능을 최적화하는데 사용할 수 있다.
		 */
		const msg = ref('안녕하세요');
		const htmlStr = ref('<strong>안녕~!!!</strong>');
		return {
			msg,
			htmlStr,
		};
	},
};
</script>

<style scoped></style>
