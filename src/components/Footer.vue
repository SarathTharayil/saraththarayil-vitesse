<script lang="ts" setup>
import siteConfig from '@/site-config'
</script>

<template>
  <footer class="w-full mt-18 pt-6 pb-8 flex flex-col gap-4 border-main border-t text-dark dark:text-white">
    <div class="flex justify-between">
      <span op-70>&nbsp;&nbsp;&copy;&nbsp;&nbsp;{{ new Date().getFullYear() }}&nbsp;&nbsp;{{ siteConfig.author
      }}</span>
      <a nav-link href="https://creativecommons.org/licenses/by-nc-sa/4.0/" target="_blank">CC BY-NC-SA 4.0</a>
    </div>
  </footer>
</template>
