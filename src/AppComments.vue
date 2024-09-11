<template>
  <div class="comments-block card pt-5">
    <h1>Комментарии</h1>
    <div v-for="comment in comments" :key="comment.id">
      <h3>{{ comment.email }}</h3>
      <div>{{ comment.body }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'AppComments',
  props: ['comments'],
}
</script>

<style lang="scss" scoped>
.comments-block {
  margin-top: 20px;
}

.comments-btn {
  margin-top: 20px;
}
</style>
