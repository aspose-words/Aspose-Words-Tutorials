---
category: general
date: 2026-07-23
description: creare un pulsante per documento Word usando Aspose.Words – guida passo‑passo
  per inserire un CommandButton ActiveX in un file .docx
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document button
- ActiveX CommandButton
- DocumentBuilder
- InsertForms2OleControl
- Aspose.Words
language: it
lastmod: 2026-07-23
og_description: 'crea pulsante documento Word con Aspose.Words: scopri come incorporare
  un CommandButton ActiveX in un file Word in pochi minuti.'
og_image_alt: Screenshot of a Word document showing an inserted CommandButton control
og_title: Pulsante per creare documento Word – Guida completa ad Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-23'
  description: create word document button using Aspose.Words – step‑by‑step guide
    to insert an ActiveX CommandButton into a .docx file.
  headline: create word document button with Aspose.Words – Full Code Example
  type: TechArticle
- description: create word document button using Aspose.Words – step‑by‑step guide
    to insert an ActiveX CommandButton into a .docx file.
  name: create word document button with Aspose.Words – Full Code Example
  steps:
  - name: '**Creates** an OLE object inside the Word file.'
    text: '**Creates** an OLE object inside the Word file.'
  - name: '**Registers** it as an ActiveX CommandButton, which Word will render as
      a clickable UI element.'
    text: '**Registers** it as an ActiveX CommandButton, which Word will render as
      a clickable UI element.'
  - name: '**Positions** it according to the rectangle we supplied.'
    text: '**Positions** it according to the rectangle we supplied.'
  - name: Launch Microsoft Word.
    text: Launch Microsoft Word.
  - name: Navigate to **File → Open** and select `CommandButton.docx`.
    text: Navigate to **File → Open** and select `CommandButton.docx`.
  - name: You should see a rectangular button labeled “CommandButton1”.
    text: You should see a rectangular button labeled “CommandButton1”.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- ActiveX
- CommandButton
title: Pulsante per creare documento Word con Aspose.Words – Esempio di codice completo
url: /it/net/working-with-oleobjects-and-activex/create-word-document-button-with-aspose-words-full-code-exam/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# crea pulsante documento Word con Aspose.Words – Guida completa di programmazione

Hai mai avuto bisogno di **creare pulsante documento Word** ma non sapevi quale API utilizzare? Non sei solo: la maggior parte degli sviluppatori si blocca quando tenta di inserire controlli interattivi in un file .docx. La buona notizia? Con Aspose.Words per .NET puoi inserire un ActiveX CommandButton completamente funzionante in un documento Word con poche righe di codice.

In questo tutorial percorreremo l’intero processo: dalla configurazione del progetto, all’inizializzazione di un `DocumentBuilder`, all’inserimento del pulsante con `InsertForms2OleControl`, fino al salvataggio del file affinché Word riconosca il controllo. Alla fine avrai un file Word pronto all’uso che contiene un pulsante cliccabile—senza necessità di complicate operazioni COM interop.

## What You’ll Need

Prima di iniziare, assicurati di avere i seguenti prerequisiti:

- **.NET 6.0** o versioni successive (il codice funziona anche con .NET Framework 4.6+).  
- **Aspose.Words for .NET** pacchetto NuGet (versione 23.9 o più recente).  
- Una conoscenza di base di C# (manteniamo la sintassi adatta ai principianti).  
- Visual Studio 2022 o qualsiasi IDE tu preferisca.

Tutto qui—nessun riferimento COM aggiuntivo, nessun interop Office, solo codice gestito puro.

---

## Step 1: Set Up Aspose.Words to **create word document button**

Prima di tutto, aggiungi il pacchetto Aspose.Words al tuo progetto:

```bash
dotnet add package Aspose.Words
```

Oppure, se utilizzi l’interfaccia NuGet di Visual Studio, cerca “Aspose.Words” e premi **Install**. Questa singola riga ti dà accesso a `Document`, `DocumentBuilder` e al metodo `InsertForms2OleControl` di cui avremo bisogno più avanti.

> **Pro tip:** Mantieni i pacchetti NuGet aggiornati; le versioni più recenti includono spesso correzioni di bug per la gestione di ActiveX.

---

## Step 2: Initialize **DocumentBuilder** for an **ActiveX CommandButton**

Ora creiamo un nuovo documento Word e avviamo un `DocumentBuilder`. Pensa a `DocumentBuilder` come al pennello che ti permette di disegnare contenuti sulla tela.

