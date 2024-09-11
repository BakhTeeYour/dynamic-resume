<template>
  <div class="form-control">
    <label :for="id">{{ label }}</label>
    <select :id="id" :value="value" @input="change">
      <option v-if="placeholder" value="" disabled selected>{{ placeholder}}</option>
      <option v-for="option in options" :value="option.value" :key="option.id">
        {{ option.label }}
      </option>
    </select>
    <small v-if="error">{{ error }}</small>
  </div>
</template>

<script>
export default {
  emits: ['update:value'],
  props: {
    options: Array,
    label: String,
    value: String,
    error: String,
    placeholder: String

  },
  data() {
    return {
      id: 'select' + Math.random()
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
