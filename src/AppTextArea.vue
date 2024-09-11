<template>
  <div>
    <div class="form-control">
      <label :for="id">{{ label }}</label>
      <textarea
          :id="id"
          :rows="rows"
          :placeholder="placeholder"
          :value="value"
          @input="change"
          >

      </textarea>
    </div>
  </div>
</template>

<script>
export default {
  emits: ['update:value'],
  props: ['error', 'placeholder', 'type', 'value', 'label', 'rows'],
  data() {
    return {
      id: 'input' + Math.random()
    }
  },
  methods: {
    change(event) {
      this.$emit('update:value', event.target.value)
    }
  }
}
</script>

<style lang="scss" scoped>

</style>
