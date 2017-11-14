<template>
    <div>
        <div class="bh-ddm" :style="{'maxHeight':maxHeight,zIndex:10,'display':isShowMenu}">
            <div v-if="type === 1" class="bh-ddm-one">
                <div v-for="(item,index) in options" class="bh-ddm-item" :class="{'bh-ddm-item-selected':item.active}" @click="setSelected(item,index)">
                    {{item.text}}
                    <i class="bh-ddm-item-img" v-if="item.active"></i>
                </div>
            </div>
            <div v-else-if="type === 2" class="bh-ddm-two">
                <div class="bh-ddm-lv1-container">
                    <div v-for="(item,index) in options" class="bh-ddm-lv1-item" :class="{'bh-ddm-lv1-item-selected':item.active}" @click="setSelected(item,index)">
                        {{item.text}}
                    </div>
                </div>
                <div class="bh-ddm-lv2-container">
                    <div v-for="(item,index) in subOptions" class="bh-ddm-lv2-item" :class="{'bh-ddm-lv2-item-selected':item.active}" @click="setLv2Selected(item,index)">
                        {{item.text}}
                        <i class="bh-ddm-item-img" v-if="item.active"></i>
                    </div>
                </div>   
            </div>
            <div v-else-if="type === 3" class="bh-ddm-three">
                <div class="bh-ddm-lv1-container">
                    <div v-for="(item,index) in options" class="bh-ddm-lv1-item" :class="{'bh-ddm-lv1-item-selected':item.active}" @click="setSelected(item,index)">
                        {{item.text}}
                    </div>
                </div>
                <div class="bh-ddm-lv2-container">
                    <div v-for="(item,index) in subOptions" class="bh-ddm-lv2-item" :class="{'bh-ddm-lv2-item-selected':item.active}" @click="setLv2Selected(item,index)">
                        {{item.text}}
                    </div>
                </div>
                <div class="bh-ddm-lv3-container">
                    <div v-for="(item,index) in grandSonOptions" class="bh-ddm-lv3-item" :class="{'bh-ddm-lv3-item-selected':item.active}" @click="setLv3Selected(item,index)">
                        {{item.text}}
                        <i class="bh-ddm-item-img" v-if="item.active"></i>
                    </div>
                </div>   
            </div>
        </div>
        <!-- 遮罩层 -->
        <div class="bh-ddm-shadow" @click="cancelShadow" :style="{'display':isShowShadow}"></div>
    </div>
