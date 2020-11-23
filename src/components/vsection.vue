<template>
    <section>
        <h2>
            正在进行
            <span v-text="todolist.length"></span>
        </h2>
        <ol>
            <li v-for="(item,index) in todolist" :key="item">
                {{item}}
                <el-button @click="complete(index)" type="success" icon="el-icon-check" circle></el-button>
                <el-button @click="deleteTodo(index)" type="info" icon="el-icon-delete" circle></el-button>
            </li>
        </ol>
        <h2>
            已经完成
            <span v-text="completedlist.length"></span>
        </h2>
        <ol>
            <li v-for="(item,index) in completedlist" :key="item">
                {{item}}
                <el-button @click="incomplete(index)" type="danger" icon="el-icon-close" circle></el-button>
                <el-button @click="deleteCompleted(index)" type="info" icon="el-icon-delete" circle></el-button>
            </li>
        </ol>
    </section>
</template>
<script>
import bus from './eventBus.js'

export default {
    name:'vsection',
    data:function() {
        return {
            todolist:[],
            completedlist:[]
        }
    },
    mounted(){
        bus.$on('add',list=>{
            this.todolist=list
        })
    },
    methods:{
        complete:function(index){
            this.completedlist.push(this.todolist[index])
            this.todolist.splice(index,1);
        },
        incomplete:function(index){
            this.todolist.push(this.completedlist[index])
            this.completedlist.splice(index,1)
        },
        deleteTodo:function(index){
            this.todolist.splice(index,1);
        },
        deleteCompleted:function(index){
            this.completedlist.splice(index,1);
        }
    }
}
</script>
<style scoped>
    section{
        width: 600px;
        padding: 0 10px;
        margin: 0 auto;
    }
    h2{
        position: relative;
    }
    ol{
        padding-left: 0;
    }
    span{
        position: absolute;
        right: 5px;
        top: 2px;
        padding:0 5px;
        height: 20px;
        border-radius: 20px;
        line-height: 22px;
        text-align: center;
        font-size: 14px;
        color: #666;
        background-color: #E6E6FA;
    }
    li{
        list-style: none;
        height: 32px;
        line-height: 32px;
        background-color: #fff;
        position: relative;
        margin-bottom: 10px;
        padding: 0 45px;
        border-radius: 5px;
    }
    button{
        padding:4px !important;
        position: absolute;
        top: 4px;
    }
    button:nth-child(1){
        right: 40px;
    }
    button:nth-child(2){
        right: 10px;
    }
</style>