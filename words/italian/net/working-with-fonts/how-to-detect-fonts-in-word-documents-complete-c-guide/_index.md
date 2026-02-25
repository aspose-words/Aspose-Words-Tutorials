---
category: general
date: 2026-02-24
description: Come rilevare i font in un documento Word usando Aspose.Words. Scopri
  come impostare il callback e caricare il documento Word con un esempio di codice
  completo.
draft: false
keywords:
- how to detect fonts
- how to set callback
- load word document
- font substitution warning
- Aspose.Words warning callback
language: it
og_description: Come rilevare i font in un documento Word utilizzando un callback
  di avviso. Questa guida mostra come impostare il callback e caricare un documento
  Word con Aspose.Words.
og_title: Come rilevare i font nei documenti Word – Tutorial C# passo passo
tags:
- C#
- Aspose.Words
- Document Processing
title: Come rilevare i font nei documenti Word – Guida completa C#
url: /it/net/working-with-fonts/how-to-detect-fonts-in-word-documents-complete-c-guide/
---

is substituted. The alt text contains the primary keyword for SEO.*" Translate.

Then "Conclusion" heading.

Paragraph.

Translate.

Then final shortcodes.

Make sure to keep markdown formatting.

Let's produce final content.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come rilevare i font nei documenti Word – Guida completa C#

Ti sei mai chiesto **come rilevare i font** mancanti quando carichi un file Word? Forse ti è capitato di aprire un documento che sembra a posto nell'editor, ma il PDF che generi sostituisce alcuni caratteri dietro le quinte. È un sintomo classico di sostituzione dei font, e individuarlo subito può salvarti da brutte sorprese di layout.

In questo tutorial percorreremo una soluzione pratica: usare **Aspose.Words** per caricare un `.docx`, collegare un callback di avviso e **come impostare il callback** che segnala ogni sostituzione di font. Alla fine non solo saprai **come rilevare i font** programmaticamente, ma comprenderai anche **come impostare il callback** correttamente e **caricare il documento Word** in modo sicuro—tutto in un unico esempio C# eseguibile.

> **Cosa otterrai**
> * Un esempio di codice completo, pronto da copiare e incollare  
> * Spiegazione passo‑passo di ogni riga  
> * Suggerimenti per gestire casi limite come più font mancanti o cartelle di font personalizzate  
> * Output console previsto così potrai verificare che tutto funzioni

---

## Prerequisiti

- .NET 6.0 o successivo (il codice funziona anche con .NET Core)  
- Pacchetto NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)  
- Un file Word che faccia riferimento intenzionalmente a un font non installato (ad es., `MissingFont.docx`)  
- Visual Studio, Rider o qualsiasi editor tu preferisca

Nessun'altra libreria è necessaria; tutto il resto fa parte del runtime standard di .NET.

---

## Come rilevare i font in un documento Word

### Passo 1: Creare le Load Options e collegare un Warning Callback

La prima cosa che facciamo è dire ad Aspose.Words che vogliamo essere avvisati di eventuali problemi durante il caricamento del file. È qui che entra in gioco **come impostare il callback**.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

