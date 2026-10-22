---
category: general
date: 2026-08-10
description: Crea un documento Word programmaticamente usando Aspose.Words, impara
  come raggruppare più forme in Word, aggiungi un rettangolo a Word e crea una forma
  di gruppo in C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- group multiple shapes word
- add rectangle to word
- how to create group shape
language: it
lastmod: 2026-08-10
og_description: Creare un documento Word programmaticamente con Aspose.Words. Questa
  guida ti mostra come raggruppare più forme in Word, aggiungere un rettangolo in
  Word e incorporare un controllo di contenuto di testo semplice, il tutto in C#.
og_image_alt: Screenshot of a Word file showing a grouped rectangle and ellipse with
  a plain‑text content control
og_title: Crea documento Word programmaticamente – raggruppa forme in C#
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create word document programmatically using Aspose.Words, learn how
    to group multiple shapes word, add rectangle to word, and create a group shape
    in C#.
  headline: Create word document programmatically and group shapes in C#
  type: TechArticle
- description: Create word document programmatically using Aspose.Words, learn how
    to group multiple shapes word, add rectangle to word, and create a group shape
    in C#.
  name: Create word document programmatically and group shapes in C#
  steps:
  - name: – Initialize the document and builder
    text: The `Document` object represents the entire DOCX file, while `DocumentBuilder`
      provides a convenient API to add content. Initializing them is the first requirement
      whenever you **create word document programmatically**.
  - name: – Create a group shape container
    text: A `Shape` with `ShapeType.Group` acts as a canvas that can hold other shapes.
      Setting `Width` and `Height` defines the bounding box for the group. This is
      the core of **how to create group shape** in Aspose.Words.
  - name: – Add a rectangle to word
    text: A rectangle is created with `ShapeType.Rectangle`. Its `Left` and `Top`
      properties position it relative to the group’s origin. This step demonstrates
      **add rectangle to word** and shows how you can control exact placement.
  - name: – Add an ellipse (circle) to the group
    text: An ellipse is added the same way as the rectangle, but with `ShapeType.Ellipse`.
      The `Left = 210` moves it to the right of the rectangle, creating a visually
      distinct pair of shapes inside the same group.
  - name: – Insert the completed group shape into the document
    text: '`builder.InsertNode(groupShape)` places the whole group at the current
      cursor location. Because the group already contains its children, you do not
      need additional insert calls for the rectangle or ellipse.'
  - name: – Create a plain‑text StructuredDocumentTag (SDT)
    text: A StructuredDocumentTag is a content control that end users can fill in
      when the document is opened in Word. Setting `Title = "CustomerName"` gives
      the control a meaningful identifier, which is useful for later data extraction.
  - name: – Save the document
    text: '`doc.Save("GroupAndSDT.docx")` writes the file to disk. The resulting DOCX
      contains the grouped shapes and the SDT. Opening the file in Microsoft Word
      will show a rectangle next to a circle, both selectable as a single object,
      followed by a placeholder “Enter name here …”.'
  - name: Using different shape types
    text: You can replace `ShapeType.Rectangle` or `ShapeType.Ellipse` with any other
      `ShapeType` (e.g., `ShapeType.Polygon`, `ShapeType.Line`). The grouping logic
      remains identical.
  - name: Setting fill color and borders
    text: '```csharp rectangleShape.FillColor = System.Drawing.Color.LightBlue; rectangleShape.StrokeColor
      = System.Drawing.Color.DarkBlue; ellipseShape.FillColor = System.Drawing.Color.LightCoral;
      ``` Adding fill and stroke improves visual distinction, especially when the
      document is shared with non‑technical'
  - name: Rotating the entire group
    text: '```csharp groupShape.Rotation = 45; // rotates both shapes together ```
      Rotating the group is more efficient than rotating each child individually.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: Crea un documento Word programmaticamente e raggruppa le forme in C#
url: /it/net/programming-with-shapes/create-word-document-programmatically-and-group-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Creare un documento Word programmaticamente e raggruppare forme in C#

