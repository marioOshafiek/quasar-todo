<template>
  <ul>
    <li>
      <div>
        <slot></slot>
        <button @click="deleteButton()">X</button>
      </div>
    </li>
  </ul>
</template>

<script>
export default {
  props: {
    task: {
      type: String,
    },

    deleteButton: {
      type: Function,
      required: true,
    },
  },
};
</script>

<style></style>
