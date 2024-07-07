<template>
	<div>
		<h2>input Value</h2>
		<!-- <input
			type="text"
			:value="inputValue"
			@input="event => (inputValue = event.target.value)"
		/> -->
		<input type="text" v-model="inputValue" />
		<div>{{ inputValue }}</div>
		<!-- <textarea
			:value="textareaValue"
			@input="event => (textareaValue = event.target.value)"
		></textarea> -->
		<textarea v-model="textareaValue"></textarea>
		<div>{{ textareaValue }}</div>
		<hr />
		<h2>checkbox value</h2>
		<label for="checkbox">{{ checkboxValue }}</label>
		<input
			type="checkbox"
			id="checkbox"
			v-model="checkboxValue"
			true-value="힣"
			false-value="힝"
		/>
		<!-- <input
			type="checkbox"
			id="checkbox"
			:checked="checkboxValue"
			@change="event => (checkboxValue = event.target.checked)"
		/> -->

		<h2>checkbox Values</h2>
		<label for="html">html</label>
		<input type="checkbox" id="html" value="html" v-model="checkboxValues" />
		<label for="css">css</label>
		<input type="checkbox" id="css" value="css" v-model="checkboxValues" />
		<label for="js">javascript</label>
		<input type="checkbox" id="js" value="js" v-model="checkboxValues" />
		<div>{{ checkboxValues }}</div>
		<h2>radio value</h2>
		<label>
			<input type="radio" name="type" value="O" v-model="radioValue" />
			<!-- <input
				type="radio"
				name="type"
				value="O"
				:checked="radioValue === 'O'"
				@change="event => (radioValue = event.target.value)"
			/> -->
			O형
		</label>
		<label>
			<input type="radio" name="type" value="A" v-model="radioValue" />
			A형
		</label>
		<div>{{ radioValue }}</div>

		<h2>select value</h2>
		<select v-model="selectValue">
			<!-- <select
			:value="selectValue"
			@change="event => (selectValue = event.target.value)"
		> -->
			<option value="html">HTML 수업</option>
			<option value="css">CSS 수업</option>
			<option value="javascript">JavaScript 수업</option>
		</select>
		<div>{{ selectValue }}</div>
	</div>
</template>

<script>
import { ref } from 'vue';

export default {
	setup() {
		const inputValue = ref('');
		const textareaValue = ref('');
		const checkboxValue = ref(true);
		const checkboxValues = ref([]);
		const radioValue = ref('O');
		const selectValue = ref('html');
		return {
			inputValue,
			textareaValue,
			checkboxValue,
			checkboxValues,
			radioValue,
			selectValue,
		};
	},
};
</script>

<style lang="scss" scoped></style>
