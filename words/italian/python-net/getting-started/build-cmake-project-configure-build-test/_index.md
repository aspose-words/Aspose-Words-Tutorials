---
category: general
date: 2026-07-06
description: Compila il progetto CMake passo dopo passo. Impara come configurare CMake,
  come compilare CMake e come eseguire CTest per test affidabili.
draft: false
keywords:
- build cmake project
- how to configure cmake
- how to build cmake
- how to run ctest
- cmake build and test
language: it
og_description: Compila rapidamente un progetto CMake con passaggi chiari. Questa
  guida mostra come configurare CMake, come compilare CMake e come eseguire CTest.
og_title: 'Compilare progetto CMake: Guida alla configurazione, compilazione e test'
schemas:
- author: Aspose
  dateModified: '2026-07-06'
  description: Build CMake project step‑by‑step. Learn how to configure CMake, how
    to build CMake, and how to run CTest for reliable testing.
  headline: 'Build CMake Project: Configure, Build & Test'
  type: TechArticle
tags:
- cmake
- ctest
- build-system
title: 'Compila progetto CMake: Configura, compila e testa'
url: /it/python/getting-started/build-cmake-project-configure-build-test/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Compilare un progetto CMake: Configurare, Compilare e Testare

Ti sei mai chiesto come **compilare un progetto CMake** senza passare ore a cercare su StackOverflow? Non sei l'unico. La maggior parte degli sviluppatori incontra lo stesso ostacolo quando cerca di passare da un semplice `CMakeLists.txt` a una pipeline di build riproducibile. 

In questo tutorial percorreremo l'intero processo—*come configurare CMake*, *come compilare CMake* e *come eseguire CTest*—così otterrai una build pulita e ripetibile che potrai eseguire su qualsiasi macchina. Alla fine avrai un esempio funzionante che potrai copiare‑incollare nel tuo repository, senza script aggiuntivi.

## Prerequisiti — Cosa ti serve prima di iniziare

- Una versione recente di CMake (3.20 o successiva) – le versioni più vecchie mancano di alcuni flag che useremo.
- Un compilatore C++ supportato dalla tua piattaforma (gcc, clang, MSVC, ecc.).
- Un terminale o prompt dei comandi con accesso a `cmake` e `ctest`.
- (Opzionale) Git per clonare il repository di esempio se vuoi seguire il codice sorgente esatto.

Se qualcuno di questi manca, procuratelo subito; altrimenti otterrai errori “command not found” più tardi, e non è mai divertente.

## Passo 1: Configurare il progetto CMake (configurazione Release)

La prima cosa da fare quando *come configurare CMake* è indicare a CMake dove si trovano i sorgenti e dove vuoi che vengano collocati gli artefatti di build. Il flag `-S` punta alla directory dei sorgenti, `-B` crea una cartella di build separata, e `-D CMAKE_BUILD_TYPE=Release` forza una build ottimizzata.

```bash
# Replace YOUR_DIRECTORY with the path to your project root
cmake -S YOUR_DIRECTORY/Examples/DocsExamples \
      -B YOUR_DIRECTORY/Examples/DocsExamples/build \
      -D CMAKE_BUILD_TYPE=Release
```

**Perché è importante:** Tenere separati i file sorgente e di build (build `out‑of‑source`) evita modifiche accidentali al codice sorgente e rende triviale pulire la directory di build in seguito. Il flag `Release` indica anche al compilatore di abilitare le ottimizzazioni, che è ciò che di solito si desidera per un binario finale.

> **Consiglio:** Se ti serve una build Debug per il debug, basta sostituire `Release` con `Debug`. Lo stesso comando funziona—CMake gestisce il resto.

## Passo 2: Compilare il progetto configurato

Ora che il passo di configurazione ha generato tutti i makefile o i file di progetto Visual Studio necessari, puoi effettivamente compilare il codice. L'opzione `--build` astrae lo strumento di build sottostante (`make`, `ninja`, `MSBuild`, ecc.), quindi lo stesso comando funziona su Linux, macOS e Windows.

```bash
cmake --build YOUR_DIRECTORY/Examples/DocsExamples/build
```

**Cosa succede dietro le quinte?** CMake legge il `CMakeCache.txt` creato nel passo precedente, determina lo strumento di build appropriato e lo invoca con i flag corretti. Questo è il nocciolo di *come compilare CMake*—non devi ricordare se stai usando `make` o `ninja`; CMake lo fa per te.

Se vuoi velocizzare le cose su macchine multi‑core, aggiungi `-- -j$(nproc)` (Linux/macOS) o `-- /m` (Windows) dopo il comando:

```bash
cmake --build YOUR_DIRECTORY/Examples/DocsExamples/build -- -j$(nproc)
```

## Passo 3: Eseguire i test di esempio con output dettagliato

Il testing è dove la teoria incontra la pratica. CMake include `ctest`, un driver di test che può scoprire ed eseguire qualsiasi test aggiunto tramite `add_test()` nel tuo `CMakeLists.txt`. Per eseguire i test e vedere l'output dettagliato, usa l'helper `-E chdir` per spostarti nella directory di build prima:

