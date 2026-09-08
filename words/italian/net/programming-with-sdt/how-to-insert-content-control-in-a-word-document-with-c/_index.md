---
category: general
date: 2026-09-08
description: Scopri come inserire un controllo di contenuto in un documento Word usando
  C# e Aspose.Words. Include i passaggi per creare il controllo di contenuto, impostare
  il segnaposto e salvare il file.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert content control
- create content control
language: it
lastmod: 2026-09-08
og_description: Inserisci un controllo contenuto in un file Word usando C# e Aspose.Words.
  Segui questa guida per creare il controllo contenuto, impostare il testo segnaposto
  e salvare il documento.
og_image_alt: Insert content control example in a Word document
og_title: Inserire il controllo di contenuto in Word con C# – guida passo passo
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to insert content control in a Word document using C# and
    Aspose.Words. Includes steps to create content control, set placeholder, and save
    the file.
  headline: How to insert content control in a Word document with C#
  type: TechArticle
tags:
- content control
- Aspose.Words
- C#
- Word automation
title: Come inserire un controllo di contenuto in un documento Word con C#
url: /it/net/programming-with-sdt/how-to-insert-content-control-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come inserire un controllo contenuto in un documento Word con C#

Se hai bisogno di **inserire un controllo contenuto** in un documento Word, questa guida ti mostra una soluzione completa e funzionante. Imparerai anche come **creare un controllo contenuto** programmaticamente, impostare il testo segnaposto e scrivere il file su disco.

I controlli contenuto ti consentono di definire aree che gli utenti possono compilare, ripetere o bloccare. Sono ampiamente usati per modelli, moduli e report dinamici. I passaggi seguenti utilizzano la libreria Aspose.Words per .NET, che funziona con .NET 6+, .NET Framework 4.6+ e .NET Core.

## Come inserire un controllo contenuto in un documento Word

1. **Aggiungi Aspose.Words al tuo progetto**  
   Apri un terminale nella cartella del progetto ed esegui:

   ```bash
   dotnet add package Aspose.Words
   ```

   Il pacchetto contiene le classi `Document`, `DocumentBuilder` e `StructuredDocumentTag` necessarie per i controlli contenuto.

2. **Crea un nuovo documento vuoto**  

   ```csharp
   // Step 1: Create a new empty document and a DocumentBuilder
   Document doc = new Document();
   DocumentBuilder builder = new DocumentBuilder(doc);
   ```

   L'oggetto `Document` rappresenta l'intero file .docx, mentre `DocumentBuilder` fornisce un cursore comodo per inserire nodi.

## Creare un controllo contenuto con Aspose.Words

I controlli contenuto sono rappresentati dalla classe `StructuredDocumentTag` (SDT). Il codice seguente crea un controllo contenuto **plain‑text** e gli assegna un titolo che potrai interrogare in seguito.

```csharp
// Step 2: Create a plain‑text StructuredDocumentTag (content control)
//         - Set a title that can be used to identify the control
//         - Provide placeholder text that appears when the control is empty
StructuredDocumentTag sdt = new StructuredDocumentTag(
    doc,
    SdtType.PlainText,      // Plain‑text control
    MarkupLevel.Block);    // Block‑level control (behaves like a paragraph)

sdt.Title = "CustomerName";
sdt.PlaceholderName = "Enter name here";
```

*Perché è importante:*  
- `SdtType.PlainText` garantisce che il controllo accetti solo caratteri di testo semplice.  
- `MarkupLevel.Block` fa sì che il controllo si comporti come un intero paragrafo, ideale per campi di modulo.  
- La proprietà `Title` è un identificatore stabile che puoi usare durante la ricerca o il binding dei dati.

## Impostare segnaposto e testo predefinito

Un segnaposto guida l'utente prima che inizi a digitare. Puoi anche pre‑popolare il controllo con contenuto predefinito.

```csharp
// Step 4: Optionally set default content for the control
sdt.XmlMapping.SetXmlFragment("<text>John Doe</text>");
```

Il frammento XML deve corrispondere al tipo di dati del controllo. Per i controlli plain‑text, è richiesto l'elemento `<text>`. Se ometti questo passaggio, verrà mostrato il segnaposto definito in precedenza.

## Inserire il controllo contenuto nella posizione desiderata

Il cursore `DocumentBuilder` determina dove appare il controllo. Per impostazione predefinita, il cursore è all'inizio del documento.

```csharp
// Step 3: Insert the StructuredDocumentTag into the document at the builder's current position
builder.InsertNode(sdt);
```

Se hai bisogno del controllo all'interno di una tabella, intestazione o dopo paragrafi esistenti, sposta prima il builder:

