<script lang="ts">
  import { DarkMode } from "flowbite-svelte";
  import { EllipsisVertical } from "lucide-svelte";
</script>

<nav
  class="p-4 flex justify-between items-center glass sticky top-0 dark:text-white z-50 md:px-16"
>
  <a href="/">GBS Svelte Building Block</a>
  <div class="flex justify-center items-center gap-2">
    <DarkMode />
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
