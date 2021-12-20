<template>
  <div>
    <h5>
      {{ title }}
      <span class="badge bg-info icons">{{ items.length }}</span>
    </h5>
    <div class="card">
      <div class="card-body">
        <ul class="list-group">
          <li
            class="list-group-item"
            v-for="item in items"
            :key="item"
          >
            <div class="row">
              <div class="col-md">
                {{ item }}
              </div>
              <div class="col-md text-end">
                <button class="btn btn-info" @click="deleteItem(item)">
                  <span class="bi bi-trash icons"></span>
                </button>
              </div>
            </div>
          </li>
        </ul>
        <br />
        <div class="input-group">
          <input
            v-on:keyup.enter="addItem(item)"
            type="text"
            v-model="item"
            class="form-control"
            placeholder= "Digite o item"
          />
          <div class="input-group-append">
            <div class="btn btn-info" @click="addItem(item)">
              <span class="bi bi-plus icons"></span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "AppItemList",
  props: ["items", "title"],
  data() {
    return {
      item: ''
    }
  },
  methods: {
    addItem(item) {
      this.$emit("addItem", item);
      this.item = '';

    },
    deleteItem(item) {
      this.$emit("deleteItem", item);
    }
  }
};
</script>

<style scoped>
</style>
