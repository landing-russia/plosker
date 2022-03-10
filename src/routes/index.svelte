<script>
  import gsap from "gsap";
  import { onMount } from "svelte";
  import Pattern from "$lib/Pattern.svelte";
  import Pattern2 from "$lib/Pattern-2.svelte";
  import Logo from "$lib/Logo.svelte";

  onMount(() => {
    const tl = gsap.timeline();

    tl.from(".box", {
      y: 20,
      autoAlpha: 0,
      duration: 0.8,
      ease: "elastic.out(1, 0.3)",
      delay: 0.25,
    });
  });
</script>

<div class="lg:flex h-screen">
  <div class="lg:basis-0 lg:flex-grow lg:flex-shrink overflow-hidden">
    <div class="container-fluid lg:h-screen flex items-center relative">
      <div class="absolute top-0 left-0 py-6">
        <Logo />
      </div>
      <div class="absolute hidden sm:block top-0 right-0 py-6 text-right mr-8">
        <div class="text-base 2xl:text-lg font-bold text-slate-300">
          +7&nbsp;978&nbsp;138-11-59
        </div>
        <div class="text-sm 2xl:text-base leading-5 text-slate-400">
          г.&nbsp;Евпатория, пр-т&nbsp;Победы,&nbsp;36, оф.&nbsp;2
        </div>
      </div>
      <div class="relative pt-32 pb-16">
        <Pattern />
        <Pattern2 />
        <h1
          class="box invisible text-4xl lg:text-5xl xl:text-6xl 2xl:text-7xl font-bold text-slate-50"
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
    <img class="portrait:h-[75vh] w-auto lg:h-screen object-cover" src="women.jpg" alt="women" />
    <div
      class="absolute inset-0 backdrop-grayscale bg-slate-800/50 mix-blend-overlay"
    />
    <div class="absolute inset-x-0 bottom-5 backdrop-blur-lg bg-slate-800/50 text-center font-bitter italic mx-10 sm:mx-20 md:mx-32 lg:mx-28 xl:mx-32 2xl:mx-48 p-4 border border-gray-500 rounded-lg">
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
