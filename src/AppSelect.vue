<template>
  <div class="form-control">
    <label :for="id">{{ label }}</label>
    <select :id="id" :value="modelValue" @input="$emit('update:ModelValue', $event.target.value)">
      <option v-if="placeholder" value="" disabled selected>{{ placeholder}}</option>
      <option v-for="option in options" :value="option.value" :key="option.id">
        {{ option.label }}
      </option>
    </select>
    <small v-if="error">{{ error }}</small>
  </div>
</template>

<script>
import {useId} from 'vue'
const id = useId()
export default {
  emits: ['update:ModelValue'],
  props: {
    options: {
      type: Array,
      default: []
    },
    label: {
      type: String,
      default: ''
    },
    modelValue: {
      type: String,
      required: true
    },
    error: {
      type: String,
      default: ''
    },
    placeholder: {
      type: String,
      default: ''
    }

  },
  data() {
    return {
      id: id
    }
  }
}
</script>

<style lang="scss" scoped>

</style>
