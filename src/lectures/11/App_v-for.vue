<template>
	<div>
		<ul>
			<!-- <li v-for="(item, index) in items" v-bind:key="index">
				{{ index }}-{{ item.message }}
			</li> -->
			<template v-for="item in evenItems" :key="item.id">
				<!-- <li v-if="index % 2 === 0">인덱스: {{ index }}, {{ item.message }}</li> -->
				<li>인덱스: {{ item.id }}, {{ item.message }}</li>
			</template>
		</ul>
		<hr />
		<ul>
			<li v-for="(value, key, index) in myObject" :key="key">
				{{ index }}-{{ key }}-{{ value }}
			</li>
		</ul>
	</div>
</template>

<script>
import { computed, reactive } from 'vue';

export default {
	/**
	 * v-for는 for-in 문법을 통해 목록을 쉽게 렌더링 할 수 있다 (array, object)
	 * 한 요소에서 v-for랑 v-if를 동시에 쓰는 것은 안 좋다고 한다.
	 * 공식 문서 읽어보고 왜 안 좋은지 주석 달기!
	 */
	setup() {
		const items = reactive([
			{ id: 1, message: 'Java' },
			{ id: 2, message: 'HTML' },
			{ id: 3, message: 'CSS' },
			{ id: 4, message: 'JavaScript' },
		]);

		const evenItems = computed(() => items.filter(item => item.id % 2 === 0));

		const myObject = reactive({
			title: '제목',
			author: '홍길동',
			publishedAt: '2016-01-01',
		});
		return {
			items,
			evenItems,
			myObject,
		};
	},
};
</script>

<style lang="scss" scoped></style>
