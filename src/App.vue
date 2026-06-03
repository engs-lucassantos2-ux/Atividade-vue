<template>
  <div id="app">
    <h1>Atividade Vue.js</h1>

    <!-- Seção 1: Saudação -->
    <section>
      <h2>1. Saudação Personalizada</h2>
      <input
        v-model="nomeDigitado"
        type="text"
        placeholder="Digite seu nome..."
      />
      <Saudacao v-if="nomeDigitado" :nome="nomeDigitado" />
    </section>

    <!-- Seção 2 e 3: Contador + comunicação pai-filho -->
    <section>
      <h2>2 e 3. Contador com Evento para o Pai</h2>
      <label>
        Defina o limite:
        <input v-model.number="limiteEscolhido" type="number" min="1" style="width: 60px;" />
      </label>
      <Contador :limite="limiteEscolhido" @limite-atingido="aoAtingirLimite" />
      <p v-if="mensagemPai" class="mensagem-pai">
        📩 Pai recebeu o evento: contagem chegou em <strong>{{ mensagemPai }}</strong>
      </p>
    </section>
  </div>
</template>

<script>
import Saudacao from './components/Saudacao.vue'
import Contador from './components/Contador.vue'

export default {
  name: 'App',
  components: {
    Saudacao,
    Contador
  },
  data() {
    return {
      nomeDigitado: '',
      limiteEscolhido: 5,
      mensagemPai: null
    }
  },
  methods: {
    aoAtingirLimite(valor) {
      this.mensagemPai = valor
    }
  }
}
</script>

<style>
#app {
  font-family: Arial, sans-serif;
  max-width: 600px;
  margin: 40px auto;
  padding: 0 20px;
}

h1 {
  border-bottom: 2px solid #333;
  padding-bottom: 8px;
}

section {
  margin-bottom: 32px;
}

h2 {
  font-size: 1.1rem;
  color: #333;
  margin-bottom: 10px;
}

input[type="text"],
input[type="number"] {
  padding: 6px 10px;
  border: 1px solid #aaa;
  border-radius: 4px;
  margin-bottom: 10px;
  font-size: 1rem;
}

.mensagem-pai {
  background-color: #fff3e0;
  border-left: 4px solid #ff9800;
  padding: 10px 14px;
  border-radius: 4px;
  margin-top: 10px;
}
</style>