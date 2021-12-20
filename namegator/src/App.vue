<template>
  <div>
    <div id="slogan" class="text-center">
      <h1>Namegator</h1>
      <br />
      <h6 class="text-secondary">Gerador de nomes ultilizando VueJS</h6>
    </div>

    <div id="main">
      <DomainList></DomainList>
    </div>
  </div>
</template>

<script>
import DomainList from "./components/DomainList.vue";

export default {
  name: "App",

  components: {
    DomainList,
  },
};
</script>

<style>
#slogan {
  margin-top: 30px;
  margin-bottom: 30px;
}
#main {
  background-color: #f1f1f1;
  padding-top: 30px;
  padding-bottom: 30px;
}
.icons {
  color: #fff;
  font-size: 0.95rem;
}
</style>
