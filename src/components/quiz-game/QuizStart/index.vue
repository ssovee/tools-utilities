<script>
import SelectCategory from './SelectCategory.vue';
import QuestionAmount from './QuestionAmount.vue';
import RedioButton from './RedioButton.vue';
export default {
  components: { SelectCategory, QuestionAmount, RedioButton },
  data() {
    return {
      difficultyRedioButton: [
        { label: 'Any', selected: true, id: 'any', groupName: 'difficulty' },
        { label: 'Easy', groupName: 'difficulty', id: 'easy' },
        { label: 'Medium', groupName: 'difficulty', id: 'medium' },
        { label: 'Hard', groupName: 'difficulty', id: 'hard' },
      ],
    };
  },
};
</script>
<template>
  <SelectCategory />
  <QuestionAmount />
  <p class="block mb-2 text-sm font-medium text-gray-900 dark:text-gray-400">
    Select Difficulty:
  </p>
  <div
    class="
      flex flex-wrap
      -mx-1
      overflow-hidden
      sm:-mx-1
      md:-mx-1
      lg:-mx-1
      xl:-mx-1
    "
  >
    <div
      v-for="readioButton in difficultyRedioButton"
      :key="readioButton"
      class="
        my-1
        px-1
        w-1/2
        overflow-hidden
        sm:my-1 sm:px-1 sm:w-1/2
        md:my-1 md:px-1 md:w-1/2
        lg:my-1 lg:px-1 lg:w-1/2
        xl:my-1 xl:px-1 xl:w-1/2
      "
    >
      <RedioButton
        :id="readioButton.id"
        :label="readioButton.label"
        :selected="readioButton.selected"
        :group-name="readioButton.groupName"
      />
    </div>
  </div>
  <p class="block mb-2 text-sm font-medium text-gray-900 dark:text-gray-400">
    Select Type:
  </p>
  <div
    class="
      flex flex-wrap
      -mx-1
      overflow-hidden
      sm:-mx-1
      md:-mx-1
      lg:-mx-1
      xl:-mx-1
    "
  >
    <div
      class="
        my-1
        px-1
        w-1/2
        overflow-hidden
        sm:my-1 sm:px-1 sm:w-1/2
        md:my-1 md:px-1 md:w-1/2
        lg:my-1 lg:px-1 lg:w-1/2
        xl:my-1 xl:px-1 xl:w-1/2
      "
    >
      <RedioButton
        id="multiple"
        label="Multiple Choice"
        :selected="true"
        group-name="type"
      />
    </div>
    <div
      class="
        my-1
        px-1
        w-1/2
        overflow-hidden
        sm:my-1 sm:px-1 sm:w-1/2
        md:my-1 md:px-1 md:w-1/2
        lg:my-1 lg:px-1 lg:w-1/2
        xl:my-1 xl:px-1 xl:w-1/2
      "
    >
      <RedioButton
        id="boolean"
        label="True / False"
        group-name="type"
      />
    </div>
  </div>
  <div class="flex justify-center items-center">
    <button
      type="button"
      class="
        text-white
        bg-gradient-to-br
        from-purple-600
        to-blue-500
        hover:bg-gradient-to-bl
        focus:ring-4 focus:outline-none focus:ring-blue-300
        dark:focus:ring-blue-800
        font-medium
        rounded-lg
        text-sm
        px-5
        py-2.5
        text-center
        mr-2
        mb-2
      "
      @click="$store.dispatch('startQuiz')"
    >
      Start Quiz
    </button>
  </div>
</template>
