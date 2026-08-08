---
category: general
date: 2026-08-07
description: Come creare un controllo di contenuto in C# usando Aspose.Words – impara
  come aggiungere SDT, impostare il segnaposto, scrivere il testo predefinito e inserire
  un controllo di testo semplice.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to create content control
- how to add sdt
- how to set placeholder
- how to write default text
- insert plain text control
language: it
lastmod: 2026-08-07
og_description: Come creare un controllo di contenuto in C# con Aspose.Words. Questo
  tutorial mostra come aggiungere SDT, impostare il segnaposto, scrivere il testo
  predefinito e inserire un controllo di testo semplice.
og_image_alt: Screenshot of a Word document showing a plain‑text content control with
  placeholder text
og_title: Come creare un controllo di contenuto in C# – guida completa ad Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to create content control in C# using Aspose.Words – learn how
    to add SDT, set placeholder, write default text, and insert plain text control.
  headline: How to create content control in C# with Aspose.Words
  type: TechArticle
- description: How to create content control in C# using Aspose.Words – learn how
    to add SDT, set placeholder, write default text, and insert plain text control.
  name: How to create content control in C# with Aspose.Words
  steps:
  - name: Expected output
    text: '- A `.docx` file on the desktop named `CustomerNameControl.docx`. - Inside
      the file, a single content control containing the text **John Doe**. - The placeholder
      text appears in light gray until the user types a new value.'
  - name: Adding multiple content controls
    text: You can repeat the **how to add sdt** steps to insert several controls in
      the same document. Just create a new `StructuredDocumentTag` for each field
      and move the builder accordingly.
  - name: Reading a placeholder programmatically
    text: 'If you need to verify that a placeholder was set correctly, inspect the
      `PlaceholderName` property:'
  - name: Using other SDT types
    text: Aspose.Words supports dropdown lists, date pickers, and rich‑text controls.
      Replace `SdtType.PlainText` with `SdtType.DropDownList` or `SdtType.RichText`
      to change the control type.
  type: HowTo
tags:
- Aspose.Words
- C#
- Content Control
- SDT
title: Come creare un controllo di contenuto in C# con Aspose.Words
url: /it/net/programming-with-sdt/how-to-create-content-control-in-c-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come creare un controllo contenuto in C# con Aspose.Words

Se hai bisogno di **come creare un controllo contenuto** in un documento Word in modo programmatico, questa guida ti mostra esattamente come fare. Vedrai come aggiungere un SDT, impostare un segnaposto, scrivere testo predefinito e inserire un controllo di testo semplice—tutto con Aspose.Words per .NET.

Il tutorial copre ogni passaggio, dalla configurazione del progetto al salvataggio del file finale `.docx`. Alla fine sarai in grado di generare documenti che contengono controlli contenuto completamente configurati, pronti per l'elaborazione successiva o per l'interazione dell'utente.

## Prerequisiti

Prima di iniziare, assicurati di avere:

- .NET 6.0 o successivo (il codice funziona anche con .NET Framework 4.7+)
- Una licenza Aspose.Words per .NET o una chiave di valutazione temporanea
- Visual Studio 2022 (o qualsiasi IDE che supporti C#)
- Familiarità di base con la sintassi C#

Non sono richiesti pacchetti NuGet aggiuntivi oltre a `Aspose.Words`.

## Come creare un controllo contenuto – passo 1: configurare il progetto

Crea una nuova applicazione console e aggiungi il pacchetto Aspose.Words:

```bash
dotnet new console -n ContentControlDemo
cd ContentControlDemo
dotnet add package Aspose.Words
```

Il processo di **come creare un controllo contenuto** inizia con un nuovo oggetto `Document`. Questo oggetto rappresenta il file Word che manipolerai.

```csharp
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Initialize a blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

> **Suggerimento:** Mantieni viva l'istanza di `DocumentBuilder` per l'intero ciclo di vita del documento; ricrearla inutilmente aggiunge overhead.

## Come aggiungere SDT – passo 2: inserire un Structured Document Tag di testo semplice

Un SDT (Structured Document Tag) è il nome tecnico per un controllo contenuto. Per **come aggiungere sdt**, istanzia un `StructuredDocumentTag` con il tipo desiderato.

```csharp
        // Create a plain‑text SDT (content control)
        StructuredDocumentTag sdt = new StructuredDocumentTag(
            document,
            SdtType.PlainText,   // Plain‑text control
            true);               // Is it a repeating section? false for single use

        // Give the control a title – this is how you reference it later
        sdt.Title = "CustomerName";

        // Insert the SDT at the current cursor position
        builder.InsertNode(sdt);
```

L'opzione `SdtType.PlainText` crea una semplice casella di testo che gli utenti possono modificare. Impostare la proprietà `Title` ti aiuta a individuare il controllo quando devi recuperare o modificare il suo contenuto in seguito.

## Come impostare il segnaposto – passo 3: configurare il testo segnaposto

Un segnaposto guida l'utente finale mostrando un testo di esempio prima che inizi a digitare. Per **come impostare il segnaposto**, assegna la proprietà `PlaceholderName`.

```csharp
        // Define the placeholder that appears when the control is empty
        sdt.PlaceholderName = "Enter name here";
```

Quando il documento si apre in Microsoft Word, il testo grigio del segnaposto appare all'interno del controllo finché l'utente non fornisce un valore.

## Come scrivere testo predefinito – passo 4: aggiungere contenuto iniziale all'interno dell'SDT

Se vuoi che il controllo contenga contenuto predefinito, devi spostare il builder all'interno dell'SDT e scrivere il testo. Questo dimostra **come scrivere testo predefinito**.

```csharp
        // Position the builder inside the SDT so we can add content
        builder.MoveTo(sdt);

        // Write the default text that will be visible initially
        builder.Write("John Doe");
```

La chiamata a `MoveTo` cambia la posizione del cursore all'interno dell'SDT. Dopo `Write`, il controllo mostra “John Doe” come valore iniziale.

## Inserire controllo di testo semplice – passo 5: salvare il documento

Infine, persisti il documento su disco. Questo completa l'operazione di **inserimento controllo di testo semplice**.

```csharp
        // Save the document with the content control embedded
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "CustomerNameControl.docx");

        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Quando apri `CustomerNameControl.docx` in Word, vedrai un controllo di testo semplice intitolato **CustomerName**, con il segnaposto “Enter name here” e il testo predefinito “John Doe”.