/// <summary>
/// Collects font‑related warnings during document loading.
/// </summary>
public class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            var substitution = (FontSubstitutionWarning)info;
            Console.WriteLine(
                $"Font '{substitution.MissingFontName}' was substituted with " +
                $"'{substitution.SubstitutedFontName}' at {substitution.Location}");
        }
    }
}
```

**Perché è importante:**  
`LoadOptions` è il punto d'accesso per personalizzare il processo di caricamento. Assegnando un'istanza di `FontWarningCollector` a `WarningCallback`, Aspose.Words invocherà il nostro metodo `Warning` ogni volta che sostituisce un font mancante con un fallback. Questo è il cuore di **come rilevare i font** che non sono presenti sulla macchina.

---

### Passo 2: Preparare l'istanza di LoadOptions

Ora istanziamo `LoadOptions` e colleghiamo il nostro callback.

```csharp
// Step 2: Initialize LoadOptions and attach the warning collector.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCollector()
};
```

**Consiglio professionale:** Se devi controllare *dove* Aspose cerca i font di sostituzione, puoi anche impostare `loadOptions.FontSettings` qui. È utile quando hai una cartella di font privata sul server.

---

### Passo 3: Caricare il documento Word

Con le opzioni pronte, finalmente **carichiamo il documento Word**. È il momento in cui Aspose analizza il DOCX e, se ci sono font mancanti, il nostro callback si attiva.

```csharp
// Step 3: Load the document that may contain missing fonts.
string filePath = @"YOUR_DIRECTORY\MissingFont.docx";
Document doc = new Document(filePath, loadOptions);
```

**Cosa succede dietro le quinte?**  
Aspose.Words legge le parti XML del DOCX, risolve ogni riferimento `<w:font>` e controlla la collezione di font del sistema. Ogni volta che un riferimento non può essere soddisfatto, sostituisce il primo font fallback corrispondente e genera un avviso `FontSubstitution`.

---

### Passo 4: Verificare l'output

Esegui il programma e osserva la console. Per ogni font mancante vedrai una riga del tipo:

```
Font 'Comic Sans MS' was substituted with 'Arial' at Paragraph 3, Run 2
```

Se il documento non contiene font mancanti, la console rimane silenziosa—significando che **come rilevare i font** non ha trovato alcun caso.

---

### Passo 5: Esempio completo funzionante (Console App)

Di seguito trovi un `Program.cs` autonomo che puoi inserire in un nuovo progetto console. Include tutti i pezzi discussi più un piccolo helper per tenere aperta la finestra della console durante il debug.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontDetectionDemo
{
    // ----- Step 1: Warning callback implementation -----
    public class FontWarningCollector : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                var substitution = (FontSubstitutionWarning)info;
                Console.WriteLine(
                    $"Font '{substitution.MissingFontName}' was substituted with " +
                    $"'{substitution.SubstitutedFontName}' at {substitution.Location}");
            }
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // ----- Step 2: Configure LoadOptions -----
            var loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningCollector()
            };

            // ----- Step 3: Load the Word file -----
            string filePath = @"YOUR_DIRECTORY\MissingFont.docx";
            Document doc = new Document(filePath, loadOptions);

            // Optional: Do something with the document (e.g., save as PDF)
            // doc.Save("output.pdf");

            // Keep console open for debugging
            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

**Output console previsto** (esempio):

```
Font 'Papyrus' was substituted with 'Times New Roman' at Paragraph 1, Run 5
Font 'Brush Script MT' was substituted with 'Calibri' at Paragraph 4, Run 1

Press any key to exit...
```

Se sostituisci `MissingFont.docx` con un file che utilizza solo font installati, vedrai solo la riga “Press any key…”—confermandosi che la logica di rilevamento funziona come previsto.

---

## Domande frequenti e casi limite

### E se devo catturare *tutti* gli avvisi, non solo le sostituzioni di font?

Basta rimuovere il controllo `if (info.Type == WarningType.FontSubstitution)`. L'oggetto `WarningInfo` contiene un enum `Type` su cui puoi fare switch per altri scenari (ad es., `DocumentStructure`, `ImageLoading`).

### Posso registrare gli avvisi su un file invece che sulla console?

Assolutamente. Sostituisci `Console.WriteLine` con una chiamata a qualsiasi framework di logging (`Serilog`, `NLog`, ecc.). Il callback viene eseguito sullo stesso thread che carica il documento, quindi assicurati che il logger sia thread‑safe.

### Come si comporta questo in un'applicazione web?

In ASP.NET Core tipicamente inietti un'implementazione singleton di `IWarningCallback` e la passi tramite `LoadOptions`. Ricorda di evitare di scrivere direttamente sullo stream di risposta—logga su un database o su una collezione in‑memory che poi potrai esporre tramite un endpoint API.

### E i font personalizzati memorizzati in una cartella non di sistema?

```csharp
var fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
loadOptions.FontSettings = fontSettings;
```

Ora Aspose.Words cercherà in `C:\MyCustomFonts` prima di ricorrere ai font del sistema operativo, riducendo il numero di avvisi di sostituzione che vedi.

---

## Riepilogo visivo

![Rilevamento avviso di sostituzione dei font in Aspose.Words](/images/font-warning-callback.png "Come rilevare i font usando un callback di avviso")

*Lo screenshot mostra l'output della console quando un font mancante viene sostituito. Il testo alternativo contiene la parola chiave principale per la SEO.*

---

## Conclusione

Ora disponi di un modello solido, pronto per la produzione, per **come rilevare i font** in qualsiasi file Word caricato con Aspose.Words. **Impostando il callback** ottieni informazioni in tempo reale sui font mancanti o sostituiti, e hai imparato il modo corretto per **caricare il documento Word** mantenendo il codice pulito e manutenibile.

Quali sono i prossimi passi? Prova a estendere il callback per raccogliere gli avvisi in una lista, quindi visualizzarli in una UI o in un report automatico. Potresti anche esplorare `FontSettings.SubstitutionSettings` per controllare *quali* font vengono scelti come fallback.

Sentiti libero di sperimentare—cambia il documento, aggiungi altri font mancanti, o integra la logica in una pipeline di elaborazione documenti più ampia. Se incontri difficoltà, lascia un commento qui sotto o contattami su GitHub.

Buona programmazione, e che i tuoi documenti vengano sempre renderizzati con i font che ti aspetti!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}