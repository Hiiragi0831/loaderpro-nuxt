<script type="ts">
// type Post = {
// 	id: string | number;
// 	title: string;
// 	description: string;
// 	text: string;
// 	date: Date;
// 	image: string;
// };
export default defineComponent({
	data() {
		return {
			posts: []
		};
	},
	created() {
		fetch('https://7b554fec6e7060c7.mokky.dev/blog')
			.then((res) => res.json())
			.then((posts) => {
				// store the posts in the reactive state
				console.log(posts);
				this.posts = posts;
			});
	},
	methods: {
		goTo(id) {
			this.$router.push('/blog/' + id);
		},
	},
});
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
<!--						<NuxtLink class="btn btn-primary" to="'/post/' + post.id">Go somewhere</NuxtLink>-->
						<button class="btn btn-primary" @click.prevent="goTo(post.id)">Go somewhere</button>
					</div>
				</div>
			</div>
		</div>
	</section>
</template>

<style scoped>

</style>
