---
"description": "Impara a usare efficacemente note a piè di pagina e note di chiusura in Aspose.Words per Java. Migliora le tue competenze di formattazione dei documenti oggi stesso!"
"linktitle": "Utilizzo di note a piè di pagina e note di chiusura"
"second_title": "API di elaborazione dei documenti Java Aspose.Words"
"title": "Utilizzo di note a piè di pagina e note di chiusura in Aspose.Words per Java"
"url": "/it/java/using-document-elements/using-footnotes-and-endnotes/"
"weight": 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Utilizzo di note a piè di pagina e note di chiusura in Aspose.Words per Java


In questo tutorial, ti guideremo attraverso l'utilizzo di note a piè di pagina e di chiusura in Aspose.Words per Java. Note a piè di pagina e di chiusura sono elementi essenziali nella formattazione dei documenti, spesso utilizzati per citazioni, riferimenti e informazioni aggiuntive. Aspose.Words per Java offre funzionalità avanzate per gestire note a piè di pagina e di chiusura in modo fluido.

## 1. Introduzione alle note a piè di pagina e alle note di chiusura

Le note a piè di pagina e le note di chiusura sono annotazioni che forniscono informazioni supplementari o citazioni all'interno di un documento. Le note a piè di pagina compaiono in fondo alla pagina, mentre le note di chiusura sono raccolte alla fine di una sezione o del documento. Sono comunemente utilizzate in articoli accademici, relazioni e documenti legali per fare riferimento alle fonti o chiarire il contenuto.

## 2. Impostazione dell'ambiente

Prima di addentrarci nell'utilizzo di note a piè di pagina e di chiusura, è necessario configurare l'ambiente di sviluppo. Assicurarsi di aver installato e configurato l'API Aspose.Words per Java nel progetto.

## 3. Aggiungere note a piè di pagina al documento

Per aggiungere note a piè di pagina al documento, segui questi passaggi:
```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";

public void getFootnoteOptions(){
    Document doc = new Document(dataDir + "Document.docx");
    
    // Specificare il numero di colonne con cui viene formattata l'area delle note a piè di pagina.
    doc.getFootnoteOptions().setColumns(3);
    doc.save("Your Directory Path" + "WorkingWithFootnotes.SetFootNoteColumns.docx");
}
```

## 4. Modifica delle opzioni delle note a piè di pagina

È possibile modificare le opzioni delle note a piè di pagina per personalizzarne l'aspetto e il comportamento. Ecco come:
```java
@Test
public void setFootnoteAndEndNotePosition() throws Exception {
    Document doc = new Document(dataDir + "Document.docx");
    
    doc.getFootnoteOptions().setPosition(FootnotePosition.BENEATH_TEXT);
    doc.getEndnoteOptions().setPosition(EndnotePosition.END_OF_SECTION);
    
    doc.save(outPath + "WorkingWithFootnotes.SetFootnoteAndEndNotePosition.docx");
}
```

## 5. Aggiungere note di chiusura al documento

Aggiungere note di chiusura al documento è semplice. Ecco un esempio:
```java
@Test
public void setEndnoteOptions() throws Exception {
    Document doc = new Document(dataDir + "Document.docx");
    DocumentBuilder builder = new DocumentBuilder(doc);
    
    builder.write("Some text");
    builder.insertFootnote(FootnoteType.ENDNOTE, "Footnote text.");
    
    EndnoteOptions option = doc.getEndnoteOptions();
    option.setRestartRule(FootnoteNumberingRule.RESTART_PAGE);
    option.setPosition(EndnotePosition.END_OF_SECTION);
    
    doc.save(outPath + "WorkingWithFootnotes.SetEndnoteOptions.docx");
}
```

## 6. Personalizzazione delle impostazioni di Endnote

È possibile personalizzare ulteriormente le impostazioni delle note di chiusura per adattarle alle esigenze del documento.

## Codice sorgente completo
```java
	string dataDir = "Your Document Directory";
	string outPath = "Your Output Directory";
	public void getFootnoteOptions(){
        Document doc = new Document(dataDir + "Document.docx");
        // Specificare il numero di colonne con cui viene formattata l'area delle note a piè di pagina.
        doc.getFootnoteOptions().setColumns(3);
        doc.save("Your Directory Path" + "WorkingWithFootnotes.SetFootNoteColumns.docx");
    }
    @Test
    public void setFootnoteAndEndNotePosition() throws Exception
    {
        Document doc = new Document(dataDir + "Document.docx");
        doc.getFootnoteOptions().setPosition(FootnotePosition.BENEATH_TEXT);
        doc.getEndnoteOptions().setPosition(EndnotePosition.END_OF_SECTION);
        doc.save(outPath + "WorkingWithFootnotes.SetFootnoteAndEndNotePosition.docx");
    }
    @Test
    public void setEndnoteOptions() throws Exception
    {
        Document doc = new Document(dataDir + "Document.docx");
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.write("Some text");
        builder.insertFootnote(FootnoteType.ENDNOTE, "Footnote text.");
        EndnoteOptions option = doc.getEndnoteOptions();
        option.setRestartRule(FootnoteNumberingRule.RESTART_PAGE);
        option.setPosition(EndnotePosition.END_OF_SECTION);
        doc.save(outPath + "WorkingWithFootnotes.SetEndnoteOptions.docx");
	}
```

## 7. Conclusion

In questo tutorial abbiamo esplorato come utilizzare note a piè di pagina e note di chiusura in Aspose.Words per Java. Queste funzionalità sono preziose per creare documenti ben strutturati con citazioni e riferimenti appropriati.

Ora che hai imparato a usare le note a piè di pagina e le note di chiusura, puoi migliorare la formattazione del tuo documento e rendere i tuoi contenuti più professionali.

### Domande frequenti

### 1. Qual è la differenza tra note a piè di pagina e note di chiusura?
Le note a piè di pagina compaiono in fondo alla pagina, mentre le note di chiusura sono raccolte alla fine di una sezione o del documento.

### 2. Come posso modificare la posizione delle note a piè di pagina o delle note di chiusura?
Puoi usare il `setPosition` Metodo per modificare la posizione delle note a piè di pagina o delle note di chiusura.

### 3. Posso personalizzare la formattazione delle note a piè di pagina e delle note di chiusura?
Sì, puoi personalizzare la formattazione delle note a piè di pagina e delle note di chiusura utilizzando Aspose.Words per Java.

### 4. Le note a piè di pagina e le note di chiusura sono importanti nella formattazione del documento?
Sì, le note a piè di pagina e le note finali sono essenziali per fornire riferimenti e informazioni aggiuntive nei documenti.

Sentiti libero di esplorare altre funzionalità di Aspose.Words per Java e migliorare le tue capacità di creazione di documenti. Buona programmazione!


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}