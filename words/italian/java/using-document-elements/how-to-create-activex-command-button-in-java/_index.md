---
category: general
date: 2026-10-07
description: Crea un pulsante di comando ActiveX in Java e aggiungilo programmaticamente
  ai documenti Word. Scopri come impostare le posizioni in alto a sinistra del pulsante.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex command button
- programmatically add command button
- how to set button left top
language: it
lastmod: 2026-10-07
og_description: Crea un pulsante di comando ActiveX in Java per incorporare controlli
  interattivi nei tuoi documenti Word. Scopri come aggiungere programmaticamente il
  pulsante di comando, impostarne la posizione e personalizzarne l'aspetto.
og_image_alt: Screenshot showing a created ActiveX command button in a Java‑generated
  Word document
og_title: Crea un pulsante di comando ActiveX in Java – guida passo passo
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Create ActiveX command button in Java and programmatically add command
    button to Word docs. Learn how to set button left top positions.
  headline: How to create ActiveX command button in Java
  type: TechArticle
- description: Create ActiveX command button in Java and programmatically add command
    button to Word docs. Learn how to set button left top positions.
  name: How to create ActiveX command button in Java
  steps:
  - name: How to set button left top
    text: Positioning the button is where the secondary keyword **how to set button
      left top** becomes relevant. The `setLeft` and `setTop` methods accept values
      measured in points (1 point = 1/72 in).
  - name: Adding multiple buttons
    text: If you need several buttons, repeat **Step 2** and **Step 3** for each control.
      Remember to adjust `setLeft` and `setTop` so the buttons don’t overlap.
  - name: Changing button behavior
    text: 'ActiveX buttons can run VBA macros when clicked. To attach a macro, set
      the `setOnAction` property with the macro name:'
  - name: Compatibility notes
    text: '- The button works only in desktop versions of Word that support ActiveX
      (e.g., Word for Windows). It will appear as a static image in Word for Mac or
      online editors. - If you target a mixed environment, consider using a **content
      control** (`RichTextContentControl`) instead of an ActiveX control.'
  - name: Next steps
    text: '- Explore other ActiveX controls such as `Forms.TextBox.1` or `Forms.CheckBox.1`.
      - Combine multiple controls with a VBA module to implement full‑featured forms.
      - Replace ActiveX with content controls if you need cross‑platform compatibility.'
  type: HowTo
tags:
- ActiveX
- Java
- Aspose.Words
title: Come creare un pulsante di comando ActiveX in Java
url: /it/java/using-document-elements/how-to-create-activex-command-button-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come creare un pulsante di comando ActiveX in Java

Se hai bisogno di **creare un pulsante di comando ActiveX** in un documento Word usando Java, questa guida ti mostra esattamente come fare. Vedrai un esempio completo e eseguibile che **aggiunge programmaticamente un pulsante di comando**, lo posiziona con `setLeft` e `setTop`, e salva il risultato come file `.docx`.

Incorporare un pulsante interattivo ti consente di creare moduli, automatizzare flussi di lavoro o raccogliere input dell'utente direttamente all'interno di un file Word. I passaggi seguenti coprono tutto, dalla configurazione del progetto alla verifica finale, così potrai copiare il codice nel tuo progetto senza perdere alcun dettaglio.

## Prerequisiti

- JDK 17 o versioni successive installate  
- Maven 3.8+ (o lo strumento di build preferito)  
- Aspose.Words per Java 23.9 o successivo – la libreria che fornisce `DocumentBuilder` e il supporto per i controlli OLE  
- Familiarità di base con la sintassi Java e i concetti di programmazione orientata agli oggetti  

Se utilizzi Maven, aggiungi la dipendenza al tuo `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

> **Suggerimento:** Usa l'ultima versione di Aspose.Words per beneficiare di correzioni di bug e nuove funzionalità OLE.

## Passo 1: Crea un nuovo documento vuoto e un DocumentBuilder

Il primo passo per **creare un pulsante di comando ActiveX** è istanziare un `Document` vuoto e un `DocumentBuilder`. Il builder ti offre un'API fluida per inserire contenuti, inclusi i controlli OLE.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` rappresenta il file Word in memoria, mentre `DocumentBuilder` agisce come un cursore che ti permette di posizionare gli elementi esattamente dove ti servono.

## Passo 2: Inserisci un controllo pulsante di comando OLE

I controlli ActiveX vengono inseriti come oggetti OLE. Aspose.Words fornisce la classe `Forms2OleControl` a questo scopo.

```java
        // Step 2: Insert an OLE command button control into the document
        Forms2OleControl commandButton = builder.insertForms2OleControl();
```

Quando chiami `insertForms2OleControl()`, Aspose crea automaticamente una forma segnaposto che ospiterà il pulsante ActiveX.

## Passo 3: Configura le proprietà del pulsante

Ora **aggiungi programmaticamente i dettagli del pulsante di comando**, come il suo ProgID, la didascalia e le dimensioni. Il ProgID più comune per un pulsante di comando è `"Forms.CommandButton.1"`.

