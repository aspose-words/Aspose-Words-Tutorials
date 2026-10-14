---
category: general
date: 2026-10-13
description: Crea un pulsante di campo modulo in Word usando Aspose.Words per Java.
  Scopri come inserire campi modulo di Word con pulsante di comando e impostare la
  didascalia del pulsante di comando in pochi semplici passaggi.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create form field button
- insert command button word
- set command button caption
language: it
lastmod: 2026-10-13
og_description: Crea un pulsante di campo modulo in Word con Aspose.Words per Java.
  Questo tutorial mostra come inserire campi pulsante di comando in Word e impostare
  rapidamente la didascalia del pulsante di comando.
og_image_alt: Screenshot of a Word document containing an inserted command button
  form field created with Aspose.Words Java
og_title: Crea pulsante di campo modulo in Word – Guida Aspose.Words per Java
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Create form field button in Word using Aspose.Words for Java. Learn
    how to insert command button word form fields and set command button caption in
    a few easy steps.
  headline: Create form field button in Word with Aspose.Words Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Crea pulsante di campo modulo in Word con Aspose.Words Java
url: /it/java/using-document-elements/create-form-field-button-in-word-with-aspose-words-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea un pulsante di campo modulo in Word con Aspose.Words per Java

Se hai bisogno di **create form field button** in un documento Word, questa guida ti accompagna passo passo attraverso l'intero processo usando Aspose.Words per Java. Che tu stia creando un modello di modulo compilabile o aggiungendo controlli interattivi a un report, imparerai come **insert command button word** form fields e **set command button caption** con un codice minimo.

Il tutorial copre tutto, dalla configurazione di Maven a un esempio completamente eseguibile, così potrai copiare‑incollare il codice, eseguirlo e vedere un file `.docx` che contiene un pulsante cliccabile pronto per ulteriori personalizzazioni.

## Prerequisiti

- Java 17 (o versioni successive) installato e configurato sulla tua macchina.
- Maven 3.6+ per la gestione delle dipendenze.
- Un IDE o un editor di testo a tua scelta (ad es., IntelliJ IDEA, VS Code).
- Una licenza valida di Aspose.Words per Java (la versione di prova gratuita è valida per la valutazione).

## Passo 1: Aggiungi Aspose.Words al tuo progetto Maven

Creare un `pom.xml` (o modificare quello esistente) e includere la dipendenza Aspose.Words:

```xml
<dependencies>
    <dependency>
        <groupId>com.aspose</groupId>
        <artifactId>aspose-words</artifactId>
        <version>24.9</version> <!-- Use the latest version available -->
    </dependency>
</dependencies>
```

> **Suggerimento:** Mantieni il numero di versione aggiornato. Le nuove release aggiungono il supporto alle ultime funzionalità di Word e migliorano le prestazioni.

## Passo 2: Inizializza un documento vuoto e un `DocumentBuilder`

La classe `DocumentBuilder` fornisce un'API fluida per modificare un documento Word. In questo passo creiamo un `Document` vuoto e vi associamo un builder.

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // DocumentBuilder lets us add content programmatically
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Creare il documento è la base per gli oggetti **create form field button** che verranno creati più avanti nel tutorial.

## Passo 3: Inserisci un campo modulo command button

Aspose.Words espone la classe `Forms2OleControl` per i controlli OLE dei moduli. Per **insert command button word** form fields, chiama `insertForms2OleControl` con il valore enum `COMMANDBUTTON`.

```java
        // Insert a Command Button form field at the current cursor position
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);
```

Il metodo restituisce un'istanza di `Forms2OleControl` che possiamo configurare prima di salvare.

## Passo 4: Definisci dimensione e posizione del pulsante

Un command button richiede dimensioni e posizionamento espliciti nella pagina. Regola larghezza, altezza e coordinate per adattarle al tuo layout.

```java
        // Set the button's visual size (in points)
        commandButton.setWidth(120);   // 120 points ≈ 1.67 inches
        commandButton.setHeight(30);   // 30 points ≈ 0.42 inches

        // Position the button relative to the page margins
        commandButton.setLeft(50);   // 50 points from the left margin
        commandButton.setTop(100);   // 100 points from the top margin
```

Regolare finemente questi valori garantisce che il pulsante appaia esattamente dove desideri nel documento finale.

## Passo 5: **Set command button caption**

Il testo visibile sul pulsante è controllato dal metodo `setCaption`. Qui è dove **set command button caption** per guidare l'utente.

