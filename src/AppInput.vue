<template>
  <div class="form-control" :class="{invalid: error}">
    <label :for="id">{{ label }}</label>
    <input
        :type="type"
        :id="id"
        :placeholder="placeholder"
        :value="value"
        @input="$emit('update:value', $event.target.value)"
    >
    <small v-if="error">{{ error }}</small>
  </div>
</template>

<script>
import { useId } from 'vue'
const id = useId()
export default {
  emits: ['update:value'],
  props: {
    error: {
      type: String,
      default: '',
    },
    placeholder: {
      type: String,
      default: 'Введите значение'
    },
    type: {
      type: String,
      required: true
    },
    value: {
      type: [String, Number],
      required: true,
    },
    label: {
      type: String,
      default: '',
    }
  },
  data() {
    return {
      id
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
