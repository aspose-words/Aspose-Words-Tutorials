---
category: general
date: 2026-07-26
description: Come inserire un pulsante ActiveX in un documento Word usando Aspose.Words
  – impara a impostare la didascalia, la posizione e le dimensioni del pulsante in
  poche righe.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert activex
- set button caption
language: it
lastmod: 2026-07-26
og_description: Come inserire un pulsante ActiveX in un documento Word con Aspose.Words.
  Segui questo tutorial passo‑passo per impostare la didascalia, la posizione e le
  dimensioni del pulsante.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX CommandButton
  with a custom caption
og_title: Come inserire un pulsante ActiveX in Word – Guida rapida
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: How to insert ActiveX button in a Word document using Aspose.Words
    – learn to set button caption, position, and size in just a few lines.
  headline: How to Insert ActiveX Button in Word – Set Button Caption
  type: TechArticle
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
- Document generation
title: Come inserire un pulsante ActiveX in Word – Impostare la didascalia del pulsante
url: /it/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come inserire un pulsante ActiveX in Word – Impostare la didascalia del pulsante

Ti sei mai chiesto **come inserire ActiveX** controlli in un file Word senza aprire l'interfaccia utente? Non sei l'unico. In molte applicazioni aziendali è necessario un pulsante cliccabile che esegue una macro, e farlo programmaticamente fa risparmiare ore. Questa guida ti mostra esattamente **come inserire ActiveX** CommandButton usando Aspose.Words per Java, e—sì—come **impostare la didascalia del pulsante** così l'utente sa cosa cliccare.

Ti guideremo attraverso l'intero processo: dalla configurazione della libreria, alla creazione di un nuovo documento, all'inserimento del pulsante, alla regolazione di dimensioni e posizione, all'assegnazione di una didascalia amichevole e, infine, al salvataggio del file. Alla fine avrai un `.docx` eseguibile che si apre in Word con un pulsante ActiveX completamente funzionante pronto a lanciare la tua macro.

---

## Cosa imparerai

- Installare e fare riferimento ad Aspose.Words in un progetto Java.  
- Creare un nuovo `Document` e `DocumentBuilder`.  
- **Insert ActiveX** CommandButton control con una singola riga di codice.  
- **Set button caption**, regolare la sua posizione e definire le sue dimensioni.  
- Salvare il documento e aprirlo in Word per vedere il risultato.

Non è necessaria alcuna esperienza pregressa con ActiveX; basta una conoscenza di base di Java e una copia di Aspose.Words.

## Prerequisiti

- Java 8 o versione più recente installata sulla tua macchina.  
- Maven o Gradle per la gestione delle dipendenze (mostreremo lo snippet Maven).  
- Una copia con licenza o di valutazione di **Aspose.Words for Java** (la versione di prova gratuita funziona bene per questa demo).  
- Microsoft Word (qualsiasi versione recente) per testare il file generato.

## Passo 1: Configura Aspose.Words nel tuo progetto

Prima di tutto—aggiungi la dipendenza Aspose.Words. Se usi Maven, inserisci questo nel tuo `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- check for the latest version -->
</dependency>
```

Gli utenti Gradle possono aggiungere:

```gradle
implementation 'com.aspose:aspose-words:24.10'
```

Dopo un rapido `mvn clean install` (o `gradle build`) la libreria sarà nel tuo classpath e sarai pronto a codificare.

## Passo 2: Crea un nuovo documento e builder

Un `Document` rappresenta l'intero file Word, mentre `DocumentBuilder` ti permette di modificarlo. Pensa al builder come a una penna che disegna su una tela fresca.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank document and a builder
        Document doc = new Document();                 // creates an empty .docx
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Perché partire da un documento vuoto? Garantisce il pieno controllo su ogni elemento che aggiungi, e non ci sono formattazioni nascoste che ti sorprendono più tardi.

## Passo 3: Inserisci il controllo ActiveX CommandButton

Ora arriva la star dello spettacolo. Aspose.Words espone `insertForms2OleControl` che può posizionare qualsiasi controllo ActiveX tu specifichi. Qui chiediamo un **CommandButton**.

```java
        // Step 3: Insert a CommandButton ActiveX control
        Forms2OleControl commandBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);
```

Il metodo restituisce un oggetto `Forms2OleControl`, fornendoti l'accesso programmatico alle proprietà del pulsante. È qui che **how to insert activex** diventa una singola riga—senza dover armeggiare con le API COM a basso livello.

## Passo 4: Posizione, dimensione e impostazione della didascalia del pulsante

