---
"description": "Scopri come salvare i documenti in formato OOXML con Aspose.Words per Java. Proteggi, ottimizza e personalizza i tuoi file senza sforzo."
"linktitle": "Salvataggio di documenti in formato OOXML"
"second_title": "API di elaborazione dei documenti Java Aspose.Words"
"title": "Salvataggio di documenti in formato OOXML in Aspose.Words per Java"
"url": "/it/java/document-loading-and-saving/saving-documents-as-ooxml-format/"
"weight": 20
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Salvataggio di documenti in formato OOXML in Aspose.Words per Java


## Introduzione al salvataggio di documenti in formato OOXML in Aspose.Words per Java

In questa guida, esploreremo come salvare documenti in formato OOXML utilizzando Aspose.Words per Java. OOXML (Office Open XML) è un formato di file utilizzato da Microsoft Word e altre applicazioni per ufficio. Illustreremo diverse opzioni e impostazioni per il salvataggio di documenti in formato OOXML.

## Prerequisiti

Prima di iniziare, assicurati di aver configurato la libreria Aspose.Words per Java nel tuo progetto.

## Salvataggio di un documento con crittografia tramite password

Puoi crittografare il tuo documento con una password mentre lo salvi in formato OOXML. Ecco come fare:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Carica il documento
Document doc = new Document("Document.docx");

// Crea OoxmlSaveOptions e imposta la password
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setPassword("password");

// Salva il documento con crittografia
doc.save("EncryptedDoc.docx", saveOptions);
```

## Impostazione della conformità OOXML

È possibile specificare il livello di conformità OOXML al momento del salvataggio del documento. Ad esempio, è possibile impostarlo su ISO 29500:2008 (Rigoroso). Ecco come fare:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.MsWordVersion;
import com.aspose.words.OoxmlCompliance;

// Carica il documento
Document doc = new Document("Document.docx");

// Ottimizza per Word 2016
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);

// Crea OoxmlSaveOptions e imposta il livello di conformità
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT);

// Salva il documento con le impostazioni di conformità
doc.save("ComplianceDoc.docx", saveOptions);
```

## Aggiornamento della proprietà dell'ora dell'ultimo salvataggio

Puoi scegliere di aggiornare la proprietà "Ultimo salvataggio" del documento al momento del salvataggio. Ecco come:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Carica il documento
Document doc = new Document("Document.docx");

// Crea OoxmlSaveOptions e abilita l'aggiornamento della proprietà Ultimo salvataggio
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setUpdateLastSavedTimeProperty(true);

// Salva il documento con la proprietà aggiornata
doc.save("UpdatedLastSavedTime.docx", saveOptions);
```

## Mantenere i personaggi di controllo legacy

Se il documento contiene caratteri di controllo legacy, puoi scegliere di mantenerli durante il salvataggio. Ecco come fare:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.SaveFormat;

// Carica un documento con caratteri di controllo legacy
Document doc = new Document("LegacyControlChars.doc");

// Crea OoxmlSaveOptions con il formato FLAT_OPC e abilita il mantenimento dei caratteri di controllo legacy
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setKeepLegacyControlChars(true);

// Salva il documento con i caratteri di controllo legacy
doc.save("LegacyControlCharsPreserved.docx", saveOptions);
```

## Impostazione del livello di compressione

È possibile regolare il livello di compressione durante il salvataggio del documento. Ad esempio, è possibile impostarlo su SUPER_VELOCE per una compressione minima. Ecco come fare:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.CompressionLevel;

// Carica il documento
Document doc = new Document("Document.docx");

// Crea OoxmlSaveOptions e imposta il livello di compressione
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST);

// Salva il documento con il livello di compressione specificato
doc.save("FastCompressionDoc.docx", saveOptions);
```

Queste sono alcune delle opzioni e impostazioni chiave che puoi utilizzare per salvare documenti in formato OOXML utilizzando Aspose.Words per Java. Sentiti libero di esplorare altre opzioni e personalizzare il processo di salvataggio dei documenti in base alle tue esigenze.

## Codice sorgente completo per salvare documenti in formato OOXML in Aspose.Words per Java

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

In questa guida completa, abbiamo esplorato come salvare documenti in formato OOXML utilizzando Aspose.Words per Java. Che tu abbia bisogno di crittografare i tuoi documenti con password, garantire la conformità a specifici standard OOXML, aggiornare le proprietà del documento, mantenere i caratteri di controllo legacy o regolare i livelli di compressione, Aspose.Words offre un set versatile di strumenti per soddisfare le tue esigenze.

## Domande frequenti

### Come posso rimuovere la protezione tramite password da un documento protetto da password?

Per rimuovere la protezione con password da un documento protetto da password, è possibile aprire il documento con la password corretta e salvarlo senza specificarne una nelle opzioni di salvataggio. In questo modo, il documento verrà salvato senza protezione con password.

### Posso impostare proprietà personalizzate quando salvo un documento in formato OOXML?

Sì, puoi impostare proprietà personalizzate per un documento prima di salvarlo in formato OOXML. Usa il `BuiltInDocumentProperties` E `CustomDocumentProperties` classi per impostare varie proprietà quali autore, titolo, parole chiave e proprietà personalizzate.

### Qual è il livello di compressione predefinito quando si salva un documento in formato OOXML?

Il livello di compressione predefinito quando si salva un documento in formato OOXML utilizzando Aspose.Words per Java è `NORMAL`È possibile modificare il livello di compressione su `SUPER_FAST` O `MAXIMUM` secondo necessità.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}