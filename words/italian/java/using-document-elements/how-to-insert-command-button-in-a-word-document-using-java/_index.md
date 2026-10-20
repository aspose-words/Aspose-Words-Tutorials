---
category: general
date: 2026-08-23
description: Scopri come inserire un pulsante di comando in un documento Word usando
  Java e Aspose.Words. Questa guida mostra come aggiungere un controllo modulo, impostare
  il nome del pulsante e incorporare un pulsante ActiveX.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert command button
- add form control
- how to add button
- set button name
- add activex button
language: it
lastmod: 2026-08-23
og_description: Inserisci un pulsante di comando in un documento Word usando Java.
  Segui questa guida per aggiungere un controllo modulo, impostare il nome del pulsante
  e incorporare un pulsante ActiveX con Aspose.Words.
og_image_alt: Screenshot of a Word document showing an inserted ActiveX command button
og_title: Inserire un pulsante di comando in Word con Java – guida passo passo
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Learn how to insert command button in a Word document using Java and
    Aspose.Words. This guide shows how to add form control, set button name, and embed
    an ActiveX button.
  headline: How to insert command button in a Word document using Java
  type: TechArticle
- description: Learn how to insert command button in a Word document using Java and
    Aspose.Words. This guide shows how to add form control, set button name, and embed
    an ActiveX button.
  name: How to insert command button in a Word document using Java
  steps:
  - name: Open `CommandButtonDemo.docx` with Microsoft Word (2016 or later).
    text: Open `CommandButtonDemo.docx` with Microsoft Word (2016 or later).
  - name: The **Submit** button appears where the cursor was positioned during insertion.
    text: The **Submit** button appears where the cursor was positioned during insertion.
  - name: Right‑click the button and choose **Properties** to see that the **Name**
      field contains `btnSubmit`.
    text: Right‑click the button and choose **Properties** to see that the **Name**
      field contains `btnSubmit`.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Come inserire un pulsante di comando in un documento Word usando Java
url: /it/java/using-document-elements/how-to-insert-command-button-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come inserire un pulsante di comando in un documento Word usando Java

Se hai bisogno di **insert command button** in un file Word, questo tutorial ti mostra una soluzione completa con Aspose.Words for Java. Vedrai come aggiungere un controllo modulo, configurare la sua didascalia e impostare il nome del pulsante senza lasciare l'IDE.

La guida copre tutto ciò che ti serve per creare un `.docx` che contiene un pulsante ActiveX pronto per l'uso in Microsoft Word. Non è necessario alcun strumento aggiuntivo e l'esempio funziona su Java 8+.

## Cosa imparerai

* Come aggiungere un controllo modulo di tipo **CommandButton** a un documento Word.  
* I passaggi esatti per **set button name** e **add activex button** proprietà.  
* Come salvare il documento in modo che il pulsante appaia correttamente quando aperto in Word.  

Dovresti avere un ambiente di sviluppo Java di base e un progetto Maven o Gradle che possa importare la libreria Aspose.Words.

## Prerequisiti

| Requisito | Motivo |
|-------------|--------|
| Java 8 o versioni successive | Aspose.Words for Java funziona su Java 8+. |
| Strumento di build Maven o Gradle | Semplifica l'aggiunta della dipendenza Aspose.Words. |
| Licenza Aspose.Words for Java (o prova gratuita) | Necessaria per l'intero set di funzionalità; l'API funziona in modalità valutazione. |
| Un IDE come IntelliJ IDEA o Eclipse | Rende più semplice modificare ed eseguire l'esempio. |

## Passo 1: Aggiungi Aspose.Words al tuo progetto

Se usi Maven, aggiungi la seguente dipendenza a `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest version -->
</dependency>
```

Per Gradle, inserisci questa riga in `build.gradle`:

```gradle
implementation 'com.aspose:aspose-words:24.9'
```

Una volta risolta la dipendenza, puoi importare le classi della libreria nel tuo file sorgente Java.

## Passo 2: Inserisci il pulsante di comando – il codice principale