Se devi **creare un documento Word programmaticamente**, questo tutorial ti mostra come costruire un file DOCX con Aspose.Words e **raggruppare più forme Word** insieme. Tratteremo anche **aggiungere un rettangolo a Word** e **come creare una forma di gruppo** che contiene sia un rettangolo sia un'ellisse, più un StructuredDocumentTag di testo semplice per l'input dell'utente.

Terminerai con un file Word pronto all'uso che contiene una forma raggruppata rettangolo‑ellisse e un controllo di contenuto dove l'utente può digitare un nome. Non è necessaria alcuna modifica manuale in Word dopo l'esecuzione del codice.

## Cosa ti serve

- .NET 6.0 o successivo (il campione è destinato a .NET 6, ma qualsiasi versione recente di .NET funziona)
- Una licenza di Aspose.Words per .NET (la versione di prova gratuita è sufficiente per i test)
- Visual Studio 2022 o qualsiasi IDE C# tu preferisca
- Familiarità di base con la sintassi C#

## Creare un documento Word programmaticamente – flusso di lavoro generale

Il processo è composto da tre fasi logiche:

1. **Inizializzare** un `Document` e un `DocumentBuilder` – la base per qualsiasi file Word che generi.
2. **Costruire una forma di gruppo** che contiene un rettangolo e un'ellisse – dimostra **raggruppare più forme Word** e **come creare una forma di gruppo**.
3. **Inserire uno StructuredDocumentTag (SDT)** – un controllo di contenuto di testo semplice che consente agli utenti finali di inserire dati, illustrando **aggiungere un rettangolo a Word** come parte del layout complessivo del documento.

