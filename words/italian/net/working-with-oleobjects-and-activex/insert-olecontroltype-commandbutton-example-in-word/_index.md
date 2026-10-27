---
category: general
date: 2026-08-17
description: Inserisci l'esempio OleControlType.CommandButton in Word usando Aspose.Words.
  Scopri come aggiungere controlli modulo a un documento Word in modo programmatico.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert olecontroltype.commandbutton example
- how to add form controls to word document
- Aspose.Words ActiveX button
- C# Word automation
- programmatic form controls
language: it
lastmod: 2026-08-17
og_description: Inserisci un esempio di OleControlType.CommandButton in Word con Aspose.Words.
  Segui questa guida per aggiungere controlli modulo a un documento Word.
og_image_alt: Screenshot showing an ActiveX CommandButton inserted into a Word document
  using Aspose.Words
og_title: Inserisci esempio di OleControlType.CommandButton in Word
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: Insert OleControlType.CommandButton example in Word using Aspose.Words.
    Learn how to add form controls to a Word document programmatically.
  headline: Insert OleControlType.CommandButton example in Word
  type: TechArticle
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Inserisci esempio di OleControlType.CommandButton in Word
url: /it/net/working-with-oleobjects-and-activex/insert-olecontroltype-commandbutton-example-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Inserisci l'esempio OleControlType.CommandButton in Word

Se hai bisogno di **insert OleControlType.CommandButton example** in un file Word, questa guida ti mostra come fare. Imparerai **how to add form controls to a Word document** usando Aspose.Words, con un programma C# completo e eseguibile.

I controlli modulo come i pulsanti ActiveX ti consentono di creare modelli Word interattivi—utili per contratti, questionari o strumenti interni. I passaggi seguenti coprono tutto, dall'impostazione del progetto alla verifica che il pulsante appaia correttamente nel file `.docx` salvato.

## Prerequisiti

