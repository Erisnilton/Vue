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
                        <button
                          class="btn btn-info"
                          @click="deletePrefixe(prefixe)"
                        >
                          <span class="bi bi-trash icons"></span>
                        </button>
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
                    <div class="btn btn-info" @click="addPrefixe(prefixe)">
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
                        <button
                          class="btn btn-info"
                          @click="deleteSufixe(sufixe)"
                        >
                          <span class="bi bi-trash icons"></span>
                        </button>
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
                    <div class="btn btn-info" @click="addSufixe(sufixe)">
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
                :key="domain.name"
              >
                <div class="row">
                  <div class="col-md">
                    {{ domain.name }}
                  </div>
                  <div class="col-md text-end">
                    <a class="btn btn-info" :href= domain.checkout target="_blank">
                      <span class="bi bi-cart-plus icons"></span>
                    </a>
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
  data() {
    return {
      prefixe: "",
      sufixe: "",
      prefixes: ["Air", "Jet", "Flight"],
      sufixes: ["Hub", "Station", "Mart"],
    };
  },
  methods: {
    addPrefixe(prefixe) {
      if (prefixe != "") {
        this.prefixes.push(prefixe);
        this.prefixe = "";
      }
    },

    deletePrefixe(prefixe) {
      this.prefixes.splice(this.prefixes.indexOf(prefixe), 1);
    },

    addSufixe(sufixe) {
      if (sufixe != "") {
        this.sufixes.push(sufixe);
        this.sufixe = "";
      }
    },
    deleteSufixe(sufixe) {
      this.sufixes.splice(this.sufixes.indexOf(sufixe), 1);
    },
  },

  computed: {
    domains() {
      const domains = [];
      for (const prefixe of this.prefixes) {
        for (const sufixe of this.sufixes) {
          const name = prefixe + sufixe;
          const url = name.toLowerCase();
          const checkout = `https://checkout.hostgator.com.br/?a=add&sld=${url}&tld=.com.br&domaincycle=2&titanDomain=1&titanSource=1`;
          domains.push({
            name,
            checkout
          });
        }
      }
      return domains;
    },
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
