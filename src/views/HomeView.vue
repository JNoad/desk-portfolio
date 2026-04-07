<template>
    
    <div class="home">
        <div class="cork">
            <PinnedNote>
                <img src="@/assets/people/john-bruce_noad_portfolio_photo.png" alt="John-Bruce Noad portfolio photo">
                <h3 style="margin: 10px;">John-Bruce Noad</h3>
            </PinnedNote>
        </div>
    </div>
</template>

<script>
// @ is an alias to /src
import PinnedNote from '@/components/PinnedNote.vue';
export default {
    name: 'HomeView',
    components: {
          PinnedNote
    }
}
</script>

<style lang="scss">
    .home {
        margin: auto; padding-top: 50px;
        width: 80%;
        height: 100vh;
        overflow: hidden;
    }
    .cork {
        border: 1px solid rgba(0, 0, 0, 0.8);
        width: 100%;  height: 500px;
        padding: 8px;

        --s: 15px; --c1: rgb(188, 140, 76); --c2: rgb(145, 98, 34); --c: var(--c1) 0 25%,var(--c2) 0 50%,#0000 0;

        background:
            linear-gradient(to right, wheat 0px, rgb(201, 182, 146)  2px 2px, wheat 4px, rgba(0, 0, 0, 0.8) 4px 5px, transparent 4px 100%),
            linear-gradient(to left, wheat 0px, rgb(201, 182, 146)  2px 2px, wheat 4px, rgba(0, 0, 0, 0.8) 4px 5px, transparent 4px 100%),
            linear-gradient(to top, wheat 0px, rgb(201, 182, 146)  2px 2px, wheat 4px, rgba(0, 0, 0, 0.8) 4px 5px, transparent 4px 100%),
            linear-gradient(to bottom, wheat 0px, rgb(201, 182, 146)  2px 2px, wheat 4px, rgba(0, 0, 0, 0.8) 4px 5px, transparent 4px 100%),

            conic-gradient(from 0deg, rgba(188, 140, 76, 0.5) 0 25%, rgba(145, 98, 34, 0.5) 25% 50%, transparent 50% 75%, transparent 75% 100%)
            0/var(--s) var(--s),
            conic-gradient(from 45deg, rgba(188, 140, 76, 0.42) 0 50%, rgba(145, 98, 34, 0.42) 50% 50%, transparent 50% 75%, transparent 75% 100%)
            0/calc(3*var(--s)) calc(3*var(--s)),
            conic-gradient(from 180deg,var(--c)) 
            0/var(--s) var(--s),
            repeating-conic-gradient(from 90deg,var(--c))
            0/calc(3*var(--s)) calc(3*var(--s))
        ;
    }
</style>
