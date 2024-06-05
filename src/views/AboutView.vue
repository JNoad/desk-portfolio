<template>
	<router-link to="/" id="back-btn">
		<img width="48" height="48" src="https://img.icons8.com/fluency-systems-filled/48/000000/circled-left-2--v2.png" alt="circled-left-2--v2"/>
	</router-link>
	<div class="about">
		<!-- <h1>This is an about page</h1> -->
		<Book :pages="array">
			<page>
				<page-front>
					<div style="width: 100%; height: 100%; text-align: center !important; display: flex; flex-direction: column; justify-content: center; align-items: center; padding-bottom: 20px;">
						<h1>About Me</h1>
						<p>By John-Bruce Noad</p>
					</div>
				</page-front>
				<page-back>
					<h2 style="text-decoration: underline">Who Am I?</h2>
					<img src="@/assets/logo.png" alt="" style="float: left; margin: 0 16px 4px 0">
					<p>I am a {{ new Date().getFullYear() - 2003 }} year old, born and raised in Cape Town South Africa. I was raised in primarily Afrikaans family, with strong Christian values. I have, however, always been in english schools where I was surrounded by different cultures and beliefs. I attended Groote Schuur Primary (in english) for 7 years before attending Wynberg Boys High for the following 5.
					<br>
					<br>
					Still unsure about my future at that point, I decided to use the next year to figure things out. I already had an interest in code/programming at this point, with basic self-taught knowledge on the topic, but during this year, this interest soared and through free online tutorials, I taught myself HTML, CSS, JavaScript and the basics NodeJS. I also began looking a little at mongoDB and Flutter, but at this point I had already discovered Life Choices and decided to join the academy.</p>

				</page-back>
			</page>

			<page>
				<page-front>
					<div  style="display: flex; flex-direction: column; align-items: center;">
						<h2 style="text-decoration: underline; width: 100%;">Hobbies and Interests:</h2>
						<p>I enjoy learning and often spend my spare time up-skilling by following along with coding tutorials or practising by doing my own coding projects and challenges. I also enjoy reading, especially non-fiction books. I particularly like the author 'Robert, Greene', who writes about concepts such as power, life/career strategies, and general self-improvement, which I am quite passionate about.
						<br>
						<br>
						I also enjoy playing chess as I find the game both challenging an stimulating. I began playing in high school, (although I had learn the basic rules, many years before) and quickly become absorbed in the game. I especially enjoyed competing against others for a position on the school's chess ladder, a ranking system for our chess players.</p>
						<img src="@/assets/logo.png" alt="">
					</div>
				</page-front>
				<page-back>
					<h2>Strengths</h2>
					<p>
						- I am a hardworking, passionate individual when it comes to my interests or the things I do. This is clear from the time I spend on my hobbies such as chess, reading and programming.
						- I am proactive and driven, when it comes to working toward my goals. This is evident form the work and learning I did independently and without external direction.
						- I am tenacious, as I will stop at nothing to get what I desire. This is best displayed in my attitude towards chess: When I face a tough opponent, I keep challenging them until I win.
						- Lastly, I am not only open to learning, but also thoroughly enjoy it, as shown by all of my previous examples.
					</p>
				</page-back>
			</page>
		</Book>
	</div>
</template>

<script>
import Book from '@/components/Book.vue';
export default {
	components: {
		Book
	},
	computed: {
		array() {
			let arr = []
			for (let i = 0; i < 10; i++) {
				arr.push(i)
			}
			return arr
		}
	},
}
</script>

<style lang="scss">
	.about {
		height: 100vh;
		display: flex;
		justify-content: center;
		align-items: center;
	}
	#back-btn {
		position: absolute;
		top: 5px; left: 5px;
	}
</style>