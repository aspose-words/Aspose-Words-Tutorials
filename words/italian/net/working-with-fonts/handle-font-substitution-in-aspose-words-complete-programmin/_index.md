---
category: general
date: 2026-06-17
description: Gestisci la sostituzione dei font in Aspose.Words e rileva rapidamente
  i font mancanti con questo tutorial passo‑passo per gli sviluppatori .NET.
draft: false
keywords:
- handle font substitution
- detect missing fonts
- how to detect missing fonts
language: it
og_description: Gestisci la sostituzione dei font in Aspose.Words e impara a rilevare
  i font mancanti nei tuoi documenti con esempi di codice chiari.
og_title: Gestisci la sostituzione dei font in Aspose.Words – Guida completa
schemas:
- author: Aspose
  dateModified: '2026-06-17'
  description: Handle font substitution in Aspose.Words and detect missing fonts quickly
    with this step‑by‑step tutorial for .NET developers.
  headline: Handle Font Substitution in Aspose.Words – Complete Programming Guide
  type: TechArticle
- description: Handle font substitution in Aspose.Words and detect missing fonts quickly
    with this step‑by‑step tutorial for .NET developers.
  name: Handle Font Substitution in Aspose.Words – Complete Programming Guide
  steps:
  - name: '**Create a test DOCX** that references a font you know isn’t on the machine
      (e.g., “Comic Sans MS” on a minimal Docker image).'
    text: '**Create a test DOCX** that references a font you know isn’t on the machine
      (e.g., “Comic Sans MS” on a minimal Docker image).'
  - name: Run the console app or API endpoint.
    text: Run the console app or API endpoint.
  - name: Verify that the console (or HTTP response) lists the substitution warning.
    text: Verify that the console (or HTTP response) lists the substitution warning.
  - name: Optionally, open the resulting PDF and check the font properties—Aspose.Words
      should show the fallback font you configured.
    text: Optionally, open the resulting PDF and check the font properties—Aspose.Words
      should show the fallback font you configured.
  type: HowTo
tags:
- Aspose.Words
- .NET
- Font Management
title: Gestire la sostituzione dei font in Aspose.Words – Guida completa alla programmazione
url: /it/net/working-with-fonts/handle-font-substitution-in-aspose-words-complete-programmin/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Gestire la sostituzione dei font in Aspose.Words – Guida completa di programmazione

Ti sei mai chiesto come **gestire la sostituzione dei font** quando un documento Word fa riferimento a un font che non è installato sul server? Non sei l'unico. In molte applicazioni reali—pensiamo a generatori di fatture o servizi di report automatici—i font mancanti causano fallback silenziosi che rovinano il layout.  

La buona notizia è che Aspose.Words fornisce un sistema di avvisi integrato che ti permette di **rilevare i font mancanti** e reagire come desideri. In questo tutorial vedremo come registrare un gestore di avvisi, caricare un documento e estrarre gli eventi di sostituzione dei font di cui hai bisogno. Alla fine vedrai anche come rispondere alla classica domanda “**come rilevare i font mancanti**?” con codice pulito e pronto per la produzione.

## Cosa copre questo tutorial

* Configurare Aspose.Words per generare avvisi per ogni sostituzione di font.
* Catturare quegli avvisi in un gestore personalizzato così da poter registrare, sostituire o abortire.
* Utilizzare i dati catturati per **rilevare i font mancanti** prima che il documento venga salvato o renderizzato.
* Suggerimenti per la risoluzione di casi limite—come quando un font di fallback viene scelto silenziosamente.
* Un esempio completo e funzionante che puoi inserire in qualsiasi app console .NET.

> **Prerequisiti** – Avrai bisogno di un SDK .NET recente (6.0+ va benissimo), di una licenza valida di Aspose.Words per .NET (o di una chiave di valutazione temporanea) e di un file DOCX di esempio che faccia riferimento intenzionalmente a un font non installato. Non sono richieste altre librerie di terze parti.

---

## ## Gestire la sostituzione dei font con un gestore di avvisi personalizzato

