<template>
	<router-link to="/" id="back-btn">
		<img width="48" height="48" src="https://img.icons8.com/fluency-systems-filled/48/000000/circled-left-2--v2.png" alt="circled-left-2--v2"/>
	</router-link>
	<div class="about">
		<!-- <h1>This is an about page</h1> -->
		<Book :pages="array">
			<page>
				<page-front>
					<div class="tester-class">
						<h1>Hello...</h1>
						<p>My name is Lindayle P. Tutwater</p>
					</div>
				</page-front>
				<page-back>
					<div class="div-2">
						Hi
					</div>

				</page-back>
			</page>

		</Book>
		<!-- <page>
			Hi
		</page> -->
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