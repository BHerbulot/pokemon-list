<template>
<div 
	class="poke-card" 
	:class="{extended: extended}"
	:id="pokeInfo.number"
	:style="{backgroundColor: backColor}"
	@click="sayName"
>
	<div class="left-part">
		<img :src="pokeInfo.src" >
		<h3>{{ pokeInfo.name }}</h3>
		<span 
			v-for="(type, index) in pokeInfo.type" 
			:key="index"
			:class="[type.className]"
			class="pill"
		>{{type.type}}</span>
	</div>
	<div class="right-part"></div>
	<div class="right-bar" @click="extended = !extended"></div>
</div>
</template>

<script>
const Color = require('color');
export default {

    components: {

    },

    props: {
    	pokeInfo: {
    		type: Object,
    		required: true,
    	},

    },

    data: function(){
        return {
        	extended: false,
        	colors: {
				'background-color-grass' : '#9bcc50',
				'background-color-poison' : '#b97fc9',
				'background-color-fire' : '#fd7d24',
				'background-color-flying' : '#3dc7ef',
				'background-color-water' : '#4592c4',
				'background-color-bug' : '#729f3f',
				'background-color-normal' : '#a4acaf',
				'background-color-electric' : '#eed535',
				'background-color-ground' : '#f7de3f',
				'background-color-fairy' : '#fdb9e9',
				'background-color-fighting' : '#d56723',
				'background-color-psychic' : '#f366b9',
				'background-color-rock' : '#a38c21',
				'background-color-steel' : '#9eb7b8',
				'background-color-ice' : '#51c4e7',
				'background-color-ghost' : '#7b62a3',
				'background-color-dragon' : '#53a4cf',
				'background-color-dark' : '#707070',
        	},
        };
    },

    computed: {
    	backColor (){
    		return Color(this.colors[this.pokeInfo.type[0].className]).darken(0.2);
    	}
    },

    mounted: function(){

    },

    methods: {
    	sayName (){
    		let synth = window.speechSynthesis;
    		let voice = synth.getVoices();
    		let voiceText = new SpeechSynthesisUtterance(this.pokeInfo.name);
    		voiceText.voice = voice[0];
    		synth.speak(voiceText);
    	},

    	extend (){
    		// "https://pokeapi.co/api/"
    	}
    },
};
</script>

<style>
	.poke-card{
		border: 1px solid #000;
		width: 250px;
		text-align: center;
		border-radius: 15px;
		position: relative;
		transition: width .5s;
		margin-right: 20px;
		margin-bottom: 20px;
		display: flex;
	}
	.extended{
		width: 550px;

	}
	.left-part{
		padding: 20px 20px 60px 20px ;
		width: 200px;
	}
	.right-part{
		padding: 20px;
		width: auto;
	}
	.right-bar{
		position: absolute;
		height: 100%;
		width: 25px;
	    right: 0;
	    top: 0;
		border-top-right-radius: 15px;
		border-bottom-right-radius: 15px;
	    cursor: pointer;
	}
	.right-bar:hover{
		background-color: rgba(0,0,0,0.4);
	}
	.right-bar::after{
		position: absolute;
	  	content: url('../../static/chevron.svg');
	  	height: 25px;
	 	width: 25px;
		right: 0;
		top: 50%;
		transform: translateY(-50%) rotate(-90deg);

	}
	.poke-card img{
		width: 215px;
		height:	215px;
	}
	.pill{
		border-radius: 3px;
	    line-height: 18px;
	    padding: 5px 10px;
	    max-width: 110px;
	    margin: 0 1.5625% 0 0;
	    text-align: center;
	}
	.background-color-grass{
    	background: linear-gradient(180deg, #9bcc50 50%, #9bcc50 50%);
    	background-color: #9bcc50;
    	color: #212121;
	}
	.background-color-poison{
	    background: linear-gradient(180deg, #b97fc9 50%, #b97fc9 50%);
	    background-color: #b97fc9;
	    color: #fff;
	}
	.background-color-fire{
	    background: linear-gradient(180deg, #fd7d24 50%, #fd7d24 50%);
	    background-color: #fd7d24;
	    color: #fff;
	}
	.background-color-flying{
		background: linear-gradient(180deg, #3dc7ef 50%, #bdb9b8 50%);
    	background-color: #3dc7ef;
    	color: #212121;

	}
	.background-color-water{
		background: linear-gradient(180deg, #4592c4 50%, #4592c4 50%);
	    background-color: #4592c4;
	    color: #fff;
	}
	.background-color-bug{
		background: linear-gradient(180deg, #729f3f 50%, #729f3f 50%);
    	background-color: #729f3f;
    	color: #fff;

	}
	.background-color-normal{
	    background: linear-gradient(180deg, #a4acaf 50%, #a4acaf 50%);
	    background-color: #a4acaf;
	    color: #212121;
	}
	.background-color-electric{
		background: linear-gradient(180deg, #eed535 50%, #eed535 50%);
	    background-color: #eed535;
	    color: #212121;

	}
	.background-color-ground{
		background: linear-gradient(180deg, #f7de3f 50%, #ab9842 50%);
	    background-color: #f7de3f;
	    color: #212121;

	}
	.background-color-fairy{
		background: linear-gradient(180deg, #fdb9e9 50%, #fdb9e9 50%);
    	background-color: #fdb9e9;
    	color: #212121;

	}
	.background-color-fighting{
	    background: linear-gradient(180deg, #d56723 50%, #d56723 50%);
	    background-color: #d56723;
	    color: #fff;
	}
	.background-color-psychic{
	    background: linear-gradient(180deg, #f366b9 50%, #f366b9 50%);
	    background-color: #f366b9;
	    color: #fff;
	}
	.background-color-rock{
	    background: linear-gradient(180deg, #a38c21 50%, #a38c21 50%);
	    background-color: #a38c21;
	    color: #fff;
	}
	.background-color-steel{
	    background: linear-gradient(180deg, #9eb7b8 50%, #9eb7b8 50%);
    	background-color: #9eb7b8;
    	color: #212121;
	}
	.background-color-ice{
	    background: linear-gradient(180deg, #51c4e7 50%, #51c4e7 50%);
	    background-color: #51c4e7;
	    color: #212121;
	}
	.background-color-ghost{
		background: linear-gradient(180deg, #7b62a3 50%, #7b62a3 50%);
		background-color: #7b62a3;
		color: #fff;
	}
	.background-color-dragon{
	    background: linear-gradient(180deg, #53a4cf 50%, #f16e57 50%);
    	background-color: #53a4cf;
		color: #fff;
	}
	.background-color-dark{
		background: linear-gradient(180deg, #707070 50%, #707070 50%);
	    background-color: #707070;
	    color: #fff;
	}
</style>
