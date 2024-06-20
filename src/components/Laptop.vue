<template>

    <div class="laptop">
        <div class="laptop-top">
            <div class="laptop-screen">
                <div class="screen-content">

                </div>
            </div>
        </div>
        <div class="laptop-bottom"></div>
    </div>
</template>
<script>
export default {
    
}
</script>
<style lang="scss">
    .laptop {
        perspective: 1500px;
        display: flex; flex-direction: column;
        align-items: center;
        $transitionSpeed: 0.7s;
        .laptop-top {
            width: 300px; height: 200px;
            padding: 8px 4px;
            background-color: #111; border-radius: 8px 8px 0 0;
            transform-origin: bottom; transform: rotateX(-60deg);
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
            width: calc(100% * 1.2); height: 8px;
            background-color: #111; border: 1px solid black;
            border-radius: 2px 2px 4px 4px;
        }
    }
</style>