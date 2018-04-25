<template>
  <div id="app">
    <HelloWorld msg="Welcome to Your Vue.js App">
			<SlotComponent @changeProperty="changeCustomProperty($event)">
				<SlotComponent @changeProperty="changeCustomProperty($event)">
					<SlotComponent @changeProperty="changeCustomProperty($event)" />
				</SlotComponent>
			</SlotComponent>
		</HelloWorld>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue';
import SlotComponent from './components/Slot.vue';

export default {
  name: 'app',
  components: {
    HelloWorld,
    SlotComponent
  },
  provide: {
    color: 'red'
  },
  methods: {
    changeCustomProperty(payload) {
      this[payload.prop] = payload.value;
      this.updateTree(this.$children, payload);
    },

    updateTree(childrens, payload) {
      if (childrens.length) {
        childrens.forEach(child => {
          child[payload.prop] = payload.value;
          this.updateTree(child.$children, payload);
        });
      }
    }
  }
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
