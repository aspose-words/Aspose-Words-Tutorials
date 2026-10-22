---
category: general
date: 2026-10-07
description: Crea un documento Word vuoto in C# e impara ad aggiungere una forma rettangolare,
  inserire una forma immagine e raggruppare più forme per report dinamici.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- insert image shape
- group multiple shapes
- add image to word
language: it
lastmod: 2026-10-07
og_description: Crea un documento Word vuoto in C# con Aspose.Words. Scopri come aggiungere
  una forma rettangolare, inserire una forma immagine e raggruppare più forme per
  documenti professionali.
og_image_alt: Screenshot of a Word file showing a grouped rectangle and logo created
  with C#
og_title: Crea un documento Word vuoto e raggruppa le forme in C# – guida passo passo
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Create blank Word document in C# and learn to add rectangle shape,
    insert image shape, and group multiple shapes for dynamic reports.
  headline: How to create blank Word document and group shapes in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Come creare un documento Word vuoto e raggruppare le forme in C#
url: /it/net/programming-with-shapes/how-to-create-blank-word-document-and-group-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come creare un documento Word vuoto e raggruppare forme in C#

Se devi **creare un documento Word vuoto** in modo programmatico, questa guida ti mostra esattamente come fare. Vedrai come **aggiungere una forma rettangolare**, **inserire una forma immagine** e **raggruppare più forme** in modo che si comportino come un unico oggetto quando **aggiungi un'immagine a Word** in seguito.

Lavorare con file Word dal codice può sembrare intimidatorio, ma Aspose.Words rende il processo semplice. Alla fine di questo tutorial avrai uno snippet C# riutilizzabile che genera un file Word pulito e vuoto contenente un rettangolo raggruppato e un logo. Potrai incorporare il risultato in fatture, report o qualsiasi flusso di lavoro documentale automatizzato.

## Prerequisiti

Prima di iniziare, assicurati di avere:

* .NET 6.0 o successivo (il codice funziona anche con .NET Framework 4.7+).  
* Una licenza valida di Aspose.Words for .NET o una chiave di valutazione gratuita.  
* Un file immagine (ad es., `logo.png`) posizionato in una cartella a cui puoi fare riferimento dal codice.  
* Visual Studio 2022 o qualsiasi IDE compatibile con C#.

Non sono necessari pacchetti NuGet aggiuntivi oltre a `Aspose.Words`.

## Come creare un documento Word vuoto con Aspose.Words

Il primo passo è sempre **creare un documento Word vuoto**. Questo oggetto ospiterà tutte le forme successive.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// 1️⃣ Initialize a new empty document.
Document doc = new Document();

// 2️⃣ Prepare a DocumentBuilder – it simplifies adding content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` rappresenta l'intero file `.docx`. A questo punto il file è vuoto, soddisfacendo il requisito di *creare un documento Word vuoto*.

## Creare un contenitore per raggruppare più forme

Raggruppare le forme ti consente di spostarle, ruotarle o ridimensionarle insieme. Aspose.Words fornisce la classe `GroupShape` a questo scopo.

```csharp
// 3️⃣ Create a GroupShape that will hold our drawing objects.
GroupShape group = new GroupShape(doc)
{
    // Define the container’s position and size on the page.
    Bounds = new Rectangle(50, 50, 300, 200)
};

// Append the group to the first paragraph of the first section.
doc.FirstSection.Body.FirstParagraph.AppendChild(group);
```

Il rettangolo `Bounds` determina dove appare il gruppo nella pagina. Posizionando il gruppo nel primo paragrafo garantisci che il **creare un documento Word vuoto** contenga immediatamente un contenitore visivo.

## Come aggiungere una forma rettangolare all'interno del gruppo

Una richiesta comune è **aggiungere una forma rettangolare** come sfondo o bordo. Il codice seguente crea un rettangolo e lo aggiunge al gruppo definito in precedenza.

```csharp
// 4️⃣ Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width = 100,
    Height = 80,
    Left = 20,
    Top = 20,
    // Optional: give the rectangle a light gray fill.
    FillColor = Color.LightGray
};

// Add the rectangle to the group.
group.AppendChild(rectangle);
```

Poiché il rettangolo vive all'interno del `GroupShape`, si sposterà insieme a qualsiasi altra forma aggiunta successivamente. Questo è il fulcro della funzionalità di **raggruppare più forme**.

## Come inserire una forma immagine all'interno del gruppo

Successivamente, **inserirai una forma immagine** (il logo) e la posizionerai accanto al rettangolo. Questo dimostra il flusso di lavoro **aggiungere immagine a Word**.

