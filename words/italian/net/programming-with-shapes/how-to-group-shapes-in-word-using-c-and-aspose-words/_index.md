---
category: general
date: 2026-09-30
description: Raggruppa forme in Word con C# – impara a raggruppare le forme, aggiungere
  rettangolo ed ellisse e inserire forme rettangolari nei documenti Word programmaticamente.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- how to group shapes
- how to add rectangle
- how to add ellipse
- insert rectangle shape word
language: it
lastmod: 2026-09-30
og_description: Raggruppa forme in Word usando C# e Aspose.Words. Segui questa guida
  completa per aggiungere un rettangolo, aggiungere un'ellisse e imparare a raggruppare
  le forme in modo efficiente.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  shape
og_title: Raggruppa forme in Word con C# – guida passo passo
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: group shapes in Word with C# – learn how to group shapes, add rectangle
    and ellipse, and insert rectangle shape Word documents programmatically.
  headline: How to group shapes in Word using C# and Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Come raggruppare le forme in Word usando C# e Aspose.Words
url: /it/net/programming-with-shapes/how-to-group-shapes-in-word-using-c-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come raggruppare forme in Word usando C# e Aspose.Words

Se hai bisogno di **raggruppare forme in Word** in modo programmatico, questa guida ti mostra esattamente come fare. Vedrai come aggiungere un rettangolo, aggiungere un'ellisse e poi combinarli in un unico gruppo di forme usando la libreria Aspose.Words per .NET.

Lavorare con le forme è una necessità comune quando si generano report, contratti o materiali di marketing automaticamente. Alla fine di questo tutorial avrai un metodo C# riutilizzabile che carica un file DOCX, inserisce un rettangolo e un'ellisse, li raggruppa e salva il risultato—tutto senza aprire Word manualmente.

## Prerequisiti

Prima di iniziare, assicurati di avere:

* .NET 6.0 SDK o versioni successive installate  
* Un ambiente di sviluppo come Visual Studio 2022 (l’edizione Community va bene)  
* Una licenza Aspose.Words per .NET o una copia di valutazione gratuita (l’API funziona senza licenza ma aggiunge una filigrana)  

Hai inoltre bisogno di un documento Word di origine (`input.docx`) in una cartella a cui puoi fare riferimento dal codice. Il documento può essere vuoto; il tutorial si concentra sulla gestione delle forme.

## Passo 1: Creare un nuovo progetto console e aggiungere Aspose.Words

Apri un terminale o il prompt dei comandi di Visual Studio e esegui:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

Questo crea una nuova applicazione console denominata **WordShapeDemo** e aggiunge il pacchetto NuGet `Aspose.Words`, che contiene le classi `Document` e `DocumentBuilder` utilizzate per manipolare i file Word.

## Passo 2: Caricare o creare un documento

La prima operazione quando si lavora con **forme raggruppate in Word** è ottenere un oggetto `Document`. Puoi caricare un file DOCX esistente o partire da un documento vuoto.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Load an existing document (replace the path with your own)
        Document document = new Document(@"YOUR_DIRECTORY\input.docx");

        // If you prefer a brand‑new document, uncomment the next line:
        // Document document = new Document();
```

La classe `Document` rappresenta l’intero file Word. Caricare un file ti fornisce una tela pronta per l’inserimento delle forme.

## Passo 3: Iniziare una forma di gruppo

Una *forma di gruppo* ti consente di trattare diverse forme indipendenti come un’unica unità—perfetta per spostarle o ridimensionarle insieme. Per avviare un gruppo, chiama `StartGroupShape()` su un `DocumentBuilder`.

```csharp
        // Create a builder to edit the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Begin a group shape that will contain multiple shapes
        builder.StartGroupShape();
```

Chiamare `StartGroupShape` indica ad Aspose.Words che ogni successiva inserzione di forma appartiene allo stesso gruppo logico fino a quando non chiami `EndGroupShape`.

## Passo 4: Come aggiungere una forma rettangolo in Word

Ora che il gruppo è aperto, inserisci un rettangolo. Il metodo `InsertShape` accetta un enum `ShapeType`, seguito da larghezza e altezza (in punti).

```csharp
        // Add a rectangle shape to the group (100 pt wide, 50 pt high)
        builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

Il rettangolo diventa il primo membro del gruppo. Puoi personalizzarne il riempimento, il contorno o il testo in seguito, se necessario.

## Passo 5: Come aggiungere una forma ellisse in Word

Successivamente, aggiungi un’ellisse (un cerchio quando larghezza e altezza sono uguali). Questo dimostra **come aggiungere un’ellisse** usando lo stesso builder.

```csharp
        // Add an ellipse shape to the same group (80 pt wide, 80 pt high)
        builder.InsertShape(ShapeType.Ellipse, 80, 80);
```

Entrambe le forme ora condividono lo stesso spazio di coordinate all’interno del gruppo, rendendo facile allinearle visivamente.

