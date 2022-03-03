<template>
  <div>
    <TheHeader />
    <main id="main">
        <section class="Home" id="Home">
          <div class="intro">
            <p>Bonjour & Bienvenue</p>
            <div class="wrapper">
              <h1>Je suis </h1>
              <h1 class="typing"></h1>
            </div>
            <div class="reseaux">
              <a href="https://github.com/Tran-Hugo"><i class="fa-brands fa-github"></i></a>
              <a href="https://www.instagram.com/hugo.tran.790/"><i class="fa-brands fa-instagram-square"></i></a>
              <a href="https://www.linkedin.com/in/hugo-tran-202569233/"><i class="fa-brands fa-linkedin"></i></a>
              <a href="mailto:TranMSHugo@gmail.com"><i class="fa-solid fa-envelope"></i></a>
            </div>
            <a href="/CV.pdf" class="btn btn-5"><span>Télécharger CV</span></a>
            <a href="#about" class="bottom_arrow_a"><button class="bottom_arrow">˅</button></a>
          </div>
          
        </section>
        <section id="about">
          <h1 class="haut_de_page">À propos de moi </h1>
          <div class="asterisque_container">
            <div class="barre"></div>
            <h2>*</h2>
            <div class="barre"></div>
          </div>
          <p class="présentation">Je sors tout juste de la formation de
            développeur web et web mobile au centre
            de formation de l'Afpa à Créteil et je
            recherche activement un poste en
            alternance.
          </p>
          <div class="asterisque_container">
            <div class="barre"></div>
            <h2>*</h2>
            <div class="barre"></div>
          </div>
          <h1>Développeur</h1>
          <h3>Front-end · Back-end</h3>
          <p class="présentation">Au cours de cette formation, j'ai fais mes premiers pas en tant que développeur web et j'ai eu l'occasion d'étudier diverses technologies notamment des Frameworks Front-end et Back-end</p>
        </section>
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
  beforeDestroy() {
    document.getElementById("main").removeEventListener('scroll', this.bgColor);
  },
  mounted(){
    document.getElementById("main").addEventListener('scroll', this.bgColor);
    this.type();
    document.querySelectorAll('a[href^="#"]').forEach(anchor => {
    anchor.addEventListener('click', function (e) {
        e.preventDefault();

        document.querySelector(this.getAttribute('href')).scrollIntoView({
            behavior: 'smooth'
        });
    });
});
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
      // console.log(document.getElementById("main").scrollTop)
            if(document.getElementById("main").scrollTop != 0){
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
*{
  margin: 0;
  padding: 0;
}
main{
  scroll-snap-type: y mandatory;
  overflow-y:scroll;
  height: 100vh;
}
section{
  height: 92vh;
  scroll-snap-align: start;
}
/* #region Home */
.Home{
  height: 100vh;
  display: flex;
  align-items: center;
  color: white;
  background: linear-gradient(rgba(0,0,0,0.7),rgba(0,0,0,0.7)),url('~/assets/images/banner.jpg');
  background-size: cover;
  background-repeat: no-repeat;
  background-attachment: fixed;
}
.intro{
  position: relative;
  left: 38%;
    p{
      font-size: 1.5rem;
    }
}
.reseaux {
  width: 20rem;
  display: flex;
  justify-content: space-between;
  margin-top: 1rem;
  a{
    color: white;
    text-decoration: none;
      i{
        font-size: 2rem;
      }
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
.test{
  height: 30vh;
}
.btn {
  color: #fff;
  cursor: pointer;
  // display: block;
  font-size:16px;
  font-weight: 400;
  line-height: 3rem;
  margin: 0 0 2em;
  max-width: 10rem; 
  position: relative;
  text-decoration: none;
  text-transform: uppercase;
  border-radius: 2.25rem;
  width: 100%; 
  margin: 2rem 0 0 0;
    &:hover { text-decoration: none; }
}
.btn-5 {
  border: 0 solid;
  box-shadow: inset 0 0 20px rgba(255, 255, 255, 0);
  outline: 1px solid;
  outline-color: rgba(255, 255, 255, .5);
  outline-offset: 0px;
  text-shadow: none;
  transition: all 1250ms cubic-bezier(0.19, 1, 0.22, 1);
} 

.btn-5:hover {
  border: 1px solid;
  box-shadow: inset 0 0 20px rgba(255, 255, 255, .5), 0 0 20px rgba(255, 255, 255, .2);
  outline-color: rgba(255, 255, 255, 0);
  outline-offset: 15px;
  text-shadow: 1px 1px 2px #427388; 
  color: #fff;
}
.bottom_arrow{
    background-color: unset;
    width: 2rem;
    height: 4rem;
    border: 1px solid rgba(255,255,255,0.5);
    border-radius: 1.5rem;
    color: white;
    &_a{
      position: relative;
      top: 20rem;
      left: 3.5rem;
      animation: bounce 1s ease infinite;
    }
}

@keyframes bounce {
  from{
    top: 20rem;
  }
  50%{
    top: 19.5rem;
  }
  to{
    top: 20rem;
  }
}
/* #endregion */
/* #region about */
#about{
  display: flex;
  flex-direction: column;
  align-items: center;
}
.haut_de_page{
  padding-top: 2rem;
}
.asterisque_container{
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 6rem;
    h2{
      font-size: 3rem;
      margin-top: 1rem;
    }
}
.barre{
  border: 1px solid rgba(194, 194, 194,0.73);
  width: 2rem;
}
.présentation{
  width: 33rem;
  text-align: center;
  color: grey;
}
/*#endregion */
</style>
