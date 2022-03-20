<script>
  import { onDestroy } from "svelte";
  import { createEventDispatcher } from "svelte";
  import Pattern from "$lib/Pattern.svelte";
  import Pattern2 from "$lib/Pattern-2.svelte";
  import Logo from "$lib/Logo.svelte";
  import SectionOne from "$lib/SectionOne.svelte";
  import SectionTwo from "$lib/SectionTwo.svelte";
  import Price from "$lib/Price.svelte";
  import Testimonials from "$lib/Testimonials.svelte";
  import { isOpenStore } from "../store/store";

  export let isOpen;
  let resume = false;

  const unsubscribe = isOpenStore.subscribe((value) => {
    isOpen = value;
  });
  onDestroy(unsubscribe);

  const dispatch = createEventDispatcher();

  function changeStore() {
    isOpenStore.update(() => (isOpen = !isOpen));
  }
</script>

<div class="bg-slate-900 grid grid-cols-1 lg:grid-cols-2 lg:min-h-screen">
  <div class="container-fluid overflow-hidden">
    <div class="h-16 mt-4 lg:mt-6 flex items-start justify-between">
      <Logo />
      <div class="hidden sm:block text-right">
        <div
          class="flex items-center justify-end text-base 2xl:text-xl font-bold text-slate-300"
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="h-4 w-4 mr-1 text-slate-400"
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
            >&nbsp;138-11-59</span
          >
        </div>
        <div class="text-sm 2xl:text-lg leading-4 2xl:leading-5 text-slate-400">
          г.&nbsp;Евпатория, пр-т&nbsp;Победы,&nbsp;36, оф.&nbsp;2
        </div>
      </div>
      <button
        on:click={changeStore}
        type="button"
        class="sm:hidden rounded-full text-slate-300 hover:text-slate-100 focus:outline-none focus:ring-1 focus:ring-offset-1 focus:ring-slate-800 z-10"
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
    </div>
    <div
      class="relative lg:min-h-full pt-10 pb-14 lg:pt-0 lg:pb-32 flex items-center"
    >
      <Pattern />
      <Pattern2 />
      <div class="relative z-10">
        <h1
          class="text-3xl xs:text-4xl lg:text-5xl xl:text-6xl 2xl:text-7xl 3xl:text-8xl font-bold text-slate-50"
        >
          Специализация&nbsp;— <span class="text-slate-400"
            >налоговое&nbsp;право</span
          >
        </h1>
        <p
          class="text-slate-400 text-lg lg:text-xl xl:text-2xl 2xl:text-3xl font-normal mt-6 max-w-4xl"
        >
          Налоговая практика для юридических лиц и&nbsp;индивидуальных
          предпринимателей
        </p>
      </div>
    </div>
  </div>
  <div
    class="relative grid min-h-144 lg:min-h-full pb-10 bg-[url('/women-mono.jpg')] bg-cover bg-center overflow-hidden"
  >
    {#if resume}
      <div
        on:click={() => (resume = false)}
        class="absolute inset-0 backdrop-blur bg-slate-900/75 z-10"
      />
      <button
        class="absolute right-6 top-6 backdrop-blur bg-slate-500/30 hover:bg-slate-600/40 border border-slate-500 px-3 py-1 text-slate-100 rounded-lg shadow-lg focus:outline-none focus:ring-1 focus:ring-offset-1 focus:ring-slate-800 transition-all duration-200 z-20"
        type="button"
        on:click={() => (resume = false)}>Закрыть</button
      >
      <div
        class="relative container-fluid max-w-xl 2xl:max-w-3xl self-center mb-8 mt-16 text-slate-100 space-y-3 z-20"
      >
        <img
          class="h-16 w-16 lg:h-20 lg:w-20 2xl:h-24 2xl:w-24 border-2 border-slate-300 mr-3 inline-block rounded-full shadow-lg"
          src="women-avatar-mono.jpg"
          alt="women-avatar"
        />
        <span class="font-bitter font-bold text-xl 2xl:text-3xl italic"
          >Татьяна Жидкова</span
        >
        <div class="h-2" />
        <p class="text-base 2xl:text-2xl">
          <span class="font-bold">2008</span> <br />
          Российский экономический университет им.&nbsp;Г.В.&nbsp;Плеханова <br /> Специальность:
          Бухгалтерский учёт и&nbsp;налогообложение
        </p>

        <p class="text-base 2xl:text-2xl">
          <span class="font-bold">2016</span> <br />
          Московский государственный юридический университет им.&nbsp;О.Е.&nbsp;Кутафина
          (МГЮА) г.&nbsp;Москва<br />
          Специальность: Юриспруденция
        </p>

        <p class="text-base 2xl:text-2xl">
          Специализируюсь в&nbsp;области налогового права, бухгалтерского учёта
          и&nbsp;более 11&nbsp;лет оказываю правовую поддержку клиентам при
          возникновении споров с&nbsp;налоговыми органами. Принимаю участие
          в&nbsp;крупных консультационных проектах для российских организаций
          в&nbsp;различных отраслях бизнеса.
        </p>
      </div>
    {:else}
      <div class="h-144 lg:h-full flex items-end justify-center">
        <button
          on:click={() => (resume = !resume)}
          type="button"
          class="backdrop-blur bg-slate-900/50 hover:bg-slate-900/60 text-center font-bitter italic px-6 py-4 border border-slate-500 rounded-lg shadow-lg focus:outline-none focus:ring-1 focus:ring-offset-1 focus:ring-slate-800 transition-all duration-200"
        >
          <p class="text-slate-50 text-2xl font-bold">Татьяна Жидкова</p>
          <p class="text-slate-50">руководитель налоговой практики</p>
        </button>
      </div>
    {/if}
  </div>
</div>

<SectionOne />

<SectionTwo />

<Price />

<Testimonials />
