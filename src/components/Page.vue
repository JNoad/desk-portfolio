<template>
    <div class="book-page unflipped">
        <div class="book-page-front">
            <slot name="page-front">
                <h1>Front</h1>
                <h3>{{ msg }}</h3>
            </slot>
        </div>
        <div class="book-page-back">
            <slot name="page-back">
                <h1>Back</h1>
                <h3>{{ msg }}</h3>
            </slot>
        </div>
    </div>

</template>
<script>
export default {
    props: ['msg'],
}
</script>
<style lang="scss">
    $page-shadow: 0 0 8px -2px black;
    $inset-front-shadow: inset 8px 0 48px -12px black;
    $inset-back-shadow: inset -8px 0 48px -12px black;

    .book-page {
        width: 50%; height: 100%;
        position: relative;
        transform-origin: left;
        transition: all 1s;
        perspective: 1500px;
        backface-visibility: hidden;
        border-radius: 0 8px 8px 0;
        // background-color: #fff;

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
            box-shadow: $inset-front-shadow;
            z-index: 2;
            border-radius: inherit;

        }
        .book-page-back {
            box-shadow: $inset-back-shadow;
            z-index: 0;
            transform: rotateY(180deg);
            border-radius: 8px 0  0 8px;

        }
        &.flipped {
            transform: rotateY(-180deg) !important;
        }
        &.backshadow-page .book-page-back {
            box-shadow: $inset-back-shadow, $page-shadow !important;
        }
        &.frontshadow-page .book-page-front {
            box-shadow: $inset-front-shadow, $page-shadow !important;
        }
    }
</style>