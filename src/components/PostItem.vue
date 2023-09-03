<template>
	<!-- Почему отдельно? Потому что вдруг нам нужно отрисовать не список постов, а отдельно взятый пост -->
	<div class="post">
		<div>
			<div><strong>Название</strong> {{ post.title }}</div>
			<div><strong>Описание</strong> {{ post.body }}</div>
		</div>
		<div class="post__btns">
			<main-btn @click="$emit('remove', post)">Удалить</main-btn>
		</div>
	</div>
</template>

<script>
export default {
	props: {
		post: {
			type: Object,
			required: true,
		},
	},
}
</script>

<style scoped>
.post {
	padding: 15px;
	border: 2px solid teal;
	margin-top: 15px;
	display: flex;
	align-items: center;
	justify-content: space-between;
}
</style>
