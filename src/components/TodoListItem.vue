<template>
  <li class="todo-list-item">
    {{ label }}
    <div class="controls">
      <VCheckbox v-model="checkboxModel"/>
      <VButton appearance="danger" circle class="delete" @click="$emit('delete')">&times;</VButton>
    </div>
  </li>
</template>

<script>
import VCheckbox from "@/components/VCheckbox.vue";
import VButton from "@/components/VButton.vue";

export default {
  name: 'TodoListItem',
  components: {VButton, VCheckbox},
  emits: ['update:checked', 'delete'],
  props: {
    label: {
      type: String,
      required: true,
    },
    checked: {
      type: Boolean,
      required: true
    }
  },
  computed: {
    checkboxModel: {
      get() {
        return this.$props.checked;
      },
      set(val) {
        this.$emit('update:checked', val);
      }
    }
  }
}
</script>

<style scoped>
li {
    padding: 0.75em;
    display: flex;
    align-items: center;
    gap: 1em;
    justify-content: space-between;
}

.controls {
    display: flex;
    gap: 1em;
    align-items: center;
    justify-content: center;
}

.delete {
    width: 1.5em;
    height: 1.5em;
    min-width: 1.5em;
    min-height: 1.5em;
}
</style>
