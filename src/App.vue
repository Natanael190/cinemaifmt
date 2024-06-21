<template>
  <Header />
  <CatalogContainer />
</template>

<script>
  import Header from "./components/header/Header.vue";
  import CatalogContainer from "./containers/CatalogContainer.vue";

  export default {
    name: "App",
    components: {
      Header,
      CatalogContainer,
    },
  };
</script>