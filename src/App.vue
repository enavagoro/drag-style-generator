<template>
  <div id="app">
    <Workshop />
		<Menu msg="hola" ref="menu" />
		<div class="image-button-container" @click="activateMenu()">
			<img class="image-button" src="https://upload-icon.s3.amazonaws.com/uploads/icons/png/1693045251584073356-512.png">
    </div>    
  </div>
</template>

<script>
import Workshop from '@/views/Workshop.vue';
import Menu from '@/components/Menu.vue';

export default {
  name:'App',
  components:{
    Workshop,
    Menu
  },
  methods: {
    activateMenu: function(value){
      this.$refs.menu.activeEnterLeft();
    }
  },
  data: function(){
    return {
      routes: [{name:'template1',link:'/template1'},
               {name:'template2',link:'/template2'},
               {name:'template3',link:'/template3'}
              ]
    };
  },
  
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

	.image-button-container {
		width: 10%;
		padding-top: 2%;
		margin-left: 5%;
	}

	.image-button {
		width: 40%;
		cursor: pointer;
		transition: .5s;
	}

	.image-button:hover {
		transition: .5s;
		transform: scale(1, 1.3);
	}

	@media (max-width: 900px) {
		#app {
			height: 100%;
			padding: 0%;
			margin: 0%;
			background-image: url("//live.staticflickr.com/1957/30375908227_9c39fa707b_k.jpg");
			background-size: cover;
		}

		.image-button-container {
			width: 30%;
			padding-top: 2%;
			margin-left: 5%;
		}

		.image-button {
			width: 60px;
			margin-left: calc((100% - 60px)/2);
			cursor: pointer;
			transition: .5s;
		}

		.image-button:hover {
			transition: .5s;
			transform: scale(1, 1.2);
		}
	}
</style>
