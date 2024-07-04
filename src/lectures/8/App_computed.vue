<template>
	<div>
		<h2>{{ teacher.name }}</h2>
		<h3>강의가 있습니까?</h3>
		<p>{{ teacher.lectures.length > 0 ? '있음!' : '없음ㅠ' }}</p>
		<p>{{ hasLecture }}</p>
		<p>{{ hasLecture }}</p>
		<p>{{ existLecture() }}</p>
		<p>{{ existLecture() }}</p>
		<button v-on:click="counter++">Counter: {{ counter }}</button>
		<hr />
		<h2>이름</h2>
		<p>{{ fullName }}</p>
	</div>
</template>

<script>
import { computed, reactive, ref } from 'vue';

export default {
	setup() {
		const teacher = reactive({
			name: '짐코딩',
			lectures: ['HTML/CSS', 'JavaScript', 'Vue3'],
		});
		const hasLecture = computed(() => {
			/**
			 * computed는 한 번 계산된 결과를 캐시한다.
			 * 반응형 데이터가 변경되는 시점에서만 다시 계산한다.
			 * 기본적으로 getter 전용이다.
			 * 새로운 계산된 속성이 필요한 경우, getter와 setter를 모두 제공하여 속성을 만들 수 있다
			 */
			console.log('computed');
			return teacher.lectures.length > 0 ? '있음!' : '없음ㅠ';
		});

		const existLecture = () => {
			// 실행 될 때마다 계산한다
			console.log('existLecture');
			return teacher.lectures.length > 0 ? '있음!' : '없음ㅠ';
		};

		const counter = ref(0);

		const firstName = ref('홍');
		const lastName = ref('길동');

		// const fullName = computed(() => firstName.value + '' + lastName.value);
		const fullName = computed({
			get() {
				return firstName.value + ' ' + lastName.value;
			},
			set(value) {
				[firstName.value, lastName.value] = value.split(' ');
			},
		});

		console.log('Console 출력: ', fullName.value);
		fullName.value = '황 상은';
		return {
			teacher,
			hasLecture,
			counter,
			existLecture,
			fullName,
		};
	},
};
</script>

<style lang="scss" scoped></style>
