<script>
  import Codesnipet from "./Codesnipet.svelte";

  export let datasetNavn = "Ingen navn";
  export let datasetBeskrivelse = "Ingen beskrivelse";
  export let datasetLenken = "";
  export let images = [];
</script>

<div class="mt-4">
  <h2 class="text-xl leading-10">{datasetNavn}</h2>
  <p class="py-2">{datasetBeskrivelse}</p>
  <div class="bg-white p-4 my-4 flex justify-evenly sm:justify-normal gap-5 flex-wrap sm:w-max">
    {#each images as img}
      <img class="max-w-[100px] hover:scale-[200%] transition-transform" src={img} alt="dataset" />
    {/each}
  </div>
  <div>
    <span>Lenken til datasete: </span>
    {#each datasetLenken as l}
      <a
        class="text-red-400 cursor-pointer hover:underline mx-2"
        target="_blank"
        rel="noopener noreferrer"
        href={l}>Click!</a
      >
    {/each}
  </div>
</div>
