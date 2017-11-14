<template>
    <div class="bh-ddb">
        <div v-for="(item,index) in options" class="bh-ddb-item" :class="{'bh-ddb-item-selected':item.active}" v-bind:style="{ width: itemWidth}" @click="setSelected(item,index)">
            <label>
                {{item.text}}
                <i class="bh-ddb-i" :class="{'bh-ddb-i-default':!item.active,'bh-ddb-i-selected':item.active,}"></i>
            </label>
        </div>
    </div>
</template>
<style>
.bh-ddb {
    overflow: auto;
    padding: 10px 0;
    border-bottom: solid 0.5px #ddd;
}
.bh-ddb-item {
    float:left;
    /* text-align: center; */
    border-right:solid 0.5px rgba(0,0,0,0.25);
}
.bh-ddb .bh-ddb-item:last-child {
    border-right:none;
}
.bh-ddb-item label {
    position: relative;
    color:#999;
    display: block;
    /* width: 100px; */
    width: 50px;
    margin: 0 auto;
}
.bh-ddb-item.bh-ddb-item-selected label {
    color:#38CDC1 !important;
}
.bh-ddb-i {
    position: absolute;
    top: 8px;
    right: 0px;
}
.bh-ddb-i-default {
    width: 0;
    height: 0;
    border-left: 5px solid transparent;
    border-right: 5px solid transparent;
    border-top: 6px solid #BFC3C7;
}
.bh-ddb-i-selected {
    width: 0;
    height: 0;
    border-left: 5px solid transparent;
    border-right: 5px solid transparent;
    border-bottom: 6px solid #38CDC1;
}
</style>
<script>
    export default {
        data () {
            return {
                itemWidth:''
            }
        },
        props:{
            options:Array
        },
        components:{
            
        },
        created() {
            this.itemWidth = (100 / this.options.length) + '%';
        },
        methods:{
            setSelected:function(param,index){
                //consoel.log('2222222222222222')
                this.$nextTick(function () {
    　　　　　　　　this.options.forEach(function (item) {
    　　　　　　　　　　Vue.set(item,'active',false);
    　　　　　　　　});
    　　　　　　　　Vue.set(param,'active',true);
                   Vue.set(param,'index',index);
                  this.$emit('dropDownButtons',param);
    　　　　　　});
            }
        }
    }
</script>