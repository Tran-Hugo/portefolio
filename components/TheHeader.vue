<template>
  <header>
      <h1>Hugo Tran</h1>
      <nav>
          <ul>
              <li>Accueil</li>
              <li>Technologies</li>
              <li>Projets</li>
              <li>Contact</li>
          </ul>
      </nav>
  </header>
</template>

<script>
export default {
    mounted(){

    },
    methods:{
        
    }
}
</script>

<style lang="scss">
header{
    display: flex;
    justify-content: space-evenly;
    width:100%;
    max-height: 5rem;
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
.scrolled {
    animation: 0.5s scroll ease-in;
    background-color: white;
    color: black;
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
</style>