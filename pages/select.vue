<template>
  <div>
    <select v-model="selectedOption">
      <option
        v-for="option in options"
        :key="option.value"
        :value="option.value"
      >
        {{ option.label }}
      </option>
    </select>
    <p>Selected option: {{ selectedOption }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      selectedOption: null,
      data: [],
      options: [
        { value: "option1", label: "Option 1" },
        { value: "option2", label: "Option 2" },
        { value: "option3", label: "Option 3" },
      ],
    };
  },
  watch: {
    selectedOption(newUserId) {
      this.fetchUserData(newUserId);
    },
  },
  methods: {
    async fetchUserData(newUserId) {
      try {
        const response = await this.$axios.get(`/api/users/${newUserId}`);
        console.log(response.data);
      } catch (error) {
        console.error(error);
      }
    },
  },
};
</script>
