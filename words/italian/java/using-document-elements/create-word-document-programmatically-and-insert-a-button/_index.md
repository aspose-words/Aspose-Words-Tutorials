---
category: general
date: 2026-09-21
description: Crea un documento Word programmaticamente e impara come salvare il pulsante
  del documento Word, inserire il pulsante di comando Word e impostare la didascalia
  del pulsante di comando usando DocumentBuilder.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- save word document button
- insert command button word
- set command button caption
- how to use documentbuilder
language: it
lastmod: 2026-09-21
og_description: Crea documenti Word programmaticamente con Aspose.Words. Scopri come
  salvare il documento Word con un pulsante, inserire un pulsante di comando, impostare
  la didascalia del pulsante di comando e utilizzare DocumentBuilder per moduli interattivi.
og_image_alt: Screenshot of a Word file that contains an inserted CommandButton created
  programmatically
og_title: Crea un documento Word programmaticamente e aggiungi un pulsante
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create word document programmatically and learn how to save word document
    button, insert command button word, and set command button caption using DocumentBuilder.
  headline: Create word document programmatically and insert a button
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word Automation
title: Crea un documento Word programmaticamente e inserisci un pulsante
url: /it/java/using-document-elements/create-word-document-programmatically-and-insert-a-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Creare un documento Word programmaticamente e inserire un pulsante

Se hai bisogno di **creare un documento Word programmaticamente**, Aspose.Words fornisce un'API fluida che ti consente di aggiungere controlli interattivi come un CommandButton. Questo tutorial spiega anche **come utilizzare DocumentBuilder**, come **salvare il pulsante del documento Word**, e come **impostare la didascalia del pulsante di comando** in modo che il pulsante appaia esattamente come ti aspetti all'interno del file .docx.

Imparerai a:

* Inizializzare un documento vuoto con `Document`.
* Lavorare con `DocumentBuilder` per modificare il documento.
* Inserire un **CommandButton** (`insert command button word`).
* Impostare il nome del pulsante e la didascalia visibile (`set command button caption`).
* Persistire il risultato su disco (`save word document button`).

I passaggi sono scritti per sviluppatori .NET che usano C# e l'ultima versione di Aspose.Words per .NET (v24.10). Non sono necessari pacchetti NuGet aggiuntivi oltre a Aspose.Words.

---

## Cosa ti serve prima di iniziare

