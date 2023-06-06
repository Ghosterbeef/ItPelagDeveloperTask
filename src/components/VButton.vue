<template>
  <button :class="buttonClass">
    <slot/>
  </button>
</template>

<script>
export default {
  name: "VButton",
  props: {
    appearance: {
      type: String,
      validator(value) {
        return ['primary', 'danger'].includes(value)
      },
      default: 'primary'
    },
    circle: {
      type: Boolean,
      default: false
    }
  },
  computed: {
    buttonClass() {
      return [this.$props.appearance, {circle: this.$props.circle}]
    }
  }
}
</script>

<style scoped>
button {
    --bg-color: #343434;
    --bg-color--hover: #565656;
    padding: 0.75em;
    border-radius: 4px;
    border: none;
    cursor: pointer;
    outline: none;
    transition: 250ms;
    font-weight: 600;
    font-size: 16px;
    line-height: 16px;
    color: #ffffff;
    background-color: var(--bg-color);
}

button:hover, button:focus-visible {
    background: var(--bg-color--hover);
}

button.primary {
    --bg-color: #42b883;
    --bg-color--hover: #42d392;
}

button.danger {
    --bg-color: #ff4b4b;
    --bg-color--hover: #e03d3d;
}

button.circle {
    border-radius: 50%;
    padding: 0;
    display: flex;
    align-items: center;
    justify-content: center;
    line-height: 1px;
}


</style>
