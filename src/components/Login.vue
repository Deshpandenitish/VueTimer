<template>
    <div class="backdrop" @click.self="closemodal">
        <div class="modal" :class="{sale:theme==='sale'}">
            <slot>Default</slot>
            <div class="actions">
                <slot name="links"></slot>
            </div>
        </div>
    </div>
</template>

<script>
import { onMounted } from 'vue';
 export default{
    props:['header','text','theme'],
    setup(props){
        onMounted(()=>{
            console.log('theme',props.theme);
        });
        return {
            header:props.header,
            text:props.text,
            theme:props.theme
        }
    },
    methods:{
        closemodal(){
            this.$emit('close');
        }
    }
 }
</script>

<style>
    .modal {
        width: 400px; /* Full width */
        padding:20px;
        margin: 100px auto;
        background: white;
        border-radius: 10px;
    }
    .backdrop{
        top: 0;
        position: fixed;
        background:rgba(0,0,0,0.5);
        width:100%;
        height: 100%;
    }
    .modal h1{
        color: aquamarine;
        border: 0;
        padding: 0;
    }
    .modal p{
        font-style: normal;
    }
    .modal.sale{
        background: crimson;
        color: white;
    }
    .modal.sale h1{
        color: white;
    }
    .modal.actions{
        text-align: center;
        margin: 30px 0 10px 0;
        color: #333;
    }
    .modal.actions a{
        color: #333;
        border-radius: 4px;
        margin-right: 10px;
        padding: 8px;
        border: 1px solid #eee;
        text-decoration: none;
        margin:10px;
    }
</style>