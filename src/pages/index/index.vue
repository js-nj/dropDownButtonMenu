<template>
    <div class="page_border">
        <mt-header></mt-header>
        <div>
            <!-- <drop-down-buttons :options="options" @dropDownButtons="getSelectedButton"></drop-down-buttons>
            <drop-down-menu  :menuParent="menuParent" :options="menuOptions" :type="type" :line="line" @dropDownMenu="getSelectedMenu"></drop-down-menu> -->
            <drop-down-button-menu :options="options" :menuOption="menuOptions" @dropDownButtonMenu="getSelectedMenu"></drop-down-button-menu>
        </div>
        
        <!-- 静态图片的写法请参照以下方式 -->
        <img class="right_icon" :src="'./static/assets/title.jpg'">
        <h1 class="index">
            首页
        </h1>
        <com-test></com-test>
    </div>
</template>
<style>
.index{
    background:#ffffff;
}
.right_icon{
    float: right;
    height: 50px;
    padding-right: 8px;
}
.page_border{
    /* padding: 4px; */
}
</style>
<script type="text/javascript">
    import { Header } from 'bh-mint-ui2';
    import comTest from '../../components/comTest.vue';
    import dropDownButtons from '../../components/dropDownButtons.vue';
    import dropDownMenu from '../../components/dropDownMenu.vue';
    import dropDownButtonMenu from '../../components/dropDownButtonMenu.vue';
    export default {
        data(){
            return {
                page: 'about',
                options:[{
                    text:'国家',
                    id:'country'
                },{
                    text:'性别',
                    id:'sex'
                },{
                    text:'交通',
                    id:'traffic'
                },{
                    text:'筛选',
                    id:'filter'
                }],
                menuOptions:[],
                // type:1,
                // line:5,
                // menuParent:{}
            }
        },
        components: {
            [Header.name]:Header,
            comTest,
            dropDownButtons,
            dropDownMenu,
            dropDownButtonMenu
        },
        mounted(){
            global.SDK.setTitleText("首页");
            this.menuOptions = [{
                    type:2,
                    menuOptions:[{
                        text:'中国',
                        id:'China',
                        children:[{
                            text:'江苏',
                            id:'js'
                        },{
                            text:'山东',
                            id:'sd'
                        }]
                    },{
                        text:'美国',
                        id:'American',
                        children:[{
                            text:'纽约',
                            id:'ny'
                        },{
                            text:'旧金山啊',
                            id:'jjs'
                        }]
                    }]
                },{
                    type:1,
                    line:10,
                    menuOptions:[{
                        text:'男',
                        id:'man'
                    },{
                        text:'女',
                        id:'woman'
                    },{
                        text:'男1',
                        id:'man1'
                    },{
                        text:'女1',
                        id:'woman1'
                    },{
                        text:'男2',
                        id:'man2'
                    },{
                        text:'女2',
                        id:'woman2'
                    },{
                        text:'男3',
                        id:'man3'
                    },{
                        text:'女3',
                        id:'woman3'
                    },{
                        text:'男4',
                        id:'man4'
                    },{
                        text:'女4',
                        id:'woman4'
                    },{
                        text:'男5',
                        id:'man5'
                    },{
                        text:'女5',
                        id:'woman5'
                    }] 
                },{
                  type:3,
                  line:4,
                  menuOptions:[{
                        text:'地铁',
                        id:'metro',
                        children:[{
                            text:'一号线',
                            id:'firstLine',
                            children:[{
                                text:'南京南',
                                id:'njn'
                            },{
                                text:'河定桥',
                                id:'hdq'
                            }]
                        },{
                            text:'二号线',
                            id:'secondLine',
                            children:[{
                                text:'仙林',
                                id:'xl'
                            },{
                                text:'油坊桥',
                                id:'yfq'
                            }]
                        }]
                    },{
                        text:'公交',
                        id:'bus',
                        children:[{
                            text:'08路',
                            id:'08',
                            children:[{
                                text:'万达',
                                id:'wd'
                            },{
                                text:'金智',
                                id:'wisedu'
                            }]
                        },{
                            text:'09路',
                            id:'09',
                            children:[{
                                text:'河海',
                                id:'hh'
                            },{
                                text:'南理工',
                                id:'nlg'
                            }]
                        },{
                            text:'09路',
                            id:'09',
                            children:[{
                                text:'河海',
                                id:'hh'
                            },{
                                text:'南理工',
                                id:'nlg'
                            }]
                        },{
                            text:'09路',
                            id:'09',
                            children:[{
                                text:'河海',
                                id:'hh'
                            },{
                                text:'南理工',
                                id:'nlg'
                            }]
                        },{
                            text:'09路',
                            id:'09',
                            children:[{
                                text:'河海',
                                id:'hh'
                            },{
                                text:'南理工',
                                id:'nlg'
                            }]
                        },{
                            text:'09路',
                            id:'09',
                            children:[{
                                text:'河海',
                                id:'hh'
                            },{
                                text:'南理工',
                                id:'nlg'
                            }]
                        },{
                            text:'09路',
                            id:'09',
                            children:[{
                                text:'河海',
                                id:'hh'
                            },{
                                text:'南理工',
                                id:'nlg'
                            }]
                        },{
                            text:'09路',
                            id:'09',
                            children:[{
                                text:'河海',
                                id:'hh'
                            },{
                                text:'南理工',
                                id:'nlg'
                            }]
                        }]
                    },{
                        text:'公交1',
                        id:'bus1',
                        children:[{
                            text:'08路1',
                            id:'081',
                            children:[{
                                text:'万达1',
                                id:'wd1'
                            },{
                                text:'金智1',
                                id:'wisedu1'
                            }]
                        },{
                            text:'09路1',
                            id:'091',
                            children:[{
                                text:'河海1',
                                id:'hh1'
                            },{
                                text:'南理工1',
                                id:'nlg1'
                            }]
                        }]
                    },{
                        text:'公交2',
                        id:'bus2',
                        children:[{
                            text:'08路2',
                            id:'082',
                            children:[{
                                text:'万达2',
                                id:'wd2'
                            },{
                                text:'金智2',
                                id:'wisedu2'
                            }]
                        },{
                            text:'09路2',
                            id:'092',
                            children:[{
                                text:'河海2',
                                id:'hh2'
                            },{
                                text:'南理工2',
                                id:'nlg2'
                            }]
                        }]
                    },{
                        text:'公交3',
                        id:'bus3',
                        children:[{
                            text:'08路3',
                            id:'083',
                            children:[{
                                text:'万达3',
                                id:'wd3'
                            },{
                                text:'金智3',
                                id:'wisedu3'
                            }]
                        },{
                            text:'09路3',
                            id:'093',
                            children:[{
                                text:'河海3',
                                id:'hh3'
                            },{
                                text:'南理工3',
                                id:'nlg3'
                            }]
                        }]
                    },{
                        text:'公交4',
                        id:'bus4',
                        children:[{
                            text:'08路4',
                            id:'084',
                            children:[{
                                text:'万达4',
                                id:'wd4'
                            },{
                                text:'金智4',
                                id:'wisedu4'
                            }]
                        },{
                            text:'09路4',
                            id:'094',
                            children:[{
                                text:'河海4',
                                id:'hh4'
                            },{
                                text:'南理工4',
                                id:'nlg4'
                            }]
                        }]
                    }]  
                },{
                    type:'filter',
                    menuOptions:[{
                        text:'距离',
                        id:'location',
                        children:[{
                            text:'一千米',
                            id:'1km'
                        },{
                            text:'两千米',
                            id:'2km'
                        }]
                    },{
                        text:'频率',
                        id:'pl',
                        children:[{
                            text:'1次',
                            id:'1time'
                        },{
                            text:'2次',
                            id:'2time'
                        },{
                            text:'3次',
                            id:'3time'
                        },{
                            text:'4次',
                            id:'4time'
                        },{
                            text:'5次',
                            id:'5time'
                        },{
                            text:'6次',
                            id:'6time'
                        }]
                    }]
                }];
        },
        methods:{
            // getSelectedButton:function(param){
            //     //this.menuOptions = [];
            //     console.log('-------------')
            //     console.log(this.menuParent);
            //     if (param.id === 'sex') {
            //         this.type = 1;
            //         this.line = 10;
            //         this.menuParent = param;
            //         this.menuOptions= [{
            //             text:'男',
            //             id:'man'
            //         },{
            //             text:'女',
            //             id:'woman'
            //         },{
            //             text:'男1',
            //             id:'man1'
            //         },{
            //             text:'女1',
            //             id:'woman1'
            //         },{
            //             text:'男2',
            //             id:'man2'
            //         },{
            //             text:'女2',
            //             id:'woman2'
            //         },{
            //             text:'男3',
            //             id:'man3'
            //         },{
            //             text:'女3',
            //             id:'woman3'
            //         },{
            //             text:'男4',
            //             id:'man4'
            //         },{
            //             text:'女4',
            //             id:'woman4'
            //         },{
            //             text:'男5',
            //             id:'man5'
            //         },{
            //             text:'女5',
            //             id:'woman5'
            //         }] 
            //     }else if (param.id === 'country'){
            //         this.type = 2;
            //         this.menuParent = param;
            //         this.menuOptions= [{
            //             text:'中国',
            //             id:'China',
            //             children:[{
            //                 text:'江苏',
            //                 id:'js'
            //             },{
            //                 text:'山东',
            //                 id:'sd'
            //             }]
            //         },{
            //             text:'美国',
            //             id:'American',
            //             children:[{
            //                 text:'纽约',
            //                 id:'ny'
            //             },{
            //                 text:'旧金山',
            //                 id:'jjs'
            //             }]
            //         }];
            //     }else if (param.id === 'traffic') {
            //         this.type = 3;
            //         this.line = 4;
            //         this.menuParent = param;
            //         this.menuOptions= [{
            //             text:'地铁',
            //             id:'metro',
            //             children:[{
            //                 text:'一号线',
            //                 id:'firstLine',
            //                 children:[{
            //                     text:'南京南',
            //                     id:'njn'
            //                 },{
            //                     text:'河定桥',
            //                     id:'hdq'
            //                 }]
            //             },{
            //                 text:'二号线',
            //                 id:'secondLine',
            //                 children:[{
            //                     text:'仙林',
            //                     id:'xl'
            //                 },{
            //                     text:'油坊桥',
            //                     id:'yfq'
            //                 }]
            //             }]
            //         },{
            //             text:'公交',
            //             id:'bus',
            //             children:[{
            //                 text:'08路',
            //                 id:'08',
            //                 children:[{
            //                     text:'万达',
            //                     id:'wd'
            //                 },{
            //                     text:'金智',
            //                     id:'wisedu'
            //                 }]
            //             },{
            //                 text:'09路',
            //                 id:'09',
            //                 children:[{
            //                     text:'河海',
            //                     id:'hh'
            //                 },{
            //                     text:'南理工',
            //                     id:'nlg'
            //                 }]
            //             },{
            //                 text:'09路',
            //                 id:'09',
            //                 children:[{
            //                     text:'河海',
            //                     id:'hh'
            //                 },{
            //                     text:'南理工',
            //                     id:'nlg'
            //                 }]
            //             },{
            //                 text:'09路',
            //                 id:'09',
            //                 children:[{
            //                     text:'河海',
            //                     id:'hh'
            //                 },{
            //                     text:'南理工',
            //                     id:'nlg'
            //                 }]
            //             },{
            //                 text:'09路',
            //                 id:'09',
            //                 children:[{
            //                     text:'河海',
            //                     id:'hh'
            //                 },{
            //                     text:'南理工',
            //                     id:'nlg'
            //                 }]
            //             },{
            //                 text:'09路',
            //                 id:'09',
            //                 children:[{
            //                     text:'河海',
            //                     id:'hh'
            //                 },{
            //                     text:'南理工',
            //                     id:'nlg'
            //                 }]
            //             },{
            //                 text:'09路',
            //                 id:'09',
            //                 children:[{
            //                     text:'河海',
            //                     id:'hh'
            //                 },{
            //                     text:'南理工',
            //                     id:'nlg'
            //                 }]
            //             },{
            //                 text:'09路',
            //                 id:'09',
            //                 children:[{
            //                     text:'河海',
            //                     id:'hh'
            //                 },{
            //                     text:'南理工',
            //                     id:'nlg'
            //                 }]
            //             }]
            //         },{
            //             text:'公交1',
            //             id:'bus1',
            //             children:[{
            //                 text:'08路1',
            //                 id:'081',
            //                 children:[{
            //                     text:'万达1',
            //                     id:'wd1'
            //                 },{
            //                     text:'金智1',
            //                     id:'wisedu1'
            //                 }]
            //             },{
            //                 text:'09路1',
            //                 id:'091',
            //                 children:[{
            //                     text:'河海1',
            //                     id:'hh1'
            //                 },{
            //                     text:'南理工1',
            //                     id:'nlg1'
            //                 }]
            //             }]
            //         },{
            //             text:'公交2',
            //             id:'bus2',
            //             children:[{
            //                 text:'08路2',
            //                 id:'082',
            //                 children:[{
            //                     text:'万达2',
            //                     id:'wd2'
            //                 },{
            //                     text:'金智2',
            //                     id:'wisedu2'
            //                 }]
            //             },{
            //                 text:'09路2',
            //                 id:'092',
            //                 children:[{
            //                     text:'河海2',
            //                     id:'hh2'
            //                 },{
            //                     text:'南理工2',
            //                     id:'nlg2'
            //                 }]
            //             }]
            //         },{
            //             text:'公交3',
            //             id:'bus3',
            //             children:[{
            //                 text:'08路3',
            //                 id:'083',
            //                 children:[{
            //                     text:'万达3',
            //                     id:'wd3'
            //                 },{
            //                     text:'金智3',
            //                     id:'wisedu3'
            //                 }]
            //             },{
            //                 text:'09路3',
            //                 id:'093',
            //                 children:[{
            //                     text:'河海3',
            //                     id:'hh3'
            //                 },{
            //                     text:'南理工3',
            //                     id:'nlg3'
            //                 }]
            //             }]
            //         },{
            //             text:'公交4',
            //             id:'bus4',
            //             children:[{
            //                 text:'08路4',
            //                 id:'084',
            //                 children:[{
            //                     text:'万达4',
            //                     id:'wd4'
            //                 },{
            //                     text:'金智4',
            //                     id:'wisedu4'
            //                 }]
            //             },{
            //                 text:'09路4',
            //                 id:'094',
            //                 children:[{
            //                     text:'河海4',
            //                     id:'hh4'
            //                 },{
            //                     text:'南理工4',
            //                     id:'nlg4'
            //                 }]
            //             }]
            //         }];
            //     }
                
            // },
            getSelectedMenu:function(param){
                
                // this.options.forEach(function(element) {
                //     if (element.active === true) {
                //         element.text = param.node.text;
                //     }   
                // });
                console.log(param);
            }
        }
    }
</script>
