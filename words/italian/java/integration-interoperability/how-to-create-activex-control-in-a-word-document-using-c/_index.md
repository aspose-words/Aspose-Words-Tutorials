---
category: general
date: 2026-08-20
description: Scopri come creare un controllo ActiveX, impostare le dimensioni del
  pulsante e aggiungere il pulsante a Word con un esempio completo in C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex control
- set button size
- add button to word
- how to insert button
- create clickable button
language: it
lastmod: 2026-08-20
og_description: Crea un controllo ActiveX in un file Word con C#. Questo tutorial
  mostra come impostare le dimensioni del pulsante, aggiungere il pulsante a Word
  e creare un pulsante cliccabile.
og_image_alt: Screenshot of a Word document showing a newly created ActiveX control
  button
og_title: Crea un controllo ActiveX in Word – guida passo‑passo in C#
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to create ActiveX control, set button size, and add button
    to Word with a complete C# example.
  headline: How to create ActiveX control in a Word document using C#
  type: TechArticle
- description: Learn how to create ActiveX control, set button size, and add button
    to Word with a complete C# example.
  name: How to create ActiveX control in a Word document using C#
  steps:
  - name: Why this works
    text: '* `InsertForms2OleControl` tells Word to embed an OLE object of type **CommandButton**,
      which is the classic ActiveX button class. * The width and height arguments
      directly **set button size**; Word translates the values from points (1 pt ≈
      1/72 in). * Naming the control (`Name = "btnSubmit"`) makes'
  - name: Pro tip
    text: 'If you want a square button, set both dimensions to the same value:'
  - name: 1. What if the button does not appear after saving?
    text: '* Verify that the Aspose.Words version supports `InsertForms2OleControl`.
      Versions prior to 22.5 lack this feature. * Ensure the target file format is
      `.docx` or `.doc`. Older formats like `.rtf` cannot store ActiveX objects.'
  - name: 2. Can I insert the button at a specific bookmark?
    text: 'Yes. Move the builder to the bookmark before calling `InsertForms2OleControl`:'
  - name: 3. How to **set button size** dynamically based on text length?
    text: Calculate the required width using the `Graphics.MeasureString` method (from
      `System.Drawing`) and convert pixels to points (`points = pixels * 72 / DPI`).
      Then pass the computed width to `InsertForms2OleControl`.
  - name: 4. Is there a way to add multiple buttons in a loop?
    text: 'Absolutely. Wrap the insertion logic in a `for` loop and adjust the `Left`
      and `Top` properties for each iteration:'
  type: HowTo
tags:
- ActiveX
- C#
- Aspose.Words
- Word automation
title: Come creare un controllo ActiveX in un documento Word usando C#
url: /it/java/integration-interoperability/how-to-create-activex-control-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come creare un controllo ActiveX in un documento Word usando C#

Se hai bisogno di **creare un controllo ActiveX** all'interno di un file Microsoft Word, questa guida ti mostra esattamente come farlo. Vedrai come **aggiungere un pulsante a Word**, impostare le dimensioni del pulsante e rendere il controllo cliccabile—tutto con un breve programma C# autonomo.

In questo tutorial imparerai a:

* Comprendere perché un controllo ActiveX è utile per documenti Word interattivi.  
* Conoscere il codice esatto necessario per **impostare la dimensione del pulsante** e assegnare una didascalia.  
* Vedere come **creare un pulsante cliccabile** che può essere collegato in seguito a una macro o a una logica esterna.  

I passaggi funzionano con Aspose.Words .NET 23.12 o versioni successive e richiedono solo un ambiente di sviluppo .NET.

> **Prerequisito** – Hai una licenza valida di Aspose.Words (o stai usando la versione di valutazione) e Visual Studio 2022 o qualsiasi IDE C#.

---

## Come creare un controllo ActiveX in un documento Word

Il primo passo è istanziare un `Document` vuoto e un `DocumentBuilder`. Il builder fornisce l'API di alto livello per inserire oggetti come i controlli ActiveX.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordActiveXDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new empty document and obtain a DocumentBuilder.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // The rest of the steps are explained in the following sections.
            InsertActiveXButton(builder);

            // Save the result so you can open it in Word.
            doc.Save("ActiveXButton.docx");
            Console.WriteLine("Document saved as ActiveXButton.docx");
        }
