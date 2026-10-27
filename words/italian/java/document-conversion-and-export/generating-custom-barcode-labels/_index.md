---
date: 2026-10-23
description: Scopri come creare etichette QR code Java con Aspose.Words. Questa guida
  passo‑passo ti mostra come incorporare barcode nei documenti Word e personalizzare
  dimensioni, colori e formato.
keywords:
- create qr code java
- how to create barcode label
- add barcode to word document
- embed barcode in word
lastmod: 2026-10-23
linktitle: Generazione di etichette barcode personalizzate
og_description: Scopri come creare etichette QR code Java con Aspose.Words. Questa
  guida spiega l'incorporamento di barcode, il controllo delle dimensioni e la personalizzazione
  dei colori nei documenti Word.
og_image_alt: 'Developer guide: generate custom QR code labels in Java with Aspose.Words'
og_title: Come creare etichette QR code Java con Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Learn how to create QR code Java labels with Aspose.Words. This step‑by‑step
    guide shows you how to embed barcodes in Word documents and customize size, colors,
    and format.
  headline: How to create QR code Java labels using Aspose.Words
  type: TechArticle
- description: Learn how to create QR code Java labels with Aspose.Words. This step‑by‑step
    guide shows you how to embed barcodes in Word documents and customize size, colors,
    and format.
  name: How to create QR code Java labels using Aspose.Words
  steps:
  - name: '**Document initialization** – Creates a fresh `Document` (or you could
      load an existing template).'
    text: '**Document initialization** – Creates a fresh `Document` (or you could
      load an existing template).'
  - name: '**Barcode parameters** – Defines the barcode type (`QR`), the value to
      encode, and the foreground/background colors.'
    text: '**Barcode parameters** – Defines the barcode type (`QR`), the value to
      encode, and the foreground/background colors.'
  - name: '**Image insertion** – `builder.insertImage` places the generated barcode
      at the desired size (200 × 200 pixels). This is the core of **how to embed barcode
      in Word**.'
    text: '**Image insertion** – `builder.insertImage` places the generated barcode
      at the desired size (200 × 200 pixels). This is the core of **how to embed barcode
      in Word**.'
  - name: '**Saving** – The final document, `CustomBarcodeLabels.docx`, contains the
      embedded barcode ready for printing or distribution.'
    text: '**Saving** – The final document, `CustomBarcodeLabels.docx`, contains the
      embedded barcode ready for printing or distribution.'
  type: HowTo
