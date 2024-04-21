<script>
  import Dataset from "../components/Dataset.svelte";

  import hcd1 from "$lib/images/hcd1.png";
  import hcd2 from "$lib/images/hcd2.png";
  import hcd3 from "$lib/images/hcd3.png";
  import hcd4 from "$lib/images/hcd4.png";
  
  import pnas1 from "$lib/images/pnas1.png";
  import pnas2 from "$lib/images/pnas2.png";
  import pnas3 from "$lib/images/pnas3.png";
  import pnas4 from "$lib/images/pnas4.png";

  import Paragraph from "../components/Paragraph.svelte";
</script>

<svelte:head>
  <title>Dyp læring i patologi</title>
</svelte:head>

<h1 class="text-2xl my-4">Dyp læring i patologi</h1>
<Paragraph
  text="Vi valgte dette prosjektet fordi det passer perfekt med bacheloroppgaven vi jobber med for Patologi i Vestlandet (PIV)."
/>
<div class="mt-4">
  <Dataset
    datasetNavn="Histopathologic Cancer Detection"
    datasetBeskrivelse="
    Dataene er en litt modifisert versjon av PatchCamelyon (PCam) benchmark datasettet. Det originale PCam datasettet inneholder duplikate bilder på grunn av sin probabilistiske prøvetaking, men versjonen presentert på Kaggle inneholder ikke duplikater."
    datasetLenken={[
      "https://www.kaggle.com/competitions/histopathologic-cancer-detection/data",
    ]}
    images={[hcd1, hcd2, hcd3, hcd4]}
  />
  <Dataset
    datasetNavn="PNAS bilder"
    datasetLenken={[
      "https://www.dropbox.com/s/jka111c16q8cn6x/PNAS-images.zip",
    ]}
    images={[pnas1, pnas2, pnas3, pnas4]}
  />
</div>
