---
date: 2025-12-29
description: Scopri come crittografare i file docx con password utilizzando le opzioni
  di salvataggio di Aspose.Words per Java. Proteggi, ottimizza e personalizza i tuoi
  file OOXML senza sforzo.
linktitle: Saving Documents as OOXML Format
second_title: Aspose.Words Java Document Processing API
title: Come crittografare un DOCX con password usando Aspose.Words per Java
url: /it/java/document-loading-and-saving/saving-documents-as-ooxml-format/
weight: 20
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Come crittografare un DOCX con password usando Aspose.Words per Java

In questa guida scoprirai **come crittografare un docx con password** durante il salvataggio dei documenti in formato OOXML usando Aspose.Words per Java. Che tu stia proteggendo report riservati o bozze di contratti, i passaggi seguenti mostrano esattamente come applicare la protezione con password e affinare altre opzioni di salvataggio OOXML.

## Risposte rapide
- **Posso crittografare un file DOCX con una password?** Sì, usa `OoxmlSaveOptions.setPassword()` prima di salvare.  
- **Quale classe controlla le impostazioni di salvataggio OOXML?** `OoxmlSaveOptions` (parte di Aspose.Words).  
- **È necessaria una licenza per la protezione con password?** È richiesta una licenza valida di Aspose.Words per l'uso in produzione.  
- **Posso combinare la crittografia con le impostazioni di conformità?** Assolutamente – imposta sia `setPassword` che `setCompliance` sulla stessa istanza di `OoxmlSaveOptions`.  
- **Quali livelli di compressione sono disponibili?** `NORMAL`, `SUPER_FAST` e `MAXIMUM` tramite `CompressionLevel`.

## Che cosa significa “encrypt docx with password”?
Crittografare un file DOCX significa che il contenuto del file è memorizzato in forma crittata e può essere aperto solo fornendo la password corretta. Questo protegge le informazioni sensibili da accessi non autorizzati, consentendo comunque agli strumenti standard di Word di aprire il file una volta inserita la password.

## Perché usare le opzioni di salvataggio di Aspose.Words per la crittografia?
Aspose.Words offre un ricco insieme di **aspose words save options** che ti consentono di controllare non solo la crittografia, ma anche i livelli di conformità, la compressione e la gestione dei caratteri legacy, tutto dal codice Java. Questo elimina la necessità di post‑processing manuale o di strumenti di terze parti.

## Prerequisiti
- Java Development Kit (JDK 8 o superiore)  
- Libreria Aspose.Words per Java aggiunta al progetto (Maven/Gradle o JAR)  
- Una licenza valida di Aspose.Words per la produzione (opzionale per la valutazione)

## Salvataggio di un documento con crittografia password

Puoi crittografare il tuo documento con una password durante il salvataggio in formato OOXML. Ecco come fare:

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

## Impostazione della conformità OOXML

Puoi specificare il livello di conformità OOXML al momento del salvataggio del documento. Ad esempio, puoi impostarlo su ISO 29500:2008 (Strict). Ecco come:

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

## Conservazione dei caratteri di controllo legacy

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

## Impostazione del livello di compressione

Puoi regolare il livello di compressione al momento del salvataggio del documento. Ad esempio, puoi impostarlo su **SUPER_FAST** per una compressione minima. Ecco come:

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

Queste sono alcune delle opzioni chiave che puoi utilizzare quando salvi documenti in formato OOXML usando Aspose.Words per Java. Sentiti libero di esplorare altre opzioni e personalizzare il processo di salvataggio del documento secondo le tue esigenze.

## Codice sorgente completo per il salvataggio di documenti in formato OOXML in Aspose.Words per Java

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

In questa guida completa, abbiamo esplorato come **encrypt docx with password** e affinare una serie di opzioni di salvataggio OOXML usando Aspose.Words per Java. Che tu debba proteggere contenuti riservati, soddisfare rigorose normative ISO, preservare caratteri legacy o controllare la compressione, la libreria ti offre un controllo granulare tramite la stessa API `OoxmlSaveOptions`.

## Domande frequenti

**D: Come rimuovo la protezione con password da un documento protetto?**  
R: Apri il documento con la password corretta, quindi salvalo nuovamente senza chiamare `setPassword`. Il nuovo file sarà non protetto.

**D: Posso impostare proprietà personalizzate quando salvo un documento in formato OOXML?**  
R: Sì. Usa `BuiltInDocumentProperties` o `CustomDocumentProperties` sull'oggetto `Document` prima di invocare `save`.

**D: Qual è il livello di compressione predefinito quando salvo un documento in formato OOXML?**  
R: Il valore predefinito è `NORMAL`. Puoi passare a `SUPER_FAST` per velocità o a `MAXIMUM` per una dimensione file più piccola.

**D: Le aspose words save options funzionano con versioni più vecchie di Word?**  
R: Sì. Regolando `MsWordVersion` e le impostazioni di conformità, puoi mirare a Word 2007‑2019 e garantire la compatibilità.

**D: È possibile combinare più opzioni di salvataggio in un'unica operazione?**  
R: Assolutamente. Crea un'istanza di `OoxmlSaveOptions`, imposta tutte le proprietà desiderate (password, conformità, compressione, ecc.) e passala a `doc.save()`.

---

**Ultimo aggiornamento:** 2025-12-29  
**Testato con:** Aspose.Words per Java 24.12  
**Autore:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}