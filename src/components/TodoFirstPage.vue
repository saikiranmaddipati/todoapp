<template>
  <div class="background-container">
    <h1 class="todo-heading">ToDo App</h1>
    <div class="row justify-center">
      <input
        type="text"
        placeholder="Enter todo item"
        class="input-item"
        v-model="newItem"
      />
    </div>
    <div class="button-container row justify-end">
      <q-btn color="green" label="ADD" class="q-px-md" v-on:click="addItem" />
    </div>
    <div class="q-pa-md">
      <q-table :columns="columns" row-key="name" :data="data">
        <template v-slot:body-cell-actions="props">
          <q-td :props="props">
            <div class="q-pa-md q-gutter-sm">
              <q-btn label="Edit" color="green" @click="alert = true" />
              <q-btn :label="label" color="green" @click="toggleView" />
              <q-btn label="Delete" color="red" @click="prompt = true" />

              <q-dialog
                v-model="alert"
                v-for="(data, index) in data"
                :key="index"
              >
                <q-card>
                  <q-card-section style="min-width: 350px">
                    <div class="text-h6 center">Edit</div>
                  </q-card-section>

                  <q-card-section class="q-pt-none">
                    <input
                      placeholder="please Enter the Todo"
                      v-model="data.toDoItem"
                    />
                  </q-card-section>

                  <q-card-actions align="right">
                    <q-btn flat label="Save" color="green" v-close-popup />
                    <q-btn flat label="Cancel" v-close-popup />
                  </q-card-actions>
                </q-card>
              </q-dialog>

              <div>
                <q-dialog v-model="prompt" persistent>
                  <q-card style="min-width: 350px">
                    <q-card-section>
                      <div class="text-h6">Delete</div>
                    </q-card-section>

                    <q-card-section class="q-pt-none">
                      Are you sure you want to delete the item?
                    </q-card-section>

                    <q-card-actions align="right" class="text-primary">
                      <q-btn
                        flat
                        label="Delete"
                        color="red"
                        @click="onDelete()"
                        v-close-popup
                      ></q-btn>
                      <q-btn flat label="cancel" v-close-popup></q-btn>
                    </q-card-actions>
                  </q-card>
                </q-dialog>
              </div>
            </div>
          </q-td>
        </template>
      </q-table>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      newItem: '',
      alert: false,
      prompt: false,
      confirm: false,
      view: false,
      label: 'incomplete',
      data: [
        {
          slno: 1,
          toDoItem: 'learn javascript',
          status: 'pending',
          actions: ''
        }
      ],
      columns: [
        {
          name: 'name',
          label: 'slno',
          align: 'left',
          sortable: true,
          field: 'slno'
        },
        {
          name: 'ToDo item',
          align: 'center',
          label: 'ToDo Item',
          field: 'toDoItem',
          sortable: true
        },
        {
          name: 'Status',
          align: 'center',
          label: 'Status',
          field: 'status',
          sortable: true
        },
        { name: 'actions', align: 'center', label: 'Action' }
      ]
    }
  },
  methods: {
    addItem () {
      this.data.push({
        slno: this.data.length + 1,
        toDoItem: this.newItem,
        status: false,
        actions: ''
      })
      this.newItem = ''
    },
    onDelete () {
      this.data.pop()
    },
    toggleView () {
      this.view = !this.view

      if (this.view) {
        this.label = 'complete'
        this.data.status = 'Completed'
      } else {
        this.label = 'Incomplete'
        this.data.status = 'Pending'
      }
    }
  }
}
</script>

<style>
.todo-heading {
  font-size: 20px;
  font-weight: bold;
  text-align: center;
  line-height: 3rem;
}
.input-item {
  width: 1000px;
  border-color: rgb(21, 160, 206);
  margin-top: 10px;
  padding: 10px;
}
.button-container {
  padding: 15px;
  margin-right: 250px;
}
</style>
