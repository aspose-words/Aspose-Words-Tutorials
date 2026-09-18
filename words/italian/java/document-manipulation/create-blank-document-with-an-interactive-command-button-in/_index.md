---
category: general
date: 2026-09-18
description: Crea un documento vuoto in Java e aggiungi un pulsante ActiveX. Impara
  come inserire un pulsante di comando, costruire un modulo interattivo e salvare
  un documento Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- create interactive form
- add activex button
- how to insert command button
- create word document
language: it
lastmod: 2026-09-18
og_description: Crea un documento vuoto in Java e incorpora un pulsante di comando
  ActiveX. Segui questa guida passo‑passo per creare un modulo interattivo e salvare
  il file Word.
og_image_alt: Screenshot of a Word document showing a clickable ActiveX command button
og_title: Crea un documento vuoto con un pulsante di comando interattivo in Word
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank document in Java and add an ActiveX button. Learn how
    to insert command button, build an interactive form, and save a Word document.
  headline: Create blank document with an interactive command button in Word using
    Java
  type: TechArticle
- description: Create blank document in Java and add an ActiveX button. Learn how
    to insert command button, build an interactive form, and save a Word document.
  name: Create blank document with an interactive command button in Word using Java
  steps:
  - name: 'Load the existing document: `Document doc = new Document("ExistingForm.docx");`'
    text: 'Load the existing document: `Document doc = new Document("ExistingForm.docx");`'
  - name: 'Move the builder to the desired location: `builder.moveToParagraph(5, 0);
      // 6th paragraph, first node`'
    text: 'Move the builder to the desired location: `builder.moveToParagraph(5, 0);
      // 6th paragraph, first node`'
  - name: Insert the button as shown in Step 3.
    text: Insert the button as shown in Step 3.
  - name: Adjust the button’s `Top`/`Left` based on the paragraph’s layout.
    text: Adjust the button’s `Top`/`Left` based on the paragraph’s layout.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
title: Crea documento vuoto con un pulsante di comando interattivo in Word usando
  Java
url: /it/java/document-manipulation/create-blank-document-with-an-interactive-command-button-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea documento vuoto con un pulsante di comando interattivo in Word usando Java

Se hai bisogno di **creare documento vuoto** che contenga un pulsante cliccabile, questa guida ti mostra esattamente come farlo con Aspose.Words per Java. Imparerai a costruire un modulo interattivo, aggiungere un pulsante ActiveX e infine salvare il file Word—tutto in pochi passaggi concisi.

Incorporare un pulsante di comando trasforma un .docx statico in un modulo funzionale con cui gli utenti finali possono interagire direttamente all'interno di Microsoft Word. Questo tutorial copre anche **come inserire pulsante di comando**, la gestione delle difficoltà comuni e l'estensione della soluzione per moduli più complessi.

## Prerequisiti

* Java 17 o versioni successive (il codice si compila con JDK 17+)
* Aspose.Words per Java 23.9 o più recente – la libreria fornisce `Document`, `DocumentBuilder` e `Forms2OleControl`.
* Un IDE o uno strumento di build (Maven/Gradle) che può aggiungere la dipendenza Aspose.Words.
* Conoscenze di base della sintassi Java e dei concetti dei documenti Word.

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## Passo 1: Crea un documento vuoto

La prima operazione è istanziare un nuovo oggetto `Document`. Questo oggetto rappresenta un file Word vuoto pronto per il contenuto.

```java
// Step 1: Create a new blank document
Document doc = new Document();
```

Creare un documento vuoto ti fornisce una tela pulita, fondamentale quando vuoi **creare documento Word** programmaticamente senza alcun modello preesistente.

## Passo 2: Inizializza un DocumentBuilder

`DocumentBuilder` è la classe principale per aggiungere testo, tabelle e controlli di modulo. Funziona sul `Document` che hai appena creato.

```java
// Step 2: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(doc);
```

Il builder mantiene il punto di inserimento corrente, così i comandi successivi influenzano la posizione corretta nel file.

## Passo 3: Inserisci un controllo pulsante di comando Forms2Ole

Aspose.Words espone la classe `Forms2OleControl` per i controlli ActiveX. Per **aggiungere pulsante activex**, richiedi un tipo `COMMANDBUTTON` dal builder.

```java
// Step 3: Insert a Forms2Ole command button control
Forms2OleControl commandButton = builder.insertForms2OleControl(OleControlType.COMMANDBUTTON);
```

Il metodo `insertForms2OleControl` inserisce il controllo nella posizione corrente del cursore del builder. Poiché il controllo è un oggetto ActiveX, funziona solo nella versione desktop di Microsoft Word, non in Word Online.

## Passo 4: Configura l'aspetto e la posizione del pulsante

Puoi impostare la didascalia, le dimensioni e la posizione del pulsante usando i metodi setter del controllo. I valori di posizione sono misurati in punti (1 punto = 1/72 di pollice).

```java
// Step 4: Configure the button's appearance and position
commandButton.setCaption("Click Me");   // Text shown on the button
commandButton.setTop(100);              // Distance from the top edge of the page (points)
commandButton.setLeft(100);             // Distance from the left edge of the page (points)
commandButton.setWidth(120);            // Optional: set button width
commandButton.setHeight(30);            // Optional: set button height
```

