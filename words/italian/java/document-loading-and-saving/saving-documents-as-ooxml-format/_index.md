---
date: 2026-01-09
description: Scopri come crittografare i file docx con password e modificare il livello
  di compressione durante il salvataggio dei documenti in formato OOXML utilizzando
  Aspose.Words per Java.
linktitle: Saving Documents as OOXML Format
second_title: Aspose.Words Java Document Processing API
title: Crittografa docx con password – Salvataggio OOXML con Aspose.Words Java
url: /it/java/document-loading-and-saving/saving-documents-as-ooxml-format/
weight: 20
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Cifra docx con password – Salvataggio OOXML con Aspose.Words Java

## Introduzione al salvataggio dei documenti in formato OOXML con Aspose.Words per Java

In questa guida imparerai come **cifrare docx con password** e salvare i documenti in formato OOXML usando Aspose.Words per Java. OOXML (Office Open XML) è il formato di file moderno utilizzato da Microsoft Word e molte altre applicazioni office. Esamineremo le opzioni più comuni — protezione con password, livelli di conformità, aggiornamento delle proprietà, gestione dei caratteri legacy e **come cambiare il livello di compressione** — così potrai personalizzare l'output secondo le tue esigenze.

## Risposte rapide
- **Come posso proteggere un file Word?** Usa `OoxmlSaveOptions.setPassword("yourPassword")` prima di salvare.  
- **Quale livello di conformità OOXML dovrei scegliere?** ISO 29500 2008 Strict per la massima compatibilità con le versioni moderne di Office.  
- **Posso mantenere i caratteri di controllo legacy?** Sì, abilita `setKeepLegacyControlChars(true)`.  
- **Come cambio il livello di compressione?** Imposta `setCompressionLevel(CompressionLevel.SUPER_FAST)` o `MAXIMUM` secondo necessità.  
- **Queste opzioni influenzano la dimensione del file?** Il livello di compressione e la gestione dei caratteri legacy possono modificare notevolmente la dimensione finale del .docx.

## Cos'è “cifrare docx con password”?
Cifrare un file DOCX significa che il documento viene salvato con crittografia AES‑256, richiedendo una password per aprirlo in Word o in qualsiasi visualizzatore compatibile. Questo è fondamentale per proteggere informazioni riservate quando i file vengono condivisi via email, archiviazione cloud o portali intranet.

## Perché utilizzare le opzioni di salvataggio OOXML?
- **Sicurezza:** La protezione con password impedisce l'accesso non autorizzato.  
- **Compatibilità:** Le impostazioni di conformità garantiscono che il file funzioni su diverse versioni di Word.  
- **Prestazioni:** Regolare la compressione può accelerare il salvataggio o ridurre la dimensione del file.  
- **Preservazione:** Mantenere i caratteri di controllo legacy conserva la fedeltà durante la conversione di documenti più vecchi.

## Prerequisiti
- Libreria Aspose.Words per Java aggiunta al tuo progetto (Maven/Gradle o JAR manuale).  
- Java 8 o superiore.  
- Un documento sorgente (`.docx` o `.doc`) che desideri elaborare.

## Salvataggio di un documento con crittografia password
Puoi cifrare il tuo documento con una password durante il salvataggio in formato OOXML. Ecco come fare:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and set the password
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setPassword("password");

// Save the document with encryption
doc.save("EncryptedDoc.docx", saveOptions);
```

> **Consiglio:** Scegli una password robusta e conservala in modo sicuro; la password non può essere recuperata dal file cifrato.

## Impostazione della conformità OOXML
Puoi specificare il livello di conformità OOXML durante il salvataggio del documento. Ad esempio, puoi impostarlo su ISO 29500:2008 (Strict). Ecco come:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.MsWordVersion;
import com.aspose.words.OoxmlCompliance;

// Load the document
Document doc = new Document("Document.docx");

// Optimize for Word 2016
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);

// Create OoxmlSaveOptions and set the compliance level
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT);

// Save the document with compliance setting
doc.save("ComplianceDoc.docx", saveOptions);
```

## Aggiornamento della proprietà “Last Saved Time”
Puoi scegliere di aggiornare la proprietà “Last Saved Time” del documento al momento del salvataggio. Ecco come:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and enable updating the Last Saved Time property
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setUpdateLastSavedTimeProperty(true);

