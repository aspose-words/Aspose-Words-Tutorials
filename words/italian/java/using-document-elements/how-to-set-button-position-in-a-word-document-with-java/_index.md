---
category: general
date: 2026-09-24
description: Imposta la posizione del pulsante in un documento Word usando Java e
  Aspose.Words. Scopri come inserire un pulsante, aggiungere un controllo ActiveX
  e creare un documento Word in stile Java.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button position
- how to insert button
- add activex control
- add button to word
- create word document java
language: it
lastmod: 2026-09-24
og_description: Imposta la posizione del pulsante in un documento Word usando Java.
  Questa guida mostra come inserire un pulsante, aggiungere un controllo ActiveX e
  creare un documento Word in Java con Aspose.Words.
og_image_alt: Screenshot of a Word document showing a CommandButton positioned at
  100 px left and 150 px top
og_title: Imposta la posizione del pulsante in un documento Word con Java – guida
  completa
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Set button position in a Word document using Java and Aspose.Words.
    Learn how to insert button, add ActiveX control, and create Word document Java
    style.
  headline: How to set button position in a Word document with Java
  type: TechArticle
- description: Set button position in a Word document using Java and Aspose.Words.
    Learn how to insert button, add ActiveX control, and create Word document Java
    style.
  name: How to set button position in a Word document with Java
  steps:
  - name: Expected output
    text: '* A `.docx` file named **CommandButtonDemo.docx**. * Inside the document,
      a **CommandButton** labeled “Click Me” appears 100 px from the left margin and
      150 px from the top margin. * The button responds to clicks when the document
      is opened in Word (it will display a default ActiveX message unless y'
  - name: Adding multiple buttons
    text: If you need to **add button to Word** more than once, repeat steps 3‑5 with
      a new `Forms2OleControl` instance each time. Remember to adjust the `setTop`
      value so buttons don’t overlap.
  - name: Working without a license
    text: 'Aspose.Words adds a watermark when used without a license. For production
      code, purchase a license and apply it at the start of `main`:'
  - name: Compatibility with older Office versions
    text: 'ActiveX controls are supported in the `.doc` (Word 97‑2003) format. To
      create a legacy file, change the save format:'
  - name: Next steps
    text: '* Explore other `Forms2OleControl.ControlType` values (e.g., `CHECKBOX`,
      `TEXTBOX`) to build richer forms. * Combine the button with VBA macros for custom
      click handling. * Use Aspose.Words’ mail‑merge feature to generate personalized
      documents that already contain interactive controls.'
  type: HowTo
- questions:
  - answer: Yes. Aspose.Words is pure Java and runs on any JDK 8+ implementation,
      including OpenJDK.
    question: Does this work with OpenJDK?
  - answer: ActiveX button appearance is controlled by the host application (Word).
      You can attach VBA code to modify properties at runtime, but the static appearance
      is limited to the default style.
    question: Can I change the button’s font or color?
  - answer: 'Move the `DocumentBuilder` cursor into the cell before calling `insertForms2OleControl`.
      The control will inherit the cell’s layout, and you can still use `setLeft`/`setTop`
      for fine‑tuning. ## Conclusion You now know how to **set button position** in
      a Word document using Java, how to **how to inse'
    question: What if I need to place the button inside a table cell?
  type: FAQPage
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
- CommandButton
title: Come impostare la posizione del pulsante in un documento Word con Java
url: /it/java/using-document-elements/how-to-set-button-position-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come impostare la posizione del pulsante in un documento Word con Java

Se hai bisogno di **impostare la posizione del pulsante** all'interno di un file Word, questa guida ti mostra una soluzione completa e eseguibile. Che tu stia creando un modello che richiede l'interazione dell'utente o automatizzando un modulo, imparerai esattamente **come inserire un pulsante** usando Aspose.Words per Java e controllarne il posizionamento.

Il tutorial copre tutto ciò di cui hai bisogno per **aggiungere un controllo ActiveX** a un documento Word, spiega come **aggiungere un pulsante a Word**, e dimostra l'intero processo per **creare un documento Word Java**. Non sono necessari riferimenti esterni—basta copiare, eseguire e verificare il risultato.

