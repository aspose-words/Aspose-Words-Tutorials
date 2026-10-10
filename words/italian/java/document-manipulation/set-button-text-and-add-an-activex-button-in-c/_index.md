---
category: general
date: 2026-10-10
description: Imposta il testo del pulsante e aggiungi un pulsante ActiveX in C# usando
  Aspose.Words. Scopri come inserire un pulsante, creare un controllo pulsante e personalizzare
  la didascalia in un documento Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button text
- how to insert button
- create button control
- add activex control
- add activex button
language: it
lastmod: 2026-10-10
og_description: Imposta il testo del pulsante e aggiungi un pulsante ActiveX in C#
  con Aspose.Words. Segui questa guida passo‑passo per inserire un pulsante, creare
  il controllo del pulsante e personalizzare la sua didascalia.
og_image_alt: Screenshot of a Word document showing an ActiveX button with custom
  text
og_title: Imposta il testo del pulsante e aggiungi un pulsante ActiveX in C# – guida
  completa
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Set button text and add an ActiveX button in C# using Aspose.Words.
    Learn how to insert button, create button control, and customize the caption in
    a Word document.
  headline: Set button text and add an ActiveX button in C#
  type: TechArticle
tags:
- ActiveX
- C#
- Aspose.Words
- button control
- document automation
title: Imposta il testo del pulsante e aggiungi un pulsante ActiveX in C#
url: /it/java/document-manipulation/set-button-text-and-add-an-activex-button-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Imposta il testo del pulsante e aggiungi un pulsante ActiveX in C#

Se devi **impostare il testo del pulsante** su un pulsante ActiveX all'interno di un documento Word, questa guida ti mostra esattamente come fare. Alla fine del tutorial sarai in grado di **inserire un pulsante**, creare un **controllo pulsante** e personalizzare la sua didascalia con poche righe di codice C#.

Lavorare con i controlli ActiveX è comune quando vuoi moduli interattivi in Word—sia che tu stia creando un modello di contratto, un sondaggio o uno strumento interno. L'esempio utilizza Aspose.Words per .NET, una libreria che consente di manipolare file Word senza avere Microsoft Office installato.

## Prerequisiti

Prima di iniziare, assicurati di avere:

