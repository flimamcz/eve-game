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
        <h2>A hora da verdade!</h2>
        <p>
          <span>3 - </span>
          Você finalmente consegue ler o bilhete: “Vamos fazer parecer um acidente. Misture o
        conteúdo deste frasco na comida dele. O remédio vai começar a fazer efeito depois
        de 30 minutos. Quando ele estiver completamente apagado, leve-o até o pé da
        árvore mais alta no início da floresta e direcione a manada de búfalos em sua
        direção. Estaremos esperando no laboratório ao norte do acampamento.” O que
        você faz?
        </p>
      </div>

      <ul class="alternative">
        <li>
          A - <button class="btn-else" @click="playOneCorrect"  id="correct" >Foge e liga para a polícia</button>
          <span v-if="correctPlayOne"  class="outTruePlayOne"> Você informa a polícia o que aconteceu e passa a localização do
            laboratório. Chegando lá ela se depara com um sítio de produção de cocaína
            e prende todos os presentes. As evidências sugerem que você ainda pode
            estar em perigo, por este motivo a polícia lhe coloca no programa de
            proteção à testemunha e você sobrevive para vivenciar uma nova história.
            Parabéns, você ganhou!
          </span>
          <div>
             <Nuxt-link v-if="nextFase" to="/gratulations" class="next-fase" >Avançar</Nuxt-link>
          </div>
        </li>

        <li>
          B - <button @click="outcomeTwoIncorrect" id="btnZero">Amarra o homem e vai ao laboratório</button> 
          <span v-if="outcomeTwoInc" class="outFalseOne" >Você amarra o homem e se dirige ao laboratório. Você entra
            silenciosamente e consegue chegar ao salão principal, onde você observa
            aproximadamente umas 10 pessoas. Um passo em falso entrega a sua
            posição e você é alvejado. Você morreu.
          </span>
            <Nuxt-link v-if="visibleExitTwo"  class="button-game-over"  to="./">Sair</Nuxt-link>
          </li>

        <li>
          C - <button id="btnTree" class="btn-else" @click="outcomeOneIncorrect">Mata o homem, pega a marreta e vai ao laboratório</button>
          <span v-if="outcomeIncorrect" class="outFalseOne"> Você mata o homem, pega a marreta e se dirige ao laboratório. Ao avistar
            2 guardas na entrada, confiante de si e seus feitos recentes, você corre na
            direção dos guardas, segurando a marreta com as duas mãos levantadas
            acima da sua cabeça e gritando “LEEROY JEENKINS!!!!”. Infelizmente, o
            efeito surpresa foi prejudicado e os guardas não tiveram dificuldade em
            alvejá-lo. Você morreu.
          </span>
          <div>
            <Nuxt-link v-if="visibleExit" class="button-game-over" to="./">Sair</Nuxt-link>
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
        document.getElementById('btnZero').setAttribute('disabled', 'true')
        const btn = document.querySelectorAll('.btn-else')
        btn.forEach((bt) => {
            bt.setAttribute('disabled', 'true')
        })
        this.correctPlayOne = true
        this.nextFase = true
      },

      outcomeOneIncorrect(){
        const btn = document.querySelectorAll('.btn-else')
        document.getElementById('btnZero').setAttribute('disabled', 'true')
        const correct = document.getElementById('correct')
        correct.setAttribute('disabled', 'true')
        btn[1].style.backgroundColor = 'red'
        btn.forEach((bt) => {
          bt.setAttribute('disabled', 'true')
        })
        this.outcomeIncorrect = true
        this.visibleGameOver()
      },
      
      outcomeTwoIncorrect(){
        const correct = document.getElementById('correct')
        correct.setAttribute('disabled', 'true')
        document.getElementById('btnTree').setAttribute('disabled', 'true')
        document.getElementById('btnZero').style.backgroundColor = 'red'
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
    background: #fa3030;;
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
    margin-bottom: 10px;
    text-align: center;
    padding-top: 8px;
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
}

.next-fase{
  font-size: 1rem;
  color: #fff;
  background: yellowgreen;
  padding: 8px 15px;
  width: 160px;
  height: 30px;
  border-radius: 2px;
}
</style>