```csharp
// 5️⃣ Create an image shape.
Shape picture = new Shape(doc, ShapeType.Image)
{
    Width = 80,
    Height = 80,
    Left = 150,
    Top = 30
};

// Load the image from disk. Replace the path with your actual image location.
picture.ImageData.SetImage(Image.FromFile(@"YOUR_DIRECTORY/logo.png"));

// Add the image shape to the same group.
group.AppendChild(picture);
```

Il metodo `SetImage` legge il file e lo incorpora direttamente nel documento Word, garantendo che l'immagine rimanga anche se il file sorgente viene spostato. Questo completa il passaggio **inserire forma immagine** e finalizza il requisito **aggiungere immagine a Word**.

## Salvare il documento

Infine, persisti il file su disco. Il file salvato contiene il documento vuoto, il rettangolo raggruppato e il logo incorporato.

```csharp
// 6️⃣ Save the document with the grouped shapes.
doc.Save(@"YOUR_DIRECTORY/GroupShape.docx");
```

Quando apri `GroupShape.docx` in Microsoft Word, vedrai un unico gruppo che include un rettangolo grigio chiaro e il logo posizionato fianco a fianco. Selezionando qualsiasi parte del gruppo potrai spostare o ridimensionare l'intera collezione, dimostrando che le forme sono effettivamente **raggruppare più forme**.

## Esempio completo, eseguibile

Di seguito trovi il programma completo che puoi copiare, incollare ed eseguire. Sostituisci `YOUR_DIRECTORY` con un percorso assoluto o relativo presente sulla tua macchina.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a blank Word document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Create a GroupShape to hold the rectangle and image.
        GroupShape group = new GroupShape(doc)
        {
            Bounds = new Rectangle(50, 50, 300, 200)
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(group);

        // Step 3: Add a rectangle shape inside the group.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 100,
            Height = 80,
            Left = 20,
            Top = 20,
            FillColor = Color.LightGray
        };
        group.AppendChild(rectangle);

        // Step 4: Insert an image shape inside the group.
        Shape picture = new Shape(doc, ShapeType.Image)
        {
            Width = 80,
            Height = 80,
            Left = 150,
            Top = 30
        };
        picture.ImageData.SetImage(Image.FromFile(@"YOUR_DIRECTORY/logo.png"));
        group.AppendChild(picture);

        // Step 5: Save the document.
        doc.Save(@"YOUR_DIRECTORY/GroupShape.docx");
    }
}
```

### Output previsto

* Un file chiamato `GroupShape.docx` situato in `YOUR_DIRECTORY`.  
* Aprendo il file in Word vedrai un unico gruppo visivo contenente un rettangolo grigio a sinistra e il `logo.png` a destra.  
* Selezionando qualsiasi parte del gruppo visivo potrai spostare o ridimensionare l'intera collezione, confermando che le forme sono correttamente **raggruppare più forme**.

## Domande frequenti e gestione dei casi limite

| Domanda | Risposta |
|---|---|
| **Posso aggiungere più di due forme allo stesso gruppo?** | Sì. Chiama `group.AppendChild(yourShape)` per ogni forma aggiuntiva `Shape`. Il gruppo può contenere un numero qualsiasi di oggetti di disegno. |
| **Cosa succede se il file immagine manca?** | `SetImage` genererà una `FileNotFoundException`. Avvolgi la chiamata in un blocco try‑catch e fornisci un fallback (ad es., una forma segnaposto). |
| **Devo impostare `WrapType` per le forme?** | Per impostazione predefinita le forme sono inline. Se ti serve un comportamento flottante, imposta `picture.WrapType = WrapType.Inline;` o un altro tipo di avvolgimento prima di aggiungerla al gruppo. |
| **Come influisce la dimensione del documento sui limiti del gruppo?** | Il rettangolo `Bounds` è definito in punti (1 pt ≈ 1/72 in). Regola le dimensioni se posizioni il gruppo su un layout di pagina diverso (ad es., A4 vs. Letter). |
| **Posso riutilizzare lo stesso gruppo in un altro documento?** | Sì. Clona il gruppo con `GroupShape cloned = (GroupShape)group.Clone(true);` e inseriscilo in un altro `Document`. |

## Consigli professionali

* **Riutilizza il `DocumentBuilder`** per aggiungere testo prima o dopo il gruppo. Rispetta automaticamente la posizione corrente del cursore.  
* **Imposta `Shape.StrokeColor`** se ti serve un bordo visibile attorno al rettangolo.  
* **Usa PNG ad alta risoluzione** per il logo per evitare la pixelatura quando

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare ulteriori funzionalità dell'API ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}