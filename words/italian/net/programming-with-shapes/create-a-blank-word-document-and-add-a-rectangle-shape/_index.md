---
category: general
date: 2026-09-05
description: Scopri come creare un documento Word vuoto e aggiungere una forma rettangolare
  che può essere nascosta usando Aspose.Words in C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- blank word document
- add rectangle shape
- how to hide shape
- hide shape word
- create hidden shape
language: it
lastmod: 2026-09-05
og_description: Creazione di un documento Word vuoto e inserimento di una forma rettangolare
  nascosta usando Aspose.Words – guida passo‑passo per sviluppatori C#.
og_image_alt: Screenshot of a blank Word document with a hidden rectangle shape created
  by Aspose.Words in C#
og_title: Crea un documento Word vuoto con una forma rettangolare nascosta
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Learn how to create a blank word document and add a rectangle shape
    that can be hidden using Aspose.Words in C#.
  headline: Create a blank word document and add a rectangle shape
  type: TechArticle
- description: Learn how to create a blank word document and add a rectangle shape
    that can be hidden using Aspose.Words in C#.
  name: Create a blank word document and add a rectangle shape
  steps:
  - name: Expected result
    text: 'Open `HiddenRectangle.docx` in Word:'
  - name: Can I hide multiple shapes at once?
    text: Yes. Create each shape, set `Hidden = true`, and insert them sequentially.
      The hidden flag works per node, so mixing hidden and visible shapes in the same
      document is supported.
  - name: What if I need the shape to be hidden only in the print view?
    text: 'Word distinguishes between **display** and **print** visibility through
      the `DisplayWhen` property. Aspose.Words does not expose a direct API for that
      flag, but you can modify the underlying XML:'
  - name: Does the hidden shape affect file size?
    text: A hidden shape adds the same XML payload as a visible one, so the file size
      increase is identical. However, because the shape
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: Crea un documento Word vuoto e aggiungi una forma rettangolare
url: /it/net/programming-with-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea un documento Word vuoto e aggiungi una forma rettangolare

Se hai bisogno di creare un **documento Word vuoto** che contenga anche una forma che non vuoi che appaia nel layout, questa guida ti mostra esattamente come farlo con Aspose.Words per .NET. Vedrai un esempio completo e eseguibile che crea un nuovo documento, aggiunge una forma rettangolare, nasconde quella forma e salva il file—senza strumenti aggiuntivi.

Il tutorial copre tutto, dalla configurazione del progetto alla risoluzione dei problemi comuni. Alla fine sarai in grado di generare un file Word che sembra vuoto al lettore ma contiene ancora metadati nascosti, utili per filigrane, archiviazione XML personalizzata o ancore di layout.

## Prerequisiti

Prima di iniziare, assicurati di avere:

