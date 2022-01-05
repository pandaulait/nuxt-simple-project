<template>
  <div>
    <ul>
      <li v-for="(content, index) in contents" :key="index">
        <nuxt-link :to="`/${content.public_uid}`">{{
          content.fields.title.value
        }}</nuxt-link>
      </li>
    </ul>
  </div>
</template>
<script>
export default {

  async asyncData({ $axios }) {
    const response = await $axios.get(
      `https://cms.spearly.app/api/v1/content_types/${process.env.CONTENT_TYPE_ID}/contents`,
      {
        headers: {
          Authorization:
            `Authorization: Bearer ${process.env.API_KEY}`
        }
      }
    );
    return { contents: response.data.contents };
  }
};
</script>