// Save the document with the updated property
doc.save("UpdatedLastSavedTime.docx", saveOptions);
```

## Mantenimento dei caratteri di controllo legacy
Se il tuo documento contiene caratteri di controllo legacy, puoi scegliere di mantenerli durante il salvataggio. Ecco come:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.SaveFormat;

// Load a document with legacy control characters
Document doc = new Document("LegacyControlChars.doc");

// Create OoxmlSaveOptions with the FLAT_OPC format and enable keeping legacy control characters
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setKeepLegacyControlChars(true);

// Save the document with legacy control characters
doc.save("LegacyControlCharsPreserved.docx", saveOptions);
```

## Come cambiare il livello di compressione durante il salvataggio OOXML
Puoi regolare il livello di compressione durante il salvataggio del documento. Ad esempio, puoi impostarlo su `SUPER_FAST` per una compressione minima o `MAXIMUM` per la dimensione più piccola del file. Ecco come:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.CompressionLevel;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and set the compression level
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST);

// Save the document with the specified compression level
doc.save("FastCompressionDoc.docx", saveOptions);
```

Queste sono alcune delle opzioni e impostazioni chiave che puoi utilizzare quando salvi documenti in formato OOXML usando Aspose.Words per Java. Sentiti libero di esplorare altre opzioni e personalizzare il processo di salvataggio del documento secondo le necessità.

## Codice sorgente completo per il salvataggio dei documenti in formato OOXML con Aspose.Words per Java
```java
public void encryptDocxWithPassword() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setPassword("password"); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.EncryptDocxWithPassword.docx", saveOptions);
}
@Test
public void ooxmlComplianceIso29500_2008_Strict() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.OoxmlComplianceIso29500_2008_Strict.docx", saveOptions);
}
@Test
public void updateLastSavedTimeProperty() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setUpdateLastSavedTimeProperty(true); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.UpdateLastSavedTimeProperty.docx", saveOptions);
}
@Test
public void keepLegacyControlChars() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Legacy control character.doc");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setKeepLegacyControlChars(true); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.KeepLegacyControlChars.docx", saveOptions);
}
@Test
public void setCompressionLevel() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.SetCompressionLevel.docx", saveOptions);
}
```

## Conclusione
In questa guida completa, abbiamo esplorato come **cifrare docx con password** e salvare i documenti in formato OOXML usando Aspose.Words per Java. Che tu abbia bisogno di proteggere i tuoi file, garantire una rigorosa conformità OOXML, aggiornare le proprietà del documento, preservare i caratteri di controllo legacy, o **cambiare il livello di compressione**, Aspose.Words fornisce un set versatile di strumenti per soddisfare le tue esigenze.

## Domande frequenti
**D: Come rimuovo la protezione con password da un documento protetto da password?**  
R: Apri il documento con la password corretta, quindi salvalo senza specificare una password in `OoxmlSaveOptions`. Questo crea una copia non protetta.

**D: Posso impostare proprietà personalizzate quando salvo un documento in formato OOXML?**  
R: Sì. Usa `BuiltInDocumentProperties` e `CustomDocumentProperties` sull'oggetto `Document` prima di chiamare `save()`.

**D: Qual è il livello di compressione predefinito quando salvo un documento in formato OOXML?**  
R: Il valore predefinito è `CompressionLevel.NORMAL`. Puoi passare a `SUPER_FAST` per la velocità o a `MAXIMUM` per la dimensione più piccola del file.

**D: L'abilitazione di `keepLegacyControlChars` influenzerà la compatibilità con le versioni moderne di Word?**  
R: Word moderno può aprire file con caratteri di controllo legacy, ma alcune funzionalità più vecchie potrebbero essere visualizzate diversamente. Usa questa opzione solo quando è necessario preservare il contenuto originale esatto.

**D: È possibile combinare più opzioni di salvataggio (ad esempio, password + compressione) in una singola chiamata?**  
R: Assolutamente. Configura tutte le proprietà desiderate su un'unica istanza di `OoxmlSaveOptions` prima di passarla a `doc.save()`.

---

**Ultimo aggiornamento:** 2026-01-09  
**Testato con:** Aspose.Words for Java 24.12  
**Autore:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}