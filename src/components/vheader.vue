<template>
    <header>
        <section>
            <div>
                <label for="todo">ToDoList</label>
                <el-input @keyup.enter.native="add" size="mini" v-model="input" type="text" id="todo" placeholder="添加Todo"></el-input>
            </div>
        </section>
    </header>
</template>
<script>
import bus from './eventBus.js'

export default {
    name:'vheader',
    data:function() {
        return {
            list:[],
            input: '',
            tips:false
        }
    },
    methods:{
        add:function(){
            if (this.input!=""){
                this.list.push(this.input)
                this.input=''
                bus.$emit('add',this.list)
            }
            else{
                const h = this.$createElement;
                this.$notify.error({
                title: '输入值为空',
                message: h('b', { style: 'color: red'}, '请重新输入')
        });
            }
        },
    }
}
</script>
<style scoped>
    header{
        height: 50px;
        background: rgba(47, 47, 47, 0.98);
    }
    section{
        margin: 0 auto;
        width:600px;
        padding:0 10px;
    }
    label{
        font-size: 24px;
        line-height: 50px;
        color: #DDD;
    }
    .el-input{
        margin-left:120px ;
        width: 360px;
    }
</style>