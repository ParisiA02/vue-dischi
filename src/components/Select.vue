<template>
    <div class="select-container">
        <select name="select" class="select">
          <option value="All">All</option>
          <option value="Rock">Rock</option>
          <option value="Soul">Soul</option>
        </select>
    </div>
</template>

<script>
export default {
  name: 'Select',
}
</script>

<style lang="scss">
    .select-container{
      width: 60%;
      height: 50px;
      text-align: center;
      margin: 0 auto;
    
      .select{
        text-align: center;
          display: block;
          font-size: 16px;
          font-family: sans-serif;
          font-weight: 700;
          color: #444;
          line-height: 1.3;
          padding: 10px;
          width: 20%;
          max-width: 20%; /* useful when width is set to anything other than 100% */
          box-sizing: border-box;
          margin-top: 20px;
          border: 1px solid #aaa;
          box-shadow: 0 1px 0 1px rgba(0,0,0,.04);
          border-radius: .5em;
          -moz-appearance: none;
          -webkit-appearance: none;
          appearance: none;
  background-color: #fff;
      }
    }
</style>
