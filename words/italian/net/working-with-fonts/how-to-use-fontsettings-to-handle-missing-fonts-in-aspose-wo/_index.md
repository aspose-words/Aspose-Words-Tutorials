---
category: general
date: 2026-03-16
description: Scopri come utilizzare FontSettings in Aspose.Words per gestire i font
  mancanti in modo elegante—codice completo, gestione degli eventi e consigli sulle
  migliori pratiche.
draft: false
keywords:
- how to use fontsettings
- handle missing fonts
- Aspose.Words font substitution
- missing font detection C#
- document loading options
language: it
og_description: Come utilizzare FontSettings in Aspose.Words per gestire i font mancanti—guida
  passo passo con esempio completo in C# e consigli pratici.
og_title: Come utilizzare FontSettings per gestire i caratteri mancanti in Aspose.Words
tags:
- Aspose.Words
- C#
- Font Management
title: Come utilizzare FontSettings per gestire i caratteri mancanti in Aspose.Words
url: /it/net/working-with-fonts/how-to-use-fontsettings-to-handle-missing-fonts-in-aspose-wo/
---

per gestire i caratteri mancanti in Aspose.Words"

- Paragraphs etc.

Make sure to keep **bold** formatting.

Translate bullet points.

Translate table content.

Translate "Pro tip", "Expected Console Output", "What to Expect", etc.

Make sure not to translate code block placeholders.

Also note "RTL formatting if needed" but Italian is LTR, fine.

Let's craft translation.

Will keep code block placeholders as is.

Now produce final content.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come utilizzare FontSettings per gestire i caratteri mancanti in Aspose.Words

Ti sei mai chiesto **come utilizzare FontSettings** quando i tuoi documenti Word fanno riferimento a caratteri che non sono installati sul server? Non sei il solo. I caratteri mancanti possono causare sostituzioni brutte o addirittura generare eccezioni, e la maggior parte degli sviluppatori ignora semplicemente il problema finché non appare in produzione.  

In questo tutorial ti mostreremo esattamente **come utilizzare FontSettings** per **gestire i caratteri mancanti** in Aspose.Words, catturare avvisi dettagliati e mantenere il rendering dei documenti prevedibile. Alla fine avrai un esempio C# pronto all'uso, comprenderai perché ogni riga è importante e saprai come adattare la soluzione a progetti più grandi.

## Cosa copre questa guida

- Configurare **FontSettings** e sottoscrivere l'evento `SubstitutionWarning`.  
- Collegare le impostazioni a `LoadOptions` affinché vengano rispettate durante il caricamento di un documento.  
- Eseguire un documento di test che deliberatamente manca di caratteri e leggere l'output della console.  
- Suggerimenti per il logging, la disabilitazione della sostituzione automatica e la gestione di casi particolari come più caratteri mancanti.  

Non è necessaria alcuna documentazione esterna—tutto ciò di cui hai bisogno è qui.

## Prerequisiti

