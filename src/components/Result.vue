<template>
  <div class="result">
    <div class="title">{{ results[resultTotal].title }}</div>
    <div class="desc">{{ results[resultTotal].desc }}</div>
  </div>
</template>
<script>
export default {
    props:['totalCorrect', 'results'],
    computed:{
        resultTotal(){
          let index = 0;
          this.results.forEach((e, i) => {
            if(e.min <= this.totalCorrect && e.max >= this.totalCorrect){
              index = i
            }
          });
          return index
        }
    }
}
</script>
 