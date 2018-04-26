<template>
  <div>
		{{state.color}}
		<button type="button" @click="changeColor()">Change Color From Child</button>
		<slot></slot>
  </div>
</template>

<script>
import EventBus from '../eventBus';

export default {
  name: 'SlotComponent',
  inject: ['state'],
  computed: {
    getState() {
      return this.state;
    }
  },
  mounted() {
    this.changeColor();
  },
  methods: {
    changeColor() {
      EventBus.$emit('updateState', {
        key: 'color',
        value: !this.getState.color
      });
    }
  }
};
</script>
