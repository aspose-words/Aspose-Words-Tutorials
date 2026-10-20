---
category: general
date: 2026-08-07
description: Come raggruppare le forme in Word con Aspose.Words e aggiungere forme
  a un documento Word usando C#. Segui questa guida passo passo per un codice pulito
  e riutilizzabile.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes in word
- add shapes to word document
language: it
lastmod: 2026-08-07
og_description: Come raggruppare le forme in Word usando Aspose.Words per .NET. Questo
  tutorial mostra come aggiungere forme a un documento Word, raggrupparle e salvare
  il file con codice C# chiaro.
og_image_alt: Screenshot of a rectangle and ellipse grouped in a Word document created
  with Aspose.Words
og_title: Come raggruppare le forme in Word – guida rapida C#
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to group shapes in Word with Aspose.Words and add shapes to Word
    document using C#. Follow this step‑by‑step guide for clean, reusable code.
  headline: How to group shapes in Word and add shapes to Word document
  type: TechArticle
- description: How to group shapes in Word with Aspose.Words and add shapes to Word
    document using C#. Follow this step‑by‑step guide for clean, reusable code.
  name: How to group shapes in Word and add shapes to Word document
  steps:
  - name: Create a document and a builder
    text: A `Document` object represents the entire DOCX file. `DocumentBuilder` provides
      a convenient API for editing the document.
  - name: Add the rectangle shape
    text: A rectangle is created by specifying `ShapeType.Rectangle`. Width, height,
      and location are set in points (1 pt ≈ 1/72 in).
  - name: Add the ellipse shape
    text: The ellipse uses `ShapeType.Ellipse`. Its size and position are independent
      of the rectangle, which allows you to control the final layout of the group.
  - name: Group the two shapes
    text: '`GroupShape` acts as a container that treats its children as a single object.
      This is the essential operation for **how to group shapes in Word**.'
  - name: Insert the grouped shape into the document
    text: '`DocumentBuilder.InsertNode` places the `GroupShape` at the current cursor
      location. Because we have not moved the builder, the group appears at the start
      of the first page.'
  - name: Save the document
    text: Finally, write the DOCX file to disk. Use a full path that your application
      can write to.
  - name: Expected output
    text: Open `GroupShape.docx`. You will see a single visual object that contains
      a blue rectangle on the left and a green ellipse on the right. Selecting the
      object in Word highlights both shapes simultaneously—proof that **how to group
      shapes in Word** succeeded.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Come raggruppare le forme in Word e aggiungere forme al documento Word
url: /it/net/programming-with-shapes/how-to-group-shapes-in-word-and-add-shapes-to-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come raggruppare forme in Word e aggiungere forme a un documento Word

Se hai bisogno di **come raggruppare forme in Word**, questa guida ti accompagna attraverso l'intero processo usando Aspose.Words per .NET. Imparerai anche **aggiungere forme a un documento Word** con poche righe di codice C#, così il risultato è pronto per qualsiasi scenario di reporting o templating.

Il tutorial copre tutto ciò di cui hai bisogno: i pacchetti NuGet richiesti, un file sorgente completo e una spiegazione del perché ogni passaggio è importante. Alla fine potrai generare un DOCX che contiene un rettangolo e un'ellisse combinati in un'unica forma di gruppo.

## Prerequisiti

Prima di iniziare, assicurati di avere:

* .NET 6.0 SDK o versioni successive installato  
* Visual Studio 2022 (o qualsiasi IDE che supporti .NET)  
* Pacchetto NuGet Aspose.Words for .NET (`Aspose.Words`) – la versione di prova gratuita funziona per i test, ma una licenza rimuove le filigrane di valutazione  

Questi elementi sono le uniche dipendenze esterne per **add shapes to Word document**.

## Come raggruppare forme in Word

Il cuore della soluzione consiste nel creare forme individuali, posizionarle nella pagina e poi avvolgerle in un `GroupShape`. I passaggi seguenti rispecchiano l'ordine logico del codice.

### Passo 1: Creare un documento e un builder

Un oggetto `Document` rappresenta l'intero file DOCX. `DocumentBuilder` fornisce un'API comoda per modificare il documento.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create an empty Word document
Document doc = new Document();

// DocumentBuilder lets you insert nodes, text, and shapes
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Perché è importante*: Il `Document` è il contenitore di tutti gli elementi Word. Il `DocumentBuilder` tiene traccia della posizione corrente del cursore, necessaria quando in seguito inserisci la forma raggruppata.

### Passo 2: Aggiungere la forma rettangolare

Un rettangolo viene creato specificando `ShapeType.Rectangle`. Larghezza, altezza e posizione sono impostate in punti (1 pt ≈ 1/72 in).

```csharp
Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
rectangleShape.Width = 100;               // 100 pt wide
rectangleShape.Height = 50;               // 50 pt tall
rectangleShape.Left = 0;                  // X‑coordinate
rectangleShape.Top = 0;                   // Y‑coordinate
rectangleShape.StrokeColor = Color.Blue; // Outline color
```

*Perché è importante*: Impostare `StrokeColor` rende la forma visibile quando il documento viene aperto. Puoi anche riempire la forma con `FillColor` se è necessario un interno solido.

