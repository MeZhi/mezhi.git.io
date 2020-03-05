<template>
  <div id="app">
    <show-blogs></show-blogs>
    <!-- <add-blog></add-blog> -->
  </div>
</template>

<script>
import AddBlog from './components/AddBlog'
import ShowBlogs from './components/ShowBlogs.vue'

export default {
  name: "app",
  components: {
    AddBlog,ShowBlogs
  }
};
</script>

<style>

</style>
