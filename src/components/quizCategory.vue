<template>
  <div>
    <div>
      <b-dropdown
        :text="dropdownOptions[targetIndex].text"
        block
        variant="primary"
        class="m-2 customDropdown"
        menu-class="w-100"
      >
        <b-dropdown-item
          v-for="(option,index) in dropdownOptions"
          :key="option.code"
          @click="()=>{targetIndex = index;handleCategory(option.code)}"
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
    handleCategory: Function
  },
  data(){return{targetIndex:0}},

}
</script>
