<template>
  <trading-vue :data="chart" :width="this.width" :height="this.height"
               :color-back="colors.colorBack"
               :color-grid="colors.colorGrid"
               :color-text="colors.colorText">
  </trading-vue>
</template>

<script>
import TradingVue from 'trading-vue-js'
import Data from '../data/data.json'

export default {
  name: 'app',
  components: { TradingVue },
  methods: {
    onResize() {
      this.width = window.innerWidth
      this.height = window.innerHeight
    }
  },
  mounted() {
    window.addEventListener('resize', this.onResize)
  },
  beforeDestroy() {
    window.removeEventListener('resize', this.onResize)
  },
  data() {
    return {
      chart: Data,
      width: window.innerWidth,
      height: window.innerHeight,
      colors: {
        colorBack: '#fff',
        colorGrid: '#eee',
        colorText: '#333',
      }
    }
  },
  created() {
    setInterval(() => {
      this.chart.chart.data.unshift([1587272400000, 7240.1, 7240.2, 7120, 7131, 709.93])
    }, 1000)

  }
}
</script>