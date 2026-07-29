---
category: general
date: 2026-07-29
description: Aggiungi un pulsante di comando a un documento Word usando Aspose.Words.
  Scopri come impostare le proprietà del controllo ActiveX e impostare la didascalia
  del pulsante di comando in pochi semplici passaggi.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add command button to word document
- set activex control properties
- set command button caption
- Aspose.Words ActiveX example
- C# insert ActiveX control
language: it
lastmod: 2026-07-29
og_description: Aggiungi un pulsante di comando a un documento Word con Aspose.Words.
  Questo tutorial mostra come impostare le proprietà del controllo ActiveX e impostare
  rapidamente la didascalia del pulsante di comando.
og_image_alt: Screenshot of a Word document with a Submit command button inserted
  via C#
og_title: Aggiungi pulsante di comando al documento Word – Aspose.Words passo passo
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Add command button to word document using Aspose.Words. Learn how to
    set activex control properties and set command button caption in a few easy steps.
  headline: Add Command Button to Word Document with Aspose.Words – Complete Guide
  type: TechArticle
- description: Add command button to word document using Aspose.Words. Learn how to
    set activex control properties and set command button caption in a few easy steps.
  name: Add Command Button to Word Document with Aspose.Words – Complete Guide
  steps:
  - name: Setting the Caption
    text: 'The caption is the text that appears on the button itself. To **set command
      button caption**, simply assign a string to the `Caption` property:'
  - name: Naming the Control
    text: 'Giving the control a meaningful name makes it easier to reference later
      (for example, when automating Word macros). We’ll set the `Name` property:'
  - name: Positioning on the Page
    text: 'Word uses points (1/72 of an inch) for layout. Adjust the `Left` and `Top`
      properties to place the button where you need it:'
  - name: Expected Result
    text: 1. The Word document opens with a single page. 2. A rectangular button labeled
      **Submit** appears at the coordinates you specified. 3. If you right‑click the
      button and choose **Properties**, you’ll see the name `btnSubmit` and other
      properties you set.
  - name: Inserting Other ActiveX Types
    text: 'The `InsertForms2OleControl` method isn’t limited to command buttons. You
      can embed check boxes, option buttons, or even custom ActiveX objects:'
  - name: Handling Word Versions
    text: Older Word versions (pre‑2007) use the binary `.doc` format, which stores
      ActiveX controls differently. Aspose.Words automatically converts the control
      when you save as `.doc`, but some properties (like precise positioning) may
      shift. If you target legacy formats, test the output in the specific Wor
  - name: Security Settings
    text: 'Word may disable ActiveX controls on machines with strict macro security.
      To avoid a “Security Warning” dialog, consider:'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Aggiungi pulsante di comando al documento Word con Aspose.Words – Guida completa
url: /it/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aggiungere un pulsante di comando a un documento Word – Guida completa di programmazione

Hai mai avuto bisogno di **aggiungere un pulsante di comando a un documento Word** ma non eri sicuro di quali chiamate API utilizzare? Non sei solo; molti sviluppatori incontrano questo ostacolo quando provano per la prima volta a inserire controlli interattivi in un file DOCX. La buona notizia è che Aspose.Words lo rende sorprendentemente semplice. In questa guida vedremo come creare un controllo ActiveX CommandButton, **impostare le proprietà del controllo ActiveX**, e **impostare la didascalia del pulsante di comando**—tutto con codice C# pulito che puoi copiare‑incollare subito.

Alla fine di questo tutorial avrai un file Word completamente funzionante che contiene un pulsante “Submit” cliccabile, pronto per essere aperto in Microsoft Word. Nessuno script VBA esterno, nessuna manipolazione manuale dell’interfaccia—solo puro controllo programmatico.

## Cosa imparerai

* Come creare un documento Word vuoto e un `DocumentBuilder`.
* La chiamata di metodo esatta per **aggiungere un pulsante di comando a un documento Word** usando Aspose.Words.
* Modi per **impostare le proprietà del controllo ActiveX** come dimensione, posizione e nome.
* La tecnica corretta per **impostare la didascalia del pulsante di comando** in modo che il pulsante mostri esattamente ciò che desideri.
* Suggerimenti per gestire casi limite come diversi tipi di pulsante, scaling DPI e compatibilità con le versioni di Word.

