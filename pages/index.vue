<template>
  <div>
    <div class="card test" style="width: 18rem;">
      <img src="http://www.logic-sunrise.com/images/validation/in-1904976125.png" class="card-img-top" alt="...">
      <div class="card-body">
        <h5 class="card-title red">Card title</h5>
        <p class="card-text">Some quick example text to build on the card title and make up the bulk of the card's content.</p>
        <a href="#" class="btn btn-primary">Go somewhere</a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
}
</script>

<style lang="scss">
@import '~/assets/scss/_variables.scss';
.card{
  .red {
    color:$red;
  }
}

</style>
