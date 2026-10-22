---
category: general
date: 2026-07-20
description: Come aggiungere un pulsante a un documento Word usando Aspose.Words.
  Impara a inserire un pulsante Forms2OleControl con DocumentBuilder in pochi minuti.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add button to word document
- Forms2OleControl
- DocumentBuilder
- insertForms2OleControl
- Word automation
language: it
lastmod: 2026-07-20
og_description: Come aggiungere un pulsante a un documento Word con Aspose.Words.
  Segui questa guida pratica per incorporare un CommandButton Forms2OleControl usando
  Java.
og_image_alt: Screenshot of a Word document with a clickable button added via Aspose.Words
  (how to add button to word document)
og_title: Come aggiungere un pulsante a un documento Word – Tutorial completo su Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: How to add button to Word document using Aspose.Words. Learn to insert
    a Forms2OleControl button with DocumentBuilder in minutes.
  headline: How to Add Button to Word Document – Step‑by‑Step Guide
  type: TechArticle
- description: How to add button to Word document using Aspose.Words. Learn to insert
    a Forms2OleControl button with DocumentBuilder in minutes.
  name: How to Add Button to Word Document – Step‑by‑Step Guide
  steps:
  - name: '`Forms2OleControlType.COMMANDBUTTON` – tells Word we want a button.'
    text: '`Forms2OleControlType.COMMANDBUTTON` – tells Word we want a button.'
  - name: '`100` – width in points (≈1.39 inches).'
    text: '`100` – width in points (≈1.39 inches).'
  - name: '`30` – height in points (≈0.42 inches).'
    text: '`30` – height in points (≈0.42 inches).'
  type: HowTo
tags:
- Aspose.Words
- Java
- Office Automation
title: Come aggiungere un pulsante a un documento Word – Guida passo passo
url: /it/java/using-document-elements/how-to-add-button-to-word-document-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come aggiungere un pulsante a un documento Word – Tutorial completo Aspose.Words

Ti sei mai chiesto **come aggiungere un pulsante a un documento Word** senza aprire l'interfaccia grafica e fare clic ovunque? Non sei l'unico. Molti sviluppatori hanno bisogno di incorporare programmaticamente controlli interattivi—pensa a un pulsante “Invia” in un modello che sarà poi compilato da un utente finale. La buona notizia? Con Aspose.Words per Java puoi farlo in poche righe.

In questo tutorial percorreremo passo dopo passo le istruzioni per inserire un `Forms2OleControl` di tipo **CommandButton** usando il `DocumentBuilder`. Alla fine avrai un file `.docx` pronto all'uso che mostra un pulsante cliccabile etichettato “Click Me”. Nessun mistero, solo codice chiaro e la motivazione dietro ogni riga.

## Cosa imparerai

- Come creare un nuovo documento Word da zero.
- Come usare **DocumentBuilder** per posizionare un **Forms2OleControl**.
- Perché impostare la didascalia del pulsante e le dimensioni nel modo in cui lo facciamo.
- Come salvare e verificare il risultato.
- Problemi comuni (ad es., librerie mancanti, tipi di controllo non supportati) e come evitarli.

**Prerequisiti** – Hai bisogno di Java 8+ (o versioni successive) e della libreria Aspose.Words per Java (versione 23.12 o successiva). Un IDE come IntelliJ IDEA o Eclipse renderà le cose più fluide, ma qualsiasi editor di testo funziona.

---

## Passo 1: Configura il tuo progetto e importa le dipendenze

Prima che qualsiasi codice venga eseguito, Maven (o Gradle) deve sapere dove recuperare Aspose.Words. Aggiungi questo snippet al tuo `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

Se preferisci Gradle, l'equivalente è:

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

> **Consiglio pro:** Usa l'ultima release; le versioni più vecchie potrebbero non includere l'API `Forms2OleControl`.

Una volta risolta la dipendenza, sei pronto a scrivere codice Java.

---

## Passo 2: Crea un nuovo documento e ottieni un DocumentBuilder

La classe `Document` rappresenta l'intero pacchetto `.docx`, mentre `DocumentBuilder` è il pennello che usi per dipingere contenuti su di esso. Pensa al `DocumentBuilder` come al “cursore” che sa dove deve andare il prossimo elemento.

```java
import com.aspose.words.*;

public class AddButtonExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder tied to the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Perché è importante:** Inizializzare un nuovo `Document` ti fornisce una tela pulita. Il builder punta automaticamente al primo paragrafo, così non devi gestire manualmente sezioni o pagine.

---

## Passo 3: Inserisci un Forms2OleControl di tipo CommandButton

Ora arriva la star dello spettacolo: `insertForms2OleControl`. Questo metodo crea un controllo OLE (Object Linking and Embedding) che Word tratta come elemento di modulo. Passeremo tre argomenti:

1. `Forms2OleControlType.COMMANDBUTTON` – indica a Word che vogliamo un pulsante.
2. `100` – larghezza in punti (≈1,39 pollici).
3. `30` – altezza in punti (≈0,42 pollici).

```java
        // Step 3: Insert a CommandButton with specific dimensions
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);
```

**Come funziona:** Dietro le quinte Aspose.Words genera l'XML appropriato nella parte `word/document.xml`, facendo riferimento all'oggetto OLE. Le dimensioni fornite sono rispettate dal motore di layout di Word, quindi il pulsante appare esattamente dove il cursore del builder è posizionato.

