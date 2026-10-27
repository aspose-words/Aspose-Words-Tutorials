---
category: general
date: 2026-09-11
description: Scopri come creare forms2olecontrol nel codice usando Aspose.Words DocumentBuilder.
  Questa guida passo‑passo copre l’inserimento di pulsanti di comando ActiveX, l’uso
  di setOleClassName e la gestione delle dimensioni.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create forms2olecontrol in code
- ActiveX command button
- Aspose.Words DocumentBuilder
- setOleClassName method
- Forms2OleControl size
language: it
lastmod: 2026-09-11
og_description: Crea forms2olecontrol nel codice con Aspose.Words. Segui questa guida
  per inserire un pulsante di comando ActiveX, impostare il suo nome di classe e regolare
  le sue dimensioni.
og_image_alt: Screenshot of a Word document showing a newly created ActiveX command
  button inserted via code
og_title: Crea forms2olecontrol nel codice – guida completa di Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create forms2olecontrol in code using Aspose.Words DocumentBuilder.
    This step‑by‑step guide covers ActiveX command button insertion, setOleClassName
    usage, and sizing.
  headline: How to create forms2olecontrol in code with Aspose.Words
  type: TechArticle
- description: Learn how to create forms2olecontrol in code using Aspose.Words DocumentBuilder.
    This step‑by‑step guide covers ActiveX command button insertion, setOleClassName
    usage, and sizing.
  name: How to create forms2olecontrol in code with Aspose.Words
  steps:
  - name: Initialise the DocumentBuilder
    text: The `DocumentBuilder` class is the entry point for most document‑generation
      tasks in Aspose.Words. It gives you methods to add text, images, tables, and,
      importantly for this tutorial, OLE controls.
  - name: Insert the Forms2OleControl
    text: The `insertForms2OleControl` method returns a `Forms2OleControl` object.
      This object represents the OLE control placeholder that Word will render as
      an ActiveX button.
  - name: Specify the ActiveX class with setOleClassName
    text: Word needs to know which type of ActiveX control to render. The class name
      for a standard command button is `"Forms.CommandButton.1"`.
  - name: Adjust the Forms2OleControl size
    text: A button that is too small or too large looks unprofessional. You can control
      its dimensions with `setWidth` and `setHeight`.
  - name: Save the document and test
    text: After configuring the control, save the document to a location of your choice.
  - name: When to use Forms2OleControl vs. Content Controls
    text: If you only need simple data entry (e.g., a plain text field), Word’s built‑in
      content controls are lighter weight. Use `Forms2OleControl` when you require
      full ActiveX functionality such as event handling or custom VBA interaction.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: Come creare forms2olecontrol nel codice con Aspose.Words
url: /it/java/using-document-elements/how-to-create-forms2olecontrol-in-code-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come creare forms2olecontrol nel codice con Aspose.Words

Se hai bisogno di **creare forms2olecontrol nel codice**, questa guida ti mostra esattamente come farlo usando l'API Aspose.Words .NET. Che tu stia automatizzando un modello che richiede un pulsante di comando ActiveX o voglia semplicemente arricchire un documento Word programmaticamente, i passaggi seguenti coprono tutto, dall'inserimento del controllo alla configurazione del suo aspetto.

In questo tutorial imparerai a usare il **Aspose.Words DocumentBuilder** per inserire un **ActiveX command button**, impostare la sua classe con il **metodo setOleClassName** e regolare la **dimensione Forms2OleControl**. Non sono necessari strumenti esterni: basta un ambiente di sviluppo .NET e la libreria Aspose.Words.

## Prerequisiti

* .NET 6.0 o versioni successive installate (il codice funziona anche con .NET Framework 4.7+)
* Una versione recente del pacchetto NuGet Aspose.Words per .NET
* Familiarità di base con C# e il concetto di controlli ActiveX nei documenti Word

Se manca qualcuno di questi, installa il pacchetto NuGet con:

```bash
dotnet add package Aspose.Words
```

## Cosa copre questo tutorial