Aspose.Words genera un oggetto `WarningInfo` ogni volta che non riesce a trovare un font richiesto. Per impostazione predefinita quegli avvisi vengono ignorati, ed è per questo che spesso non ti accorgi di una sostituzione. Per **gestire la sostituzione dei font**, sostituisci il gestore di avvisi predefinito con uno che faccia effettivamente qualcosa.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // Register a custom warning handler that prints font‑substitution events.
        FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
            (sender, args) =>
            {
                // We're only interested in font‑substitution warnings.
                if (args.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ Font substituted: {args.Description}");
                }
            });

        // Load a document that deliberately references an unavailable font.
        Document doc = new Document("Samples/MissingFont.docx");

        // Force a save to trigger any pending warnings (e.g., PDF conversion).
        doc.Save("Output/Result.pdf");
    }
}
```

### Perché funziona

* `FontSettings.DefaultWarningHandler` è una proprietà statica globale—una volta impostata, **ogni** operazione di Aspose.Words nell'AppDomain corrente utilizza il tuo delegato.
* Il `WarningInfoCollectionHandler` riceve un oggetto `WarningInfo` che contiene `WarningType` e una `Description` leggibile dall’uomo. Filtrare su `WarningType.FontSubstitution` garantisce di vedere solo gli eventi di tuo interesse.
* Chiamare `doc.Save` costringe la libreria a risolvere tutti i font, ed è in quel momento che gli avvisi vengono generati. Se ti serve solo ispezionare il documento senza salvarlo, puoi chiamare `doc.UpdatePageLayout()` al suo posto.

**Output console previsto** (supponendo che il font mancante sia “Papyrus”):

```
⚠️ Font substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
```

Quella riga è la prova che la libreria **ha rilevato i font mancanti** e ha scelto un fallback.

---

## ## Rilevare i font mancanti prima del rendering

A volte vuoi interrompere l’intero processo se un font richiesto è mancante—magari perché le linee guida del brand richiedono una tipografia esatta. Il gestore di avvisi può essere esteso per raccogliere tutti i messaggi di font mancanti in una lista, dopodiché puoi prendere una decisione.

```csharp
using System.Collections.Generic;

// ...

static List<string> missingFonts = new List<string>();

static void Main()
{
    FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
        (sender, args) =>
        {
            if (args.WarningType == WarningType.FontSubstitution)
            {
                // Store the description for later analysis.
                missingFonts.Add(args.Description);
                Console.WriteLine($"⚠️ Font substituted: {args.Description}");
            }
        });

    Document doc = new Document("Samples/MissingFont.docx");
    doc.UpdatePageLayout();   // Triggers warnings without saving.

    if (missingFonts.Count > 0)
    {
        Console.WriteLine("\n❗ Detected missing fonts:");
        foreach (var msg in missingFonts)
            Console.WriteLine($" - {msg}");

        // Optionally abort the operation.
        // throw new InvalidOperationException("Missing required fonts.");
    }
    else
    {
        Console.WriteLine("\n✅ No font substitution detected.");
    }

    // Continue with saving or further processing if you wish.
    doc.Save("Output/Result.pdf");
}
```

### Come risponde a “come rilevare i font mancanti”

* La lista `missingFonts` funge da registro di ogni evento di sostituzione.
* Dopo `UpdatePageLayout`, puoi ispezionare la lista e decidere se continuare, registrare o lanciare un’eccezione.
* Questo pattern funziona per qualsiasi formato di output (PDF, HTML, immagini) perché il sistema di avvisi è indipendente dal formato.

---

## ## Suggerimento avanzato: sostituire i font mancanti con un sostituto specifico

Se hai un font aziendale che deve essere usato, puoi dire ad Aspose.Words di sostituire automaticamente qualsiasi font mancante con il tuo fallback. Questo è utile quando vuoi che il documento *rimanga* accettabile senza post‑processing manuale.

```csharp
// Configure a fallback font collection.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
    "AnyMissingFont", new string[] { "Calibri", "Arial" });

