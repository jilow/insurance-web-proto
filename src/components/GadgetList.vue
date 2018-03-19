<template>
  <div class="gadgetList">
    <el-row :gutter="20">
      <div v-for="(model) in models" :key="model.name">
        <el-col :span="8">
          <el-card class="card">
            <img :src="model.image" slot="header" class="image">
            <div class="body">
              <span class="title">{{ model.name }}</span>
              <el-button class="button" type="primary">Go</el-button>
            </div>
          </el-card>
        </el-col>
      </div>
    </el-row>
  </div>
</template>

<script>

const models = [
  {
    "name": "iPhone 7 32GB LTE",
    "image": require("../assets/iphone-7.png"),
    "quote": {
      "quote_package_id": "acedfc65-b214-411e-856a-52f202541a72",
      "package_name": "Theft + comprehensive",
      "sum_assured": 1199900,
      "base_premium": 16999,
      "suggested_premium": 21248,
      "module": {
        "type": "root_gadgets",
        "make": "Apple",
        "model": "iPhone 7 32GB LTE"
      },
      "created_at": "2018-03-18T13:22:28Z"
    }
  },
  {
    "name": "Galaxy S8 64GB LTE",
    "image": require("../assets/galaxy-s8.png"),
    "quote": {
      "quote_package_id": "bb6c1952-5c4e-4e5a-83b7-199b6ccdb2d1",
      "package_name": "Theft + comprehensive",
      "sum_assured": 1599900,
      "base_premium": 22665,
      "suggested_premium": 28331,
      "module": {
        "type": "root_gadgets",
        "make": "Samsung",
        "model": "Galaxy S8 64GB LTE"
      },
      "created_at": "2018-03-18T13:24:31Z"
    }
  },
]

export default {
  name: 'GadgetList',
  data() {
    return {
      models: models
    }
  },
  methods: {
  }
}
</script>

<style scoped>

.card {

}

.card .image {
  display: flex;
  margin: 0 auto;
}

.card .title {
  font-weight: 700;
}

.card .body {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

</style>
