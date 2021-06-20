<template>
  <div id="app" class="container">
    
            
            <!-- <h1>Todo List</h1> -->
            <img src="http://todo-list.ch/wp-content/uploads/2016/10/logo_script_blue_00-1.png" alt="">


            <div v-if="!isEditing">

              <input type="text" v-model="todo" class="form-control" required><br>
              <input type="submit" value="Add" @click="storeTodo" class="btn btn-primary">

            </div>

            <div v-else>
                <input type="text" v-model="todo" class="form-control" required><br>
                <input type="submit" value="Update" @click="updateTodo" class="btn btn-success">
            </div>
            
            <br><br>

            <ol>

                <li v-for="(todo,i) in todos" :key="i"> 
                  
                    {{todo}} 

                    <button @click="editTodo(i, todo)" class="btn btn-success" style="margin-left: 30px;">Edit</button>
                    <button @click="removeTodo(i)" class="btn btn-danger" style="margin-left: 5px;">Delete</button>

                </li>
            </ol>

  </div>
</template>

<script>

export default {
  name: 'App',

  data: function (){
    
    return{
      
      isEditing : false,

      todo:'',

      todos:[],

      selectedTodo: null


    }
    
  },

  methods:{

      storeTodo() {
          this.todos.push(this.todo)
          this.todo = ''
      },
      removeTodo(index) {
          this.todos.splice(index, 1)
      },

      updateTodo() {
          this.todos.splice(this.selectedIndex , 1 , this.todo)
          this.todo = ''
          this.isEditing = false
      },

      editTodo(index, todo) {
          this.isEditing = true
          this.todo = todo
          this.selectedIndex = index
      },


  }

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.container {
    max-width: 960px;
    margin: 0 auto;
}
h1 {
  padding-top: 40px;
}

</style>
