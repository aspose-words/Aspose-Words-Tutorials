---
category: general
date: 2026-06-24
description: Come utilizzare IWarningCallback per rilevare i font mancanti nei documenti
  Aspose.Words. Scopri un esempio completo, eseguibile, e le migliori pratiche.
draft: false
keywords:
- how to use iwarningcallback
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
- missing font detection in .docx
language: it
og_description: Come utilizzare IWarningCallback per rilevare i font mancanti in Aspose.Words.
  Segui la guida passo‑passo per una soluzione completa e pronta per la produzione.
og_title: Come usare IWarningCallback – Rilevare i font mancanti
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: How to use IWarningCallback to detect missing fonts in Aspose.Words
    documents. Learn a full, runnable example and best practices.
  headline: How to Use IWarningCallback – Detect Missing Fonts with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document Processing
title: Come utilizzare IWarningCallback – Rilevare i font mancanti con Aspose.Words
url: /it/net/working-with-fonts/how-to-use-iwarningcallback-detect-missing-fonts-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come usare IWarningCallback – Rilevare i font mancanti con Aspose.Words

Usare **IWarningCallback** è fondamentale quando lavori con Aspose.Words e devi **rilevare i font mancanti** in un file DOCX. In questa guida percorreremo un esempio completo, pronto da copiare‑incollare, che mostra esattamente come utilizzare IWarningCallback per intercettare gli avvisi di sostituzione dei font, perché è importante e cosa fare una volta catturati.

Se hai mai aperto un documento e hai visto del testo illeggibile perché un font personalizzato non era installato, conosci la frustrazione. Alla fine di questo tutorial avrai un modo affidabile per evidenziare questi problemi programmaticamente, registrarli o addirittura applicare automaticamente un font di fallback.

## Cosa imparerai

- Lo scopo di **IWarningCallback** e quando usarlo.  
- Come implementare un raccoglitore di avvisi personalizzato che isola gli eventi di **rilevamento dei font mancanti**.  
- Come collegare il raccoglitore a **LoadOptions** affinché ogni caricamento di documento sia monitorato.  
- Come verificare l'output e gestire i casi limite (più font mancanti, avvisi silenziosi, ecc.).  

### Prerequisiti

- .NET 6.0 o successivo (il codice funziona anche su .NET Framework 4.6+).  
- Aspose.Words per .NET installato via NuGet (`Install-Package Aspose.Words`).  
- Un file DOCX che faccia riferimento a un font non presente sulla macchina (ad es., `DocumentWithMissingFont.docx`).  

Non sono necessarie librerie aggiuntive—tutto è contenuto in Aspose.Words.

---

## Come usare IWarningCallback per rilevare i font mancanti in Aspose.Words

