<template>
    <div class="book">
        <button @click="pageBackward()">
            <img width="48" height="48" src="https://img.icons8.com/fluency-systems-filled/48/000000/circled-left-2--v2.png" alt="circled-left-2--v2"/>
        </button>
        <div class="book-cover">
            <div class="book-interior">
                <Page v-for="(page, index) in pages" :key="index" :msg="'Page ' + (index + 1)" >
                    <!-- <slot :name="`page-${index}-front`"></slot> -->
                    <template v-slot:page-front>
                        <div v-html="page.content.front"></div>
                    </template>
                    <template v-slot:page-back>
                        <div v-html="page.content.back"></div>
                    </template>
                </Page>

            </div>
        </div>
        <button @click="pageForeward()">
            <img width="48" height="48" src="https://img.icons8.com/fluency-systems-filled/48/000000/circled-right-2--v2.png" alt="circled-left-2--v2"/>
        </button>
    </div>
</template>

<script>
import Page from '@/components/Page.vue';
import { renderToString } from 'vue/server-renderer';

export default {
    components: {
        Page
    },
    // props: ['pages'],
    data() {
        return {
            slotContent: '',
            contentLeft: '',
            contentRight: '',
            pages: [],
        }
    },
    methods: {
        pageBackward() {
            let pages = document.querySelectorAll('.book-page.flipped');
            let page = pages[pages.length - 1];

            if(page){
                page.classList.remove('flipped');
                page.classList.add('unflipped');
                this.setPageShadow()
                this.setPageZindex()
            }
        },
        pageForeward() {
            let page = document.querySelectorAll('.book-page.unflipped')[0];
            if(page){
                page.classList.add('flipped');
                page.classList.remove('unflipped');
                this.setPageShadow()
                setTimeout(()=> {
                    this.setPageZindex()
                }, 500)
            }
        },
        setPageShadow() {
            let pages = document.querySelectorAll('.book-page');
            let flipped = document.querySelectorAll('.book-page.flipped');
            let unFlipped = document.querySelectorAll('.book-page.unflipped');

            pages.forEach(page => {
                page.classList.remove('backshadow-page')
                page.classList.remove('frontshadow-page')
            })
            if (flipped.length) {
                flipped[flipped.length -1].classList.add('backshadow-page');
            }

            if (unFlipped.length) {
                unFlipped[0].classList.add('frontshadow-page');
            }
        },
        setPageZindex() {
            this.pages.forEach((pageData, index) => {
                let page = document.querySelectorAll('.book-page')[index];
                if (page.classList.contains('flipped')) {
                    page.style.zIndex = ''
                } else {
                    page.style.zIndex = this.pages.length - index
                }
            });
        },
        async renderSlotContent() {
            const vnodes = this.$slots.default ? this.$slots.default() : [];
            let content = '';

            for (let i = 0; i < vnodes.length; i++) {
                let string = await renderToString(vnodes[i]);
                let gap = i == 0 ? '' : '\n';
                content = content + gap + string;
            }

        let splitContent = content.split(/<page>*<\/page>/);
            splitContent.forEach((subContent, index) => {
                subContent = subContent.replaceAll(/<\/?page>/g, '')
                if (subContent) {
                    let splitSubContent = subContent.match(/<page-front>.*?<\/page-front>|<page-back>.*?<\/page-back>/g)
                    splitSubContent = splitSubContent.map(match => 
                        match.replace(/<\/?page-front>|<\/?page-back>/g, '')
                    );

                    this.pages.push({
                        index,
                        content: {
                            front: splitSubContent[0],
                            back: splitSubContent[1]
                        }
                    })      
                }
            })

            this.slotContent = content;
        },
    },
    async mounted() {
        this.setPageZindex()
        this.setPageShadow()
        this.renderSlotContent()
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
        border-radius: inherit;
        display: flex;
        justify-content: end;
        perspective: 2000px;
        > * {
            position: absolute;
            top: 0;
            right: 0;
        }

    }

    p {
        text-align: left;
    }

</style>