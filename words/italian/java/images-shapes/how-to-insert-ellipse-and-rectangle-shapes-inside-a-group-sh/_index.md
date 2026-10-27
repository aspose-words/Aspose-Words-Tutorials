---
category: general
date: 2026-10-23
description: Impara come inserire un'ellisse e come aggiungere una forma rettangolare
  in Word usando Aspose.Words. Include lo spostamento del cursore sulla forma e come
  creare una forma di gruppo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert ellipse
- how to add rectangle
- move cursor to shape
- insert rectangle shape word
- how to create group shape
language: it
lastmod: 2026-10-23
og_description: Come inserire un'ellisse e aggiungere una forma rettangolare in Word
  con Aspose.Words. Segui la guida passo‑passo per spostare il cursore sulla forma
  e creare una forma di gruppo.
og_image_alt: Screenshot of a Word document showing a group shape containing a rectangle
  and an ellipse
og_title: Come inserire forme ellittiche e rettangolari in un gruppo di forme di Word
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Learn how to insert ellipse and how to add rectangle shape in Word
    using Aspose.Words. Includes move cursor to shape and how to create group shape.
  headline: How to insert ellipse and rectangle shapes inside a group shape with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Come inserire forme ellisse e rettangolo all'interno di un gruppo di forme
  con Aspose.Words
url: /it/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come inserire forme ellisse e rettangolo all'interno di una forma di gruppo con Aspose.Words

Se hai bisogno di sapere **come inserire un'ellisse** in un documento Word in modo programmatico, questa guida mostra l'intero processo. Vedrai anche **come aggiungere una forma rettangolo**, imparerai a **spostare il cursore sulla forma**, e scoprirai **come creare una forma di gruppo** che contiene più oggetti di disegno.

L'automazione di Word richiede spesso un posizionamento preciso degli oggetti di disegno. Alla fine di questo tutorial potrai generare un file `.docx` che contiene un rettangolo e un'ellisse raggruppati, pronti per ulteriori stilizzazioni o esportazioni. Non sono necessari strumenti esterni oltre alla libreria Aspose.Words per .NET e a un ambiente di sviluppo .NET.

## Prerequisiti

* .NET 6.0 o versioni successive installato.
* Aspose.Words per .NET (pacchetto NuGet `Aspose.Words`) aggiunto al tuo progetto.
* Conoscenza di base della sintassi C# e di Visual Studio (o di qualsiasi IDE).

Questi requisiti garantiscono che il codice venga compilato senza configurazioni aggiuntive.

## Come creare una forma di gruppo in Word