| Prerequisito | Motivo |
|--------------|--------|
| Visual Studio 2022 (o qualsiasi IDE C#) | Per compilare ed eseguire il codice di esempio. |
| .NET 6.0 SDK o successivo | Fornisce l'ambiente di esecuzione per l'esempio. |
| Aspose.Words per .NET (v24.10 o più recente) | La libreria che ti consente di **creare un documento Word programmaticamente** e manipolare i controlli del modulo. |
| Familiarità di base con C# e i concetti OOP | Necessario per comprendere il flusso del codice. |

Puoi installare Aspose.Words via NuGet:

```bash
dotnet add package Aspose.Words
```

---

## Creare un documento Word programmaticamente

Il primo passo è istanziare un `Document` vuoto. Questo oggetto rappresenta l'intero file Word in memoria.

```csharp
// Step 1: Create a new blank document
Document doc = new Document();
```

Creare il documento programmaticamente ti fornisce una tela pulita su cui puoi aggiungere paragrafi, tabelle o controlli interattivi.  

---

## Come utilizzare DocumentBuilder

`DocumentBuilder` è la classe principale per modificare un `Document`. Fornisce metodi per inserire testo, immagini e campi modulo. In questo tutorial lo usiamo per posizionare un CommandButton.

```csharp
// Step 2: Initialize a DocumentBuilder to edit the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

Il builder mantiene un cursore interno che punta alla posizione di inserimento corrente. Per impostazione predefinita inizia all'inizio della prima sezione, il che è ideale per il nostro esempio.

---

## Inserire un CommandButton in Word

Aspose.Words tratta un CommandButton come un controllo ActiveX. Il metodo `InsertForms2OleControl` crea un controllo OLE generico che poi configuriamo come pulsante.

```csharp
// Step 3: Insert an ActiveX Forms2OleControl (a CommandButton)
Forms2OleControl commandButton = builder.InsertForms2OleControl();
```

A questo punto il controllo esiste nel documento ma non ha una rappresentazione visiva finché non definiamo il suo tipo.

---

## Impostare la didascalia del CommandButton

Ora diciamo al controllo OLE che deve comportarsi come un CommandButton e gli assegniamo un'etichetta amichevole.

```csharp
// Step 4: Define the control as a CommandButton
commandButton.SetControlType(Forms2OleControlType.COMMANDBUTTON);

// Step 5: Set a unique name for the button (used for identification)
commandButton.SetName("btnSubmit");

// Step 6: Set the visible caption that appears on the button
commandButton.SetCaption("Submit");
```

Impostare la **didascalia del pulsante di comando** è essenziale perché Word visualizza questo testo sulla superficie del pulsante. Se ometti `SetCaption`, il pulsante apparirà con un'etichetta generica.

---

## Salvare il documento Word con il pulsante

Infine, persisti il documento su disco. Il metodo `Save` scrive l'intero pacchetto Word, incluso il pulsante appena inserito, in un file .docx.

```csharp
// Step 7: Save the document containing the CommandButton
doc.Save("YOUR_DIRECTORY/CommandButton.docx");
```

Il file `CommandButton.docx` ora contiene un pulsante pienamente funzionante etichettato **Submit**. Quando l'utente apre il file in Microsoft Word e clicca sul pulsante, verrà attivata l'azione predefinita (che potrai successivamente collegare via VBA).

---

## Esempio completo funzionante

Di seguito trovi il programma completo che puoi copiare, incollare ed eseguire. Dimostra l'intero flusso di lavoro dalla creazione del documento al salvataggio del pulsante.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Initialize DocumentBuilder (how to use DocumentBuilder)
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a CommandButton (insert command button word)
        Forms2OleControl commandButton = builder.InsertForms2OleControl();

        // 4. Define the control type as CommandButton
        commandButton.SetControlType(Forms2OleControlType.COMMANDBUTTON);

        // 5. Give the button a unique name (optional but useful)
        commandButton.SetName("btnSubmit");

        // 6. Set the visible caption (set command button caption)
        commandButton.SetCaption("Submit");

        // 7. Save the document (save word document button)
        string outputPath = @"C:\Temp\CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Risultato atteso**

* Un file chiamato `CommandButton.docx` nella cartella specificata.
* Aprendo il file in Microsoft Word verrà mostrato un unico pulsante **Submit** nella prima pagina.
* Il pulsante può essere selezionato, ridimensionato o collegato a una macro dalla scheda **Developer** di Word.

---

## Domande comuni e gestione dei casi limite

| Domanda | Risposta |
|----------|--------|
| *E se ho bisogno di più di un pulsante?* | Ripeti i passaggi 3–6 con nomi e didascalie diversi. Ogni pulsante deve avere un valore `SetName` unico. |
| *Posso impostare le dimensioni del pulsante?* | Sì. Dopo aver inserito il controllo, puoi modificare le proprietà `Width` e `Height` tramite l'oggetto `OleFormat`. |
| *Il pulsante funzionerà su tutte le versioni di Word?* | I controlli ActiveX sono supportati nella versione desktop di Word (Windows). Non vengono renderizzati in Word Online o su macOS. |
| *Come aggiungere un gestore di click?* | Devi scrivere codice VBA che faccia riferimento al nome del pulsante (`btnSubmit`). La macro VBA può essere incorporata usando `doc.VbaProject`. |
| *E se devo inserire il pulsante all'interno di una cella di tabella?* | Sposta il cursore del builder nella cella desiderata (`builder.MoveTo(cell.FirstParagraph)`) prima di chiamare `InsertForms2OleControl`. |

---

## Consigli professionali

* **Consiglio pro:** Imposta sempre un nome significativo con `SetName`. Semplifica l'automazione VBA e rende il debug più facile.
* **Attenzione a:** Dimenticare di chiamare `SetControlType`. Senza questa chiamata l'oggetto OLE appare come un segnaposto generico anziché come un pulsante cliccabile.
* **Suggerimento sulle prestazioni:** Se generi molti documenti in un ciclo, riutilizza un'unica istanza di `DocumentBuilder` e chiama `builder.MoveToDocumentEnd()` prima di ogni inserimento per evitare reset inutili del cursore.

---

## Prossimi passi

Ora che sai come **creare un documento Word programmaticamente**, **inserire un CommandButton in Word**, **impostare la didascalia del pulsante di comando** e **salvare il documento Word con il pulsante**, puoi esplorare scenari più avanzati:

* Aggiungi controlli **TextFormField** per l'input dell'utente.
* Combina i pulsanti con campi **MacroButton** per eseguire VBA direttamente.
* Usa **DocumentBuilder.InsertImage** per posizionare icone sui tuoi pulsanti.
* Integra con ASP.NET per generare moduli Word su

## Cosa dovresti imparare dopo?

I tutorial seguenti coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell'API ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Crea nuovo documento Word](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Crea documento Word con Aspose.Words per .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Inserisci immagine in linea in documento Word usando Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}