<template>
  <form action="" @submit.prevent="onSubmit()">
    <VTextInput v-model="label"/>
    <VButton :disabled="!isFormValid">ADD TODO</VButton>
  </form>
</template>

<script>
import VTextInput from "@/components/VTextInput.vue";
import VButton from "@/components/VButton.vue";

export default {
  name: 'TodoListForm',
  components: {VButton, VTextInput},
  emits: ['submit'],
  data: () => ({
    label: ''
  }),
  computed: {
    isFormValid() {
      return this.label;
    }
  },
  methods: {
    onSubmit() {
      if (!this.isFormValid) {
        return;
      }

      this.$emit('submit', {
        id: crypto.randomUUID(),
        label: this.label,
        checked: false,
      });

      this.label = '';
    }
  }
}
</script>

<style scoped>
form {
    display: grid;
    gap: 1em;
    padding: 0.5em;
    grid-template-columns: 1fr max-content;
}

</style>
