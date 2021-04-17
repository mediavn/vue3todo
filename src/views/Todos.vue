<template>

 <div class="container"> 
   <nav class="breadcrumb" aria-label="breadcrumbs">
      <ul>
          <li><a href="../">Home</a></li>
                 
          <li class="is-active"><a href="#" aria-current="page">Todos</a></li>
      </ul>
  </nav>
  
    <div class="columns">
      <div class="column is-9">
        <div class="card events-card">
          <header class="card-header">
              <p class="card-header-title">
                  Todos
              </p>
              <a href="#" class="card-header-icon" aria-label="more options">
                  <span class="icon">
                  <i class="fa fa-angle-down" aria-hidden="true"></i>
                  </span>
              </a>
          </header>
          <div class="content">
            <table class="table is-fullwidth is-striped">
               <tbody>
                    <tr v-for="(todo, index) in todos" :key="index" 
                    :class="{'has-background-success-light':todo.done}">
                        <td width="5%"><i class="fa fa-bell-o"></i></td>
                        <td>
                          <p>
                            {{ todo.text }} <br/>{{ todo.createdAt.toString() }} 
                            <span class="level-right" style="float:right;">                                             
                              <button 
                                    v-if="!todo.done" 
                                    @click="markAsDone(index)"
                                    class="button is-primary is-small" title="Mark as done">Done</button>
                              <button 
                                    v-else
                                    @click="markAsUndone(index)"
                                    class="button is-link is-small" title="Mark as undone">Undone</button>
                              <button
                                    @click="removeTodo(index)"
                                     class="button is-danger is-small" title="Remove to do">Remove </button>
                            </span>
                          </p>
                          
                        </td>                        
                    </tr>
                    <tr>
                      <td>
                        <p v-if="todos.length===0">You dont have new task todo</p>
                      </td>
                    </tr>
               </tbody>
                        
            </table>
            
          </div>
        </div>


        
      </div>
      
      
        <div class="column is-3">
          <div class="card">
            <header class="card-header">
                <p class="card-header-title">
                   Add a todo
                </p>
            </header>
            <div class="card-content">
                <div class="content">
                    <div class="control has-icons-left has-icons-right">
                        <input v-model="todoText" @keydown.enter="addTodo" class="input is-normal" type="text" placeholder="Text input">
                    </div>
                </div>
            </div>

          </div>
                        
            
        </div> 
    </div>   
</div>
</template>

<style lang="scss">
  @import "~bulma/css/bulma.css";
</style>
<script>
import { defineComponent, reactive, ref } from "vue";

export default defineComponent ({
  setup(){
    const todos = reactive([]);
    const todoText = ref(" ");

    function addTodo(){
      todos.unshift({
        text: todoText.value,
        createdAt: new Date(),
        done:false,

      });
      todoText.value="";
    }
    function markAsDone(index){
      todos[index].done = true;
    }
    function markAsUndone(index){
      todos[index].done=false;
    }
    function removeTodo(index){
      if(!confirm("Are you sure!")){
        return;
      }
      todos.splice(index,1);
    }
    return{
      todos,
      todoText,
      addTodo,
      markAsDone,
      markAsUndone,
      removeTodo,
    }
  }
})
</script>