Di seguito trovi il **programma completo e eseguibile**. Copialo in un nuovo progetto console, regola il percorso del file e avvialo. Vedrai l'output sulla console per ogni avviso di font mancante.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    // Step 1: Create a warning collector that implements IWarningCallback.
    // This collector will be invoked each time Aspose.Words raises a warning.
    class FontWarningCollector : IWarningCallback
    {
        // The Warning method receives a WarningInfo object.
        // We filter for FontSubstitution warnings because those indicate missing fonts.
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                // Print the warning to the console – you could also log to a file or database.
                Console.WriteLine($"[Missing Font] {info.Description}");
            }
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 2: Configure LoadOptions to use our custom collector.
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningCollector()
            };

            // Step 3: Load the document with the specified options.
            // Any font that cannot be resolved triggers the warning collector above.
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFont.docx";

            try
            {
                Document doc = new Document(docPath, loadOptions);
                Console.WriteLine("Document loaded successfully.");
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Error loading document: {ex.Message}");
            }

            // Keep the console window open when debugging.
            Console.WriteLine("Press any key to exit...");
            Console.ReadKey();
        }
    }
}
```

### Output previsto

Se `DocumentWithMissingFont.docx` fa riferimento a un font chiamato *“MyFancyFont”* che non è installato, vedrai qualcosa di simile:

```
[Missing Font] Font substitution: The font 'MyFancyFont' was not found. Substituted with 'Arial'.
Document loaded successfully.
Press any key to exit...
```

Ogni riga preceduta da **[Missing Font]** è generata dalla nostra implementazione di **IWarningCallback**, dimostrando che abbiamo **rilevato con successo i font mancanti**.

---

## Passo 1: Implementare l'interfaccia IWarningCallback

Perché abbiamo bisogno di una classe personalizzata? Aspose.Words genera **avvisi** per vari motivi—problemi di formato, funzionalità deprecate e, soprattutto per noi, la sostituzione dei font. Implementando `IWarningCallback`, otteniamo un hook che riceve ogni avviso al momento in cui si verifica. Filtrare per `WarningType.FontSubstitution` isola lo scenario specifico in cui un font è mancante.

**Consiglio:** Se vuoi catturare *tutti* gli avvisi per scopi diagnostici, rimuovi semplicemente il controllo `if` e registra ogni `info.Type`.

---

## Passo 2: Collegare il callback a LoadOptions

`LoadOptions` è il punto di ingresso che indica ad Aspose.Words come trattare il documento in ingresso. Impostare `WarningCallback` su un'istanza del nostro raccoglitore garantisce che il callback sia attivo per l'intera operazione di caricamento. Puoi riutilizzare lo stesso oggetto `LoadOptions` per più documenti, il che è comodo nei pipeline di elaborazione batch.

**Domanda comune:** *E se carico un documento senza specificare LoadOptions?*  
Risposta: Aspose.Words genererà comunque avvisi internamente, ma senza un callback verranno scartati silenziosamente, e perderai la possibilità di **rilevare i font mancanti**.

---

## Passo 3: Caricare un documento e catturare gli avvisi di font mancanti

Il costruttore `Document` che accetta un percorso file e `LoadOptions` esegue il lavoro pesante. Man mano che il file viene analizzato, qualsiasi font mancante attiva il metodo `FontWarningCollector.Warning`. L'output sulla console dimostra che il meccanismo funziona.

**Caso limite:** Un singolo documento può fare riferimento a diversi font assenti. Il callback si attiva una volta per ogni font mancante, quindi vedrai più righe—perfetto per costruire un report completo.

---

## Perché usare IWarningCallback invece di controlli manuali dei font?

Potresti scansionare manualmente le proprietà `Run.Font` del documento dopo il caricamento, ma ciò richiederebbe che il documento si carichi correttamente—cosa che fallisce se il font è completamente indisponibile. Il sistema di avvisi funziona **prima** che avvenga qualsiasi sostituzione, fornendoti un quadro reale di ciò che manca.

Inoltre, il callback viene eseguito **all'interno della pipeline di caricamento**, il che ti permette di interrompere l'operazione in anticipo, sostituire i font al volo o registrare diagnostica dettagliata senza passaggi aggiuntivi sull'albero del documento.

---

## Gestire più font mancanti in modo elegante

Se prevedi molti font mancanti, considera di aggregarli in una collezione:

```csharp
class AggregatingFontCollector : IWarningCallback
{
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            MissingFonts.Add(info.Description);
        }
    }
}
```

Dopo il caricamento, puoi iterare su `MissingFonts` e, ad esempio, scriverli in un file CSV per il team di design.

---

## Bonus: Registrare gli avvisi su file

L'output sulla console è sufficiente per le demo, ma il codice di produzione solitamente registra su una destinazione persistente. Sostituisci la chiamata `Console.WriteLine` con qualcosa del tipo:

```csharp
File.AppendAllText("font-warnings.log", $"{DateTime.Now}: {info.Description}{Environment.NewLine}");
```

Ora disponi di una traccia di audit che può essere rivista in seguito, soddisfacendo i requisiti di conformità.

---

## Conclusione

Abbiamo coperto **come usare IWarningCallback** per **rilevare i font mancanti** in Aspose.Words, dall'implementazione del callback al collegamento a `LoadOptions` e alla gestione degli avvisi risultanti. Questo approccio ti fornisce una visione in tempo reale dei problemi legati ai font, permettendoti di registrarli, sostituirli o avvisare gli utenti prima che il documento venga renderizzato.

Prossimi passi che potresti esplorare:

- **Font di fallback:** assegnare programmaticamente un font predefinito quando avviene una sostituzione.  
- **Elaborazione batch:** iterare su una cartella di documenti, riutilizzando lo stesso `AggregatingFontCollector`.  
- **Feedback all'utente:** mostrare gli avvisi di font mancanti in un'interfaccia UI anziché nella console.

Provalo nel tuo progetto—niente più testo incomprensibile, solo diagnostica chiara e azionabile. Buona programmazione!

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell'API e a esplorare approcci alternativi di implementazione nei tuoi progetti.

- [How to Load DOCX and Detect Missing Fonts – Complete C# Guide](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)
- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [How to Use LoadOptions in Aspose.Words – Complete Guide](/words/english/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}