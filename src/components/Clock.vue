<template>
  <div :class="theme">
    <div class="container">
      <div class="clock">
        <div class="digits">{{ hours }}</div>
        <div class="dots">:</div>
        <div class="digits">{{ minutes }}</div>
        <div class="dots">:</div>
        <div class="digits">{{ seconds }}</div>
        <div class="time">{{ time }}</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: '_Clock',
  props: {
    theme: {
      type: String,
      default: 'red'
    }
  },
  data() {
    return {
      hours: '--',
      minutes: '--',
      seconds: '--',
      time: 'AM'
    }
  },
  methods: {
    updateClock() {
      const now = new Date()

      this.hours = String(now.getHours()).padStart(2, '0')
      this.minutes = String(now.getMinutes()).padStart(2, '0')
      this.seconds = String(now.getSeconds()).padStart(2, '0')
      this.time = Number(this.hours) > 12 ? 'PM' : 'AM'
    }
  },
  mounted() {
    setInterval(() => {
      this.updateClock()
    }, 1000)
  }
}
</script>

<style scoped>
.container {
  background: rgba(130, 130, 130, 1);
  background: linear-gradient(84deg, rgba(130, 130, 130, 1) 0%, rgba(74, 74, 74, 1) 100%);
  min-width: max-content;
  max-width: max-content;
  padding: 40px;
}

.clock {
  padding: 20px;
  background-color: #000;
  border-radius: 15px;
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;

  & div {
    padding: 10px;
    font-family: 'Orbitron', sans-serif;
    color: var(--color-theme);
    font-size: 6rem;
    box-sizing: border-box;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  & .digits {
    width: 185px;
  }

  & .time {
    font-size: 3rem;
  }
}
</style>
