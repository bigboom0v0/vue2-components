<template>
    <el-select
        v-model="modelValue"
        v-bind="$attrs"
        v-on="$listeners"
    >
        <el-option
            v-for="item in options"
            :key="item.value"
            :label="item.value"
            :value="item.value"
        />
    </el-select>
</template>
<script>
export default{
    name:"SearchFormSelect",
    model: {
        event: "change"
    },
    props:{
        value:{
            type:[String,Number,Boolean]
        },
        options:{
            type:Array,
            default:()=>[]
        }
    },
    computed:{
        modelValue:{
            get(){
                return this.value
            },
            set(value){
                // this.$emit('change',value)
            }
        }
    }
}
</script>