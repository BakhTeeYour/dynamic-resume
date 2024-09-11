<template>
  <div>
    <div class="form-control">
      <label :for="id">{{ label }}</label>
      <textarea
          :id="id"
          :rows="rows"
          :placeholder="placeholder"
          :value="modelValue"
          @input="$emit('update:modelValue', $event.target.value)"
      >

      </textarea>
    </div>
  </div>
</template>

<script>
import {useId} from 'vue'

const id = useId()
export default {
  emits: ['update:modelValue'],
  props: {
    error: {
      type: String,
      default: ''
    },
    placeholder: {
      type: String,
      default: 'Введите значение'
    },
    modelValue: {
      type: [String, Number],
      required: true,
    },
    label: {
      type: String,
      default: ''
    },
    rows: Number,
    default: 2
  },
  data() {
    return {
      id
    }
  }
}
</script>

<style lang="scss" scoped>

</style>
