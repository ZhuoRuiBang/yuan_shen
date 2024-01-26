<<template>
  <div class="loading">
  <canvas ref="canvas"></canvas>
  </div>
</template>

<script setup>
import { onMounted, ref } from 'vue'
const canvas = ref();

onMounted(() => {
  const ctx = canvas.value.getContext('2d', {
    willReadFrequently:true
  });
  init(ctx)
  const imgData = ctx.getImageData(0, 0, canvas.value.width, canvas.value.height);
  let i = 0;
  setInterval(() => {
    imgData.data[i++]=255
    imgData.data[i++]=255
    imgData.data[i++]=255
    console.log(i);
    ctx.putImageData(imgData, 0, 0);
    
  },0)
})



function init(ctx) {
  const img = new Image()
  img.onload = () => {
    canvas.value.width=img.width
    canvas.value.height = img.height
    ctx.drawImage(img, 0, 0,img.width, img.height);
  }
  img.src = '/src/assets/images/loading.png'

}
</script>

<style lang="less" scoped>
.loading{
  display: flex;
  width: 100vw;
  height: 100vh;
  align-items: center;
  justify-content: center;
  background-color: rebeccapurple;
  canvas{
    display: block;
    border: 2px solid;
  }
}
</style>