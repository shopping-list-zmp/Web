<template>
  <div class="modal fade" id="exampleModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
  <div class="modal-dialog modal-lg">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title" id="exampleModalLabel">Adding a Product</h5>
        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
      </div>
      <div class="modal-body">
        <!--  -->
        <div class="row">
  <div class="col-sm-6">
    <div class="card">
      <div class="card-body">
        <h5 class="card-title">Add Categories</h5>
        <div class="input-group mb-3">
          <span class="input-group-text" id="basic-addon1"><i class="fab fa-cuttlefish"></i></span>
          <input type="text" class="form-control" placeholder="category" v-model="category">
        </div>
        <a href="#" class="btn btn-primary d-flex justify-content-center" @click="addCategory">Add</a>
      </div>
    </div>
  </div>
  <div class="col-sm-6">
    <div class="card">
      <div class="card-body">
        <h5 class="card-title">Add product</h5>
        <select class="form-select" aria-label="Default select example" @change="setProductId($event)">
          <option selected disabled>Select categories</option>
          <option v-for="(item, i) in categories" :key="i" :value="item.id">
          {{ item.name }}
          </option>
        </select>
        <div class="input-group mt-3">
          <span class="input-group-text" id="basic-addon1"><i class="fab fa-product-hunt"></i></span>
          <input type="text" class="form-control" placeholder="protuct name" v-model.trim="name">
        </div>
        <a href="#" class="btn btn-primary mt-3 d-flex justify-content-center" @click="addProduct">Add</a>
      </div>
    </div>
  </div>
</div>
        <!--  -->
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-bs-dismiss="modal">Close</button>
      </div>
    </div>
  </div>
</div>
</template>

<script>
import AlertSuccess from '../Alerts/AlertSuccess'
export default {
  name: "Basket Modal",
  data(){
    return {
      category: "",
      categoryId: null,
      name: ""
    }
  },
  methods:{
    addCategory(){
      if(this.category){
        this.$store.dispatch("createCategory",{name: this.category})
        AlertSuccess.successAlert('Category has been added');
        this.getCategories();
      }
    },
    addProduct(){
      if(this.categoryId,this.name){
        this.$store.dispatch("createProduct",{name: this.name, category_id: this.categoryId})
        AlertSuccess.successAlert('Product has been added');
        this.$store.dispatch("products");
      }
    },
    setProductId(event){
      this.categoryId = event.target.value;
    },
    getCategories() {
      this.$store.dispatch("getCategories");
    },
  },
  computed: {
      categories(){
        return this.$store.getters.categories;
      }
    },
    created() {
      this.getCategories()
    },
}
</script>

<style scoped>
.modal-dialog {
  height: 100vh !important;
  display: flex;
}

.modal-content {
  margin: auto !important;
  height: fit-content !important;
}
</style>