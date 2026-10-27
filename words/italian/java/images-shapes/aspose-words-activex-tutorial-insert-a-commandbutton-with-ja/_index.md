---
category: general
date: 2026-08-07
description: Il tutorial Aspose.Words ActiveX mostra come aggiungere un controllo
  CommandButton a un documento Word usando Java. Scopri il codice completo, la configurazione
  e i passaggi di salvataggio.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose words activex tutorial
- aspose.words java
- activeX control java
- documentbuilder insert control
- forms2olecontrol usage
language: it
lastmod: 2026-08-07
og_description: Il tutorial Aspose.Words ActiveX spiega come incorporare un controllo
  ActiveX CommandButton in un documento Word utilizzando Java. Segui l'esempio completo
  per creare, configurare e salvare il documento.
og_image_alt: Screenshot of a Word document with a CommandButton added via Aspose.Words
  ActiveX tutorial
og_title: Tutorial ActiveX di Aspose.Words – Guida passo‑passo per Java
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Aspose.Words ActiveX tutorial shows how to add a CommandButton control
    to a Word document using Java. Learn the full code, configuration, and saving
    steps.
  headline: Aspose.Words ActiveX tutorial – insert a CommandButton with Java
  type: TechArticle
- description: Aspose.Words ActiveX tutorial shows how to add a CommandButton control
    to a Word document using Java. Learn the full code, configuration, and saving
    steps.
  name: Aspose.Words ActiveX tutorial – insert a CommandButton with Java
  steps:
  - name: Initialize a `Document` and `DocumentBuilder`.
    text: Initialize a `Document` and `DocumentBuilder`.
  - name: Insert a `Forms2OleControl` of type `COMMAND_BUTTON`.
    text: Insert a `Forms2OleControl` of type `COMMAND_BUTTON`.
  - name: Set the button’s name, caption, size, and position.
    text: Set the button’s name, caption, size, and position.
  - name: Save the document as a .docx file that contains the ActiveX control.
    text: Save the document as a .docx file that contains the ActiveX control.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
title: Tutorial ActiveX di Aspose.Words – inserire un CommandButton con Java
url: /it/java/images-shapes/aspose-words-activex-tutorial-insert-a-commandbutton-with-ja/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tutorial Aspose.Words ActiveX – inserire un CommandButton con Java

Se hai bisogno di incorporare un controllo ActiveX in un file Word, questo **tutorial Aspose.Words ActiveX** ti guida attraverso l’intero processo. Vedrai come creare un documento vuoto, inserire un CommandButton, impostarne le proprietà e salvare il risultato—tutto con semplice codice Java.

L’esempio utilizza l’Aspose.Words for Java API, che elimina la necessità di Microsoft Office sul server di build. Alla fine di questa guida potrai generare file .docx che contengono controlli CommandButton pienamente funzionali, pronti per l’uso in ambienti Windows.

## Prerequisiti

Prima di iniziare, assicurati di avere:

- Java Development Kit (JDK) 8 o versioni successive installate.
- Maven o un altro tool di build per gestire le dipendenze.
- Una licenza Aspose.Words for Java (o una chiave di valutazione temporanea) per evitare le filigrane di valutazione.
- Familiarità di base con la sintassi Java e la programmazione orientata agli oggetti.

> **Suggerimento:** Aggiungi la dipendenza Maven di Aspose.Words al tuo `pom.xml` per consentire all’IDE di risolvere automaticamente le classi:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest version -->
</dependency>
```

## Passo 1: Creare un nuovo documento vuoto e un `DocumentBuilder`

La classe `Document` rappresenta il file Word in memoria, mentre `DocumentBuilder` fornisce un’API fluida per modificare il documento. Inizializzare entrambi gli oggetti prepara il documento per ulteriori modifiche.

```java
import com.aspose.words.*;

