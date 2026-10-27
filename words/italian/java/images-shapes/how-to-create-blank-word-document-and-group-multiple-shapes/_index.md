---
category: general
date: 2026-10-26
description: Crea un documento Word vuoto in C# e impara come inserire una forma di
  gruppo, quindi aggiungi una forma rettangolare al gruppo. Questa guida copre la
  creazione di gruppi di più forme passo dopo passo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group multiple shapes
- insert rectangle shape
- how to insert group
- how to add rectangle
language: it
lastmod: 2026-10-26
og_description: Crea un documento Word vuoto in C# e scopri come inserire un gruppo,
  quindi aggiungi una forma rettangolare. Padroneggia il raggruppamento di più forme
  con un esempio di codice completo.
og_image_alt: Screenshot showing a blank Word document with a grouped rectangle shape
og_title: Crea un documento Word vuoto e raggruppa più forme – tutorial C#
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Create a blank Word document in C# and learn how to insert a group
    shape, then add a rectangle shape to the group. This guide covers group multiple
    shapes step‑by‑step.
  headline: How to create blank Word document and group multiple shapes
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Come creare un documento Word vuoto e raggruppare più forme
url: /it/java/images-shapes/how-to-create-blank-word-document-and-group-multiple-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come creare un documento Word vuoto e raggruppare più forme

Se hai bisogno di **creare un documento Word vuoto** programmaticamente, questo tutorial ti mostra esattamente come fare. Vedrai come inserire una forma di gruppo, poi **aggiungere un rettangolo** a quel gruppo, coprendo l'intero flusso di lavoro da un documento vuoto a un disegno raggruppato.

Lavorare con file Word spesso significa organizzare più disegni insieme—pensa a un diagramma composto da più forme. Alla fine di questa guida sarai in grado di **raggruppare più forme**, inserire una **forma rettangolo**, e comprendere **come inserire un gruppo** e **come aggiungere un rettangolo** in modo pulito e riutilizzabile.

## Cosa ti servirà

* .NET 6.0 o versioni successive (il codice funziona anche con .NET Framework 4.6+)
* **Aspose.Words for .NET** pacchetto NuGet (`Install-Package Aspose.Words`)
* Una conoscenza di base di C# e dell'IDE Visual Studio (qualunque IDE va bene)

> **Consiglio professionale:** Aspose.Words funziona completamente offline; non hai bisogno di una connessione internet dopo che il pacchetto è stato installato.

## Passo 1: Crea un documento Word vuoto

La prima operazione è istanziare un oggetto `Document` vuoto. Questo oggetto rappresenta il **documento Word vuoto** che successivamente arricchirai con forme.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1 – create a new blank Word document
        Document doc = new Document();               // <-- blank document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Perché è importante:* Un `Document` senza sezioni o paragrafi è comunque un file .docx valido. Partire da una base pulita garantisce che nessuna formattazione nascosta interferisca con le forme che aggiungerai in seguito.

## Passo 2: Inserisci una forma di gruppo (come inserire un gruppo)

Una **forma di gruppo** agisce come un contenitore che può contenere altri oggetti di disegno. In Aspose.Words la crei con `InsertGroupShape`.

```csharp
        // Step 2 – insert a group shape that will hold other shapes
        GroupShape group = builder.InsertGroupShape();   // <-- container for shapes
```

*Perché usare un gruppo?* Il raggruppamento ti permette di spostare, ruotare o ridimensionare più forme come un'unica unità. Questo è essenziale per diagrammi in cui gli elementi devono rimanere allineati.

## Passo 3: Inserisci una forma rettangolo (inserire forma rettangolo)

Ora aggiungi un rettangolo al documento. Il metodo `InsertShape` restituisce un oggetto `Shape` che potrai successivamente allegare al gruppo.

```csharp
        // Step 3 – create a rectangle shape with specific dimensions
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50); // width=100pt, height=50pt
```

*Perché un rettangolo?* I rettangoli sono il blocco costitutivo più comune per diagrammi di flusso, mock‑up UI e grafiche segnaposto. Le dimensioni sono espresse in punti (1 pt ≈ 1/72 pollice).

## Passo 4: Aggiungi il rettangolo al gruppo (come aggiungere un rettangolo)

