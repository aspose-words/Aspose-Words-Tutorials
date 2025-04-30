---
"description": "Impara a usare oggetti OLE e controlli ActiveX in Aspose.Words per Java. Crea documenti interattivi con facilità. Inizia subito!"
"linktitle": "Utilizzo di oggetti OLE e controlli ActiveX"
"second_title": "API di elaborazione dei documenti Java Aspose.Words"
"title": "Utilizzo di oggetti OLE e controlli ActiveX in Aspose.Words per Java"
"url": "/it/java/using-document-elements/using-ole-objects-and-activex/"
"weight": 21
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Utilizzo di oggetti OLE e controlli ActiveX in Aspose.Words per Java

In questo tutorial, esploreremo come utilizzare oggetti OLE (Object Linking and Embedding) e controlli ActiveX in Aspose.Words per Java. Gli oggetti OLE e i controlli ActiveX sono strumenti potenti che consentono di migliorare i documenti incorporando o collegando contenuti esterni, come fogli di calcolo, file multimediali o controlli interattivi. Seguiteci mentre analizziamo gli esempi di codice e impariamo a utilizzare queste funzionalità in modo efficace.

### Prerequisiti

Prima di iniziare, assicurati di avere i seguenti prerequisiti:

1. Aspose.Words per Java: assicurati di aver installato la libreria Aspose.Words nel tuo progetto Java. Puoi scaricarla da [Qui](https://releases.aspose.com/words/java/).

2. Ambiente di sviluppo Java: dovresti avere un ambiente di sviluppo Java funzionante installato sul tuo sistema.

### Inserimento di un oggetto OLE

Iniziamo inserendo un oggetto OLE in un documento Word. Creeremo un semplice documento Word e poi inseriremo un oggetto OLE che rappresenta una pagina web.

```java
string outPath = "Your Output Directory";
public void insertOleObject() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.insertOleObject("http://www.aspose.com", "htmlfile", true, true, null);
    doc.save("Your Directory Path" + "WorkingWithOleObjectsAndActiveX.InsertOleObject.docx");
}
```

In questo codice, creiamo un nuovo documento e inseriamo un oggetto OLE che visualizza il sito web di Aspose. È possibile sostituire l'URL con il contenuto desiderato.

### Inserimento di un oggetto OLE con OlePackage

Ora, esploriamo come inserire un oggetto OLE utilizzando un OlePackage. Questo permette di incorporare file esterni come oggetti OLE nel documento.

```java
@Test
public void insertOleObjectWithOlePackage() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    byte[] bs = FileUtils.readFileToByteArray(new File("Your Directory Path" + "Zip file.zip"));
    try (ByteArrayInputStream stream = new ByteArrayInputStream(bs))
    {
        Shape shape = builder.insertOleObject(stream, "Package", true, null);
        OlePackage olePackage = shape.getOleFormat().getOlePackage();
        olePackage.setFileName("filename.zip");
        olePackage.setDisplayName("displayname.zip");
        doc.save(outPath + "WorkingWithOleObjectsAndActiveX.InsertOleObjectWithOlePackage.docx");
    }
}
```

In questo esempio inseriamo un oggetto OLE utilizzando un OlePackage, consentendo di includere file esterni come oggetti incorporati.

### Inserimento di un oggetto OLE come icona

Ora vediamo come inserire un oggetto OLE come icona. Questo è utile quando si desidera visualizzare un'icona che rappresenti un file incorporato.

```java
@Test
public void insertOleObjectAsIcon() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.insertOleObjectAsIcon("Your Directory Path" + "Presentation.pptx", false, getImagesDir() + "Logo icon.ico", "My embedded file");
    doc.save(outPath + "WorkingWithOleObjectsAndActiveX.InsertOleObjectAsIcon.docx");
}
```

In questo codice inseriamo un oggetto OLE come icona, fornendo una rappresentazione visivamente più accattivante del contenuto incorporato.

### Lettura delle proprietà del controllo ActiveX

Ora concentriamoci sui controlli ActiveX. Impareremo a leggere le proprietà dei controlli ActiveX all'interno di un documento Word.

```java
@Test
public void readActiveXControlProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "ActiveX controls.docx");
    String properties = "";
    for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true))
    {
        if (shape.getOleFormat() == null) break;
        OleControl oleControl = shape.getOleFormat().getOleControl();
        if (oleControl.isForms2OleControl())
        {
            Forms2OleControl checkBox = (Forms2OleControl) oleControl;
            properties = properties + "\nCaption: " + checkBox.getCaption();
            properties = properties + "\nValue: " + checkBox.getValue();
            properties = properties + "\nEnabled: " + checkBox.getEnabled();
            properties = properties + "\nType: " + checkBox.getType();
            if (checkBox.getChildNodes() != null)
            {
                properties = properties + "\nChildNodes: " + checkBox.getChildNodes();
            }
            properties += "\n";
        }
    }
    properties = properties + "\nTotal ActiveX Controls found: " + doc.getChildNodes(NodeType.SHAPE, true).getCount();
    System.out.println("\n" + properties);
}
```

In questo codice, eseguiamo un'iterazione sulle forme in un documento Word, identifichiamo i controlli ActiveX e ne recuperiamo le proprietà.

### Conclusione

Congratulazioni! Hai imparato a lavorare con oggetti OLE e controlli ActiveX in Aspose.Words per Java. Queste funzionalità aprono un mondo di possibilità per la creazione di documenti dinamici e interattivi.

### Domande frequenti

### Qual è lo scopo degli oggetti OLE in un documento Word? 
   - Gli oggetti OLE consentono di incorporare o collegare contenuti esterni, come file o pagine Web, all'interno di un documento Word.

### Posso personalizzare l'aspetto degli oggetti OLE nel mio documento? 
   - Sì, è possibile personalizzare l'aspetto degli oggetti OLE, comprese le impostazioni delle icone e dei nomi dei file.

### Cosa sono i controlli ActiveX e come possono migliorare i miei documenti? 
   - controlli ActiveX sono elementi interattivi che possono aggiungere funzionalità ai documenti Word, ad esempio controlli di modulo o lettori multimediali.

### Aspose.Words per Java è adatto all'automazione dei documenti a livello aziendale? 
   - Sì, Aspose.Words per Java è una potente libreria per automatizzare la generazione e la manipolazione di documenti nelle applicazioni Java.

### Dove posso accedere ad Aspose.Words per Java? 
   - Puoi scaricare Aspose.Words per Java da [Qui](https://releases.aspose.com/words/java/).

Inizia subito a usare Aspose.Words per Java e scopri tutte le potenzialità dell'automazione e della personalizzazione dei documenti!



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}