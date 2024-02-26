<script setup lang="ts">
	definePageMeta({
		validate: async (route) => {
			// Check if the id is made up of digits
			return /^\d+$/.test(route.params.id)
		}
	})

	const { id } = useRoute().params;

	const { data: post, pending } = await useFetch(`https://7b554fec6e7060c7.mokky.dev/blog/${id}`, {
		lazy: true,
		server: false,
	});
	console.log(id, post);
</script>

<template>
	<div v-if="pending">Loading ...</div>
	<div v-else class="container">
		<img :src="post.image" :alt="post.title">
		<h1>{{ post.title }}</h1>
		<h4>{{ post.description }}</h4>
		<p>{{ post.text }}</p>
		<p>{{ post.date }}</p>
	</div>
</template>

<style scoped>

</style>
