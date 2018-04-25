<template>
  <div id="app" >
		<provider>
			<SlotComponent>
				<hello-world></hello-world>
			</SlotComponent>
		</provider>
    
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue';
import SlotComponent from './components/Slot.vue';
import Provider from './Provider.vue';

export default {
  name: 'app',
  components: {
    Provider,
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
