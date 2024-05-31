<template>
    <nav v-if="showBookShelf">
        <ul>
            <li class="book-red">
                <router-link to="about">About Me</router-link>
            </li>
            <li class="book-blue">
                <router-link to="resume">Resume</router-link>
            </li>
            <li class="book-green">
                <router-link to="projects">Projects</router-link>
            </li>
            <li class="book-orange">
                <router-link to="testimonials">Testimonials</router-link>
            </li>
        </ul>
        <img class="shelf" src="@/assets/shelf.png">
    </nav>
    <router-link to="/" id="back-btn" v-else>
		<img width="48" height="48" src="https://img.icons8.com/fluency-systems-filled/48/000000/circled-left-2--v2.png" alt="circled-left-2--v2"/>
	</router-link>
</template>
<script>
export default {
    computed: {
        showBookShelf() {
            return this.$route.path == '/';
        }
    }
}
</script>
<style lang="scss">
    nav {
        padding: 0;
        ul {
            display: flex;
            z-index: 11;
            justify-content: center;
            list-style-type: none;
            height: 100%;
            margin: 0;
            position: relative;
            perspective: 2000px;
            li {
                height: 110px; width: 28px;
                margin: 0 4px;
                background-image: url('@/assets/book-blue.png');
                background-size: cover;
                writing-mode: vertical-rl;
                text-orientation: sideways-right;
                font-size: small;
                justify-content: center;
                align-items: center;
                display: flex;
                &:hover {
                    transform: scale(1.05);
                }
                a {
                    padding: 4px;
                    width: 100%; height: 100% ;
                    font-weight: bold;
                    color: white; //#2c3e50;
                    text-decoration: none;
                    text-shadow: 0 0 1px black;

                }

                a.router-link-exact-active {
                    color: #42b983;
                }
            }
            .book-red {
                background-image: url('@/assets/book-red.png');
                background-size: 100% 100%;
            }
            .book-blue {
                background-image: url('@/assets/book-blue.png');
                background-size: 100% 100%;
            }
            .book-green {
                background-image: url('@/assets/book-green.png');
                background-size: 100% 100%;
            }
            .book-orange {
                background-image: url('@/assets/book-orange.png');
                background-size: 100% 100%;
            }
            &:has(li:hover) {
                li {
                    &::after {
                        height: 110px; width: 28px;
                        background-color: rgba(0, 0, 0, 0.5);
                    }
                }
            }
        }
    }
    .shelf {
        width: 500px;
        height: 75px;
        margin: auto;
        background-size: cover;
        // border: 1px solid black;
        position: relative;
        bottom: 16px;
        z-index: 10;
    }

    #back-btn {
		position: absolute;
		top: 5px; left: 5px;
	}
</style>