<template>
  <div v-if="data">
   <h1>{{data.title}}</h1>
   <p>{{data.description}}</p>
   <img :src="data.image.filename" alt="" />
   <h1>Fetch data from public api</h1>
   <img :src="dog.message" alt=""/>
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";
  const data = ref(null);
  onMounted(async () => {
    data.value = await fetch(
      "https://api.storyblok.com/v2/cdn/stories/landing-page?version=draft&token=pWaK6dZh8M6dcvj4RgOVkgtt&cv=1648747978"
    )
      .then((response) => response.json())
      .then(({ story }) => story.content);
  });
  const {data:dog} = await useAsyncData("dogs", ()=> 
$fetch("https://dog.ceo/api/breeds/image/random"),
);
</script>
<style scoped>
div{
  width: 500px;
  border: 1px solid black;
  margin: 50px auto;
}
img{
  width: 100%;
}
</style>
