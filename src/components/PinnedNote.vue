<template>
    <div class="pinnedNote">
        <div class="pin"></div>
        <div class="note">
            <div class="content">
                <slot></slot>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    // mounted() {
    //     const pins = document.querySelectorAll("div.pin");

    //     pins.forEach(pin => {
    //         pin.addEventListener('keydown', () => {
    //             // e.preventDefault()
    //             console.log('eee')
    //         })
    //     })

    // },
}
</script>
<style lang="scss">
    .pinnedNote {
        $pinSize: 20px;
        display: flex; flex-direction: column;
        width: 200px; height: 250px;
        position: relative;
        perspective: 1500px;
        .pin {
            $pinColor: crimson;
            z-index: 2;
            margin: auto;
            width: $pinSize; height: $pinSize; 
            border: 1px solid black; border-radius: $pinSize;
            background-color: $pinColor;
            background-image: 
                linear-gradient(-225deg, transparent 0% 10%, $pinColor 35% 50%, transparent 70%),
                radial-gradient($pinColor 0% 50%, rgba(255, 255, 255, 0.999), $pinColor 65% 100%)
            ;
            position: relative; top: calc(0.7 * $pinSize); //left: calc(50% - (0.5 * $pinSize));
            box-shadow: 2 2 18px 10px black;

        }
        .note {
            width: 100%; height: 100%;
            background-color: #fff;
            border: 1px solid black;
            padding: 6px;
            z-index: 1;
            box-shadow: 0 0 6px 0px black;
            overflow: hidden;
            animation-name: flutter;
            animation-duration: 3.5s;
            animation-delay: 0.4s;
            animation-iteration-count: infinite;
            animation-direction: alternate;
            animation-timing-function: ease-in-out;
            .content:has(img) {
                width: 100%;
                height: 100%;
                overflow: hidden;
                display: flex; flex-direction: column;
                img {
                    width: 100%; 
                    height: 80%;
                    object-fit: contain scale-down;
                    object-position: top center;
                    
                }

            }
        }
    }

    @keyframes flutter {
        $size: 15deg;
        0% {
            transform: rotateX(-$size);
            transform-origin: top;
        }
        100% {
            transform: rotateX($size);
            transform-origin: top;
        }
    }
</style>