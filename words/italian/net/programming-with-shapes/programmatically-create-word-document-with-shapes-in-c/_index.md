---
category: general
date: 2026-11-22
description: Creare programmaticamente un documento Word in C# e inserire una forma
  rettangolare, inserire più forme e scrivere le forme in Word utilizzando Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically create word document
- insert rectangle shape
- insert multiple shapes
- write shapes to word
language: it
lastmod: 2026-11-22
og_description: Crea programmaticamente un documento Word in C# inserendo una forma
  rettangolare, aggiungendo più forme e scrivendo le forme in Word con Aspose.Words.
og_image_alt: Screenshot of a Word document showing a rectangle and an ellipse grouped
  together
og_title: Creare programmaticamente un documento Word con forme in C#
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Programmatically create Word document in C# and insert rectangle shape,
    insert multiple shapes, and write shapes to Word using Aspose.Words.
  headline: Programmatically create Word document with shapes in C#
  type: TechArticle
- description: Programmatically create Word document in C# and insert rectangle shape,
    insert multiple shapes, and write shapes to Word using Aspose.Words.
  name: Programmatically create Word document with shapes in C#
  steps:
  - name: '**Initialize** a new `Document` and a `DocumentBuilder`.'
    text: '**Initialize** a new `Document` and a `DocumentBuilder`.'
  - name: '**Insert multiple shapes** (a rectangle and an ellipse) and place them
      inside a `GroupShape`.'
    text: '**Insert multiple shapes** (a rectangle and an ellipse) and place them
      inside a `GroupShape`.'
  - name: '**Write shapes to Word** by saving the `Document` to a `.docx` file.'
    text: '**Write shapes to Word** by saving the `Document` to a `.docx` file.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Creare programmaticamente un documento Word con forme in C#
url: /it/net/programming-with-shapes/programmatically-create-word-document-with-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Creare programmaticamente un documento Word con forme in C#

Se devi **creare programmaticamente un documento Word** che contenga grafiche personalizzate, questa guida ti mostra come farlo con Aspose.Words per .NET. Imparerai a inserire una forma rettangolare, aggiungere altre forme, raggrupparle e, infine, scrivere le forme in Word—tutto in poche righe di C#.

Creare un file Word con grafiche non richiede più modifiche manuali o script macro. Alla fine di questo tutorial avrai a disposizione un metodo riutilizzabile che produce un file `.docx` contenente un rettangolo e un'ellisse raggruppati, pronti per l'elaborazione successiva o per la generazione di report.

## Di cosa avrai bisogno

