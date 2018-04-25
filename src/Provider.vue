<template>
  <div>
		<slot></slot>
	</div>
</template>

<script>
import Vue from 'vue';
import Component from 'vue-class-component';
import EventBus from './eventBus';

const inititalState = {
  color: 'black'
};

@Component({
  name: 'Provider',
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

  mounted() {
    EventBus.$on('updateState', event => this.changeCustomProperty(event));
  }
}
</script>
