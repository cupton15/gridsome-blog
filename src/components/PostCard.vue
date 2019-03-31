<template>
    <div class="post-card">
        <div class="post-card-content">
            <p class="post-card-description" v-html="post.description"/>
        </div>
    </div>
</template>

<script>
export default {
    props: ['post']
}
</script>

<style>
    .post-card {
        position: relative;
        background-color: var(--content-bg-color);
        max-width: var(--content-size);
    }
</style>
