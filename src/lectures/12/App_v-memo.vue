<template>
	<div>
		<div v-once>
			<h2>v-once</h2>
			<p>subscribers: {{ subscribers }}</p>
			<p>views: {{ views }}</p>
			<p>likes: {{ likes }}</p>
		</div>
		<div v-memo="[subscribers]">
			<h2>v-memo</h2>
			<p>subscribers: {{ subscribers }}</p>
			<p>views: {{ views }}</p>
			<p>likes: {{ likes }}</p>
		</div>
		<div>
			<h2>힣</h2>
			<p>subscribers: {{ subscribers }}</p>
			<p>views: {{ views }}</p>
			<p>likes: {{ likes }}</p>
		</div>
		<button @click="subscribers++">Subs++</button>
		<button @click="views++">Views++</button>
		<button @click="likes++">Likes++</button>
	</div>
</template>

<script>
import { ref } from 'vue';

export default {
	/**
	 * v-memo 성능과 관련된 디렉티브로 배열 안에 반응형 데이터를 넣으면, 그 데이터가
	 * 변경 됐을 때만 재렌더링 한다.
	 * 성능최적화가 필요할 때만 사용한다.
	 * ex) 리스트의 길이가 1000개가 넘어갈 때
	 */
	setup() {
		const subscribers = ref(4000);
		const views = ref(400);
		const likes = ref(20);

		return {
			subscribers,
			views,
			likes,
		};
	},
};
</script>

<style lang="scss" scoped></style>
