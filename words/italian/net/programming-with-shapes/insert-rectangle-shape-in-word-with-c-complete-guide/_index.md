---
category: general
date: 2026-08-10
description: Inserisci una forma rettangolare in Word usando C#. Impara come nascondere
  la forma, nascondere la forma in Word e creare una forma nascosta con Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to hide shape
- hide shape in word
- create hidden shape
language: it
lastmod: 2026-08-10
og_description: Inserisci una forma rettangolare in Word usando C#. Questo tutorial
  spiega come nascondere la forma, nascondere la forma in Word e creare una forma
  nascosta con esempi di codice completi.
og_image_alt: Screenshot showing a hidden rectangle shape inserted into a Word document
  using C#
og_title: Inserisci una forma rettangolare in Word con C# – guida passo passo
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Insert rectangle shape in Word using C#. Learn how to hide shape, hide
    shape in Word, and create hidden shape with Aspose.Words.
  headline: Insert rectangle shape in Word with C# – complete guide
  type: TechArticle
- description: Insert rectangle shape in Word using C#. Learn how to hide shape, hide
    shape in Word, and create hidden shape with Aspose.Words.
  name: Insert rectangle shape in Word with C# – complete guide
  steps:
  - name: Can I hide only the outline but keep the fill visible?
    text: Yes. Instead of setting `Hidden = true`, you can set `rectangle.LineFormat.Visible
      = false` to hide the border while keeping the fill color. This is a variation
      of **how to hide shape** that preserves part of the visual appearance.
  - name: Does the hidden flag work in older Word versions (2003, 2007)?
    text: The hidden attribute is part of the Open XML specification introduced with
      Word 2007. Documents saved in the older binary `.doc` format will not preserve
      the flag. To support legacy formats, save the document as `.docx` and, if needed,
      convert it later using Aspose.Words’ `SaveFormat.Doc`.
  - name: What if I need to hide multiple shapes at once?
    text: Iterate over the `Document.GetChildNodes(NodeType.Shape, true)` collection
      and set `Hidden = true` on each shape that meets your criteria (e.g., a specific
      `ShapeType` or a custom `AlternativeText` value).
  - name: Is there a performance impact when hiding shapes?
    text: The hidden flag adds a tiny XML attribute; it does not affect rendering
      speed. However, a very large number of hidden objects can increase file size
      marginally. Remove shapes you never need to keep the document lean.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Inserire una forma rettangolare in Word con C# – guida completa
url: /it/net/programming-with-shapes/insert-rectangle-shape-in-word-with-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Inserire una forma rettangolare in Word con C# – guida completa

Se hai bisogno di **inserire una forma rettangolare** in un documento Word usando C#, questa guida ti mostra i passaggi esatti. Imparerai anche **come nascondere la forma** in modo che non compaia nel file finale, rispondendo alla comune domanda **nascondere forma in Word** e dimostrando come **creare una forma nascosta** programmaticamente.

Il tutorial copre tutto, dall’impostazione dell’Aspose.Words SDK alla verifica che la forma sia nascosta. Alla fine dell’articolo avrai uno snippet di codice riutilizzabile da inserire in qualsiasi progetto .NET.

## Prerequisiti

Prima di iniziare, assicurati di avere:

