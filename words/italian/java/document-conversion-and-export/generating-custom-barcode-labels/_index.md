---
date: 2025-12-10
description: Scopri come generare etichette di codici a barre personalizzate usando
  Aspose.Words per Java. Questa guida passo‑passo ti mostra come incorporare i codici
  a barre nei documenti Word.
linktitle: Generating Custom Barcode Labels
second_title: Aspose.Words Java Document Processing API
title: Genera etichette barcode personalizzate in Aspose.Words per Java
url: /it/java/document-conversion-and-export/generating-custom-barcode-labels/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Genera Etichette Barcode Personalizzate con Aspose.Words per Java

## Introduzione alla generazione di barcode personalizzati in Aspose.Words per Java

I barcode sono essenziali nelle applicazioni moderne—sia che tu stia gestendo l'inventario, stampando biglietti o creando tessere d'identità. In questo tutorial **genererai etichette barcode personalizzate** e le incorporerai direttamente in un documento Word utilizzando l'interfaccia `IBarcodeGenerator`. Ti guideremo passo passo, dalla configurazione dell'ambiente all'inserimento dell'immagine del barcode, così potrai iniziare a usare i barcode nei tuoi progetti Java subito.

## Risposte Rapide
- **Cosa insegna questo tutorial?** Come generare etichette barcode personalizzate e incorporarle in un file Word con Aspose.Words per Java.  
- **Quale tipo di barcode è usato nell'esempio?** QR code (puoi sostituirlo con qualsiasi tipo supportato).  
- **È necessaria una licenza?** È richiesta una licenza temporanea per l'accesso illimitato durante lo sviluppo.  
- **Quale versione di Java è necessaria?** JDK 8 o superiore.  
- **Posso modificare le dimensioni o i colori del barcode?** Sì—modifica le impostazioni di `BarcodeParameters` e `BarcodeGenerator`.

## Prerequisiti

Prima di iniziare a codificare, assicurati di avere quanto segue:

