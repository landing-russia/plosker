<script context="module">
  export const load = async ({ page }) => ({
    props: {
      key: page.path,
    },
  });
</script>

<script>
  import "../app.css";
  import { onDestroy } from "svelte";
  import Nav from "$lib/Nav.svelte";
  import Footer from "$lib/Footer.svelte";
  import SaleModal from "$lib/SaleModal.svelte";
  import PageTransition from "$lib/PageTransition.svelte";
  import { isOpenStore } from "../store/store";
  export let key;
  let isOpen;
  // let modalOpen = true;

  const unsubscribe = isOpenStore.subscribe((value) => {
    isOpen = value;
  });
  onDestroy(unsubscribe);

  function handleIsOpen(event) {
    console.log("HI");
    isOpen = true;
  }
</script>

<div class="bg-slate-900 flex flex-col min-h-screen">
  <!-- <div
    class="bg-red-500 text-center text-white text-lg font-bold font-bitter p-1"
  >
    Акция!
  </div> -->
  <!-- <SaleModal modalOpen /> -->
  <Nav {isOpen} />
  <main class="flex-grow w-full">
    <PageTransition refresh={key}>
      <slot />
    </PageTransition>
  </main>
  <Footer class="flex-shrink-0" />
</div>