Una forma creata con `InsertShape` vive direttamente nel corpo del documento. Per renderla parte del gruppo, chiama `AppendChild` sul `GroupShape`.

```csharp
        // Step 4 – add the rectangle to the previously created group
        group.AppendChild(rectangle);   // <-- rectangle now belongs to the group
```

*Cosa succede dietro le quinte?* `AppendChild` sposta il nodo del rettangolo dalla storia principale del documento nella collezione interna del gruppo, preservando la sua dimensione e posizione rispetto all'origine del gruppo.

## Passo 5: Salva il documento

Infine, scrivi il file su disco. Puoi aprire il `.docx` risultante in Microsoft Word per vedere il rettangolo raggruppato.

```csharp
        // Step 5 – save the document to a file
        doc.Save("GroupedShapeExample.docx");
    }
}
```

> **Caso limite:** Se intendi aggiungere altre forme (ad esempio cerchi, linee) allo stesso gruppo, ripeti **Passo 3** e **Passo 4** per ogni nuova forma prima di salvare. Il gruppo regolerà automaticamente il suo riquadro di delimitazione per includere tutti i figli.

## Come raggruppare più forme – estendendo l'esempio

Di seguito è riportato un breve snippet che aggiunge una seconda forma (un'ellisse) allo stesso gruppo, dimostrando **raggruppare più forme** in un unico documento.

```csharp
        // Additional shape: an ellipse
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 40);
        group.AppendChild(ellipse);   // now the group contains rectangle + ellipse
```

Quando apri `GroupedShapeExample.docx`, vedrai il rettangolo e l'ellisse muoversi insieme quando selezioni il gruppo in Word.

## Domande comuni e risoluzione dei problemi

| Domanda | Risposta |
|----------|--------|
| **Ho bisogno di una licenza per Aspose.Words?** | Una valutazione gratuita funziona senza licenza, ma aggiunge una filigrana. Per la produzione, applica una licenza per rimuovere la filigrana e sbloccare le prestazioni complete. |
| **Posso posizionare le forme con precisione?** | Sì. Dopo aver inserito una forma puoi impostare le proprietà `Shape.Left`, `Shape.Top`, `Shape.Width` e `Shape.Height`. |
| **Cosa succede se il rettangolo scompare dopo il salvataggio?** | Assicurati di chiamare `group.AppendChild(rectangle)` *dopo* aver inserito il rettangolo. È necessario aggiungere prima la forma al corpo del documento e poi spostarla nel gruppo. |
| **È possibile raggruppare forme in sezioni diverse?** | No. Tutte le forme in un gruppo devono appartenere alla stessa storia (sezione). Crea gruppi separati per sezione se necessario. |

## Riepilogo

Ora sai come **creare un documento Word vuoto**, **inserire un gruppo**, **aggiungere un rettangolo**, e **raggruppare più forme** usando Aspose.Words per .NET. L'esempio completo e eseguibile sopra può essere copiato in un'app console ed eseguito immediatamente.

## Prossimi passi

* Sperimenta con le dimensioni e i colori della **forma rettangolo** (`rectangle.FillColor = Color.LightBlue;`).  
* Esplora altri tipi di forma (`ShapeType.Polygon`, `ShapeType.Line`) per arricchire i tuoi diagrammi.  
* Impara a convertire il `.docx` finale in PDF (`doc.Save("output.pdf");`) per la distribuzione.  
* Approfondisci **come aggiungere un rettangolo** a documenti esistenti che contengono già testo—usa `DocumentBuilder.MoveTo` per posizionare il gruppo dove ti serve.

Sentiti libero di adattare il codice alle tue esigenze di reporting o generazione di diagrammi. Buon coding!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Come creare un documento Word vuoto e raggruppare forme in C#](/words/english/net/programming-with-shapes/how-to-create-blank-word-document-and-group-shapes-in-c/)
- [Come raggruppare forme in Word e aggiungere forme al documento Word](/words/english/net/programming-with-shapes/how-to-group-shapes-in-word-and-add-shapes-to-word-document/)
- [Come creare una forma rettangolo e raggruppare forme in Word con Aspose.Words](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}