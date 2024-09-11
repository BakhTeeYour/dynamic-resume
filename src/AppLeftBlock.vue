<template>
  <form class="card left-block" @submit="onAddBlock">
    <app-select
        label="Тип блока"
        :options="BlockTypeOptions"
        v-model:value="blockType"
    ></app-select>
    <app-text-area
        type="text"
        v-model:value="inputValue"
        label="Значение"
        rows="3"
        placeholder="Введите значение"
    ></app-text-area>

    <button
        class="btn primary"
        :disabled="inputValue.length < 3"
        type="submit">
      Добавить
    </button>
  </form>
</template>

<script>
import AppSelect from './AppSelect'
import AppTextArea from "./AppTextArea";
import {BlockTypeOptions} from './constants'

export default {
  name: 'AppLeftBlock',
  data() {
    return {
      BlockTypeOptions,
      blockType: 'title',
      inputValue: '',
      inputError: null
    }
  },
  components: {
    AppSelect,
    AppTextArea
  },
  methods: {
    onAddBlock(e) {
      e.preventDefault()
      if (this.inputValue === '') {
        this.inputError = 'Обязательное поле'
        return
      }
      const formData = {
        blockType: this.blockType,
        inputValue: this.inputValue
      }
      this.$emit('form-data', formData)
      this.blockType = 'title'
      this.inputValue = ''
    }
  }
}
</script>

<style lang="scss" scoped>
.left-block {
  min-width: 300px;
  display: flex;
  flex-direction: column;
  gap: 10px;
}
</style>
