---
date: '2026-02-06'
description: Scopri come caricare HTML VML con Aspose.Words per Java, crittografare
  i file HTML Java, impostare l'URI base dell'HTML e configurare le opzioni di controllo
  HTML.
keywords:
- Aspose.Words for Java
- HTML document processing
- document encryption
title: Carica HTML VML usando Aspose.Words per Java – Guida completa
url: /it/java/document-operations/aspose-words-java-html-features-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Funzionalità HTML Complete con Aspose.Words per Java: Guida per Sviluppatori

## Introduzione

Navigare nel complesso mondo dell'elaborazione dei documenti può essere scoraggiante, soprattutto quando si gestiscono varie funzionalità HTML. Che tu stia trattando il supporto Vector Markup Language (VML), documenti crittografati o comportamenti specifici di importazione HTML, **Aspose.Words per Java** offre una soluzione solida. In questa guida imparerai **come caricare html vml** in modo efficiente e sicuro, coprendo anche attività correlate come **encrypt html java**, **set html base uri** e **configure html control**.

**Cosa Imparerai:**
- Come caricare documenti HTML con supporto VML.
- Tecniche per gestire HTML a pagina fissa e avvisi.
- Metodi per crittografare e caricare documenti HTML protetti da password.
- Utilizzo dei Base URI nelle Html Load Options.
- Importazione di elementi di input HTML come tag di documento strutturato o campi modulo.
- Ignorare gli elementi `<noscript>` durante il caricamento HTML.
- Configurazione delle modalità di importazione dei blocchi per controllare la conservazione della struttura HTML.
- Supporto alle regole `@font-face` per caratteri personalizzati.

## Risposte Rapide
- **Qual è il modo principale per abilitare VML durante il caricamento di HTML?** Imposta `loadOptions.setSupportVml(true)`.
- **Posso caricare file HTML protetti da password?** Sì, passa la password a `HtmlLoadOptions`.
- **Come risolvo i percorsi relativi delle immagini?** Usa `loadOptions.setBaseUri("your/base/uri")`.
- **È possibile importare `<select>` come campo modulo?** Imposta `loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag)`.
- **Quale classe cattura gli avvisi durante il caricamento?** Implementa `IWarningCallback` e assegnala a `loadOptions.setWarningCallback(...)`.

## Prerequisiti

Prima di iniziare a implementare le varie funzionalità HTML con Aspose.Words per Java, assicurati che l'ambiente sia configurato correttamente:

- **Librerie Richieste:** È necessaria la libreria Aspose.Words versione 25.3 o successiva.
- **Ambiente di Sviluppo:** Questa guida presuppone l'uso di Maven o Gradle per la gestione delle dipendenze.
- **Base di Conoscenza:** Una comprensione di base di Java e familiarità con i documenti HTML saranno utili.

## Configurazione di Aspose.Words

Per iniziare a lavorare con Aspose.Words, devi prima includerlo nel tuo progetto. Di seguito i passaggi per configurare la libreria usando Maven e Gradle:

### Maven

Aggiungi la seguente dipendenza al tuo file `pom.xml`:

```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### Gradle

Inserisci quanto segue nel tuo file `build.gradle`:

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

#### Acquisizione della Licenza

Aspose.Words richiede una licenza per la piena funzionalità. Puoi ottenere una prova gratuita, richiedere una licenza temporanea o acquistare una licenza permanente. Visita la [pagina di acquisto](https://purchase.aspose.com/buy) per maggiori dettagli.

Per inizializzare Aspose.Words nel tuo progetto Java, assicurati di aver impostato correttamente la licenza:

```java
import com.aspose.words.License;

public class InitializeAspose {
    public static void main(String[] args) throws Exception {
        License license = new License();
        license.setLicense("path/to/your/license/file.lic");
        
        System.out.println("Aspose.Words is ready to use!");
    }
}
```

## Guida all'Implementazione

Divideremo l'implementazione in sezioni in base alle funzionalità che desideriamo realizzare.

### Come caricare html vml con Aspose.Words

**Panoramica:**  
Il caricamento di un documento HTML con supporto VML consente una resa versatile di grafica vettoriale come grafici e forme. Questo è il passaggio fondamentale per la keyword principale **load html vml**.

#### Passo‑passo

1. **Imposta le Opzioni di Caricamento**

```java
import com.aspose.words.Document;
import com.aspose.words.HtmlLoadOptions;

HtmlLoadOptions loadOptions = new HtmlLoadOptions();
loadOptions.setSupportVml(true); // Enable VML support
```

2. **Carica il Documento**

```java
Document doc = new Document("path/to/VML conditional.htm", loadOptions);
```

3. **Verifica il Tipo di Immagine**

```java
import com.aspose.words.NodeType;
import com.aspose.words.Shape;

Shape imageShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
String expectedImageType = "JPG"; // Adjust based on actual logic

if (!imageShape.getImageData().getImageType().toString().equals(expectedImageType)) {
    throw new AssertionError("Unexpected image type loaded.");
}
```

### Caricamento HTML a Pagina Fissa e Gestione degli Avvisi

**Panoramica:**  
Il caricamento di documenti HTML a pagina fissa può generare avvisi che devono essere gestiti per un'elaborazione accurata.

#### Passo‑passo

1. **Definisci il Callback per gli Avvisi**

```java
import com.aspose.words.IWarningCallback;
import com.aspose.words.WarningInfo;
import java.util.ArrayList;

private static class ListDocumentWarnings implements IWarningCallback {
    private final ArrayList<WarningInfo> mWarnings = new ArrayList<>();

    public void warning(WarningInfo info) { 
        mWarnings.add(info); 
    }

