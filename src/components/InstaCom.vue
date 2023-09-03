<template>
	<div class="instagram-comments">
		<h2 style="margin-bottom: 15px">Список комментариев</h2>
		<div class="publish">
			<div class="publish__img">
				Публикация:
				<img :src="publish.media_url" alt="" />
			</div>
			<div class="publish__username">
				<p>Пользователь: @{{ publish.username }}</p>
				<p>Количество: лайков: {{ publish.like_count }}</p>
			</div>
		</div>
		<div>
			<h4>
				<strong>Количество комментариев:</strong> {{ publish.comments_count }}
			</h4>
		</div>
		<div class="comment" v-for="comment in comments">
			<div>{{ comment.text }}</div>
		</div>
	</div>
</template>

<script>
export default {
	props: {
		comments: {
			type: Array,
			required: true,
		},
		publish: {
			type: Array,
			required: true,
		},
	},
}
</script>

<style scoped>
.instagram-comments {
	padding: 20px;
	margin: 15px 0;
	border: 2px solid red;
}
.comment {
	border: 2px solid salmon;
	padding: 10px 15px;
	margin-top: 5px;
	border-radius: 15px;
}
.publish {
	display: flex;
	justify-content: center;
	align-items: center;
	margin-bottom: 15px;
}
.publish__img {
	text-align: center;
	width: calc(20% + 60px);
	margin-right: 20px;
}
.publish__img img {
	display: block;
	width: 100%;
	border-radius: 50%;
}
</style>
