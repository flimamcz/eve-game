<template>
  <div>
    <header class="header-bottom">
      <div class="header">
        <div>
          <a href="/"><img src="logo.svg" alt="" /></a>
        </div>

        <div>
          <Nuxt-link to="./" class="button-init-history"
            >Desistir</Nuxt-link>
        </div>
      </div>
    </header>

    <div class="container">
      <div class="text">
        <h2>Tenha certeza na escolha, existe somente uma chance!</h2>
        <p>
          <span>1 - </span>
            Você acordou na floresta tonto e com uma grande dor de cabeça, sem nenhuma
            memória de como foi parar ali. Um barulho cada vez mais intenso foi o que
            despertou você desse apagão. Após abrir os olhos e levantar-se, você observa uma
            manada de búfalos vindo em sua direção, a pouquíssimos metros de distância. O
            que você faz?
        </p>
      </div>

      <ul class="alternative">
        <li>
          <span class="options">A</span> - <button class="btn-else" @click="outcomeOneIncorrect" id="btnZero">Corre o mais rápido possível</button>
          <span v-if="outcomeIncorrect" class="outFalseOne">A sua corrida não foi suficiente para superar a da manada. Você morreu</span>
          <div>
            <Nuxt-link v-if="visibleExit" class="button-game-over" to="./">Sair</Nuxt-link>
          </div>
        </li>


        <li>
          <span class="options">B</span> - <button @click="playOneCorrect" id="correct">Sobe na Arvóre</button> 
          <span v-if="correctPlayOne" class="outTruePlayOne">Você sobe na árvore e escapa por pouco da manada.</span>
            <Nuxt-link v-if="nextFase" to="/playTwo" class="next-fase">Próxima Fase</Nuxt-link>
          </li>

        <li>
          <span class="options">C</span> - <button id="btnTree" class="btn-else" @click="outcomeTwoIncorrect">Se finge de morto</button>
          <span v-if="outcomeTwoInc" class="outFalseOne">Os búfalos podem até ter acreditado, mas isso não os impediu de passar
            por cima de você. Morreu atropelado.
          </span>
          <div>
            <Nuxt-link v-if="visibleExitTwo" class="button-game-over" to="./">Sair</Nuxt-link>
          </div>
        </li>
      </ul>
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
  max-width: 700px;
  padding: 0 25px;
  margin: 0 auto;
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
    background: #fa3030;
    text-decoration: none;
    color: #fff;
}

.text h2 {
  font-size: 1.2rem;
  font-weight: 800;
  text-align: center;
  margin-bottom: 32px;
  margin-top: 32px;
}

.text p {
  font-size: 1rem;
  text-align: center;
  margin-top: 5px;
}

.text p span {
  margin-right: 10px;
}

.alternative {
  margin-top: 24px;
  margin-bottom: 120px;
}

.alternative li button {
  font-size: 1.1rem;
  font-weight: 500;
  width: 500px;
  background: #4d61fc;
  border-radius: 4px;
  color: #fff;
  margin: 0 auto;
  padding: 15px 20px;
  border: none;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.alternative li button:hover {
  background: #7988f5;
}

.alternative li button:disabled:hover {
  background: #4d61fc;
}

.alternative li {
  margin-bottom: 16px;
}

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

/* styles outcomes */

.outTruePlayOne{
    display: block;
    text-align: center;
    margin-bottom: 10px;
}

.outFalseOne{
    color: red;    
    display: block;
    text-align: center;
    margin-bottom: 10px;
}

.button-game-over{
  color: #ff0000;
}

.button-game-over{
  font-size: 1rem;
  color: #fff;
  background: #ff0000;
  padding: 8px 15px;
  width: 150px;
  height: 30px;
  border-radius: 2px;
  margin-top: 10px;
}

.next-fase{
  font-size: 1rem;
  color: #fff;
  background: yellowgreen;
  padding: 8px 15px;
  width: 150px;
  height: 30px;
  border-radius: 2px;
  margin-top: 10px;
}

@media screen and (max-width: 600px) {
  .alternative li button {
    font-size: 1rem;
    width: 320px;
    padding: 15px;
  }

  .text p {
    font-size: 0.875rem;
  }

}
</style>