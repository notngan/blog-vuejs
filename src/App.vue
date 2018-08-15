<template>
  <div>
		<app-header></app-header>
		<router-view></router-view>		
	</div>
</template>

<script>
// Imports
import addBlog from './components/addBlog.vue';
import showBlog from './components/showBlog.vue';
import listBlog from './components/listBlog.vue';
import Header from './components/Header.vue';

export default {
    components: {
      'add-blog': addBlog,
			'show-blog': showBlog,
			'list-blog': listBlog,
			'app-header': Header
    },
    data () {
        return {

        }
    },
    methods: {

    }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Nunito');

body{
  margin: 0;
	font-family: 'Nunito', sans-serif;
	}
</style>