public class ActiveXDemo {
    public static void main(String[] args) throws Exception {
        // Create an empty Word document
        Document document = new Document();

        // DocumentBuilder lets you add text, tables, and controls
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Perché è importante:**  
`DocumentBuilder` tiene traccia della posizione corrente del cursore, così qualsiasi operazione di inserimento successiva—come l’aggiunta di un controllo—appare esattamente dove desideri.

## Passo 2: Inserire un controllo ActiveX CommandButton

Aspose.Words espone `Forms2OleControl` per gli oggetti ActiveX. Il metodo `insertForms2OleControl` richiede il tipo di controllo, che specifichi tramite l’enumerazione `Forms2OleControlType`.

```java
        // Insert a CommandButton ActiveX control at the current cursor location
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
```

**Spiegazione:**  
Il controllo inserito è un oggetto basato su COM che Word renderizzerà come un pulsante cliccabile quando il documento viene aperto in un ambiente Windows.

## Passo 3: Configurare le proprietà del pulsante

Dopo l’inserimento, puoi regolare nome, didascalia, dimensioni e posizione del pulsante. Queste proprietà influenzano l’aspetto e il comportamento del controllo all’interno di Word.

```java
        // Set the logical name used by VBA or external scripts
        commandButton.setName("cmdSubmit");

        // Text displayed on the button face
        commandButton.setCaption("Submit");

        // Position the button 100 points from the left margin and 150 points from the top
        commandButton.setLeft(100);
        commandButton.setTop(150);

        // Define the button’s dimensions (width × height) in points
        commandButton.setWidth(80);
        commandButton.setHeight(30);
```

**Perché queste impostazioni sono importanti:**  

- **Name** – Consente alle macro VBA di fare riferimento al controllo (`ActiveDocument.Forms("cmdSubmit")`).
- **Caption** – Determina l’etichetta visibile su cui gli utenti fanno clic.
- **Left / Top** – Controllano il posizionamento rispetto ai margini della pagina.
- **Width / Height** – Garantiscono una dimensione visiva coerente su diverse risoluzioni dello schermo.

## Passo 4: Salvare il documento

Chiamare `save` scrive la rappresentazione in memoria su un file fisico. Puoi scegliere qualsiasi formato supportato (`.docx`, `.doc`, `.pdf`, ecc.). Per questo tutorial manteniamo il formato Word nativo.

```java
        // Persist the document with the embedded ActiveX control
        document.save("output/ActiveXDemo.docx");
    }
}
```

**Risultato:**  
Aprendo `ActiveXDemo.docx` in Microsoft Word viene visualizzato un CommandButton con etichetta **Submit** posizionato alle coordinate specificate. Cliccare il pulsante attiva il comportamento predefinito (nessun codice VBA associato per impostazione predefinita).

## Codice sorgente completo

Unendo tutti i pezzi, il programma completo e eseguibile è il seguente:

```java
import com.aspose.words.*;
import com.aspose.words.forms.*;

public class ActiveXDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a CommandButton ActiveX control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // Step 3: Configure the button's properties
        commandButton.setName("cmdSubmit");
        commandButton.setCaption("Submit");
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // Step 4: Save the document with the ActiveX control
        document.save("output/ActiveXDemo.docx");
    }
}
```

### Output previsto

- Un file chiamato **ActiveXDemo.docx** nella cartella `output`.
- Quando aperto in Microsoft Word (Windows), il documento mostra un pulsante **Submit** cliccabile nella posizione definita.
- Il pulsante può essere selezionato, spostato o collegato a codice VBA tramite l’interfaccia di Word (Sviluppatore → Proprietà).

## Gestione delle variazioni comuni

| Scenario | Adeguamento |
|----------|------------|
| **Salva come .doc** (formato legacy) | `document.save("ActiveXDemo.doc", SaveFormat.DOC);` |
| **Aggiungere un gestore di eventi** | Word non espone gli eventi ActiveX tramite Aspose.Words. È necessario aggiungere manualmente il codice VBA dopo la generazione del documento. |
| **Controlli multipli** | Ripeti il blocco di inserimento/configurazione con valori diversi per `setName` e `setCaption`. |
| **Tipo di controllo diverso (es. CheckBox)** | Usa `Forms2OleControlType.CHECKBOX` nella chiamata a `insertForms2OleControl`. |
| **Piattaforme non‑Windows** | I controlli ActiveX vengono renderizzati solo su Word per Windows. Per soluzioni cross‑platform, considera i controlli di contenuto (`StructuredDocumentTag`). |

## Best practice e insidie

- **Licenza anticipata** – Registra la licenza Aspose.Words prima di creare il `Document` per evitare i messaggi di valutazione.
- **Sistema di coordinate** – Le posizioni sono misurate in punti (1 pt = 1/72 in). Converti da pixel o centimetri se il tuo design UI utilizza quelle unità.
- **Percorsi file** – Usa percorsi assoluti o l’API `Paths` di Java per evitare `FileNotFoundException` quando la directory di output non esiste.
- **Sicurezza dei thread** – `Document` e `DocumentBuilder` non sono thread‑safe. Crea istanze separate per thread se generi documenti in parallelo.
- **Test** – Verifica il documento generato sulla versione target di Word (es. Word 2016, Word 365) perché le versioni più vecchie potrebbero visualizzare i controlli ActiveX in modo diverso.

## Conclusione

Questo **tutorial Aspose.Words ActiveX** dimostra come aggiungere programmaticamente un controllo CommandButton a un documento Word usando Java. Hai imparato a:

1. Inizializzare un `Document` e un `DocumentBuilder`.
2. Inserire un `Forms2OleControl` di tipo `COMMAND_BUTTON`.
3. Impostare nome, didascalia, dimensioni e posizione del pulsante.
4. Salvare il documento come file .docx contenente il controllo ActiveX.

Da qui puoi esplorare altri tipi di controllo, automatizzare l’iniezione di macro VBA o combinare i controlli ActiveX con altre funzionalità di Aspose.Words, come la stampa unione e i controlli di contenuto. Sperimenta con layout diversi e integra i documenti generati nel tuo più ampio pipeline di reporting basato su Java.

---


## Cosa dovresti imparare dopo?


I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare ulteriori funzionalità dell’API ed esplorare approcci alternativi di implementazione nei tuoi progetti.

- [Utilizzare oggetti OLE e controlli ActiveX in Aspose.Words per Java](/words/english/java/using-document-elements/using-ole-objects-and-activex/)
- [Come creare campi modulo e aggiungere contenuti usando DocumentBuilder in Aspose.Words per Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Convertire Word in RTF con il tutorial Aspose.Words per Java](/words/english/java/document-loading-and-saving/saving-documents-as-rtf-format/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}