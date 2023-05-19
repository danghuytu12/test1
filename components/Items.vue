<template>
  <div>
    <h2>Child Component</h2>
    <p>{{ propName }}</p>
    <p>{{ propValue1 }}</p>
    <ul>
      <li v-for="(item, index) in items">
        {{ parentMessage }} - {{ index }} - {{ item.message }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    propName: {
      type: String,
    },
    propValue1: {
      type: String,
    },
  },
  data() {
    return {
      parentMessage: "Parent",
      items: [{ message: "Foo" }, { message: "Bar" }],
    };
  },
};
</script>
