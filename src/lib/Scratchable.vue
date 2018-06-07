<template>
    <div :class="classes">
        <div v-for="item,index in list" :key="index" class="yd-grids-item">
            <div class="yd-grids-icon" @click="gotoLink(item)">
                <img :src="item.url">
            </div>
            <div class="yd-grids-txt">
                <span>{{item.text}}</span>
            </div>
        </div>
    </div>
</template>
<script type="text/ecmascript-6">
    export default {
        props: {
            callback:{
              type:Function,
            },
            list: {
                type:Array,
                required:true
            },
            num: { //每行显示的数量
                type: Number,//数据类型 String Number Boolean Function Object Array
                validator(value) {
                    return ['2', '3', '4', '5'].indexOf(value + '') > -1;
                },
                default: 4,//默认
                required: true,//是否必填
            }
        },
        data () {
            return {

            }
        },
        computed: {
            classes() {
                return 'yd-grids-' + this.num;
            },
        },
        methods: {
            gotoLink(item){
                if (this.callback){
                    this.callback(item);
                }
            }
        },
        mounted () {
            console.log(this.list);
        }
    }
</script>
<style scoped>
    .yd-grids-2{
        overflow: hidden;
        position: relative;
        background-color: #fff;
    }
    .yd-grids-3{
        overflow: hidden;
        position: relative;
        background-color: #fff;
    }
    .yd-grids-4{
        overflow: hidden;
        position: relative;
        background-color: #fff;
    }
    .yd-grids-5{
        overflow: hidden;
        position: relative;
        background-color: #fff;
    }
    .yd-grids-item {
        width: 25%;
        float: left;
        position: relative;
        z-index: 0;
        padding: .2rem 0;
        font-size: .28rem;
    }
    .yd-grids-5 .yd-grids-item {
        width: 20%;
    }

    .yd-grids-4 .yd-grids-item {
        width: 25%;
    }

    .yd-grids-3 .yd-grids-item {
        width: 33.33%;
    }

    .yd-grids-2 .yd-grids-item {
        width: 50%;
    }

    .yd-grids-icon {
        height: .9rem;
        display: flex;
        -webkit-box-pack: center;
        justify-content: center;
        align-items: center;
    }

    .yd-grids-icon img {
        height: 100%;
    }

    .yd-grids-txt {
        word-wrap: normal;
        text-overflow: ellipsis;
        white-space: nowrap;
        overflow: hidden;
        text-align: center;
        color: #333;
        padding: 0 .2rem;
    }

    .yd-grids-txt span {
        display: block;
        font-size: 0.25rem;
        color: rgb(0, 0, 0);
    }
</style>