FontSettings.DefaultFontSettings = fontSettings;
```

Inserisci lo snippet sopra **prima** di caricare il documento. Ora qualsiasi font mancante—indipendentemente dal suo nome originale—verrà scambiato con “Calibri” (o “Arial” se Calibri non è presente). Riceverai comunque l’avviso, ma il documento verrà renderizzato con il font che controlli tu.

---

## ## Problemi comuni e come evitarli

| Problema | Perché accade | Soluzione |
|----------|----------------|-----------|
| **Gli avvisi scompaiono dopo la prima chiamata** | Il `DefaultWarningHandler` statico viene sovrascritto più tardi nell’app. | Imposta il gestore **una sola volta** all’avvio dell’applicazione, o conserva un riferimento e riassegna se lo cambi. |
| **Viene segnalato solo il primo font mancante** | Alcune API raggruppano gli avvisi; devi chiamare `UpdatePageLayout` o `Save` per svuotare la coda. | Forza un aggiornamento del layout o salva nel formato che intendi generare. |
| **La sostituzione avviene comunque dopo l’abort** | Il gestore di avvisi viene eseguito *dopo* che la sostituzione è già avvenuta. | Usa il gestore per **registrare** e poi lancia un’eccezione per fermare l’elaborazione ulteriore. |
| **Font mancanti nei container Linux** | Linux spesso non ha il catalogo dei font di Windows, portando a molte sostituzioni. | Monta i font necessari nel container o usa `FontSettings.SetFontsFolder` per puntare a una directory di font personalizzata. |

---

## ## Rilevare la sostituzione dei font in uno scenario Web API

Se servi documenti tramite ASP.NET Core, probabilmente non vuoi scrivere sulla console. Invece, raccogli gli avvisi e restituiscili come parte della risposta HTTP.

```csharp
[ApiController]
[Route("api/[controller]")]
public class DocumentController : ControllerBase
{
    [HttpPost("convert")]
    public IActionResult Convert(IFormFile file)
    {
        var missingFonts = new List<string>();

        FontSettings.DefaultWarningHandler = new WarningInfoCollectionHandler(
            (s, e) =>
            {
                if (e.WarningType == WarningType.FontSubstitution)
                    missingFonts.Add(e.Description);
            });

        using var stream = file.OpenReadStream();
        var doc = new Document(stream);
        doc.UpdatePageLayout();

        if (missingFonts.Any())
        {
            return BadRequest(new { message = "Missing fonts detected", details = missingFonts });
        }

        // Convert to PDF and stream back.
        var pdfStream = new MemoryStream();
        doc.Save(pdfStream, SaveFormat.Pdf);
        pdfStream.Position = 0;
        return File(pdfStream, "application/pdf", "result.pdf");
    }
}
```

Ora l’API **rileva i font mancanti** e restituisce un payload JSON chiaro prima che venga generato qualsiasi PDF. Questa è un’illustrazione pratica di “come rilevare i font mancanti” in un servizio di livello produzione.

---

## ## Testare la tua implementazione

1. **Crea un DOCX di test** che faccia riferimento a un font che sai non sia presente sulla macchina (ad esempio “Comic Sans MS” su un’immagine Docker minimale).  
2. Esegui l’app console o il punto finale dell’API.  
3. Verifica che la console (o la risposta HTTP) elenchi l’avviso di sostituzione.  
4. Facoltativamente, apri il PDF risultante e controlla le proprietà del font—Aspose.Words dovrebbe mostrare il font di fallback che hai configurato.

Se vedi l’avviso ma il PDF utilizza ancora un font inatteso, ricontrolla l’ordine delle impostazioni `SubstitutionSettings`; la prima corrispondenza vince.

---

## ## Conclusione

Abbiamo coperto tutto ciò che ti serve per **gestire la sostituzione dei font** in Aspose.Words, dalla registrazione di un gestore di avvisi al rilevamento programmatico dei **font mancanti** e persino alla loro sostituzione con un carattere aziendale. Sfruttando il sistema di avvisi integrato ottieni piena visibilità su ogni evento “font non trovato”, rispondendo direttamente alla domanda “**come rilevare i font mancanti**?” che ogni sviluppatore si pone quando automatizza la generazione di documenti.

Qual è il prossimo passo? Prova a combinare questa logica con il **caricamento dinamico dei font** (`FontSettings.SetFontsFolder`) per supportare font caricati dagli utenti al volo, oppure estendi il gestore di avvisi per scrivere voci in un servizio di logging centrale come Serilog. Più strumenterai la gestione dei font, più affidabile diventerà il tuo pipeline di documenti.

Hai uno scenario di sostituzione dei font complesso su cui stai lavorando? Lascia un commento qui sotto e risolviamolo insieme. Buon coding!

## Cosa dovresti imparare dopo?


I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [How to Load DOCX and Detect Missing Fonts – Complete C# Guide](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}