---
category: general
date: 2026-09-14
description: Scopri come nascondere una forma in Word usando C# — includendo il codice
  per creare un documento Word, inserire una forma rettangolare in Word e nascondere
  la forma in Word programmaticamente.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to hide shape
- hide shape in word
- create word document code
- insert rectangle shape word
language: it
lastmod: 2026-09-14
og_description: Come nascondere una forma in Word usando C# — guida passo‑passo che
  mostra anche come creare il codice di un documento Word e inserire una forma rettangolare
  in Word.
og_image_alt: Word document preview with a visible rectangle shape and a hidden ellipse
  shape
og_title: Come nascondere una forma in un documento Word con codice C#
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Learn how to hide shape in Word using C#—including create word document
    code, insert rectangle shape word, and hide shape in word programmatically.
  headline: How to hide shape in a Word document with C# code
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Come nascondere una forma in un documento Word con codice C#
url: /it/net/programming-with-shapes/how-to-hide-shape-in-a-word-document-with-c-code/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come nascondere una forma in un documento Word con codice C#

Se hai bisogno di **how to hide shape** in un file Word, questo tutorial mostra la soluzione completa. Vedrai come creare un documento Word, inserire una forma rettangolare, aggiungere un'ellisse e nascondere quest'ellisse in modo che solo il rettangolo appaia quando il file viene aperto.

La guida copre tutto ciò di cui hai bisogno—nessun riferimento esterno, solo il codice e le spiegazioni. Alla fine sarai in grado di incorporare grafiche nascoste in qualsiasi documento Word generato programmaticamente.

## Prerequisiti

- .NET 6.0 o versioni successive (il codice funziona anche con .NET Framework 4.7+)
- Aspose.Words per .NET (versione di prova gratuita o licenziata)  
  Installalo tramite NuGet: `dotnet add package Aspose.Words`
- Familiarità di base con C# e Visual Studio o qualsiasi IDE tu preferisca

## Passo 1: Configurare il progetto e importare i namespace

Avvia una nuova applicazione console e aggiungi le istruzioni `using` richieste. Queste importazioni ti danno accesso a `Document`, `DocumentBuilder` e alle classi di disegno necessarie per manipolare le forme.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The rest of the code follows in the next steps
        }
    }
}
```

**Why this matters** – Importare i namespace corretti previene errori di compilazione e rende disponibile l'API per la creazione di forme e il controllo della visibilità.

## Passo 2: Creare un nuovo documento Word e un builder

Un `Document` rappresenta il file, mentre un `DocumentBuilder` fornisce un'API fluida per aggiungere contenuti. Questo è il primo punto in cui applichi la logica **how to hide shape**: è necessario un contesto documento prima che possa esistere una forma.

```csharp
// Step 2: Create a new blank document and a builder to edit it
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);
```

**Explanation** – L'oggetto `Document` inizia vuoto. Il `DocumentBuilder` è posizionato all'inizio del primo paragrafo, pronto per inserire forme o testo.

## Passo 3: Inserire una forma rettangolare visibile

Il rettangolo sarà la forma che rimane visibile quando il documento viene aperto. Puoi controllarne dimensioni, posizione e formattazione direttamente tramite l'oggetto forma.

```csharp
// Step 3: Insert a visible rectangle shape and position it
Shape visibleRectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
visibleRectangle.Left = 50;                 // 50 points from the left margin
visibleRectangle.Top = 100;                 // 100 points from the top of the page
visibleRectangle.FillColor = System.Drawing.Color.LightBlue;
visibleRectangle.LineColor = System.Drawing.Color.DarkBlue;
```

**Why this step** – Aggiungere un rettangolo dimostra il requisito **insert rectangle shape word**. Impostare `FillColor` e `LineColor` rende la forma facile da individuare nel documento finale.

## Passo 4: Inserire una forma ellittica e nasconderla

Ora aggiungi la forma che intendi celare. La proprietà `Hidden` indica a Word di non renderizzare la forma nell'interfaccia, sebbene rimanga parte della struttura del documento.

```csharp
// Step 4: Insert an ellipse shape, position it, and hide it from view
Shape hiddenEllipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
hiddenEllipse.Left = 200;      // Position away from the rectangle
hiddenEllipse.Top = 100;
hiddenEllipse.Hidden = true;   // This flag implements how to hide shape
```

**Explanation** – Impostare `Hidden = true` è il fulcro di **hide shape in word**. Word rispetta questo flag durante la visualizzazione e la stampa normali, ma la forma può comunque essere accessibile programmaticamente se necessario.

## Passo 5: Salvare il documento

Infine, scrivi il documento su disco. Scegli una cartella in cui hai i permessi di scrittura e assegna al file un nome chiaro che rifletta lo scopo del tutorial.

```csharp
// Step 5: Save the document with both shapes
string outputPath = @"C:\Temp\ShapeVisibility.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