```csharp
using System;
using System.Drawing;               // For Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 2.1: Create a new empty document
        Document document = new Document();

        // Step 2.2: Initialize DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

Nota come importiamo `System.Drawing`—la struttura `Rectangle` definisce la posizione e le dimensioni del pulsante. È qui che vivrà l’**ActiveX CommandButton**.

---

## Step 3: Use **InsertForms2OleControl** to **add a CommandButton**

Ecco il cuore del tutorial: inserire il pulsante stesso. Il metodo `InsertForms2OleControl` accetta tre argomenti—tipo di controllo, un `Rectangle` e, facoltativamente, un nome. Useremo `OleControlType.CommandButton` per specificare il controllo desiderato.

```csharp
        // Step 3: Insert an ActiveX CommandButton at (0,0) with width=100, height=30
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new Rectangle(0, 0, 100, 30));
```

Quella singola chiamata fa molto:

1. **Crea** un oggetto OLE all’interno del file Word.  
2. **Lo registra** come ActiveX CommandButton, che Word renderà come elemento UI cliccabile.  
3. **Lo posiziona** secondo il rettangolo fornito.

Se devi modificare la didascalia del pulsante o altre proprietà, puoi farlo dopo l’inserimento accedendo all’`OleFormat` sottostante. Per la maggior parte degli scenari, la didascalia predefinita (“CommandButton1”) è sufficiente.

---

## Step 4: Save the Word Document Containing the **CommandButton**

Il salvataggio è semplice—basta puntare a una cartella in cui hai permessi di scrittura. L’estensione del file deve essere `.docx` affinché il pulsante sopravviva al round‑trip.

```csharp
        // Step 4: Save the document with the embedded button
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Quando apri `CommandButton.docx` in Microsoft Word, vedrai un piccolo pulsante nell’angolo in alto a sinistra della prima pagina. Cliccarlo non fa nulla di default (per questo servirebbe VBA), ma il controllo è pienamente funzionante e può essere collegato in seguito.

> **Perché funziona:** Aspose.Words scrive lo stream OLE direttamente nel pacchetto DOCX, evitando la necessità che Word generi il controllo a runtime. Questo garantisce che il pulsante appaia esattamente dove lo hai posizionato.

---

## Step 5: Verify the Button in Word

Apri il file generato:

1. Avvia Microsoft Word.  
2. Vai su **File → Open** e seleziona `CommandButton.docx`.  
3. Dovresti vedere un pulsante rettangolare etichettato “CommandButton1”.  

Se non vedi il pulsante, assicurati che la **Design Mode** sia attiva (Developer → Design Mode). Questo attiva la rappresentazione visiva dei controlli ActiveX.

---

## Step 6: Advanced Options – Customizing the **ActiveX CommandButton**

Di seguito trovi alcuni rapidi aggiustamenti che potresti trovare utili:

| Goal | Code Snippet |
|------|--------------|
| Change caption | ```csharp<br/>OleFormat ole = builder.CurrentParagraph.Runs[0].OleFormat;<br/>ole.OleControlCaption = "Submit";``` |
| Set macro name (requires Word macro support) | ```csharp<br/>ole.OleControlMacroName = "MyMacro";``` |
| Resize after insertion | ```csharp<br/>builder.MoveToDocumentEnd();<br/>builder.InsertForms2OleControl(OleControlType.CommandButton, new Rectangle(0,0,150,40));``` |

Questi snippet dimostrano la flessibilità di `InsertForms2OleControl`. Puoi anche incorporare altri controlli ActiveX come `CheckBox` o `ListBox` cambiando il valore dell’enum `OleControlType`.

---

## Full Working Example

Di seguito trovi il programma completo, pronto per il copia‑incolla, che **crea un pulsante documento Word** da zero:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class CreateWordDocumentButton
{
    static void Main()
    {
        // 1️⃣ Create a new empty document
        Document document = new Document();

        // 2️⃣ Initialize DocumentBuilder – the tool that lets us edit the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Insert an ActiveX CommandButton at position (0,0) with size 100x30
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new Rectangle(0, 0, 100, 30));

        // 4️⃣ Save the .docx file – this is where the button lives
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);

        Console.WriteLine($"✅ Document with button saved to: {outputPath}");
    }
}
```

**Output previsto quando esegui il programma:**

```
✅ Document with button saved to: C:\Temp\CommandButton.docx
```

Apri il file risultante e vedrai il pulsante esattamente dove il codice lo ha posizionato.

---

## Common Pitfalls & How to Avoid Them

- **Missing `System.Drawing` reference** – La struttura `Rectangle` si trova lì; senza di essa il compilatore segnalerà errori.  
- **Using an older Aspose.Words version** – Le versioni precedenti non supportavano completamente `InsertForms2OleControl`. Aggiorna all’ultimo pacchetto stabile.  
- **Saving as `.doc` instead of `.docx`** – Lo stream OLE viene rimosso nel formato binario più vecchio, facendo scomparire il pulsante.  
- **Running on a headless server without Word installed** – Il pulsante sarà comunque presente nel file, ma non potrai visualizzarlo senza Word. Questo è accettabile per pipeline di generazione automatica.

---

## Next Steps – Extending the **create word document button** Workflow

Ora che hai padroneggiato le basi, considera queste idee di livello avanzato:

- **Attach VBA macros** al pulsante per logica di business personalizzata.  
- **Generate multiple buttons** in un ciclo per form dinamici.  
- **Combine with Aspose.PDF** per esportare lo stesso documento in PDF mantenendo il layout visivo (il pulsante diventa un’immagine statica nel PDF).  
- **

## What Should You Learn Next?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi con spiegazioni passo‑passo per aiutarti a padroneggiare ulteriori funzionalità dell’API e a esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}