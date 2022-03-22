<script>
  import { onMount, onDestroy } from "svelte";
  import { fade } from "svelte/transition";
  import { isOpenStore } from "../store/store";
  import Logo2 from "$lib/Logo2.svelte";

  export let isOpen;

  const unsubscribe = isOpenStore.subscribe((value) => {
    isOpen = value;
  });
  onDestroy(unsubscribe);

  let scrollNow = 0;
  let isNav = false;
  let isDark = "";

  onMount(() => {
    window.onscroll = () => {
      if (window.scrollY > scrollNow || window.scrollY < 350) {
        isNav = false;
      } else {
        isNav = true;
      }
      scrollNow = window.scrollY;
    };
  });

  if (typeof localStorage !== "undefined") {
    if (
      localStorage.theme === "dark"
      // ||
      // (!("theme" in localStorage) &&
      //   window.matchMedia("(prefers-color-scheme: dark)").matches)
    ) {
      isDark = "dark";
      document.documentElement.classList.add("dark");
    } else {
      isDark = "light";
      document.documentElement.classList.remove("dark");
    }
  }

  function isNavEsc(e) {
    if (e.code === "Escape") {
      isOpen = false;
      isOpenStore.update(() => (isOpen = false));
    }
  }

  function toggleDarkMode() {
    if (isDark === "dark") {
      document.documentElement.classList.remove("dark");
      localStorage.theme = "light";
      isDark = "light";
    } else if (isDark === "light") {
      document.documentElement.classList.add("dark");
      localStorage.theme = "dark";
      isDark = "dark";
    }
  }
</script>

<svelte:window on:keydown={isNavEsc} />

<div
  class="fixed w-full backdrop-blur bg-slate-900/90 border-b border-slate-800 shadow transform ease-in-out transition-all duration-200 {isNav
    ? 'translate-y-0'
    : '-translate-y-full'} z-40"
>
  <nav
    class="relative container-fluid flex justify-between items-start py-4 z-10"
  >
    <Logo2 />
    <a href="#contacts" class="hidden sm:block text-right">
      <div
        class="flex items-center justify-end text-base 2xl:text-lg font-bold text-slate-300"
      >
        <svg
          xmlns="http://www.w3.org/2000/svg"
          class="h-4 w-4 mr-2 text-slate-400"
          fill="none"
          viewBox="0 0 24 24"
          stroke="currentColor"
          stroke-width="2"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z"
          />
        </svg><span
          ><span class="font-semibold text-slate-400">+7&nbsp;978</span
          >&nbsp;946-12-29</span
        >
      </div>
      <div class="text-sm 2xl:text-base leading-4 text-slate-400">
        г.&nbsp;Евпатория, пр-т&nbsp;Победы,&nbsp;37, оф.&nbsp;2
      </div>
    </a>
    <button
      type="button"
      class="sm:hidden rounded-full text-slate-300 hover:text-slate-100 focus:outline-none focus:ring-1 focus:ring-offset-1 focus:ring-slate-800"
      on:click={isOpenStore.update(() => (isOpen = !isOpen))}
      ><svg
        xmlns="http://www.w3.org/2000/svg"
        class="h-8 w-8"
        fill="none"
        viewBox="0 0 24 24"
        stroke="currentColor"
      >
        <path
          stroke-linecap="round"
          stroke-linejoin="round"
          stroke-width="2"
          d="M4 6h16M4 12h16M4 18h16"
        />
      </svg></button
    >
  </nav>
</div>

{#if isOpen}
  <div
    transition:fade={{ duration: 200 }}
    class="fixed inset-0 bg-slate-700/75 z-30"
    aria-hidden="true"
    on:click={isOpenStore.update(() => (isOpen = !isOpen))}
  />
{/if}

<aside
  class="transform top-0 left-0 w-67 backdrop-blur bg-slate-900/80 fixed h-full p-3 shadow-lg overflow-auto ease-in-out transition-all duration-200 z-50 {isOpen
    ? 'translate-x-0'
    : '-translate-x-full'}"
>
  <div class="flex flex-col h-full">
    <div class="mt-1 flex items-start justify-between">
      <Logo2 />
      <button
        on:click={isOpenStore.update(() => (isOpen = false))}
        type="button"
        class="p-0.5 text-slate-400 rounded-full focus:outline-none focus:ring-1 focus:ring-offset-1 focus:ring-slate-800"
      >
        <svg
          xmlns="http://www.w3.org/2000/svg"
          class="h-5 w-5"
          viewBox="0 0 20 20"
          fill="currentColor"
        >
          <path
            fill-rule="evenodd"
            d="M4.293 4.293a1 1 0 011.414 0L10 8.586l4.293-4.293a1 1 0 111.414 1.414L11.414 10l4.293 4.293a1 1 0 01-1.414 1.414L10 11.414l-4.293 4.293a1 1 0 01-1.414-1.414L8.586 10 4.293 5.707a1 1 0 010-1.414z"
            clip-rule="evenodd"
          />
        </svg>
      </button>
    </div>
    <div class="mt-10 flex-grow text-2xl font-semibold font-bitter text-slate-300 space-y-5">
      <a
        href="#practice"
        on:click={isOpenStore.update(() => (isOpen = false))}
        class="flex items-center"
      ><span
          >Практика</span
        >
      </a>
      <a
        href="#price"
        on:click={isOpenStore.update(() => (isOpen = false))}
        class="flex items-center"
      ><span
          >Тарифы</span
        >
      </a>
      <a
        href="#testimonials"
        on:click={isOpenStore.update(() => (isOpen = false))}
        class="flex items-center"
      ><span
          >Отзывы</span
        >
      </a>
      <a
        href="#contact-info"
        on:click={isOpenStore.update(() => (isOpen = false))}
        class="flex items-center"
      ><span
          >Контакты</span
        >
      </a>
    </div>

    <div
      class="my-4 flex-shrink-0 text-2xl leading-tigth font-bold text-slate-400"
    >
      <div class="flex items-center text-slate-200">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          class="h-5 w-5 mr-2 text-slate-400"
          fill="none"
          viewBox="0 0 24 24"
          stroke="currentColor"
          stroke-width="2"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z"
          />
        </svg><span
          ><span class="font-semibold text-slate-400">+7&nbsp;978</span
          >&nbsp;946-12-29</span
        >
      </div>
      <div class="mt-3 text-sm font-normal">г.&nbsp;Евпатория, пр-т&nbsp;Победы,&nbsp;37, оф.&nbsp;2</div>
    </div>
  </div>
</aside>
