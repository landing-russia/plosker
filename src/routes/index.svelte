<script>
  import { onDestroy } from "svelte";
  import { createEventDispatcher } from "svelte";
  import Pattern from "$lib/Pattern.svelte";
  import Pattern2 from "$lib/Pattern-2.svelte";
  import Logo from "$lib/Logo.svelte";
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

<div class="lg:flex h-screen">
  <div class="lg:basis-0 lg:flex-grow lg:flex-shrink overflow-hidden">
    <div class="container-fluid lg:h-screen flex items-center relative">
      <div class="absolute inset-x-0 top-5 flex items-start justify-between">
        <Logo />
        <div class="hidden sm:block mr-4 xl:mr-8 text-right">
          <div
            class="flex items-center justify-end text-base 2xl:text-lg font-bold text-slate-300"
          >
            <svg
              xmlns="http://www.w3.org/2000/svg"
              class="h-4 w-4 mr-2"
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
            </svg><span>+7&nbsp;978&nbsp;138-11-59</span>
          </div>
          <div class="text-sm 2xl:text-base leading-4 text-slate-400">
            г.&nbsp;Евпатория, пр-т&nbsp;Победы,&nbsp;36, оф.&nbsp;2
          </div>
        </div>
        <button
          type="button"
          class="sm:hidden rounded-full text-slate-300 hover:text-slate-100 mr-4 p-1 focus:outline-none focus:ring-1 focus:ring-offset-1 focus:ring-slate-800 z-10"
          on:click={changeStore}
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
      <div class="relative pt-32 pb-16">
        <Pattern />
        <Pattern2 />
        <h1
          class="relative z-10 text-3xl xs:text-4xl lg:text-5xl xl:text-6xl 2xl:text-7xl font-bold text-slate-50"
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
  <div class="lg:basis-0 lg:flex-grow lg:flex-shrink relative">
    <img
      class="{resume
        ? 'h-screen'
        : 'min-h-[85vh]'} w-auto lg:h-screen object-cover"
      src="women.jpg"
      alt="women"
    />
    <div
      class="absolute inset-0  {resume
        ? 'bg-slate-900/80 backdrop-blur-lg'
        : 'bg-slate-900/90 mix-blend-color'}
      "
    />
    {#if resume}
      <button
        class="absolute right-4 top-6 bg-slate-500 px-3 py-1 text-slate-100 rounded-lg z-20"
        type="button"
        on:click={() => (resume = false)}>Закрыть</button
      >
      <div
        class="absolute container-fluid mt-6 inset-x-0 top-8 text-slate-100 space-y-3"
      >
        <div class="">
          <img
            class="h-24 w-24 mr-3 inline-block rounded-full"
            src="women-avatar.jpg"
            alt="women-avatar"
          />
          <span class="font-bitter font-bold text-xl italic">Татьяна Жидкова</span>

        </div>
        <p>
          <span class="font-bold">2008</span> <br />
          Российский экономический университет им. Плеханова Специальность: Бухгалтерский
          учет и налогообложение
        </p>

        <p>
          <span class="font-bold">2016</span> <br />
          Московский государственный юридический университет имени О.Е. Кутафина
          (МГЮА) г. Москва<br />
          Специальность: Юриспруденция
        </p>

        <p>
          Специализируюсь в области налогового права, бухгалтерского учета и
          более 11 лет оказываю правовую поддержку клиентам при возникновении
          споров с налоговыми органами. Принимаю участие в крупных
          консультационных проектах для российских организаций в различных
          отраслях бизнеса.
        </p>
      </div>
    {:else}
      <button
        on:click={() => (resume = !resume)}
        type="button"
        class="absolute inset-x-0 bottom-5 backdrop-blur-md bg-slate-900/50 hover:bg-slate-900/60 text-center font-bitter italic mx-10 sm:mx-20 md:mx-32 lg:mx-28 xl:mx-32 2xl:mx-48 p-4 border border-slate-500 rounded-lg shadow-lg focus:outline-none focus:ring-1 focus:ring-offset-1 focus:ring-slate-800 transition-all duration-200"
      >
        <p class="text-slate-50 text-2xl font-bold">Татьяна Жидкова</p>
        <p class="text-slate-50">руководитель налоговой практики</p>
      </button>
    {/if}
  </div>
</div>

<div class="h-96" />
<div class="h-96" />
<div class="h-96" />
<div class="h-96" />
<div class="h-96" />