- .NET 6.0 SDK o versioni successive installato  
- Visual Studio 2022 (o qualsiasi IDE C#)  
- Una licenza Aspose.Words per .NET o una licenza temporanea gratuita  
- Familiarità di base con C# e i concetti dei file Word  

> **Pro tip:** Se stai usando la versione di prova gratuita, posiziona il file di licenza nella stessa cartella dell'eseguibile e caricalo all'inizio di `Main`.

## Passo 1: Crea un nuovo progetto console e aggiungi Aspose.Words

Apri un terminale ed esegui:

```bash
dotnet new console -n OleCommandButtonDemo
cd OleCommandButtonDemo
dotnet add package Aspose.Words
```

## Passo 2: Scrivi il programma completo

Crea o sostituisci `Program.cs` con il codice seguente. Contiene tutte le direttive `using` necessarie, il caricamento della licenza e il flusso di lavoro a quattro passaggi mostrato nello snippet originale.

```csharp
using System;
using System.Drawing;               // For Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;          // For OleControlType

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Optional: load a trial or commercial license.
        // -------------------------------------------------
        // var license = new Aspose.Words.License();
        // license.SetLicense("Aspose.Words.lic");

        // -------------------------------------------------
        // Step 1: Create a new blank document
        // -------------------------------------------------
        Document doc = new Document();

        // -------------------------------------------------
        // Step 2: Initialize a DocumentBuilder to work with the document
        // -------------------------------------------------
        DocumentBuilder builder = new DocumentBuilder(doc);

        // -------------------------------------------------
        // Step 3: Insert an ActiveX CommandButton control
        // -------------------------------------------------
        // OleControlType.CommandButton creates a CommandButton.
        // "ClickMe" is the control's name.
        // The Rectangle defines the button's position (x, y) and size (width, height).
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            "ClickMe",
            new Rectangle(100, 100, 80, 30));

        // -------------------------------------------------
        // Step 4: Save the document containing the ActiveX button
        // -------------------------------------------------
        string outputPath = "ActiveXButton.docx";
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### Perché ogni riga è importante

* **License loading** – garantisce che non sei limitato dalle restrizioni di valutazione.  
* **`Document doc = new Document();`** – crea il contenitore per tutto il contenuto Word; è la base del **insert OleControlType.CommandButton example**.  
* **`DocumentBuilder builder = new DocumentBuilder(doc);`** – fornisce un'API fluida per aggiungere testo, immagini e controlli.  
* **`InsertForms2OleControl`** – il metodo principale che implementa **how to add form controls to a Word document**. Il valore enum `OleControlType.CommandButton` indica ad Aspose.Words di creare un pulsante ActiveX.  
* **`new Rectangle(100, 100, 80, 30)`** – posiziona il pulsante a 100 pt dal margine sinistro e superiore, con una larghezza di 80 pt e un'altezza di 30 pt. Regola questi valori per adattarli al tuo layout.  
* **`doc.Save`** – scrive il file .docx su disco; il file ora contiene il pulsante incorporato.

## Passo 3: Compila ed esegui il programma

Dalla cartella del progetto, esegui:

```bash
dotnet run
```

Dovresti vedere il messaggio nella console:

```
Document saved to ActiveXButton.docx
```

Apri `ActiveXButton.docx` in Microsoft Word. Vedrai un pulsante con l'etichetta **ClickMe** posizionato approssimativamente al centro della pagina. Cliccare il pulsante attiva il comportamento predefinito di ActiveX (che di solito non fa nulla a meno che non venga associata una macro).

![esempio insert olecontroltype.commandbutton](/images/activex-button.png "ActiveX CommandButton inserito in un documento Word")

*Testo alternativo dell'immagine:* insert olecontroltype.commandbutton example – un ActiveX CommandButton visualizzato in un documento Word.

## Passo 4: Personalizzare il pulsante (opzionale)

L'esempio base **insert OleControlType.CommandButton example** crea un pulsante predefinito. Puoi modificare la sua didascalia, il carattere o persino allegare una macro modificando l'oggetto OLE sottostante. Di seguito trovi un modo conciso per cambiare la didascalia del pulsante dopo l'inserimento:

```csharp
// Retrieve the first shape (our button) from the document
Shape buttonShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

// Access the OLE format and set the caption
buttonShape.OleFormat.GetControl().SetProperty("Caption", "Submit");
```

> **Nota:** La manipolazione diretta delle proprietà OLE richiede la comprensione dell'interfaccia COM sottostante. Per la maggior parte degli scenari, la didascalia predefinita è sufficiente.

## Passo 5: Problemi comuni e come evitarli

| Problema | Perché accade | Soluzione |
|----------|----------------|-----------|
| Il pulsante non appare in Word | Il documento è stato salvato come `.docx` ma aperto in un visualizzatore che rimuove i controlli OLE (es. Google Docs). | Apri il file in Microsoft Word o Word Online con diritti di modifica. |
| Errore di runtime `ArgumentOutOfRangeException` | Le coordinate `Rectangle` sono fuori dai margini della pagina. | Usa valori all'interno delle dimensioni della pagina (es. 0‑500 per A4). |
| Eccezione di licenza | Una licenza di prova scade dopo 30 giorni. | Carica un file di licenza valido o richiedi una prova estesa da Aspose. |

## Passo 6: Come questo esempio si inserisce in progetti di automazione più ampi

Quando devi **how to add form controls to Word document** su larga scala—ad esempio generare centinaia di modelli di contratto—racchiudi la logica di inserimento in un metodo riutilizzabile:

```csharp
static void AddCommandButton(DocumentBuilder builder, string name, Rectangle bounds)
{
    builder.InsertForms2OleControl(OleControlType.CommandButton, name, bounds);
}
```

Puoi quindi chiamare `AddCommandButton` all'interno di cicli che elaborano le righe di dati, assicurando che ogni documento generato contenga un pulsante con nome univoco (es. `Approve_001`, `Approve_002`).

## Conclusione

Ora disponi di un **insert OleControlType.CommandButton example** completo che dimostra **how to add form controls to a Word document** usando Aspose.Words per .NET. Il tutorial ha coperto l'impostazione del progetto, il codice sorgente completo, suggerimenti di personalizzazione e i passaggi comuni di risoluzione dei problemi.

Da qui potresti esplorare:

- Aggiungere altri tipi di controllo come **CheckBox** o **ComboBox** (`OleControlType.CheckBox`, `OleControlType.ComboBox`).  
- Associare il pulsante a una macro VBA per una maggiore interattività.  
- Generare PDF dallo stesso documento mantenendo i campi modulo.

Sperimenta con diverse dimensioni, posizioni e nomi di controllo per adattarli al tuo caso d'uso specifico. Buon coding!

## Cosa dovresti imparare dopo?

I tutorial seguenti coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice funzionanti completi con spiegazioni passo passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Insert Combo Box Form Field In Word Document](/words/english/net/add-content-using-documentbuilder/insert-combo-box-form-field/)
- [Insert Check Box Form Field In Word Document](/words/english/net/add-content-using-documentbuilder/insert-check-box-form-field/)
- [Insert Text Input Form Field In Word Document](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}