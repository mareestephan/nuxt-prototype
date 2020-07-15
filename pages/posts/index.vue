<template>
    <div>
        <h1>Posts page INDEX</h1>

        <li v-for="post in posts" :key="post.id" > 
<nuxt-link :to="`/posts/${post.slug}`"> {{post.meta_title}} </nuxt-link>
        </li>

    </div>
</template>

<script>
export default {
  asyncData({ $axios }) {
    return (
      $axios
        // .get("http://35.190.35.153/system-api/pages-to-create/all-sale")
        .get("http://35.190.35.153/system-api/pages-to-create/all-sale")
        // .get(
        //   "https://my-json-server.typicode.com/mareestephan/jsonProducts/pages_to_create"
        // )
        .then(response => {
          // console.log(response.data);
          return { posts: response.data.pages_to_create };
        })
    );
  },
  data() {}
};
</script>

<style>
</style>
