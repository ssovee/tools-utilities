<script>
export default {
  props: {
    message: { required: true, type: String },
    id: { required: true, type: String },
  },
  data() {
    return {
      timeOutClear: '',
    };
  },
  watch: {
    message: function () {
      const div = document.getElementById(this.id);
      div.style.display = 'none';
      if (this.message !== '') {
        div.style.display = 'flex';
        div.style.animation = 'fade-in 0.5s';
        this.timeOutClear = setTimeout(() => {
          div.style.display = 'none';
        }, 2000);
      }
    },
  },
  mounted() {
    const div = document.getElementById(this.id);
    if(div){
      div.style.display = 'none';
    }
  },
  unmounted() {
    clearTimeout(this.timeOutClear);
  },
};
</script>

<template>
  <div
    :id="id"
    class="
      fixed z-[100]
      top-5
      right-5
      flex
      items-center
      w-full
      max-w-xs
      p-4
      mb-4
      text-capitalize text-gray-500
      bg-white
      rounded-lg
      shadow
      dark:text-gray-400 dark:bg-gray-800
    "
    role="alert"
  >
    <div
      class="
        inline-flex
        items-center
        justify-center
        flex-shrink-0
        w-8
        h-8
        text-red-500
        bg-red-100
        rounded-lg
        dark:bg-red-800 dark:text-red-200
      "
    >
      <svg
        class="w-5 h-5"
        fill="currentColor"
        viewBox="0 0 20 20"
        xmlns="http://www.w3.org/2000/svg"
      >
        <path
          fill-rule="evenodd"
          d="M4.293 4.293a1 1 0 011.414 0L10 8.586l4.293-4.293a1 1 0 111.414 1.414L11.414 10l4.293 4.293a1 1 0 01-1.414 1.414L10 11.414l-4.293 4.293a1 1 0 01-1.414-1.414L8.586 10 4.293 5.707a1 1 0 010-1.414z"
          clip-rule="evenodd"
        />
      </svg>
    </div>
    <div class="ml-3 text-sm font-normal">
      {{ message }}
    </div>
  </div>
</template>
<style>
@keyframes fade-in {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
</style>
