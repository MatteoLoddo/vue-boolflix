<template>
	<div class="">
		<input type="text" v-model="SearchText" placeholder="Nome Del Film" @keyup.enter="$emit('SearchText', SearchText)" >
		<button class="btn" @click="$emit('SearchText', SearchText) " >Cerca</button>
	</div>
</template>

<script>
export default {
	name: 'TheHeader',
	data() {
		return {
			SearchText: "",

		}
	},

	methods: {

	},
}
</script>

<style>
</style>