- questions:
  - answer: Yes, but it will have evaluation limitations. Obtain a [temporary license](https://purchase.aspose.com/temporary-license/)
      for full functionality.
    question: Can I use Aspose.Words for Java without a license?
  - answer: Aspose.BarCode supports QR, Code 128, EAN‑13, DataMatrix, PDF417, and
      many other formats—over 20 symbologies in total. See the [documentation](https://reference.aspose.com/words/java/)
      for the complete list.
    question: What types of barcodes can I generate?
  - answer: Adjust the width and height arguments in `builder.insertImage`, or calculate
      exact Word twips using `twipsToPixels` for pixel‑perfect control.
    question: How can I change the barcode size?
  - answer: Yes, you can customize the text font through the `CodeTextParameters`
      property of the `BarcodeGenerator`.
    question: Is it possible to use custom fonts for the barcode text?
  - answer: Visit the [support forum](https://forum.aspose.com/c/words/8/) for assistance
      from the Aspose community and engineers.
    question: Where can I get help if I run into problems?
  type: FAQPage
second_title: Aspose.Words Java Document Processing API
tags:
- barcode generation
- Aspose.Words
- Java document processing
- QR code
title: Come creare etichette QR code Java con Aspose.Words
url: /it/java/document-conversion-and-export/generating-custom-barcode-labels/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come creare etichette QR code Java con Aspose.Words

I codici a barre sono essenziali nelle applicazioni moderne—sia che tu stia gestendo l'inventario, stampando biglietti o creando tessere d'identità. In questo tutorial **create QR code Java** etichette e le incorporerai direttamente in un documento Word utilizzando l'interfaccia `IBarcodeGenerator`. Ti guideremo passo passo, dalla configurazione dell'ambiente all'inserimento dell'immagine del codice a barre, così potrai iniziare a usare i codici a barre nei tuoi progetti Java subito.

## Risposte rapide
- **Che cosa insegna questo tutorial?** Come creare etichette QR code Java e incorporarle in un file Word con Aspose.Words per Java.  
- **Quale tipo di codice a barre è usato nell'esempio?** QR code (puoi sostituirlo con uno dei più di 20 tipi supportati).  
- **Ho bisogno di una licenza?** È necessaria una licenza temporanea per l'accesso illimitato durante lo sviluppo.  
- **Quale versione di Java è richiesta?** JDK 8 o superiore.  
- **Posso modificare le dimensioni o i colori del codice a barre?** Sì—modifica le impostazioni `BarcodeParameters` e `BarcodeGenerator`.  

## Cos'è create QR code Java?
`create QR code Java` si riferisce alla generazione di un'immagine QR‑code in modo programmatico in un ambiente Java e al suo inserimento in un documento o componente UI. Aspose.Words per Java insieme ad Aspose.BarCode ti permette di produrre l'immagine interamente in memoria, evitando file temporanei.

## Perché generare etichette di codici a barre personalizzate con Aspose.Words?
Aspose.Words supporta **oltre 35 formati di input e output** e può elaborare **documenti di 500 pagine in meno di 3 secondi** su hardware server standard. Utilizzando la generazione di codici a barre in memoria ottieni il pieno controllo su tipo, dimensione e colori, mantenendo il flusso di lavoro interamente incentrato su Java e indipendente dalla piattaforma.

## Prerequisiti

- Java Development Kit (JDK): versione 8 o superiore.  
- Libreria Aspose.Words per Java: [Download here](https://releases.aspose.com/words/java/).  
- Libreria Aspose.BarCode per Java: [Download here](https://releases.aspose.com/).  
- Integrated Development Environment (IDE): IntelliJ IDEA, Eclipse o qualsiasi IDE preferisci.  
- Licenza temporanea: ottieni una [temporary license](https://purchase.aspose.com/temporary-license/) per l'accesso illimitato.

## Importare i pacchetti

Useremo le librerie Aspose.Words e Aspose.BarCode. Importa i seguenti pacchetti nel tuo progetto:

```java
import com.aspose.barcode.generation.*;
import com.aspose.words.BarcodeParameters;
import com.aspose.words.IBarcodeGenerator;
import java.awt.*;
import java.awt.image.BufferedImage;
```

Queste importazioni ci danno accesso all'API di generazione dei codici a barre e alle classi dei documenti Word di cui avremo bisogno.

## Passo 1: creare una classe di utilità per le operazioni di codice a barre

La classe di utilità contiene helper riutilizzabili come **convert twips to pixels** e **hex‑color conversion**.  
La classe `CustomBarcodeGeneratorUtils` fornisce metodi statici per la conversione delle unità e la gestione dei colori.

### Codice

```java
class CustomBarcodeGeneratorUtils {
    public static double twipsToPixels(String heightInTwips, double defVal) {
        try {
            int lVal = Integer.parseInt(heightInTwips);
            return (lVal / 1440.0) * 96.0; // Assuming default DPI is 96
        } catch (Exception e) {
            return defVal;
        }
    }

    public static Color convertColor(String inputColor, Color defVal) {
        if (inputColor == null || inputColor.isEmpty()) return defVal;
        try {
            int color = Integer.parseInt(inputColor, 16);
            return new Color((color & 0xFF), ((color >> 8) & 0xFF), ((color >> 16) & 0xFF));
        } catch (Exception e) {
            return defVal;
        }
    }
}
```

**Spiegazione**  
- `twipsToPixels` – Word misura le dimensioni in **twips**; questo metodo le converte in pixel dello schermo, utile quando è necessario dimensionare l'immagine del codice a barre con precisione.  
- `convertColor` – Converte una stringa esadecimale (ad es., `"FF0000"` per il rosso) in un oggetto `java.awt.Color`, permettendoti di **add barcode to Word document** con colori di primo piano e di sfondo personalizzati.

## Passo 2: implementare il generatore di codice a barre personalizzato

Ora implementeremo l'interfaccia `IBarcodeGenerator`. Questa classe è responsabile di **generate QR code Java**‑style immagini che Aspose.Words può incorporare.  
L'interfaccia `IBarcodeGenerator` definisce un unico metodo che restituisce un `BufferedImage` rappresentante il codice a barre.

### Codice

```java
class CustomBarcodeGenerator implements IBarcodeGenerator {
    public BufferedImage getBarcodeImage(BarcodeParameters parameters) {
        try {
            BarcodeGenerator gen = new BarcodeGenerator(
                CustomBarcodeGeneratorUtils.getBarcodeEncodeType(parameters.getBarcodeType()),
                parameters.getBarcodeValue()
            );

            gen.getParameters().getBarcode().setBarColor(
                CustomBarcodeGeneratorUtils.convertColor(parameters.getForegroundColor(), Color.BLACK)
            );
            gen.getParameters().setBackColor(
                CustomBarcodeGeneratorUtils.convertColor(parameters.getBackgroundColor(), Color.WHITE)
            );

            return gen.generateBarCodeImage();
        } catch (Exception e) {
            return new BufferedImage(100, 100, BufferedImage.TYPE_INT_ARGB);
        }
    }

    public BufferedImage getOldBarcodeImage(BarcodeParameters parameters) {
        throw new UnsupportedOperationException();
    }
}
```

**Spiegazione**  
- `getBarcodeImage` crea un'istanza di `BarcodeGenerator`, applica i colori forniti tramite `BarcodeParameters` e infine restituisce un `BufferedImage`.  
- Il metodo gestisce anche gli errori restituendo un'immagine segnaposto, garantendo che la creazione del documento Word non vada in crash.

## Come incorporare un codice a barre in Word usando Aspose.Words?

Carica il tuo file Word con `new Document("template.docx")` (o crea un nuovo `Document`) e chiama `builder.insertImage` con l'immagine del codice a barre restituita dal generatore. Questo modello a due passaggi incorpora il codice a barre direttamente senza scrivere un file intermedio su disco. Specificando le dimensioni dell'immagine in pixel o convertendo i twips di Word in pixel, puoi controllare la dimensione e il posizionamento esatti del codice a barre nel documento, garantendo un layout professionale che stampa correttamente su qualsiasi stampante.

## Passo 3: generare un codice a barre e incorporarlo in Word

Con il generatore pronto, possiamo ora produrre un'immagine di codice a barre e **insert it into a Word document**.

### Codice

```java
import com.aspose.words.*;

public class GenerateCustomBarcodeLabels {
    public static void main(String[] args) throws Exception {
        // Load or create a Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Set up custom barcode generator
        CustomBarcodeGenerator barcodeGenerator = new CustomBarcodeGenerator();
        BarcodeParameters barcodeParameters = new BarcodeParameters();
        barcodeParameters.setBarcodeType("QR");
        barcodeParameters.setBarcodeValue("https://example.com");
        barcodeParameters.setForegroundColor("000000");
        barcodeParameters.setBackgroundColor("FFFFFF");

        // Generate barcode image
        BufferedImage barcodeImage = barcodeGenerator.getBarcodeImage(barcodeParameters);

        // Insert barcode image into Word document
        builder.insertImage(barcodeImage, 200, 200);

        // Save the document
        doc.save("CustomBarcodeLabels.docx");

        System.out.println("Barcode labels generated successfully!");
    }
}
```

**Spiegazione**  

1. **Document initialization** – Crea un nuovo `Document` (oppure puoi caricare un modello esistente).  
2. **Barcode parameters** – Definisce il tipo di codice a barre (`QR`), il valore da codificare e i colori di primo piano/sfondo.  
3. **Image insertion** – `builder.insertImage` posiziona il codice a barre generato nella dimensione desiderata (200 × 200 pixel). Questo è il fulcro di **how to embed barcode in Word**.  
4. **Saving** – Il documento finale, `CustomBarcodeLabels.docx`, contiene il codice a barre incorporato pronto per la stampa o la distribuzione.

## Problemi comuni e risoluzione

| Sintomo | Probabile causa | Soluzione |
|---------|-----------------|-----------|
| Il codice a barre appare vuoto | I colori di `BarcodeParameters` sono gli stessi (es., nero su nero) | Verifica i valori di `foregroundColor` e `backgroundColor`. |
| L'immagine è distorta | Dimensioni dei pixel errate passate a `insertImage` | Regola gli argomenti di larghezza/altezza o usa la conversione `twipsToPixels` per una dimensione precisa. |
| Errore di tipo di codice a barre non supportato | Uso di un tipo non riconosciuto da `CustomBarcodeGeneratorUtils.getBarcodeEncodeType` | Assicurati che la stringa del tipo di codice a barre corrisponda a uno dei `EncodeTypes` supportati (es., `"QR"`, `"CODE128"`). |

## Domande frequenti

**Q: Posso usare Aspose.Words per Java senza licenza?**  
A: Sì, ma avrà limitazioni di valutazione. Ottieni una [temporary license](https://purchase.aspose.com/temporary-license/) per la piena funzionalità.

**Q: Quali tipi di codici a barre posso generare?**  
A: Aspose.BarCode supporta QR, Code 128, EAN‑13, DataMatrix, PDF417 e molti altri formati—oltre 20 simbologie in totale. Consulta la [documentation](https://reference.aspose.com/words/java/) per l'elenco completo.

**Q: Come posso modificare la dimensione del codice a barre?**  
A: Regola gli argomenti di larghezza e altezza in `builder.insertImage`, o calcola i twips Word esatti usando `twipsToPixels` per un controllo pixel‑perfetto.

**Q: È possibile usare font personalizzati per il testo del codice a barre?**  
A: Sì, puoi personalizzare il font del testo tramite la proprietà `CodeTextParameters` del `BarcodeGenerator`.

**Q: Dove posso ottenere aiuto se incontro problemi?**  
A: Visita il [support forum](https://forum.aspose.com/c/words/8/) per assistenza dalla community e dagli ingegneri di Aspose.

## Conclusione

Seguendo i passaggi sopra, ora sai come **create QR code Java** immagini e **embed barcode in Word** documenti usando Aspose.Words per Java. Questa tecnica è sufficientemente flessibile per etichette di inventario, biglietti per eventi o qualsiasi scenario in cui un codice a barre deve far parte di un documento generato. Sperimenta con diversi tipi di codici a barre, colori e opzioni di dimensionamento per adattarli alle tue esigenze aziendali specifiche.

---

**Ultimo aggiornamento:** 2026-10-23  
**Testato con:** Aspose.Words per Java 24.12, Aspose.BarCode per Java 24.12  
**Autore:** Aspose

## Tutorial correlati

- [Crea PDF da Word con generazione di codice a barre – Aspose.Words per Java](/words/java/document-conversion-and-export/using-barcode-generation/)
- [Salva Word come PDF con guida passo passo Aspose Words Java](/words/java/document-conversion-and-export/save-word-as-pdf-with-aspose-words-step-by-step-java-guide/)
- [Crea documento Word vuoto in Java con Aspose Words](/words/java/document-manipulation/create-blank-word-document-in-java-with-aspose-words/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}