Crea una nuova classe Java chiamata `InsertCommandButtonDemo`. Il codice qui sotto esegue tutte e quattro le azioni necessarie per **insert command button**:

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Add form control – an ActiveX CommandButton – to the document
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // 3️⃣ Set button name and displayed caption (this answers the "set button name" need)
        commandButton.setName("btnSubmit");
        commandButton.setCaption("Submit");

        // 4️⃣ Save the document with the embedded button
        doc.save("CommandButtonDemo.docx");
    }
}
```

### Perché ogni riga è importante

* **Document & DocumentBuilder** – Forniscono la rappresentazione in‑memoria di un file Word e l'API per modificarne il contenuto.  
* **insertForms2OleControl** – Questo metodo **adds form control** di tipo `COMMAND_BUTTON`. L'oggetto `Forms2OleControl` restituito rappresenta il controllo ActiveX.  
* **setName** – Assegna un identificatore programmatico (`btnSubmit`). Le macro Word o VBA possono fare riferimento a questo nome in seguito.  
* **setCaption** – Definisce il testo che l'utente vede sul pulsante, rispondendo alla domanda “come aggiungere un pulsante”.  
* **save** – Scrive il `.docx` su disco, preservando il pulsante ActiveX incorporato.  

Eseguendo il programma si crea `CommandButtonDemo.docx` nella directory di lavoro. Aprendo il file in Microsoft Word viene mostrato un pulsante etichettato **Submit** che puoi cliccare (visualizzerà una finestra di dialogo ActiveX predefinita in modalità valutazione).

## Passo 3: Verifica il pulsante inserito in Word

1. Apri `CommandButtonDemo.docx` con Microsoft Word (2016 o successivo).  
2. Il pulsante **Submit** appare dove il cursore era posizionato durante l'inserimento.  
3. Fai clic destro sul pulsante e scegli **Properties** per vedere che il campo **Name** contiene `btnSubmit`.  

Se il pulsante non appare, assicurati che i **ActiveX controls** siano abilitati nelle impostazioni del Trust Center di Word.

## Passo 4: Personalizzare il pulsante (opzionale)

Puoi ulteriormente personalizzare il pulsante regolando le sue dimensioni, posizione o aggiungendo una macro VBA. La classe `Forms2OleControl` espone proprietà aggiuntive come `setWidth`, `setHeight` e `setLeft`. Di seguito un esempio che rende il pulsante più grande:

```java
commandButton.setWidth(100);   // Width in points
commandButton.setHeight(30);   // Height in points
commandButton.setLeft(50);     // Horizontal offset from the left margin
```

Queste righe possono essere inserite dopo la chiamata `setCaption`. Dimostrano la personalizzazione **add activex button** oltre l'inserimento di base.

## Problemi comuni e come evitarli

| Sintomo | Causa | Correzione |
|---------|-------|------------|
| Il pulsante non appare in Word | Documento salvato prima che il controllo fosse aggiunto | Assicurati che `insertForms2OleControl` sia chiamato prima di `doc.save`. |
| La didascalia del pulsante è vuota | `setCaption` non chiamato o chiamato con una stringa vuota | Fornisci una stringa non vuota, ad esempio `"Submit"`. |
| VBA non riesce a trovare il pulsante | Mismatch del nome tra il codice VBA e il valore di `setName` | Mantieni il nome coerente; usa `setName("btnSubmit")` e fai riferimento a `btnSubmit` in VBA. |
| Avviso di sicurezza all'apertura del file | La sicurezza macro di Word blocca i controlli ActiveX | Regola Trust Center > Macro Settings, o firma il documento con un certificato attendibile. |

## Esempio completo, eseguibile

Di seguito il file sorgente completo, pronto per il copia‑incolla nel tuo IDE. Include le istruzioni di import, la gestione delle eccezioni e un blocco di commenti che spiega ogni passaggio principale.

```java
// InsertCommandButtonDemo.java
// Demonstrates how to insert an ActiveX CommandButton into a Word document using Aspose.Words for Java.

import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Add a CommandButton form control (ActiveX) to the document.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // Step 3: Configure the button – set its programmatic name and visible caption.
        commandButton.setName("btnSubmit");   // This answers the "set button name" requirement.
        commandButton.setCaption("Submit");   // This is the text the user sees.

        // Optional: Resize and reposition the button (demonstrates add activex button customization).
        commandButton.setWidth(100);
        commandButton.setHeight(30);
        commandButton.setLeft(50);

        // Step 4: Save the document. The button is now embedded and will appear in Word.
        doc.save("CommandButtonDemo.docx");
    }
}
```

**Risultato atteso:** Dopo aver eseguito il programma, `CommandButtonDemo.docx` contiene un unico pulsante **Submit**. Aprendo il file in Word il pulsante appare esattamente dove era posizionato il cursore di `DocumentBuilder`.

## Prossimi passi

* **Add more form controls** – Usa `Forms2OleControlType.CHECK_BOX`, `RADIO_BUTTON` o `TEXT_BOX` per creare moduli Word completi.  
* **Combine with mail merge** – Inserisci pulsanti in un documento con stampa unione per creare moduli interattivi personalizzati.  
* **Attach VBA macros** – Incorpora programmaticamente VBA che reagisce all'evento `Click` del pulsante per automazione avanzata.  

Questi argomenti estendono naturalmente la tecnica **add form control** che hai appena imparato.

---

### Riepilogo

Ora sai come **insert command button** in un documento Word usando Java, come **add form control**, come **set button name** e come personalizzare **add activex button**. L'esempio completo funziona subito, e puoi adattarlo a qualsiasi flusso di generazione di documenti. Buon coding!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Come creare campi modulo e aggiungere contenuto usando DocumentBuilder in Aspose.Words per Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Inserire campo modulo Combo Box in documento Word](/words/english/net/working-with-form-fields/insert-form-fields/)
- [Inserire campo modulo Check Box in documento Word](/words/english/net/add-content-using-documentbuilder/insert-check-box-form-field/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}