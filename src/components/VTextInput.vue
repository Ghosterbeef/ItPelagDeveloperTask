<template>
  <input type="text" placeholder="Enter new task" v-model="inputModel">
</template>

<script>
export default {
  name: 'VTextInput',
  emits: ['update:modelValue'],
  props: {
    modelValue: {
      type: String,
      required: true
    }
  },
  computed: {
    inputModel: {
      get() {
        return this.$props.modelValue
      },
      set(val) {
        this.$emit('update:modelValue', val);
      }
    }
  }
}
</script>

<style scoped>
input {
    padding: 0.75em;
    border-radius: 4px;
    font-weight: 400;
    font-size: 16px;
    color: #343434;
    outline: none;
    background: #ffffff;
    border: 2px solid transparent;
}

input:hover, input:focus-visible {
    transition: 250ms;
    border-color: #42d392;
}
</style>