- Java Development Kit (JDK): Versione 8 o superiore.  
- Libreria Aspose.Words per Java: [Download here](https://releases.aspose.com/words/java/).  
- Libreria Aspose.BarCode per Java: [Download here](https://releases.aspose.com/).  
- Integrated Development Environment (IDE): IntelliJ IDEA, Eclipse o qualsiasi IDE tu preferisca.  
- Licenza Temporanea: Ottieni una [temporary license](https://purchase.aspose.com/temporary-license/) per l'accesso illimitato.

## Importare i Pacchetti

Utilizzeremo le librerie Aspose.Words e Aspose.BarCode. Importa i seguenti pacchetti nel tuo progetto:

```java
import com.aspose.barcode.generation.*;
import com.aspose.words.BarcodeParameters;
import com.aspose.words.IBarcodeGenerator;
import java.awt.*;
import java.awt.image.BufferedImage;
```

Queste importazioni ci danno accesso all'API di generazione dei barcode e alle classi dei documenti Word di cui avremo bisogno.

## Passo 1: Creare una Classe di Utilità per le Operazioni sui Barcode

Per mantenere il codice principale pulito, incapsuleremo gli helper comuni—come **convertire twips in pixel** e **conversione di colore esadecimale**—in una classe di utilità.

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

- `twipsToPixels` – Word misura le dimensioni in **twips**; questo metodo le converte in pixel dello schermo, utile quando è necessario dimensionare l'immagine del barcode con precisione.  
- `convertColor` – Trasforma una stringa esadecimale (es. `"FF0000"` per il rosso) in un oggetto `java.awt.Color`, consentendoti di **inserire barcode** con colori di primo piano e sfondo personalizzati.

## Passo 2: Implementare il Generatore di Barcode Personalizzato

Ora implementeremo l'interfaccia `IBarcodeGenerator`. Questa classe sarà responsabile di generare immagini **generate qr code java**‑style che Aspose.Words potrà incorporare.

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

## Passo 3: Generare un Barcode e **incorporare barcode in Word**

Con il generatore pronto, possiamo ora produrre un'immagine barcode e **inserirla in un documento Word**.

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

1. **Inizializzazione del Documento** – Crea un nuovo `Document` (oppure puoi caricare un modello esistente).  
2. **Parametri del Barcode** – Definisce il tipo di barcode (`QR`), il valore da codificare e i colori di primo piano/sfondo.  
3. **Inserimento dell'Immagine** – `builder.insertImage` posiziona il barcode generato nella dimensione desiderata (200 × 200 pixel). Questo è il cuore di **come inserire barcode** in un file Word.  
4. **Salvataggio** – Il documento finale, `CustomBarcodeLabels.docx`, contiene il barcode incorporato, pronto per la stampa o la distribuzione.

## Perché generare etichette barcode personalizzate con Aspose.Words?

- **Controllo totale** sull'aspetto del barcode (tipo, dimensione, colori).  
- **Integrazione fluida**—nessun file immagine intermedio; il barcode è generato in memoria e inserito direttamente.  
- **Cross‑platform**—funziona su qualsiasi OS che supporta Java, rendendolo ideale per la generazione di documenti lato server.  
- **Scalabile**—puoi iterare su una fonte dati per creare centinaia di etichette personalizzate in un unico run.

## Problemi Comuni & Risoluzione

| Sintomo | Probabile Causa | Soluzione |
|---------|-----------------|-----------|
| Il barcode appare vuoto | I colori di `BarcodeParameters` sono uguali (es. nero su nero) | Verifica i valori di `foregroundColor` e `backgroundColor`. |
| L'immagine è distorta | Dimensioni pixel errate passate a `insertImage` | Regola gli argomenti di larghezza/altezza o usa la conversione `twipsToPixels` per una dimensione precisa. |
| Errore di tipo barcode non supportato | È stato usato un tipo non riconosciuto da `CustomBarcodeGeneratorUtils.getBarcodeEncodeType` | Assicurati che la stringa del tipo di barcode corrisponda a uno dei `EncodeTypes` supportati (es. `"QR"`, `"CODE128"`). |

## Domande Frequenti

**D: Posso usare Aspose.Words per Java senza licenza?**  
R: Sì, ma avrà alcune limitazioni. Ottieni una [temporary license](https://purchase.aspose.com/temporary-license/) per la piena funzionalità.

**D: Quali tipi di barcode posso generare?**  
R: Aspose.BarCode supporta QR, Code 128, EAN‑13 e molti altri formati. Consulta la [documentazione](https://reference.aspose.com/words/java/) per l'elenco completo.

**D: Come posso modificare la dimensione del barcode?**  
R: Regola gli argomenti di larghezza e altezza in `builder.insertImage`, oppure usa `twipsToPixels` per convertire le unità di misura di Word in pixel.

**D: È possibile usare font personalizzati per il testo del barcode?**  
R: Sì, puoi personalizzare il font del testo tramite la proprietà `CodeTextParameters` del `BarcodeGenerator`.

**D: Dove posso ottenere supporto se incontro problemi?**  
R: Visita il [support forum](https://forum.aspose.com/c/words/8/) per assistenza dalla community e dagli ingegneri di Aspose.

## Conclusione

Seguendo i passaggi sopra, ora sai come **generare immagini barcode personalizzate** e **incorporare barcode in documenti Word** usando Aspose.Words per Java. Questa tecnica è sufficientemente flessibile per etichette di inventario, biglietti per eventi o qualsiasi scenario in cui un barcode debba far parte di un documento generato. Sperimenta con diversi tipi di barcode e opzioni di stile per soddisfare le esigenze specifiche della tua attività.

---

**Ultimo Aggiornamento:** 2025-12-10  
**Testato Con:** Aspose.Words per Java 24.12, Aspose.BarCode per Java 24.12  
**Autore:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}