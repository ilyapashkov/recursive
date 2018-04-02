<template>
  <div id="app">
    <HelloWorld msg="Welcome to Your Vue.js App">
			<SlotComponent>
				<SlotComponent>
					<SlotComponent/>
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
