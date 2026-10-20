---
category: general
date: 2026-04-24
description: Salva il documento come txt e converti Word in LaTeX con Aspose.Words.
  Scopri come esportare rapidamente le equazioni matematiche di Word in LaTeX.
draft: false
keywords:
- save document as txt
- convert word to latex
- convert word equations to latex
- export word math latex
language: it
og_description: Salva il documento come txt e converti le equazioni di Word in LaTeX
  usando C#. Guida completa passo‑passo con codice.
og_title: Salva documento come TXT – Esporta matematica di Word in LaTeX
tags:
- Aspose.Words
- C#
- LaTeX
title: Salva documento come TXT – Esporta Word Math in LaTeX in C#
url: /it/net/programming-with-officemath/save-document-as-txt-export-word-math-to-latex-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Salva documento come TXT – Esporta Word Math in LaTeX in C#

Hai mai avuto bisogno di **save document as txt** mantenendo intatte le tue eleganti equazioni? Non sei l'unico. La funzione integrata di Word “Save as plain text” elimina Office Math, lasciandoti con un incomprensibile nonsense. E se potessi conservare quelle equazioni, ma in LaTeX pulito?  

In questo tutorial ti guideremo passo passo attraverso le esatte istruzioni per creare testo pronto per **convert Word to LaTeX** usando Aspose.Words per .NET. Alla fine avrai un file `.txt` in cui ogni equazione è rappresentata come markup LaTeX corretto, pronto per essere inserito in un articolo o in un file markdown. Nessun convertitore esterno, nessun copia‑incolla manuale—solo poche righe di C#.

## Cosa imparerai

- Come caricare un file `.docx` con Aspose.Words.
- Configurare `TxtSaveOptions` in modo che Office Math venga esportato come LaTeX.
- Salvare il risultato in un file di testo semplice che puoi aprire con qualsiasi editor.
- Gestione dei casi limite per equazioni inline vs. display, e un rapido suggerimento per l'elaborazione batch di più documenti.

### Prerequisiti

- .NET 6.0 o successivo (il codice funziona anche con .NET Framework 4.6+).
- Pacchetto NuGet Aspose.Words per .NET (`Install-Package Aspose.Words`).
- Un documento Word che contenga almeno un'equazione (oggetto Office Math).

---

## Passo 1: Installa Aspose.Words e configura il progetto

Per prima cosa, aggiungi la libreria al tuo progetto. Apri un terminale nella cartella della soluzione e esegui:

```bash
dotnet add package Aspose.Words
```

> **Suggerimento:** Se stai usando Visual Studio, l'interfaccia utente del NuGet Package Manager funziona altrettanto bene—cerca “Aspose.Words” e fai clic su Install.

Ora crea una nuova app console (o inserisci il codice in una esistente). Le direttive `using` di cui avrai bisogno sono:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

Queste importano la classe `Document` e il tipo `TxtSaveOptions` nello spazio dei nomi.

## Passo 2: Carica il documento sorgente

Dobbiamo indicare ad Aspose.Words il file Word che contiene le equazioni. Sostituisci `YOUR_DIRECTORY/input.docx` con il percorso reale sul tuo computer.

```csharp
// Load the source .docx file
Document doc = new Document(@"C:\MyDocs\input.docx");
```

> **Perché è importante:** Caricare il documento consente ad Aspose.Words di accedere completamente agli oggetti Office Math interni, che altrimenti sono invisibili a un semplice esportatore di testo.

## Passo 3: Configura TxtSaveOptions per l'esportazione LaTeX

La magia avviene nell'oggetto `TxtSaveOptions`. Impostando `OfficeMathExportMode` su `LaTeX`, ogni equazione viene trasformata nella sua equivalente LaTeX.

```csharp
// Configure save options to export Office Math as LaTeX
TxtSaveOptions txtOptions = new TxtSaveOptions
{
    // Export all Office Math objects as LaTeX code
    OfficeMathExportMode = OfficeMathExportMode.LaTeX,

    // Optional: keep line breaks similar to the original layout
    PreserveTableLayout = true
};
```

> **E se ti servisse MathML?** Cambia `OfficeMathExportMode` in `MathML`. La stessa API supporta diversi formati di output.

## Passo 4: Salva il documento come testo semplice

Ora scriviamo il file. Il risultato `Math.txt` conterrà testo ordinario più frammenti LaTeX per ogni equazione.

```csharp
// Save the document as a .txt file with LaTeX equations
doc.Save(@"C:\MyDocs\Math.txt", txtOptions);
Console.WriteLine("Document saved as txt with LaTeX equations.");
```

Eseguendo il programma si ottiene un file che appare più o meno così:

