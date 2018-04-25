<template>
  <div>
		{{state.color}}
		<button type="button" @click="changeColor()">Change Color From Child</button>
		
  </div>
</template>

<script>
export default {
  name: 'SlotComponent',
  inject: ['state'],
  computed: {
    getState() {
      return this.state;
    }
  },
  methods: {
    changeColor() {
      this.$emit('updateState', {key: 'color', value: 'pink'});
    }
  }
};
</script>
