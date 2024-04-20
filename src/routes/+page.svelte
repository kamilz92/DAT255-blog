<script>
  import Dataset from "../components/Dataset.svelte";
  import hcd1 from "$lib/images/hcd1.png";
  import hcd2 from "$lib/images/hcd2.png";
  import pnas1 from "$lib/images/pnas1.png";
  import pnas2 from "$lib/images/pnas2.png";
</script>

<svelte:head>
  <title>Dyp læring i patologi</title>
</svelte:head>

<h1 class="text-2xl my-4">Dyp læring i patologi</h1>
<p>
  I dette prosjektet har vi valgt å utforske maskinlæring i patologi. Patologi
  betyr sykdomsmønstre, men det de hovedsakelig jobber med er å se etter diverse
  sykdommer og feil i bilder av vevsprøver. Disse bildene kalles for WSI (Whole
  Slide Images), og er mikroskopiske bilder av vevet som er farget og kuttet i
  tynne skiver. Det er dermed mulig for de å se etter kreft, fibrose og mer i
  forskjellige vei.
</p>
<div class="mt-4">
  <Dataset
    datasetNavn="Histopathologic Cancer Detection"
    datasetLenken={[
      "https://www.kaggle.com/competitions/histopathologic-cancer-detection/data",
    ]}
    images={[hcd1, hcd2, hcd1, hcd2]}
  />
  <Dataset
    datasetNavn="PNAS bilder"
    datasetLenken={[
      "https://www.dropbox.com/s/jka111c16q8cn6x/PNAS-images.zip",
      "https://www.dropbox.com/s/7v9v9v7v3v7v7v7/PNAS_images.zip?dl=0",
    ]}
    images={[pnas1, pnas2, pnas1, pnas2]}
  />
</div>
