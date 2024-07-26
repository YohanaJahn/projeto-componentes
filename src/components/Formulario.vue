<script setup>
import { ref } from 'vue';
const emit = defineEmits(['mostrarFormulario'])
const usuario = ref({
  nome: '',
  email: '',
  senha: '',
  confirmacaoSenha: '',
  dataNascimento: '',
  endereco: '',
  cidade: '',
  estado: '',
  hobbies: [],
  linguagens: '',
  biografia: ''
})


function salvarPerfil() {
  if (usuario.value.senha == usuario.value.confirmacaoSenha) {
    console.log(usuario.value.senha, usuario.value.confirmacaoSenha)
    emit("mostrarFormulario", usuario)
  } else {
    alert('!Senha não é a Mesma!')
  }
}


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
</script>
<template>
  <div>
    <h1>Formulário de Edição de Perfil</h1>
    <form @submit.prevent="salvarPerfil()" validate>
      <div class="container-col3">
        <div class="col-3">
          <label for="">Nome: </label>
          <input type="text" v-model="usuario.nome" minlength="3" required />
        </div>

        <div class="col-3">
          <label for="">Sobrenome: </label>
          <input type="text" v-model="usuario.sobrenome" minlength="3" required />
        </div>
        <div class="col-3">
          <label for="">Email: </label>
          <input type="email" v-model="usuario.email" required />
        </div>
      </div>
      <div class="container-col5">
        <div class="col-5">
          <label for="">Cidade: </label>
          <input type="text" v-model="usuario.cidade" />
        </div>
        <div class="col-5">
          <label for="">Estado: </label>
          <select id="stateField" v-model="usuario.estado">
            <option selected disabled value="">Selecionar...</option>
            <option v-for="state of states" :key="state.uf" :value="state.uf">
              {{ state.name }}
            </option>
          </select>
        </div>
        <div class="col-5">
          <label for="">Data de Nascimento: </label>
          <input type="date" v-model="usuario.dataNasc" />
        </div>
        <div class="col-5">
          <label for="">Senha: </label>
          <input type="password" v-model="usuario.senha" required />
        </div>

        <div class="col-5">
          <label for="">Confirme a senha: </label>
          <input type="password" v-model="usuario.confirmacaoSenha" required />
        </div>
      </div>

      <div class="container-col2">
        <div class="hobbies col-2">
          <p>Hobbies:</p>

          <input type="checkbox" value="games" v-model="usuario.hobbies" />
          <label>Games</label>

          <input type="checkbox" value="fotografia" v-model="usuario.hobbies" />
          <label>Fotografia</label>

          <input type="checkbox" value="culinaria" v-model="usuario.hobbies" />
          <label>Culinária</label>

          <input type="checkbox" value="musica" v-model="usuario.hobbies" />
          <label>Música</label>
        </div>
        <div class="langProg col-2">
          <p>Linguagens de programação:</p>
          <input type="radio" v-model="usuario.linguagens" value="Java" id="langJava" />
          <label for="langJava">Java</label>
          <input type="radio" v-model="usuario.linguagens" value="JavaScript" id="langJs" />
          <label for="langJs">JavaScript</label>
          <input type="radio" v-model="usuario.linguagens" value="C++" id="langC++" />
          <label for="langC++">C++</label>
          <input type="radio" v-model="usuario.linguagens" value="Python" id="langPython" />
          <label for="langPython">Python</label>
        </div>
      </div>
      <div class="container-col1">
        <div class="col-1">
          <h3 class="textCenter">Biografia</h3>
          <textarea name="Biography" id="Biography" v-model="usuario.biografia"></textarea>
        </div>
      </div>
      <button type="submit">enviar</button>
    </form>
  </div>
</template>