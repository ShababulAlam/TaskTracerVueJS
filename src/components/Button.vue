<template>
    <button @click="onClick()" class="btn" v-bind:style="{ background: color}" >{{text}}</button>
</template>

<script>
export default {
    name: 'Button',
    props: {
        text: String,
        color: String
    },
    methods:{
        onclick(){
            console.log('Click')
        }
    }
}
</script>