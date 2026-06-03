<template>
  <div class="saudacao">
    <p>Olá, <strong>{{ nome }}</strong>! Seja bem-vindo(a)!</p>
  </div>
</template>

<script>
export default {
  name: 'Saudacao',
  props: {
    nome: {
      type: String,
      required: true
    }
  }
}
</script>

<style scoped>
.saudacao {
  background-color: #e8f5e9;
  border-left: 4px solid #4caf50;
  padding: 12px 16px;
  border-radius: 4px;
  font-size: 1.1rem;
}
</style>