> **Prerequisito:** Visual Studio (o qualsiasi IDE C#) con Aspose.Words per .NET installato (pacchetto NuGet `Aspose.Words`). Nessuna esperienza precedente con ActiveX richiesta.

---

## Passo 1: Configurare il progetto e importare i namespace

Prima di poter **aggiungere un pulsante di comando a un documento Word**, ci serve un progetto C# che faccia riferimento ad Aspose.Words. Crea una nuova applicazione console .NET, quindi aggiungi il pacchetto NuGet:

```bash
dotnet add package Aspose.Words
```

Ora porta i namespace richiesti nel tuo file sorgente:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.ActiveX;
```

Queste tre direttive `using` ti danno accesso alle classi `Document`, `DocumentBuilder` e `Forms2OleControl` che alimentano l’inserimento di ActiveX.

*Pro tip:* Se usi Visual Studio, l’IDE suggerirà di aggiungere questi automaticamente quando digiti i nomi delle classi.

---

## Passo 2: Creare un documento vuoto e un builder

Un nuovo oggetto `Document` rappresenta un file Word vuoto. Il `DocumentBuilder` è la nostra “penna” pratica che consente di disegnare, inserire testo e—fondamentale—posizionare controlli ActiveX.

```csharp
// Initialize a new, empty Word document.
Document doc = new Document();

// Attach a builder to the document for editing.
DocumentBuilder builder = new DocumentBuilder(doc);
```

A questo punto il documento è solo una tela bianca—pensalo come un foglio pulito in attesa del tuo pulsante di comando.

---

## Passo 3: Inserire il controllo ActiveX CommandButton

Ora inseriamo finalmente **un pulsante di comando in un documento Word**. Aspose.Words fornisce il metodo `InsertForms2OleControl`, che accetta il tipo di controllo e le dimensioni. Useremo `Forms2OleControlType.CommandButton` e gli assegneremo una larghezza comoda di 150 punti e un’altezza di 30 punti.

```csharp
// Insert a CommandButton ActiveX control with a specific size.
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton,
    width: 150,
    height: 30);
```

Il metodo restituisce un’istanza `Forms2OleControl`, che utilizzeremo per **impostare le proprietà del controllo ActiveX** nel passo successivo.

---

## Passo 4: Configurare il controllo – Nome, Didascalia e Posizione

### Impostare la Didascalia

La didascalia è il testo che appare sul pulsante stesso. Per **impostare la didascalia del pulsante di comando**, assegna semplicemente una stringa alla proprietà `Caption`:

```csharp
commandButton.Caption = "Submit";
```

Puoi cambiare `"Submit"` con qualsiasi cosa—“Save”, “Export”, “Launch”, ecc.—e Word mostrerà esattamente quel testo.

### Assegnare un Nome al Controllo

Dare al controllo un nome significativo lo rende più facile da riferire in seguito (ad esempio, quando automatizzi macro Word). Impostiamo la proprietà `Name`:

```csharp
commandButton.Name = "btnSubmit";
```

### Posizionare sulla Pagina

Word utilizza i punti (1/72 di pollice) per il layout. Regola le proprietà `Left` e `Top` per collocare il pulsante dove ti serve:

```csharp
commandButton.Left = 100; // 100 points from the left margin
commandButton.Top  = 200; // 200 points from the top of the page
```

Se devi allineare il pulsante rispetto a un paragrafo, puoi spostare prima il cursore del builder, quindi inserire il controllo; le coordinate saranno relative a quella posizione.

*Caso limite:* Su monitor ad alta DPI le dimensioni visive potrebbero apparire leggermente diverse in Word. Per mantenere la dimensione fisica del pulsante costante su tutti i dispositivi, puoi calcolare i punti in base alla DPI target (normalmente 96 DPI per Word).

---

## Passo 5: Salvare il documento

Con il pulsante completamente configurato, persistere il file è una riga di codice:

```csharp
// Save the document; the ActiveX control is stored inside the DOCX.
doc.Save("CommandButton.docx");
```

Il risultato `CommandButton.docx` contiene un pulsante ActiveX pienamente funzionante. Aprilo in Microsoft Word e vedrai un pulsante “Submit” posizionato esattamente dove lo hai inserito.

### Risultato Atteso

1. Il documento Word si apre con una singola pagina.  
2. Un pulsante rettangolare etichettato **Submit** appare alle coordinate specificate.  
3. Se fai clic destro sul pulsante e scegli **Properties**, vedrai il nome `btnSubmit` e le altre proprietà impostate.

---

## Passo 6: Varianti avanzate e problemi comuni

### Inserire altri tipi di ActiveX

Il metodo `InsertForms2OleControl` non è limitato ai pulsanti di comando. Puoi incorporare caselle di controllo, pulsanti di opzione o anche oggetti ActiveX personalizzati:

```csharp
// Example: Insert a CheckBox instead of a CommandButton.
Forms2OleControl checkBox = builder.InsertForms2OleControl(
    Forms2OleControlType.CheckBox,
    width: 20,
    height: 20);
