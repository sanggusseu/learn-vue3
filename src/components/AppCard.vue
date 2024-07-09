<template>
	<div class="card">
		<div class="card-body">
			<span class="badge bg-secondary">{{ typeName }}</span>
			<h5 class="card-title mt-2">{{ title }}</h5>
			<p class="card-text">
				{{ content }}
			</p>
			<a href="#" class="btn" :class="isLikeClass" @click="toggleLike">
				좋아요
			</a>
		</div>
	</div>
</template>

<script>
import { computed } from 'vue';

export default {
	props: {
		type: {
			type: String,
			default: 'news',
			validator: value => ['news', 'notice'].includes(value),
		},
		title: {
			type: String,
			required: true,
		},
		content: {
			type: String,
			// required: true,
		},
		isLike: {
			type: Boolean,
			default: false,
		},
	},
	emits: ['toggleLike'],
	setup(props, context) {
		const isLikeClass = computed(() =>
			props.isLike ? 'btn-danger' : 'btn-outline-danger',
		);
		const typeName = computed(() =>
			props.type === 'news' ? '뉴스' : '공지사항',
		);
		const toggleLike = () => {
			// props.isLike = !props.isLike;
			// props.obj.title = '김길동';
			context.emit('toggleLike', props.isLike);
		};
		return {
			isLikeClass,
			typeName,
			toggleLike,
		};
	},
};
</script>

<style lang="scss" scoped></style>
