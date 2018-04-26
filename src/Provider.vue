<template>
  <div>
		<slot></slot>
	</div>
</template>

<script>
import Vue from 'vue';
import EventBus from './eventBus';

const inititalState = {
  color: 'black'
};

export default {
  name: 'Provider',
  data() {
    return {
      state: inititalState
    };
  },
  provide() {
    return {
      state: this.state
    };
  },
  mounted() {
    EventBus.$on('updateState', event => this.changeCustomProperty(event));
  },
  methods: {
    changeCustomProperty(payload) {
      Vue.set(this.state, payload.key, payload.value);
    }
  }
};
</script>
