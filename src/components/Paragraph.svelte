<script>
  export let text = "";
  export let bigP = false;
</script>

<p class={bigP ? 'py-4' : 'py-2'}>{text}</p>
