<template>
	<!-- В данном компоненте нет корневого блока(root). Посты находятся здесь в отдельном блоке и располагаются один за другим. Во Vue 2 такое не прокатит. Там в шаблоне должен располагаться какой-то корневой элемент допустим <div>. Во Vue 3 можно использовать несколько блоков, при этом корневой элемент какой-то не является обязательным. Но все же когда мы используем циклы, лучше какой-нибудь корневой элемент сделать. -->
	<div v-if="posts.length > 0">
		<h3>Список постов</h3>
		<post-item
			v-for="post in posts"
			:post="post"
			:key="post.id"
			@remove="$emit('remove', post)"
		/>
	</div>
	<!-- Можно добавить дир. v-show чтобы div с постами полностью не удалялся из DOM дерева -->
	<h2 v-else style="color: red">Список постов пуст</h2>
</template>

<script>
import PostItem from '@/components/PostItem'
export default {
	// Текущий компонент ожидает posts как аргумент. Эти аргументы называются props
	// Пропсы в дочернем компоненте изменять нельзя
	components: { PostItem },
	props: {
		posts: {
			type: Array,
			required: true,
		},
	},
}
</script>

<style scoped></style>
