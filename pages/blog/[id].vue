<script lang="js">
	export default {
		validate({params}) {
			return /^\d+$/.test(params.id)
		}
	}
</script>

<template>
	<h1>{{$route.params.id}}</h1>
</template>

<style scoped>

</style>