Una forma di gruppo funge da contenitore che consente di spostare, ruotare o formattare più forme come un'unica unità. Il codice seguente crea un gruppo con una dimensione specifica (300 × 200 punti) e prepara il documento per ulteriori operazioni di disegno.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapeDemo
{
    static void Main()
    {
        // Create a new blank document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a group shape that will act as a container for other shapes.
        GroupShape group = builder.InsertGroupShape(300, 200);
        
        // The group shape is now part of the document.
        // Subsequent shape insertions will be placed inside this group.
```

*Perché questo passaggio è importante*: La forma di gruppo definisce un sistema di coordinate locale. Tutte le forme aggiunte dopo aver spostato il cursore nel gruppo saranno posizionate rispetto all'origine del gruppo, rendendo i calcoli di layout semplici.

## Come aggiungere una forma rettangolo in Word

Ora che il gruppo esiste, puoi **inserire una forma rettangolo** al suo interno. Il rettangolo servirà come sfondo o segnaposto visivo per altri contenuti.

```csharp
        // Move the cursor into the group so that the next shape is added to it.
        builder.MoveTo(group);
        
        // Insert a rectangle of width 100 points and height 50 points.
        builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

*Spiegazione*: `MoveTo(group)` indica al builder che il punto di inserimento attivo è la forma di gruppo. Senza spostare il cursore, `InsertShape` aggiungerebbe il rettangolo al corpo principale del documento invece che al gruppo.

## Come inserire un'ellisse

Con il rettangolo in posizione, ora puoi dimostrare **come inserire un'ellisse**. L'ellisse sarà centrata all'interno dello stesso gruppo, sovrapponendosi al rettangolo se desiderato.

```csharp
        // Keep the cursor inside the same group.
        builder.MoveTo(group);
        
        // Insert an ellipse of width 80 points and height 80 points.
        builder.InsertShape(ShapeType.Ellipse, 80, 80);
```

*Perché il cursore deve essere spostato*: Ogni chiamata a `InsertShape` rispetta la posizione corrente del cursore. Richiamare nuovamente `MoveTo(group)` garantisce che l'ellisse sia anche un figlio del gruppo, preservando la gerarchia prevista.

## Spostare il cursore sulla forma prima di inserire oggetti aggiuntivi

Se devi aggiungere altre forme in seguito, sposta sempre **il cursore sulla forma** prima di ogni inserimento. Questo schema evita collocamenti accidentali al di fuori del gruppo.

```csharp
        // Example: add a third shape, such as a line.
        builder.MoveTo(group);
        builder.InsertShape(ShapeType.Line, 150, 0);
```

*Suggerimento*: Riutilizzare `MoveTo(group)` è poco costoso e migliora la leggibilità del codice. Inoltre rende più facile la manutenzione futura poiché il contesto di inserimento è esplicito.

## Salva il documento

Infine, salva il documento su disco. L'esempio salva il file come `GroupShape.docx` in una cartella specificata.

```csharp
        // Save the document to the desired location.
        document.Save(@"C:\Temp\GroupShape.docx");
    }
}
```

Quando apri il file salvato in Microsoft Word, vedrai un unico gruppo contenente un rettangolo e un'ellisse, entrambi posizionati correttamente.

### Output previsto

* Un file `.docx` denominato `GroupShape.docx`.
* All'interno del documento, un oggetto di disegno raggruppato di dimensioni 300 × 200 punti.
* All'interno del gruppo:
  * Un rettangolo (100 × 50 punti) situato all'origine del gruppo.
  * Un'ellisse (80 × 80 punti) che sovrappone il rettangolo.
  * Qualsiasi altra forma aggiunta dopo aver spostato il cursore.

## Varianti comuni e casi limite

| Situazione | Approccio consigliato |
|------------|-----------------------|
| **Dimensioni unità diverse** | Aspose.Words utilizza i punti (1 pt = 1/72 in). Converti centimetri o pollici in punti prima di chiamare `InsertShape`. |
| **Rotazione delle forme all'interno del gruppo** | Dopo aver inserito una forma, recupera il suo oggetto `ShapeBase` e imposta `ShapeBase.RotationAngle`. |
| **Aggiungere testo all'interno di una forma** | Usa `ShapeBase.AppendChild(new Paragraph(document))` e poi aggiungi un `Run` con il testo desiderato. |
| **Salvare in PDF invece di DOCX** | Chiama `document.Save("GroupShape.pdf", SaveFormat.Pdf);` – la gerarchia del gruppo è preservata nell'output PDF. |

Queste varianti dimostrano che la stessa logica **come inserire un'ellisse** può essere adattata a molti scenari reali.

## Consigli professionali

* **Riutilizza la stessa istanza di `DocumentBuilder`** – riduce l'overhead di memoria e mantiene lo stato del documento coerente.
* **Convalida le dimensioni della forma** – larghezze o altezze estremamente grandi possono causare problemi di rendering in versioni più vecchie di Word.
* **Raggruppa prima di applicare lo stile** – applicare colori di riempimento o stili di linea al gruppo dopo aver aggiunto tutti i figli garantisce un aspetto uniforme.

## Conclusione

Ora comprendi **come inserire un'ellisse** e **come aggiungere una forma rettangolo** all'interno di un contenitore raggruppato in un documento Word usando Aspose.Words. Spostando costantemente **il cursore sulla forma** prima di ogni inserimento, mantieni una gerarchia pulita ed eviti collocamenti accidentali. L'esempio completo compila, viene eseguito e produce una forma raggruppata che può essere ulteriormente personalizzata o esportata.

Pronto a esplorare di più? Prova a combinare questa tecnica con **come creare una forma di gruppo** per diagrammi complessi, o sperimenta **inserire una forma rettangolo in Word** insieme a caselle di testo per la generazione di report ricchi. Buon coding!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Come creare una forma rettangolo e forme di gruppo in Word con Aspose.Words](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)
- [Come creare un documento Word vuoto e aggiungere una forma ellisse nascosta in C#](/words/english/java/images-shapes/how-to-create-blank-word-document-and-add-a-hidden-ellipse-s/)
- [Come creare un documento docx con forma di gruppo e aggiungere controlli interattivi in C#](/words/english/java/images-shapes/how-to-create-group-shape-docx-and-add-interactive-controls/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}