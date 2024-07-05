<template>
	<div>
		<h2 v-if="visible">Hello Vue3!</h2>
		<h2 v-else>false 입니다.</h2>
		<button v-on:click="visible = !visible">toggle</button>
		<hr />
		<h2 v-if="type === 'A'">A입니다.</h2>
		<h2 v-else-if="type === 'B'">B입니다.</h2>
		<h2 v-else-if="type === 'C'">C입니다.</h2>
		<h2 v-else>A, B, C 모두 아닙니다.</h2>
		<button v-on:click="type = 'A'">A</button>
		<button v-on:click="type = 'B'">B</button>
		<button v-on:click="type = 'C'">C</button>
		<button v-on:click="type = 'else'">else</button>
		<hr />
		<template v-if="visible">
			<h1>Title</h1>
			<p>Paragraph 1</p>
			<p>Paragraph 2</p>
		</template>
		<hr />
		<h1 v-show="ok">제목 입니당</h1>
		<button v-on:click="ok = !ok">toggle</button>
	</div>
</template>

<script>
import { ref } from 'vue';

export default {
	setup() {
		/**
		 * v-if, v-show
		 * v-if: false면 렌더링 조차 안 된다.
		 * v-show: 항상 렌더링 되며, false일 때 display: none이 적용된다.
		 * 일반적으로 v-if는 전환 비용이 높아 자주 전환해야 한다면 v-show를 사용하는 것이 좋고
		 * 런타임 시 조건이 변경되지 않는다면 v-if를 사용하는 것이 더 낫다.
		 */
		const visible = ref(true);
		const type = ref('A');
		const ok = ref(true);

		return {
			visible,
			type,
			ok,
		};
	},
};
</script>

<style lang="scss" scoped></style>
