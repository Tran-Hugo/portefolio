<template>
  <div>
    <TheHeader />
    <main id="main" @scroll="scrolling()">
        <section class="Home" id="home">
          <div class="intro">
            <p class="show home_mark">Bonjour & Bienvenue</p>
            <div class="wrapper">
              <h1>Je suis </h1>
              <h1 class="typing"><strong></strong></h1>
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
          <h2 class="haut_de_page">À propos de moi </h2>
          <div class="asterisque_container">
            <div class="barre"></div>
            <h2>*</h2>
            <div class="barre"></div>
          </div>
          <p class="présentation">Basé en région parisienne, je sors tout juste de la formation de
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
          <p class="présentation2">Au cours de cette formation, j'ai fais mes premiers pas en tant que développeur web et j'ai eu l'occasion d'étudier diverses technologies notamment des Frameworks Front-end et Back-end. Je souhaite évoluer en tant que développeur et monter en compétence.</p>
          <div class="asterisque_container">
            <div class="barre"></div>
            <h2>*</h2>
            <div class="barre"></div>
          </div>
          <img class="photo" src="@/assets/images/photo.jpg" alt="photo de profil">
        </section>
        <section id="technologies">
          <h2 class="haut_de_page text-center">Technologies</h2>
          <div class="asterisque_container">
            <div class="barre"></div>
            <h2>*</h2>
            <div class="barre"></div>
          </div>
            <div class="tech_container">
              <div class="tech_container_1">
                <div class="show-1 show- show">
                  <p>Html 5 & CSS 3</p>
                  <img src="@/assets/images/html-css.png" alt="html.png">
                </div>
                <div class="show-3 show- show">
                  <p>JavaScript</p>
                  <img src="@/assets/images/javascript.png" alt="javascript.png">
                </div>
                <div class="show-5 show- show">
                  <p>Vue.js</p>
                  <img src="@/assets/images/vue.png" alt="vue.png">
                </div>
                <div class="show-7 show- show">
                  <p>Nuxt.js</p>
                  <img src="@/assets/images/nuxt.svg" alt="nuxt.svg">
                </div>
              </div>
              <img class="img_responsive" src="@/assets/images/responsive.png" alt="responsive.png">
              <div class="tech_container_2">
                <div class="show-2 show- show">
                  <img src="@/assets/images/php-logo.svg" alt="php8.png">
                  <p>Php 8</p>
                </div>
                <div class="show-4 show- show">
                  <img src="@/assets/images/symfony.png" alt="symfony.png">
                  <p>Symfony 5</p>
                </div>
                <div class="show-6 show- show">
                  <img src="@/assets/images/api-platform.png" alt="api-platform.png">
                  <p>Api Platform</p>
                </div>
                <div class="show-8 show- show">
                  <img src="@/assets/images/mysql.png" alt="mysql.png">
                  <p>MySQL</p>
                </div>
              </div>
            </div>
        </section>
        <section id="projets">
          <div class="la_notule">
            <div class="la_notule_band">
              <p>Site e-commerce pour une librairie fictive "La Notule"</p>
            </div>
          </div>
          <h2 class="text-center">La Notule</h2>
          <div class="la_notule_tech">
            <h3>Technologies :</h3>
            <ul>
              <li>Vue.js 3</li>
              <li>Symfony 5</li>
              <li>Api Platform</li>
            </ul>
          </div>
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
  mounted(){
    this.type();
    this.observe();
    this.smooth();
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
    scrolling(){
            if(document.getElementById("main").scrollTop != 0){
                document.querySelector('header').classList.add('scrolled');
            } else {
              document.querySelector('header').classList.remove('scrolled');
            }

            const navLi = document.querySelectorAll('.links');
            const sec = document.querySelectorAll('section');
            let current = "";
            sec.forEach(section=>{
              const sectionTop = section.offsetTop;
              if(document.getElementById("main").scrollTop>sectionTop-100){
                current = section.getAttribute('id');
              }
            })
              navLi.forEach(li => {
                li.classList.remove('active');
                if(li.classList.contains("li_"+current)){
                  li.classList.add('active')
                }
              })
    },
    smooth(){
      document.querySelectorAll('a[href^="#"]').forEach(anchor => {
      anchor.addEventListener('click', function (e) {
        e.preventDefault();

        document.querySelector(this.getAttribute('href')).scrollIntoView({
            behavior: 'smooth'
        });
      });
    });
    },
    observe(){
      const ratio = .7;
      const options = {
        root: null,
        rootMargin: '0px',
        threshold: ratio
      }

      const handleInteserct = function(entries, observer){
        entries.forEach(function(entry){
          // if(entry.intersectionRatio > ratio && Array.from(entry.target.classList).includes('home_mark')){
          if(entry.intersectionRatio > ratio){
            entry.target.classList.add('show-ing')
            observer.unobserve(entry.target);
          }
        })
      }

      var observer = new IntersectionObserver(handleInteserct, options);
      document.querySelectorAll('.show').forEach(function(r){
        observer.observe(r)
      })
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
  scroll-padding-top:8vh ;
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
  font-size: 3rem;
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
  &2{
    @extend .présentation;
    width: 60rem;
  }
}
.photo{
  height: 14rem;
  width:14rem;
  border: 1px solid;
  border-radius: 7rem;
  margin-top: 3rem;
  object-fit: cover;
  object-position: top;
}
/*#endregion */
/*#region technologies*/
#technologies{
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: #8080800a;
}
.tech_container{
  display: flex;
  justify-content: space-around;
  align-items: center;
  width: 80%;
  height: 70%;
  &_1{
    width: 25%;
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    height: 100%;
    .show-{
      justify-content: flex-end;
    }
  }
  &_2{
    width: 25%;
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    height: 100%;
    .show-{
      justify-content: flex-start;
    }
  }
}
.show-{
  display: flex;
  align-items: center;
  height: 8.3rem;
  width: 100%;
  opacity: 0;
  transform: translateY(+30px);
  &ing{
    opacity: 1;
    transform: translateY(0);
    transition: 2s;
  }
  &1{
    transition-delay: .2s;
    position: relative;
    left: 13rem;
  }
  &2{
    transition-delay: .4s;
    position: relative;
    right: 13rem;
  }
  &3{
    transition-delay: .6s;
  }
  &4{
    transition-delay: .8s;
  }
  &5{
    transition-delay: 1s;
  }
  &6{
    transition-delay: 1.2s;
  }
  &7{
    transition-delay: 1.4s;
    position: relative;
    left: 13rem;
  }
  &8{
    transition-delay: 1.6s;
    position: relative;
    right: 13rem;
  }
  p{
    font-size: 2rem;
    font-weight: bold;
  }
  img{
    height: 6.9rem;
    width: 7.3rem;
    margin-inline: 1rem;
  }
}


.img_responsive{
  height: 20rem;
  width: 20rem;
}
/*#endregion */
/*#region Projets*/
#projets{
  display: flex;
  flex-direction: column;
  align-items: center;
}
.la_notule{
  width: 100%;
  height: 40vh;
  background-image:url("@/assets/images/la_notule.png") ;
  background-size: cover;
  background-repeat: no-repeat;
  background-attachment: fixed;
  background-position-y: 8vh;
  display: flex;
  align-items: flex-end;
  &_band{
    background-color: rgba(128, 128, 128,  70%);
    width: 100%;
    height: 7vh;
    color: white;
    font-size: 1.5rem;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  &_tech{
    display: flex;
    width: 90%;
    ul {
      list-style-type: none;
      display: flex;
      align-items: center;
      justify-content: space-around;
      padding: 0;
      margin: 0;
      width: 20vw;
      li{
        border: 1px solid;
        border-radius: 3rem;
        padding: .3rem 1.1rem;
        &:hover{
          color: white;
          background-color: grey;
          transition: 500ms;
        }
      }
    }
  }
}

/*#endregion */
</style>
