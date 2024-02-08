<script setup type="ts">
	const { data: posts } = useFetch('https://7b554fec6e7060c7.mokky.dev/blog');
</script>

<template>
	<h1>Blog</h1>
	<section>
		<div class="container">
			<div class="row row-cols-4 gap-3">
				<div class="card" style="width: 18rem;" v-for="post in posts" :key="post.id">
					<img :src="post.image" class="card-img-top" :alt="post.title"/>
					<div class="card-body">
						<h5 class="card-title">{{ post.title }}</h5>
						<p class="card-text">{{ post.description }}</p>
						<NuxtLink class="btn btn-primary" :to="`/blog/${post.id}`">Go somewhere</NuxtLink>
					</div>
				</div>
			</div>
		</div>
	</section>
</template>

<style scoped>

</style>