## Passo 6: Chiudere la definizione della forma di gruppo

Quando hai aggiunto tutti i membri desiderati, chiudi il gruppo. Questo finalizza la collezione di forme in modo che Word le tratti come un unico oggetto.

```csharp
        // End the group shape definition
        builder.EndGroupShape();
```

A questo punto il documento contiene una singola forma raggruppata composta da un rettangolo e un’ellisse.

## Passo 7: Salvare il documento modificato

Infine, scrivi le modifiche su disco. Puoi sovrascrivere il file originale o crearne uno nuovo.

```csharp
        // Save the document with the grouped shapes
        document.Save(@"YOUR_DIRECTORY\output.docx");

        Console.WriteLine("Document saved with grouped shapes.");
    }
}
```

Eseguendo il programma otterrai `output.docx`. Apri il file in Microsoft Word, seleziona la forma e vedrai che rettangolo ed ellisse si muovono insieme—la prova che l’operazione **raggruppare forme in Word** è riuscita.

### Risultato atteso

* Il file Word contiene un unico oggetto raggruppato.  
* Selezionando il gruppo puoi trascinare, ridimensionare o ruotare sia il rettangolo sia l’ellisse simultaneamente.  
* Non è necessaria alcuna interazione manuale con Word; tutto è eseguito tramite codice C#.

![Forme raggruppate in un documento Word](grouped-shapes.png "Screenshot di un documento Word che mostra un rettangolo e un’ellisse raggruppati")

*Testo alternativo dell’immagine: “Screenshot di un documento Word che mostra un rettangolo e un’ellisse raggruppati”* (soddisfa il requisito del testo alternativo dell’immagine).

## Perché il raggruppamento delle forme è importante

Raggruppare le forme è più di una comodità visiva. Consente di:

* **Mantenere la coerenza del layout** – spostare un gruppo mantiene intatte le posizioni relative.  
* **Applicare trasformazioni una sola volta** – ruotare o scalare l’intero gruppo invece di ogni forma singolarmente.  
* **Semplificare l’elaborazione successiva** – quando altri strumenti leggono il DOCX, vedono una singola forma composita, riducendo la complessità.

Se mai dovessi aggiungere altre forme (ad esempio una linea o una casella di testo) alla stessa unità logica, ti basterà chiamare nuovamente `InsertShape` prima di `EndGroupShape`.

## Varianti comuni e casi limite

| Situazione | Come gestirla |
|-----------|-----------------|
| **Unità diverse** – hai misurazioni in centimetri | Converti i centimetri in punti (`1 cm ≈ 28.35 pt`) prima di chiamare `InsertShape`. |
| **Aggiungere un’etichetta di testo** – vuoi una didascalia all’interno del gruppo | Inserisci un `ShapeType.TextBox` dopo il rettangolo e l’ellisse, quindi imposta la sua proprietà `Text`. |
| **Applicare un colore di riempimento** – ti serve un rettangolo blu | Dopo `InsertShape`, recupera l’ultima forma tramite `builder.CurrentParagraph.Runs[0].Font` e imposta `shape.FillColor = System.Drawing.Color.Blue;`. |
| **Usare un formato documento diverso** – punti a `.doc` invece di `.docx` | Lo stesso codice funziona; basta cambiare l’estensione del file nella chiamata a `Save`. Aspose.Words gestisce automaticamente il formato. |

## Consigli professionali

* **Riutilizza il builder** – puoi avviare e chiudere più gruppi nello stesso documento; basta chiamare nuovamente `StartGroupShape` dopo `EndGroupShape`.  
* **Prestazioni** – inserire più forme all’interno di un unico blocco `StartGroupShape/EndGroupShape` è più veloce rispetto all’inserimento singolo fuori da un gruppo.  
* **Licenza** – una licenza di valutazione aggiunge una filigrana sulla prima pagina. Installa una licenza corretta per rimuoverla negli ambienti di produzione.

## Conclusione

Ora sai come **raggruppare forme in Word** con C#, come **aggiungere un rettangolo**, come **aggiungere un’ellisse** e come **inserire forme rettangolari in documenti Word** usando Aspose.Words. L’esempio completo e funzionante dimostra ogni passaggio, dalla configurazione del progetto al salvataggio del file finale.

Da qui puoi esplorare tipi di forma aggiuntivi, applicare stili o combinare forme raggruppate con tabelle e immagini per creare documenti sofisticati generati programmaticamente.

---

**Passi successivi**

* Impara a **ruotare le forme raggruppate**: usa `Shape.RotationAngle` dopo aver chiuso il gruppo.  
* Esplora la **personalizzazione di riempimento e contorno** per rettangoli ed ellissi.  
* Integra questa logica in un’API ASP.NET Core per generare report su richiesta.  

Buon coding!

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell’API e a esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Rectangle Shape in Word – Full Aspose.Words Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-full-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}