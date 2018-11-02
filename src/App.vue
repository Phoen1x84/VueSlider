<template>
	<div>
    <div :style="rangeValue.width">{{slider.blueprint}}
    <div v-if ="rangeValue.items!=null" v-for="item in rangeValue.items">
      <div v-for="item in rangeValue.items">
          <img v-bind:src="item.img" class="storage-item" v-bind:style="item.styleObject"/>
      </div>
  </div></div>
    <img v-bind:src="slider.value" style="width:100%; height=100%" class="storage-area">
		<h2 style="text-align:center">The Size Selected {{rangeValue.label}}</h2>

    <VueSlideBar v-model="slider.value" :data="slider.data" :range="slider.range" :processStyle="{ backgroundColor: '#d8d8d8' }"
		 @callbackRange="callbackRange">
			<template slot="tooltip" slot-scope="tooltip">
				<img src="static/images/rectangle-slider.svg">
			</template>
		</VueSlideBar>
	</div>
</template>

<script>
import VueSlideBar from "vue-slide-bar";


export default {
  data() {
    return {
      rangeValue: {},
      slider: {
        value:
          "https://uploads.codesandbox.io/uploads/user/ccdf5b36-b082-4813-94e2-f5b2feef495c/C0nH-floorplan-e3.svg",
        data: [
          "https://uploads.codesandbox.io/uploads/user/ccdf5b36-b082-4813-94e2-f5b2feef495c/Ky1j-floorplan-e6.svg",
          "https://uploads.codesandbox.io/uploads/user/ccdf5b36-b082-4813-94e2-f5b2feef495c/YC11-floorplan-e5.svg",
          "https://uploads.codesandbox.io/uploads/user/ccdf5b36-b082-4813-94e2-f5b2feef495c/0xHp-floorplan-e4.svg",
          "https://uploads.codesandbox.io/uploads/user/ccdf5b36-b082-4813-94e2-f5b2feef495c/C0nH-floorplan-e3.svg",
          "https://uploads.codesandbox.io/uploads/user/ccdf5b36-b082-4813-94e2-f5b2feef495c/P7SR-floorplan-e2.svg"
        ],
        range: [
          {
            label: "10sq",
          },
          {
            label: "20sq",
            isHide: true,
          },
          {
            label: "30sq",
           
          },
          {
            label: "40sq",
            isHide: true,
           
          },
          {
            label: "50sq",
            
          }
        ]
      }
    };
  },
  methods: {
    callbackRange(val) {
      this.rangeValue = val;
    }
  },
  components: {
    VueSlideBar
  }
};
</script>

<style>
.storage-area {
  position: relative;
  width: 100%;
}
.storage-item {
  position: absolute;
}
</style>
