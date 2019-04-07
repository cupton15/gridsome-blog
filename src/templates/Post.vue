<template>
  <Layout>
    <h1> {{ $page.post.title }} </h1>
    <div v-html="$page.post.content" />
  </Layout>
</template>

<script>
export default {

}
</script>

<page-query>
    query Post ($path: String!) {
        post: post (path: $path) {
            title,
            content
        }
    }
</page-query>

<style>

</style>
