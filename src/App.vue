<template>
  <div id="app">
    <TableLayout msg="Запчастини" />
  </div>
</template>

<script>
import TableLayout from './components/TableLayout.vue';

export default {
  name: 'App',
  components: {
    TableLayout,
  },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;600&display=swap');

:root {
  --primary-black: #18191e;
  --primary-white: #fff;
  --gray-600: #a2a3a5;
  --gray-border: hsla(220, 2%, 64%, 0.3);
  --primary-accent-b-2-b: hsla(104, 88%, 39%, 1);
  --link-color: #4c6bff;
  --primary-accent-b-2-c: #4c6bff;
  --secondary-red: #d20000;
  --all-red-50: #fbe6e6;
  --secondary-purple: #7a00cd;
  --secondary-orange: #fa8d1a;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

button {
  border: none;
  background-color: transparent;
  outline: none;

  cursor: pointer;
}

input {
  cursor: pointer;
}

a {
  color: inherit;
  text-decoration: none;
  transition: all 0.3s ease-in-out;
}

.table {
  border-collapse: collapse;
}

.table th,
.table td {
  padding: 0;
  margin: 0;
}

#app {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;

  font-family: 'Inter', sans-serif;
  font-size: 14px;
}
</style>
