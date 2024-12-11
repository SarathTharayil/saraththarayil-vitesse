<script lang="ts" setup>
import siteConfig from '@/site-config'
import { getLinkTarget } from '@/utils/link'
</script>

<template>
  <footer class="!fixed bottom-0 bg-transparent z-50 w-full h-20 px-6 flex flex-col gap-4 border-main border-t !border-op-50 text-dark dark:text-white">
    <div class="flex flex-wrap gap-4">
      <template v-for="(link, index) in siteConfig.footer.navLinks" :key="link.text">
        <a
          :aria-label="`${link.text}`" :target="getLinkTarget(link.href)" class="nav-link flex items-center"
          :href="link.href"
        >
          {{ link.text }}
        </a>
        <span v-if="index < siteConfig.footer.navLinks.length - 1" op-70> / </span>
      </template>
    </div>
    <div class="flex justify-between">
      <a nav-link href="https://creativecommons.org/licenses/by-nc-sa/4.0/" target="_blank">CC BY-NC-SA 4.0</a>
      <span op-70>&nbsp;&nbsp;&copy;&nbsp;&nbsp;{{ new Date().getFullYear() }}&nbsp;&nbsp;{{ siteConfig.author }}.</span>
    </div>
  </footer>
</template>

<!-- <footer class="!fixed bg-transparent z-899 w-screen h-20 px-6 relative w-full mt-18 pt-4 pb-8 flex flex-col gap-4 border-main border-t !border-op-50 text-dark dark:text-white">

  <div flex justify-between>
    <span op-70>&nbsp;&nbsp;&copy;&nbsp;&nbsp;{{ new Date().getFullYear() }}&nbsp;&nbsp;{{ siteConfig.author
    }}</span>
    <a nav-link href="https://creativecommons.org/licenses/by-nc-sa/4.0/" target="_blank">CC BY-NC-SA 4.0</a>
  </div>
</footer> -->
