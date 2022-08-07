<template>
  <div class="box">
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
        this.descricao = ''
        console.log(tempoDecorrido);
        console.log(this.descricao);
      }
    }
  })
</script>
