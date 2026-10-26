---
category: general
date: 2026-10-26
description: Scopri come creare un documento Word in C# e aggiungere un pulsante ActiveX
  programmaticamente. Questa guida passo‑passo copre l'inserimento di un pulsante
  di comando, la sua nasconditura in fase di progettazione e il salvataggio del file.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- how to add activex button
- create command button word
- programmatically add command button
language: it
lastmod: 2026-10-26
og_description: Crea un documento Word in C# e aggiungi programmaticamente un pulsante
  ActiveX. Segui questo tutorial completo per incorporare un pulsante di comando che
  appare solo durante l'esecuzione.
og_image_alt: Screenshot of a Word document created with C# that contains an ActiveX
  command button
og_title: Crea un documento Word in C# con un pulsante di comando ActiveX – guida
  completa
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn how to create Word document C# and add an ActiveX button programmatically.
    This step‑by‑step guide covers inserting a command button, hiding it at design
    time, and saving the file.
  headline: How to create Word document C# with an ActiveX command button
  type: TechArticle
tags:
- C#
- Aspose.Words
- ActiveX
- Word automation
title: Come creare un documento Word in C# con un pulsante di comando ActiveX
url: /it/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-with-an-activex-command-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come creare un documento Word C# con un pulsante di comando ActiveX

Se hai bisogno di **creare un documento Word C#** che contenga un pulsante interattivo, questa guida ti mostra esattamente come fare. Dopo le prime due frasi avrai chiara l'approccio generale, e i passaggi successivi ti accompagneranno riga per riga nel codice da scrivere.

Imparerai ad aggiungere un pulsante ActiveX, a nasconderlo durante la progettazione e a renderlo visibile solo quando l'utente apre il file. Il tutorial copre anche le insidie più comuni, come gli avvisi di sicurezza e la compatibilità di versione, così potrai distribuire documenti affidabili.

## Prerequisiti

Prima di iniziare, assicurati di avere:

* .NET 6.0 o successivo installato  
* Una copia con licenza di **Aspose.Words for .NET** (la versione di prova gratuita è sufficiente per sperimentare)  
* Familiarità di base con C# e Visual Studio (qualsiasi IDE che supporti .NET va bene)  

Non sono necessari altri pacchetti NuGet oltre a `Aspose.Words`.

## Passo 1: Creare un documento Word C# e inizializzare il DocumentBuilder

Il primo passo è istanziare un oggetto `Document` e un `DocumentBuilder`. Il `Document` rappresenta l'intero file .docx, mentre il `DocumentBuilder` fornisce metodi fluent per aggiungere contenuti.

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Create a new empty document.
        Document document = new Document();

        // Attach a builder to the document so we can insert nodes.
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Perché è importante:** Senza un `DocumentBuilder` dovresti manipolare manualmente il DOM OpenXML, operazione soggetta a errori e più difficile da leggere. Il builder astrae questi dettagli e garantisce un file Word ben formato.

## Passo 2: Come aggiungere un pulsante ActiveX – inserire un controllo CommandButton

Ora inseriamo un **controllo CommandButton ActiveX** in una posizione specifica. Il rettangolo definisce la posizione del pulsante (X, Y) e le dimensioni (larghezza, altezza) in punti.

```csharp
        // Define the button's position and size.
        RectangleF buttonRect = new RectangleF(100, 100, 120, 30);

        // Insert the ActiveX CommandButton control.
        builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,   // Type of ActiveX control
            buttonRect,                          // Geometry
            "ClickMe");                          // Caption shown at design time
```

**Perché è importante:** `InsertForms2OleControl` è l'unico metodo di Aspose.Words che crea un vero oggetto ActiveX OLE. Il valore enum `Forms2OleControlType.CommandButton` indica a Word di incorporare un pulsante cliccabile anziché un contenitore OLE generico.

## Passo 3: Aggiungere programmaticamente il pulsante di comando – nasconderlo fino al runtime

Word tratta qualsiasi forma inserita come visibile per impostazione predefinita. Per mantenere il pulsante invisibile durante la progettazione del modello, imposta la proprietà `Hidden` sulla forma appena creata dal builder.

```csharp
        // Retrieve the shape that represents the newly added control.
        Shape oleShape = (Shape)builder.CurrentParagraph.GetChildNodes(NodeType.Shape, true)[0];

        // Hide the shape; it will become visible when the document is opened.
        oleShape.Hidden = true;
```

**Perché è importante:** Impostare `Hidden = true` impedisce al pulsante di ingombrare la vista di progettazione. Quando il documento viene aperto in Word, l'ambiente di runtime rivela automaticamente il controllo, preservando l'esperienza utente prevista.

## Passo 4: Salvare il file – creare il documento Word con pulsante di comando

Infine, scrivi il documento su disco. Scegli un percorso a cui la tua applicazione possa scrivere e usa l'estensione `.docx` per garantire la compatibilità moderna.

```csharp
        // Save the document containing the ActiveX button.
        document.Save(@"C:\Temp\ActiveXButton.docx");
    }
}
```

