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
    
}
</script>
<style lang="scss">
    .pinnedNote {
        $pinSize: 20px;
        display: flex; flex-direction: column;
        width: 200px; height: 250px;
        position: relative;
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
        }
        .note {
            width: 100%; height: 100%;
            background-color: #fff;
            border: 1px solid black;
            padding: 6px;
            z-index: 1;
            overflow: hidden;
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
</style>