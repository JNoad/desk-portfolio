<template>
    <div class="project-window" 
        @mousedown="$event.preventDefault(); beginDrag($event)" 
        @mouseup="dragging = false" 
        :style="{left: x + 'px', top: y + 'px', width, height}"
    >
        <div class="title-bar">
            <span>
                {{ title }}
            </span>

            <div class="buttons" > 
                <button @click="width = '800px'; height = '500px'; x = 250; y = 80;">-</button>
                <button @click="width = '100%'; height = '100%'; x = 0; y = 0;">□</button>
                <button>x</button>
            </div>
        </div>
        <div class="content">
            <iframe :src="url" frameborder="0"></iframe>
        </div>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                dragging: false,
                x: 250,
                y: 80,
                width: '850px',
                height: '450px',
                offsetX: 0,
                offsetY: 0,
                title: "JS Calculator",
                url: 'https://john-bruce-js-calculator.netlify.app/',
            }
        },
        methods: {
            beginDrag(e) {
                this.dragging = true;
                this.offsetX = e.offsetX
                this.offsetY = e.offsetY
            },
            drag(e) {                
                let windowRect = e.target.getBoundingClientRect();
                let parentElRect = e.target.parentElement.getBoundingClientRect();
                
                let xShift = e.offsetX - this.offsetX;
                let yShift = e.offsetY - this.offsetY;
                if (
                    this.dragging 
                    && this.x + windowRect.x + xShift > parentElRect.left
                    && this.x + windowRect.width + xShift < parentElRect.right
                ) {                 
                    this.x += xShift;
                    this.y += yShift;  
                }
            },
        },
    }
</script>

<style lang="scss" scoped>
    .project-window {
        width: 850px;
        height: 550px;
        background-color: #333;

        box-shadow: 0 0 6px -2px black;

        border-radius: 8px;
        overflow: hidden;

        position: relative;
        top: 20%; left: 20%;

        display: flex; flex-direction: column;

        .title-bar {
            width: 100%;
            height: 24px;
            background-color: crimson;
            
            display: flex;
            justify-content: space-between;
            
            span {
                text-align: start;
                padding-top: 2px;
                padding-left: 12px;
                color: #fff;

            }

            .buttons {
                
                button {
                    background-color: transparent;
                    padding: 3px 8px;
                    border: 2px solid #fff;
                    color: #fff;
                    &:hover {
                        background-color: red;
                    }
                    &:active {
                        background-color: darken(crimson, 20%);
                        scale: 0.95;
                    }
                }
            }
        }
        .content {
            width: 100%; flex-grow: 1;
            overflow: hidden;
            iframe {
                width: 140%; height: 140%;
                transform: scale(0.75);
                transform-origin: 0 0;
            }
        }
    }
</style>