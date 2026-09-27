---
category: general
date: 2026-09-27
description: Crea un file docx contenente ActiveX in Java usando Aspose.Words. Impara
  a inserire un pulsante di comando ActiveX passo dopo passo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create docx containing activex
- insert activex command button
- Aspose.Words Java
- ActiveX control in Word
- generate Word document programmatically
language: it
lastmod: 2026-09-27
og_description: Crea un file docx contenente ActiveX in Java con Aspose.Words. Segui
  questa guida per inserire un pulsante di comando ActiveX e salvare il documento.
og_image_alt: Screenshot of a Word document that contains an ActiveX command button
og_title: Crea un docx contenente ActiveX in Java – guida completa
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create docx containing ActiveX in Java using Aspose.Words. Learn to
    insert an ActiveX command button step‑by‑step.
  headline: How to create docx containing ActiveX with Java and Aspose.Words
  type: TechArticle
- description: Create docx containing ActiveX in Java using Aspose.Words. Learn to
    insert an ActiveX command button step‑by‑step.
  name: How to create docx containing ActiveX with Java and Aspose.Words
  steps:
  - name: The document should show a single page with a button labeled **Click Me**
      positioned near the top‑left corner.
    text: The document should show a single page with a button labeled **Click Me**
      positioned near the top‑left corner.
  - name: If the button does not appear, check that **ActiveX controls are enabled**
      in Word’s Trust Center (File → Options → Trust Center → Trust Center Settings
      → ActiveX Settings).
    text: If the button does not appear, check that **ActiveX controls are enabled**
      in Word’s Trust Center (File → Options → Trust Center → Trust Center Settings
      → ActiveX Settings).
  - name: The button is functional only on Windows versions of Word that support ActiveX.
      On macOS or web‑based Word, the control will be displayed as a static image.
    text: The button is functional only on Windows versions of Word that support ActiveX.
      On macOS or web‑based Word, the control will be displayed as a static image.
  type: HowTo
tags:
- docx
- activex
- java
- aspose-words
title: Come creare un docx contenente ActiveX con Java e Aspose.Words
url: /it/java/using-document-elements/how-to-create-docx-containing-activex-with-java-and-aspose-w/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come creare docx contenente ActiveX con Java e Aspose.Words

Se hai bisogno di **creare docx contenente ActiveX**, questa guida ti mostra una soluzione completa. Imparerai come **inserire un pulsante di comando ActiveX** in un file Word usando Aspose.Words per Java, quindi salvare il risultato come .docx che può essere aperto in Microsoft Word.

Generare un documento Word programmaticamente ti libera dalla modifica manuale e garantisce coerenza tra report, contratti o modelli di modulo. I passaggi seguenti coprono tutto, dalla configurazione del progetto alla gestione dei problemi comuni, così potrai integrare la tecnica in qualsiasi applicazione Java.

## Prerequisiti

* Java Development Kit (JDK) 8 o versioni successive installato.
* Maven 3.6+ (o un altro strumento di build che preferisci).
* Un file di licenza Aspose.Words per Java (la valutazione gratuita funziona per i test).
* Microsoft Word installato sulla macchina di destinazione se vuoi verificare visivamente il controllo ActiveX.

Questi elementi sono necessari perché Aspose.Words fornisce l'API che crea il documento, mentre Word è necessario per renderizzare il controllo ActiveX.

## Passo 1: Configurare il progetto Maven

Crea un nuovo progetto Maven o aggiungi la dipendenza Aspose.Words a un `pom.xml` esistente:

```xml
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>activex-docx-demo</artifactId>
    <version>1.0.0</version>
    <properties>
        <maven.compiler.source>1.8</maven.compiler.source>
        <maven.compiler.target>1.8</maven.compiler.target>
    </properties>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.10</version> <!-- use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

> **Suggerimento:** Mantieni la versione di Aspose.Words sincronizzata con le note di rilascio ufficiali per beneficiare delle correzioni di bug e delle nuove funzionalità ActiveX.

## Passo 2: Scrivere il codice Java che crea il documento

Crea una classe chiamata `ActiveXDocxCreator`. Il codice qui sotto include tutti gli import necessari, un metodo `main` e commenti dettagliati che spiegano ogni operazione.

```java
package com.example.activex;

import com.aspose.words.*;
import java.io.File;

/**
 * Demonstrates how to create a DOCX file that contains an ActiveX command button.
 * The resulting file can be opened in Microsoft Word where the button appears
 * on the first page.
 */
public class ActiveXDocxCreator {

