<!-- Please remove this file from your project -->
<template>
  <div>
    <button class="w-full" @click="increment">Click me: {{ count }}</button>
    <button class="w-full" @click="decrement">Decrement: {{ number }}</button>
    <span class="flex justify-center">{{ publishedBooksMessage }}</span>

    <!-- check className -->
    <div
      class="text-center"
      :class="{ 'text-indigo-700': isActive, 'text-danger': hasError }"
    >
      IsActive
    </div>

    <!-- check className -->
    <div class="text-center" :class="[isActive ? 'text-black' : '']">
      Active color
    </div>
    <Items :propName="propValue" :propValue1="proValue1" />

    <NuxtLink to="/demo">
      <button class="bg-red-500 px-5">Demo</button>
    </NuxtLink>
  </div>
</template>

<script>
import Items from "./Items.vue";

export default {
  name: "NuxtTutorial",
  components: {
    Items,
  },
  data() {
    return {
      // actions buttons
      count: 1,
      number: 0,
      // change value
      author: {
        name: "John Doe",
        books: [
          "Vue 2 - Advanced Guide",
          "Vue 3 - Basic Guide",
          "Vue 4 - The Mystery",
        ],
      },
      isActive: true,
      propValue: "Test",
      proValue1: "Demo",
    };
  },
  methods: {
    // actions buttons
    increment() {
      this.count++;
    },
    decrement() {
      this.number--;
    },
  },
  // change value
  computed: {
    publishedBooksMessage() {
      return this.author.books.length > 0 ? "More than 0" : "Not";
    },
  },
};
</script>
