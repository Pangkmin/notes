<template>
	<nav>
        <span class="pageinfo">共<em>{{pagesum}}</em>页/{{total}}条</span>
        <ul class="pagesumnav">
            <li :class="{'disabled': current == 1}" @click="setCurrent(current-1)">上一页</li>

            <template v-for="(num,id) in grouplist">
				<li v-if="current < 5 && num < 6" @click="setCurrent(num)" :class="{'actived':(current==num)}">{{num}}</li>
            	<li v-else-if="current< 5 && num == 6">..</li>
            	<li v-else-if="num == 1 || num == pagesum || (current > 4 && current-2 <= num && num <= current+2)" @click="setCurrent(num)" :class="{'actived':(current==num)}">{{num}}</li>
            	<li v-else-if="current > 4 && num == current-3">..</li>
            	<li v-else-if="current > 4 && num == current+3">..</li>
            </template>
            <li :class="{'disabled': current == pagesum}" @click="setCurrent(current+1)">下一页</li>
        </ul>
        <div class="pagesumjump">
            <select class="pageSelect" @change="pageNum">
                <option v-for="(num,ide) in dispaly" :key="ide">{{num}}条/页</option>
            </select>
            到第
            <input type="text" v-model="jumpDefault" @keyup.enter="submit($event)" >
            页
            <button @click="jumpTo">跳转</button>
        </div>
    </nav>
</template>

<script>
export default {
	name: 'PageNav',
	props:{
	    total:{// 数据总条数
	        type:Number,
	        default:10,
	    },
	    dispaly:{// 每页显示条数
	        type:Array,
	        default(){
	            return [10,20,30,50]
	        }
	    },
	    pagegroup:{// 显示页码个数
	        type:Number,
	        default:5,
	    },
	},
	data(){
	    return{
	        current: 1,//当前页码
	        currentSize: this.dispaly[0],//当前显示条数，默认10条
	        jumpDefault:1, //跳转默认值
	    }
	},
	computed:{
	    pagesum(){  // 根据数据的条数和每页显示数量算出总页数,如果没有则为1 ;
	    	return Math.ceil(this.total/this.currentSize) || 1
	    },
	    grouplist(){ //获取分页码
	        var len=this.pagesum
	        var count=Math.floor(this.pagegroup/2)
	        var center =this.current
	        var temp=[]
	        while(len--){
	            temp.push(this.pagesum-len)
	        }
	        return temp
	    }
	},
	methods:{
	    pageNum(){ //切换显示条数
	        let nums=document.getElementsByClassName('pageSelect')[0].value
	        var num=nums.split('条')[0]
	        this.currentSize=num
	        this.jumpDefault=1
	        this.setCurrent(1)
	    },
	    setCurrent(idx){
	        // 判断当前页码不等于本身，和大于零，而且要小于总页数的时候，才触发
	        if (this.current != idx && idx > 0 && idx < this.pagesum + 1) {
	            this.current = idx;
	        }
	        this.$emit('pagedata',{currentpage:this.current,currentSize:this.currentSize})
	    },
	    jumpTo(){
            this.current=parseInt(this.jumpDefault)
            this.setCurrent(this.current)
	    },
	    submit($event){
	        this.jumpTo()
	    }
	},
	watch:{
		//监听input框参数
	    jumpDefault(){  
	        if(this.jumpDefault>=this.pagesum){
	            this.jumpDefault=this.pagesum
	        }
	    }
	}
}
</script>

<style scoped>
nav{
    margin:10px 0;
    font-size: 0;
    color: #333;
}
nav *{
	box-sizing: border-box;
}
.pageinfo{
	display: inline-block;
	vertical-align: middle;
	font-size: 12px;
	margin: 0 10px 5px 0;
	line-height: 30px;
}
.pageinfo em{
    font-style: normal;
    color:#009688;
    padding:2px;
}
.pagesumjump{
	display: inline-block;
	vertical-align: middle;
	font-size: 12px;
	margin-bottom: 5px;
}
.pagesumjump .pageSelect{
    height:30px;
    border:1px solid #e2e2e2;
    outline: none;
    background:none;
    padding: 0 3px;
    margin: 0 10px;
}
.pagesumjump .pageSelect:focus {
    border-color: #009688!important;
}
.pagesumjump input{
    text-align: center;
    width:40px;
    height:30px;
    line-height: 28px;
    border:1px solid #e2e2e2;
    margin:0 3px;
}
.pagesumjump button{
    margin-left: 5px;
    padding:0 10px;
    background:none;
    border:1px solid #e2e2e2;
    cursor: pointer;
    height: 30px;
    line-height: 28px;
    display: inline-block;
    transition: all .3s;
}
.pagesumjump button:hover{
    border-color: #009688;
}
.pagesumnav{
    display: inline-block;
    vertical-align: middle;
}
.pagesumnav li{
    display: inline-block;
    vertical-align: middle;
    font-size: 12px;
    border:1px solid #e2e2e2;
    padding: 0 15px;
    height: 30px;
    line-height: 28px;
    text-align: center;
    margin: 0 -1px 5px 0;
    cursor: pointer;
    -webkit-user-select:none; 
    -moz-user-select:none; 
    -ms-user-select:none; 
    user-select:none;
}
.pagesumnav li:hover{
    color:#009688;
}
.disabled{
    color: #d2d2d2!important;
    cursor: not-allowed!important;
}
.pagesumnav li.actived{
    background-color: #009688;
    color:#fff;
    border-color: #009688
}
</style>
