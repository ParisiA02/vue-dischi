<template>
  <div class="disc">
        <div class="img-container">
            <img :src="details.poster" :alt="details.title">
        </div>
        <div class="text-container">
        <div class="text-title">
            {{details.title.toUpperCase()}}
        </div>
        <div class="artist-text">
            {{details.author}}
        </div>
        <div class="year-text">
            {{details.year}}
        </div>
        </div>
    </div>
</template>

<script>
export default {
  name: 'Disc',
  props: {
      details: Object,
  }
}
</script>

<style lang="scss">
    .disc{
        width: 200px;
        min-height: 360px;
        margin-bottom: 20px;
        background-color: #2E3A46;

        .img-container{
          width: 80%;
          height: 150px;
          margin: 20px auto;

          img{
            width: 100%;
            height: 100%;
            object-fit: cover;
          }
        }

        .text-container{
          width: 80%;
          margin: 0 auto;
          text-align: center;

          .text-title{
            font-size: 20px;
            margin-bottom: 20px;
            color: white;
          }

          .artist-text{
            font-size: 20px;
            color: #7A8080;
          }
          .year-text{
            font-size: 20px;
            color: #7A8080;
          }
        }
    }
</style>
