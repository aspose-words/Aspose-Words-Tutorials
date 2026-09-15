---
category: general
date: 2026-09-14
description: Crea un controllo ActiveX in un documento Word con C#. Scopri come inserire
  ActiveX, aggiungere un pulsante interattivo e generare il file .docx programmaticamente.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex control
- how to insert activex
- add interactive button
- create word document
- create button with code
language: it
lastmod: 2026-09-14
og_description: Crea un controllo ActiveX in un documento Word con C#. Segui questo
  esempio completo per inserire ActiveX, aggiungere un pulsante interattivo e salvare
  il file.
og_image_alt: Screenshot of a Word document containing a newly created ActiveX CommandButton
og_title: Crea un controllo ActiveX in Word con C# – guida passo passo
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Create ActiveX control in a Word document with C#. Learn how to insert
    ActiveX, add interactive button, and generate the .docx file programmatically.
  headline: How to create ActiveX control in a Word document with C#
  type: TechArticle
tags:
- ActiveX
- C#
- Word automation
title: Come creare un controllo ActiveX in un documento Word con C#
url: /it/net/working-with-oleobjects-and-activex/how-to-create-activex-control-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come creare un controllo ActiveX in un documento Word con C#

Se hai bisogno di **creare un controllo ActiveX** all'interno di un file Microsoft Word, questa guida ti mostra una soluzione completa, pronta all'uso. Vedrai esattamente come inserire un ActiveX CommandButton, impostarne le proprietà e salvare il file `.docx` risultante usando solo codice C#.

Aggiungere un pulsante interattivo a un documento Word è una esigenza comune quando si desidera che gli utenti finali attivino macro o logica personalizzata direttamente dall'interfaccia del documento. L'esempio qui sotto dimostra **come inserire ActiveX** senza fare affidamento su strumenti di terze parti, e copre anche **come creare un documento Word** programmaticamente.

Al termine di questo tutorial sarai in grado di **creare un pulsante con codice**, personalizzarne la didascalia e produrre un file Word portatile che conserva il controllo ActiveX.

## Prerequisiti

- .NET 6.0 o successivo (la libreria Aspose.Words per .NET funziona con .NET Core e .NET Framework)
- Un riferimento al pacchetto NuGet `Aspose.Words`  
  ```bash
  dotnet add package Aspose.Words
  ```
- Conoscenza di base di C# e della programmazione orientata agli oggetti

## Passo 1: Configurare il progetto e importare i namespace

Crea un nuovo progetto console (o integra il codice in qualsiasi applicazione C# esistente). Importa i namespace richiesti affinché il compilatore possa individuare le classi di elaborazione Word.

```csharp
using System;
using System.Drawing;               // Provides RectangleF
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
```

> **Perché questo passo è importante** – L'API `Aspose.Words` fornisce le classi `Document`, `DocumentBuilder` e `Forms2OleControl` che consentono di manipolare i file Word a livello di oggetto. Senza questi riferimenti il resto del codice non compilerebbe.

## Passo 2: Creare un nuovo documento Word e un DocumentBuilder

L'oggetto `Document` rappresenta l'intero pacchetto `.docx`, mentre `DocumentBuilder` offre un'API fluida per inserire contenuti.

```csharp
// Step 2: Initialize a fresh Word document
Document document = new Document();

// Attach a builder to the document – the builder knows where to write next
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Spiegazione** – Istanziare un nuovo `Document` ti fornisce una tela pulita. Il cursore del builder inizia all'inizio della prima sezione, pronto per la successiva inserzione.

## Passo 3: Inserire il CommandButton ActiveX

Usa `InsertForms2OleControl` per posizionare un controllo ActiveX in una posizione specifica. Il metodo richiede il tipo di controllo e un `RectangleF` che definisce le coordinate X/Y e le dimensioni (in punti).

```csharp
// Step 3: Add an ActiveX CommandButton at (100,100) with width 120 and height 30
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    OleControlType.CommandButton,
    new RectangleF(100, 100, 120, 30));
