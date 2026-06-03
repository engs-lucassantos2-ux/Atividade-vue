<template>
  <div class="contador">
    <p>Contagem atual: <strong>{{ contagem }}</strong></p>
    <p class="limite-info">Limite configurado: {{ limite }}</p>
    <div class="botoes">
      <button @click="incrementar">+ Incrementar</button>
      <button @click="resetar">Resetar</button>
    </div>
    <p v-if="limiteAtingido" class="aviso">
      🚨 Limite de {{ limite }} atingido!
    </p>
  </div>
</template>

<script>
export default {
  name: 'Contador',
  props: {
    limite: {
      type: Number,
      default: 5
    }
  },
  emits: ['limite-atingido'],
  data() {
    return {
      contagem: 0,
      limiteAtingido: false
    }
  },
  methods: {
    incrementar() {
      if (this.contagem < this.limite) {
        this.contagem++
        if (this.contagem === this.limite) {
          this.limiteAtingido = true
          this.$emit('limite-atingido', this.contagem)
        }
      }
    },
    resetar() {
      this.contagem = 0
      this.limiteAtingido = false
    }
  }
}
</script>

<style scoped>
.contador {
  background-color: #e3f2fd;
  border-left: 4px solid #2196f3;
  padding: 12px 16px;
  border-radius: 4px;
}

.limite-info {
  font-size: 0.9rem;
  color: #555;
}

.botoes {
  display: flex;
  gap: 8px;
  margin: 8px 0;
}

button {
  padding: 6px 14px;
  border: none;
  border-radius: 4px;
  cursor: pointer;
  background-color: #2196f3;
  color: white;
  font-size: 0.95rem;
}

button:hover {
  background-color: #1976d2;
}

.aviso {
  color: #c62828;
  font-weight: bold;
  margin-top: 8px;
}
</style>