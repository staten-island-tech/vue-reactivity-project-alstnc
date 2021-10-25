<template>
<div>
  <div class="character-builder">
    <div id="preview-img">
      <img class="background-img" src="../img/backgrounds/bg4.jpg" />
      <img class="sprite body" :src="bodyImage" />
      <img class="sprite eyes" :src="eyeImage" />
      <img class="sprite hair" :src="hairImage" />
      <img class="sprite shirt" :src="shirtImage" />
      <img class="sprite pants" :src="pantsImage" />
      <img class="sprite shoes" src="../assets/img/shoes/shoes.png" />
    </div>
    <div class="selection">
      <h1 class="category-text">Body</h1>
      <img class="body-box" v-for="(body, index) in bodies" :key="body.url" :src="body.url" @click="updateBody(index)"/>
      <h1 class="category-text">Eyes</h1>
      <img class="body-box" v-for="(eye, index) in eyes" :key="eye.url" :src="eye.url" @click="updateEyes(index)"/>
      <h1 class="category-text">Hair</h1>
      <div class="hair-container">
        <img class="body-box" v-for="(hair, index) in hair" :key="hair.url" :src="hair.url" @click="updateHair(index)"/>
      </div>
      <h1 class="category-text">Shirt</h1>
      <div class="shirt-container">
        <img class="body-box" v-for="(shirt, index) in shirts" :key="shirt.url" :src="shirt.url" @click="updateShirt(index)"/>
      </div>
      <h1 class="category-text">Pants</h1>
      <img class="body-box" v-for="(pant, index) in pants" :key="pant.url" :src="pant.url" @click="updatePants(index)"/>
    </div>
  </div>
  <button class="eightbit-btn" @click="saveImage()">Save Image</button>
</div>
</template>

