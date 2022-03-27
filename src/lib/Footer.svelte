<script>
  import Logo2 from "./Logo2.svelte";

  $: currentYear = new Date().getFullYear();
</script>

<div
  class="bg-slate-900 h-32 w-full flex items-center justify-center text-gray-400 text-lg font-semibold shadow"
>
  <div class="space-y-2 pt-2">
    <Logo2 />
    <p class="text-base text-center text-slate-400 font-bitter font-normal">
      &copy;&nbsp;{currentYear}
    </p>
  </div>
</div>