```

> **Perché funziona** – `OleControlType.CommandButton` indica all'API di creare un CommandButton Windows standard. Il rettangolo posiziona il pulsante rispetto all'angolo superiore sinistro della pagina, consentendoti di **aggiungere un pulsante interattivo** esattamente dove ti serve.

## Passo 4: Configurare le proprietà del pulsante

Ora imposta il testo visibile del pulsante (`Caption`) e il suo nome interno (`Name`). Queste proprietà sono ciò che gli utenti vedono e a cui il codice VBA può fare riferimento in seguito.

```csharp
// Step 4: Define the button’s caption and programmatic name
commandButton.Caption = "Click Me";
commandButton.Name = "btnClick";
```

> **Consiglio pratico** – Il `Name` deve essere unico all'interno del documento; altrimenti, le macro VBA potrebbero fare riferimento al controllo sbagliato.

## Passo 5: Salvare il documento

Infine, scrivi il file su disco. Il controllo ActiveX è memorizzato all'interno del pacchetto Word, quindi il file salvato manterrà la piena funzionalità quando aperto in Microsoft Word.

```csharp
// Step 5: Persist the document – the ActiveX control stays embedded
string outputPath = @"C:\Temp\CommandButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

> **Risultato** – Aprendo `CommandButton.docx` in Word viene mostrato un CommandButton cliccabile etichettato “Click Me”. Il controllo può essere collegato a una macro tramite l'interfaccia Word (`Developer → Design Mode → Properties`).

## Elenco completo del codice sorgente

Unendo tutti i passaggi si ottiene un unico programma autonomo che puoi copiare, incollare ed eseguire.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Create a new document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert an ActiveX CommandButton at the desired location
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            new RectangleF(100, 100, 120, 30));

        // Set the button's caption and internal name
        commandButton.Caption = "Click Me";
        commandButton.Name = "btnClick";

        // Save the document – the control is preserved
        string outputPath = @"C:\Temp\CommandButton.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### Output previsto

Eseguendo il programma stampa una riga di conferma:

```
Document saved to C:\Temp\CommandButton.docx
```

Quando apri il file generato in Microsoft Word, vedrai un **CommandButton** posizionato alle coordinate specificate. Cliccando il pulsante in modalità design lo evidenzia; in modalità esecuzione si comporta come qualsiasi pulsante ActiveX standard.

## Variazioni comuni e casi limite

| Scenario | Adeguamento |
|----------|------------|
| **Tipo di controllo diverso** | Sostituire `OleControlType.CommandButton` con `OleControlType.CheckBox`, `OleControlType.OptionButton`, ecc. |
| **Pulsanti multipli** | Chiamare `InsertForms2OleControl` più volte, aggiornando le coordinate `RectangleF` per ogni nuovo pulsante. |
| **Dimensionamento dinamico** | Calcolare le dimensioni del rettangolo in base alle dimensioni della pagina (`builder.PageSetup.PageWidth`). |
| **Salvataggio su stream** | Usare `document.Save(stream, SaveFormat.Docx)` quando è necessario restituire il file da un'API web. |
| **Formato Word 97‑2003** | Modificare il formato di salvataggio in `SaveFormat.Doc` per produrre un file `.doc` che incorpora ancora il controllo ActiveX. |

> **Consiglio professionale:** Testa sempre il documento generato sulla versione di Word di destinazione, poiché le versioni più vecchie potrebbero applicare impostazioni di sicurezza che disabilitano i controlli ActiveX per impostazione predefinita.

## Domande frequenti

**Questo funziona con .NET Core?**  
Sì. La libreria Aspose.Words è cross‑platform e pienamente compatibile con .NET Core e .NET 5/6+.

**Posso assegnare una macro al pulsante programmaticamente?**  
L'API non incorpora codice VBA direttamente. Dopo che il documento è stato generato, aprilo in Word, abilita la scheda Developer e registra o scrivi una macro che faccia riferimento a `btnClick`.

**Cosa succede se il pulsante non appare?**  
Verifica che la scheda `Developer` sia abilitata in Word e che il documento non sia aperto in **Protected View**. Controlla inoltre che le coordinate del rettangolo siano entro i margini della pagina.

## Conclusione

Ora sai come **creare un controllo ActiveX** all'interno di un file Word usando C#. Il tutorial ha coperto **come inserire ActiveX**, ha dimostrato **come aggiungere un pulsante interattivo**, ha mostrato **come creare un documento Word** da zero, e ha illustrato **come creare un pulsante con codice** che persiste dopo il salvataggio.  

Da qui puoi esplorare altri tipi di ActiveX, collegare il pulsante a macro VBA, o incorporare la logica in un servizio più ampio di generazione di documenti. Sperimenta con diverse dimensioni, posizioni e proprietà dei controlli per adattare l'esperienza utente esattamente alle tue esigenze.

---

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell'API ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Crea nuovo documento Word](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Crea progetto VBA in documento Word](/words/english/net/working-with-vba-macros/create-vba-project/)
- [Crea e formatta un documento Word in Aspose.Words per .NET](/words/english/net/document-styling/apply-paragraph-style/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}