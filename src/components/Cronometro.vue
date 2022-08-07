<template>
  <section>
    <strong>
      {{ tmpDecorrido }}
    </strong>
  </section>
</template>

<script lang="ts">
import { defineComponent} from "vue";

export default defineComponent({
  name: 'CronometroComponent',
  props: {
    tmpEmSegundos: {
      type: Number,
      default: 0
    }
  },
  computed: {
    tmpDecorrido (): string {
      return new Date(this.tmpEmSegundos * 1000).toISOString().substr(11, 8)
    }
  },
})
</script>
