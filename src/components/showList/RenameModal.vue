<template>
  <div
      class="modal fade pt-5"
      id="renameModal"
      tabindex="-1"
      aria-labelledby="exampleModalLabel"
      aria-hidden="true"
  >
    <div class="modal-dialog">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title" id="exampleModalLabel">Rename</h5>
          <button
              type="button"
              class="btn-close"
              data-bs-dismiss="modal"
              aria-label="Close"
          ></button>
        </div>
        <div class="modal-body">
          <input type="text" class="inputList" v-model="listName"/>
        </div>
        <div class="modal-footer">
          <button type="button" class="btn btn-success" @click="handleCreateList" data-dismiss="modal">OK</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "CreateListModal",
  data() {
    return {
      listName: "",
    };
  },
  methods: {
    handleCreateList(){
      console.log(this.listName);
      this.listName = "";
    }
  }
};
</script>

<style scoped>
.inputList {
  border: none;
  border-bottom: 1px solid rgb(80, 82, 75);
  padding: 5px 10px;
  outline: none;
  width: 100%;
}

.inputList:focus {
  border-bottom: 2px solid rgb(27, 219, 20);
}

.modal-dialog {
  height: 80% !important;
  padding-top: 10%;
}

.modal-content {
  min-height: 38% !important;
  overflow: visible;
}

.modal-body {
  height: 80%;
  overflow: auto;
}
</style>