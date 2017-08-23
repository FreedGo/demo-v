<template>
	<div id="demo">
		<table>
			<tr v-for="item in list">
				<td v-for="subItem in item">{{subItem}}</td>
			</tr>
		</table>
	</div>
</template>

<script>
	import Vue from 'vue';
	import vueResource from 'vue-resource'; //引用vueresource模块

	Vue.use(vueResource);

	export default {
		name: 'hello',
		data () {
			return {
				msg: 'Welcome to Your Vue.js App',
                list:[]
			}
		},
		created(){
			//在生命周期中的create来调用方法，获取数据
			this.getTableList();
		},
		methods:{
			//定义方法，ajax请求json数据
			getTableList(){
				this.$http.get('../../static/json/test.json').then(function (res) {
					this.list = res.body;
				},function (res) {
					
				})
			},

		}
	}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
	h1, h2 {
		font-weight: normal;
	}

	ul {
		list-style-type: none;
		padding: 0;
	}

	li {
		display: inline-block;
		margin: 0 10px;
	}

	a {
		color: #42b983;
	}
	td{
		border:#ccc solid 1px;
	}
</style>
