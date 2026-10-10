---
category: general
date: 2026-10-10
description: Crea un documento Word vuoto, inserisci un'immagine in Word, aggiungi
  un gruppo di immagini e nascondi la forma nel file salvato. Segui questa guida passo
  passo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert image into word
- add image group
- hide shape word document
language: it
lastmod: 2026-10-10
og_description: Crea un documento Word vuoto, inserisci un'immagine in Word, aggiungi
  un gruppo di immagini e nascondi la forma. Questa guida mostra il codice C# completo.
og_image_alt: Screenshot of a blank Word document with a hidden image group
og_title: Crea un documento Word vuoto, aggiungi un gruppo di immagini, nascondi la
  forma
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Create a blank Word document, insert image into Word, add an image
    group, and hide shape in the saved file. Follow this step‑by‑step guide.
  headline: Create a blank Word document, add an image group, hide shape
  type: TechArticle
tags:
- Word automation
- Aspose.Words
- C#
- Document processing
title: Crea un documento Word vuoto, aggiungi un gruppo di immagini, nascondi la forma
url: /it/java/images-shapes/create-a-blank-word-document-add-an-image-group-hide-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea un documento Word vuoto, aggiungi un gruppo di immagini, nascondi la forma

Se hai bisogno di **creare un documento Word vuoto** e in seguito nascondere elementi visivi, questo tutorial ti mostra esattamente come fare. Imparerai a inserire un'immagine in Word, aggiungere un gruppo di immagini e nascondere la forma in un documento Word in una singola routine C# riutilizzabile.

Useremo la libreria Aspose.Words per .NET, che consente di manipolare file .docx senza avere Microsoft Word installato. Alla fine di questa guida avrai un programma eseguibile che produce un file Word contenente un gruppo di immagini nascosto, pronto per l'elaborazione successiva o per la visualizzazione condizionale.

## Prerequisiti

- .NET 6.0 o successivo (il codice funziona anche con .NET Framework 4.6+)
- Pacchetto NuGet Aspose.Words per .NET (`Install-Package Aspose.Words`)
- Una cartella su disco dove poter leggere un file immagine e scrivere il documento di output
- Familiarità di base con C# e Visual Studio (o qualsiasi IDE preferisci)

## Crea un documento Word vuoto con Aspose.Words

Il primo passo è **creare un documento Word vuoto**. Aspose.Words fornisce la classe `Document` che rappresenta un file Word in memoria. Istanziarla senza argomenti ti restituisce un documento vuoto pronto per i contenuti.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();                 // blank .docx container
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Perché è importante:* Iniziare con un documento vuoto garantisce che non ci siano formattazioni nascoste o sezioni residue che interferiscano con la forma che aggiungerai in seguito.

## Inserisci immagine in Word usando DocumentBuilder

Successivamente, **inseriamo un'immagine in Word** creando prima una forma di gruppo che conterrà l'immagine. Le forme di gruppo ti permettono di trattare più oggetti di disegno come un'unica unità, utile quando in seguito vuoi nasconderli o spostarli insieme.

```csharp
        // Step 2: Insert a group shape with the desired size (width: 300, height: 200)
        GroupShape group = builder.InsertGroupShape(300, 200);
```

Il metodo `InsertGroupShape` crea un contenitore vuoto. Le dimensioni sono espresse in punti (1 punto = 1/72 di pollice). Regola la dimensione per corrispondere alla risoluzione dell'immagine che intendi incorporare.

## Aggiungi il gruppo di immagini al documento

Ora **aggiungiamo il gruppo di immagini** spostando il cursore del builder all'interno del gruppo appena creato e inserendo l'immagine. Tutti gli inserimenti successivi faranno parte del gruppo.

```csharp
        // Step 3: Position the builder inside the group so subsequent inserts go into it
        builder.MoveTo(group);

        // Step 4: Add an image to the group shape
        // Replace the path with the actual location of your PNG/JPEG file
        builder.InsertImage(@"YOUR_DIRECTORY\photo1.png");
```

**Suggerimento:** Usa un percorso assoluto o un percorso relativo correttamente escapato; altrimenti `InsertImage` genera una `FileNotFoundException`.

## Nascondi la forma in un documento Word

