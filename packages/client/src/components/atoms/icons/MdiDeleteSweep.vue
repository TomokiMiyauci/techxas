<template>
  <base-svg v-bind="$attrs">
    <path :d="mdiDeleteSweep" />
  </base-svg>
</template>

<script lang="ts">
  import { mdiDeleteSweep } from '@mdi/js'
  import { defineComponent } from '@nuxtjs/composition-api'

  export default defineComponent({
    setup() {
      return { mdiDeleteSweep }
    }
  })
</script>
