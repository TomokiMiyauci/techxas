<template>
  <base-tooltip>
    <template #activator>
      <base-switcher :value="isLight" @change="onChange">
        <template #on>
          <mdi-weather-night />
        </template>
        <template #off>
          <mdi-weather-sunny />
        </template>
      </base-switcher>
    </template>

    <span>{{ $t('tooltip') }}</span>
  </base-tooltip>
</template>

<script lang="ts">
  import BaseSwitcher from '@/components/atoms/BaseSwitcher.vue'
  import BaseTooltip from '@/components/atoms/BaseTooltip.vue'
  import ButtonCircle from '@/components/atoms/buttons/ButtonCircle.vue'
  import MdiWeatherNight from '@/components/atoms/icons/MdiWeatherNight.vue'
  import MdiWeatherSunny from '@/components/atoms/icons/MdiWeatherSunny.vue'
  import { defineComponent, computed } from '@nuxtjs/composition-api'
  import Vue from 'vue'
  declare module 'vue/types/vue' {
    interface ColorMode extends Vue {
      value: Mode
      preference: Mode
      unknown: string
    }
    interface Vue {
      $colorMode: ColorMode
    }
  }

  type Mode = 'light' | 'dark'
  export default defineComponent({
    components: {
      ButtonCircle,
      BaseSwitcher,
      BaseTooltip,
      MdiWeatherSunny,
      MdiWeatherNight
    },

    setup(_, { root }) {
      const onChange = (): void => {
        root.$colorMode.value === 'light'
          ? (root.$colorMode.preference = 'dark')
          : (root.$colorMode.preference = 'light')
      }
      const isLight = computed(() => root.$colorMode.value === 'dark')

      return { isLight, onChange }
    }
  })
</script>

<i18n lang="yml">
en:
  tooltip: Color Mode
ja:
  tooltip: カラーモード
</i18n>
