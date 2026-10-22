---
category: general
date: 2026-07-20
description: Crea un documento Word vuoto in Java usando Aspose.Words. Scopri come
  creare un gruppo, inserire una forma rettangolare e incorporare un'immagine nella
  forma.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to create group
- add image word document
- insert rectangle shape
- embed image in shape
language: it
lastmod: 2026-07-20
og_description: Crea un documento Word vuoto in Java con Aspose.Words. Questa guida
  mostra come creare un gruppo, inserire una forma rettangolare e incorporare un'immagine
  nella forma per file Word dinamici.
og_image_alt: Screenshot of a blank Word document containing a grouped shape with
  a rectangle and an embedded image
og_title: Crea un documento Word vuoto con forma raggruppata – Guida Java
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Create blank word document in Java using Aspose.Words. Learn how to
    create group, insert rectangle shape, and embed image in shape.
  headline: Create blank word document with grouped shape – Java guide
  type: TechArticle
- description: Create blank word document in Java using Aspose.Words. Learn how to
    create group, insert rectangle shape, and embed image in shape.
  name: Create blank word document with grouped shape – Java guide
  steps:
  - name: '`output.docx` appears in the project folder.'
    text: '`output.docx` appears in the project folder.'
  - name: Opening the file shows a single page with a grouped shape.
    text: Opening the file shows a single page with a grouped shape.
  - name: Inside the group, the rectangle is positioned at the top‑left, and the image
      sits directly below it.
    text: Inside the group, the rectangle is positioned at the top‑left, and the image
      sits directly below it.
  - name: Selecting the group in Word highlights both child objects, confirming they
      are truly grouped.
    text: Selecting the group in Word highlights both child objects, confirming they
      are truly grouped.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word Automation
title: Crea un documento Word vuoto con forma raggruppata – Guida Java
url: /it/java/images-shapes/create-blank-word-document-with-grouped-shape-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea documento Word vuoto con forma raggruppata – Guida Java

Ti sei mai chiesto come **creare un documento Word vuoto** che contenga già una forma raggruppata in modo elegante? Forse stai creando un modello di report, o ti serve un segnaposto per un logo e una didascalia. In ogni caso, il problema è comune: inizi con un file vuoto, poi devi aggiungere un gruppo, inserire un rettangolo all'interno e infine incorporare un'immagine—tutto in modo programmatico.

In questo tutorial percorreremo un esempio Java completo, pronto‑all‑uso, che fa esattamente questo. Imparerai **come creare un gruppo**, **inserire una forma rettangolare**, e **aggiungere un'immagine al documento Word** all'interno dello stesso gruppo. Alla fine avrai un file Word che sembra un modello rifinito, pronto per ulteriori personalizzazioni.

> **Cosa otterrai:** una classe Java completamente funzionale, spiegazioni passo‑passo, consigli per gestire i percorsi dei file e un'anteprima dell'output previsto. Nessuna documentazione esterna necessaria—tutto ciò che ti serve è qui.

---

## Crea documento Word vuoto – Panoramica passo‑passo

La prima cosa di cui abbiamo bisogno è un vero file Word vuoto. Aspose.Words rende questo banale: basta istanziare la classe `Document` con il suo costruttore predefinito. Questo ti fornisce una tela pulita, equivalente ad aprire Word e cliccare **Nuovo → Documento vuoto**.

```java
import com.aspose.words.*;

public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a blank Word document
        Document doc = new Document();               // <-- blank document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Perché iniziare con un documento vuoto?**  
> Un documento vuoto garantisce che nessuno stile o sezione nascosta interferisca con le forme che aggiungerai in seguito. Mantiene inoltre le dimensioni del file al minimo, utile quando generi decine di file in un lavoro batch.

---

## Come creare un gruppo e aggiungere forme

Una **forma di gruppo** è essenzialmente un contenitore che può contenere più forme figlie—pensala come una cartella per oggetti di disegno. Raggruppando, puoi spostare, ridimensionare o ruotare l'intero insieme con un unico comando.

```java
        // 2️⃣ Insert a group shape 200x200 points
        GroupShape group = builder.insertGroupShape(200.0, 200.0);
```

Il metodo `insertGroupShape` restituisce un oggetto `GroupShape` che useremo come genitore per il rettangolo e l'immagine. La dimensione è espressa in punti (1 punto = 1/72 di pollice), quindi 200 punti ti danno circa una casella di 2,78 × 2,78 pollici.

> **Consiglio professionale:** Se hai bisogno che il gruppo sia trasparente, imposta `group.setFillColor(Color.getWhite());` dopo la creazione.

Ora che il gruppo esiste, dobbiamo indicare al builder dove posizionare le forme successive. Il cursore del builder deve essere posizionato all'interno del primo paragrafo del gruppo.

```java
        // Move the cursor to the first paragraph of the group
        builder.moveTo(group.getFirstParagraph());
```

---

## Inserisci forma rettangolare all'interno del gruppo

Un rettangolo è spesso usato come segnaposto per testo o come indicatore visivo. Aggiungerlo come **prima figlia** del gruppo garantisce che si trovi dietro eventuali immagini successive.

```java
        // 3️⃣ Insert a rectangle (100x50 points) as the first child
        builder.insertShape(ShapeType.RECTANGLE, 100.0, 50.0);
