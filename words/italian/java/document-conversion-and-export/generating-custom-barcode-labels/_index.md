---
date: 2026-02-09
description: Genera etichette di codici a barre personalizzate usando Aspose Barcode
  Java in Aspose.Words per Java. Scopri come incorporare i codici a barre nei documenti
  Word e genera esempi Java di codici QR.
linktitle: Generating Custom Barcode Labels
second_title: Aspose.Words Java Document Processing API
title: Generazione di etichette barcode personalizzate con Aspose Barcode Java
url: /it/java/document-conversion-and-export/generating-custom-barcode-labels/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Generazione di Etichette Barcode Personalizzate con Aspose Barcode Java

## Introduzione alla Generazione di Etichette Barcode Personalizzate in Aspose.Words per Java

I barcode sono essenziali nelle applicazioni moderne, e **Aspose Barcode Java** semplifica la loro creazione direttamente all'interno dei documenti Word. Che tu debba **incorporare un barcode in Word**, generare un QR code per un URL, o convertire unità di misura, questo tutorial ti guida passo passo. Pronto a iniziare? Andiamo!

## Risposte Rapide
- **Quale libreria crea barcode in Java?** Aspose Barcode Java abbinato a Aspose.Words per Java.  
- **Quale tipo di barcode è mostrato?** QR code (generate qr code java).  
- **Come converto i twip in pixel?** Usa il metodo di utilità `twipsToPixels` fornito.  
- **Posso aggiungere un barcode a un file Word esistente?** Sì – basta utilizzare il metodo `DocumentBuilder.insertImage`.  
- **È necessaria una licenza?** Una licenza temporanea rimuove i limiti di valutazione.

## Cos'è Aspose Barcode Java?
Aspose Barcode Java è una potente API che consente agli sviluppatori di generare una vasta gamma di barcode 1D e 2D (inclusi i QR code) in modo programmatico. Quando viene combinata con Aspose.Words per Java, puoi **incorporare un barcode in Word** senza uscire dall'ambiente Java.

## Perché usare Aspose Barcode Java con Aspose.Words?
- **Controllo totale** sull'aspetto del barcode (colori, dimensioni, formato).  
- **Integrazione fluida** – l'immagine del barcode può essere inserita direttamente in un documento Word.  
- **Cross‑platform** – funziona su qualsiasi piattaforma compatibile con Java.  
- **Estensibile** – puoi creare classi di utilità per riutilizzare la logica del barcode in più progetti.

## Prerequisiti

Prima di iniziare a programmare, assicurati di avere quanto segue:

- Java Development Kit (JDK): versione 8 o superiore.  
- Libreria Aspose.Words per Java: [Download here](https://releases.aspose.com/words/java/).  
- Libreria Aspose.BarCode per Java: [Download here](https://releases.aspose.com/).  
- Ambiente di sviluppo integrato (IDE): IntelliJ IDEA, Eclipse o qualsiasi IDE tu preferisca.  
- Licenza temporanea: ottieni una [temporary license](https://purchase.aspose.com/temporary-license/) per accesso illimitato.

## Importare i Pacchetti

Useremo le librerie Aspose.Words e Aspose.BarCode. Importa i seguenti pacchetti nel tuo progetto:

```java
import com.aspose.barcode.generation.*;
import com.aspose.words.BarcodeParameters;
import com.aspose.words.IBarcodeGenerator;
import java.awt.*;
import java.awt.image.BufferedImage;
```

Queste importazioni ci permettono di utilizzare le funzionalità di generazione dei barcode e di integrarle nei documenti Word.

Dividiamo il compito in passaggi gestibili.

## Passo 1: Creare una Classe di Utilità per le Operazioni sui Barcode

Per semplificare le operazioni legate ai barcode, creeremo una classe di utilità con metodi di supporto per attività comuni come la conversione dei colori e la **conversione di twip in pixel**.

### Codice:

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

- `twipsToPixels` converte l'unità di misura usata da Word (twip) in pixel dello schermo – un comodo helper quando occorrono dimensioni precise.  
- `convertColor` traduce una stringa di colore esadecimale (es. “FF0000”) in un oggetto Java `Color`, permettendoti di personalizzare il colore di primo piano e di sfondo del barcode.

## Passo 2: Implementare il Generatore di Barcode Personalizzato

Implementeremo l'interfaccia `IBarcodeGenerator` affinché Aspose.Words possa richiedere un'immagine barcode ogni volta che incontra un campo barcode.

### Codice:

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

- `getBarcodeImage` costruisce un `BarcodeGenerator` usando il tipo **generate qr code java** specificato (QR nel nostro esempio).  
- Applica i colori di primo piano e di sfondo tramite i metodi di utilità, quindi restituisce l'immagine renderizzata.  
- L'immagine di fallback garantisce che il programma continui anche se la creazione del barcode fallisce.

## Passo 3: Generare un Barcode e Aggiungerlo a un Documento Word

Ora uniamo tutto: creiamo un documento, generiamo un barcode e **come aggiungere un barcode** al file Word.

### Codice:

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

1. **Inizializzazione del Documento** – crea un nuovo `Document` (oppure puoi caricare un .docx esistente).  
2. **Parametri del Barcode** – definisci il tipo (`QR`), il valore e i colori, dimostrando l'uso di **generate qr code java**.  
3. **Inserimento Immagine** – `builder.insertImage` posiziona il barcode dove necessario, mostrando effettivamente **come aggiungere un barcode** a un file Word.  
4. **Salvataggio** – il documento finale (`CustomBarcodeLabels.docx`) contiene il barcode incorporato, pronto per la stampa o la distribuzione.

## Problemi Comuni e Soluzioni

| Problema | Causa | Soluzione |
|----------|-------|-----------|
| Il barcode appare vuoto | Stringa colore non valida o tipo di barcode non supportato | Verifica il formato esadecimale del colore e usa un tipo supportato (es. QR, Code128). |
| La dimensione dell'immagine è errata | Conversione pixel errata | Usa `twipsToPixels` per calcolare le dimensioni esatte in base al layout di Word. |
| Eccezione di licenza | Nessuna licenza Aspose valida | Applica una licenza temporanea o acquistata prima di eseguire il codice. |

## Domande Frequenti

**D: Posso usare Aspose.Words per Java senza licenza?**  
R: Sì, ma incontrerai limitazioni di valutazione. Ottieni una [temporary license](https://purchase.aspose.com/temporary-license/) per la piena funzionalità.

**D: Quali tipi di barcode posso generare?**  
R: Aspose.BarCode supporta QR, Code 128, EAN‑13 e molti altri. Consulta la [documentazione ufficiale](https://reference.aspose.com/words/java/) per l'elenco completo.

**D: Come posso modificare la dimensione del barcode?**  
R: Regola i parametri width/height in `builder.insertImage` o modifica le proprietà `XDimension` e `BarHeight` sull'oggetto `BarcodeGenerator`.

**D: Posso usare font personalizzati per la parte leggibile dal barcode?**  
R: Assolutamente. Usa la proprietà `CodeTextParameters` per impostare famiglia, dimensione e stile del font.

**D: Dove posso trovare supporto per Aspose.Words?**  
R: Visita il [forum di supporto](https://forum.aspose.com/c/words/8/) per assistenza dalla community e dal supporto ufficiale.

---

**Ultimo aggiornamento:** 2026-02-09  
**Testato con:** Aspose.Words per Java 24.12, Aspose.BarCode per Java 24.12  
**Autore:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}