Infine, **nascondiamo la forma nel documento Word** impostando la proprietà `Hidden` del gruppo a `true`. Le forme nascoste non vengono visualizzate quando il documento è aperto in Word, ma rimangono nel file e possono essere rivelate programmaticamente in seguito.

```csharp
        // Step 5: Hide the entire group (the image will not be visible in the saved document)
        group.Hidden = true;

        // Step 6: Save the document with the hidden group
        doc.Save(@"YOUR_DIRECTORY\GroupHidden.docx");
    }
}
```

Quando apri *GroupHidden.docx* in Microsoft Word, vedrai una pagina completamente vuota perché il gruppo di immagini è nascosto. Il file contiene comunque i dati dell'immagine, che puoi rendere visibili più tardi con `group.Hidden = false` se necessario.

## Esempio completo, eseguibile

Di seguito trovi il programma completo che puoi copiare‑incollare in un nuovo progetto console:

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
            // 1️⃣ Create a blank Word document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a group shape (300 pt × 200 pt)
            GroupShape group = builder.InsertGroupShape(300, 200);

            // 3️⃣ Move inside the group so inserts become part of it
            builder.MoveTo(group);

            // 4️⃣ Insert the image (replace with your own file)
            builder.InsertImage(@"YOUR_DIRECTORY\photo1.png");

            // 5️⃣ Hide the group so the image is not shown
            group.Hidden = true;

            // 6️⃣ Save the result
            doc.Save(@"YOUR_DIRECTORY\GroupHidden.docx");

            Console.WriteLine("Document created successfully.");
        }
    }
}
```

**Output previsto**

- Un file chiamato `GroupHidden.docx` appare in `YOUR_DIRECTORY`.
- Aprendo il file in Word viene mostrata una pagina vuota.
- L'immagine nascosta può essere rivelata modificando `group.Hidden = false` e salvando nuovamente.

## Varianti comuni e casi limite

| Situazione | Come adattare il codice |
|------------|--------------------------|
| **Immagini multiple** | Inserisci chiamate aggiuntive a `InsertImage` dopo `builder.MoveTo(group)`. Tutte le immagini rimarranno nello stesso gruppo e condivideranno il flag di nascondimento. |
| **Formati immagine diversi** | Aspose.Words supporta PNG, JPEG, BMP, GIF, TIFF. Basta cambiare l'estensione del file; non è necessario modificare il codice. |
| **Visibilità condizionale** | Memorizza una variabile personalizzata del documento (`doc.Variables.Add("ShowImages", "true")`) e imposta `group.Hidden` in base al suo valore a runtime. |
| **Documenti di grandi dimensioni** | Crea il gruppo in una pagina specifica (`builder.InsertBreak(BreakType.PageBreak)`) prima di inserire il gruppo per evitare spostamenti di layout. |
| **Compatibilità con versioni Word più vecchie** | Salva come `doc.Save("output.doc", SaveFormat.Doc)` se ti serve il formato legacy `.doc`; le forme nascoste si comportano allo stesso modo. |

**Suggerimento professionale:** Imposta sempre `group.Hidden = true` *dopo* aver inserito tutti gli elementi figli. Cambiare il flag prima di aggiungere contenuti può far sì che alcuni elementi vengano renderizzati in modo inatteso nelle versioni più vecchie di Word.

## Conclusione

Ora sai come **creare un documento Word vuoto**, **inserire un'immagine in Word**, **aggiungere un gruppo di immagini** e **nascondere la forma nel documento Word** usando Aspose.Words per .NET. L'esempio completo dimostra ogni passaggio, dall'inizializzazione del documento al salvataggio di un file che contiene un gruppo di immagini nascosto.

Successivamente, potresti approfondire:

- Aggiungere caselle di testo o grafici allo stesso gruppo
- Usare `DocumentBuilder.StartBookmark` / `EndBookmark` per contrassegnare sezioni nascoste
- Attivare o disattivare la visibilità in modo programmatico in base all'input dell'utente o a variabili del documento

Sentiti libero di sperimentare con forme, dimensioni e regole di visibilità diverse per adattarle al tuo scenario di automazione. Buon coding!

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell'API ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Crea una forma di gruppo in un documento Word usando Aspose.Words per .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Crea un documento Word con immagine flottante in .NET](/words/english/net/add-content-using-documentbuilder/insert-floating-image/)
- [Inserisci immagine inline in un documento Word usando Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}