## Prerequisiti

* Java 17 (o qualsiasi runtime Java 8+) installato.
* Maven o Gradle per gestire le dipendenze.
* Una licenza Aspose.Words per Java (la versione di prova gratuita funziona per la valutazione).
* Una conoscenza di base della sintassi Java.

> **Consiglio professionale:** Conserva i JAR di Aspose.Words in una cartella `libs/` e aggiungili al classpath del tuo progetto per evitare conflitti di versione.

## Passo 1: Configurare il progetto Maven

Crea un semplice progetto Maven (o usa Gradle) e aggiungi la dipendenza Aspose.Words:

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word-button-demo</artifactId>
    <version>1.0.0</version>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- latest at time of writing -->
        </dependency>
    </dependencies>
</project>
```

Eseguendo `mvn clean compile` si scarica la libreria e si prepara il percorso di compilazione.

## Passo 2: Creare un nuovo documento Word

La prima operazione è **creare un documento Word java**. Instanzi un oggetto `Document` e un `DocumentBuilder` che ti permette di modificare il file.

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

La classe `Document` rappresenta l'intero file .docx, mentre `DocumentBuilder` fornisce un'API fluida per inserire contenuti.

## Passo 3: Come inserire un pulsante – aggiungere un controllo ActiveX

Aspose.Words espone la classe `Forms2OleControl` per inserire controlli ActiveX legacy come un CommandButton. Questo passo mostra il modo esatto per **come inserire un pulsante** nel documento.

```java
        // Insert a CommandButton ActiveX control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);
```

Il metodo `insertForms2OleControl` restituisce un'istanza `Forms2OleControl` che puoi configurare. Questo è il nucleo del processo di **aggiunta di un controllo ActiveX**.

## Passo 4: Impostare la posizione del pulsante

Ora impostiamo effettivamente **la posizione del pulsante**. I metodi `setLeft` e `setTop` del controllo accettano valori in punti (1 pt = 1/72 in). Per allineare il pulsante con le coordinate tipiche dello schermo, puoi convertire i pixel in punti (1 px ≈ 0.75 pt). Nell'esempio posizioniamo il pulsante a 100 px dal bordo sinistro e a 150 px dal bordo superiore.

```java
        // Position the button on the page
        commandButton.setLeft(100 * 0.75);   // 75 pt ≈ 100 px
        commandButton.setTop(150 * 0.75);    // 112.5 pt ≈ 150 px
```

Poiché la logica di **impostare la posizione del pulsante** è incapsulata qui, puoi riutilizzare queste righe ogni volta che devi spostare un controllo. Regola i numeri per adattarli ai requisiti del tuo layout.

## Passo 5: Definire dimensione e didascalia

Un pulsante senza etichetta è confuso. Usa `setWidth`, `setHeight` e `setCaption` per dargli un aspetto visibile.

```java
        // Define size and caption
        commandButton.setWidth(120 * 0.75);   // 90 pt width
        commandButton.setHeight(30 * 0.75);   // 22.5 pt height
        commandButton.setCaption("Click Me");
```

La dimensione è espressa anch'essa in punti, quindi convertiamo dai pixel per coerenza.

## Passo 6: Salvare il documento – completare il flusso **create Word document java**

Infine, salva il file su disco. Il percorso può essere assoluto o relativo alla radice del progetto.

```java
        // Save the document containing the CommandButton
        doc.save("output/CommandButtonDemo.docx");
    }
}
```

Eseguendo il programma si genera `CommandButtonDemo.docx` nella cartella `output`. Aprendo il file in Microsoft Word appare un pulsante cliccabile posizionato esattamente dove lo hai impostato.

### Output previsto

* Un file `.docx` chiamato **CommandButtonDemo.docx**.
* All'interno del documento, appare un **CommandButton** con l'etichetta “Click Me” a 100 px dal margine sinistro e 150 px dal margine superiore.
* Il pulsante risponde ai click quando il documento è aperto in Word (mostrerà un messaggio ActiveX predefinito a meno che non venga allegato del codice VBA personalizzato).

## Passo 7: Varianti comuni e casi limite

### Aggiungere più pulsanti

Se devi **add button to Word** più di una volta, ripeti i passi 3‑5 con una nuova istanza `Forms2OleControl` ogni volta. Ricorda di regolare il valore `setTop` affinché i pulsanti non si sovrappongano.

```java
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);
        secondButton.setLeft(200 * 0.75);
        secondButton.setTop(250 * 0.75);
        secondButton.setWidth(120 * 0.75);
        secondButton.setHeight(30 * 0.75);
        secondButton.setCaption("Second");
