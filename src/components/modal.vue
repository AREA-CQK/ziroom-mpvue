<template>
    <div v-if="show">
        <div>{{text}}</div>
        <div>
            <div @click="cancelHandle">取消</div>
            <div @click="commitHandle">确定</div>
        </div>
    </div>
</template>
<script>
    export default {
        data () {
            return {
                
            }
        },
        props:{
            text:{
                type:String
            },
            show:{
                type:Boolean
            }
        },
        methods:{
            commitHandle(){
                this.$emit('commit');
            },
            cancelHandle(){
                this.$emit('cancel');
            }
        },
        created () {

        }
    }
</script>
<style>

</style>
