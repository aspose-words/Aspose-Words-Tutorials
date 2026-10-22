---
category: general
date: 2026-10-13
description: Impara la sostituzione dei caratteri in un documento usando C#. Questa
  guida mostra come impostare la codifica big5, caricare un DOCX e sostituire i caratteri
  legacy con quelli moderni.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- font substitution in document
- big5 encoding
- C# LoadOptions
- legacy font replacement
- document encoding for Chinese
- Docx loading C#
language: it
lastmod: 2026-10-13
og_description: La sostituzione dei font nel documento è essenziale quando si lavora
  con file cinesi legacy. Segui questo tutorial passo‑passo per caricare un DOCX con
  codifica big5 e sostituire i vecchi font.
og_image_alt: Screenshot of C# code that performs font substitution in document
og_title: Sostituzione dei font in un documento con C# – guida completa
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn font substitution in document using C#. This guide shows how
    to set big5 encoding, load a DOCX, and replace legacy fonts with modern ones.
  headline: How to perform font substitution in document with C#
  type: TechArticle
tags:
- C#
- Aspose.Words
- Unicode
- Chinese text
title: Come eseguire la sostituzione dei font in un documento con C#
url: /it/net/working-with-fonts/how-to-perform-font-substitution-in-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Sostituzione dei font nel documento – tutorial completo C#

Se hai bisogno di **font substitution in document** per visualizzare correttamente i file cinesi legacy, questa guida ti mostra esattamente come farlo. Configurando la codifica del testo corretta e sostituendo un font obsoleto con uno moderno, garantisci che il DOCX finale venga visualizzato come previsto.

L'elaborazione dei documenti spesso fallisce quando la sorgente utilizza una codifica vecchia come **big5** o fa riferimento a un font che non esiste più sul sistema. Questo tutorial ti guida nel caricamento di un DOCX con la corretta **big5 encoding**, nell'applicazione della **legacy font replacement** e nella produzione di un output pulito che funziona su qualsiasi macchina Windows.

Imparerai:

* Come creare un oggetto `LoadOptions` con **big5 encoding**.  
* Come aprire un file DOCX usando **C# LoadOptions**.  
* Come eseguire **font substitution in document** mappando un vecchio font a un equivalente moderno.  
* Gestione dei casi limite per font mancanti e famiglie di font multiple.

Non sono necessari strumenti esterni oltre alla libreria Aspose.Words per .NET, e il codice completo può essere copiato in un progetto console e eseguito immediatamente.

## Prerequisiti