Di seguito trovi il codice completo, eseguibile, seguito da una spiegazione passo‑passo.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1 – Initialize the document and builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2 – Create a group shape container
            Shape groupShape = new Shape(doc, ShapeType.Group)
            {
                Width = 400,
                Height = 200
            };

            // Step 3 – Add a rectangle to the group
            Shape rectangleShape = new Shape(doc, ShapeType.Rectangle)
            {
                Width = 200,
                Height = 100,
                Left = 0,
                Top = 0
            };
            groupShape.GroupShape.AddChild(rectangleShape);

            // Step 4 – Add an ellipse (circle) to the group
            Shape ellipseShape = new Shape(doc, ShapeType.Ellipse)
            {
                Width = 100,
                Height = 100,
                Left = 210, // Position next to the rectangle
                Top = 0
            };
            groupShape.GroupShape.AddChild(ellipseShape);

            // Step 5 – Insert the completed group shape into the document
            builder.InsertNode(groupShape);

            // Step 6 – Create a plain‑text StructuredDocumentTag for user input
            StructuredDocumentTag sdtTag = new StructuredDocumentTag(
                doc,
                SdtType.PlainText,
                MarkupLevel.Block)
            {
                Title = "CustomerName"
            };
            builder.InsertNode(sdtTag);
            builder.Writeln("Enter name here …");

            // Step 7 – Save the document
            doc.Save("GroupAndSDT.docx");
            Console.WriteLine("Document created successfully.");
        }
    }
}
```

### Passo 1 – Inizializzare il documento e il builder
L'oggetto `Document` rappresenta l'intero file DOCX, mentre `DocumentBuilder` fornisce un'API comoda per aggiungere contenuti. Inizializzarli è il primo requisito ogni volta che **crei un documento Word programmaticamente**.

> **Suggerimento:** Se prevedi di riutilizzare lo stesso documento in più operazioni, mantieni un'unica istanza di `DocumentBuilder` per evitare creazioni di oggetti non necessarie.

### Passo 2 – Creare un contenitore di forma di gruppo
Una `Shape` con `ShapeType.Group` funge da tela che può contenere altre forme. Impostare `Width` e `Height` definisce il riquadro di delimitazione per il gruppo. Questo è il fulcro di **come creare una forma di gruppo** in Aspose.Words.

> **Caso limite:** Se la larghezza del gruppo è più piccola della larghezza combinata dei suoi figli, questi verranno ritagliati. Assicurati che il gruppo sia sufficientemente grande da contenere ogni forma figlia.

### Passo 3 – Aggiungere un rettangolo a Word
Un rettangolo viene creato con `ShapeType.Rectangle`. Le proprietà `Left` e `Top` lo posizionano rispetto all'origine del gruppo. Questo passo dimostra **aggiungere un rettangolo a Word** e mostra come controllare il posizionamento esatto.

> **Errore comune:** Dimenticare di impostare `Left`/`Top` fa sì che il rettangolo appaia all'origine predefinita del gruppo (0,0), potenzialmente sovrapponendosi ad altri figli.

### Passo 4 – Aggiungere un'ellisse (cerchio) al gruppo
Un'ellisse viene aggiunta nello stesso modo del rettangolo, ma con `ShapeType.Ellipse`. Il valore `Left = 210` la sposta a destra del rettangolo, creando una coppia di forme visivamente distinte all'interno dello stesso gruppo.

> **Perché usare un gruppo?** Il raggruppamento ti consente di spostare, ruotare o ridimensionare entrambe le forme insieme con un'unica operazione successiva, mantenendo il loro layout relativo.

### Passo 5 – Inserire la forma di gruppo completata nel documento
`builder.InsertNode(groupShape)` posiziona l'intero gruppo nella posizione corrente del cursore. Poiché il gruppo contiene già i suoi figli, non è necessario effettuare ulteriori chiamate di inserimento per il rettangolo o l'ellisse.

### Passo 6 – Creare uno StructuredDocumentTag (SDT) di testo semplice
Uno StructuredDocumentTag è un controllo di contenuto che gli utenti finali possono compilare quando il documento viene aperto in Word. Impostare `Title = "CustomerName"` assegna al controllo un identificatore significativo, utile per l'estrazione dei dati in seguito.

> **Perché uno SDT di testo semplice?** Limita l'input a testo semplice, evitando formattazioni accidentali che potrebbero compromettere l'elaborazione successiva.

### Passo 7 – Salvare il documento
`doc.Save("GroupAndSDT.docx")` scrive il file su disco. Il DOCX risultante contiene le forme raggruppate e lo SDT. Aprendo il file in Microsoft Word vedrai un rettangolo accanto a un cerchio, entrambi selezionabili come un unico oggetto, seguito da un segnaposto “Enter name here …”.

#### Output previsto
- Un file chiamato **GroupAndSDT.docx** nella cartella di esecuzione.
- In Word: una forma raggruppata (rettangolo + ellisse) che puoi spostare come un'unica unità.
- Subito sotto il gruppo, un controllo di contenuto con sfondo grigio che invita l'utente a digitare un nome.

## Varianti aggiuntive e best practice

### Utilizzare diversi tipi di forma
Puoi sostituire `ShapeType.Rectangle` o `ShapeType.Ellipse` con qualsiasi altro `ShapeType` (ad es. `ShapeType.Polygon`, `ShapeType.Line`). La logica di raggruppamento rimane identica.

### Impostare colore di riempimento e bordi
```csharp
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```
Aggiungere riempimento e contorno migliora la distinzione visiva, soprattutto quando il documento è condiviso con stakeholder non tecnici.

### Ruotare l'intero gruppo
```csharp
groupShape.Rotation = 45; // rotates both shapes together
```
Ruotare il gruppo è più efficiente rispetto a ruotare ogni figlio singolarmente.

### Esportare in PDF
Se ti serve una versione PDF, basta chiamare:
```csharp
doc.Save("GroupAndSDT.pdf", SaveFormat.Pdf);
```
Tutte le forme raggruppate e lo SDT (renderizzato come campo di testo) appariranno nel PDF.

## Problemi comuni e come evitarli

| Sintomo | Causa | Correzione |
|---------|-------|------------|
|         |       |            |
|         |       |            |
|         |       |            |

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare ulteriori funzionalità dell'API ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}