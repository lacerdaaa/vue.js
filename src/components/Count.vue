<template>
    <div :class="counterClass">
      <p>{{ counter }}</p>
      <button @click="increment">Incrementar</button>
    </div>
  </template>
  
  <script>
  export default {
    name: 'CounterComponent',
    data() {
      return {
        counter: 0,
        colors: ['red', 'blue', 'green', 'yellow', 'purple'],
      };
    },
    computed: {
      counterClass() {
        return this.colors[this.counter % this.colors.length];
      },
    },
    methods: {
      increment() {
        this.counter++;
      },
    },
  };
  </script>
  
  <style scoped>
  .red {
    color: red;
  }
  .blue {
    color: blue;
  }
  .green {
    color: green;
  }
  .yellow {
    color: yellow;
  }
  .purple {
    color: purple;
  }
  button {
    margin-top: 10px;
    padding: 10px;
    background-color: #ccc;
    border: none;
    cursor: pointer;
  }
  </style>
  