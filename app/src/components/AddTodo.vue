<template>
    <div>
        <form @submit="addTodo">
            <input type="text" v-model="title" name="title" placeholder="add Todo..."/>
            <input type="submit" value="Submit" class="btn"/>
        </form>
    </div>
</template>

<script>
    import { uuid } from 'vue-uuid';

    export default {
        name: "AddTodo",
        data(){
            return{
                title:""
            }
        },
        methods:{
            addTodo(e){
                console.log(uuid);
                e.preventDefault();
                const newTodo = {
                    id:uuid.v4(),
                    title:this.title,
                    completed:false
                };
                this.$emit("add-todo", newTodo);
                this.title="";
            }
        }
    }
</script>
<style scoped>
    form {
        display: flex;
        padding: 5px 5px;
    }
    input{
        flex: 10;
        padding: 5px;
    }
    input[type="submit"]{
        flex: 2;
    }
</style>