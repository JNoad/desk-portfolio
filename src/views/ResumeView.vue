<template>
    <div>
        <Book>
            <page>
                <page-front>
                    <h1>Resume</h1>
                    <h3>By Jon-Bruce Noad</h3>
                </page-front>
                <page-back>
                    <h2>Education</h2>
                    <table>
                        <thead>
                            <th></th>
                            <th></th>
                            <th></th>
                            <th></th>
                        </thead>
                    </table>
                </page-back>
            </page>
            <page>
                <page-front>
                    <h2>Skills</h2>
                </page-front>
                <page-back>
                    <h2>CV</h2>
                </page-back>
            </page>
        </Book>
    </div>
</template>
<script>
import Book from '@/components/Book.vue';
export default {
    components: {
        Book
    }
}
</script>
<style lang="scss">
    
</style>