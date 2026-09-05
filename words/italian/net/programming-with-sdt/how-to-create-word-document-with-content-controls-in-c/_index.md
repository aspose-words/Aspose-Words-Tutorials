---
category: general
date: 2026-09-05
description: Crea un documento Word con Aspose.Words, imposta il testo segnaposto,
  aggiungi un controllo e salva il documento come docx in C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- set placeholder text
- save document as docx
- how to add control
- how to create tag
language: it
lastmod: 2026-09-05
og_description: Crea un documento Word utilizzando Aspose.Words per .NET, imposta
  il testo segnaposto, aggiungi un controllo e salva il documento come docx. Segui
  questo tutorial completo.
og_image_alt: Screenshot showing a word document created with a content control placeholder
og_title: Crea un documento Word con controlli di contenuto in C# – guida passo passo
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create word document with Aspose.Words, set placeholder text, add control,
    and save document as docx in C#.
  headline: How to create word document with content controls in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Content Control
- Document Generation
title: Come creare un documento Word con controlli di contenuto in C#
url: /it/net/programming-with-sdt/how-to-create-word-document-with-content-controls-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come creare un documento Word con controlli di contenuto in C#

Se hai bisogno di **creare un documento Word** che includa controlli di contenuto strutturati, questa guida mostra come aggiungere un tag di testo semplice, **impostare il testo segnaposto** e **salvare il documento come docx** utilizzando Aspose.Words per .NET. L'esempio è completamente eseguibile e dimostra l'approccio consigliato per la generazione programmatica di Word.

Imparerai a:

* Inizializzare un file Word vuoto con `Document` e `DocumentBuilder`.
* **Come aggiungere un controllo** (un `StructuredDocumentTag`) al corpo del documento.
* **Come creare un tag** con un titolo e un segnaposto che guidano l'utente finale.
* Persistere il risultato con `document.Save`, assicurandoti che il file sia un valido `.docx`.

Il tutorial presuppone che tu abbia un ambiente di sviluppo C# di base e una licenza per Aspose.Words (la valutazione gratuita è sufficiente per scopi di apprendimento).

---

## Prerequisiti

| Requisito | Motivo |
|-------------|--------|
| .NET 6.0 o successivo | Fornisce il runtime per Aspose.Words per .NET. |
| Pacchetto NuGet Aspose.Words per .NET | Fornisce le classi `Document`, `DocumentBuilder` e `StructuredDocumentTag`. |
| IDE come Visual Studio 2022 | Rende più semplice eseguire e fare il debug del campione. |

Installa il pacchetto con la CLI di .NET:

```bash
dotnet add package Aspose.Words
```

---

## Passo 1: Configura il progetto per **creare un documento Word**

Crea un nuovo progetto console (o aggiungi il codice a uno esistente). Le prime righe istanziano un file Word vuoto e un `DocumentBuilder` che ti permette di scrivere contenuti.

```csharp
using Aspose.Words;
using Aspose.Words.Markup;

// Initialize a new empty document.
Document document = new Document();

// Obtain a builder positioned at the start of the document.
DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` rappresenta la struttura del file, mentre `DocumentBuilder` tiene traccia del punto di inserimento. Questo modello è la base per qualsiasi scenario di generazione di Word.

---

## Passo 2: **Come aggiungere un controllo** – crea un controllo di contenuto plain‑text (tag)

Un controllo di contenuto in Word è chiamato *structured document tag* (SDT). Il codice seguente crea un SDT di testo semplice, assegna un titolo e definisce il segnaposto che appare quando il documento viene aperto.

```csharp
// Create a plain‑text StructuredDocumentTag (SDT) at block level.
StructuredDocumentTag contentControl = new StructuredDocumentTag(
    document, SdtType.PlainText, MarkupLevel.Block);

// Assign a meaningful title – useful for later retrieval.
contentControl.Title = "CustomerName";

// Define the placeholder text that prompts the user.
contentControl.PlaceholderName = "Enter name";

// Insert the tag at the builder's current cursor location.
builder.InsertNode(contentControl);
```

**Perché è importante:**  
* La proprietà `Title` funge da identificatore stabile, consentendoti di localizzare o sostituire il controllo programmaticamente in seguito.  
* `PlaceholderName` fornisce una guida visiva al consumatore del documento senza richiedere codice UI aggiuntivo.

![Crea documento Word con segnaposto del controllo di contenuto](image.png)

*Testo alternativo dell'immagine: Crea documento Word con un controllo di contenuto che mostra il testo segnaposto.*

---

## Passo 3: Sposta il cursore all'interno del controllo e scrivi il testo predefinito

Dopo aver inserito il controllo, il cursore del builder punta ancora all'esterno. Sposta il cursore nel tag in modo che le scritture successive diventino parte del contenuto del controllo.

