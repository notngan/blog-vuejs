<template>
    <div v-theme:column="'narrow'" id="show-blog">
			<h1>All Blog Articles</h1>
			
			<input type="text" v-model="search" placeholder="search blogs" id="searchBox">
			
			<div v-for="blog in filteredBlogs" class="single-blog">
				<router-link v-bind:to="'/blog/'+ blog.id"><h2>{{ blog.title | toUppercase }}</h2></router-link>
				<article>{{ blog.content | snippet}}</article>
			</div>
    </div>
</template>

<script>
	import searchMixin from '../mixins/searchMixin'

export default {
	data () {
		return {
			blogs: [],
			search: ''
		}
	},
	methods: {
		
	},
	created(){
		this.$http.get('https://notngan-vuejs-practice.firebaseio.com/posts.json')
			.then(function(data){
			return data.json();
		}).then(function(data){
			var blogArr = [];
			for(let key in data){
				data[key].id = key;
				blogArr.push(data[key]);
			}
			this.blogs = blogArr;
		})
	},
	computed: {
	
	},
	filters: {
			toUppercase(val){
			return val.toUpperCase()
		}
	},
	directives: {
		'rainbox': {
				bind(el, binding, vnode){
				el.style.color = '#' + Math.random().toString().slice(2,8)
			}
		}	
	},
	mixins: [searchMixin]
}
</script>
<style>
#show-blog{
    max-width: 800px;
    margin: 0px auto;
}
.single-blog{
    padding: 20px;
    margin: 20px 0;
    box-sizing: border-box;
    background: #eee;
}
#show-blog a{
	text-decoration: none;
	color: #444;
	}
	#searchBox {
		width: 100%;
		height: 28px;
		padding: 4px;
		box-sizing: border-box;
	}
</style>