```java
        // Step 3: Configure the button's properties (type, position, size, caption)
        commandButton.setProgId("Forms.CommandButton.1"); // ActiveX class identifier
        commandButton.setCaption("Click Me");            // Text shown on the button
        commandButton.setWidth(80);                      // Width in points
        commandButton.setHeight(30);                     // Height in points
```

### Come impostare la posizione sinistra e superiore del pulsante

Posizionare il pulsante è dove la parola chiave secondaria **how to set button left top** diventa rilevante. I metodi `setLeft` e `setTop` accettano valori misurati in punti (1 punto = 1/72 in).

```java
        // Position the button 100 points from the left margin and 150 points from the top
        commandButton.setLeft(100);   // Horizontal offset
        commandButton.setTop(150);    // Vertical offset
```

Regola questi numeri per adattarli al tuo layout. Ad esempio, per allineare il pulsante a una cella di tabella, calcola le coordinate della cella e passale a `setLeft`/`setTop`.

## Passo 4: Salva il documento

Infine, scrivi il documento su disco. Il file conterrà il pulsante ActiveX pronto per l'interazione quando aperto in Microsoft Word.

```java
        // Step 4: Save the document containing the button
        doc.save("CommandButton.docx");
        System.out.println("Document saved successfully.");
    }
}
```

Eseguendo il metodo `main` viene prodotto `CommandButton.docx`. Apri il file in Word, abilita il contenuto se richiesto, e vedrai un pulsante cliccabile con etichetta **Click Me** posizionato alle coordinate specificate.

![Create ActiveX command button in Java](/images/activex-button-screenshot.png){.center width=600 alt="Screenshot della creazione di un pulsante di comando ActiveX in Java che mostra il pulsante all'interno del documento Word"}

## Varianti comuni e casi limite

### Aggiungere più pulsanti

Se ti servono diversi pulsanti, ripeti **Passo 2** e **Passo 3** per ogni controllo. Ricorda di regolare `setLeft` e `setTop` affinché i pulsanti non si sovrappongano.

### Modificare il comportamento del pulsante

I pulsanti ActiveX possono eseguire macro VBA quando vengono cliccati. Per collegare una macro, imposta la proprietà `setOnAction` con il nome della macro:

```java
commandButton.setOnAction("MyMacro");
```

Assicurati che il documento di destinazione contenga il modulo VBA corrispondente; altrimenti Word visualizzerà un errore.

### Note di compatibilità

- Il pulsante funziona solo nelle versioni desktop di Word che supportano ActiveX (ad esempio, Word per Windows). Apparirà come un'immagine statica in Word per Mac o negli editor online.  
- Se il tuo target è un ambiente misto, considera l'uso di un **controllo di contenuto** (`RichTextContentControl`) invece di un controllo ActiveX.

## Codice sorgente completo per riferimento

Di seguito trovi l'esempio completo e autonomo che puoi copiare in un nuovo progetto Maven e eseguire immediatamente.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an OLE command button control
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Configure the button
        commandButton.setProgId("Forms.CommandButton.1");
        commandButton.setCaption("Click Me");
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // How to set button left top – position the control
        commandButton.setLeft(100);   // Horizontal offset in points
        commandButton.setTop(150);    // Vertical offset in points

        // Save the resulting document
        doc.save("CommandButton.docx");
        System.out.println("Document saved successfully.");
    }
}
```

**Output previsto:** Dopo l'esecuzione, troverai `CommandButton.docx` nella directory di lavoro del tuo progetto. Aprendo il file in Microsoft Word verrà mostrato un pulsante nella posizione specificata con la didascalia “Click Me”.

## Conclusione

Ora sai come **creare un pulsante di comando ActiveX** in Java, **aggiungere programmaticamente un pulsante di comando** a un documento Word, e controllare con precisione il suo layout usando i metodi **how to set button left top**. Questa tecnica apre la porta a moduli Word ricchi e interattivi che possono attivare macro, avviare applicazioni esterne o raccogliere input dell'utente direttamente nel documento.

### Prossimi passi

- Esplora altri controlli ActiveX come `Forms.TextBox.1` o `Forms.CheckBox.1`.  
- Combina più controlli con un modulo VBA per implementare moduli completi.  
- Sostituisci ActiveX con controlli di contenuto se hai bisogno di compatibilità multipiattaforma.  

Sentiti libero di sperimentare con dimensioni, didascalia e posizionamento per adattarli al design della tua interfaccia. Se incontri problemi, verifica che la versione di Aspose.Words che stai usando supporti i controlli OLE e controlla che le impostazioni di sicurezza di Word consentano l'esecuzione di ActiveX. Buona programmazione!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo passo per aiutarti a padroneggiare funzionalità aggiuntive dell'API ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Incorporare oggetti OLE e controlli ActiveX nei documenti Word](/words/english/python-net/document-structure-and-content-manipulation/document-ole-objects-active-x/)
- [Come creare campi modulo e aggiungere contenuto usando DocumentBuilder in Aspose.Words per Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Creare forma rettangolare in Word con Java – Guida completa](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}