<template>
    <button class="post-card" @click="onClick" v-bind:class="{ expanded: expanded }">
        <div class="post-card-content-box">
            <h2 v-html="post.title"></h2>
            <p v-if="!expanded" class="post-card-description" v-html="post.description"/>
            <div v-if="expanded" v-html="post.content" class="post-card-content"></div>
        </div>
    </button>
</template>

<script>
export default {
    data() {
        return {
            expanded: false
        }
    },
    methods: {
        onClick() {
            this.expanded = !this.expanded
        }
    },
    props: ['post']
}
</script>

<style>
    .post-card {
        position: relative;
        background-color: var(--content-bg-color);
        max-width: var(--content-size);
        margin: 0 auto;
    }

    .post-card.expanded {
        max-width: 100%;
    }
</style>