* .NET 6.0 SDK o versioni successive installate  
* Visual Studio 2022 (o qualsiasi IDE che supporti C#)  
* Una licenza di Aspose.Words per .NET (la valutazione gratuita è sufficiente per l'apprendimento)  

Hai inoltre bisogno di un riferimento al pacchetto NuGet `Aspose.Words`:

```bash
dotnet add package Aspose.Words
```

## Come inserire un pulsante in un documento Word

Il primo passo è creare un nuovo `Document` e un `DocumentBuilder`. Il builder è il punto di ingresso per aggiungere contenuti, inclusi i controlli ActiveX.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Perché è importante:** `Document` rappresenta l'intero file .docx, mentre `DocumentBuilder` fornisce metodi di alto livello come `InsertParagraph` e `InsertFormField`. Partire da un documento vuoto garantisce che il pulsante appaia esattamente dove lo desideri.

## Crea il controllo pulsante con Forms2OleControl

Ora creiamo il vero e proprio controllo pulsante. `Forms2OleControl` è la classe che Aspose.Words usa per tutti gli oggetti ActiveX, e il tipo `COMMANDBUTTON` viene visualizzato come un pulsante cliccabile in Word.

```csharp
        // Step 2: Insert a Forms2OleControl of type COMMANDBUTTON
        Forms2OleControl button = builder.InsertForms2OleControl(
            Forms2OleControlType.COMMANDBUTTON, // control type
            100,  // left position (points)
            50,   // top position (points)
            200,  // width (points)
            150); // height (points)
```

**Spiegazione:**  
* `InsertForms2OleControl` posiziona il controllo alle coordinate esatte che fornisci.  
* La dimensione è definita in punti (1 punto = 1/72 di pollice). Regola questi numeri per adattarli al tuo layout.

## Aggiungi il controllo ActiveX e assegnagli un nome univoco

Ogni oggetto ActiveX dovrebbe avere un nome distinto così da poterlo richiamare in seguito (ad esempio, quando gestisci eventi in VBA).

```csharp
        // Step 3: Assign a unique name to the control
        button.SetName("MyActiveXButton");
```

**Consiglio:** Evita spazi o caratteri speciali nel nome; Word tratta il nome come un identificatore nel suo modello di modulo interno.

## Imposta il testo del pulsante (didascalia) sul pulsante ActiveX

Qui entra in gioco la parola chiave principale **set button text**. La proprietà `Caption` definisce l'etichetta che gli utenti vedono sul pulsante.

```csharp
        // Step 4: Set the text that appears on the button
        button.SetCaption("Click Me");
```

Puoi modificare la didascalia in qualsiasi momento prima di salvare il documento. Se in seguito devi localizzare l'interfaccia, chiama semplicemente `SetCaption` di nuovo con una stringa diversa.

## Salva il documento e verifica il risultato

Infine, scrivi il documento su disco. Aprendo il file in Microsoft Word vedrai il pulsante con la didascalia personalizzata.

```csharp
        // Step 5: Save the document
        doc.Save("ActiveXButton.docx");
        System.Console.WriteLine("Document created with an ActiveX button.");
    }
}
```

**Output previsto:** Quando apri *ActiveXButton.docx* in Word, vedrai un pulsante posizionato alle coordinate specificate, etichettato **Click Me**. Cliccando il pulsante si attiverà il comportamento predefinito del pulsante di comando di Word (che potrai personalizzare in seguito con VBA).

![Esempio di impostazione del testo del pulsante](https://example.com/activex-button.png){alt="Esempio di impostazione del testo del pulsante"}

## Aggiungi un pulsante ActiveX e gestisci gli eventi (opzionale)

Se desideri che il pulsante esegua un'azione personalizzata, puoi aggiungere una macro VBA che reagisce all'evento `Click`. La macro può essere iniettata programmaticamente, ma questo è al di fuori dello scopo di questo tutorial. La parte importante è che il pulsante è già presente e la sua didascalia è impostata—pronto per qualsiasi gestione degli eventi tu voglia implementare.

## Problemi comuni e come evitarli

| Problema | Perché accade | Soluzione |
|----------|----------------|-----------|
| Il pulsante appare disallineato | Le coordinate sono in punti, non in pixel | Converti i valori pixel in punti (`points = pixels * 72 / DPI`) |
| La didascalia non cambia dopo il salvataggio | `SetCaption` chiamato dopo `Save` | Imposta sempre la didascalia **prima** di chiamare `doc.Save` |
| Controllo non visibile in versioni più vecchie di Word | Alcune versioni più vecchie di Word non supportano pienamente ActiveX | Testa sulla versione di Word di destinazione; considera l'uso di `CheckBox` o `DropDownList` come alternativa |
| Avviso di licenza nell'output | La licenza di valutazione scade | Applica una licenza valida di Aspose.Words tramite `License license = new License(); license.SetLicense("Aspose.Words.lic");` |

## Esempio completo, eseguibile

Di seguito trovi il programma completo che puoi copiare, incollare ed eseguire. Include tutte le direttive `using` necessarie e dimostra l'intero flusso di lavoro dalla creazione del documento al salvataggio.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXButtonDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new document and builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert an ActiveX command button at a specific location
            Forms2OleControl button = builder.InsertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON,
                100,   // left (points)
                50,    // top (points)
                200,   // width (points)
                150);  // height (points)

            // Give the button a unique identifier
            button.SetName("MyActiveXButton");

            // Set the visible text on the button (set button text)
            button.SetCaption("Click Me");

            // Save the document
            const string outputPath = "ActiveXButton.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}. Open it in Word to see the button.");
        }
    }
}
```

Esegui il programma con `dotnet run`. Dopo l'esecuzione, apri *ActiveXButton.docx* per confermare che la didascalia del pulsante sia **Click Me**.

## Riepilogo di quanto hai imparato

* Hai imparato come **set button text** su un pulsante ActiveX usando Aspose.Words.  
* Hai visto i passaggi esatti per **how to insert button**, **create button control** e **add activex control** a un documento Word.  
* Ora disponi di uno snippet di codice riutilizzabile che puoi adattare a qualsiasi progetto di automazione Word basato su moduli.

## Prossimi passi

* Esplora altri valori `Forms2OleControlType` come `CHECKBOX` o `LISTBOX` per creare moduli più ricchi.  
* Combina il pulsante con una macro VBA per eseguire calcoli o convalide dei dati.  
* Usa l'API `FormField` di Aspose.Words per leggere l'input dell'utente dopo che il documento è stato compilato.

Sentiti libero di sperimentare dimensioni, posizione e didascalia per adattarle ai requisiti del tuo design. Se incontri problemi, la documentazione di Aspose.Words fornisce riferimenti dettagliati per ogni classe utilizzata in questo tutorial.

Buon coding!

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell'API e a esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [Add Shadow to Shape in Word with Aspose.Words – Step‑by‑Step](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-word-with-aspose-words-step-by-step/)
- [Add Page Numbers to the Footer of a Word Document Using Aspose.Words for .NET](/words/english/net/working-with-headers-and-footers/add-page-numbers/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}