* .NET 6.0 SDK o versioni successive (il codice funziona anche con .NET Framework 4.7+)
* Visual Studio 2022 (o qualsiasi IDE che supporti C#)
* Una licenza **Aspose.Words** NuGet attiva (la versione di prova gratuita funziona per i test)
* Familiarità di base con C# e il concetto di nodi del documento

Puoi installare la libreria con il seguente comando CLI:

```bash
dotnet add package Aspose.Words
```

> **Suggerimento professionale:** mantieni la tua versione di Aspose.Words aggiornata; l'API usata in questo tutorial è stabile a partire dalla versione 23.10.

## Come creare un documento Word vuoto con Aspose.Words

Il primo passo è istanziare un oggetto `Document`. Un nuovo `Document` rappresenta un **documento Word vuoto**—nessun paragrafo, nessuna sezione, solo il contenitore del file.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new, empty Word document
Document document = new Document();
```

> **Perché è importante:** Iniziare con un documento pulito garantisce che la forma nascosta che aggiungerai in seguito non interferisca con il contenuto o gli stili esistenti.

## Aggiungi una forma rettangolare al documento

Successivamente creiamo una forma rettangolare. In Aspose.Words una forma è un nodo che può essere posizionato ovunque nell’albero del documento e può essere configurato con dimensioni, riempimento, stile della linea e visibilità.

```csharp
// Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(document);

// Define a rectangle shape (the "add rectangle shape" step)
Shape rectangle = new Shape(document, ShapeType.Rectangle)
{
    Width = 150,   // Width in points (1 point = 1/72 inch)
    Height = 80,   // Height in points
    FillColor = System.Drawing.Color.LightGray,
    StrokeColor = System.Drawing.Color.DarkGray,
    StrokeWeight = 0.5
};
```

Il codice sopra crea un rettangolo visibile. A questo punto potresti inserirlo nel documento con `builder.InsertNode(rectangle)`. Tuttavia, poiché vogliamo che la forma rimanga nascosta, regoleremo la sua proprietà `Hidden` prima dell’inserimento.

## Come nascondere una forma in un documento Word

Word fornisce un attributo `Hidden` per i nodi forma. Quando impostato su `true`, la forma non appare nel layout della pagina, ma rimane parte dell’XML del documento. Questo è il fulcro del requisito **come nascondere una forma**.

```csharp
// Hide the shape so it won't be displayed
rectangle.Hidden = true;
```

> **Spiegazione:** Impostare `Hidden = true` aggiunge l’attributo `<w:hide>` all’XML della forma. I programmi di elaborazione testi ignorano la forma durante il rendering, ma la forma può ancora essere accessibile programmaticamente o tramite la vista XML di Word.

## Inserisci la forma nascosta nel documento vuoto

Ora posizioniamo il rettangolo nascosto nell’albero del documento. Poiché il documento è ancora vuoto, la forma diventa il primo nodo nella storia principale.

```csharp
// Insert the hidden rectangle at the current cursor position
builder.InsertNode(rectangle);
```

Se apri il file risultante in Microsoft Word, vedrai una pagina apparentemente vuota. La forma è presente, ma è invisibile.

## Salva il documento

Infine, scrivi il documento su disco. Puoi scegliere qualsiasi formato supportato (`.docx`, `.pdf`, `.odt`, ecc.). Per questo tutorial useremo il moderno formato DOCX.

```csharp
// Save the file – adjust the path as needed
string outputPath = Path.Combine(Environment.CurrentDirectory, "HiddenRectangle.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

### Risultato atteso

Apri `HiddenRectangle.docx` in Word:

* Il documento appare vuoto (nessuna forma o testo visibile).
* Se ispezioni il file con uno strumento come **Open XML SDK** o il **Word XML Viewer**, vedrai l’elemento `<w:pict>` contenente il rettangolo con l’attributo `hidden`.

![documento Word vuoto con forma rettangolare nascosta](image.png){: .align-center alt="documento Word vuoto con forma rettangolare nascosta"}

## Esempio completo e eseguibile

Di seguito trovi il programma completo che puoi copiare‑incollare in un’applicazione console. Include tutte le direttive `using` necessarie, la gestione degli errori e i commenti.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Prepare a DocumentBuilder to manipulate the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Define a rectangle shape (add rectangle shape)
        Shape rectangle = new Shape(document, ShapeType.Rectangle)
        {
            Width = 150,
            Height = 80,
            FillColor = System.Drawing.Color.LightGray,
            StrokeColor = System.Drawing.Color.DarkGray,
            StrokeWeight = 0.5,
            // 4️⃣ Hide the shape (how to hide shape)
            Hidden = true
        };

        // 5️⃣ Insert the hidden shape into the blank document
        builder.InsertNode(rectangle);

        // 6️⃣ Save the document (create hidden shape)
        string outputPath = Path.Combine(
            Environment.CurrentDirectory, "HiddenRectangle.docx");
        document.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Esegui il programma (`dotnet run`) e verifica il file di output. La console confermerà la posizione di salvataggio.

## Domande comuni e casi particolari

### Posso nascondere più forme contemporaneamente?

Sì. Crea ogni forma, imposta `Hidden = true` e inseriscile sequenzialmente. Il flag nascosto funziona per nodo, quindi è supportato mescolare forme nascoste e visibili nello stesso documento.

### Cosa succede se ho bisogno che la forma sia nascosta solo nella visualizzazione di stampa?

Word distingue tra visibilità **display** e **print** tramite la proprietà `DisplayWhen`. Aspose.Words non espone un’API diretta per quel flag, ma è possibile modificare l’XML sottostante:

```csharp
rectangle.GetShapeRenderer().GetShapeXml()
    .SetAttribute("w:display", "print");
```

Usa questa opzione solo quando hai bisogno della visibilità solo in stampa.

### La forma nascosta influisce sulla dimensione del file?

Una forma nascosta aggiunge lo stesso payload XML di una forma visibile, quindi l’aumento della dimensione del file è identico. Tuttavia, poiché la forma

## Cosa dovresti imparare dopo?

I tutorial seguenti coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Crea documento Word vuoto con forma rettangolare ombreggiata – Guida passo‑passo](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Crea forma rettangolare in Word usando C# – Guida passo‑passo](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Tutorial ombra forma Aspose.Words – Aggiungi un'ombra a una forma Word in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}