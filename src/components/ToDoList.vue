<template>
  <div class="app">
    <div class="container">
      <h1>TODO List</h1>
      <input 
        class="input"  
        v-model="newToDo" 
      />

      <button class="add-button" v-on:click="add()">Add</button>

      <ul style="list-style-type: none;">
        <li v-for="(todo,i) in existingToDo" :key="todo.id">
          <span>
            {{ i + 1 }}: {{ todo.text }}
          </span>
          <button class="delete-button" @click="deleteToDo(i)">Del</button>
        </li>
      </ul>

    </div>
  </div>
</template>

<script>
export default {
  name: 'todolist',
  data (){
    return{
      newToDo: '',
      existingToDo:[
        // {text: 'Teste 1', id:0},
        // {text: 'Teste 2', id:1},
        // {text: 'Teste 3', id:2}
      ]
    }
  },
  methods:{
    add(){
      this.existingToDo.push({
        text: this.newToDo,
        id: new Date().valueOf()
      }),
      this.newToDo = ''
    },
    deleteToDo(i){
      this.existingToDo.splice(i, 1)
    }
  }
}
</script>

<style scoped>

.input{
  margin: 5px;
}
li{
  margin: 5px;
}
span{
  margin: 5px;
}
button{
  border-radius: 5px;
}
</style>