---

## Passo 4: Imposta la didascalia (testo) sul pulsante

Un pulsante senza etichetta è confuso—immagina un pulsante dell'ascensore silenzioso. Il metodo `setCaption` imposta il testo visibile:

```java
        // Step 4: Define the button's label
        commandButton.setCaption("Click Me");
```

Puoi cambiare la didascalia in qualsiasi cosa: “Submit”, “Approve” o anche una stringa localizzata. La didascalia è memorizzata nelle proprietà dell'oggetto OLE, così Word la renderà nativamente.

---

## Passo 5: Salva il documento e verifica il risultato

Infine, scrivi il file su disco. Scegli una cartella in cui hai permessi di scrittura; altrimenti otterrai un `IOException`.

```java
        // Step 5: Persist the document
        String outputPath = "output/button-demo.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

Apri `button-demo.docx` in Microsoft Word. Dovresti vedere un pulsante etichettato **Click Me** posizionato in cima al documento. Cliccarlo in Word attiverà il comportamento OLE predefinito (di solito un messaggio segnaposto, a meno che non colleghi una macro).

---

## Casi limite comuni e come gestirli

| Situazione | Perché accade | Soluzione |
|------------|----------------|-----------|
| **Tipo `Forms2OleControl` mancante** | Le versioni più vecchie di Aspose.Words non esponevano questo enum. | Aggiorna a 23.12+ o successiva. |
| **Il pulsante appare come immagine** | Le impostazioni di sicurezza di Word bloccano i controlli OLE. | Abilita “Consenti l'accesso al modello di oggetti del progetto VBA” nel Centro protezione, oppure usa un file `.docm` abilitato alle macro. |
| **Dimensione errata** | Confusione tra punti e pixel. | Ricorda che 1 punto = 1/72 pollice. Regola i numeri di conseguenza. |
| **Salvataggio genera `FileNotFoundException`** | Il percorso non esiste. | Assicurati che la directory (`output/`) sia creata prima di `doc.save`. Usa `new File("output").mkdirs();`. |

---

## Estendere l'esempio: aggiungere più pulsanti o altri controlli

Se ti servono più pulsanti, sposta semplicemente il cursore del builder con `builder.moveTo` o `builder.writeln()` prima di chiamare nuovamente `insertForms2OleControl`.

```java
        // Add a second button below the first
        builder.writeln(); // moves to a new paragraph
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 120, 35);
        secondButton.setCaption("Submit");
```

Puoi anche inserire un **CheckBox**, **ComboBox** o **ListBox** sostituendo `Forms2OleControlType.COMMANDBUTTON` con il valore enum appropriato (`CHECKBOX`, `COMBOBOX`, ecc.). Gli stessi parametri di larghezza/altezza si applicano.

---

## Come si inserisce in flussi di lavoro più ampi di automazione Word

- **Generazione di template:** Crea un modello di contratto che includa un pulsante “Approve” per l'approvazione a valle.
- **Reporting:** Genera un report giornaliero con un pulsante “Refresh Data” che attiva una macro.
- **Distribuzione di moduli:** Spedisci un questionario con controlli interattivi pre‑popolati.

Tutti questi scenari beneficiano dell’**automazione Word** mostrata. Inserendo i controlli programmaticamente, elimini la modifica manuale e riduci gli errori umani.

---

## Codice sorgente completo (pronto per il copia‑incolla)

```java
import com.aspose.words.*;

public class AddButtonExample {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document doc = new Document();

        // Obtain a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a CommandButton (width: 100pt, height: 30pt)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);

        // Set the button caption
        commandButton.setCaption("Click Me");

        // Optionally add a second button
        builder.writeln(); // new paragraph
        Forms2OleControl secondButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 120, 35);
        secondButton.setCaption("Submit");

        // Save the document
        String outputPath = "output/button-demo.docx";
        new java.io.File("output").mkdirs(); // ensure directory exists
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

**Output previsto:** Quando apri `output/button-demo.docx` in Microsoft Word, vedrai due pulsanti—“Click Me” e “Submit”—impilati verticalmente in cima al file.

---

## Conclusione

Abbiamo risposto a **come aggiungere un pulsante a un documento Word** usando Aspose.Words per Java, passo dopo passo. Partendo da un `Document` vuoto, abbiamo sfruttato **DocumentBuilder** per inserire un `Forms2OleControl` di tipo **CommandButton**, impostato una didascalia amichevole e salvato il risultato. Il metodo scala a più controlli e si integra perfettamente in pipeline più ampie di **automazione Word**.

Pronto per la prossima sfida? Prova a sostituire il pulsante con un **CheckBox**, o collega una macro per reagire quando l'utente clicca il pulsante in un file `.docm`. Lo stesso schema si applica—basta cambiare l’enum e regolare la didascalia.

Se incontri difficoltà, ricontrolla la versione della libreria e i permessi della cartella di output. Sentiti libero di lasciare un commento qui sotto con domande o di condividere il tuo caso d'uso. Buona programmazione!

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo passo per aiutarti a padroneggiare funzionalità aggiuntive dell'API e a esplorare approcci alternativi di implementazione nei tuoi progetti.

- [Come creare campi modulo e aggiungere contenuto usando DocumentBuilder in Aspose.Words per Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Inserire immagine inline in un documento Word usando Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)
- [Creare forma di gruppo in un documento Word usando Aspose.Words per .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}