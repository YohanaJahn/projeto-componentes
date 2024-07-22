<script setup>
import { ref } from 'vue'

const user = ref({
  nome: '',
  sobrenome: '',
  email: '',
  dataNasc: '',
  cidade: '',
  estado: '',
  hobbies: [],
  langProg: '',
  biografia: ''
})

const userPass = ref({
  senha: '',
  confSenha: ''
})

const states = [
  { uf: 'AC', name: 'Acre' },
  { uf: 'AL', name: 'Alagoas' },
  { uf: 'AP', name: 'Amapá' },
  { uf: 'AM', name: 'Amazonas' },
  { uf: 'BA', name: 'Bahia' },
  { uf: 'CE', name: 'Ceará' },
  { uf: 'DF', name: 'Distrito Federal' },
  { uf: 'ES', name: 'Espírito Santo' },
  { uf: 'GO', name: 'Goiás' },
  { uf: 'MA', name: 'Maranhão' },
  { uf: 'MT', name: 'Mato Grosso' },
  { uf: 'MS', name: 'Mato Grosso do Sul' },
  { uf: 'MG', name: 'Minas Gerais' },
  { uf: 'PA', name: 'Pará' },
  { uf: 'PB', name: 'Paraíba' },
  { uf: 'PR', name: 'Paraná' },
  { uf: 'PE', name: 'Pernambuco' },
  { uf: 'PI', name: 'Piauí' },
  { uf: 'RJ', name: 'Rio de Janeiro' },
  { uf: 'RN', name: 'Rio Grande do Norte' },
  { uf: 'RS', name: 'Rio Grande do Sul' },
  { uf: 'RO', name: 'Rondônia' },
  { uf: 'RR', name: 'Roraima' },
  { uf: 'SC', name: 'Santa Catarina' },
  { uf: 'SP', name: 'São Paulo' },
  { uf: 'SE', name: 'Sergipe' },
  { uf: 'TO', name: 'Tocantins' }
]

const mostrarResultado = ref(false)

function salvarPerfil() {
  if (userPass.value.senha == userPass.value.confSenha) {
    mostrarResultado.value = true
  } else {
    alert('!Senha não é a Mesma!')
  }
}
</script>

<template>
  <main>
    <h1>Editor de Perfil</h1>
    <transition name="form" mode="out-in">
      <div v-if="mostrarResultado" class="perfil">
        <p v-for="(value, key) of user" :key="key">{{ key }}: {{ value }}</p>

        <button type="submit" @click="mostrarResultado = false">Voltar</button>
      </div>
      <div v-else class="editPerfil">
        <form @submit.prevent="salvarPerfil()" validate>
          <div class="container-col3">
            <div class="col-3">
              <label for="">Nome: </label>
              <input type="text" v-model="user.nome" minlength="3" required />
            </div>

            <div class="col-3">
              <label for="">Sobrenome: </label>
              <input type="text" v-model="user.sobrenome" minlength="3" required />
            </div>
            <div class="col-3">
              <label for="">Email: </label>
              <input type="email" v-model="user.email" required />
            </div>
          </div>
          <div class="container-col5">
            <div class="col-5">
              <label for="">Cidade: </label>
              <input type="text" v-model="user.cidade" />
            </div>
            <div class="col-5">
              <label for="">Estado: </label>
              <select v-model="user.estado">
                <option selected disabled value="">Selecionar...</option>
                <option v-for="state of states" :key="state.uf" :value="state.uf">
                  {{ state.name }}
                </option>
              </select>
            </div>
            <div class="col-5">
              <label for="">Data de Nascimento: </label>
              <input type="date" v-model="user.dataNasc" />
            </div>
            <div class="col-5">
              <label for="">Senha: </label>
              <input type="password" v-model="userPass.senha" required />
            </div>

            <div class="col-5">
              <label for="">Confirme a senha: </label>
              <input type="password" v-model="userPass.confSenha" required />
            </div>
          </div>

          <div class="container-col2">
            <div class="hobbies col-2">
              <p>Hobbies:</p>

              <input type="checkbox" value="games" v-model="user.hobbies" />
              <label>Games</label>

              <input type="checkbox" value="fotografia" v-model="user.hobbies" />
              <label>Fotografia</label>

              <input type="checkbox" value="culinaria" v-model="user.hobbies" />
              <label>Culinária</label>

              <input type="checkbox" value="musica" v-model="user.hobbies" />
              <label>Música</label>
            </div>
            <div class="langProg col-2">
              <p>Linguagens de programação:</p>
              <input type="radio" v-model="user.langProg" value="Java" id="langJava" />
              <label for="langJava">Java</label>
              <input type="radio" v-model="user.langProg" value="JavaScript" id="langJs" />
              <label for="langJs">JavaScript</label>
              <input type="radio" v-model="user.langProg" value="C++" id="langC++" />
              <label for="langC++">C++</label>
              <input type="radio" v-model="user.langProg" value="Python" id="langPython" />
              <label for="langPython">Python</label>
            </div>
          </div>
          <div class="container-col1">
            <div class="col-1">
              <h3 class="textCenter">Biografia</h3>
              <textarea name="Biography" id="Biography" v-model="user.biografia"></textarea>
            </div>
          </div>
          
          <button type="submit">Verificar</button>
        </form>
      </div>
    </transition>
  </main>
</template>

<style scoped>
main h1 {
  color: #000000;
}
.form-enter-active,
.form-leave-active {
  transition: opacity 0.5s ease;
}

.form-enter-from,
.form-leave-to {
  opacity: 0;
}
label {
  display: inline-block;
  color: #000000;
}
input,
select {
  margin-right: 6rem;
  background-color: #f2ebdc;
  color: #000000;
}
.options:hover {
  transition-delay: 100ms;
  transition-duration: 500ms;
  transition-timing-function: linear;
  background-color: #8f866f;
  color: #0e3e27;
}

div {
  text-align: left;
}

.container-col1 {
  display: grid;
  grid-template-columns: auto;
}
.col-1 {
  margin-top: 20px;
  grid-column: auto;
}
.col-1 textarea {
  display: flex;
  margin-right: auto;
  margin-left: auto;
  background-color: #ffffff;
  color: #000000;
  border-radius: 6px;
}

.container-col2 {
  display: grid;
  grid-template-columns: auto auto;
  grid-template-rows: 1fr;
}
.col-2 {
  margin: 10px 10px 10px 0;
}
.langProg input,
.hobbies input {
  margin: 0 5px 0 15px;
}

.container-col3 {
  display: grid;
  grid-template-columns: auto auto auto;
}
.col-3 {
  display: flex;
  flex-direction: column;
  margin: 10px;
  flex: 0 0 auto;
}

.container-col5 {
  display: grid;
  grid-template-columns: auto auto auto auto auto;
}
.col-5 {
  display: flex;
  flex-direction: column;
  margin: 10px;
}
.textCenter {
  text-align: center;
  font-weight: bolder;
  margin: 10px;
}

button {
  padding: 1rem;
  transition-delay: 50ms;
  transition-duration: 200ms;
  transition-timing-function: linear;
  background-color: #195973;
  color: #ffffff;
  border-radius: 8px;
  border: 2px solid #000000;
}
button:hover {
  transition-delay: 50ms;
  transition-duration: 200ms;
  transition-timing-function: linear;
  background-color: #00b7ff3b;
  color: #000000;
}
.perfil p {
  color: #000000;
  font-family: 'Baskervville SC', serif !important;
  font-size: 22px !important;
}
</style>