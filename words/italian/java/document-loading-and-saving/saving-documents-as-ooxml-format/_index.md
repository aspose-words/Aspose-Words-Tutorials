---
title: Salvataggio di documenti in formato OOXML in Aspose.Words per Java
linktitle: Salvataggio dei documenti in formato OOXML
second_title: API di elaborazione dei documenti Java Aspose.Words
description: Scopri come salvare i documenti in formato OOXML con Aspose.Words per Java. Proteggi, ottimizza e personalizza i tuoi file senza sforzo.
weight: 20
url: /it/java/document-loading-and-saving/saving-documents-as-ooxml-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Salvataggio di documenti in formato OOXML in Aspose.Words per Java


## Introduzione al salvataggio di documenti in formato OOXML in Aspose.Words per Java

In questa guida, esploreremo come salvare documenti in formato OOXML usando Aspose.Words per Java. OOXML (Office Open XML) è un formato di file usato da Microsoft Word e altre applicazioni per ufficio. Tratteremo varie opzioni e impostazioni per salvare documenti in formato OOXML.

## Prerequisiti

Prima di iniziare, assicurati di aver configurato la libreria Aspose.Words per Java nel tuo progetto.

## Salvataggio di un documento con crittografia tramite password

Puoi crittografare il tuo documento con una password mentre lo salvi in formato OOXML. Ecco come puoi farlo:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Carica il documento
Document doc = new Document("Document.docx");

// Crea OoxmlSaveOptions e imposta la password
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setPassword("password");

// Salvare il documento con crittografia
doc.save("EncryptedDoc.docx", saveOptions);
```

## Impostazione della conformità OOXML

Puoi specificare il livello di conformità OOXML quando salvi il documento. Ad esempio, puoi impostarlo su ISO 29500:2008 (Strict). Ecco come:

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

// Salvare il documento con le impostazioni di conformità
doc.save("ComplianceDoc.docx", saveOptions);
```

## Aggiornamento della proprietà dell'ultimo orario salvato

Puoi scegliere di aggiornare la proprietà "Ultimo orario salvato" del documento quando lo salvi. Ecco come:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Carica il documento
Document doc = new Document("Document.docx");

// Crea OoxmlSaveOptions e abilita l'aggiornamento della proprietà Ultimo salvataggio
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setUpdateLastSavedTimeProperty(true);

// Salvare il documento con la proprietà aggiornata
doc.save("UpdatedLastSavedTime.docx", saveOptions);
```

## Mantenere i personaggi di controllo legacy

Se il tuo documento contiene caratteri di controllo legacy, puoi scegliere di mantenerli durante il salvataggio. Ecco come:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.SaveFormat;

//Carica un documento con caratteri di controllo legacy
Document doc = new Document("LegacyControlChars.doc");

// Crea OoxmlSaveOptions con il formato FLAT_OPC e abilita il mantenimento dei caratteri di controllo legacy
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setKeepLegacyControlChars(true);

// Salva il documento con i caratteri di controllo legacy
doc.save("LegacyControlCharsPreserved.docx", saveOptions);
```

## Impostazione del livello di compressione

Puoi regolare il livello di compressione quando salvi il documento. Ad esempio, puoi impostarlo su SUPER_FAST per una compressione minima. Ecco come:

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

Queste sono alcune delle opzioni e impostazioni chiave che puoi usare quando salvi documenti in formato OOXML usando Aspose.Words per Java. Sentiti libero di esplorare altre opzioni e personalizzare il tuo processo di salvataggio documenti come necessario.

## Codice sorgente completo per salvare i documenti in formato OOXML in Aspose.Words per Java

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

In questa guida completa, abbiamo esplorato come salvare documenti in formato OOXML utilizzando Aspose.Words per Java. Che tu abbia bisogno di crittografare i tuoi documenti con password, garantire la conformità con specifici standard OOXML, aggiornare le proprietà del documento, preservare i caratteri di controllo legacy o regolare i livelli di compressione, Aspose.Words fornisce un set versatile di strumenti per soddisfare le tue esigenze.

## Domande frequenti

### Come faccio a rimuovere la protezione tramite password da un documento protetto da password?

Per rimuovere la protezione tramite password da un documento protetto da password, puoi aprire il documento con la password corretta e poi salvarlo senza specificare una password nelle opzioni di salvataggio. Questo salverà il documento senza protezione tramite password.

### Posso impostare proprietà personalizzate quando salvo un documento in formato OOXML?

 Sì, puoi impostare proprietà personalizzate per un documento prima di salvarlo in formato OOXML. Utilizza`BuiltInDocumentProperties` E`CustomDocumentProperties` classi per impostare varie proprietà quali autore, titolo, parole chiave e proprietà personalizzate.

### Qual è il livello di compressione predefinito quando si salva un documento in formato OOXML?

 Il livello di compressione predefinito quando si salva un documento in formato OOXML utilizzando Aspose.Words per Java è`NORMAL` Puoi modificare il livello di compressione in`SUPER_FAST` O`MAXIMUM` secondo necessità.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