```bash
cmake -E chdir YOUR_DIRECTORY/Examples/DocsExamples/build \
      ctest --verbose
```

**Perché usare `--verbose`?** Stampa la riga di comando di ogni test, il codice di uscita e qualsiasi output scritto dal test stesso. Questo è essenziale quando impari *come eseguire CTest* perché mostra esattamente cosa succede dietro le quinte.

Typical output looks like this:

```
Test project /path/to/DocsExamples/build
    Start 1: MyFirstTest
1/1 Test #1: MyFirstTest .......................   Passed    0.02 sec

100% tests passed, 0 tests failed
```

Se un test fallisce, il log dettagliato includerà il comando fallito e eventuali messaggi di errore, rendendo il debug molto più veloce.

## Passo 4: Automatizzare l'intero flusso di lavoro (Opzionale)

Per molti progetti vorrai una singola riga di comando che configuri, compili e testi in un unico passaggio. Puoi ottenerlo con un semplice script Bash (o PowerShell):

```bash
#!/usr/bin/env bash
SRC=YOUR_DIRECTORY/Examples/DocsExamples
BUILD=$SRC/build

# 1️⃣ Configure
cmake -S "$SRC" -B "$BUILD" -D CMAKE_BUILD_TYPE=Release

# 2️⃣ Build
cmake --build "$BUILD" -- -j$(nproc)

# 3️⃣ Test
cmake -E chdir "$BUILD" ctest --verbose
```

Salvalo come `run_all.sh`, rendilo eseguibile (`chmod +x run_all.sh`), e avrai una pipeline **cmake build and test** riproducibile che puoi inserire in qualsiasi sistema CI (GitHub Actions, GitLab CI, Azure Pipelines, come preferisci).

## Casi limite e problemi comuni

| Situazione | Cosa controllare | Soluzione |
|-----------|-------------------|-----|
| **Compilatore mancante** | CMake aborts with “No CMAKE_CXX_COMPILER could be found.” | Installa un compilatore (`sudo apt install build-essential` su Ubuntu, `xcode-select --install` su macOS). |
| **La cartella out‑of‑source esiste già** | CMake potrebbe rifiutare di riconfigurare se la cartella contiene file obsoleti. | Elimina la directory `build` (`rm -rf build`) o esegui `cmake --fresh` (CMake 3.24+). |
| **CTest non riesce a trovare i test** | `add_test()` non è mai stato chiamato o l'eseguibile del test non è stato compilato. | Verifica che `add_test(NAME MyTest COMMAND MyTestExe)` sia presente in `CMakeLists.txt` e che il target venga compilato. |
| **Le build parallele entrano in conflitto su comandi personalizzati** | Alcuni comandi personalizzati non sono contrassegnati come `DEPENDS`, causando fallimenti non deterministici. | Aggiungi corretti `add_custom_command(... DEPENDS ...)`. |

Comprendere queste sfumature fa la differenza tra una build instabile e una pipeline CI solida come una roccia.

## Panoramica visiva (Il testo alternativo include la parola chiave)

![Diagramma che mostra il flusso di configurazione, compilazione e test di un progetto CMake](/images/cmake-workflow.png "Diagramma del flusso di lavoro Build CMake Project")

## Riepilogo – Cosa hai imparato

Abbiamo iniziato con la domanda fondamentale: *come compilare un progetto CMake* da zero. Alla fine ora sai come **configurare CMake** con una build pulita out‑of‑source, **compilare CMake** usando il flag universale `--build`, e **eseguire CTest** con output dettagliato per verificare che tutto funzioni. Hai anche uno script pronto all'uso che collega i tre passaggi, fornendoti un flusso di lavoro completo **cmake build and test**.

## Cosa c'è dopo?

- **Aggiungere il reporting della copertura** – integra `gcov` o `llvm-cov` e lascia che CTest pubblichi i risultati.
- **Cross‑compilation** – esplora `-DCMAKE_TOOLCHAIN_FILE` per compilare su dispositivi embedded.
- **Creazione di pacchetti** – usa `cpack` per impacchettare i tuoi binari per la distribuzione.
- **Integrazione CI** – copia lo script in un workflow di GitHub Actions e osserva l'automazione eseguirsi su ogni pull request.

Sentiti libero di sperimentare con diversi tipi di build, aggiungere più test o sostituire il sorgente di esempio con il tuo progetto. I pattern che abbiamo coperto oggi si applicano a qualsiasi codebase basata su CMake, sia che si tratti di una piccola utility o di un enorme sistema multi‑modulo.

Buona compilazione, e che le tue build CMake siano sempre riproducibili!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Come esportare LaTeX da Word – Guida passo‑passo](/words/english/net/basic-conversions/how-to-export-latex-from-word-step-by-step-guide/)
- [Come salvare Markdown da DOCX – Guida passo‑passo](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)
- [Come visualizzare la versione di Aspose.Words in Python e .NET: Guida passo‑passo](/words/english/python-net/document-properties-metadata/display-aspose-words-version-python-net/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}