<script>
import * as htmlToImage from 'html-to-image';
export default {
  name: 'Builder',
  data() {
    return {
      bodySelection: null,
      selectedBody: 0,
      selectedEyes: 0,
      selectedPants: 0,
      selectedHair: 0,
      selectedShirt: 0,
      bodies: [
        {
          name: "Tone 1",
          url: require("@/assets/img/body/body1.png")
        },
        {
          name: "Tone 2",
          url: require("@/assets/img/body/body2.png")
        },
        {
          name: "Tone 3",
          url: require("@/assets/img/body/body3.png")
        },
        {
          name: "Tone 4",
          url: require("@/assets/img/body/body4.png")
        },
        {
          name: "Tone 5",
          url: require("@/assets/img/body/body5.png")
        },
      ],
      eyes: [
        {
          name: "Black Eyes",
          url: require("@/assets/img/eyes/eyes-black.png")
        },
        {
          name: "Brown Eyes",
          url: require("@/assets/img/eyes/eyes-brown.png")
        },
        {
          name: "Blue Eyes",
          url: require("@/assets/img/eyes/eyes-blue.png")
        },
        {
          name: "Green Eyes",
          url: require("@/assets/img/eyes/eyes-green.png")
        },
        {
          name: "Gray Eyes",
          url: require("@/assets/img/eyes/eyes-gray.png")
        },
        {
          name: "Pink Eyes",
          url: require("@/assets/img/eyes/eyes-pink.png")
        },
        {
          name: "Red Eyes",
          url: require("@/assets/img/eyes/eyes-red.png")
        },
      ],
      pants: [
        {
          name: "Gray Pants",
          url: require("@/assets/img/pants/pants-gray.png")
        },
        {
          name: "Brown Pants",
          url: require("@/assets/img/pants/pants-brown.png")
        },
        {
          name: "Blue Pants",
          url: require("@/assets/img/pants/pants-blue.png")
        },
        {
          name: "Green Pants",
          url: require("@/assets/img/pants/pants-green.png")
        },
        {
          name: "Pink Pants",
          url: require("@/assets/img/pants/pants-pink.png")
        },
        {
          name: "Red Pants",
          url: require("@/assets/img/pants/pants-red.png")
        },
        {
          name: "Purple Pants",
          url: require("@/assets/img/pants/pants-purple.png")
        },
        {
          name: "White Pants",
          url: require("@/assets/img/pants/pants-white.png")
        },
      ],
      hair: [
        {
          name: "Black Buzzcut",
          url: require("@/assets/img/hair/buzz-black.png")
        },
        {
          name: "Black Short Hair",
          url: require("@/assets/img/hair/man-black.png")
        },
        {
          name: "Black Afro",
          url: require("@/assets/img/hair/fro-black.png")
        },
        {
          name: "Black Long Hair",
          url: require("@/assets/img/hair/long-black.png")
        },
        {
          name: "Black Braids",
          url: require("@/assets/img/hair/braid-black.png")
        },
        {
          name: "Black French Braids",
          url: require("@/assets/img/hair/french-black.png")
        },
        {
          name: "Brown Buzzcut",
          url: require("@/assets/img/hair/buzz-brown.png")
        },
        {
          name: "Brown Short Hair",
          url: require("@/assets/img/hair/man-brown.png")
        },
        {
          name: "Brown Afro",
          url: require("@/assets/img/hair/fro-brown.png")
        },
        {
          name: "Brown Long Hair",
          url: require("@/assets/img/hair/long-brown.png")
        },
        {
          name: "Brown Braids",
          url: require("@/assets/img/hair/braid-brown.png")
        },
        {
          name: "Brown French Braids",
          url: require("@/assets/img/hair/french-brown.png")
        },
        {
          name: "Blonde Buzzcut",
          url: require("@/assets/img/hair/buzz-blonde.png")
        },
        {
          name: "Blonde Short Hair",
          url: require("@/assets/img/hair/man-blonde.png")
        },
        {
          name: "Blonde Afro",
          url: require("@/assets/img/hair/fro-blonde.png")
        },
        {
          name: "Blonde Long Hair",
          url: require("@/assets/img/hair/long-blonde.png")
        },
        {
          name: "Blonde Braids",
          url: require("@/assets/img/hair/braid-blonde.png")
        },
        {
          name: "Blonde French Braids",
          url: require("@/assets/img/hair/french-blonde.png")
        },
        {
          name: "Pink Buzzcut",
          url: require("@/assets/img/hair/buzz-pink.png")
        },
        {
          name: "Pink Short Hair",
          url: require("@/assets/img/hair/man-pink.png")
        },
        {
          name: "Pink Afro",
          url: require("@/assets/img/hair/fro-pink.png")
        },
        {
          name: "Pink Long Hair",
          url: require("@/assets/img/hair/long-pink.png")
        },
        {
          name: "Pink Braids",
          url: require("@/assets/img/hair/braid-pink.png")
        },
        {
          name: "Pink French Braids",
          url: require("@/assets/img/hair/french-pink.png")
        },
        {
          name: "Blue Buzzcut",
          url: require("@/assets/img/hair/buzz-blue.png")
        },
        {
          name: "Blue Short Hair",
          url: require("@/assets/img/hair/man-blue.png")
        },
        {
          name: "Blue Afro",
          url: require("@/assets/img/hair/fro-blue.png")
        },
        {
          name: "Blue Long Hair",
          url: require("@/assets/img/hair/long-blue.png")
        },
        {
          name: "Blue Braids",
          url: require("@/assets/img/hair/braid-blue.png")
        },
        {
          name: "Blue French Braids",
          url: require("@/assets/img/hair/french-blue.png")
        },
                {
          name: "Red Buzzcut",
          url: require("@/assets/img/hair/buzz-red.png")
        },
        {
          name: "Red Short Hair",
          url: require("@/assets/img/hair/man-red.png")
        },
        {
          name: "Red Afro",
          url: require("@/assets/img/hair/fro-red.png")
        },
        {
          name: "Red Long Hair",
          url: require("@/assets/img/hair/long-red.png")
        },
        {
          name: "Red Braids",
          url: require("@/assets/img/hair/braid-red.png")
        },
        {
          name: "Red French Braids",
          url: require("@/assets/img/hair/french-red.png")
        },
      ],
      shirts: [
        {
          name: "Black Shirt",
          url: require("@/assets/img/shirt/shirt-black.png")
        },
        {
          name: "Brown Shirt",
          url: require("@/assets/img/shirt/shirt-brown.png")
        },
        {
          name: "Blue Shirt",
          url: require("@/assets/img/shirt/shirt-blue.png")
        },
        {
          name: "Green Shirt",
          url: require("@/assets/img/shirt/shirt-green.png")
        },
        {
          name: "Pink Shirt",
          url: require("@/assets/img/shirt/shirt-pink.png")
        },
        {
          name: "Red Shirt",
          url: require("@/assets/img/shirt/shirt-red.png")
        },
        {
          name: "Purple Shirt",
          url: require("@/assets/img/shirt/shirt-purple.png")
        },
        {
          name: "White Shirt",
          url: require("@/assets/img/shirt/shirt-white.png")
        },
        {
          name: "Black Dress",
          url: require("@/assets/img/shirt/dress-black.png")
        },
        {
          name: "Brown Dress",
          url: require("@/assets/img/shirt/dress-brown.png")
        },
        {
          name: "Blue Dress",
          url: require("@/assets/img/shirt/dress-blue.png")
        },
        {
          name: "Green Dress",
          url: require("@/assets/img/shirt/dress-green.png")
        },
        {
          name: "Pink Dress",
          url: require("@/assets/img/shirt/dress-pink.png")
        },
        {
          name: "Red Dress",
          url: require("@/assets/img/shirt/dress-red.png")
        },
        {
          name: "Purple Dress",
          url: require("@/assets/img/shirt/dress-purple.png")
        },
        {
          name: "White Dress",
          url: require("@/assets/img/shirt/dress-white.png")
        },
      ]
    }
  },
  methods: {
    updateBody(index) {  
      this.selectedBody = index
    },
    updateEyes(index) {  
      this.selectedEyes = index
    },
    updatePants(index) {  
      this.selectedPants = index
    },
    updateHair(index) {  
      this.selectedHair = index
    },
    updateShirt(index) {  
      this.selectedShirt = index
    },
    saveImage() {
      htmlToImage.toJpeg(document.getElementById('preview-img'), { quality: 0.95 })
      .then(function (dataUrl) {
        var link = document.createElement('a');
        link.download = 'my-character.jpeg';
        link.href = dataUrl;
        link.click();
      });
    }
  },
  computed: {
    bodyImage() {
      return this.bodies[this.selectedBody].url;
    },
    eyeImage() {
      return this.eyes[this.selectedEyes].url;
    },
    pantsImage() {
      return this.pants[this.selectedPants].url;
    },
    hairImage() {
      return this.hair[this.selectedHair].url;
    },
    shirtImage() {
      return this.shirts[this.selectedShirt].url;
    },
  }
}
</script>

