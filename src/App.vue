<template>
  <div class="title">
    <h1>view-images</h1>
    <p>A images viewer plugin for Vue3</p>
  </div>
  <div class="images">
      <img
        v-for="(item, index) in images"
        :src="item"
        :key="index"
        @click="viewImages(index)"
      />
  </div>
  <p style="color: #eee">Photos from Jesse Luo</p>
  <div class="usage">
    <h1>usage</h1>
    <pre>
      &lt;template&gt;
        &lt;div class="images"&gt;
          &lt;img
              :src="item"
              v-for="(item, index) in images"
              :key="index"
              @click="viewImages(index)"
          /&gt;
        &lt;/div&gt;
      &lt;/template&gt;

      import view from 'view-images'
      import 'view-images/dist/style.css'

      export default {
        setup () {

          const images = [
            'https://../assets/01.jpeg',
            'https://../assets/02.jpeg',
            'https://../assets/03.jpeg',
            'https://../assets/04.jpeg',
            'https://../assets/05.jpeg',
          ]

          const viewImages = index => {
            view({ images, current: index })
          }

          return {
            viewImages,
            images
          }

        }
      }
    </pre>
  </div>
</template>

<script>
import view from './view-images'

// import view from 'view-images'
// import 'view-images/dist/style.css'

// import view from '../dist/view-images.es'
// import '../dist/style.css'

import img_01 from './assets/01.jpeg'
import img_02 from './assets/02.jpeg'
import img_03 from './assets/03.jpeg'
import img_04 from './assets/04.jpeg'
import img_05 from './assets/05.jpeg'

export default {
  setup () {

    const images = [ img_01 , img_02, img_03, img_04, img_05 ]

    const viewImages = index =>{
      view({ images, current: index })
    }

    return {
      viewImages,
      images
    }
  }
}

</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.images {
  display: flex;
  justify-content: center;
}
.images > img {
  width: 200px;
  height: 200px;
  object-fit: cover;
  margin: 5px;
  border-radius: 8px;
  cursor: pointer;
}
.usage {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.usage > pre {
  background: #f8f8f8;
  border-radius: 8px;
  text-align: left;
  width: 600px;
  padding: 30px 0;
}
</style>