Un pulsante che fluttua al centro della pagina non è molto utile. Vuoi posizionarlo dove gli utenti se lo aspettano, dargli una dimensione sensata e—soprattutto—**set button caption** così sanno cosa succederà al click.

```java
        // Step 4a: Position the button (coordinates are in points)
        commandBtn.setLeft(100);   // distance from the left margin
        commandBtn.setTop(150);    // distance from the top margin

        // Step 4b: Define width and height
        commandBtn.setWidth(120);
        commandBtn.setHeight(30);

        // Step 4c: Set the button caption (the text that appears on the button)
        commandBtn.setCaption("Click Me");
```

**Perché questi numeri?** Word usa i punti (1 pt ≈ 1/72 pollice). `100 pt` ≈ 1,4 pollici da sinistra, `150 pt` ≈ 2,1 pollici dall'alto—circa il centro di una pagina A4 standard. Regola i valori in base al tuo layout.

Impostare la didascalia è fondamentale; senza di essa il pulsante appare come un rettangolo vuoto. Il metodo `setCaption` accetta qualsiasi stringa, così potrai localizzarla in seguito se necessario.

## Passo 5: Salva il documento

Infine, scrivi il documento su disco. Puoi scegliere qualsiasi cartella ti piaccia; assicurati solo che il percorso esista.

```java
        // Step 5: Save the document to a .docx file
        String outputPath = "C:/Temp/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Quando apri `ActiveXButton.docx` in Word, vedrai un pulsante ben posizionato etichettato **“Click Me.”** Se lo fai doppio‑click, Word ti chiederà di abilitare le macro (poiché i controlli ActiveX sono considerati macro‑enabled). Da lì potrai collegare una routine VBA all'evento `Click` del pulsante.

## Casi particolari e consigli che potresti dimenticare

- **Macro‑Enabled Format**: Word disabilita i controlli ActiveX nei file `.docx` standard a meno che l'utente non abiliti le macro. Se vuoi che il pulsante funzioni subito, considera di salvare come `.docm` (macro‑enabled) usando `doc.save(outputPath, SaveFormat.DOCM);`.
- **Compatibility**: Le versioni più vecchie di Word (pre‑2007) usano il formato binario `.doc`. Aspose.Words può salvare in quel formato, ma le proprietà del controllo potrebbero apparire leggermente diverse.
- **Security Settings**: Alcuni ambienti aziendali bloccano ActiveX. Se il tuo pulsante non appare, controlla Word → Centro protezione → Impostazioni ActiveX.
- **Multiple Buttons**: Vuoi più di uno? Basta ripetere la chiamata `insertForms2OleControl` e regolare i valori `Left`/`Top` di ciascun pulsante. Tieni traccia degli oggetti restituiti per impostare didascalie individuali.
- **Styling the Caption**: La didascalia eredita il font predefinito. Per cambiarlo, dovresti modificare l'XML sottostante o applicare uno stile Word dopo l'inserimento—oltre lo scopo di questa breve guida, ma fattibile con l'API `ParagraphFormat` di Aspose.Words.

## Esempio completo funzionante

Di seguito trovi la classe Java completa, pronta per l'esecuzione. Copiala nel tuo IDE, modifica il percorso di output e premi **Run**.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control
        Forms2OleControl commandBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Position the button (points from the left/top margins)
        commandBtn.setLeft(100);
        commandBtn.setTop(150);

        // Set size (width × height in points)
        commandBtn.setWidth(120);
        commandBtn.setHeight(30);

        // Set the button caption – this is the visible text
        commandBtn.setCaption("Click Me");

        // Save the document; you may also use SaveFormat.DOCM for macro‑enabled files
        String outputPath = "C:/Temp/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

**Output previsto**: Dopo l'esecuzione, la console stampa il percorso di salvataggio. Aprendo il file generato in Word vedrai un pulsante posizionato più o meno al centro della pagina, etichettato “Click Me”. Cliccandolo verrà attivato l'evento standard di click ActiveX (dovrai collegare una macro VBA per rispondere).

## Conclusione

Ora sai **how to insert ActiveX** CommandButton controls in un documento Word programmaticamente con Aspose.Words, e hai visto esattamente come **set button caption**, posizionare e dimensionare il controllo. Questo approccio elimina il lavoro manuale sull'interfaccia, si integra perfettamente nei generatori di report automatizzati, e ti dà il pieno controllo su

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell'API ed esplorare approcci alternativi nei tuoi progetti.

- [Inserire forme nei documenti Word usando Aspose.Words per .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Inserire immagine in linea in un documento Word usando Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Inserire un'immagine nell'intestazione del documento Word | Aspose.Words per .NET](/words/english/net/header-footer-formatting/insert-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}