- .NET 6.0 o versioni successive installate (il codice funziona anche con .NET Framework 4.6+)
- Una licenza valida di Aspose.Words per .NET o una chiave di valutazione temporanea
- Visual Studio 2022 (o qualsiasi IDE che supporti C#)
- Familiarità di base con la sintassi C# e il Document Object Model (DOM) dei file Word

Non sono necessari pacchetti NuGet aggiuntivi oltre a `Aspose.Words`.

## Passo 1: Creare un nuovo documento vuoto e un DocumentBuilder

La prima operazione è istanziare un oggetto `Document`. Il `DocumentBuilder` fornisce un’API comoda per inserire contenuti come forme, paragrafi e tabelle.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty Word document.
Document document = new Document();

// DocumentBuilder lets you add elements to the document.
DocumentBuilder builder = new DocumentBuilder(document);
```

**Perché è importante:** `Document` rappresenta l’intero file .docx, mentre `DocumentBuilder` mantiene un cursore che traccia dove verrà posizionato il prossimo elemento. Inizializzare entrambi gli oggetti è la base per qualsiasi attività di automazione di Word.

## Passo 2: Inserire la forma rettangolare

Ora inserisci il rettangolo. Il metodo `InsertShape` richiede il tipo di forma e le sue dimensioni in punti (1 punto ≈ 1/72 pollice). Una dimensione di **200 × 100 punti** produce un rettangolo di circa 2,78 × 1,39 pollici.

```csharp
// Insert a rectangle of 200x100 points.
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

**Perché è importante:** L’oggetto `Shape` che ottieni è completamente configurabile—colore, bordo, testo e visibilità possono essere modificati prima di salvare il documento.

## Passo 3: Nascondere la forma

Per impedire che il rettangolo venga visualizzato o stampato, imposta la sua proprietà `Hidden` su `true`. Questa proprietà corrisponde direttamente all’attributo “Hidden” di Word, che Word rispetta sia in visualizzazione che in stampa.

```csharp
// Hide the shape so it never appears.
rectangle.Hidden = true;
```

**Perché è importante:** Impostare `Hidden` è il modo standard per **nascondere forma in Word** senza rimuoverla dalla struttura del documento. La forma rimane accessibile al codice, consentendo manipolazioni successive come formattazione condizionale o toggle di visibilità basati sui dati.

## Passo 4: Salvare il documento

Infine, persisti il documento su disco. Scegli qualsiasi cartella ti piaccia; l’esempio utilizza un percorso segnaposto che dovrai sostituire con uno reale.

```csharp
// Save the document with the hidden rectangle.
document.Save(@"C:\Temp\HiddenShape.docx");
```

**Perché è importante:** Il salvataggio finalizza il file e scrive il flag nascosto nell’Open XML sottostante. Quando apri il documento in Microsoft Word, il rettangolo sarà invisibile, confermando che hai **creato una forma nascosta** con successo.

## Passo 5: Verificare la forma nascosta

Apri il file generato `HiddenShape.docx` in Microsoft Word:

1. Vai su **File → Opzioni → Visualizzazione** e assicurati che *“Mostra testo nascosto”* sia **deselezionato**.  
2. Il rettangolo non dovrebbe essere visibile su alcuna pagina.  
3. Per ricontrollare, abilita *“Mostra testo nascosto”*; il rettangolo apparirà con un contorno puntinato tenue, dimostrando che la forma esiste ma è nascosta.

Se il rettangolo è ancora visibile, verifica di aver salvato il file dopo aver impostato `Hidden = true` e di aver aperto il file corretto.

## Esempio completo eseguibile

Di seguito trovi il programma completo che puoi copiare, incollare ed eseguire direttamente.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a rectangle shape of 200x100 points.
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // Step 3: Hide the shape so it does not appear when viewed or printed.
        rectangle.Hidden = true;

        // Step 4: Save the document with the hidden shape.
        string outputPath = @"C:\Temp\HiddenShape.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
        Console.WriteLine("Open the file in Word to verify that the rectangle is hidden.");
    }
}
```

**Output previsto:** La console stampa il percorso del file e un breve promemoria. Quando il file viene aperto in Word, il rettangolo è invisibile a meno che il testo nascosto non sia abilitato.

## Domande frequenti e casi particolari

### Posso nascondere solo il contorno mantenendo il riempimento visibile?

Sì. Invece di impostare `Hidden = true`, puoi impostare `rectangle.LineFormat.Visible = false` per nascondere il bordo mantenendo il colore di riempimento. Questa è una variante di **come nascondere forma** che preserva parte dell’aspetto visivo.

### Il flag nascosto funziona nelle versioni più vecchie di Word (2003, 2007)?

L’attributo nascosto fa parte della specifica Open XML introdotta con Word 2007. I documenti salvati nel vecchio formato binario `.doc` non conservano il flag. Per supportare formati legacy, salva il documento come `.docx` e, se necessario, converti successivamente usando `SaveFormat.Doc` di Aspose.Words.

### E se devo nascondere più forme contemporaneamente?

Itera sulla collezione `Document.GetChildNodes(NodeType.Shape, true)` e imposta `Hidden = true` su ogni forma che soddisfa i tuoi criteri (ad esempio, un `ShapeType` specifico o un valore personalizzato di `AlternativeText`).

```csharp
foreach (Shape shp in document.GetChildNodes(NodeType.Shape, true))
{
    if (shp.AlternativeText == "HideMe")
        shp.Hidden = true;
}
```

### C’è un impatto sulle prestazioni quando si nascondono forme?

Il flag nascosto aggiunge un piccolo attributo XML; non influisce sulla velocità di rendering. Tuttavia, un numero molto elevato di oggetti nascosti può aumentare marginalmente la dimensione del file. Rimuovi le forme che non ti servono per mantenere il documento leggero.

## Suggerimenti e migliori pratiche

- **Assegna alla forma un nome significativo** usando `rectangle.Name = "MyHiddenRectangle"`; questo aiuta quando devi cercare la forma nel DOM in un secondo momento.  
- **Imposta `AlternativeText`** con un tag personalizzato (es. `"HiddenShape"`). Questo ti permette di individuare la forma senza fare affidamento sul suo indice.  
- **Avvolgi il codice in un blocco try‑catch** per gestire elegantemente errori di licenza o eccezioni I/O.  
- **Rilascia il Document** dopo il salvataggio se elabori molti file in un ciclo, per liberare risorse non gestite: `document.Dispose();`.

## Conclusione

Ora sai come **inserire una forma rettangolare** in un documento Word con C#, come **nascondere forma in Word** e come **creare una forma nascosta** che rimane parte della struttura del documento ma invisibile agli utenti finali. L’esempio completo e eseguibile dimostra l’intero flusso di lavoro, dalla creazione del documento alla verifica.

Successivamente, potresti esplorare **come nascondere forma** in base all’input dell’utente, o combinare forme nascoste con controlli di contenuto per una generazione dinamica di documenti. Puoi applicare la stessa tecnica ad altri tipi di forma come ellissi, frecce o disegni personalizzati.

Sentiti libero di sperimentare con dimensioni, colori e impostazioni di visibilità diversi. Se incontri problemi, rivedi i passaggi sopra o consulta la documentazione di Aspose.Words per approfondire i dettagli dell’API. Buon coding!

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell’API e a esplorare approcci alternativi di implementazione nei tuoi progetti.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}