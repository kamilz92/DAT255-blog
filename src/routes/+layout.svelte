<script>
  import "../app.css";
  import Footer from "../components/Footer.svelte";
  import Header from "../components/Header.svelte";
</script>

<div class="flex flex-col min-h-screen bg-gray-200">
  <Header />
  <main
    class="max-w-[1200px] mx-auto flex-grow flex py-10 flex-col px-2 lg:px-0"
  >
    <slot />
  </main>
  <Footer />
</div>
