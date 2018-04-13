<template>
  <div class="hello">
    <h1>课程表</h1>
    <div class="ke">
       <p>项目</p>
       <p>第一节</p>
       <p>第二节</p>
       <p>第三节</p>
       <p>第四节</p>
       <p>第五节</p>
       <p>第六节</p>
       <p>第七节</p>
       <p>第八节</p>
    </div>
    <div v-for='i in arr' class="wrap">
      <div class="box">
               <h3>{{i.week}}</h3>
               <p>{{i.one}}</p>
               <p>{{i.two}}</p>
               <p>{{i.three}}</p>
               <p>{{i.four}}</p>
               <p>{{i.five}}</p>
               <p>{{i.six}}</p>
               <p>{{i.seven}}</p>
               <p>{{i.eight}}</p>
               <button @click="update">修改</button>
      </div>
    </div>
    
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  created(){
    this.$http.get('http://localhost:3000/').then(e=>this.arr=e.body)
  },
  data(){
    return {
      arr:[],
      lan:{},
      lanf:false
    }
  },
  methods:{
  update(e){
      this.$http.post('http://localhost:3000/update',this.lan,{emulateJSON:true}).then(function(){
        this.arr.push(this.lan)
      })
    },
    abc(){
      this.lanf=!this.lanf
    }
  }
  
}
</script>


<style scoped>
.ke{
   float :left;
   margin :16px 0 50px 0;
   width: 230px;
   font-size :20px;
   color :red;
   font-weight :bold;
  }
  .ke p{
    width :100%;
    height :30px;
    cursor :pointer;
  }
	.box{
		width: 180px;
		float: left;
		margin: 5px;
    font-size :20px;
	}
  .box p{
    width :100%;
    height :30px;
    background :#ccc;
    cursor :pointer;
  }

</style>
