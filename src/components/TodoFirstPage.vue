<template>
  <div class="background-container">
    <h1 class="todo-heading">ToDo App</h1>
    <div class="row justify-center">
      <input type="text" placeholder="Enter todo item" class="input-item" v-model="newItem"/>
    </div>
    <div class="button-container row justify-end">
        <q-btn color="green" label="ADD" class="q-px-md" @click="addItem"/>
    </div>
    <div class="q-pa-md">
      <q-table
       :columns="columns"
       row-key="name"
    ></q-table>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      newItem: '',
      items: []
    }
  },
  methods: {
    addItem () {
    }
  },
  columns: [
    {
      required: true,
      name: 'name',
      label: 'Sl.No',
      align: 'left'
    }
  ]
}
</script>

<style>
.todo-heading{
    font-size: 20px;
    font-weight: bold;
    text-align: center;
    line-height: 3rem;
}
.input-item{
    width: 1000px;
    border-color: rgb(21, 160, 206);
    margin-top: 10px;
    padding: 10px;
}
.button-container{
    padding: 15px;
    margin-right: 250px;
}
</style>
