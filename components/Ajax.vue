<template>
	<div>
		<table>
		<button @click="add">增加</button>
		<div v-if='jj'>
		标题：<input type="text"/>
		内容：<input type="text"/>
		<button @click="">录入</button>
		</div>
		
		<tr>
			<td>标题</td>
			<td>内容</td>
			</tr>
			<tr v-for="i in arr">
			<td>{{i.week}}</td>
			<td>{{i.one}}</td>
			<button id="jian" @click="del">删除</button>
			
			</tr>
		</table>
	</div>

</template>
<script>
	export default {
	created(){
			this.$http.get("http://localhost:3001").then(e=>this.arr=e.body)

		},
		data(){
			return {
			    jj:false,
				arr:[]
			}
		},
	methods: {
      del(e){
    this.$http.post('http://localhost:3000/del',{id:e.id},{emulateJSON:true}).then(function(){
      var _index=this.arr.indexOf(e)			
      this.arr.splice(_index,1)
    })
  },
      add(){
      this.jj=!this.jj
      }
	}
 }
</script>

<style>
</style>