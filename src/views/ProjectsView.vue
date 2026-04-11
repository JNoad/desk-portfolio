<template>
    <div id="projects">
        <div class="laptop-screen">
            <div class="laptop-desktop" @mousemove="dragWindow">
                <ProjectWindow ref="projectWindow"/>
            </div>
            <TaskbarNav/>
            <div class="camera"></div>
        </div>
    </div>
</template>
<script>
    import ProjectWindow from '@/components/ProjectWindow.vue';
    import TaskbarNav from '@/components/TaskbarNav.vue';
    export default {
        components: {
            TaskbarNav,
            ProjectWindow
        },
        methods: {
            dragWindow(e) {
                e.preventDefault();
                if (this.$refs.projectWindow) {
                    this.$refs.projectWindow.drag(e);
                }
            }
        },
        mounted() {
            console.clear()
        }
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
            transform: rotateX(2deg); transform-origin: bottom;
            width: 99.5%; height: 100%;
            margin: 0.25% auto;

            --frameColor: #282828;
            background-color: var(--frameColor);
            border: 32px solid var(--frameColor);
            border-top: 40px solid var(--frameColor);
            border-radius: 32px 32px 0 0;

            display: flex; flex-direction: column;
            
            animation: creakScreen 8s ease-in-out 1.5s infinite alternate;
            
            .laptop-desktop {
                width: 100%; height: 100%;
                background-image: url(https://img.freepik.com/free-photo/jungle-landscape-pixel-art-style_23-2151557050.jpg);
                background-size: 100% 100%;
                border-radius: 12px 12px 0 0;
                overflow: hidden;
                box-shadow: 
                inset 0 3px 6px -2px black, 
                inset 6px 0px 6px -6px rgba(0, 0, 0, 0.8), 
                inset -6px 0px 6px -6px rgba(0, 0, 0, 0.8)
            ;
            position: relative;
            &::after {
                content: "";
                position: absolute;
                inset: 0;
                /* Use 'soft-light' or 'overlay' to affect the content visually */
                background: linear-gradient(180deg, transparent 60%, rgba(255,255,255,0.5) 70%, transparent 80%); // glare
                mix-blend-mode: overlay; 
                pointer-events: none;
                animation: creakScreenGlare 8s ease-in-out 1.5s infinite alternate;
            }             
            }

            & * {
                cursor: url(../assets/cursor_pointer.png), pointer;
                &:active {
                    cursor: url(../assets/cursor_pointer_click.png), pointer;
                }
            }

            .camera {
                width: 30px; height: 30px;
                border-radius: 50%;
                background: 
                    /* 1. Small white reflection (glare) */
                    radial-gradient(circle at 30% 30%, rgba(255, 255, 255, 0.4) 0%, transparent 15%),
                    /* 2. Dark blue sensor glow */
                    radial-gradient(circle at center, #1a2a44 0%, transparent 45%),
                    /* 3. Outer lens depth (slight metallic/dark grey ring) */
                    radial-gradient(circle at center, #050505 30%, #111 60%, #333 100%);
                box-shadow: inset 0 0 10px rgba(0, 0, 0, 1), 0 0 1px 1px rgba(255, 255, 255, 0.2);
                position: absolute;
                top: -35px; left: calc(50% - 15px);
            }
        }
    }

    @keyframes creakScreen {
        $size: 0.65deg;
        $default: 2deg;
        0% {
            transform: rotateX($default - $size);
        }
        80% {
            transform: rotateX($default + $size);
        }
        100% {
            transform: rotateX($default + $size);
        }
    }
    @keyframes creakScreenGlare {
        $size: 8%;
        0% {
            transform: translateY(-$size);
        }
        80% {
            transform: rotateX(0%);
        }
        100% {
            transform: rotateX($size);
        }
    }
</style>