```

Il rettangolo eredita il sistema di coordinate del gruppo, quindi la sua dimensione di 100 × 50 punti sarà centrata per impostazione predefinita. Puoi stilizzarlo ulteriormente—aggiungere un bordo, cambiare il colore di riempimento o applicare un'ombra—accedendo all'oggetto `Shape` restituito.

```java
        // Optional styling (commented out for brevity)
        // Shape rect = builder.getCurrentShape();
        // rect.setFillColor(Color.getLightGray());
        // rect.setStrokeColor(Color.getBlack());
```

---

## Aggiungi immagine al documento Word – incorporare immagine nella forma

Ora la parte divertente: **incorporare immagine nella forma**. Inseriremo un'immagine JPEG come seconda figlia dello stesso gruppo. Poiché il cursore è ancora all'interno del gruppo, l'immagine diventerà automaticamente un nodo figlio.

```java
        // 4️⃣ Insert an image (make sure the path is correct)
        builder.insertImage("sample.jpg");   // <-- replace with your image path
```

Se il file immagine non viene trovato, Aspose.Words genera una `FileNotFoundException`. Per evitarlo, posiziona `sample.jpg` nella directory di lavoro del progetto o usa un percorso assoluto.

> **E se avessi bisogno di un formato immagine diverso?**  
> Aspose.Words supporta PNG, BMP, GIF, TIFF e anche SVG. Basta cambiare l'estensione del file e la libreria gestirà la conversione.

---

## Salva il documento e visualizza il risultato

Infine, salviamo il documento in memoria su disco. Il `.docx` risultante conterrà una singola pagina con una forma raggruppata che contiene sia il rettangolo sia l'immagine.

```java
        // 5️⃣ Save the document to verify the output
        doc.save("output.docx");
    }
}
```

Quando apri `output.docx` in Microsoft Word, dovresti vedere un gruppo di 200 × 200 punti nell'angolo in alto a sinistra. All'interno del gruppo, un rettangolo grigio chiaro si trova in alto, e direttamente sotto di esso l'immagine specificata appare, perfettamente allineata.

![Grouped shape example](grouped-shape.png){:alt="Screenshot di un documento Word vuoto con una forma raggruppata contenente un rettangolo e un'immagine incorporata"}

---

## Varianti comuni e gestione dei casi limite

| Scenario | Cosa modificare | Perché è importante |
|----------|----------------|---------------------|
| **Dimensione gruppo diversa** | Regola i parametri di `insertGroupShape(width, height)` | Gruppi più grandi possono ospitare layout più complessi. |
| **Immagini multiple** | Chiama `builder.insertImage()` ripetutamente dopo aver spostato il cursore al paragrafo del gruppo ogni volta | Ogni chiamata aggiunge un nuovo figlio; puoi anche posizionarli usando `Shape.setLeft()` / `setTop()`. |
| **Percorsi immagine dinamici** | Usa `String.format("images/%s.jpg", imageName)` | Rende il codice riutilizzabile per l'elaborazione batch. |
| **Salvataggio come PDF** | Sostituisci `doc.save("output.pdf")` | Aspose.Words può convertire al volo, permettendoti di generare PDF direttamente. |
| **Rotazione del gruppo** | `group.setRotation(45);` | Utile per filigrane decorative o intestazioni stilizzate. |

---

## Output previsto e verifica

Dopo aver eseguito la classe:

1. `output.docx` appare nella cartella del progetto.  
2. Aprendo il file si vede una singola pagina con una forma raggruppata.  
3. All'interno del gruppo, il rettangolo è posizionato in alto‑a‑sinistra, e l'immagine si trova direttamente sotto di esso.  
4. Selezionando il gruppo in Word evidenzia entrambi gli oggetti figli, confermando che sono davvero raggruppati.

Se uno di questi passaggi fallisce, ricontrolla il percorso dell'immagine e assicurati che il JAR di Aspose.Words sia nel tuo classpath.

---

## Conclusione

Ora sai **come creare un documento Word vuoto** e arricchirlo con una forma raggruppata che contiene un rettangolo e un'immagine incorporata. Padroneggiando **come creare un gruppo**, **inserire una forma rettangolare**, e **aggiungere un'immagine al documento Word**, puoi costruire template Word sofisticati interamente tramite codice—senza necessità di modifiche manuali.

Pronto per la prossima sfida? Prova ad aggiungere caselle di testo all'interno dello stesso gruppo, o sperimenta con diversi stili di forma per adattarli al branding aziendale. Potresti persino generare un'intera libreria di report in cui ogni documento inizia con questo layout esatto.

Buon coding, e sentiti libero di condividere le tue varianti nei commenti qui sotto!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Crea documento Word Java – Aggiungi forma rettangolare con effetto ombra](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Come creare campi modulo e aggiungere contenuto usando DocumentBuilder in Aspose.Words per Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Come creare documenti PDF con Aspose.Words per Java | API di elaborazione documenti](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}