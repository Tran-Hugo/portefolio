<template>
  <header>
      <h1>Hugo</h1>
      <nav class="navbar_links" :class="{open: isOpen}">
          <ul>
              <a href="#home"><li class="links li_home active">Accueil</li></a>
              <a href="#about"><li class="links li_about">À propos</li></a>
              <a href="#technologies"><li class="links li_technologies">Technologies</li></a>
              <a href="#projets"><li class="links li_projets">Projets</li></a>
          </ul>
      </nav>
      <div class="toggle-button" @click="isOpen = !isOpen">
          <i v-if="!isOpen" class="fa-solid fa-bars"></i>
          <i v-else class="fas fa-times"></i>
      </div>
  </header>
</template>

<script>
export default {
    data(){
        return{
            isOpen: false,
        }
    },
}
</script>

<style lang="scss">
@import '~/assets/scss/_responsive.scss';
header{
    display: flex;
    justify-content: space-evenly;
    width:100%;
    max-height: 8vh;
    position: fixed;
    top: 0;
    left: 0;
    color: white;
    animation: 0.5s unscroll ease-in;
    z-index: 10;
    h1{
        margin: 1rem 0 0 0;
    }
    nav{
        width: 30rem;
        ul{
            display: flex;
            justify-content: space-between;
            margin: 1rem 1rem 0 0;
            height: 4rem;
            align-items: center;
            list-style-type: none;
            font-size: 1.5rem;
        }
    }
}
ul a{
    color: unset;
    text-decoration: none;
    &:hover{
        color: unset;
    }
}
.scrolled {
    animation: 0.5s scroll ease-in;
    background-color: white;
    color: black;  
    box-shadow: 2px 3px 8px -2px rgba(0,0,0,0.23);

}
@keyframes scroll {
    from {
        background-color: unset;
        color:white;
    }
    to {
        background-color: white;
        color: black;
    }
}
@keyframes unscroll{
    from {
        background-color: white;
        color: black;
    }
    to {
        background-color: unset;
        color:white;
    }
}
.toggle-button{
      display: none;
      position: absolute;
      top: .75rem;
      right: 1rem;
      font-size: 3.5rem;
  }
.active{
    font-weight: bold;
    transform: scale(1.1);
    transition: all 300ms cubic-bezier(0.075, 0.82, 0.165, 1);
}

@media #{$small-up}{
  header{
    flex-direction: column;
    max-height: unset;
    background-color: #5555554f;
    min-height: 8vh;
  }
  nav{
    width: unset !important;
    height: 0;
    opacity: 0;
    transition: all .5s ease;
    visibility: hidden;
    ul {
        flex-direction: column;
        height: fit-content !important;
        width: 100%;
        li{
            padding: 1rem;
        }
    }
  } 
  .toggle-button{
      display: flex;
  }
  .open{
      height: fit-content;
      opacity: 1;
      visibility: visible;
    
  }
}
</style>