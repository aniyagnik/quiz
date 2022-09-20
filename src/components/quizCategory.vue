<template>
  <div>
    <div>
      <b-dropdown
        text="Select Category for the quiz"
        block
        variant="primary"
        class="m-2"
        menu-class="w-100"
      >
        <b-dropdown-item
          href="#"
          v-for="option in dropdownOptions"
          :key="option.code"
          @click="()=>selectCategory(option.code)"
          >{{ option.text }}</b-dropdown-item
        >
      </b-dropdown>
    </div>
  </div>
</template>

<script>
export default {
  name:'quizCategory',
  props: {
    dropdownOptions: Array,
    selectCategory: Function
  },
};
</script>
