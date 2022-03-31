# cpnt-262-a8
### Will Tengyuan Li
### March 31,2022
### Plan 
- fetching data from storyblok
- fetching data from public api
### Todo
- create a nuxt 3 project
- install storyblok
- connect storyblok to nuxt.
- create a storyblok content.
- get the json.
- fetching data from storyblok content
``` 
      import { ref, onMounted } from "vue";
  const data = ref(null);
  onMounted(async () => 
    data.value = await fetch(
      "https://api.storyblok.com/v2/cdn/stories/landing-page?version=draft&token=pWaK6dZh8M6dcvj4RgOVkgtt&cv=1648747978"
    )
      .then((response) => response.json())
      .then(({ story }) => story.content);
  });
 ``` 
 - fetching data from a public api
 ``` 
  const {data:dog} = await useAsyncData("dogs", ()=> 
$fetch("https://dog.ceo/api/breeds/image/random"),
);
``` 
- use the data in the template with{{}}.
### Deploy to Netlify
https://keen-speculoos-685bb8.netlify.app/
### Attributes
- Storyblok Tutorial #1: Fetching data from youtube : https://www.youtube.com/watch?v=-fQB8FDYLSg&ab_channel=LIFTED
- nuxtjs guide: https://www.nuxtjs.cn/guides/features/data-fetching
- dog api: https://dog.ceo/dog-api/