```csharp
builder.MoveToDocumentEnd();   // Example: place the control at the end of the file
builder.InsertNode(sdt);
```

## Salvare il documento con il controllo contenuto inserito

```csharp
// Step 5: Save the document with the content control
doc.Save(@"C:\Temp\SDT.docx");
```

Il file `SDT.docx` ora contiene un controllo contenuto plain‑text intitolato **CustomerName** con il segnaposto “Enter name here” e il testo predefinito “John Doe”.

![Esempio di inserimento di un controllo contenuto in un documento Word](insert-content-control.png)

*Testo alternativo dell'immagine:* Esempio di inserimento di un controllo contenuto in un documento Word

### Risultato atteso

Quando apri `SDT.docx` in Microsoft Word:

- Apparirà un segnaposto grigio “Enter name here” se elimini il testo predefinito.  
- Il controllo sarà evidenziato quando ci clicchi dentro, indicando che può essere modificato.  
- La scheda **Developer** (se abilitata) mostrerà il titolo del controllo **CustomerName** nel pannello Proprietà.

## Esempio completo funzionante

Di seguito trovi un programma unico e autonomo che puoi copiare, compilare ed eseguire. Dimostra ogni passaggio, dalla configurazione del progetto al salvataggio del file.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class InsertContentControlDemo
{
    static void Main()
    {
        // 1. Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Create a plain‑text content control (StructuredDocumentTag)
        StructuredDocumentTag sdt = new StructuredDocumentTag(
            doc,
            SdtType.PlainText,
            MarkupLevel.Block);

        sdt.Title = "CustomerName";          // Identifier for later use
        sdt.PlaceholderName = "Enter name here";

        // 3. Insert the control at the current cursor position
        builder.InsertNode(sdt);

        // 4. Set default text (optional)
        sdt.XmlMapping.SetXmlFragment("<text>John Doe</text>");

        // 5. Save the document
        string outputPath = @"C:\Temp\SDT.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Esegui il programma con `dotnet run`. Dopo l'esecuzione, apri il file generato per verificare che il controllo contenuto appaia come descritto.

## Consigli pratici e problemi comuni

| Situazione | Approccio consigliato |
|-----------|----------------------|
| **Controlli multipli dello stesso tipo** | Assegna a ogni controllo un `Title` unico. Puoi recuperare un controllo in seguito con `doc.GetChildNodes(NodeType.StructuredDocumentTag, true).Cast<StructuredDocumentTag>().FirstOrDefault(s => s.Title == "YourTitle")`. |
| **Controllo non visibile in Word** | Assicurati di aver salvato il documento con estensione `.docx` e che la versione di `Aspose.Words` sia compatibile con la tua versione di Office. |
| **Necessità di un controllo rich‑text** | Usa `SdtType.RichText` invece di `PlainText`. Il frammento XML utilizzerà quindi elementi `<w:richText>`. |
| **Posizionare il controllo all'interno di una cella di tabella** | Sposta prima il builder nella cella: `builder.MoveTo(cell.FirstParagraph); builder.InsertNode(sdt);`. |
| **Prestazioni con documenti di grandi dimensioni** | Crea il `StructuredDocumentTag` una sola volta e riutilizzalo se ti servono molti controlli identici; clonalalo tramite `sdt.Clone(true)`. |

## Prossimi passi

- **Creare controlli contenuto ripetibili** (`SdtType.RepeatingSection`) per tabelle che crescono dinamicamente.  
- **Associare controlli contenuto a dati XML** usando `sdt.XmlMapping.LoadXml(xmlString)`.  
- **Bloccare il controllo** (`sdt.LockContentControl = true`) per impedire modifiche da parte dell'utente mantenendo gli aggiornamenti programmatici.  

Esplorare questi argomenti approfondirà la tua capacità di costruire modelli Word robusti con Aspose.Words.

---

**Conclusione**  
Ora sai come **inserire un controllo contenuto** in un documento Word usando C#. Il tutorial ha coperto la creazione del controllo, l'impostazione del segnaposto e del testo predefinito, l'inserimento nella posizione desiderata e il salvataggio del file finale. Con questa base potrai creare moduli sofisticati, modelli di stampa unione e report automatizzati che sfruttano le funzionalità native dei controlli contenuto di Word.

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi con spiegazioni passo‑passo per aiutarti a padroneggiare ulteriori funzionalità dell'API e a esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Set Content Control Style](/words/english/net/programming-with-sdt/set-content-control-style/)
- [Set Content Control Color](/words/english/net/programming-with-sdt/set-content-control-color/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}