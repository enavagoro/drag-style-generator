<template>
	<div>
        <div class="menu" v-if="seen" v-bind:class="{ enterLeft :a_enterLeft, outLeft :a_outLeft }">
            <div class="menu-image-button-container" @click="activeOutLeft()">
                <img class="menu-image-button" src="https://upload-icon.s3.amazonaws.com/uploads/icons/png/21418105741578287700-512.png">
            </div>
            <div class="menu-item-list">
                      <!--<draggable
                            class="dragArea list-group"
                            :list="list1"
                            :group="{ name: 'people', pull: 'clone', put: false }"
                            @change="log"
                        >
                            <div
                            class="list-group-item"
                            v-for="element in list1"
                            :key="element.name"
                            >
                            {{ element.name }}
                            </div>
                        </draggable>-->
                
                <draggable
                    class="dragArea list-group"
                    :list="elements"
                    :group="{ name: 'element', pull: 'clone', put: false }"
                    clone:="cloneDog"
                    @change="log"
                >
                    <div class="menu-item" v-for="(element, key) in elements" v-bind:key="key" >
                        <span class="text-left">{{ element.name }}</span>
                    </div>
                </draggable>
            </div>
            
        </div>
        <!--<div class="menu-overlay" v-if="seen" @click="activeOutLeft()">
        </div>
        -->
        <h1>{{elements}}</h1>

        <h1>{{list2}}</h1>
    </div>
</template>

<script>

import axios from 'axios';
import draggable from 'vuedraggable';

export default {
  name: 'Menu',
  components:{
      draggable
  },
  props: {
    msg: String,
  },
  methods:{
    changeSeen: function(){
      this.seen = !this.seen
    },
    activeOutLeft: function(){
      this.a_enterLeft = false;
      this.a_outLeft = !this.a_outLeft;
      setTimeout(() => this.changeSeen(), 500);
    },
    activeEnterLeft: function(){
      this.a_outLeft = false;
      this.changeSeen();
      this.a_enterLeft = !this.a_enterLeft;
    },
    log: function(evt) {
      window.console.log(evt);
    }    
  },
  data: function(){
    return {
      seen: false,
      a_enterLeft: false,
      a_outLeft: false,
      cryptos: [],
      errors: [],
      elements: [
        { name: "red", color: "#f44336" },
        { name: "blue", color: "#3f51b5" },
        { name: "yellow", color: "#ffd600" },
        { name: "green", color: "#4caf50" }
      ],
    };
  },
  created () {

  },
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
	@import url('https://fonts.googleapis.com/css?family=Roboto+Condensed');

	.menu {
		position: fixed;
		width: 20%;
		overflow: auto;
		height: 100vh;
		background: #1c1c1c;
		z-index: 999;
        top: 0;
	}

	.menu-overlay {
		position: fixed;
		top: 0;
		left: 0;
		right: 0;
		bottom: 0;
		z-index: 0;
		background-color: rgba(0, 0, 0, 0.3);
		cursor: pointer;
	}

	.menu-list {
		width: 100%;
	}

	.menu-item {
		cursor: pointer;
		margin-top: 10%;
		background: white;
		width: 80%;
		margin-left: 10%;
		margin-bottom: 2%;
		padding-top: 1%;
		padding-bottom: 2.5%;
		border-radius: 10px;
		-webkit-box-shadow: 0px 2px 2px 2px rgba(184, 184, 184, .5);
		-moz-box-shadow: 0px 2px 2px 2px rgba(184, 184, 184, .5);
		box-shadow: 0px 2px 2px 2px rgba(184, 184, 184, .5);
	}

	.menu-text {
		text-align: left;
		font-size: 21px;
		margin-top: 4%;
		font-family: 'Roboto', sans-serif;
		font-weight: 600;
		color: #1c1c1c;
	}

	.text-left {
		font-size: 16px;
		margin-top: 4%;
		font-family: 'Roboto', sans-serif;
		font-weight: 600;
		color: #1c1c1c;
	}

	.text-rigth {
		font-size: 16px;
		margin-top: 4%;
		font-family: 'Roboto', sans-serif;
		font-weight: 600;
		color: #1c1c1c;
		float: right;
	}

	/* animaciones */

	.enterLeft {
		animation: enter-left .5s ease-in;
	}

	.outLeft {
		animation: out-left .5s ease-out;
	}

	@keyframes out-left {
		0% {
			transform: translateX(0%);
		}

		100% {
			transform: translateX(-100%);
		}
	}

	@keyframes enter-left {
		0% {
			transform: translateX(-100%);
		}

		100% {
			transform: translateX(0%);
		}
	}

	.menu-image-button-container {
		width: 60%;
		padding-top: 10%;
		margin-left: 20%;
	}

	.menu-image-button {
		width: 60px;
		margin-left: calc((100% - 60px)/2);
		cursor: pointer;
		transition: .5s;
	}

	.menu-image-button:hover {
		transition: .5s;
		transform: scale(1, 1.2);
	}

	@media (max-width: 900px) {
		.menu {
			width: 80%;
			overflow: auto;
			height: 100vh;
			background: #1c1c1c;
			position: absolute;
			z-index: 999;
		}
	}
</style>