    public ArrayList<WarningInfo> warnings() { return mWarnings; }
}
```

2. **Configura le Opzioni di Caricamento**

```java
HtmlLoadOptions loadOptions = new HtmlLoadOptions();
ListDocumentWarnings warningCallback = new ListDocumentWarnings();
loadOptions.setWarningCallback(warningCallback);
```

3. **Carica il Documento e Controlla gli Avvisi**

```java
Document doc = new Document("path/to/HtmlFixed.html", loadOptions);

if (warningCallback.warnings().size() != 1) {
    throw new AssertionError("Unexpected number of warnings.");
}
```

### Crittografia di Documenti HTML

**Panoramica:**  
Crittografare un documento HTML con una password garantisce un accesso sicuro, fondamentale per informazioni sensibili—questo affronta lo scenario **encrypt html java**.

#### Passo‑passo

1. **Prepara le Opzioni di Firma Digitale**

```java
import com.aspose.words.CertificateHolder;
import com.aspose.words.DigitalSignatureUtil;
import com.aspose.words.SignOptions;

CertificateHolder certificateHolder = CertificateHolder.create("path/to/morzal.pfx", "aw");
SignOptions signOptions = new SignOptions();
signOptions.setComments("Comment");
signOptions.setSignTime(new Date());
signOptions.setDecryptionPassword("docPassword");
```

2. **Firma e Crittografa il Documento**

```java
String inputFileName = "path/to/Encrypted.docx";
String outputFileName = "path/to/output/directory/HtmlLoadOptions.EncryptedHtml.html";

DigitalSignatureUtil.sign(inputFileName, outputFileName, certificateHolder, signOptions);
```

3. **Carica il Documento Crittografato**

```java
import com.aspose.words.Document;

HtmlLoadOptions loadOptions = new HtmlLoadOptions("docPassword");
Document doc = new Document(outputFileName, loadOptions);

if (!doc.getText().trim().equals("Test encrypted document.")) {
    throw new AssertionError("Unexpected document text.");
}
```

### Base URI per le Html Load Options

**Panoramica:**  
Specificare un **set html base uri** aiuta a risolvere gli URI relativi, soprattutto quando si trattano immagini o altre risorse collegate.

#### Passo‑passo

1. **Configura le Opzioni di Caricamento con Base URI**

```java
HtmlLoadOptions loadOptions = new HtmlLoadOptions(LoadFormat.HTML, "", "path/to/imageDir");
```

2. **Carica il Documento e Verifica l'Immagine**

```java
import com.aspose.words.Document;
import com.aspose.words.NodeType;

Document doc = new Document("path/to/Missing image.html", loadOptions);
Shape imageShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);

if (!imageShape.isImage()) {
    throw new AssertionError("Expected an image shape.");
}
```

### Importazione di HTML Select come Structured Document Tag

**Panoramica:**  
Per **configure html control** puoi importare gli elementi `<select>` come Structured Document Tags, ottenendo un controllo più fine sui campi modulo all'interno dei documenti Word.

#### Passo‑passo

1. **Imposta il Tipo di Controllo Preferito**

```java
import com.aspose.words.HtmlLoadOptions;
import com.aspose.words.ControlType;

HtmlLoadOptions loadOptions = new HtmlLoadOptions();
loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag);
```

2. **Carica il Documento e Verifica la Struttura**

```java
import com.aspose.words.Document;
import com.aspose.words.NodeType;
import com.aspose.words.StructuredDocumentTag;

Document doc = new Document("path/to/Input HTML with select element.html", loadOptions);
StructuredDocumentTag sdt = (StructuredDocumentTag)doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (!sdt.getTagName().equals("Select")) {
    throw new AssertionError("Expected a Structured Document Tag with tag name 'Select'.");
}
```

## Problemi Comuni e Soluzioni

| Problema | Motivo | Correzione |
|----------|--------|------------|
| Le grafiche VML non compaiono | Flag `supportVml` lasciato al valore predefinito (`false`) | Assicurati di chiamare `loadOptions.setSupportVml(true)` prima del caricamento. |
| Immagini mancanti dopo il caricamento | I percorsi relativi non possono essere risolti | Usa **set html base uri** (`loadOptions.setBaseUri(...)`) per puntare alla cartella corretta. |
| HTML protetto da password genera eccezione | Password non fornita | Passa la password a `new HtmlLoadOptions("yourPassword")`. |
| I controlli del modulo appaiono come testo semplice | `HtmlControlType` errato | Imposta `loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag)` o `FormField` secondo necessità. |
| Avvisi inattesi | Elementi HTML non gestiti | Implementa `IWarningCallback` per catturare e rivedere gli avvisi. |

## Domande Frequenti

**D: Posso caricare file HTML che contengono sia VML sia grafica SVG moderna?**  
R: Sì. Abilita VML con `setSupportVml(true)`; SVG è gestito automaticamente da Aspose.Words.

**D: Come crittografo un documento HTML senza utilizzare un certificato digitale?**  
R: Usa il costruttore di `HtmlLoadOptions` che accetta una password e salva il documento con `Document.save(..., SaveFormat.HTML)` dopo aver impostato la password.

**D: Cosa succede se il Base URI punta a una cartella inesistente?**  
R: Aspose.Words solleverà una `FileNotFoundException` per le risorse mancanti. Verifica il percorso prima del caricamento.

**D: È possibile cambiare il tipo di controllo predefinito per tutti gli elementi di modulo HTML?**  
R: Sì. Usa `loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag)` per applicarlo globalmente.

**D: I callback per gli avvisi sono thread‑safe?**  
R: L'implementazione del callback deve essere thread‑safe se prevedi di caricare documenti in modo concorrente. Usa collezioni sincronizzate o storage thread‑local.

---

**Ultimo Aggiornamento:** 2026-02-06  
**Testato Con:** Aspose.Words per Java 25.3  
**Autore:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}