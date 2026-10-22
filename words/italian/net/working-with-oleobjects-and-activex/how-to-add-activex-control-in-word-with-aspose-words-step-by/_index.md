---
category: general
date: 2026-08-07
description: Impara come aggiungere un controllo ActiveX in un documento Word usando
  C#. Include l'associazione di una macro a un pulsante e l'aggiunta di esempi di
  pulsanti cliccabili in Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex control
- associate macro with button
- add clickable button word
- add command button word
language: it
lastmod: 2026-08-07
og_description: Come aggiungere un controllo ActiveX in un documento Word usando Aspose.Words.
  Segui questa guida per inserire un pulsante, associare una macro al pulsante e aggiungere
  una parola pulsante cliccabile.
og_image_alt: Screenshot showing a Word document with an ActiveX command button inserted
  via Aspose.Words
og_title: come aggiungere un controllo ActiveX in Word – tutorial completo C#
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Learn how to add activex control in a Word document using C#. Includes
    associate macro with button and add clickable button word examples.
  headline: how to add activex control in Word with Aspose.Words – step‑by‑step guide
  type: TechArticle
- description: Learn how to add activex control in a Word document using C#. Includes
    associate macro with button and add clickable button word examples.
  name: how to add activex control in Word with Aspose.Words – step‑by‑step guide
  steps:
  - name: Why each line matters
    text: '| Line | Purpose | |------|---------| | `Document doc = new Document();`
      | Instantiates a fresh Word package in memory. | | `DocumentBuilder builder
      = new DocumentBuilder(doc);` | Provides a fluent API for inserting content,
      including ActiveX controls. | | `InsertForms2OleControl` | The only Aspose.'
  - name: Common pitfalls when associating a macro
    text: '* **Macro security settings** – If the document is opened on a machine
      with strict security policies, the macro may be blocked. Provide instructions
      to lower the security level or sign the macro. * **Naming conflicts** – The
      macro name must be unique within the document’s VBA project; otherwise Word'
  - name: 'Edge case: Long captions'
    text: Word truncates captions that exceed the button’s width. To avoid clipping,
      either increase the width argument in `InsertForms2OleControl` or shorten the
      text. Testing with different languages (e.g., German or Japanese) is advisable
      because character width varies.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: come aggiungere un controllo ActiveX in Word con Aspose.Words – guida passo
  passo
url: /it/net/working-with-oleobjects-and-activex/how-to-add-activex-control-in-word-with-aspose-words-step-by/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# come aggiungere un controllo ActiveX in Word con Aspose.Words

Se hai bisogno di **come aggiungere un controllo ActiveX** in un file Microsoft Word in modo programmatico, questo tutorial ti mostra i passaggi esatti usando Aspose.Words per .NET. Vedrai come inserire un pulsante di comando, impostarne la didascalia e **associare macro al pulsante** in modo che il controllo reagisca quando l'utente lo clicca. Alla fine avrai un file `.docm` abilitato alle macro che contiene un pulsante pienamente funzionante.

Aggiungere un pulsante ActiveX è una necessità comune quando si creano modelli interattivi come domande di prestito, moduli di inserimento dipendenti o report automatizzati. Questa guida analizza ogni riga di codice, spiega **perché** ogni passaggio è importante e copre le tipiche insidie che potresti incontrare.

## Prerequisiti

