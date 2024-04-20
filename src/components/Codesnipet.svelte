<script>
  export let code = []; 
</script>

<pre class="p-2 mt-2 bg-white rounded-md whitespace-normal flex flex-col min-w-max">
    <!-- svelte for each -->
    {#each code as line, i}
      <code class="text-gray-900"><span class="mx-2">{i + 1}</span> {line}</code>
    {/each}
</pre>