* .NET 6.0 o successivo (l'esempio utilizza la sintassi della console .NET 6).  
* Aspose.Words per .NET – installare tramite `dotnet add package Aspose.Words`.  
* Un file DOCX salvato con **big5 encoding** che fa riferimento al font legacy `MingLiU-ExtB`.  
* Familiarità di base con C# e Visual Studio o qualsiasi IDE a tua scelta.

## Passo 1: Configurare il progetto e importare i namespace

Crea una nuova applicazione console e aggiungi le direttive `using` richieste. Questo assicura che il codice venga compilato senza modifiche aggiuntive.

```csharp
using System;
using System.Text;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSubstitutionDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The tutorial steps are called from here.
            PerformFontSubstitution();
        }

        static void PerformFontSubstitution()
        {
            // Steps 2‑4 are implemented inside this method.
        }
    }
}
```

> **Consiglio:** Mantieni il metodo `Main` il più minimale possibile; migliora la leggibilità e rende il tutorial più facile da seguire.

## Passo 2: Definire le opzioni di caricamento con la corretta codifica del testo (big5 per il cinese tradizionale)

La classe `LoadOptions` indica ad Aspose.Words come interpretare i byte grezzi nel file sorgente. L'uso della **big5 encoding** è fondamentale per i caratteri cinesi tradizionali salvati con quella pagina di codice legacy.

```csharp
// Step 2: Define load options with big5 encoding.
LoadOptions loadOptions = new LoadOptions
{
    // Explicitly set the encoding to the traditional Chinese code page.
    Encoding = Encoding.GetEncoding("big5")
};
```

**Perché è importante:** Se ometti la codifica o usi l'UTF‑8 predefinito, i caratteri possono apparire come simboli incomprensibili (mojibake). Specificare `big5` preserva i glifi originali prima di qualsiasi sostituzione di font.

## Passo 3: Caricare il file DOCX usando la codifica specificata

Passa l'istanza `loadOptions` al costruttore `Document`. Questo carica il file rispettando la **document encoding for Chinese** definita in precedenza.

```csharp
// Step 3: Load the DOCX file with the big5 encoding.
string inputPath = @"C:\Docs\big5_doc.docx"; // Update this path to your file location.
Document doc = new Document(inputPath, loadOptions);
```

Se il file non viene trovato, il programma genera una `FileNotFoundException`. Assicurati che il percorso sia corretto e che l'applicazione abbia i permessi di lettura.

## Passo 4: Sostituire un font legacy con un equivalente moderno

Molti documenti cinesi più vecchi fanno riferimento a `MingLiU-ExtB`, che potrebbe non essere presente nelle installazioni Windows più recenti. Mappandolo a `Microsoft JhengHei` (un font Unicode ampiamente disponibile) garantisci una corretta visualizzazione.

```csharp
// Step 4: Perform font substitution in document.
doc.FontInfos.Substitution.Add("MingLiU-ExtB", "Microsoft JhengHei");

// Optional: Verify that the substitution succeeded.
foreach (FontInfo fontInfo in doc.FontInfos)
{
    Console.WriteLine($"Original: {fontInfo.FontFamilyName}, Substituted: {fontInfo.SubstitutedFontFamilyName}");
}
```

**Spiegazione:**  
* `FontInfos.Substitution.Add(oldFont, newFont)` registra una regola di sostituzione globale. Ogni volta che Aspose.Words incontra `MingLiU-ExtB`, lo sostituisce con `Microsoft JhengHei`.  
* Il ciclo opzionale stampa la mappatura, utile per il debug in documenti grandi con più famiglie di font.

## Passo 5: Salvare il documento elaborato

Dopo la sostituzione, scrivi il documento in un nuovo file. L'output mostrerà il testo cinese usando il font moderno, eliminando gli avvisi di glifi mancanti.

```csharp
// Step 5: Save the updated document.
string outputPath = @"C:\Docs\big5_doc_fixed.docx";
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved to {outputPath}");
```

Apri il file risultante in Microsoft Word o in qualsiasi visualizzatore DOCX; dovresti vedere i caratteri cinesi tradizionali renderizzati correttamente con `Microsoft JhengHei`.

## Gestione dei casi limite e delle insidie comuni

| Situazione | Approccio consigliato |
|-----------|----------------------|
| **Il font sorgente non è elencato nel documento** | Usa `doc.FontInfos.Substitution.Add` con un pattern wildcard, ad esempio `doc.FontInfos.Substitution.Add("*MingLiU*", "Microsoft JhengHei")`. |
| **È necessario sostituire più font legacy** | Chiama `Add` per ogni coppia, oppure carica un dizionario di sostituzione da un file di configurazione. |
| **Il font di destinazione non è disponibile sulla macchina di destinazione** | Scegli un font fornito con Windows (es. `Arial Unicode MS`) o incorpora il font usando `doc.FontInfos.EmbeddingMode = FontEmbeddingMode.EmbedAll`. |
| **Persistono errori di codifica** | Verifica che il file sorgente utilizzi davvero **big5**; puoi ispezionarlo con un editor esadecimale o usare `File.ReadAllBytes` e confrontare i pattern di byte. |

## Esempio completo funzionante

Di seguito trovi il programma completo e autonomo. Copialo in `Program.cs`, regola i percorsi dei file e avvialo.

```csharp
using System;
using System.Text;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSubstitutionDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            PerformFontSubstitution();
        }

        static void PerformFontSubstitution()
        {
            // 1️⃣ Define big5 encoding for Traditional Chinese.
            LoadOptions loadOptions = new LoadOptions
            {
                Encoding = Encoding.GetEncoding("big5")
            };

            // 2️⃣ Load the DOCX that uses the legacy font.
            string inputPath = @"C:\Docs\big5_doc.docx";
            Document doc = new Document(inputPath, loadOptions);

            // 3️⃣ Substitute MingLiU-ExtB with Microsoft JhengHei.
            doc.FontInfos.Substitution.Add("MingLiU-ExtB", "Microsoft JhengHei");

            // 4️⃣ (Optional) Log substitution details for verification.
            foreach (FontInfo fontInfo in doc.FontInfos)
            {
                Console.WriteLine($"Original: {fontInfo.FontFamilyName}, Substituted: {fontInfo.SubstitutedFontFamilyName}");
            }

            // 5️⃣ Save the corrected document.
            string outputPath = @"C:\Docs\big5_doc_fixed.docx";
            doc.Save(outputPath, SaveFormat.Docx);

            Console.WriteLine($"✅ Font substitution in document completed. Output saved to {outputPath}");
        }
    }
}
```

**Risultato atteso:** L'apertura di `big5_doc_fixed.docx` mostra tutti i caratteri cinesi tradizionali renderizzati correttamente, senza avvisi di glifi mancanti, perché `MingLiU-ExtB` è stato sostituito da `Microsoft JhengHei`.

## Conclusione

Ora disponi di un metodo affidabile per le attività di **font substitution in document** usando C#. Configurando la **big5 encoding**, caricando il DOCX con `LoadOptions` e mappando i font legacy a equivalenti moderni, elimini i problemi di rendering che affliggono i vecchi file cinesi.  

Da qui puoi:

* Estendere la mappa di sostituzione per coprire altri font legacy.  
* Automatizzare il processo per lotti di documenti (ciclo su una cartella).  
* Combinare la sostituzione dei font con altre trasformazioni di documento, come l'aggiunta di filigrane o la conversione in PDF.

Sentiti libero di sperimentare con diversi font di destinazione o di incorporare font personalizzati per una piena portabilità. Se incontri problemi, rivedi la tabella dei casi limite sopra o consulta la documentazione di Aspose.Words per la gestione avanzata dei font.

Happy coding!

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Abilita avvisi di sostituzione dei font in Aspose.Words – Guida completa](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [Registra avvisi di sostituzione dei font – Guida completa Aspose.Words](/words/english/net/working-with-fonts/log-font-substitution-warnings-complete-aspose-words-guide/)
- [Carica con codifica in documento Word](/words/english/net/programming-with-loadoptions/load-with-encoding/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}