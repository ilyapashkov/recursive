<template>
  <div>
		<slot></slot>
	</div>
</template>

<script>
import EventBus from './eventBus';

const inititalState = {
  color: true
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
    EventBus.$on('updateState', event => this.updateState(event));
  },
  methods: {
    updateState(payload) {
      this.state[payload.key] = payload.value;
    }
  }
};
</script>