```csharp
// Position the builder inside the newly added content control.
builder.MoveTo(contentControl);

// Write default text that appears when the placeholder is cleared.
builder.Write("John Doe");
```

Se preferisci lasciare il controllo vuoto, ometti la chiamata a `Write`. Il segnaposto rimane visibile finché l'utente non digita un valore.

---

## Passo 4: **Imposta il testo segnaposto** (approccio alternativo)

A volte è necessario modificare il segnaposto dopo che il tag è stato creato. Puoi modificare direttamente la proprietà `PlaceholderName`:

```csharp
contentControl.PlaceholderName = "Type the customer's full name here";
```

Cambiare il segnaposto **non** influisce sul contenuto esistente, rendendo sicuro l'aggiornamento dei suggerimenti UI senza alterare i dati inseriti dall'utente.

---

## Passo 5: **Salva il documento come docx**

Persisti il documento in memoria su un file fisico. Il metodo `Save` determina automaticamente il formato dall'estensione del file.

```csharp
// Save the document in DOCX format.
document.Save("YOUR_DIRECTORY/SdtExample.docx");
```

Se ti serve un formato diverso (ad esempio PDF o HTML), fornisci un valore dell'enumerazione `SaveFormat`:

```csharp
document.Save("SdtExample.pdf", SaveFormat.Pdf);
```

---

## Passo 6: Esempio completo, eseguibile

Unendo tutti i pezzi ottieni un programma conciso che dimostra **come creare un tag**, impostarne il segnaposto e **salvare il documento come docx**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // 1. Initialize document and builder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2. Create a plain‑text content control (tag).
        StructuredDocumentTag sdt = new StructuredDocumentTag(
            document, SdtType.PlainText, MarkupLevel.Block);
        sdt.Title = "CustomerName";
        sdt.PlaceholderName = "Enter name";

        // 3. Insert the control and move inside it.
        builder.InsertNode(sdt);
        builder.MoveTo(sdt);

        // 4. Write default text (optional).
        builder.Write("John Doe");

        // 5. Save the file as DOCX.
        document.Save("SdtExample.docx");
        Console.WriteLine("Word document created successfully.");
    }
}
```

**Output previsto:**  
L'esecuzione del programma crea `SdtExample.docx` contenente un unico paragrafo con un controllo di contenuto plain‑text intitolato *CustomerName*. Il controllo mostra “John Doe” come contenuto iniziale; se il testo predefinito viene rimosso, il segnaposto “Enter name” appare in grigio chiaro quando il file è aperto in Microsoft Word.

---

## Variazioni comuni e casi limite

| Scenario | Regolazione consigliata |
|----------|------------------------|
| **Multiple controls** | Ripeti i passi 2‑4 per ogni campo, assegnando a ciascuno un `Title` unico. |
| **Rich‑text control** | Usa `SdtType.RichText` invece di `PlainText`. |
| **Repeating section** | Scegli `SdtType.RepeatingSection` e aggiungi controlli figli all'interno della sezione. |
| **Existing document** | Carica un file esistente con `new Document("template.docx")` e inserisci i controlli nella posizione desiderata. |
| **Unicode placeholder** | Imposta `PlaceholderName` a qualsiasi stringa Unicode; Word la renderizza correttamente. |
| **Large documents** | Dispone di `DocumentBuilder` dopo l'uso per liberare memoria (`builder.Dispose();`). |

**Suggerimento:** Quando devi recuperare il valore inserito dall'utente in seguito, chiama `StructuredDocumentTag.GetText()` dopo aver salvato e riaperto il documento. Questo metodo restituisce il testo interno senza il segnaposto.

**Attenzione a:** Usare un segnaposto che coincida con il testo predefinito può creare confusione, poiché Word nasconde il segnaposto quando è presente qualsiasi testo. Mantienili distinti.

---

## Conclusione

Ora sai **come creare un documento Word** programmaticamente, **come aggiungere un controllo**, **come creare un tag**, **impostare il testo segnaposto** e **salvare il documento come docx** usando Aspose.Words per .NET. L'esempio completo può essere copiato in qualsiasi progetto C# e ampliato per supportare tipi di controllo aggiuntivi, sezioni ripetitive o integrazioni con fonti di dati.

Passi successivi che potresti esplorare:

* Aggiungere **controlli di contenuto immagine** (`SdtType.Picture`) per incorporare grafiche fornite dall'utente.  
* Utilizzare **il binding** per mappare gli SDT a dati XML per scenari di stampa unione.  
* Convertire il DOCX generato in PDF (`SaveFormat.Pdf`) per la distribuzione.

Sperimenta con diversi tipi di tag e messaggi segnaposto per adattarli al flusso di lavoro della tua applicazione. Buon coding!

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Crea documento Word con Aspose.Words per .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Crea un documento Word con tabella usando Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)
- [Crea documento Word con intestazione e piè di pagina usando Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}