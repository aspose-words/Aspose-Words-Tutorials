---
category: general
date: 2026-07-16
description: Il tutorial cmake build x64 mostra come usare CMake per generare una
  soluzione Visual Studio 2022 e compilare un progetto VS su un host a 64 bit. Include
  i passaggi per impostare la directory di origine.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- cmake build x64
- cmake generate visual studio
- build vs project
- how to use cmake
- set source directory
language: it
lastmod: 2026-07-16
og_description: 'cmake build x64 spiegato: impara come impostare la directory di origine,
  generare una soluzione Visual Studio 2022 e compilare un progetto VS su un host
  a 64‑bit.'
og_image_alt: Diagram illustrating cmake build x64 workflow from source folder to
  VS2022 solution
og_title: cmake build x64 – Guida passo‑passo per generare e compilare soluzioni VS 2022
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: cmake build x64 tutorial shows how to use CMake to generate a Visual
    Studio 2022 solution and build a VS project on a 64‑bit host. Includes set source
    directory steps.
  headline: cmake build x64 – Complete Guide to Generating and Building VS 2022 Projects
  type: TechArticle
tags:
- cmake
- visual-studio
- x64
- build-automation
title: cmake build x64 – Guida completa alla generazione e alla compilazione di progetti
  VS 2022
url: /it/python/integration-interoperability/cmake-build-x64-complete-guide-to-generating-and-building-vs/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# cmake build x64 – Guida completa per generare e compilare progetti VS 2022

Ti sei mai chiesto **come usare CMake** per produrre una soluzione Visual Studio a 64 bit senza impazzire? Non sei solo. In questo tutorial seguirà un flusso di lavoro **cmake build x64** che imposta la directory sorgente, esegue il generatore per Visual Studio 2022 e infine compila il progetto VS—tutto con pochi comandi Bash puliti.

Alla fine della guida avrai uno script riproducibile da inserire in qualsiasi repository, oltre a una solida comprensione dei concetti di base così da poterlo adattare alle tue esigenze.

---

## Cosa imparerai

- **Imposta correttamente la directory sorgente** in modo che CMake sappia dove si trova il tuo `CMakeLists.txt`.  
- **cmake generate visual studio** – invoca il generatore Visual Studio 2022 con i flag corretti per host e architettura.  
- Esegui un **cmake build x64** della soluzione generata, opzionalmente selezionando la configurazione Release.  
- Comprendi le insidie comuni quando provi a **build vs project** su una macchina a 64‑bit.  

Nessuna magia avanzata di CMake richiesta; basta un terminale e un'installazione recente di Visual Studio.

---

## Prerequisiti

| Requisito | Perché è importante |
|-----------|----------------------|
| CMake ≥ 3.20 | Supporta i flag `-Thost=` e `-Ax64` usati per build a 64‑bit. |
| Visual Studio 2022 (Community, Professional o Enterprise) | Il generatore `Visual Studio 17 2022` fa riferimento a questa versione. |
| Una shell compatibile Bash (Git Bash, WSL, PowerShell con alias `bash`) | Lo script qui sotto usa la sintassi Bash per chiarezza. |
| Albero sorgente contenente un `CMakeLists.txt` valido | CMake non può generare una soluzione senza di esso. |

Se manca qualcuno di questi, installalo prima—CMake da <https://cmake.org/download/> e VS 2022 dal programma di installazione Microsoft.

---

## Passo 1 – Imposta le directory sorgente e di build (`set source directory`)

Prima di chiamare CMake devi dirgli **dove** cercare i file del progetto. Codificare percorsi in modo statico rende lo script fragile, quindi useremo variabili d'ambiente che potrai regolare per progetto.

```bash
# Define where your source lives and where the generated files will be placed
SRC_DIR="YOUR_DIRECTORY/Examples/DocsExamples"
BUILD_DIR="${SRC_DIR}/build"
```

> **Perché è importante:**  
> CMake tratta la *directory sorgente* (`SRC_DIR`) come la radice del progetto. La *directory di build* (`BUILD_DIR`) è dove vivono tutti i file intermedi, le cache e il file finale `.sln`. Tenerle separate evita di inquinare l’albero sorgente e rende la pulizia triviale (`rm -rf "$BUILD_DIR"`).

Puoi sostituire `YOUR_DIRECTORY` con qualsiasi percorso assoluto o relativo; assicurati solo che la cartella contenga un `CMakeLists.txt`.

---

## Passo 2 – Genera una soluzione Visual Studio 2022 (`cmake generate visual studio`)

Ora chiediamo a CMake di produrre una soluzione VS 2022 che punti a **x64**. I flag chiave sono:

- `-G "Visual Studio 17 2022"` – seleziona il generatore VS 2022.  
- `-Thost=x64` – indica a CMake che l'*host* (l’IDE) gira come processo a 64 bit.  
- `-Ax64` – forza il progetto generato a compilare per l'architettura x64.

```bash
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 -S "$SRC_DIR" -B "$BUILD_DIR"
```

> **Cosa succede dietro le quinte?**  
> CMake legge `CMakeLists.txt` da `$SRC_DIR`, risolve tutte le chiamate `add_executable()` e `add_library()`, quindi crea un file `.sln` e un insieme di file `.vcxproj` all’interno di `$BUILD_DIR`. Quei file di progetto sono ora pronti per essere aperti in Visual Studio o compilati dalla riga di comando.

