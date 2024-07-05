<template>
	<div>
		<div :style="styleObject">
			Lorem ipsum dolor, sit amet consectetur adipisicing elit. Aperiam
			voluptatibus explicabo quo vitae ut dolorum commodi accusamus. Labore,
			ipsa dolor reiciendis quas impedit temporibus, iste qui, eligendi et neque
			voluptate?
		</div>
		<button v-on:click="fontSize--">-</button>
		<button v-on:click="fontSize++">+</button>
	</div>
</template>

<script>
import { computed, reactive, ref } from 'vue';

export default {
	setup() {
		/**
		 * style 객체를 만들 때 속성에 하이픈이 있다면
		 * 하이픈 대신 카멜케이스로 작성한다.
		 */

		// const styleObject = reactive({
		// 	color: 'red',
		// 	fontSize: '13px',
		// });

		const fontSize = ref(13);

		const styleObject = computed(() => {
			return {
				color: 'red',
				fontSize: fontSize.value + 'px',
			};
		});
		return {
			styleObject,
			fontSize,
		};
	},
};
</script>

<style lang="scss" scoped></style>
