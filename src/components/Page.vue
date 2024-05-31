<template>
    <div class="book-page unflipped">
        <div class="book-page-front">
            <h1>Front</h1>
            <h3>{{ msg }}</h3>
        </div>
        <div class="book-page-back">
            <h1>Back</h1>
            <h3>{{ msg }}</h3>
        </div>
    </div>

</template>
<script>
export default {
    props: ['msg'],
}
</script>
<style lang="scss">
    .book-page {
        width: 50%; height: 100%;
        position: relative;
        transform-origin: left;
        transition: all 1s;
        perspective: 1500px;
        backface-visibility: hidden;
        border-radius: 0 8px 8px 0;
        background-color: #fff;

        z-index: var(--zIndex);
        // overflow: hidden;
        .book-page-front, .book-page-back {
            width: 100%; height: 100%;
            padding: 16px 32px;
            background-color: #fff;
            border-radius: 8px 0 0 0 8px;
            position: absolute;
            top: 0; right: 0;
        }
        .book-page-front {
            box-shadow: inset 8px 0 48px -12px black;
            z-index: 2;
            border-radius: inherit;

        }
        .book-page-back {
            box-shadow: inset -8px 0 48px -12px black;
            z-index: 0;
            transform: rotateY(180deg);
            border-radius: 8px 0  0 8px;

        }
    }
    .flipped {
        transform: rotateY(-180deg);
    }
</style>