<script>
import HeaderTitle from '../CommonComponents/HeaderTitle.vue';
import ToastMessage from '../CommonComponents/ToastMessage.vue';
export default {
  components: {
    HeaderTitle,
    ToastMessage,
  },
  data() {
    return {
      interval: 0,
    };
  },
  mounted() {
    this.interval = setInterval(() => {
      this.$store.commit('getDuration');
    }, 100);
  },
  beforeUnmount() {
    clearInterval(this.interval);
  },
};
</script>
<template>
  <HeaderTitle heading="Stopwatch" />
  <ToastMessage
    id="stopwatchError"
    :message="$store.state.stopwatch.errorMessage"
  />
  <p class="text-6xl text-center mb-5 dark:text-gray-100">
    {{ $store.state.stopwatch.duration }}
  </p>
  <div class="flex items-center justify-center mb-3">
    <div
      class="inline-flex shadow-md hover:shadow-lg focus:shadow-lg"
      role="group"
    >
      <button
        type="button"
        class="
          rounded-l
          inline-block
          px-7
          py-3
          bg-green-600
          text-white
          font-medium
          text-sm
          leading-snug
          uppercase
          hover:bg-green-700
          focus:bg-green-700 focus:outline-none focus:ring-0
          active:bg-green-800
          transition
          duration-150
          ease-in-out
        "
        @click="$store.commit('startStopwatch')"
      >
        Start
      </button>
      <button
        type="button"
        class="
          inline-block
          px-7
          py-3
          bg-yellow-300
          text-white
          font-medium
          text-sm
          leading-snug
          uppercase
          hover:bg-yellow-500
          focus:bg-yellow-500 focus:outline-none focus:ring-0
          active:bg-yellow-400
          transition
          duration-150
          ease-in-out
        "
        @click="$store.commit('resetStopwatch')"
      >
        Reset
      </button>
      <button
        type="button"
        class="
          rounded-r
          inline-block
          px-7
          py-3
          bg-red-600
          text-white
          font-medium
          text-sm
          leading-snug
          uppercase
          hover:bg-red-700
          focus:bg-red-700 focus:outline-none focus:ring-0
          active:bg-red-800
          transition
          duration-150
          ease-in-out
        "
        @click="$store.commit('stopStopwatch')"
      >
        Stop
      </button>
    </div>
  </div>
</template>
