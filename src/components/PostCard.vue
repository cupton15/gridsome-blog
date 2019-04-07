<template>
  <button
    class="post-card"
    :class="{ expanded: expanded }"
    @click="onClick"
  >
    <div class="post-card-content-box">
      <h2 v-html="post.title" />
      <p
        v-if="!expanded"
        class="post-card-description"
        v-html="post.description"
      />
      <div
        v-if="expanded"
        class="post-card-content" 
        v-html="post.content"
      />
    </div>
  </button>
</template>

<script>
import smoothReflow from 'vue-smooth-reflow';

export default {
    mixins: [smoothReflow],
    props: {
        post: {
            required: true,
            type: Object,
            validator: function(obj){
                return ( 
                    obj.title && obj.title.length 
                    && obj.description && obj.description.length
                    && obj.content && obj.content.length
                );
            }
        }
    },
    data() {
        return {
            expanded: false
        }
    },
    mounted() {
        this.$smoothReflow({
            property: ['height', 'width'],
             transition: 'height .25s ease-in-out, width .25s ease-out'
        })
    },
    methods: {
        onClick() {
            this.expanded = !this.expanded
        }
    }
}
</script>

<style>
    .post-card {
        position: relative;
        display: block;
        margin: 0 auto;
        background-color: var(--content-bg-color);
        max-width: var(--content-size);    
    }

    .post-card.expanded {
        max-width: 100%;
    }
</style>
