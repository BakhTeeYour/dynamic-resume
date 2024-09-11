<template>
  <div class="container pt-5">
    <div class="wrapper">
      <div>
        <app-left-block @form-data="onAddBlock">

        </app-left-block>
      </div>
      <app-right-block :block-value="blockValue">

      </app-right-block>
    </div>
    <button
        class="btn primary comments-btn"
        v-if="comments.length < 1"
        @click="getComments">
      Загрузить комментарий
    </button>
    <app-comments v-else :comments="comments">

    </app-comments>
  </div>
</template>

<script>
import AppLeftBlock from './AppLeftBlock';
import AppRightBlock from './AppRightBlock';
import AppComments from './AppComments';
import axios from "axios";

export default {
  name: 'App',
  data() {
    return {
      blockValue: [],
      comments: [],
      isLoading: false,
    }
  },
  components: {
    AppLeftBlock,
    AppRightBlock,
    AppComments
  },
  methods: {
    onAddBlock(e) {
      this.blockValue.push(e)
    },
    async getComments() {
      this.isLoading = true

      try {
        const {data} = await axios.get('https://jsonplaceholder.typicode.com/comments?limit=50')
        this.comments = data.slice(0, 20)
        this.isLoading = false
      } catch (e) {
        this.isLoading = false
      }
    }
  }
}
</script>

<style lang="scss">
.wrapper {
  display: flex;
  justify-content: space-between;
  gap: 20px
}
</style>
