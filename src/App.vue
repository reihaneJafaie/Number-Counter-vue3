<script setup>
import counterWithOutApi from "./components/counterWithOutApi.vue";

</script>

<template>
  <section>
    <div class="card">
      <img src="../src/assets/reihaneJafaie.png" alt="Avatar" />
      <div class="textBox">
        <h4 class="title"><b>Rei CodeBanu</b></h4>
        <p>
          This project is an animated counter component built with Vue.js 3. The
          counters start animating when the user scrolls and the component comes
          into view. The project can be implemented in two ways: using an API to
          fetch data and without using an API with static data.
        </p>
        <div>
          github: https://github.com/reihaneJafaie instagram : rei_codebanu
        </div>
      </div>
    </div>
    <section style="height: 700px"></section>

    <!-- main Components -->
    <counterWithOutApi />


  </section>
</template>

<style scoped>
.card {
  transition: 0.3s;
  width: 80%;
  font-family: "Gill Sans", "Gill Sans MT", Calibri, "Trebuchet MS", sans-serif;
  /* background-color: palevioletred; */
  border-radius: 18px;
  padding: 30px;
  margin: 0 auto;
}

.card:hover {
  box-shadow: 0 8px 16px 0 rgba(0, 0, 0, 0.2);
}
.title {
  font-size: 32px;
  color: rgb(133, 30, 30);
  margin: 10px 0;
}
.textBox {
  font-size: 20px;
  margin: 0;
}

img {
  width: 300px;
  border-radius: 15px;
}
</style>
س