    public static void main(String[] args) {
        // 1. Initialize a new empty document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert an ActiveX Forms2OleControl at the current cursor position.
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // 3. Configure the control to be a CommandButton and set its caption.
        commandButton.setControlType(Forms2OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");

        // 4. Position the button on the page.
        //    The coordinates are measured in points (1 point = 1/72 inch).
        commandButton.setLeft(100); // 100 points from the left margin
        commandButton.setTop(150);  // 150 points from the top margin

        // 5. (Optional) Set the size of the button for better visibility.
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        // 6. Save the document to the desired location.
        String outputPath = "output/ActiveXCommandButton.docx";
        try {
            // Ensure the output directory exists.
            new File("output").mkdirs();
            doc.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error while saving the document: " + e.getMessage());
        }
    }
}
```

### Perché ogni riga è importante

* `Document` è il contenitore di tutto il contenuto Word. Creare una nuova istanza ti fornisce una tela pulita.
* `DocumentBuilder` fornisce un'API fluida per inserire elementi; traccia automaticamente il punto di inserimento.
* `insertForms2OleControl()` crea un segnaposto generico per un controllo OLE. Aspose.Words lo tratta come un contenitore ActiveX.
* `setControlType(Forms2OleControlType.COMMANDBUTTON)` indica a Word che il segnaposto deve essere visualizzato come un CommandButton.
* `setCaption("Click Me")` definisce il testo visualizzato sul pulsante.
* `setLeft` e `setTop` posizionano il pulsante rispetto ai margini della pagina. Regola questi valori per adattarli al tuo layout.
* `setWidth` e `setHeight` sono opzionali ma migliorano l'aspetto del pulsante, soprattutto quando la dimensione predefinita è troppo piccola.
* `doc.save` scrive la struttura in‑memoria in un file .docx fisico che Word può aprire.

## Passo 3: Verificare il documento generato

Apri `output/ActiveXCommandButton.docx` in Microsoft Word:

1. Il documento dovrebbe mostrare una singola pagina con un pulsante etichettato **Click Me** posizionato vicino all'angolo in alto a sinistra.
2. Se il pulsante non appare, verifica che **i controlli ActiveX siano abilitati** nel Trust Center di Word (File → Opzioni → Trust Center → Impostazioni Trust Center → Impostazioni ActiveX).
3. Il pulsante è funzionale solo nelle versioni Windows di Word che supportano ActiveX. Su macOS o Word basato sul web, il controllo verrà visualizzato come un'immagine statica.

## Passo 4: Gestire i casi limite comuni

| Situazione | Motivo | Azione consigliata |
|-----------|--------|--------------------|
| Il pulsante manca dopo aver aperto il file | Le impostazioni di sicurezza di Word bloccano ActiveX | Abilita “Esegui tutti i controlli senza restrizioni” per le posizioni attendibili. |
| Il .docx generato non può essere aperto | Versione di Aspose.Words incompatibile | Aggiorna all'ultima versione di Aspose.Words; le versioni più vecchie potrebbero non incorporare correttamente le parti OLE richieste. |
| Hai bisogno che il pulsante esegua una macro | ActiveX da solo non contiene codice macro | Combina il controllo ActiveX con una macro VBA che gestisce l'evento `Click`. Usa il metodo `DocumentBuilder.insertOleObject` per incorporare un modello abilitato alle macro. |
| Il layout è errato su diverse dimensioni di pagina | Le coordinate sono punti assoluti | Usa `builder.getPageSetup().setPageWidth` e `setPageHeight` per standardizzare la dimensione della pagina prima di posizionare il controllo. |

## Passo 5: Estendere la soluzione

Puoi inserire altri controlli ActiveX modificando l'enumerazione `ControlType`:

```java
commandButton.setControlType(Forms2OleControlType.CHECKBOX); // inserts a checkbox
```

Aspose.Words supporta anche l'inserimento di **caselle di testo ActiveX**, **list box** e **combo box**. Si applicano gli stessi metodi di posizionamento (`setLeft`, `setTop`, `setWidth`, `setHeight`).

Se devi posizionare più controlli, chiama `builder.insertForms2OleControl()` più volte e regola le coordinate di ciascun controllo di conseguenza.

## File sorgente completo

Di seguito trovi l'intero file `ActiveXDocxCreator.java` pronto per copia‑incolla:

```java
package com.example.activex;

import com.aspose.words.*;
import java.io.File;

public class ActiveXDocxCreator {
    public static void main(String[] args) {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        Forms2OleControl commandButton = builder.insertForms2OleControl();
        commandButton.setControlType(Forms2OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        String outputPath = "output/ActiveXCommandButton.docx";
        try {
            new File("output").mkdirs();
            doc.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error while saving the document: " + e.getMessage());
        }
    }
}
```

Eseguendo questo programma si ottiene un **docx contenente ActiveX** che puoi distribuire agli utenti finali che necessitano di moduli interattivi.

## Conclusione

Ora sai come **creare docx contenente ActiveX** usando Java e Aspose.Words, e come **inserire un pulsante di comando ActiveX** programmaticamente. Il tutorial ha coperto la configurazione del progetto, il codice sorgente completo, i passaggi di verifica e le strategie per affrontare problemi tipici.

Da qui potresti esplorare:

* Aggiungere macro VBA per rispondere al clic del pulsante.
* Incorporare altri controlli ActiveX come caselle di controllo o combo box.
* Automatizzare la generazione di moduli multi‑pagina con dati dinamici.

Sperimenta con coordinate, dimensioni e tipi di controllo diversi per adattarli al layout specifico del tuo documento. Buon coding!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Utilizzare oggetti OLE e controlli ActiveX in Aspose.Words per Java](/words/english/java/using-document-elements/using-ole-objects-and-activex/)
- [Come creare campi modulo e aggiungere contenuto usando DocumentBuilder in Aspose.Words per Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Creare forma rettangolare in Word con Aspose.Words – Guida passo‑passo](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}