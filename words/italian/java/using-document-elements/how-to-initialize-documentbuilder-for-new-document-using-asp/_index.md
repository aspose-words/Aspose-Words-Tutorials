---
category: general
date: 2026-10-04
description: Scopri come inizializzare DocumentBuilder per un nuovo documento e aggiungere
  un pulsante ActiveX con Aspose.Words in Java. Guida passo‑passo con codice completo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- initialize DocumentBuilder for new document
- insert ActiveX button
- Forms2OleControl command button
- Aspose.Words DocumentBuilder example
- create Word document with ActiveX
language: it
lastmod: 2026-10-04
og_description: Inizializza DocumentBuilder per un nuovo documento e incorpora un
  pulsante di comando ActiveX usando l'API Java di Aspose.Words. Segui questo breve
  tutorial.
og_image_alt: Screenshot showing DocumentBuilder initialized for a new document with
  an ActiveX button
og_title: Inizializzare DocumentBuilder per un nuovo documento – guida completa di
  Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to initialize DocumentBuilder for new document and add an
    ActiveX button with Aspose.Words in Java. Step‑by‑step guide with full code.
  headline: How to initialize DocumentBuilder for new document using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- Java
- DocumentBuilder
- ActiveX
title: Come inizializzare DocumentBuilder per un nuovo documento usando Aspose.Words
url: /it/java/using-document-elements/how-to-initialize-documentbuilder-for-new-document-using-asp/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come inizializzare DocumentBuilder per un nuovo documento usando Aspose.Words

Se hai bisogno di **inizializzare DocumentBuilder per un nuovo documento** in un progetto Java, questo tutorial ti mostra i passaggi esatti. Vedrai come creare un file Word vuoto, allegare un pulsante di comando ActiveX e salvare il risultato—tutto con un unico esempio di codice autonomo.

Lavorare programmaticamente con documenti Word spesso significa gestire dettagli a basso livello come i controlli dei moduli. Alla fine di questa guida sarai in grado di incorporare un pulsante ActiveX senza uscire dal tuo IDE, il che è utile per generare modelli, report automatizzati o moduli interattivi.

## Prerequisiti

Prima di iniziare, assicurati di avere:

* Java 17 o versioni successive installato  
* Maven 3.8+ (o Gradle se preferisci)  
* Una licenza Aspose.Words per Java (la versione di prova gratuita è valida per i test)  
* Familiarità di base con la sintassi Java  

Se sei nuovo a Aspose.Words, la libreria fornisce un'API di alto livello per creare, modificare e salvare documenti Word. La classe `DocumentBuilder` è il punto di ingresso principale per costruire il contenuto del documento.

## Step 1: Configura il progetto Maven

Crea un nuovo progetto Maven (o aggiungilo a uno esistente) e includi la dipendenza Aspose.Words:

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>activex-demo</artifactId>
    <version>1.0.0</version>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- Use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

> **Consiglio professionale:** Mantieni la versione della libreria aggiornata; le versioni più recenti aggiungono il supporto per controlli di modulo aggiuntivi e migliorano le prestazioni.

## Step 2: Inizializza `DocumentBuilder` per un nuovo documento

Il cuore del tutorial è l'operazione **initialize DocumentBuilder for new document**. Prima crei un'istanza vuota di `Document`, quindi la passi al costruttore di `DocumentBuilder`.

```java
import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a new empty document
        Document doc = new Document();

        // Step 2.2: Initialize DocumentBuilder for new document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Perché è importante:* Inizializzare `DocumentBuilder` collega il builder a un oggetto `Document` specifico, consentendoti di aggiungere paragrafi, tabelle o controlli di modulo direttamente a quel documento. Senza questo passaggio il builder non avrebbe alcun target su cui operare.

## Step 3: Inserisci un controllo pulsante di comando ActiveX

Aspose.Words espone la classe `Forms2OleControl` per incorporare controlli ActiveX legacy. Il codice seguente aggiunge un **pulsante di comando Forms2OleControl** alla posizione corrente del cursore.

```java
        // Step 3.1: Insert an ActiveX command button control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 3.2: Set the button caption (the text displayed on the button)
        commandButton.setCaption("Click Me");
