<template>
  <div>
    <div id="main">
      <div class="container">
        <div class="row">
          <div class="col-md">
            <AppItemList
              :items="prefixes"
              title="Prefixo"
              @addItem="addPrefixe"
              @deleteItem="deletePrefixe"
            ></AppItemList>
          </div>
          <div class="col-md">
            <AppItemList
              :items="sufixes"
              title="Sufixo"
              @addItem="addSufixe"
              @deleteItem="deleteSufixe"
            ></AppItemList>
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
                    <a
                      class="btn btn-info"
                      :href="domain.checkout"
                      target="_blank"
                    >
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
    <br />
  </div>
</template>

<script>
import bootstrap from "bootstrap/dist/css/bootstrap.css";

import AppItemList from "./AppItemList.vue";

export default {
  name: "App",

  components: {
    AppItemList,
  },

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
            checkout,
          });
        }
      }
      return domains;
    },
  },
};
</script>

<style>
</style>
