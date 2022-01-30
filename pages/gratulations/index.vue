<template>
  <div>
    <header class="header-bottom">
      <div class="header">
        <div>
          <a href="/"><img src="logo.svg" alt="" /></a>
        </div>

        <div>
          <Nuxt-link to="./" class="button-init-history"
            >Página Inicial</Nuxt-link>
        </div>
      </div>
    </header>

    <div class="container gratulations">
      <h2>Uhulllll!! Parabéns, <span>você</span> <br> venceu!</h2>
      <div class="img-grat">
        <img src="gratulations-people.svg" alt="">
      </div>
    </div>
    <footer class="footer">
        <p>EveHistory</p>
    </footer>
  </div>
</template>

<script>
export default {
  name: "play1",
  data(){
      return {
          correctPlayOne: false,
          outcomeIncorrect: false,
          outcomeTwoInc: false,
          visibleExit: false,
          visibleExitTwo: false,
          nextFase: false
      }
  },
  methods: {
      playOneCorrect(){
        correct.style.backgroundColor = 'yellowGreen'
        const btn = document.querySelectorAll('.btn-else')
        btn.forEach((bt) => {
            bt.setAttribute('disabled', 'true')
        })
        this.correctPlayOne = true
        this.nextFase = true
      },

      outcomeOneIncorrect(){
        const btn = document.querySelectorAll('.btn-else')
        const correct = document.getElementById('correct')
        correct.setAttribute('disabled', 'true')
        btn[0].style.backgroundColor = 'red'
        btn.forEach((bt) => {
          bt.setAttribute('disabled', 'true')
        })
        this.outcomeIncorrect = true
        this.visibleGameOver()
      },
      
      outcomeTwoIncorrect(){
        const btn = document.querySelectorAll('.btn-else')
        const correct = document.getElementById('correct')
        correct.setAttribute('disabled', 'true')
        btn[0].setAttribute('disabled', 'true')
        btnTree.style.backgroundColor = 'red'
        this.outcomeTwoInc = true
        this.visibleGameOverTwo()
      },

      visibleGameOver(){
        this.visibleExit = true
      },

      visibleGameOverTwo(){
        this.visibleExitTwo = true
      }
  }
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,400;0,700;1,400;1,500&display=swap");

* {
  box-sizing: border-box;
  padding: 0;
  margin: 0;
  list-style-type: none;
  text-decoration: none;
  font-family: "Poppins", sans-serif;
}

body{
    overflow-y: visible;
}

.container {
  max-width: 1000px;
  padding: 0 25px;
  margin: 20px auto;
}

.gratulations h2{
  font-size: 2.1rem;
  font-weight: 800;
  text-align: center;
}

.gratulations h2 span{
  color: #4D61FC;
}

.img-grat{
  display: flex;
  justify-content: center;
  height: 350px;
}

.header-bottom{
  border-bottom: 1px solid rgba(0, 0, 0, 0.05);
}

.header{
    padding: 24px;
    max-width: 1000px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin: 0 auto;
}

.button-init-history{
    font-size: 16px;
    font-weight: 800;
    color: #fff;
    background: #0000FF;
    border: none;
    padding: 10px 20px;
    border-radius: 3px;
    transition: .4s;
    text-decoration: none;
}

.button-init-history:hover{
    background: #4c04d1;
    text-decoration: none;
    color: #fff;
}

/* footer */

.footer{
  background: #4D61FC;
  color: #fff;
  width: 100vw;
  height: 10vh;
  position: fixed;
  bottom: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}

.footer p{
  font-size: 1.1rem;
  font-weight: 800;
}
</style>