**Perché è importante:** Salvare come `.docx` garantisce che il controllo ActiveX incorporato rispetti lo standard Office Open XML, supportato da Word 2007 e versioni successive. Se ti serve il supporto legacy a `.doc`, cambia l'estensione e usa `SaveFormat.Doc`.

## Esempio completo funzionante

Mettendo tutto insieme, ecco il programma completo che puoi copiare, incollare ed eseguire:

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Step 1: Create a new document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a CommandButton ActiveX control.
        RectangleF commandButtonRect = new RectangleF(100, 100, 120, 30);
        builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton,
            commandButtonRect,
            "ClickMe");

        // Step 3: Hide the control so it appears only at runtime.
        Shape oleShape = (Shape)builder.CurrentParagraph
                                         .GetChildNodes(NodeType.Shape, true)[0];
        oleShape.Hidden = true;

        // Step 4: Save the document containing the ActiveX control.
        document.Save(@"C:\Temp\ActiveX.docx");
    }
}
```

**Output previsto:** Dopo aver eseguito il programma, apri `C:\Temp\ActiveX.docx` in Microsoft Word. Vedrai un documento vuoto; il pulsante non è visibile in modalità progettazione. Premi **Alt + F9** per alternare i codici campo, poi clicca sull'area del pulsante—Word renderizzerà il controllo ActiveX e potrai interagire con esso (ad es., doppio‑click per visualizzarne le proprietà).

## Casi limite e consigli di best‑practice

| Situazione | Cosa controllare | Correzione consigliata |
|-----------|-------------------|------------------------|
| **L'utente disabilita ActiveX** | Word può mostrare un avviso di sicurezza o bloccare il controllo. | Istruisci gli utenti finali ad abilitare “ActiveX controls” nel Trust Center, oppure fornisci un’alternativa macro‑firmata. |
| **Documento aperto in Word Online** | Word Online non supporta ActiveX; il pulsante verrà omesso. | Usa un collegamento ipertestuale di fallback o un content control se ti serve la compatibilità cloud. |
| **Impostazioni DPI diverse** | Le dimensioni del rettangolo possono apparire più grandi o più piccole su display ad alta DPI. | Usa `GraphicsUnit.Point` (impostazione predefinita) e testa su DPI comuni (96 dpi, 120 dpi). |
| **Pulsanti multipli** | La chiamata `GetChildNodes(NodeType.Shape, true)[0]` restituisce solo la prima forma. | Itera su `builder.CurrentParagraph.GetChildNodes(NodeType.Shape, true)` e imposta `Hidden` per ogni forma aggiunta. |
| **Formato legacy .doc** | Alcune proprietà ActiveX vengono perse salvando come `.doc`. | Preferisci `.docx` a meno che non sia richiesto un vincolo legacy rigoroso. |

**Consiglio esperto:** Dopo aver inserito il pulsante, puoi assegnare una macro alla sua proprietà `OnAction` tramite l'interfaccia di Word. Questo ti consente di definire un comportamento di click personalizzato senza scrivere ulteriore codice C#.

## Domande frequenti

* **Funziona con .NET Core?**  
  Sì. Aspose.Words for .NET è pienamente compatibile con .NET 5, .NET 6 e versioni successive. Basta referenziare lo stesso pacchetto NuGet.

* **Posso cambiare la didascalia del pulsante dopo che il documento è stato generato?**  
  La didascalia impostata in `InsertForms2OleControl` diventa il testo predefinito in fase di progettazione. Gli utenti possono modificarla in Word, ma è anche possibile aggiornare la didascalia programmaticamente accedendo alle proprietà dell'oggetto OLE tramite l'API `Shape.OleFormat`.

* **E se ho bisogno di una dimensione diversa per il pulsante?**  
  Modifica i valori di `RectangleF`. I primi due parametri sono le coordinate X e Y; gli ultimi due sono larghezza e altezza in punti (1 pt = 1/72 pollice).

## Conclusione

Ora sai come **creare un documento Word C#** e **aggiungere programmaticamente un pulsante di comando** usando Aspose.Words. Il tutorial ha coperto l'inizializzazione del documento, l'inserimento di un pulsante ActiveX, la sua nasconditura fino al runtime e il salvataggio del file finale. Con questi blocchi di costruzione puoi incorporare controlli interattivi in qualsiasi modello Word generato.

Prosegui esplorando argomenti correlati come **come aggiungere la gestione degli eventi al pulsante ActiveX**, **creare lo stile del pulsante di comando Word** con VBA, e **aggiungere programmaticamente pulsanti di comando** a documenti esistenti. Estendere questo schema a caselle di controllo, combo box o oggetti OLE personalizzati segue gli stessi passaggi—basta cambiare il valore enum `Forms2OleControlType`.

Inizia a sperimentare: sostituisci la didascalia, regola la posizione o concatena più controlli. Più pratichi, più diventerai fluente nel fornire documenti Word ricchi e interattivi da C#. Buon coding!

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell'API e a esplorare approcci alternativi nei tuoi progetti.

- [Come aggiungere un pulsante di comando programmaticamente in un documento Word](/words/english/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/)
- [Come aggiungere un pulsante ActiveX in un documento Word con Aspose.Words](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)
- [Creare documento Word con pulsante ActiveX – Guida C#](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}