Se esegui il comando e vedi una lunga lista di messaggi di configurazione che termina con `-- Configuring done` e `-- Generating done`, hai completato con successo il passo **cmake generate visual studio**.

---

## Passo 3 – Compila la soluzione generata (`cmake build x64`)

Con la soluzione pronta, il passo logico successivo è compilarla. CMake può gestire la build per te, delegando a MSBuild in background.

```bash
cmake --build "$BUILD_DIR" --config Release
```

> **Perché usare `--config Release`?**  
> I progetti Visual Studio supportano più configurazioni (Debug, Release, RelWithDebInfo, ecc.). Specificare `Release` garantisce che i binari siano ottimizzati per la produzione e che il relativo `.exe` o `.dll` risieda nella cartella `Release/` all’interno dell’albero di build.

Se preferisci una build Debug, sostituisci `Release` con `Debug`. Il comando funziona allo stesso modo, dimostrando che **come usare CMake** per configurazioni diverse è solo una questione di scambiare questo flag.

---

## Passo 4 – Verifica la build (`build vs project` sanity check)

Una compilazione riuscita dovrebbe lasciarti con un eseguibile o una libreria. Verifichiamone l’esistenza:

```bash
# Example for an executable named MyApp.exe
if [[ -f "$BUILD_DIR/Release/MyApp.exe" ]]; then
  echo "✅ Build succeeded! Executable ready at $BUILD_DIR/Release/MyApp.exe"
else
  echo "❌ Build failed or executable not found."
fi
```

> **Insidie comuni:**  
> - Dimenticare di eseguire il passo del generatore dopo aver modificato `CMakeLists.txt` farà fallire questo controllo.  
> - Mescolare toolchain a 32 bit e 64 bit può provocare errori di linker; mantieni sempre `-Ax64` coerente.  
> - Se vedi errori “MSB3073”, di solito significa che un passo post‑build (come la copia di risorse) è fallito—esamina l’output per indizi.

---

## Passo 5 – Pulizia e riesecuzione (Iterare su un `cmake build x64`)

Durante lo sviluppo spesso è necessario ricostruire da zero. Il modo più pulito è eliminare la cartella di build e ricominciare:

```bash
rm -rf "$BUILD_DIR"
mkdir "$BUILD_DIR"
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 -S "$SRC_DIR" -B "$BUILD_DIR"
cmake --build "$BUILD_DIR" --config Release
```

> **Suggerimento:**  
> Aggiungere `-DCMAKE_BUILD_TYPE=Release` al comando del generatore è opzionale per generatori multi‑config come Visual Studio, ma può tornare utile quando si passa a un generatore a configurazione singola come Ninja.

---

## Passo 6 – Estendere lo script (Scenari avanzati `cmake generate visual studio`)

E se il tuo progetto si trovasse in una sottodirectory, o avessi bisogno di passare definizioni personalizzate? CMake lo permette con gli argomenti `-D`:

```bash
cmake -G "Visual Studio 17 2022" -Thost=x64 -Ax64 \
      -S "$SRC_DIR" -B "$BUILD_DIR" \
      -DMyFeature_ENABLED=ON -DCMAKE_INSTALL_PREFIX="/opt/myapp"
```

Ora la soluzione VS generata avrà la macro `MyFeature_ENABLED` definita, e il target di installazione posizionerà i file sotto `/opt/myapp`. Questo dimostra la flessibilità di **come usare CMake** oltre il flusso di base a tre passi.

---

## Output previsto

Quando esegui lo script completo dall’inizio alla fine, il terminale dovrebbe mostrare qualcosa di simile:

```
-- The C compiler identification is MSVC 19.35.31107.0
-- The CXX compiler identification is MSVC 19.35.31107.0
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
...
-- Configuring done
-- Generating done
-- Build files have been written to: /path/to/Examples/DocsExamples/build
...
[ 50%] Building CXX object CMakeFiles/MyApp.dir/main.cpp.obj
[100%] Linking CXX executable Release/MyApp.exe
✅ Build succeeded! Executable ready at /path/to/Examples/DocsExamples/build/Release/MyApp.exe
```

Se qualcosa va storto, CMake emetterà messaggi di errore che indicano la riga incriminata in `CMakeLists.txt` o componenti SDK mancanti—perfetto per un debug rapido.

---

## Conclusione

Abbiamo coperto tutto ciò che serve per eseguire un **cmake build x64**: impostare la directory sorgente, invocare il passo **cmake generate visual studio**, compilare il **build vs project** risultante e verificare l’output. Lo script è compatto, portabile e pronto per l’integrazione in pipeline CI o flussi di lavoro locali.

Prossimamente potresti esplorare:

- Aggiungere l’esecuzione di test unitari con `ctest`.  
- Passare al generatore Ninja per build incrementali più veloci (`-G Ninja`).  
- Usare i preset di CMake (`CMakePresets.json`) per memorizzare i flag appena digitati.

Sentiti libero di sperimentare, rompere le cose e poi ricostruire—dopotutto è il modo più veloce per imparare **come usare CMake** in modo efficace. Buona compilazione!

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi con spiegazioni passo‑passo per aiutarti a padroneggiare ulteriori funzionalità API e a esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Costruisci tabella](/words/hindi/net/add-content-using-documentbuilder/build-table/)
- [Costruisci tabella con stile](/words/hindi/net/programming-with-table-styles-and-formatting/build-table-with-style/)
- [Costruisci tabella con bordi](/words/hindi/net/programming-with-table-styles-and-formatting/build-table-with-borders/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}