### Passo 3: Aggiungere la forma ellisse

L'ellisse utilizza `ShapeType.Ellipse`. La sua dimensione e posizione sono indipendenti dal rettangolo, il che ti permette di controllare il layout finale del gruppo.

```csharp
Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
ellipseShape.Width = 80;
ellipseShape.Height = 80;
ellipseShape.Left = 120;                  // Placed to the right of the rectangle
ellipseShape.Top = 0;
ellipseShape.StrokeColor = Color.Green;
```

*Perché è importante*: Posizionando l'ellisse a `Left = 120`, non si sovrappone al rettangolo, rendendo il gruppo visivamente distinto.

### Passo 4: Raggruppare le due forme

`GroupShape` agisce come un contenitore che tratta i suoi figli come un unico oggetto. Questa è l'operazione essenziale per **how to group shapes in Word**.

```csharp
GroupShape groupShape = new GroupShape(doc);
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);
```

*Perché è importante*: Il raggruppamento ti consente di spostare, ridimensionare o ruotare entrambe le forme insieme. Qualsiasi trasformazione applicata a `groupShape` si propaga ai suoi figli.

### Passo 5: Inserire la forma raggruppata nel documento

`DocumentBuilder.InsertNode` posiziona il `GroupShape` nella posizione corrente del cursore. Poiché non abbiamo spostato il builder, il gruppo appare all'inizio della prima pagina.

```csharp
builder.InsertNode(groupShape);
```

*Perché è importante*: Inserire direttamente il nodo evita la necessità di un paragrafo o di una cella di tabella separata. Il gruppo diventa parte del flusso del documento.

### Passo 6: Salvare il documento

Infine, scrivi il file DOCX su disco. Usa un percorso completo a cui la tua applicazione possa scrivere.

```csharp
doc.Save(@"C:\Temp\GroupShape.docx");
```

*Perché è importante*: `doc.Save` finalizza tutte le modifiche. Il file risultante può essere aperto in Microsoft Word, LibreOffice o qualsiasi visualizzatore che supporti DOCX.

## File sorgente completo

Copia il codice qui sotto in un nuovo progetto console (`dotnet new console`) ed eseguilo. Il programma crea un file chiamato `GroupShape.docx` contenente un rettangolo e un'ellisse raggruppati.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordShapeGrouping
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new document and a builder to edit it
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Define a rectangle shape
            Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
            rectangleShape.Width = 100;
            rectangleShape.Height = 50;
            rectangleShape.Left = 0;
            rectangleShape.Top = 0;
            rectangleShape.StrokeColor = Color.Blue;

            // Step 3: Define an ellipse shape
            Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
            ellipseShape.Width = 80;
            ellipseShape.Height = 80;
            ellipseShape.Left = 120;
            ellipseShape.Top = 0;
            ellipseShape.StrokeColor = Color.Green;

            // Step 4: Group the two shapes together
            GroupShape groupShape = new GroupShape(doc);
            groupShape.AppendChild(rectangleShape);
            groupShape.AppendChild(ellipseShape);

            // Step 5: Insert the grouped shape into the document
            builder.InsertNode(groupShape);

            // Step 6: Save the document
            doc.Save(@"C:\Temp\GroupShape.docx");
        }
    }
}
```

### Output previsto

Apri `GroupShape.docx`. Vedrai un unico oggetto visivo che contiene un rettangolo blu a sinistra e un'ellisse verde a destra. Selezionando l'oggetto in Word evidenzia entrambe le forme simultaneamente—prova che **how to group shapes in Word** è riuscito.

## Domande comuni e casi particolari

* **Posso aggiungere più di due forme?**  
  Sì. Chiama `groupShape.AppendChild` per ogni `Shape` aggiuntiva prima di inserire il gruppo.

* **E se devo ruotare il gruppo?**  
  Imposta `groupShape.RotationAngle = 45;` (angolo in gradi) dopo aver costruito il gruppo.

* **Devo chiamare `doc.UpdatePageLayout()`?**  
  No per questo scenario. Il layout si aggiorna automaticamente quando il documento viene salvato.

* **Come influisce la licenza sul codice?**  
  Con una licenza valida di Aspose.Words (`License license = new License(); license.SetLicense("Aspose.Words.lic");`) il documento generato non contiene filigrane di valutazione.

## Conclusione

Ora sai **how to group shapes in Word** e **add shapes to Word document** usando Aspose.Words per .NET. Il tutorial ha coperto la creazione di un documento, la definizione di forme individuali, il loro raggruppamento, l'inserimento del gruppo e il salvataggio del file.  

Da qui puoi sperimentare con:

* Aggiungere caselle di testo o immagini al gruppo  
* Modificare i colori di riempimento, gli stili di linea o gli effetti di ombra  
* Raggruppare forme all'interno di tabelle o intestazioni  

Queste estensioni ti consentono di creare template Word sofisticati in modo programmatico mantenendo il codice pulito e manutenibile. Buon coding!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo passo per aiutarti a padroneggiare funzionalità aggiuntive dell'API ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Crea una forma di gruppo in un documento Word usando Aspose.Words per .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Inserisci forme nei documenti Word usando Aspose.Words per .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Crea documento Word con Aspose.Words – Guida passo‑passo](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}