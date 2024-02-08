<script setup lang="ts">
	definePageMeta({
		validate: async (route) => {
			// Check if the id is made up of digits
			return /^\d+$/.test(route.params.id)
		}
	})

	const { id } = useRoute().params;

	const { data: post } = useFetch(`https://7b554fec6e7060c7.mokky.dev/blog/${id}`);
	console.log(id, post);
</script>

<template>
	<div class="container">
<!--		<img :src="post.image" :alt="post.title">-->
		<h1>{{ post.title }}</h1>
		<h4>{{ post.description }}</h4>
		<p>{{ post.text }}</p>
		<p>{{ post.date }}</p>
	</div>
</template>

<style scoped>

</style>
