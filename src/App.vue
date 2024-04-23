<template>

  <div class="container mt-5">
      <div class="row mb-4">
        <div class="col form-inline">
          <b-form-input v-model="newTask" placeholder="Enter Task" @keyup.enter="add"></b-form-input> 
          <b-form-input v-model="newTaskText" placeholder="Enter Additional Text"></b-form-input>
          <b-button class="ml-2" variant="primary" @click="add">Add</b-button>
        </div>
      </div>

      <div class="row">
        <div class="col-md-3">
          <div class="p-2 alert custom-alert-1">
            <h3>Backlog</h3>
            <draggable class="list-group kanban-column" :list="arrBacklog" group="tasks">
              <div class="list-group-item" v-for="task in arrBacklog" :key="task.id">
                {{ task.name }} - {{ task.text }}
              </div>
            </draggable>
          </div>
        </div>

        <div class="col-md-3">
          <div class="p-2 alert custom-alert-2">
            <h3>In progress</h3>
            <draggable class="list-group kanban-column" :list="arrInProgress" group="tasks">
              <div class="list-group-item" v-for="task in arrInProgress" :key="task.id">
                {{ task.name }} - {{ task.text }}
              </div>
            </draggable>
          </div>
        </div>

        <div class="col-md-3">
          <div class="p-2 alert custom-alert-3">
            <h3>Tested</h3>
            <draggable class="list-group kanban-column" :list="arrTested" group="tasks">
              <div class="list-group-item" v-for="task in arrTested" :key="task.id">
                {{ task.name }} - {{ task.text }}
              </div>
            </draggable>
          </div>
        </div>

        <div class="col-md-3">
          <div class="p-2 alert custom-alert-4">
            <h3>Done</h3>
            <draggable class="list-group kanban-column" :list="arrDone" group="tasks">
              <div class="list-group-item" v-for="task in arrDone" :key="task.id">
                {{ task.name }} - {{ task.text }}
              </div>
            </draggable>
          </div>
        </div>
      </div>
  </div>

</template>

<script>
import draggable from "vuedraggable";

export default {
  name: 'App',
  components: {
   draggable
  },
  data( ){
    return {
      newTask: "",
      newTaskText: "",
      arrBacklog: [
        { id: 1, name: "Code sign Up Page", text: "" },
      ],
      arrInProgress: [
        { id: 2, name: "Test Dashboard", text: "" },
      ],
      arrTested: [
        { id: 3, name: "Style registration", text: "" },
      ],
      arrDone: [
        { id: 4, name: "Help with Designs", text: "" },
      ]
    }
  },
  methods:{
    add(){
      if(this.newTask) {
        this.arrBacklog.push({ id: this.arrBacklog.length + 1, name: this.newTask, text: this.newTaskText }),
        this.newTask = "";
        this.newTaskText = "";
      }
    }
  }
}
</script>

<style>
.kanban-column {
  min-height: 300px;
}

.custom-alert-1 {
  background-color: rgba(240,185,180,255)
}

.custom-alert-2 {
  background-color: rgba(254,236,190,255)
}

.custom-alert-3 {
  background-color: rgba(255,249,243,255)
}

.custom-alert-4 {
  background-color: rgba(135,112,112,255)
}



</style>
