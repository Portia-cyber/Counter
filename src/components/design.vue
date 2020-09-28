<template>
  <div v-if="loaded" class="container mx-auto bg-white focus:outline-none focus:shadow-outline border border-gray-300 rounded-lg py-2 px-4 block w-full appearance-none leading-normal">
    <section class="text-3xl flex justify-center content-center flex-col mx-auto text-center ">
      <h5 v-if="!expired">Buy Now</h5>
      <h5 v-else > Timer Done </h5>
    </section>
    <section class="text-3xl flex justify-center content-center flex-col me-auto text-center">
      <section class="flex text-6xl justify-center content-center">
        <div class="days mr-2 relative">
          {{ displayDays }}
          <div class="label text-sm absolute bottom-0"> Days</div>
        </div>
        <span class="leading-snug">:</span>
        <div class="days mr-2 relative">
          {{ displayHours }}
          <div class="label text-sm absolute bottom-0"> Hours</div>
        </div>
        <span class="leading-snug">:</span>
        <div class="days mr-2 relative">
          {{ displayMinutes }}
          <div class="label text-sm absolute bottom-0"> Minutes</div>
        </div>
        <span class="leading-snug">:</span>
        <div class="days mr-2 relative">
          {{ displaySeconds }}
          <div class="label text-sm absolute bottom-0"> Seconds</div>
        </div>
      </section>
    </section>
  </div>
</template>

<script>
export default {
  name: 'design.vue',
  data () {
    return {
      displayDays: 0,
      displayHours: 0,
      displayMinutes: 0,
      displaySeconds: 0,
      loaded: false,
      expired: false
    }
  },
  computed: {
    _seconds: () => 1000,
    _minutes () {
      return this._seconds * 60
    },
    _hours () {
      return this._minutes * 60
    },
    _days () {
      return this._hours * 24
    }
  },
  mounted () {
    this.showRemaining()
  },
  methods: {
    showRemaining () {
      const timer = setInterval(() => {
        const now = new Date()
        const end = new Date(2021, 4, 22, 10, 10, 10, 10)
        const distance = end.getTime() - now.getTime()
        if (distance < 0) {
          clearInterval(timer)
          this.expired = true
          return
        }
        const days = Math.floor(distance / this._days)
        const hours = Math.floor((distance % this._days) / this._hours)
        const minutes = Math.floor((distance % this._hours) / this._minutes)
        const seconds = Math.floor((distance % this._minutes) / this._seconds)
        this.displayMinutes = minutes < 10 ? '0' + minutes : minutes
        this.displaySeconds = seconds < 10 ? '0' + seconds : seconds
        this.displayHours = hours < 10 ? '0' + hours : hours
        this.displayDays = days < 10 ? '0' + days : days
        this.loaded = true
      }, 1000)
    }
  }

}
</script>

<style scoped>
.seconds{
  max-width: 60px;
}
</style>
