<template>
  <div>
    <div id="slogan" class="text-center">
      <h1>Namegator</h1>
      <br />
      <h6 class="text-secondary">Gerador de nomes ultilizando VueJS</h6>
    </div>
    <div id="main">
      <div class="container">
        <div class="row">
          <div class="col-md">
            <h5>Prefixos <span class="badge bg-info text-dark">{{ prefixes.length}}</span></h5>
            <div class="card">
              <div class="card-body">
                <ul class="list-group">
                  <li
                    class="list-group-item"
                    v-for="prefixe in prefixes"
                    :key="prefixe"
                  >
                    {{ prefixe }}
                  </li>
                </ul>
                <br>
                <input type="text" class="form-control" placeholder="Digite o prefixo"/>
              </div>
            </div>
          </div>
          <div class="col-md">
            <h5>SUfixos <span class="badge bg-info text-dark"> {{ sufixes.length }}</span></h5>
            <div class="card">
              <div class="card-body">
                <ul class="list-group">
                  <li
                    class="list-group-item"
                    v-for="sufixe in sufixes"
                    :key="sufixe"
                  >
                    {{ sufixe }}
                  </li>
                </ul>
                <br>
                <input class="form-control" type="text" placeholder="Digite o sufixe"/>
              </div>
            </div>
          </div>
        </div>
        <br>
        <h5>Dominios <span class="badge bg-info text-dark"> {{ domains.length }}</span></h5>
        <div class="card">
          <div class="card-body">
            <ul class="list-group">
              <li class="list-group-item" v-for="domain in domains" :key="domain"> {{ domain }}</li>
            </ul>

          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import bootstrap from "bootstrap/dist/css/bootstrap.css";
export default {
  name: "App",
  data: function () {
    return {
      prefixes: ["Air", "Jet", 'Flight'],
      sufixes: ['Hub', 'Station', 'Mart'],
      domains: ['AirHub', 'AirStation', 'AirMart', 'JetHut', 'JetStation', 'JetMart', 'FlightHub', 'FlightStation', 'FlightMart']
    };
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
</style>