</template>
<style>
.bh-ddm {
  background-color: #fff;
  border-bottom: solid 1px #eee;
  /* max-height:440px; */
  overflow: auto;
  position: absolute;
  width: 100%;
}
.bh-ddm-item {
  /* height:44px; */
  text-align: left;
  padding: 11px 16px;
  border-bottom: solid 0.5px #eee;
}
.bh-ddm-item-img {
  float: right;
  width: 24px;
  height: 24px;
  position: relative;
}
.bh-ddm-item-img:after {
  content: "\00a0";
  display: inline-block;
  border: 2px solid #38cdc1;
  border-top-width: 0;
  border-right-width: 0;
  width: 18px;
  height: 8px;
  -webkit-transform: rotate(-50deg);
  position: absolute;
  top: 6px;
  left: 4px;
}
.bh-ddm-item-selected {
  color: #38cdc1;
}
.bh-ddm-lv1-container {
  float: left;
  width: 30%;
  background-color: #f4f4f4;
  border-right: solid 0.5px rgba(0, 0, 0, 0.25);
}
.bh-ddm-two {
  overflow: auto;
  display: flex;
}
.bh-ddm-two .bh-ddm-lv2-container {
  float: right;
  width: 70%;
}
.bh-ddm-three {
  overflow: auto;
  display: flex;
}
.bh-ddm-three .bh-ddm-lv2-container {
  float: left;
  width: 30%;
}
.bh-ddm-three .bh-ddm-lv3-container {
  float: right;
  width: 40%;
  border-left: solid 0.5px rgba(0, 0, 0, 0.1);
}
.bh-ddm-lv1-item {
  padding: 11px 20px;
  /* border-right:solid 0.5px rgba(0,0,0,0.25); */
}
.bh-ddm-lv2-item {
  padding: 11px 20px;
}
.bh-ddm-lv3-item {
  padding: 11px 20px;
}
.bh-ddm-lv1-item.bh-ddm-lv1-item-selected {
  background-color: #fff;
  border-top: solid 0.5px rgba(0, 0, 0, 0.25);
  border-bottom: solid 0.5px rgba(0, 0, 0, 0.25);
  border-right: solid 0.5px #fff;
  width: calc(100% + 1px);
}
.bh-ddm-lv1-container .bh-ddm-lv1-item:first-child.bh-ddm-lv1-item-selected {
  border-top: none;
}
.bh-ddm-lv1-container .bh-ddm-lv1-item:last-child.bh-ddm-lv1-item-selected {
  border-bottom: none;
}
.bh-ddm-lv2-item-selected {
  color: #38cdc1;
}
.bh-ddm-lv3-item-selected {
  color: #38cdc1;
}
.bh-ddm-shadow {
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.25);
  z-index: 9;
  position: absolute;
}
</style>
<script>
export default {
  data() {
    return {
      subOptions: [],
      subParentOptions: "",
      grandSonOptions: [],
      grandSonParentOptions: "",
      maxHeight: "",
      isShowShadow: "none",
      isShowMenu: "block"
    };
  },
  props: {
    options: {
      type: Array,
      default: [],
      required: true
    },
    type: {
      type: Number,
      default: 1,
      required: true
    },
    line: {
      type: Number,
      default: 3
    },
    menuParent: {
      type: Object,
      default: {},
      required: true
    }
  },
  computed: {
    // 仅读取
    // options: function () {
    //     var totalItem = {
    //         text:'全部'+ this.menuParent.text,
    //         id:this.menuParent.id + 'All'
    //     };
    //     return this.options.unshift(totalItem);
    // },
    // 读取和设置
    // aPlus: {
    //     get: function () {
    //         return this.a + 1
    //     },
    //     set: function (v) {
    //         this.a = v - 1
    //     }
    // }
  },
  components: {},
  created() {
    //this.maxHeight = this.line * 44 + 'px';
  },
  watch: {
    options: function(newData, oldData) {
      if (newData.length > 0) {
        this.isShowShadow = "block";
        this.isShowMenu = "block";
      }
      //切换变化时
      if (oldData.length != 0 && newData.length != 0) {
        if (oldData[0].id != newData[0].id) {
          //console.log('options empty')
          this.subOptions = [];
          this.grandSonOptions = [];
          console.log(this.menuParent);
          var totalItem = {
            text: "全部" + this.menuParent.text,
            id: this.menuParent.id + "All"
          };
          this.options.unshift(totalItem);
        }
      }
      //第一次进来
      if (oldData.length === 0 && newData.length != 0) {
        var totalItem = {
          text: "全部" + this.menuParent.text,
          originText: this.menuParent.text,
          originId: this.menuParent.id,
          id: this.menuParent.id + "All"
        };
        this.options.unshift(totalItem);
      }
    },
    subOptions: function(newData, oldData) {
      if (oldData.length != 0 && newData.length != 0) {
        if (oldData[0].id != newData[0].id) {
          this.grandSonOptions = [];
        }
      }
    },
    line: function(newData, oldData) {
      this.maxHeight = newData * 44 + "px";
    }
  },
  methods: {
    setSelected: function(param, index) {
      this.$nextTick(function() {
        this.options.forEach(function(item) {
          Vue.set(item, "active", false);
        });
        Vue.set(param, "active", true);
        if (this.type != 1) {
          if (param.id.indexOf("All") > -1) {
            //清除二三级的选中信息
            if (this.subOptions.length > 0) {
              this.subOptions.forEach(function(ele) {
                if (ele.active) {
                  ele.active = false;
                }
              });
            }
            if (this.grandSonOptions.length > 0) {
              this.grandSonOptions.forEach(function(ele) {
                if (ele.active) {
                  ele.active = false;
                }
              });
            }
            this.subOptions = [];
            this.grandSonOptions = [];
            var returnData = {
              node: {
                text: param.originText,
                id: param.originId
              }
            };
            this.postEventToParent(returnData);
          } else {
            //设置二级列表数据来源
            this.subOptions = param.children;
            this.subParentOptions = param;
            //清除切换一级列表导致二级数据的变化，比如，选择某一级，点击了其二级项，再切换一级，再点击此二级的项，再返回之前的某一级，发现其二级保留了之前的状态
            this.subOptions.forEach(function(item) {
              Vue.set(item, "active", false);
            });
          }
        } else {
          if (param.id.indexOf("All") > -1) {
            var returnData = {
              node: {
                text: param.originText,
                id: param.originId
              }
            };
          } else {
            var returnData = {
              node: param
            };
          }
          // console.log(returnData);
          this.postEventToParent(returnData);
        }
      });
    },
    setLv2Selected: function(param, index) {
      this.$nextTick(function() {
        this.subOptions.forEach(function(item) {
          Vue.set(item, "active", false);
        });
        Vue.set(param, "active", true);
        if (this.type != 2) {
          //设置三级列表数据来源
          this.grandSonOptions = param.children;
          this.grandSonParentOptions = param;
          //清除切换二级列表导致三级数据的变化
          this.grandSonOptions.forEach(function(item) {
            Vue.set(item, "active", false);
          });
        } else {
          var returnData = {
            node: param,
            parentNode: this.subParentOptions
          };
          this.postEventToParent(returnData);
        }
      });
    },
    setLv3Selected: function(param, index) {
      this.$nextTick(function() {
        this.grandSonOptions.forEach(function(item) {
          Vue.set(item, "active", false);
        });
        Vue.set(param, "active", true);
        var returnData = {
          node: param,
          parentNode: this.grandSonParentOptions,
          grandNode: this.subParentOptions
        };
        this.postEventToParent(returnData);
      });
    },
    cancelShadow: function() {
      this.isShowShadow = "none";
      this.isShowMenu = "none";
    },
    postEventToParent(data){
        this.$emit("dropDownMenu", data);
        this.cancelShadow();
    }
  }
};
</script>