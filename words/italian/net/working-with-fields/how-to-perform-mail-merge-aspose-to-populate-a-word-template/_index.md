---
category: general
date: 2026-09-11
description: Mail merge di Aspose consente di caricare un modello Word e di popolarlo
  con i dati, automatizzando la generazione di documenti per creare lettere personalizzate.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- mail merge aspose
- populate word template
- load word template
- automate document generation
- create personalized letters
language: it
lastmod: 2026-09-11
og_description: Mail merge di Aspose ti consente di caricare un modello Word e di
  popolarlo, semplificando la generazione dei documenti così da poter creare rapidamente
  lettere personalizzate.
og_image_alt: Screenshot of C# code using Aspose.Words to perform a mail merge on
  a Word template
og_title: 'Mail merge Aspose: popola un modello Word in pochi minuti'
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Mail merge aspose lets you load word template and populate word template
    with data, automating document generation for creating personalized letters.
  headline: How to perform mail merge aspose to populate a Word template
  type: TechArticle
tags:
- Aspose.Words
- C#
- document automation
title: Come eseguire il mail merge con Aspose per popolare un modello Word
url: /it/net/working-with-fields/how-to-perform-mail-merge-aspose-to-populate-a-word-template/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come eseguire il mail merge aspose per popolare un modello Word

Se hai bisogno di **mail merge aspose** per generare un batch di lettere personalizzate, questa guida ti mostra esattamente come caricare un modello Word, popolarlo con i dati e automatizzare la generazione dei documenti in poche righe di C#. Che tu stia costruendo un sistema di mailing o uno strumento di reporting, l'esempio completo qui sotto ti consente di creare lettere personalizzate senza scrivere alcuna logica di merge manuale.

Imparerai come **caricare il modello Word**, utilizzare la classe low‑code `MailMerger` e **popolare il modello Word** con una fonte di dati anonima. Alla fine del tutorial avrai un'app console pronta all'uso che produce un documento Word unito che puoi inviare via email, stampare o archiviare.

## Prerequisiti

* SDK .NET 6.0 o successivo installato  
* Una licenza valida di Aspose.Words per .NET (o una chiave di valutazione gratuita)  
* Il pacchetto NuGet `Aspose.Words` (versione 23.10 o più recente) installato nel tuo progetto  
* Un file Word (`MailMergeTemplate.docx`) che contiene segnaposti MERGEFIELD come **«Name»** e **«Age»**  

Puoi creare il modello in Microsoft Word inserendo *Insert → Quick Parts → Field → MergeField* e denominando i campi esattamente come i nomi delle proprietà nella tua fonte di dati.

## Passo 1 – Preparare la fonte di dati per il mail merge

Il merge low‑code funziona con qualsiasi collezione enumerabile. In questo esempio utilizziamo un array di oggetti anonimi, ma potresti anche passare un `DataTable`, una lista di POCO o dati letti da un database.

```csharp
using Aspose.Words;
using Aspose.Words.LowCode;

// Sample data that will replace the MERGEFIELDs in the template
var data = new[]
{
    new { Name = "Alice",   Age = 30 },
    new { Name = "Bob",     Age = 45 },
    new { Name = "Charlie", Age = 28 }
};
```

**Perché è importante:**  
Il nome della proprietà di ogni oggetto (`Name`, `Age`) deve corrispondere a un MERGEFIELD nel modello. La classe `MailMerger` mappa automaticamente le proprietà ai campi, eliminando la necessità di eventi manuali `FieldMerging`.

## Passo 2 – Caricare il modello Word che contiene MERGEFIELD

Caricare il modello è semplice con la classe `Document`. Il percorso può essere assoluto o relativo alla directory di lavoro dell'eseguibile.

```csharp
// Load the Word template that contains MERGEFIELDs
Document template = new Document("YOUR_DIRECTORY/MailMergeTemplate.docx");
```

**Consiglio professionale:**  
Se esegui il codice da Visual Studio, imposta *Copy to Output Directory* per il file modello su **Copy always**. Questo garantisce che il file sia disponibile quando il binario compilato viene eseguito.

## Passo 3 – Creare un'istanza di MailMerger legata al modello

La classe `MailMerger` si trova nello spazio dei nomi `Aspose.Words.LowCode` e fornisce un unico metodo `Execute` che accetta la fonte di dati.

```csharp
// Bind the template to a MailMerger instance
MailMerger merger = new MailMerger(template);
```

**Perché usare MailMerger?**  
`MailMerger` astrae le chiamate boilerplate `MailMerge.Execute`, gestendo internamente il rilevamento dei campi, il binding dei dati e la clonazione del documento. Questo rende il codice ideale per scenari di **automazione della generazione di documenti** dove desideri una soluzione pulita e low‑code.

## Passo 4 – Eseguire il merge low‑code utilizzando i dati preparati

Eseguendo `Execute` si ottiene un nuovo `Document` che contiene

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche illustrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare ulteriori funzionalità dell'API ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Rinominare i campi di merge Word con Aspose.Words per Java](/words/english/java/mail-merge-reporting/rename-word-merge-fields-aspose-words-java/)
- [Creare un documento Word con intestazione e piè di pagina usando Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Creare e formattare un documento Word in Aspose.Words per .NET](/words/english/net/document-styling/apply-paragraph-style/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}