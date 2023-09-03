<template>
	<div class="app">
		<h1>Страница с постами</h1>
		<main-btn @click="showDialog" style="margin: 15px 0">Создать пост</main-btn>
		<main-dialog v-model:show="dialogVisible">
			<post-form @create="createPost" />
		</main-dialog>
		<insta-com :comments="comments" :publish="publish" />
		<post-list @remove="removePost" :posts="posts" />
	</div>
</template>

<script>
import PostForm from '@/components/PostForm'
import PostList from '@/components/PostList'
import InstaCom from '@/components/InstaCom'
import axios from 'axios'

export default {
	components: {
		PostList,
		PostForm,
		InstaCom,
	},
	data() {
		return {
			posts: [],
			comments: [],
			publish: [],
			dialogVisible: false,
			modificatorValue: '',
			testURL: 'https://jsonplaceholder.typicode.com/posts?_limit=2',
			commentsURL:
				'https://graph.facebook.com/v17.0/17944200101041000?fields=comments%2Cmedia_url%2Ccomments_count%2Cusername%2Clike_count&access_token=EAAL2VLFyJbIBOw8tVICjoAastIaIucSC9xNQV5JqKSz7dz7pJ3JH8CtkcrqQIlyXv23p5CG0CZCIoCinav6ZA6Y63e1MNvre59gXsgnSTz4ZCKkwrbGnZB4OTlK5QMLjZBAKd7EWgegDxW19c2q7ZCm3tKLZCjZBchYHL2Or8PptM1JNfUdz93XKQnoUsbKbbpmF',
		}
	},
	methods: {
		createPost(post) {
			this.posts.push(post)
			this.dialogVisible = false
		},
		removePost(post) {
			this.posts = this.posts.filter(p => p.id !== post.id) // В результирующий массив попадают те посты, id которых не равен посту который мы пытаемся удалить
		},
		showDialog() {
			this.dialogVisible = true
		},
		async fetchPosts() {
			try {
				const response = await axios.get(this.testURL)
				this.posts = response.data
			} catch (error) {
				alert('Ошибка')
			}
		},
		async fetchComments() {
			try {
				const response = await axios.get(this.commentsURL)
				this.comments = response.data.comments.data
				this.publish = response.data
				console.log(response.data)
			} catch (error) {
				console.log('Ошибка')
			}
		},
	},
	mounted() {
		this.fetchPosts()
		this.fetchComments()
	},
}
</script>

<style>
* {
	margin: 0;
	padding: 0;
	box-sizing: border-box;
}
.app {
	padding: 20px;
}
</style>
