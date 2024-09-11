<template>
  <div class="form-control" :class="{invalid: error}">
    <label :for="id">{{ label }}</label>
    <input
        :type="type"
        :id="id"
        :placeholder="placeholder"
        :value="value"
        @input="change"
    >
    <small v-if="error">{{ error }}</small>
  </div>
</template>

<script>
export default {
  emits: ['update:value'],
  props: ['error', 'placeholder', 'type', 'value', 'label'],
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
.form-control small {
  color: red;
}

.form-control.invalid input {
  border-color: red;
}
</style>
