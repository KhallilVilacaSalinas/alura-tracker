<template>
  <BoxComponent>
    <div class="columns">
      <div class="column is-10">
        {{tarefa.descricao || 'Tarefa sem descricao'}}
      </div>
      <div class="column">
        <CronometroComponent
            :tmpEmSegundos="tarefa.duracaoEmSegundos"
        />
      </div>
    </div>
  </BoxComponent>
</template>

<script lang="ts">
import {defineComponent, PropType} from "vue";
import CronometroComponent from "@/components/Cronometro.vue";
import ITarefa from "@/interfaces/ITarefa";
import BoxComponent from "@/components/Box.vue";

export default defineComponent( {
  name: "TarefaComponent",
  components: {
    CronometroComponent,
    BoxComponent
  },
  props: {
    tarefa: {
      type: Object as PropType<ITarefa>,
      required: true
    }
  }
})
</script>

<style scoped>

</style>