* Creare un'istanza di `DocumentBuilder`
* Inserire un `Forms2OleControl` (l'oggetto sottostante per un pulsante di comando ActiveX)
* Assegnare il nome di classe corretto con `setOleClassName`
* Impostare larghezza e altezza visive usando le proprietà **Forms2OleControl size**
* Salvare il documento e verificare il risultato

Al termine della guida avrai un file Word completamente funzionale contenente un pulsante cliccabile che potrai ulteriormente personalizzare o collegare a macro VBA.

---

## Come creare forms2olecontrol nel codice – passo‑per‑passo

### Passo 1: Inizializzare il DocumentBuilder

La classe `DocumentBuilder` è il punto di ingresso per la maggior parte delle attività di generazione di documenti in Aspose.Words. Ti fornisce metodi per aggiungere testo, immagini, tabelle e, soprattutto per questo tutorial, controlli OLE.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document doc = new Document();

// Initialise the builder for the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Perché è importante:**  
`DocumentBuilder` mantiene la posizione corrente del cursore all'interno del documento. Creandolo subito, ti assicuri che qualsiasi inserimento successivo — come il **ActiveX command button** — appaia esattamente dove desideri.

### Passo 2: Inserire il Forms2OleControl

Il metodo `insertForms2OleControl` restituisce un oggetto `Forms2OleControl`. Questo oggetto rappresenta il segnaposto del controllo OLE che Word renderizzerà come pulsante ActiveX.

```csharp
// Insert the Forms2OleControl at the current cursor location
Forms2OleControl commandButton = builder.InsertForms2OleControl();
```

**Perché è importante:**  
Senza questa chiamata non puoi manipolare le proprietà del controllo. Il `Forms2OleControl` restituito ti dà pieno accesso al **metodo setOleClassName**, agli attributi di dimensione e ad altre impostazioni specifiche OLE.

### Passo 3: Specificare la classe ActiveX con setOleClassName

Word deve sapere quale tipo di controllo ActiveX renderizzare. Il nome della classe per un pulsante di comando standard è `"Forms.CommandButton.1"`.

```csharp
// Tell Word that this OLE control is a CommandButton
commandButton.SetOleClassName("Forms.CommandButton.1");
```

**Perché è importante:**  
Il metodo `setOleClassName` è il ponte tra il segnaposto OLE generico e il concreto **ActiveX command button**. Usare un nome di classe errato porta a un oggetto vuoto o a un errore di runtime quando il documento viene aperto.

### Passo 4: Regolare la dimensione del Forms2OleControl

Un pulsante troppo piccolo o troppo grande appare poco professionale. Puoi controllare le sue dimensioni con `setWidth` e `setHeight`.

```csharp
// Set the visual dimensions (points) of the button
commandButton.SetWidth(80);   // width in points
commandButton.SetHeight(30);  // height in points
```

**Perché è importante:**  
Queste proprietà costituiscono la **dimensione Forms2OleControl**. Influenzano l'aspetto del pulsante nell'interfaccia di Word e garantiscono che qualsiasi macro allegata abbia un'area cliccabile sufficiente.

### Passo 5: Salvare il documento e testare

Dopo aver configurato il controllo, salva il documento in una posizione a tua scelta.

```csharp
// Save the document as a .docx file
doc.Save("ActiveXButton.docx");
```

Apri `ActiveXButton.docx` in Microsoft Word. Dovresti vedere un pulsante etichettato “CommandButton1” (la didascalia predefinita). Cliccarlo non farà nulla a meno che non aggiungi una macro VBA, ma il controllo stesso è pienamente funzionante.

**Output previsto:**  

![Documento Word con un pulsante ActiveX inserito](/images/activeX-button.png "Screenshot di un documento Word che mostra un nuovo pulsante ActiveX inserito tramite codice")

*Il testo alternativo dell'immagine contiene la parola chiave principale per l'accessibilità e la SEO.*

---

## Comprendere la classe ActiveX Forms2OleControl

La classe `Forms2OleControl` incapsula l'infrastruttura OLE di basso livello che Word utilizza per gli elementi ActiveX. Eredita da `Shape`, il che significa che puoi anche applicare formattazioni tipiche delle forme (ad esempio bordi, rotazione) se necessario.

* **ActiveX command button** – Il caso d'uso più comune; puoi collegarlo a una macro tramite gli strumenti di sviluppo di Word.
* **metodo setOleClassName** – Determina quale classe COM Word carica; altri valori validi includono `"Forms.TextBox.1"` e `"Forms.ComboBox.1"`.
* **dimensione Forms2OleControl** – Controllata tramite `SetWidth`/`SetHeight`. Questi metodi accettano punti (1 pt = 1/72 in).

### Quando usare Forms2OleControl vs. Content Controls

Se hai bisogno solo di inserimento dati semplice (ad esempio, un campo di testo semplice), i controlli di contenuto integrati in Word sono più leggeri. Usa `Forms2OleControl` quando richiedi la piena funzionalità ActiveX, come la gestione degli eventi o l'interazione VBA personalizzata.

---

## Impostare proprietà aggiuntive (opzionale)

Mentre i passaggi fondamentali sono sufficienti per **creare forms2olecontrol nel codice**, spesso desideri perfezionare l'aspetto o il comportamento del pulsante.

```csharp
// Change the button caption (requires a VBA macro to read it)
commandButton.SetOleData("Caption", "Submit");

// Disable the button initially
commandButton.SetOleData("Enabled", false);

// Add a tooltip
commandButton.SetOleData("ToolTipText", "Click to submit the form");
```

**Perché è importante:**  
`SetOleData` ti consente di scrivere valori di proprietà arbitrari direttamente nello stream OLE. Questo è il modo più flessibile per personalizzare un **ActiveX command button** senza ricorrere a VBA.

---

## Problemi comuni e risoluzione

| Sintomo | Probabile causa | Soluzione |
|--------|--------------|-----|
| Il pulsante appare come una casella grigia | Nome classe errato passato a `setOleClassName` | Verifica che la stringa sia esattamente `"Forms.CommandButton.1"` (case‑sensitive) |
| La dimensione non cambia | Larghezza/Altezza impostate prima di inserire il controllo | Chiama sempre `SetWidth`/`SetHeight` **dopo** `InsertForms2OleControl` |
| Il documento genera “OLE object not found” all'apertura | Licenza Aspose.Words mancante (la versione di valutazione può limitare OLE) | Applica una licenza valida o usa la versione di prova gratuita con supporto OLE completo |
| La didascalia del pulsante rimane “CommandButton1” | `SetOleData` non usato o macro che non legge la proprietà | Usa una macro VBA per leggere la proprietà `"Caption"` o imposta la didascalia tramite l'interfaccia di Word |

---

## Esempio completo, eseguibile

Di seguito trovi un'applicazione console completa che puoi copiare, incollare ed eseguire. Dimostra tutto ciò che è stato trattato in questo tutorial.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace Forms2OleControlDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1. Create a new document and a DocumentBuilder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2. Insert the Forms2OleControl (ActiveX placeholder)
            Forms2OleControl commandButton = builder.InsertForms2OleControl();

            // 3. Set the ActiveX class to CommandButton
            commandButton.SetOleClassName("Forms.CommandButton.1");

            // 4. Define the visual size of the button
            commandButton.SetWidth(80);   // 80 points = ~1.11 inches
            commandButton.SetHeight(30);  // 30 points = ~0.42 inches

            // Optional: set a custom caption via OLE data (requires VBA to read)
            commandButton.SetOleData("Caption", "Submit");

            // 5. Save the document
            string outputPath = "ActiveXButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Spiegazione di ogni sezione**

* **Using directives** – Importa lo spazio dei nomi Aspose.Words necessario per `Document`, `DocumentBuilder` e `Forms2OleControl`.
* **Creazione del documento** – Istanzia un file Word vuoto.
* **InsertForms2OleControl** – Posiziona il controllo OLE al cursore corrente del builder.
* **SetOleClassName** – Indica a Word che il controllo è un **ActiveX command button**.
* **SetWidth / SetHeight** – Regola la **dimensione Forms2OleControl** per un aspetto professionale.
* **SetOleData (opzionale)** – Dimostra come scrivere proprietà aggiuntive come una didascalia.
* **Save** – Scrive il file `.docx` finale su disco.

Esegui il programma (`dotnet run`) e apri `ActiveXButton.docx`. Dovresti vedere un pulsante che potrai successivamente collegare a una macro.

---

## Conclusione

Ora sai come **creare forms2olecontrol nel codice** usando Aspose.Words, dall'inizializzare il `DocumentBuilder` alla configurazione del **ActiveX command button** con `setOleClassName` e al controllo della sua **dimensione Forms2OleControl**. Questo approccio ti consente di automatizzare documenti Word complessi, incorporare elementi UI interattivi e mantenere tutta la logica all'interno

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Come creare campi modulo e aggiungere contenuto usando DocumentBuilder in Aspose.Words per Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Creare Group Shape in un documento Word usando Aspose.Words per .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Creare forma rettangolare in Word con Aspose.Words – Guida passo‑per‑passo](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}