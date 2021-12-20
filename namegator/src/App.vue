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
            <h5>
              Prefixos
              <span class="badge bg-info icons">{{ prefixes.length }}</span>
            </h5>
            <div class="card">
              <div class="card-body">
                <ul class="list-group">
                  <li
                    class="list-group-item"
                    v-for="prefixe in prefixes"
                    :key="prefixe"
                  >
                  <div class="row">
                    <div class="col-md">
                      {{ prefixe }}
                    </div>
                    <div class="col-md text-end">
                    <button class="btn btn-info" v-on:click=deletePrefixe(prefixe)> <span class="bi bi-trash icons"></span></button>

                    </div>
                  </div>
                  </li>

                </ul>
                <br />
                <div class="input-group">
                  <input
                    v-on:keyup.enter="addPrefixe(prefixe)"
                    type="text"
                    v-model="prefixe"
                    class="form-control"
                    placeholder="Digite o prefixo"
                  />
                  <div class="input-group-append">
                    <div class="btn btn-info" v-on:click="addPrefixe(prefixe)">
                      <span class="bi bi-plus icons"></span>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div class="col-md">
            <h5>
              SUfixos
              <span class="badge bg-info icons"> {{ sufixes.length }}</span>
            </h5>
            <div class="card">
              <div class="card-body">
                <ul class="list-group">
                  <li
                    class="list-group-item"
                    v-for="sufixe in sufixes"
                    :key="sufixe"
                  >
                  <div class="row">
                    <div class="col-md">
                      {{ sufixe }}
                    </div>
                    <div class="col-md text-end">
                      <button class="btn btn-info" v-on:click=deleteSufixe(sufixe)><span class="bi bi-trash icons"></span></button>
                    </div>
                  </div>
                  </li>
                </ul>
                <br />
                <div class="input-group">
                  <input
                    v-on:keyup.enter="addSufixe(sufixe)"
                    class="form-control"
                    v-model="sufixe"
                    type="text"
                    placeholder="Digite o sufixe"
                  />
                  <div class="input-group-append">
                    <div class="btn btn-info" v-on:click="addSufixe(sufixe)">
                      <span class="bi bi-plus icons"></span>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
        <br />
        <h5>
          Dominios
          <span class="badge bg-info icons"> {{ domains.length }}</span>
        </h5>
        <div class="card">
          <div class="card-body">
            <ul class="list-group">
              <li
                class="list-group-item"
                v-for="domain in domains"
                :key="domain"
              >
               
                <div class="row">
                  <div class="col-md">
                     {{ domain }}
                  </div>
                  <div class="col-md text-end">
                    <button class="btn btn-info"><span class="bi bi-cart-plus icons"></span></button>
                  </div>
                </div>
              </li>
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
      prefixe: '',
      sufixe: '',
      prefixes: ["Air", "Jet", "Flight"],
      sufixes: ["Hub", "Station", "Mart"],
      domains: [
        "AirHub",
        "AirStation",
        "AirMart",
        "JetHut",
        "JetStation",
        "JetMart",
        "FlightHub",
        "FlightStation",
        "FlightMart",
      ],
    };
  },
  methods: {

    addPrefixe(prefixe) {
      this.prefixes.push(prefixe);
      this.prefixe = '';
      this.generate();
    },
    deletePrefixe(prefixe){
      this.prefixes.splice(this.prefixes.indexOf(prefixe), 1);
      this.generate();
    },

    addSufixe(sufixe) {
      this.sufixes.push(sufixe);
      this.sufixe = '';
      this.generate();
    },
    deleteSufixe(sufixe) {
      this.sufixes.splice(this.sufixes.indexOf(sufixe), 1);
      this.generate();
    },

    generate(){
      this.domains = [];
      for(const prefixe of this.prefixes) {
        for(const sufixe of this.sufixes) {
          this.domains.push(prefixe + sufixe)
        }
      }
    }
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