```java
        // Define the text that appears on the button
        commandButton.setCaption("Click Me");
```

Puoi sostituire `"Click Me"` con qualsiasi etichetta che corrisponda all'intento del tuo modulo, come `"Submit"` o `"Approve"`.

## Passo 6: Salva il documento

Infine, scrivi il documento su disco. Il file risultante contiene il pulsante interattivo e può essere aperto in Microsoft Word o LibreOffice.

```java
        // Save the document with the embedded command button
        doc.save("CommandButtonDemo.docx");
    }
}
```

Eseguendo il programma si genera `CommandButtonDemo.docx`. Aprendolo in Word si visualizza un pulsante etichettato **Click Me** posizionato a 50 pt dalla sinistra e 100 pt dall'alto della pagina.

### Output previsto

- Un file `.docx` chiamato `CommandButtonDemo.docx`.
- Il documento contiene una singola pagina con un campo modulo command button.
- Il pulsante mostra la didascalia impostata (ad es., **Click Me**).

## Varianti comuni e casi particolari

| Situazione | Come adattare |
|-----------|--------------|
| **Multiple buttons** | Chiama `insertForms2OleControl` più volte, regolando `setLeft`/`setTop` per ogni nuovo pulsante. |
| **Different caption per button** | Usa `setCaption` con una stringa unica dopo ogni inserimento. |
| **Button inside a table cell** | Sposta il cursore nella cella desiderata con `builder.moveTo(cell.getFirstParagraph())` prima di inserire il controllo. |
| **Legacy Word formats (.doc)** | Salva usando `doc.save("Demo.doc", SaveFormat.DOC);` – il command button viene preservato. |
| **Read‑only forms** | Dopo l'inserimento, imposta `commandButton.setEnabled(false);` per impedire l'interazione dell'utente. |

## Suggerimenti per un'implementazione robusta

- **Convalida le dimensioni**: Larghezze estremamente grandi possono far traboccare il pulsante oltre il margine della pagina.
- **Applicazione della licenza**: Senza una licenza valida, Aspose.Words aggiunge una filigrana al documento generato. Applica la tua licenza subito con `License license = new License(); license.setLicense("Aspose.Words.lic");`.
- **Test**: Apri il file generato in Word e attiva **Design Mode** (Sviluppatore → Design Mode) per visualizzare le proprietà del pulsante.

## Riepilogo del codice sorgente completo

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a Command Button form field
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 3: Define the button's size and position on the page
        commandButton.setWidth(120);
        commandButton.setHeight(30);
        commandButton.setLeft(50);
        commandButton.setTop(100);

        // Step 4: Set the text that appears on the button
        commandButton.setCaption("Click Me");

        // Step 5: Save the document with the embedded command button
        doc.save("CommandButtonDemo.docx");
    }
}
```

Copia il codice in un file chiamato `InsertCommandButtonDemo.java`, compila con Maven (`mvn compile`) ed esegui (`mvn exec:java -Dexec.mainClass=InsertCommandButtonDemo`). Il documento generato apparirà nella cartella radice del tuo progetto.

## Conclusione

Ora sai come **create form field button** in Word usando Aspose.Words per Java, come **insert command button word** form fields e come **set command button caption** programmaticamente. Questo esempio completo ti fornisce una solida base per creare documenti Word più ricchi e interattivi—che tu abbia bisogno di un singolo pulsante di invio o di un'intera suite di controlli modulo.

### Qual è il prossimo passo?

- Esplora altri controlli modulo come le caselle di controllo (`Forms2OleControlType.CHECKBOX`) e le caselle di testo (`Forms2OleControlType.TEXTBOX`).
- Combina i campi modulo con la stampa unione per generare questionari personalizzati.
- Usa l'API `FormField` di Aspose.Words per leggere i dati inseriti dall'utente dopo che il documento è stato compilato.

Sentiti libero di sperimentare con diverse dimensioni, didascalie e posizioni. Una volta padroneggiati i command button, aggiungere moduli completi al tuo flusso di automazione Word diventa un compito semplice. Buon coding!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo passo per aiutarti a padroneggiare funzionalità aggiuntive dell'API e a esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Come creare campi modulo e aggiungere contenuti usando DocumentBuilder in Aspose.Words per Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Aggiungi un campo modulo Combo Box a un documento Word con Aspose.Words per .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Aggiungi un campo modulo Check Box a un documento Word con Aspose.Words per .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}