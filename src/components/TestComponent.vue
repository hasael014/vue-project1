<template>
    {{ ids }} de {{ author }} con {{ subject }}
    <div>
        <button @click="add" >sumar el id</button>
    </div>
    <p>{{ msj }}</p>
    <p v-text="producto" ></p>
    <input type="text" v-model.trim="ids">
    <div v-show="false" v-for="(item, index) in lang" :key="index" >{{ item }} . {{ index }}</div>
    <div v-show="false" v-for="(char, index) in 'Asaelhb'" :key="index" >{{ char }}</div>
    <div v-show="false" v-for="(item, name, index) in producto" :key="index" >{{ index }} . {{ name }} => {{ item }}</div>
    <div v-show="false" v-for="nu in 5" :key="nu" >{{ nu }}</div>
</template>

<script>
import { ref, reactive, onMounted, getCurrentInstance } from 'vue';
export default {
    name: "name_test",
    props: {
        id : {
            type: Number,
            default: 0,
            required: false
        },
        price :{
            type: Number,
            default: 10,
            required: false
        },
        name: {
            type: String,
            required: false
        },
        author: String,
        subject : String
    },
    // data(){
    //     return{
    //         pruebita : this.id,
    //         msj : "nada"
    //     }
    // },
    // methods:{
    //     meth(){
    //         this.pruebita--;
    //     }
    // },
    setup(props, context){
        const name = getCurrentInstance().ctx.$options.name;
        // let test = name+" tiene " + props.id

        const producto = reactive({
            name: props.name,
            price: props.price
        })

        console.log("prueba del DOOM")

        const ids = ref(props.id)
        const add = ()=>{
            ids.value++;
            producto.price++
        }

        const lang = ["html", "css", "Js", "Terminal"]

        return {
            lang,
            producto,
            ids,
            add
        }
    }    
}
</script>