<script>
  import gsap from "gsap";
  import { onMount } from "svelte";
  import Pattern from "$lib/Pattern.svelte"
  import Pattern2 from "$lib/Pattern-2.svelte"
  import Logo from "$lib/Logo.svelte"

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
      <div class="absolute top-0 right-0 py-6 text-right text-gray-400 mr-8">
        <div class="text-lg font-semibold">+7&nbsp;978&nbsp;138-11-59</div>
        <div class="leading-4">г.&nbsp;Евпатория, пр-т&nbsp;Победы,&nbsp;36, оф.&nbsp;2</div>
      </div>
      <div class="relative pt-24 pb-20">
        <Pattern />
        <Pattern2 />
        <h1 class="box invisible text-5xl xl:text-6xl 2xl:text-7xl font-bold text-gray-100">
          Специализация&nbsp;— <span class="text-gray-400">налоговое право</span
          >
        </h1>
        <p class="text-gray-400 text-xl font-normal mt-6">
          Налоговая практика для юридических лиц и&nbsp;индивидуальных
          предпринимателей
        </p>
      </div>
    </div>
  </div>
  <div class="bg-gray-700 lg:basis-0 lg:flex-grow lg:flex-shrink relative">
    <img class="object-cover h-screen" src="women.jpg" alt="women">
    <div class="absolute inset-0 backdrop-grayscale bg-gray-800/20 hover:backdrop-grayscale-0 hover:bg-gray-800/0 transition-all duration-200"></div>
  </div>
</div>

<div class="h-96" />
<div class="h-96" />
<div class="h-96" />
<div class="h-96" />
<div class="h-96" />
