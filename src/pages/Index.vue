<template>
  <Layout>
    <PostCard v-for="edge in $page.posts.edges" :key="edge.node.id" :post="edge.node"/>
  </Layout>
</template>

<page-query>
{
  posts: allPost {
    edges {
      node {
        id,
        description,
        title,
        content
      }
    }
  }
}
</page-query>

<script>
import PostCard from '../components/PostCard';

export default {
  components: {
    PostCard
  },
  metaInfo: {
    title: 'My gridsome blog!'
  }
}
</script>

<style>

</style>
