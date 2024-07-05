<template>
	<div>
		<!-- <div class="text" :class="{ active: isActive, 'text-danger': hasError }">
			텍스트 입니다.
		</div> -->
		<!-- <div class="text" :class="classObject">텍스트 입니다.</div> -->
		<!-- <div class="text" :class="[activeClass, errorClass]">텍스트 입니다.</div> -->
		<div
			class="text"
			:class="[isActive ? 'active-class' : 'class', errorClass, classObject]"
		>
			텍스트 입니다.
		</div>
		<button v-on:click="toggle">toggle</button>
		<button v-on:click="hasError = !hasError">toggleError</button>
	</div>
</template>

<script>
import { computed, reactive, ref } from 'vue';

export default {
	setup() {
		/**
		 * 원래 html 속성에 v-bind를 하면 기존값은 사라지지만
		 * class만 예외적으로 v-bind 따로, 기존값 따로 설정할 수 있다.
		 * v-bind는 자주 쓰는 디렉티브라 :로 단축하여 사용할 수 있다.
		 * 값으로 변수, 객체, 배열을 줄 수 있다.
		 */
		const isActive = ref(true);
		const hasError = ref(false);

		// const classObject = reactive({
		// 	active: true,
		// 	'text-danger': true,
		// });

		const classObject = computed(() => {
			return {
				active: true && true,
				'text-danger': true && true,
			};
		});

		const activeClass = ref('active');
		const errorClass = ref('error');

		const toggle = () => {
			isActive.value = !isActive.value;
		};

		return {
			isActive,
			toggle,
			hasError,
			classObject,
			activeClass,
			errorClass,
		};
	},
};
</script>

<style scoped>
.active {
	font-weight: 900;
}

.text-danger {
	color: red;
}
</style>
