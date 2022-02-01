<template>
    <div>
      <header class="header-bottom">
        <div class="header">
          <div>
            <a href="#"><img src="logo.svg" alt="" /></a>
          </div>
          
          <div>
           <Nuxt-link to="/plays" class="button-init-history">Iniciar História</Nuxt-link>
          </div>
        </div>
      </header>

      <section class="intro">
        <div class="intro-text">
          <h1>Embarque nessa <span class="crop-azul">aventura</span>,
            <span class="crop-azul">desafie</span> sua tomada de <span class="crop-azul">decisão</span> com trechos de histórias.
          </h1>
        </div>

        <div class="intro-img">
          <img src="people-img.svg" alt="people-img">
        </div>
      </section>

      <footer class="footer">
        <p>EveHistory</p>
      </footer>
    </div>
</template>

<script>
export default {
  name: "IndexPage",
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,400;0,700;1,400;1,500&display=swap");

*{
    box-sizing: border-box;
    padding: 0;
    margin: 0;
    list-style-type: none;
    text-decoration: none;
    font-family: 'Poppins', sans-serif;
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
    background: linear-gradient(to right, #0000FF, #9898eb);
    text-decoration: none;
    color: #fff;
}

/* INTRO */

.intro{
    max-width: 1000px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin: 100px auto 0 auto;
    padding: 0 24px;
}

.intro-text{
  max-width: 482px;
}

.intro-text h1{
  font-size: 1.765rem;
  font-weight: 700;
  line-height: 1.4;
  text-align: center;
}

.crop-azul{
  color: #4D61FC;
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

/* RESPONSIVE */

@media screen and (max-width: 860px){
  
  .intro-text h1{
    max-width: 300px;
    font-size: 1.37rem;
    margin-right: 20px;
  }

}

@media screen and (max-width: 768px){
  
  .intro-text h1{
    width: min(98%, 400px);
    font-size: 1.6rem;
    padding: 0 10px;
    margin-right: 0;
    margin-left: 30px;
    text-align: center;
  }

  .intro{
    max-width: 400px;
    display: block;
    margin: 100px auto 0 auto;
}


  .intro-img{
    display: none;
  }

}

</style>
