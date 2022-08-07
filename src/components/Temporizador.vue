<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <CronometroComponent :tmpEmSegundos="tmpEmSegundos"/>

    <ButtonComponent @clicado="iniciar" icone="fas fa-play" texto="play" :desabilitado="cronometroRodando"/>
    <ButtonComponent @clicado="finalizar" icone="fas fa-stop" texto="stop" :desabilitado="!cronometroRodando"/>

  </div>
</template>

<script lang="ts">
import {defineComponent} from "vue";
import CronometroComponent from "@/components/Cronometro.vue";
import ButtonComponent from "@/components/Button.vue";

export default defineComponent({
  name: "TemporizadorComponent",
  emits: ['aoTemporizadorFinalizado'],
  components: {
    ButtonComponent,
    CronometroComponent
  },
  data() {
    return {
      tmpEmSegundos: 0,
      cronometro: 0,
      cronometroRodando: false
    }
  },
  methods: {
    iniciar() {
      this.cronometroRodando = true
      this.cronometro = setInterval(() => {
        this.tmpEmSegundos += 1
      }, 1000)
    },
    finalizar() {
      this.cronometroRodando = false
      clearInterval(this.cronometro)
      this.$emit('aoTemporizadorFinalizado', this.tmpEmSegundos)
      this.tmpEmSegundos = 0
    }
  }
});
</script>