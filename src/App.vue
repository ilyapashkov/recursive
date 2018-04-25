<template>
  <div id="app" >
    <HelloWorld msg="Welcome to Your Vue.js App">
			{{ state.color }}
			<SlotComponent @updateState="changeCustomProperty($event)">
			</SlotComponent>
		</HelloWorld>
  </div>
</template>

<script>
import Vue from 'vue';
import Component from 'vue-class-component';
import HelloWorld from './components/HelloWorld.vue';
import SlotComponent from './components/Slot.vue';

const inititalState = {
  color: 'black'
};

@Component({
  name: 'app',
  components: {
    HelloWorld,
    SlotComponent
  },
  provide() {
    return {
      state: this.state
    };
  },
  methods: {
    changeCustomProperty(payload) {
      Vue.set(this.state, payload.key, payload.value);
    }
  }
})
export default class App extends Vue {
  constructor(state = inititalState) {
    super();
    this.state = Vue.set(this, 'state', state);
  }
}
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
