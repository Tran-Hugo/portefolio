<template>
  <div>
    <TheHeader />
    <main>
        <div class="Home">
          <div class="intro">
            <p>Bonjour & Bienvenu</p>
            <div class="wrapper">
              <h1>Je suis </h1>
              <h1 class="typing"></h1>
            </div>
          </div>
          
        </div>
        <p>test</p>
    </main>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  data(){
    return{
      texts:["Hugo Tran.","Développeur Web.",],
      count:0,
      index:0,
      currentText:'',
      letter:'',
      typing: true,
    }
  },
  beforeMount () {
    window.addEventListener('scroll', this.bgColor);
  },
  beforeDestroy() {
    window.removeEventListener('scroll', this.bgColor);
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
        
      if(this.typing === true){
        this.letter = this.currentText.slice(0,++this.index)
        document.querySelector('.typing').textContent = this.letter;
        if(this.letter.length === this.currentText.length){
          this.typing = false;
        }
      } else {
        this.letter = this.currentText.slice(0,--this.index)
        document.querySelector('.typing').textContent = this.letter;
        if(this.letter.length === 0){
          this.typing = true;
          this.count++;
        }
      }
      if (this.typing === true){
        setTimeout(this.type, 300);
      } else {
        setTimeout(this.type, 50);
      }
    },
    bgColor(){
            if(window.scrollY != 0){
                document.querySelector('header').classList.add('scrolled');
            } else {
              document.querySelector('header').classList.remove('scrolled');
            }
    },
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
.intro{
  position: relative;
  left: 38%;
  p{
    font-size: 1.5rem;
  }
}
.wrapper{
  display: flex;
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
