<template>
    <div id="projects">
        <div class="laptop-screen">
            <div class="laptop-desktop">

            </div>
        </div>
    </div>
</template>
<script>
export default {
    
}
</script>
<style lang="scss">
    #projects {
        widows: 100vw; height: 100vh;
        margin: 0;
        box-sizing: border-box;
        overflow: hidden;

        --s: 150px; --c1: rgb(188, 140, 76); --c2: rgb(145, 98, 34); --c: var(--c1) 0 25%,var(--c2) 0 50%,#0000 0;
        background:
            // linear-gradient(to top, wheat 0px, rgb(201, 182, 146)  2px 2px, wheat 4px, rgba(0, 0, 0, 0.8) 4px 5px, transparent 4px 100%),
            linear-gradient(to top, 
                transparent 0%, 
                transparent calc(50% - 20px), 
                rgb(201, 182, 146) calc(50% - 20px) calc(50% - 10px), 
                wheat calc(50% - 10px) calc(50% + 10px), 
                rgba(0, 0, 0, 0.8) calc(50% + 10px) calc(50% + 20px), 
                transparent calc(50% + 20px) 100%
            ),

            linear-gradient(to bottom, transparent 50%, white 50%),
            conic-gradient(from 0deg, rgba(188, 140, 76, 0.5) 0 25%, rgba(145, 98, 34, 0.5) 25% 50%, transparent 50% 75%, transparent 75% 100%)
            0/var(--s) var(--s),
            conic-gradient(from 45deg, rgba(188, 140, 76, 0.42) 0 50%, rgba(145, 98, 34, 0.42) 50% 50%, transparent 50% 75%, transparent 75% 100%)
            0/calc(3*var(--s)) calc(3*var(--s)),
            conic-gradient(from 180deg,var(--c)) 
            0/var(--s) var(--s),
            repeating-conic-gradient(from 90deg,var(--c))
            0/calc(3*var(--s)) calc(3*var(--s))
        ;
        
        perspective: 1000px;

        .laptop-screen {
            transform: rotateX(1deg);
            transform-origin: bottom;
            box-sizing: border-box;
            width: 99.5%; height: 100%;
            margin: 0.25% auto;
            --frameColor: #282828;
            border: 32px solid var(--frameColor);
            border-top: 40px solid var(--frameColor);
            border-radius: 32px 32px 0 0;

            .laptop-desktop {
                width: 100%; height: 100%;
                background-image: url(https://img.freepik.com/free-photo/jungle-landscape-pixel-art-style_23-2151557050.jpg);
                background-size: 100% 100%;
                
                cursor: url(../assets/cursor_pointer.png), pointer;
                &:active {
                    cursor: url(../assets/cursor_pointer_click.png), pointer;
                }
            }
        }
    }
</style>