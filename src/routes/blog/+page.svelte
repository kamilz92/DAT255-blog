<script>
  import Articel from "../../components/Articel.svelte";
  import Codesnipet from "../../components/Codesnipet.svelte";
  import Paragraph from "../../components/Paragraph.svelte";
</script>

<svelte:head>
  <title>Dyp læring i patologi - Blog</title>
</svelte:head>

<h1 class="text-2xl my-4">Blog</h1>

<Articel title="Dyp læring i patologi">
  <Paragraph
    bigP={true}
    text="I dette prosjektet har vi valgt å utforske maskinlæring i patologi. Patologi betyr sykdomslære, men det de hovedsakelig jobber med er å se etter diverse sykdommer og feil i bilder av vevsprøver. Disse bildene kalles for WSI (Whole Slide Images), og er mikroskopiske bilder av vevet som er farget og kuttet i tynne skiver. Det er dermed mulig for de å se etter kreft, fibrose og mer i forskjellig vei."
  />
  <Paragraph
    bigP={true}
    text="Problemet i dag er at antallet patologer synker og arbeidet de gjør blir ganske repetitivt, det å ha et verktøy som maskinlæring til å bruke hadde vært veldig nyttig og gjort arbeidet mer effektivt."
  />

  <Paragraph
    bigP={true}
    text="Målet med denne oppgaven er dermed å utforske litt for vår egen del hva maskinlæring kan klare bare med et bilde som input."
  />
  <Paragraph
    bigP={true}
    text="Vi har dermed tenkt å trene litt forskjellige modeller med litt forskjellige datasett, og gi disse modellene litt forskjellige oppgaver med forskjellige vanskelighetsgrader."
  />
  <Paragraph
    bigP={true}
    text="Til den første testen valgte vi å gå ut fra en konkurranse i Kaggle hvor målet var å se etter kreft ved hjelp av disse bildene."
  />
  <Paragraph
    bigP={true}
    text="Den andre testen er et nytt datasett, hvor en del av informasjonen vi hadde var hvor mange dager pasienten levde etter testen var tatt. Dette var nok den vanskeligste oppgaven vi gav til modellene, og vi hadde ikke så mye håp om at dette kom til å fungere."
  />
  <Paragraph
    bigP={true}
    text="Den tredje og siste testen brukte samme datasettet som test nummer 2, men denne gangen ville vi trene modellen på hvilken molekylær subtype vevet hadde. Denne informasjonen kan brukes til prognose og behandling av brystkreft. Dette er ikke noe som er synlig på bildene og vi regner med dette egentlig var ment som tilleggs informasjon i datasettet til å trene modellen til noe annet, men det var likevel interessant for oss å se om modellen klarte å finne en kobling. Om den hadde klart det ville vi sett på dette som nyttig."
  />
  <Paragraph
    bigP={true}
    text="Vi var veldig begrenset til hva vi kunne gjøre i forhold til hvilke datasett vi kunne finne. Vi brukte noen av de som var vedlagt i oppgaven, men ellers fant vi lite på nett som virket relevant for hva vi ville gjøre i oppgaven. Men likevel har vi fått eksperimentert litt og kommet fram til at for noen oppgaver så kan maskinlæring være veldig nyttig, men enkelte oppgaver er ikke egnet for dette."
  />
</Articel>

<Articel title="Integreringsforsøk: Svelte og Gradio">
  <Paragraph
    bigP={true}
    text="Vi prøvde å integrere vår maskinlæringsmodell i en Svelte webapplikasjon, en
  prosess som viste seg å være mer utfordrende enn forventet. Til tross for at
  prosjektet ikke utviklet seg som vi hadde håpet, var prosessen svært
  lærerik."
  />
  <Paragraph text="Javascript kode:" />
  <Codesnipet
    code={[
      "import { client } from '@gradio/client';",
      "",
      "const response_0 = await fetch('https://raw.githubusercontent.com/gradio-app/gradio/main/test/test_files/bus.png');",
      "const exampleImage = await response_0.blob();",
      "",
      "const app = await client('http://127.0.0.1:7860/');",
      "const result = await app.predict('/predict', [",
      "  exampleImage,  // blob in 'img' Image component",
      "]);",
      "",
      "console.log(result.data);",
    ]}
  />
  <Paragraph text="Python kode:"></Paragraph>
  <Codesnipet
    code={[
      "from fastai.vision.all import load_learner",
      "import pathlib",
      "import gradio as gr",
      "from pathlib import Path",
      "pathlib.PosixPath = pathlib.WindowsPath",
      "",
      "def get_x(r): return f'/kaggle/input/histopathologic-cancer-detection/train/{r['id']}.tif'",
      "def get_y(r): return r['label']",
      "model = load_learner('histopathologic_cancer_detection.pkl')",
      "",
      "def predict_img(img):",
      "try:",
      "pred, pred_idx, probs = model.predict(img)",
      "return f'Prediction: {pred}; Probability: {probs[pred_idx]:.04f}'",
      "except Exception as e:",
      "print(f'An error occurred: {str(e)}')",
      "return str(e)",
      "",
      "iface = gr.Interface(fn=predict_img, inputs=gr.Image(), outputs='text', title='Histopathologic Cancer Detection')",
      "iface.launch()",
    ]}
  />¨
  <Paragraph text="Feil melding:" />
  <Codesnipet
    isError={true}
    code={[
      "Uncaught (in promise):",
      JSON.stringify({
        type: "status",
        endpoint: "/predict",
        fn_index: 0,
        time: "2024-04-21T10:03:05.581Z",
        queue: true,
        message: null,
        stage: "error",
        success: false,
      }),
    ]}
  />
  <Paragraph
    bigP={true}
    text="
  Vi prøvde ut Gradio med en tekstmodell og oppnådde positive resultater. Da vi så nærmere på dette, begynte vi å mistenke at våre tidligere problemer med Svelte kanskje var forårsaket av hvordan plattformen takler TIF-bildefilformatet."
  />
</Articel>
