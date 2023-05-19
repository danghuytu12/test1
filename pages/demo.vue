<template>
  <div>
    <h1 class="text-red-500">About Page</h1>
    <NuxtLogo :responseData="data" />
    <div v-for="result in data" :key="result.title">
      {{ result.title }}
    </div>
    <button @click="say('demo')">Click</button>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import NuxtLogo from "../components/NuxtLogo.vue";

interface IProps {
  completed: boolean;
  id: string;
  title: string;
  userId: string;
}

export default Vue.extend({
  name: "Demo",
  data() {
    return {
      loading: false,
      data: [] as IProps[],
    };
  },
  methods: {
    async fetchData() {
      this.loading = true;
      try {
        const response = await this.$axios.get("todos");
        this.data = response.data;
      } catch (error) {
        console.error(error);
      } finally {
        this.loading = false;
      }
    },
    say(message: string) {
      alert(message);
    },
  },
  mounted() {
    this.fetchData();
  },
  components: {
    NuxtLogo,
  },
});
</script>
