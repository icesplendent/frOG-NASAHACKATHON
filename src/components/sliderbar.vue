<script setup></script>

<template>
	<div class="w-full h-20 flex flex-col justify-center items-center">
		<div id="sliderbar" class="w-full flex flex-col justify-center items-center">
			<div class="season-mode flex flex-row">
				<button
        @click="
            emitSummer();
            buttonSound();
          "
					type="button"
					id = "summerBtn"
					dir="ltr"
					class="text-white bg-[#099B9B] hover:bg-[#8AB4B1] rounded-s-lg text-sm px-4 py-1 text-center font-jura"
          >Summer
				</button>
				<button
        @click="
            emitWinter();
            buttonSound();
          "
					type="button"
					id="winterBtn"
					dir="rtl"
					class="text-black bg-white hover:bg-[#8AB4B1] font-medium rounded-s-lg text-sm px-4 py-1 text-center font-jura"
				>Winter 
				</button>
			</div>
      <input v-model="sildervalue" @input="emitSliderValue" type="range" class="myslider mt-2" min="2002" max="2023">
		<!-- <span class="rangeValue">{{sildervalue}}</span> -->
		<div class="years flex flex-row justify-between items-cente mt-2 mb-5">
			<p class="year">2002</p>
			<p class="year">2003</p>
			<p class="year">2004</p>
			<p class="year">2005</p>
			<p class="year">2006</p>
			<p class="year">2007</p>
			<p class="year">2008</p>
			<p class="year">2009</p>
			<p class="year">2010</p>
			<p class="year">2011</p>
			<p class="year">2012</p>
			<p class="year">2013</p>
			<p class="year">2014</p>
			<p class="year">2015</p>
			<p class="year">2016</p>
			<p class="year">2017</p>
			<p class="year">2018</p>
			<p class="year">2019</p>
			<p class="year">2020</p>
			<p class="year">2021</p>
			<p class="year">2022</p>
			<p class="year">2023</p>
		</div>
	</div>
	</div>
</template>

<script>
export default {
	data () {
		return {
			sildervalue: 2023,
			summer: true,
			winter: false
		}
	},
	methods: {
		emitSliderValue() {
			this.$emit("sliderChange", this.sildervalue);
		},
		emitSummer() {
			const summerBtn = document.getElementById('summerBtn');
			const winterBtn = document.getElementById('winterBtn');
			console.log("summerBtn click");
			if(this.summer){
				// this.summer = this.summer;
			} 
			else{
				console.log("change to summer");
				this.winter = false;
				this.summer = true;
				summerBtn.style.backgroundColor = '#099B9B';
				summerBtn.style.color = 'white';
				winterBtn.style.backgroundColor = 'white';
				winterBtn.style.color = 'black';	
			}
			this.$emit("changeToSummer", this.summer);
		},
		emitWinter() {
			const summerBtn = document.getElementById('summerBtn');
			const winterBtn = document.getElementById('winterBtn');
			console.log("winterBtn click");
			if(this.winter){
				// this.winter = this.winter;
			} 
			else{
				console.log("change to winter");
				this.winter = true;
				this.summer = false;
				summerBtn.style.backgroundColor = 'white';
				summerBtn.style.color = 'black';
				winterBtn.style.backgroundColor = '#099B9B';
				winterBtn.style.color = 'white';
			}
			this.$emit("changeToWinter", this.summer);
		}
	}
}
</script>

<style scoped>
.myslider {
	/* position: absolute; */
	bottom: 1rem;
	width: 68%;
	height: 5px;
	/* transform: translate(-50%, -50%); */
	-webkit-appearance: none;
	appearance: none;
	background-color: #ffffff;
	/* border: 1px solid #ffffff;
	border-radius: 1rem; */
  opacity: 0.7;
  transition: opacity 0.2s ease-in;
  -webkit-transition: opacity 0.2s ease-in;
}

.myslider:hover {
  opacity: 1;
}

.myslider::-webkit-slider-thumb {
  -webkit-appearance: none;
  appearance: none;
  height: 20px;
  width: 10px;
  background-color: #868686;
  /* border: 1px solid #000000;
	border-radius: 1rem; */
  -webkit-transition: all 0.3s ease-in;
  transition: all 0.3s ease-in;
}

.myslider::-webkit-slider-thumb:hover {
  box-shadow: 2px 2px 20px rgba(0, 0, 0, 0, 4);
}

.rangeValue {
  color: #ffffff;
  text-align: center;
}

.years {
	width: 71%;
}
.year{
	color: #ffffff;
	font-size: 0.5rem;
	font-family: "Jura";
}

/* TODO: css of button */
.summerBtn {
	background-color: #099B9B;
    color: rgb(255, 255, 255);
}

.winterBtn {
  background-color: rgb(255, 255, 255);
  color: rgb(0, 0, 0);
}


.font-jura {
	font-family: "Jura";
}

</style>