```
This is a simple paragraph.

Here is an inline equation: $E = mc^2$

And a displayed equation:
\[
\int_{0}^{\infty} e^{-x} \, dx = 1
\]
```

Nota come l'equazione inline utilizzi `$…$` mentre l'equazione display è avvolta in `\[` e `\]`. Questa è la convenzione standard di LaTeX, e Aspose.Words la applica automaticamente.

## Passo 5: Verifica l'output (opzionale)

Se vuoi ricontrollare che il LaTeX sia valido, puoi passare il `.txt` a un compilatore LaTeX come `pdflatex` o a un render online come Overleaf. Il testo dovrebbe compilare senza errori, e le equazioni appariranno esattamente come in Word.

```bash
pdflatex Math.txt
```

Se ottieni “Undefined control sequence”, assicurati che i pacchetti LaTeX necessari (ad es., `amsmath`) siano inclusi nel preambolo quando inserisci il testo in un documento LaTeX più grande.

## Gestione delle variazioni comuni

### Conversione di più file in una cartella

```csharp
string[] files = Directory.GetFiles(@"C:\MyDocs\", "*.docx");
foreach (var file in files)
{
    Document d = new Document(file);
    d.Save(Path.ChangeExtension(file, ".txt"), txtOptions);
}
Console.WriteLine("Batch conversion complete.");
```

### Gestione di equazioni Inline vs. Display

Aspose.Words rileva automaticamente il tipo di equazione in base al layout in Word. Se devi forzare uno stile particolare, puoi post‑processare l'output:

```csharp
string txt = File.ReadAllText(@"C:\MyDocs\Math.txt");
txt = txt.Replace("$", "\\(").Replace("$", "\\)"); // forces inline math delimiters
File.WriteAllText(@"C:\MyDocs\Math_fixed.txt", txt);
```

### Esportazione in altri formati

Se LaTeX non è il tuo obiettivo, basta cambiare la modalità di esportazione:

```csharp
txtOptions.OfficeMathExportMode = OfficeMathExportMode.MathML; // for MathML
```

Oppure usa `HtmlSaveOptions` se preferisci MathML incorporato in HTML.

---

## Esempio completo funzionante

Di seguito trovi il programma completo, pronto per l'esecuzione. Copialo e incollalo in `Program.cs` di un progetto console .NET.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

namespace WordToLatexTxt
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the source document
            Document doc = new Document(@"C:\MyDocs\input.docx");

            // 2️⃣ Set up save options to export Office Math as LaTeX
            TxtSaveOptions saveOptions = new TxtSaveOptions
            {
                OfficeMathExportMode = OfficeMathExportMode.LaTeX,
                PreserveTableLayout = true
            };

            // 3️⃣ Save as plain‑text with LaTeX equations
            string outputPath = @"C:\MyDocs\Math.txt";
            doc.Save(outputPath, saveOptions);

            Console.WriteLine($"✅ Saved document as txt at: {outputPath}");
            Console.WriteLine("Open the file to see LaTeX‑formatted equations.");
        }
    }
}
```

Esegui il programma (`dotnet run`), apri `Math.txt` e vedrai il contenuto Word con le equazioni LaTeX intatte.

---

## Domande frequenti

**D: Funziona con i vecchi file .doc?**  
R: Sì—Aspose.Words può aprire file `.doc` legacy, ma le equazioni complesse potrebbero essere salvate come immagini. In tal caso l'esportatore usa un commento segnaposto.

**D: E se un'equazione contiene simboli personalizzati?**  
R: Aspose.Words mappa la maggior parte dei simboli Office Math a comandi LaTeX standard. Per simboli davvero personalizzati potresti dover modificare manualmente il LaTeX generato.

**D: L'output è codificato in UTF‑8?**  
R: Per impostazione predefinita, `TxtSaveOptions` scrive in UTF‑8, che è sicuro per la maggior parte delle lingue e dei simboli.

---

## Conclusione

Ora sai come **save document as txt** preservando ogni equazione come markup LaTeX pulito. Questo approccio ti consente di **convert Word to LaTeX** senza strumenti di terze parti, e scala da un singolo file a intere cartelle. Successivamente, potresti esplorare **convert word equations to LaTeX** per l'elaborazione batch, o approfondire **export word math latex** per pipeline HTML o Markdown.

Sentiti libero di sperimentare—sostituisci `OfficeMathExportMode` con MathML, modifica la gestione delle interruzioni di riga, o integra questo snippet in un flusso di lavoro più ampio di generazione documenti. Buona programmazione, e che le tue equazioni vengano sempre renderizzate perfettamente!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}