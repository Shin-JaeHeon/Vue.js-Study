<template lang"pug">
html
	head
		title {{title}}
	body
		h1 {{h1title}}
		p {{changed}}
		div#app
			p(v-if="seen") 이제 나를 볼 수 있어요
		div#a2
			ol
				li( v-for="todo in todos)
					{{todo.data}}
		div#a3
			p {{message}}
			button(v-on:click="reverseMessage") 메세지 뒤집기
		div#a4
			p {{message}}
			input(v-model="message)
		ol
			todo-item(v-for="item in list",v-bind:todo="item",v-bind:key="item.id")
</template>
<script>
import index from  './index.vue'
	export deafult {
		data(){
			title: 'Hello, World',
			h1title: 'Hello, Page',
			changed:'this can changed by you!'
		}
	}
	let app = new Vue({
		el:'#app',
		data : {
			seen: true	
		}
	});
	let app2 = new Vue({
		el:'#a2',
		data : {
			todos:[
				{data:'Angular?'},
				{data:'React?'},
				{data:'Vue.js!'}
			]
		}
	});
	let a3 = new Vue({
		el:'#a3',
		data : {
			message: 'Hello? Vue.js'
		},
		methods: {
			reverseMessage:()=>{
				this.message = this.message.split('').reverse().join();
			}
		}
	});
	let a4 = new Vue({
		el:'#a4',
		data:{
			message:'Hello, Vue.js!'
		}
	});
	Vue.component('todo-itme',{
		props:['todo'],
		template:'<li>{{todo.text}}</li>'
	});
	let a5 = new Vule({
		el:'#a5',
		data:{
			liet{
				{id:0, text:'Google'},
				{id:1, text:'Facebook'},
				{id:2, text:'Open source'}
			}
		}
	});
</script>
<style lang="stylus" scoped>
p
	font-size 2rem
	text-align center
</style>