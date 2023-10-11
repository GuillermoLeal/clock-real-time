<template>
  <Clock theme="yellow" />
  <Clock theme="blue" />
  <Clock theme="red" />
</template>

<script>
import Clock from './components/Clock.vue'

export default {
  name: 'App',
  components: {
    Clock
  }
}
</script>

<style>
:root {
  --color-theme: #fff;
}

.yellow {
  --color-theme: #ffe600;
}

.blue {
  --color-theme: #0071e1;
}

.red {
  --color-theme: #ff0000;
}
</style>
