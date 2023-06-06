<template>
  <input type="checkbox" :id="id" v-model="checkboxModel">
</template>

<script>
export default {
  name: 'Checkbox',
  emits: ['update:modelValue'],
  props: {
    modelValue: {
      type: Boolean,
      required: true,
    }
  },
  data: () => ({
    id: crypto.randomUUID(),
  }),
  computed: {
    checkboxModel: {
      get() {
        return this.$props.modelValue;
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
    width: 1.5em;
    height: 1.5em;
    min-width: 1.5em;
    min-height: 1.5em;
    accent-color: #42b883;
}
</style>