**Result** – Aprendo `ShapeVisibility.docx` in Microsoft Word viene mostrato solo il rettangolo azzurro chiaro. L'ellisse nascosta non appare, confermando che hai padroneggiato con successo **how to hide shape** in un file Word.

## Esempio completo funzionante

Unendo tutti gli snippet ottieni un unico programma eseguibile:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a new document and builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert a visible rectangle
            Shape visibleRectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            visibleRectangle.Left = 50;
            visibleRectangle.Top = 100;
            visibleRectangle.FillColor = System.Drawing.Color.LightBlue;
            visibleRectangle.LineColor = System.Drawing.Color.DarkBlue;

            // Insert a hidden ellipse
            Shape hiddenEllipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
            hiddenEllipse.Left = 200;
            hiddenEllipse.Top = 100;
            hiddenEllipse.Hidden = true; // hides the shape

            // Save the document
            string outputPath = @"C:\Temp\ShapeVisibility.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Output previsto

- **Visual**: Quando apri `ShapeVisibility.docx`, vedi un rettangolo azzurro chiaro posizionato vicino al margine sinistro. Nessuna ellisse è visibile.
- **Programmatic**: L'ellisse nascosta rimane nell'XML del documento (`<w:drawing>` element) con l'attributo `w:hidden` impostato, cosa che puoi verificare aprendo il file come zip e ispezionando `document.xml`.

## Domande comuni e casi particolari

| Domanda | Risposta |
|----------|--------|
| *Posso nascondere più forme?* | Sì. Imposta `Hidden = true` su ogni forma che desideri nascondere. |
| *Le forme nascoste verranno stampate?* | Per impostazione predefinita Word non stampa gli oggetti nascosti. Se hai bisogno di stamparli, rimuovi il flag `Hidden` prima della stampa. |
| *La proprietà hidden è supportata nelle versioni più vecchie di Word?* | L'attributo `Hidden` fa parte dello standard Office Open XML e funziona in Word 2007 e versioni successive. |
| *E se devo alternare la visibilità a runtime?* | Recupera la forma tramite `document.GetChildNodes(NodeType.Shape, true)` e inverte la proprietà `Hidden` in base alla tua logica. |

## Consigli professionali

- **Performance**: Se generi molti documenti, riutilizza un'unica istanza di `DocumentBuilder` invece di crearne una nuova per ogni file.
- **Version control**: Conserva i file `.docx` generati in una cartella sotto controllo di versione; le forme nascoste possono fungere da marcatori di metadati per l'elaborazione a valle.
- **Testing**: Automatizza un rapido test visivo convertendo il DOCX in PDF con Aspose.Words (`document.Save("out.pdf")`). Anche il PDF nasconderà l'ellisse, confermando che il flag hidden si propaga attraverso le conversioni di formato.

## Conclusione

Ora sai **how to hide shape** in un documento Word usando C#. Il tutorial ha mostrato come creare un documento, **insert rectangle shape word**, aggiungere un'ellisse e applicare il flag `Hidden` per ottenere il comportamento **hide shape in word**. Con il codice completo e pronto all'uso puoi integrare grafiche nascoste in qualsiasi flusso di lavoro di reporting o templating automatizzato.

### Prossimi passi

- Esplora altre proprietà delle forme come rotazione, ombra e avvolgimento del testo.  
- Combina forme nascoste con proprietà personalizzate del documento per incorporare dati leggibili da macchine.  
- Approfondisci i pattern **create word document code** per tabelle, grafici e controlli di contenuto per ampliare il tuo toolkit di automazione.

Sentiti libero di sperimentare con diversi tipi di forma e impostazioni di visibilità—il tuo prossimo progetto di automazione Word è a pochi righe di codice di distanza!

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Crea forma rettangolare in Word usando C# – Guida passo‑passo](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Crea documento Word vuoto con forma rettangolare ombreggiata – Guida passo‑passo](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Tutorial Ombra Forma Aspose.Words – Aggiungi un'ombra a una forma Word in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}