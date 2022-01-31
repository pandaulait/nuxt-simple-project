<template>
  <div>
    Hello
    <div v-if="testValue">
      {{ testValue }}
    </div>
    <div v-else>
      undefined: process.env.TEST_VALUE
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      testValue: process.env.TEST_VALUE
    }
  }
};
</script>
