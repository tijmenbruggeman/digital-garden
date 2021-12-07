<template>
    <main>
        <h1>{{note.title}}</h1>
        <nuxt-link to="/notes">All notes</nuxt-link>
        <nuxt-content :document="note" />
    </main>
</template>

<script lang="ts">
    import Vue from 'vue'

    export default Vue.extend({
        // context is the Vue Instance
        async asyncData({ $content, route }) {
            const note = await $content(`notes/${route.params.slug}`).fetch<any>();
            return {
                note,
            }
        },
        methods: {
            goBack() {
                this.$router.go(-1);
            },
        }
    });
</script>

<style scoped>

</style>