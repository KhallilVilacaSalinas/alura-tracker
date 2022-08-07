<template>
  <div class="box formulario">
    <div class="columns">
      <div class="column is-7" role="form" aria-label="Formulario para criacao de uma nova tarefa">
        <input
            type="text"
            class="input"
            placeholder="Qual tarefa voce deseja iniciar?"
            v-model="descricao"
        />
      </div>
      <div class="column">
        <TemporizadorComponent @aoTemporizadorFinalizado="finalizarTarefa"/>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
  import { defineComponent } from "vue";
  import TemporizadorComponent from "@/components/Temporizador.vue";

  export default defineComponent({
    name: 'FormularioComponent',
    emits: ['aoSalvarTarefa'],
    components: {
      TemporizadorComponent
    },
    data () {
      return {
        descricao: ''
      }
    },
    methods: {
      finalizarTarefa (tempoDecorrido: number) {
        this.$emit('aoSalvarTarefa', {
          duracaoEmSegundos: tempoDecorrido,
          descricao: this.descricao
        })
        this.descricao = ''
      }
    }
  })
</script>

<style>
.formulario {
  color: var(--texto-primario);
  background-color: var(--bg-primario);
}
</style>
