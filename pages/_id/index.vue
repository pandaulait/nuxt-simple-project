<template>
  <div>
    <h1>{{ fields.title.value }}</h1>
    <img alt="" :src="fields.image.value" />
    <div v-html="fields.description.value" />
    参照コンテンツ↓
    <div v-for="(v, index) in fields.ref.value" :key="index">
      <h1>{{ v.fields.title.value }}</h1>
      <img alt="" :src="v.fields.image.value" />
      <div v-html="v.fields.description.value" />
    </div>
  </div>
</template>
<script>
export default {
  async asyncData({ $axios, params }) {
    const response = await $axios.get(
      `https://cms.spearly.app/api/v1/contents/${params.id}`,
      {
        headers: {
          Authorization:
            `Authorization: Bearer ${process.env.API_KEY}`
        }
      }
    );
    return { fields: response.data.fields };
  }
};
</script>