```

Il metodo `InsertActiveXButton` (definito di seguito) contiene la logica per **come inserire il pulsante** e configurarlo.

```csharp
        /// <summary>
        /// Inserts a CommandButton ActiveX control, sets its size, name, and caption.
        /// </summary>
        static void InsertActiveXButton(DocumentBuilder builder)
        {
            // Step 2: Insert a CommandButton ActiveX control with the desired size (width: 100, height: 30).
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                "CommandButton", 100, 30);

            // Step 3: Assign a name to the control for later reference.
            commandButton.Name = "btnSubmit";

            // Step 4: Set the caption that will be displayed on the button.
            commandButton.Caption = "Submit";

            // Optional: Position the button on the page (e.g., 100 points from the top left).
            commandButton.Left = 100;
            commandButton.Top = 150;
        }
    }
}
```

L'esecuzione del programma crea **ActiveXButton.docx**. Aprendo il file in Word compare un pulsante con l'etichetta **Submit**. Il controllo è pienamente funzionale—cliccandolo verrà sollevato l'evento standard `CommandButton_Click`, che potrai successivamente collegare a una macro VBA.

### Perché funziona

* `InsertForms2OleControl` indica a Word di incorporare un oggetto OLE di tipo **CommandButton**, che è la classe classica del pulsante ActiveX.  
* Gli argomenti di larghezza e altezza impostano direttamente **la dimensione del pulsante**; Word traduce i valori da punti (1 pt ≈ 1/72 in).  
* Dare un nome al controllo (`Name = "btnSubmit"`) lo rende facile da individuare da VBA (`ActiveDocument.InlineShapes("btnSubmit")`).  

---

## Impostare la dimensione e la didascalia del pulsante

Se desideri un aspetto diverso, regola i valori numerici nella chiamata a `InsertForms2OleControl`. La firma del metodo è:

```csharp
Forms2OleControl InsertForms2OleControl(string progId, double width, double height);
```

* **progId** – L'identificatore programmatico della classe ActiveX (`"CommandButton"` per un pulsante standard).  
* **width / height** – Dimensione in punti. Per un pulsante largo 2 cm, usa `width = 56.7` (2 cm ≈ 56.7 pt).  

Puoi anche modificare la didascalia dopo l'inserimento:

```csharp
commandButton.Caption = "Send Request";
```

Cambiare la didascalia non influisce sulla dimensione, ma modifica il feedback visivo per l'utente.

### Consiglio professionale

Se vuoi un pulsante quadrato, imposta entrambe le dimensioni allo stesso valore:

```csharp
Forms2OleControl squareBtn = builder.InsertForms2OleControl("CommandButton", 50, 50);
squareBtn.Caption = "OK";
```

---

## Aggiungere un pulsante a Word e renderlo cliccabile

Il codice sopra già **add button to Word**. Per far sì che il pulsante esegua un'azione, devi scrivere una macro VBA che gestisca l'evento `Click`. Ecco una macro minima che puoi incollare nell'editor VBA di Word (`Alt+F11` → Insert → Module):

```vba
Sub btnSubmit_Click()
    MsgBox "You clicked the Submit button!", vbInformation
End Sub
```

Poiché il controllo è nominato `btnSubmit`, Word mappa automaticamente l'evento `Click` a `btnSubmit_Click`. Questo è il modo standard per **create clickable button** senza librerie esterne.

> **Nota:** Le impostazioni di sicurezza delle macro in Word potrebbero bloccare i controlli ActiveX. Assicurati che sia selezionata “Enable all macros” o “Enable VBA macros” per il documento, oppure firma digitalmente la macro per l'uso in produzione.

---

## Domande comuni: come inserire un pulsante e risolvere i problemi

### 1. Cosa succede se il pulsante non appare dopo il salvataggio?

* Verifica che la versione di Aspose.Words supporti `InsertForms2OleControl`. Le versioni precedenti alla 22.5 non includono questa funzionalità.  
* Assicurati che il formato di file di destinazione sia `.docx` o `.doc`. Formati più vecchi come `.rtf` non possono memorizzare oggetti ActiveX.

### 2. Posso inserire il pulsante in un segnalibro specifico?

Sì. Sposta il builder sul segnalibro prima di chiamare `InsertForms2OleControl`:

```csharp
builder.MoveToBookmark("InsertHere");
builder.InsertForms2OleControl("CommandButton", 100, 30);
```

### 3. Come **impostare la dimensione del pulsante** dinamicamente in base alla lunghezza del testo?

Calcola la larghezza necessaria usando il metodo `Graphics.MeasureString` (da `System.Drawing`) e converti i pixel in punti (`points = pixels * 72 / DPI`). Quindi passa la larghezza calcolata a `InsertForms2OleControl`.

### 4. È possibile aggiungere più pulsanti in un ciclo?

Assolutamente. Avvolgi la logica di inserimento in un ciclo `for` e regola le proprietà `Left` e `Top` per ogni iterazione:

```csharp
for (int i = 0; i < 3; i++)
{
    Forms2OleControl btn = builder.InsertForms2OleControl("CommandButton", 80, 25);
    btn.Name = $"btnOption{i + 1}";
    btn.Caption = $"Option {i + 1}";
    btn.Left = 50;
    btn.Top = 100 + i * 40; // stagger vertically
}
```

---

## Output previsto

Quando esegui il programma e apri **ActiveXButton.docx**:

* Un singolo pulsante **Submit** appare vicino all'angolo in alto a sinistra della prima pagina.  
* La dimensione del pulsante corrisponde alle dimensioni fornite (`100 pt × 30 pt`).  
* Se hai aggiunto la macro VBA, cliccando il pulsante verrà mostrata una finestra di messaggio: “You clicked the Submit button!”.

Ora hai creato con successo **create ActiveX control**, **set button size**, e **add button to Word** imparando anche **how to insert button** e **create clickable button** per future attività di automazione.

---

## Conclusione

In questo tutorial hai imparato a **create ActiveX control** all'interno di un documento Word con C#. Seguendo i passaggi puoi **set button size**, assegnare al controllo un nome significativo e **add button to Word** affinché diventi un **clickable button** collegato a una macro VBA.  

Da qui potresti approfondire:

* Collegare il pulsante a un add‑in COM .NET invece di VBA.  
* Utilizzare altre classi ActiveX come `CheckBox` o `ComboBox`.  
* Automatizzare la creazione di moduli completi con più controlli.

Sentiti libero di sperimentare con dimensioni diverse.

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare ulteriori funzionalità dell'API ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Create Word Document with Floating Image in .NET](/words/english/net/add-content-using-document-builder/insert-floating-image/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Create Accessible PDF from Word – Complete Guide](/words/english/net/programming-with-pdfsaveoptions/create-accessible-pdf-from-word-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}