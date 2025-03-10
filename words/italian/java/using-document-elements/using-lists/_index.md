---
title: Utilizzo di elenchi in Aspose.Words per Java
linktitle: Utilizzo degli elenchi
second_title: API di elaborazione dei documenti Java Aspose.Words
description: Impara a usare gli elenchi in Aspose.Words per Java con questo tutorial passo dopo passo. Organizza e formatta i tuoi documenti in modo efficace.
weight: 18
url: /it/java/using-document-elements/using-lists/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Utilizzo di elenchi in Aspose.Words per Java


In questo tutorial completo, esploreremo come usare efficacemente gli elenchi in Aspose.Words per Java, una potente API per lavorare con i documenti Microsoft Word a livello di programmazione. Gli elenchi sono essenziali per strutturare e organizzare i contenuti nei tuoi documenti. Tratteremo due aspetti chiave del lavoro con gli elenchi: il riavvio degli elenchi in ogni sezione e la specifica dei livelli degli elenchi. Immergiamoci!

## Introduzione ad Aspose.Words per Java

Prima di iniziare a lavorare con gli elenchi, prendiamo confidenza con Aspose.Words per Java. Questa API fornisce agli sviluppatori gli strumenti per creare, modificare e manipolare documenti Word in un ambiente Java. È una soluzione versatile per attività che vanno dalla semplice generazione di documenti alla formattazione complessa e alla gestione dei contenuti.

