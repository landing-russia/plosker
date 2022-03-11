<script>
  // import gsap from "gsap";
  import { onMount } from "svelte";
  import Pattern from "$lib/Pattern.svelte";
  import Pattern2 from "$lib/Pattern-2.svelte";
  import Logo from "$lib/Logo.svelte";

  // onMount(() => {
  //   const tl = gsap.timeline();

  //   tl.from(".box", {
  //     y: 20,
  //     autoAlpha: 0,
  //     duration: 0.8,
  //     ease: "elastic.out(1, 0.3)",
  //     delay: 0.25,
  //   });
  // });
</script>

<div class="lg:flex h-screen">
  <div class="lg:basis-0 lg:flex-grow lg:flex-shrink overflow-hidden">
    <div class="container-fluid lg:h-screen flex items-center relative">
      <div class="absolute inset-x-0 top-5 flex items-start justify-between">
        <Logo />
        <div class="hidden sm:block mr-4 xl:mr-8 text-right">
          <div class="text-base 2xl:text-lg font-bold text-slate-300">
            +7&nbsp;978&nbsp;138-11-59
          </div>
          <div class="text-sm 2xl:text-base leading-5 text-slate-400">
            г.&nbsp;Евпатория, пр-т&nbsp;Победы,&nbsp;36, оф.&nbsp;2
          </div>
        </div>
        <button
        type="button"
        class="sm:hidden rounded-full text-slate-300 hover:text-slate-100 mr-4 p-1 focus:outline-none focus:ring-1 focus:ring-offset-1 focus:ring-slate-800 z-10"
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
      class="portrait:h-[75vh] w-auto lg:h-screen object-cover"
      src="women.jpg"
      alt="women"
    />
    <div class="absolute inset-0 bg-slate-900/90 mix-blend-color" />
    <div
      class="absolute inset-x-0 bottom-5 backdrop-blur-md bg-slate-900/50 text-center font-bitter italic mx-10 sm:mx-20 md:mx-32 lg:mx-28 xl:mx-32 2xl:mx-48 p-4 border border-slate-500 rounded-lg shadow-lg"
    >
      <p class="text-slate-50 text-2xl font-bold">Татьяна Жидкова</p>
      <p class="text-slate-50">руководитель налоговой практики</p>
    </div>
  </div>
</div>

<div class="h-96" />
<div class="h-96" />
<div class="h-96" />
<div class="h-96" />
<div class="h-96" />
