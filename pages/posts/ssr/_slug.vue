<template>
    
<div>

  
    <h1>this is blog number {{$route.params.slug}}</h1>
    <!-- <h1>{{post[0].meta_title}}</h1>
    <a :href="`${post[0].link}`" :key='post[0].meta_title'>{{post[0].link}}</a>
    <pre>{{post}}</pre> -->

 <li v-for="post in posts" :key="post.product_id" > 
<a :href="`${post.product_link}`"> {{post.product_link}} </a>
        </li>

</div>

</template>

<script>
export default {
  asyncData({ $axios, route }) {
    // console.log(route.params.category_id);
    return $axios
      .get(
        `http://35.190.35.153/system-api/pages-to-create/all-sale?slug=${
          route.params.slug
        }`
      )
      .then(response => {
        // console.log(response.data.pages_to_create[0].matched_products);
        return { posts: response.data.pages_to_create[0].matched_products };
      });
  }
};
</script>

<style>
</style>
