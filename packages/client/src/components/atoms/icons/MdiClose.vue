<template>
  <base-svg>
    <path :d="mdiClose" />
  </base-svg>
</template>

<script lang="ts">
  import { mdiClose } from '@mdi/js'
  import { defineComponent } from '@nuxtjs/composition-api'

  export default defineComponent({
    setup() {
      return { mdiClose }
    }
  })
</script>
