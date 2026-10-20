---
category: general
date: 2026-10-20
description: Nascondi/Mostra una forma con la nuova proprietà `Hidden` usando Aspose.Words
  per C#. Scopri come alternare la visibilità della forma, gestire i casi limite e
  salvare il risultato.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- Hide/Show a Shape with the new `Hidden` prop
- Aspose.Words hide shape
- C# shape hidden property
- Word document shape visibility
- programmatically hide shape
language: it
lastmod: 2026-10-20
og_description: Nascondi/Mostra una forma con la nuova proprietà `Hidden` usando Aspose.Words
  per C#. Padroneggia il toggle della visibilità delle forme ed evita le insidie più
  comuni.
og_image_alt: Screenshot of a Word document where a shape is hidden using the Hidden
  property
og_title: Nascondi/Mostra una forma con la nuova proprietà `Hidden` in Aspose.Words
  (C#)
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Hide/Show a Shape with the new `Hidden` prop using Aspose.Words for
    C#. Learn how to toggle shape visibility, handle edge cases, and save the result.
  headline: Hide/Show a Shape with the new `Hidden` prop in Aspose.Words for C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Nascondi/Mostra una forma con la nuova proprietà `Hidden` in Aspose.Words per
  C#
url: /it/net/programming-with-shapes/hide-show-a-shape-with-the-new-hidden-prop-in-aspose-words-f/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Nascondi/Mostra una Forma con la nuova proprietà `Hidden` in Aspose.Words per C#

Se hai bisogno di **nascondere/mostrare una forma con la nuova proprietà `Hidden`** in un documento Word, questa guida ti mostra esattamente come farlo con Aspose.Words per .NET. Che tu stia generando report, creando template o pulendo documenti importati, controllare la visibilità delle forme programmaticamente ti evita modifiche manuali.

In questo tutorial imparerai a caricare un documento, individuare una forma, attivare la proprietà `Hidden` e salvare il file modificato. I passaggi coprono anche variazioni comuni come la gestione di più forme e il trattamento di grafica inline rispetto a quella flottante.

## Prerequisiti

Prima di iniziare, assicurati di avere:

* .NET 6.0 (o successivo) installato – Aspose.Words supporta .NET Standard 2.0 e .NET Core.  
* Una copia con licenza di **Aspose.Words for .NET** (la versione di prova gratuita è sufficiente per esplorare).  
* Un IDE come Visual Studio 2022 o Visual Studio Code.  
* Un documento Word (`input.docx`) che contiene almeno una forma (ad esempio, un'immagine, SmartArt o una tela di disegno).

## Passo 1: Caricare il documento Word

La prima operazione è creare un oggetto `Document` che rappresenta il file .docx su disco.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*Perché questo passo è importante*: `Document` è il punto di ingresso per tutte le operazioni di Aspose.Words. Caricare il file in memoria ti dà pieno accesso al suo albero di nodi, incluse le forme.

## Passo 2: Recuperare la forma target

Per attivare/disattivare la visibilità devi ottenere un riferimento al nodo della forma. L'esempio qui sotto recupera la prima forma nel documento, ma puoi adattare la logica per individuare le forme per nome, tipo o indice.

```csharp
// Get the first Shape node in the document tree
Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

if (shape == null)
{
    throw new InvalidOperationException("No shape was found in the document.");
}
```

*Perché questo passo è importante*: `GetChild` con `true` esegue una ricerca profonda, assicurando di trovare le forme anche quando sono annidate in tabelle o intestazioni. Verificare `null` previene una `NullReferenceException` quando il documento non contiene forme.

## Passo 3: Nascondere la forma con la proprietà `Hidden`

Aspose.Words ha introdotto la proprietà `Hidden` per controllare se una forma viene renderizzata o stampata. Impostandola su `true` la forma viene nascosta; impostandola su `false` la forma diventa nuovamente visibile.

```csharp
// Hide the shape so it will not appear in the rendered document
shape.Hidden = true;
```

Se hai bisogno di **mostrare** una forma precedentemente nascosta, assegna semplicemente `false`:

```csharp
// Show the shape again
shape.Hidden = false;
```

*Perché questo passo è importante*: La proprietà `Hidden` funziona sia per forme fluttuanti che inline, e si integra con la formattazione “Hidden” nativa di Word. Questo approccio è più affidabile rispetto alla rimozione della forma perché il nodo rimane nell'albero del documento, preservando layout e riferimenti.

## Passo 4: Salvare il documento modificato

Dopo aver regolato la visibilità, scrivi le modifiche in un nuovo file (o sovrascrivi l'originale se lo desideri).

```csharp
// Save the document with the updated shape visibility
doc.Save("YOUR_DIRECTORY/ShapeHidden.docx");
```

*Perché questo passo è importante*: `Save` serializza l'albero di nodi in memoria in un pacchetto .docx che Word può aprire. Il flag nascosto viene mantenuto, così aprendo il file in Microsoft Word la forma verrà mostrata secondo l'impostazione `Hidden`.

## Esempio completo e eseguibile

Mettere insieme tutti i passaggi ti fornisce un programma autonomo che puoi copiare, compilare ed eseguire.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HideShowShapeExample
{
    static void Main()
    {
        // 1. Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Retrieve the first shape in the document
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            Console.WriteLine("No shape found. Exiting.");
            return;
        }

        // 3. Toggle the Hidden property
        // Hide the shape
        shape.Hidden = true;
        // To show the shape again, uncomment the following line:
        // shape.Hidden = false;

        // 4. Save the modified document
        doc.Save("YOUR_DIRECTORY/ShapeHidden.docx");

        Console.WriteLine("Document saved. Shape hidden = " + shape.Hidden);
    }
}
```

**Output previsto** quando esegui il programma:

```
Document saved. Shape hidden = True
```

Aprendo `ShapeHidden.docx` in Microsoft Word il documento viene visualizzato senza la forma target. Se imposti `shape.Hidden = false;` prima di salvare, la forma riappare.

## Gestire più forme

L'esempio sopra funziona per una singola forma. I documenti reali spesso contengono molte grafiche. Usa un ciclo per nascondere o mostrare tutte le forme che soddisfano una condizione (ad esempio, un nome o tipo specifico).

```csharp
// Hide every picture shape in the document
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    if (s.ShapeType == ShapeType.Image)
    {
        s.Hidden = true; // hide picture
    }
}
doc.Save("YOUR_DIRECTORY/AllPicturesHidden.docx");
```

*Suggerimento*: Filtrare per `ShapeType` evita di nascondere involontariamente elementi decorativi come caselle di testo o SmartArt.

## Casi limite e migliori pratiche

| Situazione | Gestione consigliata |
|-----------|----------------------|
| **La forma è all'interno di un'intestazione/piè di pagina** | Recupera prima il nodo dell'intestazione/piè di pagina, quindi chiama `GetChild(NodeType.Shape, …)` su quel sotto‑documento. |
| **Il documento non contiene forme** | Controlla sempre `null` dopo `GetChild` o verifica `doc.GetChildNodes(NodeType.Shape, true).Count`. |
| **È necessario preservare il flag nascosto tra diverse versioni di Word** | La proprietà `Hidden` è memorizzata nell'XML della forma come `<w:hidden/>`, supportata da Word 2007 e versioni successive. |
| **Prestazioni con documenti di grandi dimensioni** | Usa `doc.GetChildNodes(NodeType.Shape, true)` una sola volta e riutilizza la collezione invece di chiamare ripetutamente `GetChild`. |

## Consiglio professionale: combinare `Hidden` con `WrapType`

Quando una forma è nascosta, Word riserva comunque lo spazio che occuperebbe a meno che non cambi anche il comportamento di avvolgimento. Impostare `WrapType = WrapType.None` rimuove l'area segnaposto.

```csharp
shape.Hidden = true;
shape.WrapType = WrapType.None;
```

Ciò garantisce che il layout si riduca come se la forma non fosse mai esistita, utile per generare report puliti.

## Conclusione

Ora sai come **nascondere/mostrare una forma con la nuova proprietà `Hidden`** usando Aspose.Words per C#. La soluzione copre il caricamento di un documento, l'individuazione di una forma, il toggle della proprietà `Hidden` e la persistenza della modifica. Seguendo i consigli delle migliori pratiche — controllare `null`, gestire più forme e regolare le impostazioni di avvolgimento — puoi controllare in modo affidabile la visibilità delle forme in qualsiasi scenario di automazione Word.

Pronto a esplorare di più? Considera i prossimi passi:

* **Nascondi/Mostra più forme** basate su metadati personalizzati (utilizza la tecnica “nascondere forma programmaticamente”).
* **Combina `Hidden` con contenuto condizionale** usando i campi di Aspose.Words per la generazione dinamica di report.
* **Esplora altre proprietà dei nodi**, come `Visible` per oggetti grafico o `IsDeleted` per il controllo a livello di paragrafo.

Buona programmazione e goditi il controllo fine che Aspose.Words offre per la visibilità delle forme nei documenti Word!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [how to hide shape in Word using C# – step-by-step guide](/words/english/net/programming-with-shapes/how-to-hide-shape-in-word-using-c-step-by-step-guide/)
- [How to Hide Shape in Word with C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/how-to-hide-shape-in-word-with-c-step-by-step-guide/)
- [Create a Blank Word Document with a Hidden Ellipse Shape – Full C# Guide](/words/english/net/programming-with-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape-ful/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}