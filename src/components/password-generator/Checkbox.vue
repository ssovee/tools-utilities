<script>
export default {
  props: {
    title: { type: String, required: true },
    checkboxValue: { type: Boolean, required: true },
  },
  methods: {
    checkUncheck(event) {
      this.$store.commit('checkboxChange', {
        checked: event.target.checked,
        title: this.title,
      });
    },
  },
};
</script>

<template>
  <div class="flex items-center">
    <input
      :id="title"
      v-model="checkboxValue"
      :checked="checkboxValue"
      type="checkbox"
      :value="checkboxValue"
      class="
        w-4
        h-4
        text-blue-600
        bg-gray-100
        rounded
        border-gray-300
        focus:ring-blue-500
        dark:focus:ring-blue-600 dark:ring-offset-gray-800
        focus:ring-2
        dark:bg-gray-700 dark:border-gray-600
      "
      @change="checkUncheck($event)"
    >
    <label
      :for="title"
      class="ml-2 text-sm font-medium text-gray-900 dark:text-gray-300"
    >{{ title }}</label>
  </div>
</template>
