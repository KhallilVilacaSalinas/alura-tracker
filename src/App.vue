<template>
  <main class="columns is-gapless is-multiline modo-escuro">
    <div class="column is-one-quarter">
      <BarraLateral/>
    </div>
    <div class="column is-three-quarter conteudo">
      <div class="formulario">
        <FormularioComponent @aoSalvarTarefa="salvarTarefa"/>
      </div>
      <div class="lista">
        <TarefaComponent
            v-for="(tarefa, index) in tarefas" :key="index"
            :tarefa="tarefa"/>
        <BoxComponent v-if="listaEstaVazia">
          Voce nao esta muito produtivo hoje :(
        </BoxComponent>
      </div>

    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from "@/components/BarraLateral.vue";
import FormularioComponent from "@/components/Formulario.vue";
import TarefaComponent from "@/components/Tarefa.vue";
import BoxComponent from "@/components/Box.vue"
import ITarefa from "@/interfaces/ITarefa";

export default defineComponent({
  name: 'App',
  components: {
    BarraLateral,
    FormularioComponent,
    TarefaComponent,
    BoxComponent
  },
  data() {
    return {
      tarefas: [] as ITarefa[]
    }
  },
  computed: {
    listaEstaVazia(): boolean {
      return this.tarefas.length === 0
    }
  },
  methods: {
    salvarTarefa(tarefa: ITarefa) {
      this.tarefas.push(tarefa);
    }
  }
});
</script>

<style>
.lista{
  padding: 1.25rem;
}
main {
 --bg-primario: #fff;
 --texto-primario: #000;
}
main.modo-escuro {
  --bg-primario: #2b2d42;
  --texto-primario: #ddd;
}
.conteudo {
  background-color: var(--bg-primario);
}
</style>
