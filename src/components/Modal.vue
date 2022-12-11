<template>
    <div class="modal" @click.self="closeModal">
        <div class="popup" :class="{blue: theme === 'blue'}">
            <slot></slot>
            <slot name="links"></slot>
        </div>
    </div>
</template>

<script>
    export default{
        props:['model','text','theme'],
        methods:{
            closeModal(){
                this.$emit('close')
            }
        }
    }
</script>


<style>
.modal{
    width: 100vw;
    height: 40vh;
    display: flex;
    justify-content: center;

}
.popup{
    height: 200px;
    width: auto;
    background: gray;
    border-radius: 10px;
}
p{
    color: white;
}
.blue{
    color: aqua;
}
</style>