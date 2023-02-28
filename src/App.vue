<template>
  <div id="app">
    <CalculatorView />
  </div>
</template>

<style>
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@700&display=swap");
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Roboto", sans-serif;
  font-weight: 700;
}
body {
  background-color: #1e293b;
}
</style>
<script>
import CalculatorView from "./views/CalculatorView.vue";
export default {
  components: {
    CalculatorView,
  },
};
</script>
