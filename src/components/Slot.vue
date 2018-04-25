<template>
  <div>
		<h1 :style="{color: color}">I'm slot component</h1>
		<button type="button" @click="changeColor()">Change Color</button>
		<slot></slot>
  </div>
</template>

<script>
export default {
  name: 'SlotComponent',
  inject: ['color'],
  data() {
    return {
      color: this.color
    };
  },

  methods: {
    changeColor() {
      this.$emit('changeProperty', {prop: 'color', value: 'blue'});
    }
  }
};
</script>
