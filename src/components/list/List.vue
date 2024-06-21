<template>
  <div v-if="items && items.length > 0" class="list">
    <template v-for="(movie, index) in items" :key="index">
      <Link :link="movie" :active="active" @link-clicked="$emit('movieSelection', movie)" />
    </template>  
  </div>
</template>

<script>
  import './list.scss';
  import Link from '../link/Link.vue';
  export default {
    name: "List",
    props: {
      items: Array,
      active: Number,
    },
    components: {
      Link,
    }
  };
</script>
