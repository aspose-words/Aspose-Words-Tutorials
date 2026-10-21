---
category: general
date: 2026-09-21
description: Scopri come generare un modello di documento, popolare un modello Word
  e sostituire i segnaposto in un file DOCX usando C# – guida passo passo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- generate document template
- populate word template
- how to replace placeholder
- fill docx template
- replace text docx
language: it
lastmod: 2026-09-21
og_description: Genera un modello di documento in C# popolando un modello Word, sostituendo
  i segnaposto e salvando un file DOCX compilato. Segui questa guida completa.
og_image_alt: Screenshot of a C# program generating and filling a DOCX template
og_title: Genera modello di documento in C# – riempi i file DOCX con i dati
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to generate document template, populate word template and
    replace placeholders in a DOCX file using C# – step‑by‑step guide.
  headline: How to generate document template and fill it with data in C#
  type: TechArticle
tags:
- C#
- DOCX
- template processing
title: Come generare un modello di documento e riempirlo con i dati in C#
url: /it/net/find-and-replace-text/how-to-generate-document-template-and-fill-it-with-data-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come generare un modello di documento e riempirlo con dati in C#

Se hai bisogno di **generare modelli di documento** che possano essere riutilizzati per fatture, contratti o report, questa guida ti mostra esattamente come fare. Imparerai a **popolare template Word** segnaposto, sostituirli con valori reali e infine **riempire template docx** programmaticamente.

Creare un modello riutilizzabile elimina il copia‑incolla manuale e garantisce coerenza in tutti i documenti generati. I passaggi seguenti funzionano con qualsiasi file `.docx` che contenga semplici token segnaposto come `{{Name}}`.

## Prerequisiti

Prima di iniziare, assicurati di avere:

* .NET 6.0 SDK o versioni successive installato  
* Visual Studio 2022 (o qualsiasi IDE tu preferisca)  
* Il pacchetto NuGet **Aspose.Words for .NET** – fornisce la classe `Document` usata nell’esempio  

Puoi aggiungere il pacchetto con il seguente comando:

```bash
dotnet add package Aspose.Words
```

## Passo 1: Preparare il modello Word

Crea un documento Word (`Template.docx`) che contenga segnaposto dove dovrebbero apparire i dati dinamici. Una convenzione comune è l’uso di doppie parentesi graffe:

```
Dear {{Name}},

Your order #{{OrderId}} has been shipped on {{ShipDate}}.
```

Salva il file in una cartella a cui puoi fare riferimento dal codice, ad esempio `C:\Docs\Template.docx`.

## Passo 2: Caricare il documento modello

La prima azione programmatica è caricare il modello in memoria. Il costruttore `Document` legge il file e costruisce un modello di oggetti che puoi manipolare.

```csharp
using System;
using Aspose.Words;

class Program
{
    static void Main()
    {
        // Load the template document from disk
        string templatePath = @"C:\Docs\Template.docx";
        Document doc = new Document(templatePath);
```

**Perché è importante:** Caricare il file crea una copia pulita ogni volta, così il modello originale rimane intatto per esecuzioni future.

## Passo 3: Sostituire i segnaposto con dati reali

Aspose.Words fornisce un semplice metodo `Range.Replace` che scansiona il documento alla ricerca di una stringa specifica e la sostituisce. Avvolgi la chiamata in un metodo di supporto per mantenere il flusso principale ordinato.

```csharp
        // Helper to replace a single placeholder
        void ReplacePlaceholder(string placeholder, string value)
        {
            // The placeholder includes the curly braces exactly as they appear in the template
            doc.Range.Replace(placeholder, value, new FindReplaceOptions());
        }

        // Populate the template with real values
        ReplacePlaceholder("{{Name}}", "John Doe");
        ReplacePlaceholder("{{OrderId}}", "A12345");
        ReplacePlaceholder("{{ShipDate}}", DateTime.Today.ToString("MMMM d, yyyy"));
```

**Come funziona:** `Range.Replace` attraversa ogni paragrafo, cella di tabella, intestazione e piè di pagina, assicurandosi che tutte le occorrenze del token vengano aggiornate. Questo è il modo più affidabile per **how to replace placeholder** testo in un file DOCX.

### Gestione di più occorrenze e token mancanti

* Se un segnaposto appare più di una volta, `Replace` aggiorna automaticamente tutte le istanze.  
* Se un segnaposto è assente, il metodo semplicemente non fa nulla—non viene sollevata alcuna eccezione.  
* Per documenti di grandi dimensioni, puoi migliorare le prestazioni disabilitando `doc.UpdateFields()` fino al completamento di tutte le sostituzioni.

