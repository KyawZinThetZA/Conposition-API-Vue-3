<template>
  <div v-if="post && user">
    <h1 class="text-3xl">{{ post.title }}</h1>
    <div class="text-gray-500 mb-10">by {{ user.name }}</div>
    <div>{{ post.body }}</div>
  </div>
</template>
<script setup async>
import { useRoute } from "vue-router";
import useResource from "../composables/useResource.js";
import { watch } from "vue";
const route = useRoute();

//post
const { item: post, fetchOne: fetchPost } = useResource("posts");
fetchPost(route.params.id);
// await fetchPost(route.params.id);
//user
const { item: user, fetchOne: fetchUser } = useResource("users");

// fetchUser(post.value.userId);

watch(
  () => ({ ...post.value }),
  () => fetchUser(post.value.userId)
);
// (async()=>{
//   await fetchPost(route.params.id);
//   fetchUser(post.value.userId);
// })();
</script>
