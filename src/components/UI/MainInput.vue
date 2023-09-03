<template>
	<input
		:value="modelValue"
		@input="updateInput"
		class="cr-post-input"
		type="text"
	/>
</template>

<script>
export default {
	name: 'main-input',
	props: {
		modelValue: [String, Number],
	},
	methods: {
		updateInput(event) {
			this.$emit('update:modelValue', event.target.value)
		},
	},
}
</script>

<style scoped>
.cr-post-input {
	width: 100%;
	border: 1px solid teal;
	padding: 10px 15px;
	margin-top: 15px;
}
</style>
