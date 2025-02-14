<template>
    <div>
        <!--        物料选择-->
        <MaterialSelect/>
        <div class="graph-view-wrapper">
            <el-button @click="save" class="save-btn">保存画布数据</el-button>
            <div id="editor" @drop="dropHandler" @dragover="dragoverHandler"></div>
        </div>
        <EditAttributes/>
    </div>
</template>
<script>
import { createEditor } from './editor';
import MaterialSelect from './components/MaterialSelect.vue';
import EditAttributes from './components/EditAttributes.vue';
import defaultGraphData from 'defaultGraphData.json';
import {createNode,getBoundingBox} from "./editor/utils";
import lodash from 'lodash'
export default {
    name:'EditorPage',
    components:{
        MaterialSelect,
        EditAttributes
    },
    data(){
        return {
            graphView:'',
            dataModel:'',
            selector:''
        }
    },
    mounted(){
        const {graphView,dataModel,selector} = createEditor('#editor',defaultGraphData);
        selector.addSelectChangeListener((selectedNodes)=>{
            this.$eventBus.$emit('nodeSelectedChange',selectedNodes)
        })
        this.graphView = graphView;
        this.dataModel = dataModel;
        this.selector = selector;
    },
    methods:{
        dragoverHandler(event){
            event.preventDefault();
        },
        dropHandler(event){},
        save(){}
    }
}
</script>

<style lang="less" scoped>

</style>
<style lang="less">
* {
    margin: 0;
    padding: 0;
}
</style>