<script setup>
import { onMounted } from "vue";
import '@tensorflow/tfjs';
let model = null;
let tensorImg = null;
let img;
const loadmodel = async function () {
  /*  model = await tensor.loadGraphModel("https://tfhub.dev/tensorflow/tfjs-model/ssd_mobilenet_v2/1/default/1",{fromTFHub: true})
   //model = await tensor.loadGraphModel("../public/modeljsvprueba/model.json");
   console.log(model); */

}
/* loadmodel(); */
const makepredict = async function () {
  /* let result = await model.executeAsync(tensorImg)
  result.forEach(element => {
    console.log(element.bufferSync())
  }); */
  cocoSsd.load().then(model => {
    // detect objects in the image.
    model.detect(img).then(predictions => {
      console.log('Predictions: ', predictions);
    });
  });
}
onMounted(() => {
  img = document.getElementById('image');
  /* const image = document.getElementById("image");
  tensorImg = tensor.browser.fromPixels(image, 3);
  tensorImg = tensorImg.expandDims();  */
});
</script>


<template>
  <div id="main">
    <h1>Let's see those tensors!</h1>
    <div class="description">
      We're learning about working with images today!
    </div>
    <p>Add your code to index.js and then click the run button.</p>
    ./assets/images/lemons.jpg
    <img id="image" src="./assets/images/lemons.jpg" crossorigin="anonymous"
      style="width: 50%; height: 700px;" />
    <canvas id="newImage"></canvas>
  </div>
  <div>
    <form id="run-code">
      <button id="run" type="button" @click="makepredict()">Run</button>
    </form>
  </div>
</template>