- .NET 6.0 o versioni successive (il codice funziona anche con .NET Framework 4.6+)
- Aspose.Words per .NET (pacchetto NuGet `Aspose.Words`)
- Un IDE come Visual Studio 2022 (qualsiasi editor in grado di compilare C# va bene)

> **Suggerimento:** Installa il pacchetto con il comando CLI `dotnet add package Aspose.Words` prima di iniziare a scrivere codice.

## Creare programmaticamente un documento Word – panoramica

Il flusso complessivo è composto da tre fasi logiche:

1. **Inizializzare** un nuovo `Document` e un `DocumentBuilder`.  
2. **Inserire più forme** (un rettangolo e un'ellisse) e posizionarle all'interno di un `GroupShape`.  
3. **Scrivere le forme in Word** salvando il `Document` in un file `.docx`.

Ogni fase è racchiusa in un passaggio dedicato qui sotto, così potrai copiare‑incollare il codice direttamente nel tuo progetto.

![Creare programmaticamente un documento Word con forme raggruppate](grouped-shapes.png){: .align-center alt="Creare programmaticamente un documento Word con forme raggruppate"}

## Passo 1: Inizializzare il documento e il builder

La classe `Document` rappresenta l'intero file Word, mentre `DocumentBuilder` fornisce un'API fluida per aggiungere contenuti.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document document = new Document();

// Initialize a DocumentBuilder for the document
DocumentBuilder builder = new DocumentBuilder(document);
```

*Perché è importante:* Creare prima il `Document` ti offre una tela pulita. Il `DocumentBuilder` tiene traccia del punto di inserimento corrente, fondamentale quando in seguito alleghi le forme a una gerarchia di paragrafi.

## Passo 2: Inserire un contenitore di forme raggruppate

Un `GroupShape` ti permette di trattare diverse forme individuali come un'unica unità. Questo è utile quando vuoi spostarle o ridimensionarle insieme.

```csharp
// Insert a group shape container at the current cursor position
GroupShape groupShape = builder.InsertGroupShape();
```

*Spiegazione:* `InsertGroupShape` inserisce un contenitore vuoto e lo rende automaticamente la forma corrente. Tutte le successive inserzioni di forme verranno aggiunte a questo contenitore finché non chiudi il gruppo.

## Inserire forma rettangolare

Ora aggiungiamo la prima grafica—un rettangolo. Questo soddisfa il requisito **insert rectangle shape**.

```csharp
// Insert a rectangle shape (width: 100 pt, height: 50 pt)
builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

Il rettangolo eredita il contesto di formattazione del gruppo, quindi appare all'interno del `GroupShape`. Puoi anche impostare colore della linea, riempimento o testo in seguito, se necessario.

## Inserire più forme

Per dimostrare la capacità **insert multiple shapes**, aggiungiamo un'ellisse subito dopo il rettangolo. Puoi continuare ad aggiungere quante forme desideri (ad esempio triangoli, stelle) prima di chiudere il gruppo.

```csharp
// Insert an ellipse shape (width: 80 pt, height: 40 pt)
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

A questo punto il gruppo contiene due forme distinte: un rettangolo e un'ellisse. Poiché condividono lo stesso genitore, puoi spostarle come un'unica unità.

## Passo 3: Collegare il gruppo di forme alla gerarchia dei paragrafi

I documenti Word memorizzano il contenuto in un albero di paragrafi. Per rendere il gruppo visibile nel file finale, dobbiamo collegarlo al paragrafo corrente.

```csharp
// Append the group shape to the current paragraph so it becomes part of the document flow
groupShape.AppendChild(builder.CurrentParagraph);
```

*Perché questo passaggio è necessario:* Senza aggiungere il gruppo a un paragrafo, le forme esistono solo in memoria e vengono omesse quando il documento viene salvato.

## Passo 4: Salvare il documento – scrivere le forme in Word

Infine, persisti il `Document` in memoria su disco. Questo realizza l'obiettivo **write shapes to word**.

```csharp
// Define the output path (adjust the folder as needed)
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");

// Save the document in DOCX format
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Quando apri `GroupShape.docx` in Microsoft Word, vedrai un rettangolo e un'ellisse raggruppati insieme, esattamente come inserito dal codice.

### Output previsto

- Un file chiamato **GroupShape.docx** situato nella cartella di output del progetto.
- All'interno del file Word: un singolo paragrafo contenente un rettangolo raggruppato (100 pt × 50 pt) e un'ellisse (80 pt × 40 pt). Selezionando una delle forme, si seleziona l'intero gruppo.

## Gestire casi limite comuni

| Situazione | Raccomandazione |
|-----------|----------------|
| **DPI o dimensione pagina diversi** | Imposta esplicitamente `builder.PageSetup.PaperSize` prima di inserire le forme per evitare ridimensionamenti inattesi. |
| **Necessità di posizionare le forme con precisione** | Usa `builder.MoveTo` per spostare il punto di inserimento, quindi imposta le proprietà `groupShape.Left` e `groupShape.Top` (i valori sono in punti). |

## Cosa dovresti imparare dopo?


I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare ulteriori funzionalità dell'API e a esplorare approcci alternativi nei tuoi progetti.

- [Create Word Document – Insert Rectangle Shape & Shadow in C#](/words/english/net/programming-with-shapes/create-word-document-insert-rectangle-shape-shadow-in-c/)
- [Create word document programmatically and group shapes in C#](/words/english/net/programming-with-shapes/create-word-document-programmatically-and-group-shapes-in-c/)
- [Programmatically create a Word document with a group shape](/words/english/net/programming-with-shapes/programmatically-create-a-word-document-with-a-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}