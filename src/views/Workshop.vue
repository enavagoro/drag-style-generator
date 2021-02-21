<template>
    <div class="workshop">
    <h1>Holaaaaaa</h1>
                  <draggable
                    class="dragArea" style="background:#37474f;"
                    :list="list2"
                    :group="{ name: 'people', put: true }"
                    @change="log"
                >
                    <div
                    class="menu-item"
                    v-for="element in list2"
                    :key="element.name"
                    v-bind:style="{'background': element.color}"
                    >
                    <span class="text-left">{{ element.name }}</span>
                </div>
                </draggable>
    </div>
</template>

<script>
import draggable from 'vuedraggable';

export default {
    name:'Workshop',
    components:{
        draggable
    },
    props:{

    },
    methods:{
        log: function(evt) {
        window.console.log(evt);
        }
    },
    data: function(){
        return {
            list2: []
        };
    }
}
</script>

<style scoped>
    .dragArea{
        width: 50%;
        margin-left: 25%;
        min-height: 500px;
    }

	.menu-item {
		cursor: pointer;
		margin-top: 0%;
		background: white;
		width: 80%;
		margin-left: 10%;
		margin-bottom: 0%;
		padding-top: 1%;
		padding-bottom: 2.5%;
		border-radius: 10px;
		-webkit-box-shadow: 0px 2px 2px 2px rgba(184, 184, 184, .5);
		-moz-box-shadow: 0px 2px 2px 2px rgba(184, 184, 184, .5);
		box-shadow: 0px 2px 2px 2px rgba(184, 184, 184, .5);
	}
</style>