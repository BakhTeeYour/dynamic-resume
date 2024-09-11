<template>
  <div class="card right-block">
    <h1 v-if="!value.length">Добавьте первый блок, чтобы увидеть результат</h1>
    <div style="display: flex; flex-direction: column" v-else v-for="block in value" v-html="block"></div>
  </div>
</template>

<script>
const getBlock = (title, value) => {
  switch (value) {
    case 'title' :
      return `<h1>${title}</h1>`
    case 'subtitle' :
      return `<h2>${title}</h2>`
    case 'avatar' :
      return `<img
                   style="
                   border-radius: 50%;
                   width: 150px;
                   height: 150px;
                   align-self: center"
                   src="${title}"
                   alt="logo">`
    case 'text' :
      return `<div style="padding-bottom: 8px">${title}</div>`
  }
}
export default {
  name: 'AppRightBlock',
  props: ['blockValue'],
  computed: {
    value() {
      return this.blockValue.map(e => getBlock(e.inputValue, e.blockType))
    }
  }
}
</script>

<style lang="scss" scoped>
.right-block {
  flex-grow: 1;
}

h3 {
  margin: 0;
}
</style>
