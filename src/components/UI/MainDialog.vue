<template>
	<div class="dialog" v-if="show" @click.stop="hideDialog">
		<div @click.stop class="dialog__content">
			<slot></slot>
			<!-- Поместили slot чтобы модалка была динамически изменяема -->
		</div>
	</div>
</template>

<script>
export default {
	name: 'main-dialog',
	props: {
		show: {
			// Этот пропс будет отвечать за то, видим ли мы модальное окно или нет. Типа boolean флажок(звоночек :3)
			type: Boolean,
			default: false,
		},
	},
	methods: {
		hideDialog() {
			this.$emit('update:show', false)
		},
	},
}
</script>

<style scoped>
.dialog {
	top: 0;
	bottom: 0;
	right: 0;
	left: 0;
	background: rgba(0, 0, 0, 0.5);
	position: fixed;
	display: flex;
}
.dialog__content {
	margin: auto;
	padding: 20px;
	background: white;
	border-radius: 12px;
	min-height: 50px;
	min-width: 300px;
}
</style>
