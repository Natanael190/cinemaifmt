<template>
  <div class="link">
    <a :class="{ 'active' : link.id === active }" href="#" @click.prevent="handleLinkClick">{{ link.title }}</a>
  </div>
</template>

<script>  
  export default {
    name: "Link",
    props: {
      link: Object,
      active: Number,
    },
    methods: {
      handleLinkClick() {
        this.$emit('linkClicked', this.link);
      }
    }
  };
</script>
