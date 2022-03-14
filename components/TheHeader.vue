<template>
  <header>
    <div class="toggle_container">
      <h1>Hugo</h1>
      <div class="toggle-button" @click="isOpen = !isOpen">
        <i v-if="!isOpen" class="fa-solid fa-bars"></i>
        <i v-else class="fas fa-times"></i>
      </div>
    </div>

    <nav class="navbar_links" :class="{ open: isOpen }">
      <ul>
        <li class="links li_home active"><a href="#home">Accueil</a></li>
        <li class="links li_about"><a href="#about">À propos</a></li>
        <li class="links li_technologies">
          <a href="#technologies">Technologies</a>
        </li>
        <li class="links li_projets"><a href="#projets">Projets</a></li>
      </ul>
    </nav>
  </header>
</template>

<script>
export default {
  data() {
    return {
      isOpen: false,
    }
  },
}
</script>

<style lang="scss">
@import '~/assets/scss/_responsive.scss';
header {
  display: flex;
  justify-content: space-evenly;
  width: 100%;
  // max-height: 8vh;
  position: fixed;
  top: 0;
  left: 0;
  color: white;
  animation: 0.5s unscroll ease-in;
  z-index: 10;
  h1 {
    margin: 1rem 0 0 0;
  }
  nav {
    width: 30rem;
    ul {
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
ul a {
  color: unset;
  text-decoration: none;
  &:hover {
    color: unset;
  }
}
.scrolled {
  animation: 0.5s scroll ease-in;
  background-color: white;
  color: black;
  box-shadow: 2px 3px 8px -2px rgba(0, 0, 0, 0.23);
}
@keyframes scroll {
  from {
    background-color: unset;
    color: white;
  }
  to {
    background-color: white;
    color: black;
  }
}
@keyframes unscroll {
  from {
    background-color: white;
    color: black;
  }
  to {
    background-color: unset;
    color: white;
  }
}
.toggle {
  &-button {
    display: none;
    //   position: absolute;
    //   top: .75rem;
    //   right: 1rem;
    font-size: 3.5rem;
  }
}
.active {
  font-weight: bold;
  transform: scale(1.1);
  transition: all 300ms cubic-bezier(0.075, 0.82, 0.165, 1);
}

@media #{$small-up} {
  header {
    flex-direction: column;
    max-height: unset;
    background-color: white;
    color: black;
    min-height: 8vh;
    animation: unset;
    h1 {
      margin: 1rem 0 0 1rem;
    }
  }
  nav {
    width: unset !important;
    height: 0;
    opacity: 0;
    transition: all 0.5s ease;
    visibility: hidden;
    ul {
      flex-direction: column;
      height: fit-content !important;
      width: 100%;
      li {
        padding: 1rem;
        color: black;
      }
    }
  }
  .toggle {
    &-button {
      display: flex;
      margin-right: 0.5rem;
    }
    &_container {
      display: flex;
      justify-content: space-between;
    }
  }
  .open {
    height: fit-content;
    opacity: 1;
    visibility: visible;
  }
  .scrolled {
    animation: unset;
  }
}
@media screen and (max-height: 430px) {
  header {
    background-color: white;
    color: black;
    animation: unset;
  }
  .scrolled {
    animation: unset;
  }
}
</style>