* .NET 6 (o .NET Core 3.1 / .NET Framework 4.8) installato.  
* Una licenza valida di Aspose.Words per .NET o una chiave di valutazione temporanea.  
* Visual Studio 2022 (o qualsiasi IDE che supporti C#).  
* Familiarità di base con le macro di Word (VBA) se prevedi di scrivere la macro che il pulsante attiverà.

> **Suggerimento:** Quando esegui l'esempio, salva l'output in una cartella per cui hai i permessi di scrittura, altrimenti `doc.Save` genererà un'eccezione.

## Come aggiungere un controllo ActiveX in un documento Word usando Aspose.Words

Il nucleo della soluzione è un breve programma C# che crea un nuovo documento, inserisce un controllo ActiveX **CommandButton** e salva il file come documento abilitato alle macro (`.docm`). Il codice è completo e pronto per il copia‑incolla.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert an ActiveX CommandButton control (Forms2OleControl)
        // Parameters: control type, left, top, width, height (in points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            0,   // left position (points)
            0,   // top position (points)
            150, // width (points)
            30   // height (points)
        );

        // Step 3: Set the button's visible caption – this is the add clickable button word
        commandButton.Caption = "Click Me";

        // Step 4 (optional): Associate a macro with the button's click action
        // This demonstrates how to associate macro with button
        commandButton.OnAction = "MyMacro";

        // Step 5: Save the document as a macro‑enabled file to preserve the button reference
        // The file extension .docm tells Word to keep ActiveX controls and macros
        doc.Save("CommandButton.docm");
    }
}
```

### Perché ogni riga è importante

| Riga | Scopo |
|------|-------|
| `Document doc = new Document();` | Istanzia un nuovo pacchetto Word in memoria. |
| `DocumentBuilder builder = new DocumentBuilder(doc);` | Fornisce un'API fluida per inserire contenuti, inclusi controlli ActiveX. |
| `InsertForms2OleControl` | L'unico metodo di Aspose.Words che crea un controllo ActiveX; specifichi il tipo di controllo (`CommandButton`) e la sua geometria. |
| `commandButton.Caption = "Click Me";` | Imposta il **testo del pulsante cliccabile** che l'utente finale vede. Senza una didascalia il pulsante appare vuoto. |
| `commandButton.OnAction = "MyMacro";` | **associare macro al pulsante** – indica a Word quale macro VBA eseguire quando il controllo viene cliccato. |
| `doc.Save("CommandButton.docm");` | Salva il documento come file abilitato alle macro; un normale `.docx` rimuoverebbe il controllo e la macro. |

> **Nota:** Le coordinate (sinistra, alto) sono misurate in punti (1 pt ≈ 1/72 in). Regolale per posizionare il pulsante dove ti serve nella pagina.

## Come associare una macro al pulsante

La proprietà `OnAction` collega il pulsante a una macro VBA chiamata `MyMacro`. Devi ancora creare quella macro all'interno del file Word, manualmente o iniettando codice VBA programmaticamente (Aspose.Words non scrive codice VBA). Ecco una macro minimale che puoi aggiungere usando l'editor **Sviluppatore → Visual Basic** di Word:

```vba
Sub MyMacro()
    MsgBox "Button clicked!", vbInformation, "ActiveX Demo"
End Sub
```

Quando l'utente apre `CommandButton.docm` e clicca il pulsante, Word esegue `MyMacro` e mostra una finestra di messaggio. Se la sicurezza delle macro è impostata su **Disabilita tutte le macro senza notifica**, il pulsante apparirà disabilitato. Consiglia agli utenti di abilitare le macro per il documento o di firmare la macro con un certificato attendibile.

### Problemi comuni nell'associare una macro

* **Impostazioni di sicurezza delle macro** – Se il documento viene aperto su una macchina con politiche di sicurezza rigide, la macro potrebbe essere bloccata. Fornisci istruzioni per abbassare il livello di sicurezza o firmare la macro.  
* **Conflitti di denominazione** – Il nome della macro deve essere unico all'interno del progetto VBA del documento; altrimenti Word genererà errori “nome procedura duplicato”.  
* **Word a 64‑bit vs 32‑bit** – I controlli ActiveX funzionano allo stesso modo, ma l'editor VBA può mostrare messaggi di avviso diversi a seconda della versione di Office.  

## Come aggiungere il testo del pulsante cliccabile a un modulo Word

La proprietà `Caption` è ciò che gli utenti vedono sul pulsante. Puoi personalizzarla ulteriormente:

```csharp
commandButton.Caption = "Submit Form";
commandButton.Font.Size = 10;      // Adjust font size
commandButton.Font.Name = "Arial"; // Choose a readable font
```

Se hai bisogno che la didascalia cambi dinamicamente in base all'input dell'utente, puoi successivamente accedere al controllo tramite il modello a oggetti di Word:

```vba
Sub UpdateButtonCaption()
    Dim btn As InlineShape
    Set btn = ActiveDocument.InlineShapes(1).OLEFormat.Object
    btn.Caption = "Updated Text"