checkBox.Name = "chkAgree";
checkBox.Caption = "I Agree";
```

Lo stesso schema di **impostare le proprietà del controllo ActiveX** si applica—basta cambiare l’enumerazione del tipo.

### Gestire le versioni di Word

Le versioni più vecchie di Word (pre‑2007) usano il formato binario `.doc`, che memorizza i controlli ActiveX in modo diverso. Aspose.Words converte automaticamente il controllo quando salvi come `.doc`, ma alcune proprietà (come il posizionamento preciso) potrebbero spostarsi. Se punti a formati legacy, testa l’output nella versione specifica di Word di cui hai bisogno.

### Impostazioni di sicurezza

Word potrebbe disabilitare i controlli ActiveX su macchine con sicurezza macro rigorosa. Per evitare la finestra di dialogo “Security Warning”, considera:

* Firmare il documento con un certificato attendibile.  
* Istruire gli utenti ad abilitare il contenuto ActiveX per quella posizione di file.  
* Usare un’alternativa senza macro (ad esempio, controlli di contenuto semplici) se la sicurezza è una preoccupazione.

---

## Passo 7: Esempio completo funzionante

Di seguito trovi il programma completo, pronto per l’esecuzione, che incorpora tutti i passaggi discussi. Copialo in `Program.cs`, regola il percorso di output se necessario, e premi **Run**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.ActiveX;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a CommandButton ActiveX control.
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,
            width: 150,   // Width in points
            height: 30);  // Height in points

        // Step 3: Set the control's name and caption.
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";

        // Step 4: Position the control on the page.
        commandButton.Left = 100; // 100 points from left edge
        commandButton.Top  = 200; // 200 points from top edge

        // Optional: Add a paragraph above the button for context.
        builder.MoveToDocumentEnd();
        builder.Writeln("Click the button below to submit the form:");

        // Step 5: Save the document.
        string outputPath = "CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved successfully to {outputPath}");
    }
}
```

**Cosa fa questo codice:**

* Inizia con un documento nuovo.  
* Inserisce un pulsante di comando, **imposta le proprietà del controllo ActiveX** e **imposta la didascalia del pulsante di comando**.  
* Aggiunge un breve paragrafo esplicativo.  
* Salva il file come `CommandButton.docx`.

Esegui il programma, apri il file generato e vedrai il pulsante posizionato sotto il testo esplicativo.

---

## Conclusione

Abbiamo appena dimostrato come **aggiungere un pulsante di comando a un documento Word** usando Aspose.Words, come **impostare le proprietà del controllo ActiveX** e come **impostare la didascalia del pulsante di comando**—tutto in uno snippet C# conciso e pronto per la produzione. L’approccio è scalabile: cambia il tipo di controllo, modifica le dimensioni o itera su una fonte dati per inserire decine di pulsanti automaticamente.

Vuoi andare oltre? Prova:

* Collegare il pulsante a una macro che avvia un’esportazione di dati.  
* Aggiungere immagini o icone personalizzate all’interno del pulsante usando la proprietà `Picture`.  
* Costruire un modulo completo con più controlli ActiveX (caselle di testo, combo box, ecc.).

Sperimentare è il modo migliore per padroneggiare l’automazione di Word. Se incontri difficoltà, ricorda di ricontrollare i calcoli DPI e le impostazioni di sicurezza di Word. Buona programmazione, e che i tuoi documenti diventino sempre più interattivi!

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Aggiungere contenuto usando Document Builder in Aspose.Words per .NET](/words/english/net/add-content-using-document-builder/)
- [Creare forma di gruppo in un documento Word usando Aspose.Words per .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Creare documento Word con intestazione e piè di pagina usando Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}