## Passo 4: Salvare il documento riempito

Una volta sostituiti tutti i segnaposto, scrivi il risultato in un nuovo file. Tenere l’output separato preserva il modello originale per esecuzioni future.

```csharp
        // Save the filled document to a new file
        string outputPath = @"C:\Docs\FilledTemplate.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Risultato:** `FilledTemplate.docx` ora contiene il contenuto personalizzato:

```
Dear John Doe,

Your order #A12345 has been shipped on September 21, 2026.
```

## Passo 5: Verificare l'output (opzionale)

Se vuoi confermare programmaticamente che le sostituzioni siano avvenute correttamente, puoi leggere nuovamente il file salvato e cercare i valori attesi:

```csharp
        Document verifyDoc = new Document(outputPath);
        bool nameReplaced = verifyDoc.Range.Text.Contains("John Doe");
        Console.WriteLine($"Name replacement successful: {nameReplaced}");
```

L’esecuzione del passaggio di verifica stampa `true` quando il segnaposto è stato sostituito correttamente.

## Problemi comuni e consigli di best‑practice

| Problema | Perché accade | Correzione consigliata |
|----------|----------------|------------------------|
| **I segnaposto contengono spazi extra** | `"{{ Name }}"` non corrisponde a `"{{Name}}"`. | Mantieni i token segnaposto privi di spazi, oppure rimuovi gli spazi su entrambi i lati prima della sostituzione. |
| **Word aggiunge formattazione nascosta** | Word può memorizzare il segnaposto diviso in più run, facendo sì che `Replace` lo salti. | Usa `Document.Range.Replace` con `FindReplaceOptions` impostato a `MatchCase = false` e `FindWholeWordsOnly = false`. |
| **Documenti grandi causano rallentamenti** | Sostituire i token uno alla volta attiva una scansione completa del documento ogni volta. | Esegui le sostituzioni in batch in un unico passaggio chiamando `Range.Replace` per ciascun token prima di salvare. |
| **Salvataggio in una cartella di sola lettura** | `doc.Save` genera un `UnauthorizedAccessException`. | Assicurati che la directory di destinazione abbia permessi di scrittura, oppure scegli un percorso scrivibile dall’utente (es. `%TEMP%`). |

## Esempio completo funzionante

Di seguito trovi il programma completo, autonomo, che puoi copiare, incollare ed eseguire.

```csharp
using System;
using Aspose.Words;

class Program
{
    static void Main()
    {
        // Paths – adjust to your environment
        string templatePath = @"C:\Docs\Template.docx";
        string outputPath   = @"C:\Docs\FilledTemplate.docx";

        // 1️⃣ Load the template document
        Document doc = new Document(templatePath);

        // 2️⃣ Replace placeholders
        void Replace(string placeholder, string value) =>
            doc.Range.Replace(placeholder, value, new FindReplaceOptions());

        Replace("{{Name}}", "John Doe");
        Replace("{{OrderId}}", "A12345");
        Replace("{{ShipDate}}", DateTime.Today.ToString("MMMM d, yyyy"));

        // 3️⃣ Save the filled document
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");

        // 4️⃣ (Optional) Verify replacement
        Document verify = new Document(outputPath);
        Console.WriteLine($"Verification – name found: {verify.Range.Text.Contains("John Doe")}");
    }
}
```

**Output console previsto**

```
Document saved to C:\Docs\FilledTemplate.docx
Verification – name found: True
```

Apri `FilledTemplate.docx` in Microsoft Word per vedere il testo personalizzato.

## Conclusione

Ora sai come **generare modelli di documento**, **popolare template Word** e **riempire template docx** sostituendo i token **how to replace placeholder** con dati reali. L’approccio funziona per qualsiasi numero di segnaposto e scala a documenti di grandi dimensioni se segui i consigli di best‑practice.

### Cosa fare dopo?

* **Tabelle dinamiche:** Usa `DocumentBuilder` per inserire righe basate su collezioni.  
* **Sezioni condizionali:** Nascondi o mostra parti del modello con campi `IF`.  
* **Esportazione PDF:** Chiama `doc.Save("output.pdf")` per creare una versione PDF del documento riempito.  

Sperimenta con queste varianti per costruire un motore di generazione documenti completo per fatture, contratti o qualsiasi report ripetibile.

---


## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell’API ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Documento Word - Trova e sostituisci testo](/words/english/net/find-and-replace-text/)
- [Genera documento Word](/words/english/java/word-processing/generate-word-document/)
- [Recupera DOCX corrotto – Apri e carica documento Word](/words/english/python-net/document-operations/recover-corrupted-docx-open-load-word-document/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}