<style>
.character-builder {
  display: flex;
  justify-content: center;
  padding: 50px;
}
.selection {
  width: 512px;
  height: 560px;
  margin-left: 20px;
  border: solid 5px rgba(0,0,0,0.5);
  background-color: rgba(255,255,255,0.5);
}
.category-text {
  color: white;
  font-size: 16px;
}
.body-box {
  width: 48px;
  height: 48px;
  border: solid 2px;
  margin: 5px;
}
.body-box:hover {
  cursor: pointer;
  border: solid white 2px;
  transition: all 0.4s;
}
.hair-container {
  max-width: 400px;
  max-height: 55px;
  padding: 10px;
  overflow-x: hidden;
  margin: auto;
}
.shirt-container {
  max-width: 300px;
  max-height: 55px;
  padding: 10px;
  overflow-x: hidden;
  margin: auto;
}
#preview-img {
  width: 512px;
  height: 560px;
  border: solid 5px rgba(0,0,0,0.5);
  border-radius: 2px;
  outline: solid 4px #5B2B2A;
  box-shadow: 0 0 0 10px black;
  background-image: url("../img/backgrounds/bg4.jpg");
  background-size: 125%;
  background-repeat: no-repeat;
  background-position: bottom;
  display: flex;
  justify-content: center;
  position: relative;
  top: 0;
  left: 0;
}

.sprite {
  width: 75%;
  height: 75%;
}

.body {
  position: relative;
  top: 0;
  left: 0;
  z-index: 1;
}

.background-img {
  position: absolute;
  width: 100%;
  height: 100%;
  z-index: 0;
}

.eyes {
  position: absolute;
  z-index: 2;
}

.hair {
  position: absolute;
  z-index: 3;
}

.shirt {
  position: absolute;
  z-index: 5;
}

.pants {
  position: absolute;
  z-index: 4;
}

.shoes {
  position: absolute;
  z-index: 8;
}

.eightbit-btn {
    background: #76c442;
    display: inline-block;
    position: relative;
    text-align: center;
    font-size: 30px;
    padding: 20px;
    margin-bottom: 40px;
    font-family: 'RetroComputer';
    text-decoration: none; 
    color: white;
    box-shadow: inset -4px -4px 0px 0px #4AA52E;
}
    .eightbit-btn:hover,
    .eightbit-btn:focus {
        background: #5ea132;
        box-shadow: inset -4px*1.5 -4px*1.5 0px 0px #4AA52E;
        cursor: pointer;
        transition: all 0.4s;
    }

    .eightbit-btn:active {
        box-shadow: inset 4px 4px 0px 0px #4AA52E;
    }

    .eightbit-btn:before,
    .eightbit-btn:after {
    content: '';
        position: absolute;
        width: 100%;
        height: 100%;
        box-sizing: content-box;
    }

    .eightbit-btn:before {
        top: -6px;
        left: 0;
        border-top: 6px black solid;
        border-bottom: 6px black solid;
    }

    .eightbit-btn:after {
        left: -6px;
        top: 0;
        border-left: 6px black solid;
        border-right: 6px black solid;
    }

</style>
