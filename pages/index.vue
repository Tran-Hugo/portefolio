<template>
  <div>
    <TheHeader />
    <main>
        <div class="Home">
          <div class="wrapper">
            <h1>Je suis </h1>
            <h1 class="typing">hi</h1>
          </div>
        </div>
    </main>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  data(){
    return{
      texts:["Hugo Tran","Développeur Web",],
      count:0,
      index:0,
      currentText:'',
      letter:'',
    }
  },
  mounted(){
    this.type();
  },
  methods:{
    type(){
      if(this.count===this.texts.length){
        this.count = 0;
      }
      this.currentText = this.texts[this.count];
      this.letter = this.currentText.slice(0,++this.index)
      document.querySelector('.typing').textContent = this.letter;
      
      if(this.letter.length === this.currentText.length){
        this.count++;
        this.index = 0;
      }
      setTimeout(this.type, 300);
    }
  }
}
</script>

<style lang="scss">
@import '~/assets/scss/_variables.scss';
.Home{
  height: 100vh;
  display: flex;
  align-items: center;
  color: white;
  background: linear-gradient(rgba(0,0,0,0.7),rgba(0,0,0,0.7)),url('~/assets/images/banner.jpg');
  background-size: cover;
}
.wrapper{
  display: flex;
  position: relative;
  left: 38%;
  h1{
    font-size: 3rem;
  }
}
.typing{
  position: relative;
  margin-left: 1rem;
  font-weight: bold;

  &::after{
    content:"";
    position:absolute;
    right: -0.5rem;
    width: 1px;
    height: 100%;
    border-right: 2px solid white;
    animation: blink 0.8s infinite ease;
  }
}
@keyframes blink{
  0%{
    opacity: 0;
  }
  100%{
    opacity: 1;
  }
}



</style>
