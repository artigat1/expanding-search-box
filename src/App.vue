<template>
    <app-expanding-search-box />
</template>

<script>
    import ExpandingSearchBox from '@/components/expanding-search-box.vue'

    export default {
        name: 'App',
        components: {
            appExpandingSearchBox: ExpandingSearchBox,
        }
    }
</script>

<style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: left;
    color: #2c3e50;
    margin: 10px;
  }
</style>
