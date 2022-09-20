<template>
  <div>
    <div>
      <b-dropdown
        text="Block Level Dropdown Menu"
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
  props: {
    dropdownOptions: Array,
    selectCategory: Function
  },
};
</script>