```

### Lavorare senza licenza

Aspose.Words aggiunge una filigrana quando viene usato senza licenza. Per il codice di produzione, acquista una licenza e applicala all'inizio di `main`:

```java
        License license = new License();
        license.setLicense("Aspose.Words.lic");
```

### Compatibilità con versioni Office più vecchie

I controlli ActiveX sono supportati nel formato `.doc` (Word 97‑2003). Per creare un file legacy, cambia il formato di salvataggio:

```java
        doc.save("CommandButtonDemo.doc", SaveFormat.DOC);
```

## Codice sorgente completo (eseguibile)

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Optional: apply a license if you have one
        // License license = new License();
        // license.setLicense("Aspose.Words.lic");

        // Step 1: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a CommandButton ActiveX control (how to insert button)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControl.ControlType.COMMANDBUTTON);

        // Step 3: Position the button on the page (set button position)
        commandButton.setLeft(100 * 0.75);   // distance from the left edge (points)
        commandButton.setTop(150 * 0.75);    // distance from the top edge (points)

        // Step 4: Define the button's size and caption
        commandButton.setWidth(120 * 0.75);   // width in points
        commandButton.setHeight(30 * 0.75);   // height in points
        commandButton.setCaption("Click Me");

        // Step 5: Save the document containing the CommandButton (create word document java)
        doc.save("output/CommandButtonDemo.docx");
    }
}
```

Salva il file come `src/main/java/CommandButtonDemo.java`, esegui `mvn exec:java -Dexec.mainClass=CommandButtonDemo` e apri il documento generato per vedere il risultato.

## Domande frequenti

**Q: Funziona con OpenJDK?**  
A: Sì. Aspose.Words è puro Java e gira su qualsiasi implementazione JDK 8+, incluso OpenJDK.

**Q: Posso cambiare il font o il colore del pulsante?**  
A: L'aspetto del pulsante ActiveX è controllato dall'applicazione host (Word). Puoi allegare codice VBA per modificare le proprietà a runtime, ma l'aspetto statico è limitato allo stile predefinito.

**Q: E se devo posizionare il pulsante all'interno di una cella di tabella?**  
A: Sposta il cursore `DocumentBuilder` nella cella prima di chiamare `insertForms2OleControl`. Il controllo erediterà il layout della cella e potrai comunque usare `setLeft`/`setTop` per una regolazione fine.

## Conclusione

Ora sai come **impostare la posizione del pulsante** in un documento Word usando Java, come **come inserire un pulsante**, come **aggiungere un controllo ActiveX**, e come **add button to Word** seguendo le migliori pratiche per i progetti **create Word document java**. L'esempio completo dimostra l'intero flusso di lavoro—dalla configurazione del progetto a un file `.docx` salvato contenente un CommandButton funzionante.

### Prossimi passi

* Esplora altri valori `Forms2OleControl.ControlType` (ad esempio `CHECKBOX`, `TEXTBOX`) per creare moduli più ricchi.
* Combina il pulsante con macro VBA per gestire click personalizzati.
* Usa la funzionalità di mail‑merge di Aspose.Words per generare documenti personalizzati che contengono già controlli interattivi.

Buon coding e divertiti ad automatizzare i documenti Word con Java!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo passo per aiutarti a padroneggiare ulteriori funzionalità dell'API ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Come creare campi modulo e aggiungere contenuti usando DocumentBuilder in Aspose.Words per Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Aggiungere un campo modulo Combo Box a un documento Word con Aspose.Words per .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Come caricare documenti Word con Aspose.Words Java: Guida completa](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}