### Impostazione dell'ambiente

 Per iniziare, assicurati di avere Aspose.Words for Java installato e configurato nel tuo ambiente di sviluppo. Puoi scaricarlo[Qui](https://releases.aspose.com/words/java/). 

## Riavvio degli elenchi in ogni sezione

In molti scenari, potresti dover riavviare gli elenchi in ogni sezione del tuo documento. Questo può essere utile per creare documenti strutturati con più sezioni, come report, manuali o documenti accademici.

Ecco una guida passo passo su come ottenere questo risultato utilizzando Aspose.Words per Java:

### Inizializza il tuo documento: 
Iniziamo creando un nuovo oggetto documento.

```java
Document doc = new Document();
```

### Aggiungi un elenco numerato: 
Aggiungi un elenco numerato al tuo documento. Useremo lo stile di numerazione predefinito.

```java
doc.getLists().add(ListTemplate.NUMBER_DEFAULT);
```

### Configurare le impostazioni dell'elenco: 
\Abilita l'avvio dell'elenco a ogni sezione.

```java
List list = doc.getLists().get(0);
list.isRestartAtEachSection(true);
```

### Impostazione di DocumentBuilder: 
Crea un DocumentBuilder per aggiungere contenuti al tuo documento.

```java
DocumentBuilder builder = new DocumentBuilder(doc);
builder.getListFormat().setList(list);
```

### Aggiungi elementi all'elenco: 
Utilizza un loop per aggiungere elementi di elenco al tuo documento. Inseriremo un'interruzione di sezione dopo il quindicesimo elemento.

```java
for (int i = 1; i < 45; i++) {
    builder.writeln(MessageFormat.format("List Item {0}", i));
    if (i == 15)
        builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
}
```

### Salva il tuo documento: 
Salvare il documento con le opzioni desiderate.

```java
OoxmlSaveOptions options = new OoxmlSaveOptions();
options.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL);
doc.save(outPath + "RestartListAtEachSection.docx", options);
```

Seguendo questi passaggi, puoi creare documenti con elenchi che ricominciano da ogni sezione, mantenendo una struttura dei contenuti chiara e organizzata.

## Specificazione dei livelli di elenco

Aspose.Words per Java consente di specificare livelli di elenco, il che è particolarmente utile quando sono necessari formati di elenco diversi all'interno del documento. Esploriamo come fare:

### Inizializza il tuo documento: 
Crea un nuovo oggetto documento.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Crea un elenco numerato: 
Applicare un modello di elenco numerato da Microsoft Word.

```java
builder.getListFormat().setList(doc.getLists().add(ListTemplate.NUMBER_ARABIC_DOT));
```

### Specificare i livelli dell'elenco: 
Scorrere i diversi livelli dell'elenco e aggiungere contenuti.

```java
for (int i = 0; i < 9; i++) {
    builder.getListFormat().setListLevelNumber(i);
    builder.writeln("Level " + i);
}
```

### Crea un elenco puntato: 
Ora creiamo un elenco puntato.

```java
builder.getListFormat().setList(doc.getLists().add(ListTemplate.BULLET_DIAMONDS));
```

### Specificare i livelli degli elenchi puntati: 
Simile all'elenco numerato, specifica i livelli e aggiungi il contenuto.

```java
for (int i = 0; i < 9; i++) {
    builder.getListFormat().setListLevelNumber(i);
    builder.writeln("Level " + i);
}
```

### Formattazione dell'elenco delle fermate: 
Per interrompere la formattazione dell'elenco, impostare l'elenco su null.

```java
builder.getListFormat().setList(null);
```

### Salva il tuo documento: 
Salvare il documento.

```java
builder.getDocument().save(outPath + "SpecifyListLevel.docx");
```

Seguendo questi passaggi, puoi creare documenti con livelli di elenco personalizzati, che ti consentono di controllare la formattazione degli elenchi nei tuoi documenti.

## Codice sorgente completo
```java
	string outPath = "Your Output Directory";
 public void restartListAtEachSection() throws Exception
    {
        Document doc = new Document();
        doc.getLists().add(ListTemplate.NUMBER_DEFAULT);
        List list = doc.getLists().get(0);
        list.isRestartAtEachSection(true);
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.getListFormat().setList(list);
        for (int i = 1; i < 45; i++)
        {
            builder.writeln(MessageFormat.format("List Item {0}", i));
            if (i == 15)
                builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
        }
        // IsRestartAtEachSection verrà scritto solo se la conformità è superiore a OoxmlComplianceCore.Ecma376.
        OoxmlSaveOptions options = new OoxmlSaveOptions(); { options.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL); }
        doc.save(outPath + "WorkingWithList.RestartListAtEachSection.docx", options);
    }
    @Test
    public void specifyListLevel() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Crea un elenco numerato basato su uno dei modelli di elenco di Microsoft Word
        // applicarlo al paragrafo corrente del generatore di documenti.
        builder.getListFormat().setList(doc.getLists().add(ListTemplate.NUMBER_ARABIC_DOT));
        // Ci sono nove livelli in questa lista, proviamoli tutti.
        for (int i = 0; i < 9; i++)
        {
            builder.getListFormat().setListLevelNumber(i);
            builder.writeln("Level " + i);
        }
        // Crea un elenco puntato basato su uno dei modelli di elenco di Microsoft Word
        // applicarlo al paragrafo corrente del generatore di documenti.
        builder.getListFormat().setList(doc.getLists().add(ListTemplate.BULLET_DIAMONDS));
        for (int i = 0; i < 9; i++)
        {
            builder.getListFormat().setListLevelNumber(i);
            builder.writeln("Level " + i);
        }
        // Questo è un modo per interrompere la formattazione dell'elenco.
        builder.getListFormat().setList(null);
        builder.getDocument().save(outPath + "WorkingWithList.SpecifyListLevel.docx");
    }
    @Test
    public void restartListNumber() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Crea un elenco basato su un modello.
        List list1 = doc.getLists().add(ListTemplate.NUMBER_ARABIC_PARENTHESIS);
        list1.getListLevels().get(0).getFont().setColor(Color.RED);
        list1.getListLevels().get(0).setAlignment(ListLevelAlignment.RIGHT);
        builder.writeln("List 1 starts below:");
        builder.getListFormat().setList(list1);
        builder.writeln("Item 1");
        builder.writeln("Item 2");
        builder.getListFormat().removeNumbers();
        // Per riutilizzare il primo elenco, dobbiamo riavviare la numerazione creando una copia della formattazione dell'elenco originale.
        List list2 = doc.getLists().addCopy(list1);
        // Possiamo modificare il nuovo elenco in qualsiasi modo, anche impostando un nuovo numero di partenza.
        list2.getListLevels().get(0).setStartAt(10);
        builder.writeln("List 2 starts below:");
        builder.getListFormat().setList(list2);
        builder.writeln("Item 1");
        builder.writeln("Item 2");
        builder.getListFormat().removeNumbers();
        builder.getDocument().save(outPath + "WorkingWithList.RestartListNumber.docx");
	}
```

## Conclusione

Congratulazioni! Hai imparato a lavorare con gli elenchi in Aspose.Words per Java in modo efficace. Gli elenchi sono essenziali per organizzare e presentare il contenuto nei tuoi documenti. Sia che tu debba riavviare gli elenchi a ogni sezione o specificare i livelli di elenco, Aspose.Words per Java fornisce gli strumenti necessari per creare documenti dall'aspetto professionale.

Ora puoi usare con sicurezza queste funzionalità per migliorare le tue attività di generazione e formattazione dei documenti. Se hai domande o hai bisogno di ulteriore assistenza, non esitare a contattare il[Forum della comunità Aspose](https://forum.aspose.com/) per supporto.

## Domande frequenti

### Come faccio a installare Aspose.Words per Java?
 Puoi scaricare Aspose.Words per Java da[Qui](https://releases.aspose.com/words/java/) e seguire le istruzioni di installazione riportate nella documentazione.

### Posso personalizzare il formato di numerazione degli elenchi?
Sì, Aspose.Words per Java fornisce ampie opzioni per personalizzare i formati di numerazione degli elenchi. Puoi fare riferimento alla documentazione API per i dettagli.

### Aspose.Words per Java è compatibile con gli ultimi standard dei documenti Word?
Sì, è possibile configurare Aspose.Words per Java in modo che sia conforme a vari standard dei documenti Word, tra cui ISO 29500.

### Posso generare documenti complessi con tabelle e immagini utilizzando Aspose.Words per Java?
Assolutamente! Aspose.Words per Java supporta la formattazione avanzata dei documenti, tra cui tabelle, immagini e altro. Controlla la documentazione per gli esempi.

### Dove posso ottenere una licenza temporanea per Aspose.Words per Java?
Puoi ottenere una licenza temporanea[Qui](https://purchase.aspose.com/temporary-license/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
