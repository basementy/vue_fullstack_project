<template>
  <div>
    <h5>
      {{ title }}
      <span class="badge badge-info">{{ items.length }}</span>
    </h5>
    <div class="card">
      <div class="card-body">
        <ul class="list-group">
          <li class="list-group-item" v-for="item in items" :key="item">
            <div class="row">
              <div class="col">{{ item }}</div>
              <div class="col text-right">
                <button class="btn btn-info" @click="deleteItem(item)">
                  <span class="fa fa-trash"></span>
                </button>
              </div>
            </div>
          </li>
        </ul>
        <br />
        <div class="input-group">
          <input
            v-model="item"
            type="text"
            placeholder="Digito o prefixo"
            class="form-control"
            @keyup.enter="addItem(item)"
          />
          <div class="input-group-append">
            <button class="btn btn-info" @click="addItem(item)">
              <span class="fa fa-plus"></span>
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "AppItemList",
  props: ["title", "items"],
  data: () => ({
    item: ""
  }),

  methods: {
    addItem(item) {
      this.$emit("addItem", item);
      this.item = "";
    },

    deleteItem(item) {
      this.$emit("deleteItem", item);
    }
  }
};
</script>

<style scoped>
</style>