End Sub
```

### Caso limite: Didascalie lunghe

Word tronca le didascalie che superano la larghezza del pulsante. Per evitare il taglio, aumenta l'argomento di larghezza in `InsertForms2OleControl` o abbrevia il testo. È consigliabile testare con diverse lingue (ad es., tedesco o giapponese) perché la larghezza dei caratteri varia.

## Come aggiungere il testo del pulsante di comando per l'automazione del modulo

Oltre alla didascalia visiva, il concetto di **add command button word** riguarda il nome programmatico del controllo. Aspose.Words non espone una proprietà `Name` diretta per i controlli ActiveX, ma è possibile impostare il campo `AltText`, che Word tratta come identificatore del controllo:

```csharp
commandButton.AltText = "SubmitButton";
```

Successivamente in VBA puoi fare riferimento al pulsante tramite il valore `AltText`:

```vba
Sub FindButton()
    Dim shp As Shape
    For Each shp In ActiveDocument.Shapes
        If shp.AlternativeText = "SubmitButton" Then
            MsgBox "Found the Submit button!"
        End If
    Next shp
End Sub
```

Questa tecnica è utile quando hai più pulsanti e devi differenziarli programmaticamente.

## Esempio completo funzionante

Di seguito trovi il programma completo che puoi compilare ed eseguire come applicazione console. Include stilizzazione opzionale, associazione della macro e un blocco di commenti che descrive ogni passaggio.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class AddActiveXButton
{
    static void Main()
    {
        // 1️⃣ Create a new document and a builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert an ActiveX CommandButton.
        //    left=50pt, top=100pt places the button away from the margin.
        Forms2OleControl btn = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            50,   // left
            100,  // top
            200,  // width
            40    // height
        );

        // 3️⃣ Add clickable button word (caption) and style it.
        btn.Caption = "Submit Form";
        btn.Font.Size = 11;
        btn.Font.Name = "Calibri";

        // 4️⃣ Associate macro with button – this is how to associate macro with button.
        btn.OnAction = "SubmitMacro";

        // 5️⃣ Give the control a friendly identifier (add command button word).
        btn.AltText = "SubmitButton";

        // 6️⃣ Save as macro‑enabled document.
        doc.Save("SubmitForm.docm");
    }
}
```

**Risultato atteso:** Aprendo `SubmitForm.docm` in Microsoft Word viene visualizzato un pulsante con bordo blu etichettato *Submit Form*. Cliccando il pulsante si attiva la macro VBA `SubmitMacro` (a condizione che tu abbia aggiunto la macro al documento). Il pulsante può essere spostato, ridimensionato o stilizzato ulteriormente usando lo stesso oggetto `Forms2OleControl`.

## Testare la soluzione

1. Compila ed esegui l'app console C#.  
2. Apri il file `SubmitForm.docm` generato in Word.  
3. Se richiesto, abilita le macro.  
4. Clicca il pulsante *Submit Form* – dovresti vedere la finestra di messaggio definita in `SubmitMacro`.

Se il pulsante appare ma non fa nulla, verifica che il nome della macro corrisponda esattamente (`SubmitMacro`) e che la sicurezza delle macro non ne blocchi l'esecuzione.

## Domande frequenti

| Domanda | Risposta |
|----------|----------|
| *Posso aggiungere più di un pulsante ActiveX?* | Sì. Chiama `InsertForms2OleControl` più volte con coordinate diverse. Usa valori distinti per `OnAction` e `AltText` per differenziarli. |
| *Il controllo ActiveX è visibile in Word Online?* | No. |

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Aggiungere contenuto usando Document Builder in Aspose.Words per .NET](/words/english/net/add-content-using-document-builder/)
- [Tutorial Ombra Forma Aspose.Words – Aggiungere un'ombra a una forma Word in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Aggiungere una nuova sezione a un documento Word | Aspose.Words per .NET](/words/english/net/document-sections/add-section/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}