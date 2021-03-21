<template>
  <div class="home">
    <HelloWorld msg="Welcome to your postits wall !" />
    <PostItWall />
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";
import PostItWall from "@/components/PostItWall.vue";

export default {
  name: "Home",
  components: {
    HelloWorld,
    PostItWall
  }
};
</script>
