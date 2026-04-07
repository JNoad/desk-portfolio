<template>

    <div class="laptop">
        <div class="laptop-top">
            <div class="laptop-screen">
                <div class="screen-content" @click="$router.push('/projects')">

                </div>
            </div>
        </div>
        <div class="laptop-bottom">
            <div class="keyboard"></div>
            <div class="side"></div>
        </div>
    </div>
</template>
<script>
export default {
    
}
</script>
<style lang="scss">
    .laptop {
        perspective: 1000px;
        // display: flex; flex-direction: column;
        align-items: center;
        $transitionSpeed: 0.7s;
        width: 22em;
        height: 110%;
        //overflow: hidden;
        bottom: 25%;
        z-index: 11;
        .laptop-top {
            flex-grow: 0;
            width: 70%; height: 60%;
            padding: 8px 4px; margin: 0 auto; margin-top: 16px;
            background-color: #111; border-radius: 8px 8px 0 0;
            transform-origin: bottom ; transform: rotateX(-60deg);
            transition: all $transitionSpeed;
            cursor: pointer;
            .laptop-screen {
                width: 100%; height: 100%;
                background: #222; border-radius: 8px 8px 0 0;
                background-image: none;
                .screen-content {
                    width: 100%; height: 100%;
                    background-image: url(https://upload.wikimedia.org/wikipedia/commons/0/02/Television_static.gif);
                    opacity: 0; transition: all $transitionSpeed;
                }
            }
            &:hover {
                transform: rotateX(30deg);
                .screen-content {
                    opacity: 0.8;
                }
            }
        }
        .laptop-bottom {
            width: 70%; height: 70%;
            margin: 0 auto;
            align-content: center;
            perspective: 1000px;
            transform-origin: top;
            transform: rotateX(80deg);
            .keyboard {
                width: 100%;
                height: 100%;
                background-color: #111; border: 1px solid black;
            }
            .side {
                width: 100%; height: 30px;
                background-color: #111; border: 1px solid black;
                border-radius: 20% 20% 40% 40%;
                transform-origin: top;
                transform: rotateX(-10deg);
                position: relative;
                top: -6px;
            }
        }
    }
</style>