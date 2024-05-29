<template>
    <div class="book">
        <button @click="pageBackward()">
            <img width="48" height="48" src="https://img.icons8.com/fluency-systems-filled/48/000000/circled-left-2--v2.png" alt="circled-left-2--v2"/>
        </button>
        <div class="book-cover">
            <div class="book-interior" :class="{pagingBackward: 'paging-backward'}, {pagingForeward: 'paging-foreward'}">
                <div class="book-page book-left-page">
                    <h2>About Me</h2>
                    <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Ducimus voluptate deleniti asperiores, beatae rerum aspernatur dolorem odio assumenda inventore aut praesentium, provident hic necessitatibus dolorum placeat magnam iure vel impedit, nemo ipsum. Minus asperiores odio nulla aut dolor praesentium iure. Numquam atque accusantium nam, corrupti consequatur vitae rerum repellendus voluptatibus?</p>
                </div>
                <div class="book-page book-right-page">
    
                </div>
            </div>
        </div>
        <button @click="pageForeward()">
            <img width="48" height="48" src="https://img.icons8.com/fluency-systems-filled/48/000000/circled-right-2--v2.png" alt="circled-left-2--v2"/>
        </button>
    </div>
</template>
<script>

export default {
    data() {
        return {
            pagingBackward: false,
            pagingForeward: false,      
        }
    },
    methods: {
        pageBackward() {
            
            this.pagingBackward = true
            setTimeout(() => {
                this.pagingBackward = false
            }, 1000)
        },
        pageForeward() {
            let page = document.querySelector('.book-right-page');

            page.classList += ' flip'
            this.pagingForeward = true
            setTimeout(() => {
                this.pagingForeward = false
            }, 1000)
        },
    },
}
</script>
<style lang="scss">
    .book {
        display: flex;
        button img {
            opacity: 0.6;
        }
    }
    .book-cover {
        border-radius: 8px;
        width: 1100px; height: 650px;
        background-color: #7C2F02;
        margin: auto; padding: 8px 12px;
        
    }

    .book-interior {
        width: 100%; height: 100%;
        // background-color: #fff;
        border-radius: inherit;
        display: flex;
        // overflow: hidden;
        box-shadow: 0 0 6px -3px black;
        perspective: 2000px;

    }

    .book-page {
        width: 50%; height: 100%;
        padding: 16px 32px;
        background-color: #fff;
        border-radius: 8px 0 0 0 8px;
        &:nth-child(1) {
            box-shadow: inset -8px 0 48px -12px black;

        }
        &:nth-child(2) {
            box-shadow: inset 8px 0 48px -12px black;
            // animation: pageBackward 1s;
        }
    }

    p {
        text-align: left;
    }

    .flip {
        transform: rotateY(-180deg);
        transform-origin: left;
        transition: transform 1s;
        perspective: 1500px;
    }

    // Animations
    @keyframes pageBackward {
        from {width: 100%;}
        to {width: 0%;}
    }
    @keyframes pageForward {
        
    }
</style>