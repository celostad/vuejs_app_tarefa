<template>
    <div id="ctask">
        
       <form @submit.prevent="addItem" >
           <input
           type="text"
           placeholder="Tarefa de hoje?"
           v-model="tarefa"
           />
           <button type="submit">Adicionar</button>
       </form>

       <ItemTask :lista="tarefas" :delete="deleteTask" />

       <span v-show="tarefas.length > 0">
           Você tem <strong :class="{pend: pendente}" >{{tarefas.length}}</strong> tarefas pendentes.
       </span>

    </div>
</template>


<script>
import ItemTask from './ItemTask';
export default {
    name: 'CTask',
    components:{
        ItemTask
    },
    data(){
        return{
            tarefa: '',
            tarefas: [],
            pendente: false
        }
    },
    methods:{
        addItem(){
           if(this.tarefa !== ''){
               this.tarefas.push({
                   text: this.tarefa,
                   key: Date.now(),
               });
           }else{
               alert('Digite uma tarefa..');
               return;
           }

            this.tarefa = '';
            console.log(this.tarefas);

        },
        deleteTask(key){
           let filtro = this.tarefas.filter( (item) => {
              return (item.key !== key);
           });

           return this.tarefas = filtro;
        }
    },
    watch:{
        tarefas:{
            deep: true,
            handler(){
                localStorage.setItem('tasks', JSON.stringify(this.tarefas));
                this.tarefas.length > 4 ? this.pendente = true : this.pendente = false;             
            }
        }
    },
    created(){ // É chamado automaticamente após a instancia do vuejs ser criada..
        const minhaLista = localStorage.getItem('tasks');
        this.tarefas = JSON.parse(minhaLista) || [];
    }
}
</script>

<style scoped>
    #ctask{
        max-width: 700px;
        background: #FFF;
        border-radius: 4px;
        padding: 20px;
        margin: 20px auto;
        box-shadow: 0 0 20px rgba(0,0,0, 0.3);
    }

    form{
        margin-top: 30px;
        display: flex;
        flex-direction: row;
    }

    form button{
        cursor: pointer;
        background: #0f5959;
        border:0;
        border-radius: 4px;
        margin-left: 10px;
        padding: 0 15px;
        display: flex;
        justify-content: center;
        align-items: center;
        color: #FFF;
    }

    input{
      flex:1;  
      border: 1px solid #eee;
      padding: 6px 10px;
      border-radius: 4px;
      font-size: 14px;
      outline: none;
    }

    .pend{
       color: #FF0000; 
    }
</style>