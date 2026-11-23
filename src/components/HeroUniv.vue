<script setup>

import { ref } from 'vue'

const nome = ref('')
const email = ref('')
const modalidade = ref('')

const msgerro = ref('')
const sucesso = ref('')

function adicionarParaDesconto() {

  if (!nome.value.trim() || !email.value.trim() || !modalidade.value.trim()) {
    msgerro.value = "Preencha todos os campos!"

    setTimeout(() => {
      msgerro.value = ''
    }, 1500)
    return
  }

  sucesso.value = "Seu desconto será enviado por e-mail!"

    setTimeout(() => {
      sucesso.value = ''
    }, 10000)

    nome.value = ''
    email.value = ''
    modalidade.value = ''
}

</script>

<template>
  <section id="hero">
    <div class="container">
      <div class="hero__grid">
        <div class="hero__texts">
          <span class="tag">
            Processo Seletivo 2026 Aberto
          </span>
          <h1>Construa o seu futuro na <span class="realce">UniversaVUE</span>
          </h1>

          <p class="hero__text">
            Cursos de Graduação, Tecnólogo e Pós-Graduação
            com metodologia moderna, flexibilidade total para a
            sua rotina e mensalidades que cabem no seu bolso.
          </p>

          <div class="actions">
            <button class="btn btn__solid">Explorar Cursos</button>
            <button class="btn btn__outline">Formas de ingresso</button>
          </div>
        </div>

        <div class="form__box">
          <h2 class="form__title">Garanta sua bolsa de estudos</h2>
          <p>Preencha os dados abaixo e receba condições especiais no seu e-mail.</p>
          <form class="form" @submit.prevent="adicionarParaDesconto">
            <p class="msg__erro" v-if="msgerro">
              {{ msgerro }}
            </p>
            <p class="msg__sucesso" v-if="sucesso">
              {{ sucesso }}
            </p>
            <div class="group__form">
              <label for="nome">Nome completo</label>
              <input placeholder="Digite seu nome" class="field" v-model="nome" id="nome"/>
            </div>

            <div class="group__form">
              <label for="email">Email</label>
              <input placeholder="email@gmail.com" class="field" v-model="email" id="email"/>
            </div>

            <div class="group__form">
              <label for="modalidade">Modalidade</label>
              <select class="field" v-model="modalidade" id="modalidade">
                <option value="" disabled>Selecione</option>
                <option value="Graduação EAD">Graduação EAD</option>
                <option value="Pós-Graduação EAD">Pós-Graduação EAD</option>
                <option value="Cursos Abertos EAD">Cursos Abertos EAD</option>
              </select>
            </div>
            <button class="btn btn__solid" type="submit">Quero meu desconto</button>
          </form>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
#hero {
  background-color: #9f0712;
  color: white;
  min-height: 90vh;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 4rem 0;
}


.container {
  margin: 0 auto;
  max-width: 524px;
  padding: 0 1rem;
}

.hero__grid {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.tag {
  color: yellow;
  border-radius: 25px;
  border: 1px solid yellow;
  font-size: 12px;
  padding: 3px 1rem;
  margin-bottom: 1rem;
  display: block;
  width: fit-content;
}

.realce {
  color: yellow;
}

.hero__text {
  margin-top: 1rem;
  font-weight: lighter;
}

.actions {
  display: flex;
  gap: 1rem;
  margin: 2rem 0;
}

.btn {
  cursor: pointer;
  border: 0;
  border-radius: 10px;
  cursor: pointer;
  padding: 10px;
}

.btn__solid {
  background-color: yellow;
  color: black;
  font-weight: bold;
}

.btn__outline {
  border: 2px solid white;
  color: white;
  font-weight: bold;
  background-color: transparent;
}


.form__box {
  display: flex;
  flex-direction: column;
  gap: 10px;
  border-radius: 10px;
  background-color: white;
  color: black;
  width: 100%;
  padding: 2rem 1.4rem;
}


.form {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.form__title {
  color: #9f0712;
}

.group__form {
  display: flex;
  flex-direction: column;
}

label {
  font-size: 14px;
  display: block;
  font-weight: bold;
  padding: 0 0 3px;
}

.field {
  border: 1px solid #ccc;
  border-radius: 6px;
  padding: 10px;
}

@media(min-width:710px) {
  .hero__grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    align-items: center;
    gap: 23px;
  }

  .container {
    margin: 0 auto;
    max-width: 992px;
    padding: 0 1rem;
  }
}


.msg__erro {
  background-color: pink;
  color: red;
  font-weight: bold;
  padding: 1rem 3rem;
}

.msg__sucesso{
  background-color: green;
  color: white;
  font-weight: bold;
  padding: 1rem 3rem;
}
</style>