### Output previsto

- Un file `.docx` sul desktop chiamato `CustomerNameControl.docx`.
- All'interno del file, un singolo controllo contenuto che contiene il testo **John Doe**.
- Il testo segnaposto appare in grigio chiaro finché l'utente non digita un nuovo valore.

## Variazioni aggiuntive e casi limite

### Aggiungere più controlli contenuto

Puoi ripetere i passaggi di **come aggiungere sdt** per inserire diversi controlli nello stesso documento. Basta creare un nuovo `StructuredDocumentTag` per ogni campo e spostare il builder di conseguenza.

```csharp
// Example: add a second control for "OrderNumber"
StructuredDocumentTag orderTag = new StructuredDocumentTag(document, SdtType.PlainText, true);
orderTag.Title = "OrderNumber";
orderTag.PlaceholderName = "Enter order #";
builder.InsertNode(orderTag);
builder.MoveTo(orderTag);
builder.Write("12345");
```

### Leggere programmaticamente un segnaposto

Se devi verificare che un segnaposto sia stato impostato correttamente, ispeziona la proprietà `PlaceholderName`:

```csharp
string placeholder = sdt.PlaceholderName; // returns "Enter name here"
```

### Utilizzare altri tipi di SDT

Aspose.Words supporta liste a discesa, selettori di data e controlli di testo ricco. Sostituisci `SdtType.PlainText` con `SdtType.DropDownList` o `SdtType.RichText` per cambiare il tipo di controllo.

## Problemi comuni e come evitarli

| Sintomo | Causa | Soluzione |
|---------|-------|-----------|
| Il segnaposto non appare mai | Il documento è stato salvato prima che il segnaposto fosse assegnato | Assicurati che `PlaceholderName` sia impostato **prima** di chiamare `Save`. |
| Il testo predefinito manca | Il builder non è stato spostato all'interno dell'SDT | Chiama `builder.MoveTo(sdt)` prima di `builder.Write`. |
| Il titolo del controllo è vuoto | Proprietà `Title` non impostata | Assegna sempre un `Title` significativo per il recupero successivo. |

## Conclusione

Ora sai **come creare un controllo contenuto** in C# usando Aspose.Words, inclusi **come aggiungere sdt**, **come impostare il segnaposto**, **come scrivere testo predefinito** e **inserire controllo di testo semplice**. L'esempio completo si compila in un file Word pronto all'uso che dimostra ciascun concetto.

Da qui puoi esplorare scenari più avanzati, come collegare i controlli contenuto a dati XML, gestire sezioni ripetute o convertire il documento in PDF mantenendo i controlli. Ognuno di questi argomenti si basa direttamente sui fondamenti trattati in questo tutorial.

Buon coding!

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Rich Text Box Content Control](/words/hindi/net/programming-with-sdt/rich-text-box-content-control/)
- [Rich Text Box Content Control](/words/hongkong/net/programming-with-sdt/rich-text-box-content-control/)
- [Rich Text Box Content Control](/words/spanish/net/programming-with-sdt/rich-text-box-content-control/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}