*Perché configurare queste proprietà?* Impostare `Top` e `Left` garantisce che il pulsante appaia dove ti aspetti nella pagina, mentre `Caption` definisce l'etichetta visibile all'utente. Se ometti larghezza/altezza, Word assegna dimensioni predefinite, che potrebbero non corrispondere al tuo design.

### Consiglio Pro
Se prevedi di aggiungere più controlli, chiama `builder.moveToDocumentEnd()` prima di ogni inserimento per evitare oggetti sovrapposti.

## Passo 5: Salva il documento con il pulsante di comando incorporato

Infine, scrivi il documento su disco. L'estensione del file deve essere `.docx` (o `.doc` per versioni Word più vecchie) per preservare il controllo ActiveX.

```java
// Step 5: Save the document with the embedded command button
String outputPath = "C:/temp/CommandButton.docx";
doc.save(outputPath);
System.out.println("Document saved to: " + outputPath);
```

Quando apri `CommandButton.docx` in Microsoft Word, vedrai un pulsante con l'etichetta **Click Me**. Cliccandolo si attiverà l'azione predefinita di ActiveX (che, di default, non fa nulla). In seguito puoi collegare una macro o uno script VBA per definire un comportamento personalizzato.

## Come inserire un pulsante di comando in un modulo esistente (opzionale)

Se hai già un modulo con campi di testo e vuoi **creare modulo interattivo** che includa un pulsante, segui questi passaggi aggiuntivi:

1. Carica il documento esistente: `Document doc = new Document("ExistingForm.docx");`
2. Sposta il builder nella posizione desiderata: `builder.moveToParagraph(5, 0); // 6° paragrafo, primo nodo`
3. Inserisci il pulsante come mostrato nel Passo 3.
4. Regola `Top`/`Left` del pulsante in base al layout del paragrafo.

Questo approccio ti consente di arricchire qualsiasi modello Word pre‑costruito con un pulsante ActiveX senza ricreare l'intero file.

## Casi limite e risoluzione dei problemi

| Situazione | Cosa controllare | Correzione consigliata |
|------------|------------------|------------------------|
| Il pulsante non appare in Word | Assicurati di aver aperto il file nella versione desktop di Word (Word Online rimuove ActiveX). | Apri il file in Word 2016+ desktop. |
| La didascalia è troncata | Verifica che la larghezza del pulsante sia sufficiente a contenere il testo. | Aumenta `setWidth` finché la didascalia non si adatta. |
| Salvataggio genera `IOException` | Conferma che la directory di output esista e che tu abbia i permessi di scrittura. | Crea la directory o esegui il programma con privilegi elevati. |
| Più pulsanti si sovrappongono | Il cursore del builder potrebbe non essersi spostato dopo l'inserimento precedente. | Chiama `builder.moveToDocumentEnd()` prima di inserire ogni nuovo controllo. |

## Esempio completo eseguibile

Di seguito trovi un programma Java completo e autonomo che puoi copiare, compilare ed eseguire. Dimostra **creare documento vuoto**, **aggiungere pulsante activex** e **salvare documento Word** in un unico flusso.

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) {
        try {
            // 1. Create a new blank document
            Document doc = new Document();

            // 2. Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3. Insert an ActiveX command button
            Forms2OleControl commandButton = builder.insertForms2OleControl(OleControlType.COMMANDBUTTON);

            // 4. Configure button properties
            commandButton.setCaption("Click Me");
            commandButton.setTop(100);   // points from top
            commandButton.setLeft(100);  // points from left
            commandButton.setWidth(120);
            commandButton.setHeight(30);

            // 5. Save the document
            String outPath = "CommandButton.docx";
            doc.save(outPath);
            System.out.println("Document created: " + outPath);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Output previsto**

```
Document created: CommandButton.docx
```

Aprendo `CommandButton.docx` si visualizza una singola pagina con un pulsante etichettato **Click Me** posizionato a 100 pt dal bordo superiore e sinistro.

## Conclusione

Ora sai come **creare documento vuoto**, incorporare un **pulsante ActiveX** e trasformare un semplice file Word in un **modulo interattivo**. Padroneggiando **come inserire pulsante di comando**, puoi estendere questo modello per aggiungere caselle di controllo, caselle combinate o persino logica VBA personalizzata.

Successivamente, considera di esplorare questi argomenti correlati:

* **Crea modulo interattivo** con campi di testo (`builder.insertField`)  
* **Aggiungi pulsante activex** che esegue una macro VBA (`builder.insertOleObject`)  
* **Crea documento Word** da un modello usando `Document(docTemplatePath)`  
* Convertire il .docx risultante in PDF mantenendo il pulsante (nota: il PDF renderizzerà il pulsante come immagine statica).

Sentiti libero di sperimentare con dimensioni, posizione e didascalia del pulsante per adattarle al design della tua interfaccia. Buon coding!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Come creare campi modulo e aggiungere contenuto usando DocumentBuilder in Aspose.Words per Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Crea progetto VBA in documento Word](/words/english/net/working-with-vba-macros/create-vba-project/)
- [Crea nuovo documento Word](/words/english/net/add-content-using-documentbuilder/create-new-document/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}