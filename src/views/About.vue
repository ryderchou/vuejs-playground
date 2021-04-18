<template>
  <div class="about">
    <h1>This is an about page</h1>
    <div class="card-slider">
      <transition-group class="card-slider-items" tag="section">
        <div class="card-slider-item" v-for="item of showimg " :key="item.id" :data-id="item.id">
          <img :src="item.src" />
        </div>
      </transition-group>
    </div>
  </div>
</template>
<script>
export default {
  data () {
    return {
      now: 0,
      images: [
        { id: 1, src: 'https://picsum.photos/300/320?random=1' },
        { id: 2, src: 'https://picsum.photos/300/320?random=2' },
        { id: 3, src: 'https://picsum.photos/300/320?random=3' },
        { id: 4, src: 'https://picsum.photos/300/320?random=4' },
        { id: 5, src: 'https://picsum.photos/300/320?random=5' }
      ]
    }
  },
  computed: {
    allImages () {
      // 5 + 4
      const ary = []
      const total = this.images.length
      let count
      if (total > 0) {
        while (ary.length < 5 + 4) {
          count = Math.floor(ary.length / total)
          for (let i = 0; i < total; i++) {
            ary.push({ id: count + '-' + this.images[i].id, src: this.images[i].src })
          }
        }
      }
      return ary
    },
    showimg () {
      const start = this.now - 4
      return this.allImages.slice(start).concat(this.allImages.slice(0, start))
    }
  }
}
</script>

<style scoped>
.card-slider {
  display: flex;
  width: 100%;
  overflow: hidden;
}
.card-slider-items {
  display: flex;
  width: 100%;
  margin-left: calc(-1*25% * 2.5 );
}
.card-slider-item {
  flex: calc(25%-20px) 0 0;
  margin: 10px;
  background-color: bisque;
}
.img{
  width: 100%;

}
</style>
