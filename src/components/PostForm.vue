<template>
	<form @submit.prevent>
		<h4>Create Post</h4>
		<main-input v-model="post.title" type="text" placeholder="Название" />
		<main-input v-model="post.body" type="text" placeholder="Описание" />
		<main-btn class="btn-post-form" @click="createPost">Создать</main-btn>
	</form>
</template>

<script>
export default {
	data() {
		return {
			post: {
				title: '',
				body: '',
			},
		}
	},
	methods: {
		createPost() {
			// При создании нам нужно передать дочерний элемент в родительский массив
			this.post.id = Date.now()
			this.$emit('create', this.post)
			this.post = {
				title: '',
				body: '',
			}
		},
	},
}
</script>

<style scoped>
form {
	display: flex;
	flex-direction: column;
}

.btn-post-form {
	margin-top: 15px;
	align-self: flex-end;
}
</style>
