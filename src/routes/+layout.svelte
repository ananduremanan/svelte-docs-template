<script lang="ts">
  import "../app.css";
  import Navbar from "$lib/components/Navbar.svelte";
  import { onMount } from "svelte";

  let menuItemsArray: any[] = [];
  let isActiveLink = false;

  async function fetchData() {
    const modules = import.meta.glob("./components/**/*.svx");
    const menuItems = Object.keys(modules).map(
      (item) => item.replace("./components/", "").split("/")[0]
    );
    console.log("MODULES & Menu", modules, menuItems);
    menuItemsArray = menuItems;
  }

  onMount(fetchData);
</script>

<Navbar />
<div class="px-4 flex h-screen">
  <div class="w-80 hidden md:block sticky top-0 h-screen overflow-y-auto">
    {#if menuItemsArray}
      <ul class="dark:text-white">
        <li class="px-12 mt-4"><a href="/">Introduction</a></li>
        {#each menuItemsArray as menu}
          <li class="px-12 mt-4"><a href={`/components/${menu}`}>{menu}</a></li>
        {/each}
      </ul>
    {/if}
  </div>
  <article class="prose lg:prose-xl dark:prose-invert px-4">
    <slot />
  </article>
</div>
<footer>
  <div class="p-4">All Rights Reserved GBS © 2024</div>
</footer>