- .NET 6+ (o .NET Framework 4.6.2+).  
- Aspose.Words per .NET 23.9 o successivo (l'API che usiamo è stabile nelle versioni recenti).  
- Un semplice file `.docx` che faccia riferimento a un carattere che sai non sia installato (ad es., *Comic Sans MS* su un container Linux).  

Tutto qui—nessun pacchetto NuGet aggiuntivo oltre ad Aspose.Words.

## Perché è importante gestire i caratteri mancanti

Quando un documento fa riferimento a un carattere che il runtime non riesce a trovare, Aspose.Words sostituisce automaticamente il più vicino disponibile. Tale sostituzione è spesso accettabile, ma a volte è necessario **registrare** quali caratteri erano mancanti (per conformità) o **impedire** del tutto la sostituzione (ad es., per PDF specifici del brand). Intervenendo su `FontSettings.SubstitutionWarning`, ottieni piena visibilità e controllo.

## Passo 1: Creare FontSettings e sottoscrivere l'evento Substitution‑Warning

La prima cosa da fare è istanziare `FontSettings`. Questo oggetto contiene tutta la configurazione relativa ai caratteri per la libreria. La parte cruciale è collegare l'evento `SubstitutionWarning`, che si attiva **ogni volta** che Aspose.Words non riesce a trovare un carattere richiesto.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1 – Initialise FontSettings and listen for missing‑font warnings
FontSettings fontSettings = new FontSettings();

// The lambda receives detailed info about the missing font and the chosen substitute.
fontSettings.SubstitutionWarning += (sender, e) =>
{
    // e.MissingFontName  → the name Aspose.Words tried to load.
    // e.SubstitutedFontName → the font that was actually used instead.
    // e.WarningType → the enum describing why the warning was raised.
    Console.WriteLine($"Missing font: {e.MissingFontName}");
    Console.WriteLine($"Substituted with: {e.SubstitutedFontName}");
    Console.WriteLine($"Reason: {e.WarningType}");
};
```

**Perché è importante:**  
- **Visibilità:** Sai immediatamente quali caratteri sono assenti.  
- **Auditabilità:** La console (o un logger) può essere reindirizzata a un file per report di conformità.  
- **Controllo:** In seguito potrai decidere di sostituire la sostituzione con un carattere personalizzato.

> **Suggerimento professionale:** Se preferisci un framework di logging (Serilog, NLog, ecc.), sostituisci le chiamate `Console.WriteLine` con `logger.Information(...)`.

## Passo 2: Collegare FontSettings a LoadOptions

`LoadOptions` è il veicolo che indica ad Aspose.Words come trattare il file durante la fase di caricamento. Assegnando l'oggetto `FontSettings`, garantisci che il gestore degli avvisi sia attivo *prima* che venga analizzato qualsiasi contenuto.

```csharp
// Step 2 – Bind FontSettings to LoadOptions so the loader knows about our event handler
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

**Perché è importante:**  
- Se carichi un documento senza passare `LoadOptions`, verrà utilizzata la gestione predefinita dei caratteri e perderai gli avvisi.  
- Questo approccio ti permette anche di modificare altri comportamenti di caricamento (ad es., protezione con password) nello stesso oggetto.

## Passo 3: Caricare il documento con le opzioni configurate

Ora leggiamo finalmente il file Word. Il percorso può essere assoluto o relativo; Aspose.Words rispetterà le `LoadOptions` appena preparate.

```csharp
// Step 3 – Load the document while applying our FontSettings
string docPath = @"YOUR_DIRECTORY/MissingFonts.docx";   // <-- adjust to your environment
Document document = new Document(docPath, loadOptions);
```

Se il documento contiene un carattere non installato, l'evento `SubstitutionWarning` si attiva e vedrai un output simile a quello mostrato di seguito.

### Output previsto della console

```
Missing font: Comic Sans MS
Substituted with: Arial
Reason: FontSubstitution
```

Il sostituto esatto può variare in base alla catena di fallback dei caratteri del sistema operativo, ma il **nome del carattere mancante** verrà sempre segnalato.

## Passo 4: Verificare il risultato (rendering opzionale)

Spesso vuoi assicurarti che il documento mantenga un aspetto accettabile dopo la sostituzione. Un modo rapido è salvarlo come PDF e aprire il risultato.

```csharp
// Optional: Save as PDF to visually confirm the substitution
document.Save(@"OUTPUT/Result.pdf", SaveFormat.Pdf);
Console.WriteLine("Document saved as PDF – check the rendering.");
```

Se desideri **impedire** del tutto la sostituzione, imposta `FontSettings.SubstitutionSettings.TableSubstitution = false` prima del caricamento. In tal caso Aspose.Words genererà un'eccezione per i caratteri mancanti, che potrai catturare e gestire.

```csharp
// Disable automatic substitution – will raise an exception on missing fonts
fontSettings.SubstitutionSettings.TableSubstitution = false;
```

## Esempio completo funzionante

Di seguito trovi il programma completo, pronto all'esecuzione. Incollalo in un'applicazione console, regola il percorso del file e premi **F5**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSettingsDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create FontSettings and hook the warning event
            FontSettings fontSettings = new FontSettings();
            fontSettings.SubstitutionWarning += (sender, e) =>
            {
                Console.WriteLine($"Missing font: {e.MissingFontName}");
                Console.WriteLine($"Substituted with: {e.SubstitutedFontName}");
                Console.WriteLine($"Reason: {e.WarningType}");
            };

            // 2️⃣ Attach FontSettings to LoadOptions
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings
                // Uncomment the next line to *disable* substitution and force an exception
                // , FontSettings = { SubstitutionSettings = { TableSubstitution = false } }
            };

            // 3️⃣ Load the document
            string docPath = @"YOUR_DIRECTORY/MissingFonts.docx";
            Document doc = new Document(docPath, loadOptions);

            // 4️⃣ (Optional) Save as PDF to see the visual result
            doc.Save(@"OUTPUT/Result.pdf", SaveFormat.Pdf);
            Console.WriteLine("Processing complete. Check the console for missing‑font warnings.");
        }
    }
}
```

### Cosa aspettarsi

- La console stampa ogni carattere mancante insieme al sostituto scelto.  
- Il PDF risultante (se hai mantenuto il salvataggio opzionale) visualizza il documento usando il carattere di fallback, garantendo l'integrità del layout.

## Domande frequenti e casi particolari

| Domanda | Risposta |
|----------|--------|
| **Cosa succede se mancano più caratteri?** | L'evento si attiva una volta per ogni carattere mancante, quindi otterrai una riga di log separata per ciascuno. |
| **Posso sostituire il fallback con un carattere personalizzato?** | Sì. All'interno del gestore dell'evento puoi chiamare `e.SubstitutedFont = new FontInfo("MyCustomFont")`. |
| **L'avviso viene generato anche per i caratteri incorporati che non si caricano?** | Assolutamente sì—sia che il carattere sia esterno o incorporato, la superficie di avviso è la stessa. |
| **Devo liberare le risorse di `Document`?** | `Document` implementa `IDisposable`. Avvolgi l'uso in un blocco `using` se carichi molti file in un ciclo. |
| **Funziona nei container Linux?** | Finché Aspose.Words riesce a individuare i caratteri di sistema (ad es., tramite `fontconfig`), lo stesso meccanismo di evento funziona. |

## Best practice e consigli avanzati

- **Centralizzare il logging:** Crea un metodo di supporto che scriva sia sulla console sia su un file di log persistente.  
- **Elaborazione batch:** Quando converti decine di documenti, riutilizza un'unica istanza di `FontSettings` per evitare sottoscrizioni ripetitive all'evento.  
- **Performance:** Gli avvisi di sostituzione aggiungono un overhead trascurabile, ma se elabori migliaia di file, considera di disabilitarli dopo aver verificato il set di caratteri.  
- **Sicurezza di versione:** L'API `SubstitutionWarning` è stabile sin da Aspose.Words 16.0, quindi puoi contare su di essa per futuri aggiornamenti.

## Conclusione

Abbiamo illustrato **come utilizzare FontSettings** in Aspose.Words per **gestire elegantemente i caratteri mancanti**. Creando un oggetto `FontSettings`, sottoscrivendo `SubstitutionWarning` e caricando i documenti tramite `LoadOptions`, ottieni piena visibilità sui problemi di caratteri e puoi decidere se registrarli, sostituirli o interrompere l'elaborazione.  

Dall'output semplice della console alla logica di sostituzione personalizzata, il modello scala a pipeline di documenti a grande volume, garantendo che il risultato rimanga coerente e auditabile.

**Passi successivi:**  

- Esplora la **sostituzione personalizzata dei caratteri** assegnando `e.SubstitutedFont` all'interno dell'evento.  
- Combina questo approccio con il **rendering del documento in immagini** per la generazione di miniature.  
- Dai un'occhiata a **Aspose.PDF** se devi incorporare i caratteri sostituiti direttamente nel PDF finale per una portabilità completa.

Buon coding, e che i tuoi documenti non soffrano mai più di un carattere mancante!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}