<template>
	<div class="">
		<input type="text" v-model="SearchText">
		<button class="btn" @click="$emit('SearchText', SearchText)">Cerca</button>
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
