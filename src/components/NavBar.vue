<template>
    <nav v-if="showBookShelf">
        
        <div class="desk-nav">
            <div class="on-desk">
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
                <Laptop/>
            </div>
            <div class="desk">
                <!-- <router-link class="book" to="about">
                    About Me
                </router-link> -->
                <div class="top"></div>
                <div class="side"></div>
            </div>
        </div>
    </nav>
    <router-link to="/" id="back-btn" v-else>
		<img width="48" height="48" src="https://img.icons8.com/fluency-systems-filled/48/000000/circled-left-2--v2.png" alt="circled-left-2--v2"/>
	</router-link>
</template>

<script>
import Laptop from '@/components/Laptop.vue';
export default {
    components: {
        Laptop
    },
    computed: {
        showBookShelf() {
            return this.$route.path == '/';
        }
    }
}
</script>
<style lang="scss">
    nav {
        padding: 0; margin: 0;
        position: absolute; bottom: 0; left: 0;
        width: 100%; height: 220px;
        display: flex; flex-direction: column;
        justify-content: center; align-items: center;
        align-content: end;
        
        // --base-hue: 0; // Starting color (Red)
        // border: 4px solid hsl(var(--base-hue), 70%, 50%);
        // padding: 20px;

        // // Initial selector targets the first child
        // $selector: "*";

        // @for $i from 1 through 10 {
        //     #{$selector} {
        //     // Calculate a new hue for this specific depth level
        //     $new-hue: $i * 100; 
        //     border: 2px solid hsl($new-hue, 70%, 50%);
        //     padding: 2px;
        //     }
        //     // Appends another "*" to the selector for the next loop (e.g., "* *" -> "* * *")
        //     $selector: "#{$selector} *";
        // }
        .desk-nav {
            width: 100%;
            height: 100%;
            position: relative;
            top: 0;
            left: 0;
            perspective: 1000px;

            .on-desk {
                display: flex;
                justify-content: center;
                align-items: center;
                width: calc(80% + 80px); height: calc(100% - 12px);
                margin: 0 auto;
                ul {
                    display: flex;
                    z-index: 11;
                    justify-content: center;
                    align-items: center;
                    list-style-type: none;
                    margin: 0;
                    position: relative;
                    perspective: 2000px;
                    height: 100%;
                    margin-bottom: 32px;
                    li {
                        height: 110px; width: 28px;
                        margin: 0 1px;
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
            // .book {
            //     position: absolute;
            //     bottom: -80px; left: 150px;
            //     background-color: crimson;
            //     width: 60px;
            //     height: 90px;
            //     z-index: 11;
            // }
            .desk {
                position: absolute;
                bottom: 0;
                left: 50%;
                transform: translateX(-50%); // perfect centering
                z-index: 10;

                width: calc(80% + 80px);
                height: 200px;

                perspective: 1000px;
                transform-style: preserve-3d;

                .top {
                    position: absolute;
                    bottom: 12px; // anchor to bottom so rotation pivots correctly
                    left: 0;

                    width: 100%;
                    height: 300px;

                    transform-origin: bottom center;
                    transform: rotateX(75deg); // 88deg is too extreme (almost flat)

                    background-image: linear-gradient(
                        -170deg,
                        darken(burlywood, 40%),
                        darken(burlywood, 25%),
                        burlywood
                    );

                    border: 1px solid black;
                    border-top: 6px solid black;
                }

                .side {
                    position: absolute;
                    bottom: 0;
                    left: 0;

                    width: 100%;
                    height: 12px;

                    background-color: burlywood;
                    border: 1px solid black;

                    transform: translateZ(0); // ensures it sits at the front edge
                }
            }
        }
    }

    #back-btn {
		position: absolute;
		top: 5px; left: 5px;
	}
</style>