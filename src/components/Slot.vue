<template>
  <div>
		<h1 :style="{color: color}">I'm slot component</h1>
		<slot></slot>
  </div>
</template>

<script>
export default {
  name: 'SlotComponent',
  data() {
    return {
      color: this.color
    };
  }
};
</script>