```

### Che cos'è un pulsante di comando ActiveX?

Un pulsante di comando ActiveX è un elemento UI legacy che può eseguire macro o attivare eventi quando l'utente lo clicca all'interno di un documento Word. Sebbene le versioni moderne di Office favoriscano i Content Controls, molti modelli aziendali si affidano ancora a ActiveX per compatibilità retroattiva.

## Step 4: Salva il documento

Dopo aver inserito il controllo, chiami semplicemente `save`. Il file conterrà il pulsante ActiveX e potrà essere aperto in Microsoft Word.

```java
        // Step 4: Save the document containing the ActiveX button
        String outputPath = "output/ActiveXButton.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Quando apri `ActiveXButton.docx` in Word, vedrai un pulsante etichettato **Click Me**. Cliccare il pulsante non farà nulla a meno che non venga allegata una macro, ma il controllo stesso è pienamente funzionale.

## Esempio completo, eseguibile

Di seguito trovi il programma completo che puoi copiare‑incollare in `src/main/java/com/example/ActiveXButtonDemo.java`. Include tutti gli import e la gestione degli errori necessari per un rapido test.

```java
package com.example;

import com.aspose.words.*;

public class ActiveXButtonDemo {
    public static void main(String[] args) {
        try {
            // Step 1: Create a new empty document
            Document doc = new Document();

            // Step 2: Initialize DocumentBuilder for new document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Insert an ActiveX command button control
            Forms2OleControl commandButton = builder.insertForms2OleControl(
                    Forms2OleControlType.COMMANDBUTTON);
            commandButton.setCaption("Click Me");

            // Step 4: Save the document
            String outputPath = "output/ActiveXButton.docx";
            doc.save(outputPath);
            System.out.println("Document saved to " + outputPath);
        } catch (Exception e) {
            System.err.println("Error creating document: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Output previsto**

```
Document saved to output/ActiveXButton.docx
```

Apri il file generato in Microsoft Word 2016 o versioni successive; dovresti vedere un pulsante etichettato *Click Me* posizionato in cima alla prima pagina.

## Variazioni comuni e casi limite

| Scenario | Adeguamento |
|----------|------------|
| **Aggiungere il pulsante a un paragrafo specifico** | Sposta il cursore del builder con `builder.moveToParagraph(index, NodeType.PARAGRAPH);` prima di chiamare `insertForms2OleControl`. |
| **Impostare le dimensioni del pulsante** | Usa `commandButton.setWidth(100);` e `commandButton.setHeight(30);` per definire le dimensioni in punti. |
| **Aggiungere una macro al pulsante** | Dopo aver salvato il documento, aprilo in Word, abilita la scheda Sviluppatore e allega manualmente una macro VBA al pulsante (i controlli ActiveX non possono essere scriptati direttamente da Aspose.Words). |
| **Target formato .doc (binario)** | Cambia `doc.save(outputPath, SaveFormat.DOC);` per produrre un file Word 97‑2003 legacy. |
| **Eseguire su Android** | Usa Aspose.Words per Android tramite la sua API Java; lo stesso codice funziona finché la libreria è inclusa nell'APK. |

## Suggerimenti per la risoluzione dei problemi

* **`java.lang.NoClassDefFoundError`** – Assicurati che il JAR di Aspose.Words sia nel classpath. Maven lo aggiunge automaticamente; per build manuali, posiziona il JAR in `libs/` e aggiungilo alle librerie del tuo IDE.  
* **Il pulsante non appare in Word** – Verifica che l'opzione *Mostra moduli legacy* sia abilitata nel Trust Center di Word (`File → Options → Trust Center → Trust Center Settings → Macro Settings`).  
* **Eccezione di licenza** – Se esegui il codice senza una licenza valida, Aspose.Words inserirà una filigrana. Registra una prova gratuita o acquista una licenza per rimuoverla.

## Conclusione

Ora sai come **inizializzare DocumentBuilder per un nuovo documento**, inserire un pulsante di comando ActiveX e salvare il risultato con Aspose.Words per Java. Questo modello ti consente di generare template Word interattivi in modo programmatico, particolarmente utile per report automatizzati o flussi di lavoro basati su moduli.

Da qui puoi esplorare controlli di modulo aggiuntivi (`Forms2OleControlType.CHECKBOX`, `COMBOBOX`, ecc.), combinare il pulsante con macro VBA personalizzate o generare documenti completi che includono tabelle, immagini e stili—tutto usando lo stesso flusso di lavoro `DocumentBuilder`.

---

*Pronto a creare automazioni Word più complesse? Dai un'occhiata alle nostre guide su **insert table with DocumentBuilder**, **apply styles programmatically** e **export to PDF with Aspose.Words**.*

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Come creare campi modulo e aggiungere contenuto usando DocumentBuilder in Aspose.Words per Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Come salvare un documento come PDF con Aspose.Words per Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Aggiungere una filigrana a un documento usando Aspose.Words per Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}