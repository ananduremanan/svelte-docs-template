<script lang="ts">
  import { DarkMode } from "flowbite-svelte";
  import { EllipsisVertical } from "lucide-svelte";
</script>

<nav
  class="p-4 flex justify-between items-center glass sticky top-0 dark:text-white z-50 md:px-16 border-b"
>
  <a href="/">GBS Svelte Building Block</a>
  <div class="flex justify-center items-center gap-2">
    <DarkMode />
    <input
      placeholder="Search Documentation"
      class="bg-gray-100 px-2 py-1 rounded-lg outline-none hidden md:block"
    />
    <a
      href="https://github.com/ananduremanan/svelte-docs-template"
      target="_blank"><img src="/icons/github.svg" alt="" class="w-6 h-6" /></a
    >
    <EllipsisVertical size="18" class="md:hidden" />
  </div>
</nav>

<style>
  .glass {
    background: rgba(255, 255, 255, 0.25);
    backdrop-filter: blur(4px);
    -webkit-backdrop-filter: blur(4px);
  }
</style>
