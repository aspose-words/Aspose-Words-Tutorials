---
category: general
date: 2026-07-03
description: Esporta le forme fluttuanti in linea durante la conversione di Word in
  PDF in linea. Scopri come impostare le opzioni PDF e salvare Word come PDF con opzioni
  in Java.
draft: false
keywords:
- export floating shapes inline
- convert word to pdf inline
- how to set pdf options
- save word as pdf options
language: it
og_description: Esporta le forme fluttuanti in linea quando converti un documento
  Word in PDF. Questo tutorial mostra come impostare le opzioni PDF e le opzioni di
  salvataggio di Word in PDF.
og_title: Esporta forme fluttuanti in linea – Guida alla conversione PDF in Java
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Export floating shapes inline while converting Word to PDF inline.
    Learn how to set PDF options and save Word as PDF options in Java.
  headline: Export Floating Shapes Inline – Complete Guide to PDF Conversion
  type: TechArticle
- description: Export floating shapes inline while converting Word to PDF inline.
    Learn how to set PDF options and save Word as PDF options in Java.
  name: Export Floating Shapes Inline – Complete Guide to PDF Conversion
  steps:
  - name: 1. “What if my document contains complex SmartArt?”
    text: SmartArt is treated as a drawing object. The inline flag works for most
      vector shapes, but very intricate SmartArt may still be rendered as an image.
      In those cases, consider flattening the SmartArt in Word before conversion,
      or use `pdfOptions.setExportSmartArtAsImage(true)` to force image export.
  - name: 2. “Can I combine inline and block exports in the same document?”
    text: Unfortunately the API applies the setting globally. If you need mixed behavior,
      split the document into sections, export each section separately with different
      options, then merge the PDFs using `PdfMerger`.
  - name: 3. “Does this affect font embedding?”
    text: No. Font embedding is controlled by `pdfOptions.setEmbedFullFonts(true)`
      (default). You can safely enable or disable it without touching the inline shape
      flag.
  - name: 4. “How do I verify that shapes are really `<span>`?”
    text: Open the resulting PDF in a tool like **PDF.js** or **Adobe Acrobat** →
      **Edit PDF** → **Object Inspector**. You’ll see the shape wrapped in a `<span>`
      element in the underlying XML. If you see `<div>`, the option wasn’t applied.
  type: HowTo
tags:
- Java
- PDF
- Aspose.Words
title: Esporta forme fluttuanti in linea – Guida completa alla conversione PDF
url: /it/java/document-conversion-and-export/export-floating-shapes-inline-complete-guide-to-pdf-conversi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Esporta Forme Fluttuanti Inline – Guida Completa alla Conversione PDF

Ti è mai capitato di dover **esportare forme fluttuanti inline** quando converti un documento Word in PDF? Non sei l’unico: molti sviluppatori incontrano questo problema quando i loro diagrammi o icone si spostano misteriosamente in livelli separati. La buona notizia è che un’unica opzione PDF può mantenere quelle forme all’interno dei tag `<span>`, preservando il layout esattamente come lo vedi in Word.

In questo tutorial vedremo **come impostare le opzioni PDF** in Java, ti mostreremo il codice esatto per **salvare Word come PDF con opzioni**, e spiegheremo perché potresti voler **convertire Word in PDF inline** invece dell’esportazione predefinita a livello di blocco. Alla fine avrai a disposizione uno snippet pronto all’uso da inserire in qualsiasi progetto Maven o Gradle.

## Cosa Imparerai

- La differenza tra esportazione inline `<span>` e blocco `<div>` per le forme fluttuanti.  
- Come configurare `PdfSaveOptions` per forzare il rendering inline.  
- Codice passo‑passo che carica un `.docx`, applica l’opzione e genera un PDF.  
- Problemi comuni (font mancanti, forme non supportate) e come evitarli.  
- Suggerimenti per testare l’output e estendere l’approccio ad altri elementi del documento.

**Prerequisiti** – avrai bisogno di Java 8 o superiore, della libreria Aspose.Words for Java (o di qualsiasi API che implementi la classe `PdfSaveOptions`), e di un file Word di esempio con forme fluttuanti (il tutorial utilizza `FloatingShapes.docx`). Non sono richiesti altri strumenti esterni.

---

## Passo 1: Carica il Documento Word di Origine

La prima cosa da fare è aprire il `.docx` che vuoi trasformare. È un’operazione semplice, ma assicurati che il percorso sia assoluto o correttamente risolto dal classpath.

```java
import com.aspose.words.Document;

// Step 1: Load the source Word document
Document doc = new Document("YOUR_DIRECTORY/FloatingShapes.docx");
```

*Perché è importante:*  
Se il documento non viene caricato correttamente, la successiva conversione in PDF genererà una `FileNotFoundException`. L’utilizzo di `Document` garantisce che il modello interno sia completamente popolato, incluse le eventuali forme fluttuanti presenti nella pagina.

---

## Passo 2: Crea le Opzioni di Salvataggio PDF e Imposta le Forme Fluttuanti Inline

Qui avviene la magia. Per impostazione predefinita Aspose.Words esporta le forme fluttuanti come elementi di blocco `<div>`, il che può interrompere il flusso nei PDF basati su HTML. Impostare `setExportFloatingShapesAsInlineTag(true)` indica al motore di avvolgere ogni forma in un `<span>` inline.

```java
import com.aspose.words.PdfSaveOptions;

// Step 2: Create PDF save options and set floating shapes to be exported as inline <span> elements
PdfSaveOptions pdfOptions = new PdfSaveOptions();
pdfOptions.setExportFloatingShapesAsInlineTag(true); // true → <span>, false → <div>
```

*Perché è importante:*  
- **Fedeltà del layout** – I tag inline mantengono la forma allineata al testo circostante, evitando spazi indesiderati.  
- **Ricercabilità** – Gli elementi inline sono più facilmente indicizzati correttamente dai lettori PDF.  
- **Controllo dello stile** – Puoi targettizzare il `<span>` con CSS se in seguito converti il PDF di nuovo in HTML.

> **Consiglio professionale:** Se mai avrai bisogno del vecchio comportamento a blocco per un documento specifico, basta passare `false` o omettere del tutto la chiamata.

---

## Passo 3: Salva il Documento come PDF Utilizzando le Opzioni Configurate

Ora combini il `Document` caricato con il `PdfSaveOptions` e scrivi il file. Questa singola riga fa il lavoro pesante.

```java
// Step 3: Save the document as a PDF using the configured options
doc.save("YOUR_DIRECTORY/FloatingShapes.pdf", pdfOptions);
```

*Perché è importante:*  
Il metodo `save` rispetta ogni flag impostato su `pdfOptions`. Dimenticare di passare le opzioni farà tornare l’esportazione predefinita a blocchi, vanificando lo scopo di **esportare forme fluttuanti inline**.

---

## Esempio Completo Funzionante

Mettendo tutto insieme, ecco un programma compatto che puoi compilare ed eseguire subito. Sostituisci `YOUR_DIRECTORY` con un percorso reale sulla tua macchina.

```java
import com.aspose.words.*;

public class ExportFloatingShapesInlineDemo {
    public static void main(String[] args) {
        try {
            // Load the source Word document
            Document doc = new Document("YOUR_DIRECTORY/FloatingShapes.docx");

            // Configure PDF options to export floating shapes as inline <span>
            PdfSaveOptions pdfOptions = new PdfSaveOptions();
            pdfOptions.setExportFloatingShapesAsInlineTag(true);

            // Save as PDF with the above options
            doc.save("YOUR_DIRECTORY/FloatingShapes.pdf", pdfOptions);

            System.out.println("PDF created successfully with inline floating shapes.");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Output previsto** – Dopo aver eseguito il programma, apri `FloatingShapes.pdf`. Dovresti vedere le forme allineate al testo, senza spazi bianchi aggiuntivi, e la rappresentazione HTML (se ispezioni la struttura interna del PDF) conterrà tag `<span>` attorno a ciascuna forma.

![Export floating shapes inline example](https://example.com/export-inline.png "Screenshot showing floating shapes rendered inline in the PDF")

*Testo alternativo dell’immagine:* **esporta forme fluttuanti inline** screenshot del PDF con forme inline.

---

## Domande Frequenti & Casi Limite

### 1. “E se il mio documento contiene SmartArt complesso?”

Lo SmartArt è trattato come oggetto di disegno. Il flag inline funziona per la maggior parte delle forme vettoriali, ma SmartArt molto intricato potrebbe comunque essere renderizzato come immagine. In questi casi, considera di appiattire lo SmartArt in Word prima della conversione, oppure usa `pdfOptions.setExportSmartArtAsImage(true)` per forzare l’esportazione come immagine.

### 2. “Posso combinare esportazioni inline e a blocco nello stesso documento?”

Sfortunatamente l’API applica l’impostazione a livello globale. Se ti serve un comportamento misto, dividi il documento in sezioni, esporta ogni sezione separatamente con opzioni diverse, poi unisci i PDF usando `PdfMerger`.

### 3. “Questo influisce sull’incorporamento dei font?”

No. L’incorporamento dei font è controllato da `pdfOptions.setEmbedFullFonts(true)` (impostazione predefinita). Puoi abilitarlo o disabilitarlo tranquillamente senza toccare il flag delle forme inline.

### 4. “Come verifico che le forme siano davvero `<span>`?”

Apri il PDF risultante con uno strumento come **PDF.js** o **Adobe Acrobat** → **Edit PDF** → **Object Inspector**. Vedrai la forma avvolta da un elemento `<span>` nell’XML sottostante. Se trovi `<div>`, l’opzione non è stata applicata.

---

## Estendere l’Approccio – Opzioni Correlate

Mentre sei qui, potresti voler esplorare altri parametri di conversione PDF:

| Opzione | Cosa fa | Caso d'uso tipico |
|--------|----------|-------------------|
| `setCompressImages(true)` | Riduce le dimensioni delle immagini | Download più veloci |
| `setUseHighQualityRendering(true)` | Migliora il rendering vettoriale | PDF pronti per la stampa |
| `setExportDocumentStructure(true)` | Aggiunge tag strutturali per l’accessibilità | Conformità WCAG |
| `setSaveFormat(SaveFormat.PDF)` | Imposta esplicitamente il formato (raramente necessario) | Pipeline multi‑formato |

Queste impostazioni si combinano bene con gli scenari **convertire word in pdf inline** dove hai bisogno sia di fedeltà del layout sia di performance.

---

## Testare la Conversione

1. **Controllo visivo** – Apri il PDF in due visualizzatori (Chrome e Adobe Reader) per assicurarti che le forme siano allineate.  
2. **Diff automatizzato** – Usa una libreria come `pdfbox` per estrarre l’XML e verificare la presenza dei tag `<span>`.  
3. **Benchmark delle prestazioni** – Misura il tempo impiegato con e senza `setCompressImages` per valutare il compromesso.

Un rapido esempio JUnit:

```java
@Test
public void testInlineExport() throws Exception {
    Document doc = new Document("src/test/resources/FloatingShapes.docx");
    PdfSaveOptions opts = new PdfSaveOptions();
    opts.setExportFloatingShapesAsInlineTag(true);
    ByteArrayOutputStream out = new ByteArrayOutputStream();
    doc.save(out, opts);
    String pdfXml = new String(out.toByteArray(), StandardCharsets.UTF_8);
    assertTrue(pdfXml.contains("<span"));
}
```

---

## Conclusione

Ora disponi di una soluzione solida, end‑to‑end, per **esportare forme fluttuanti inline** quando **converti Word in PDF inline**. Configurando `PdfSaveOptions` controlli il tag HTML usato per ogni forma, mantenendo i PDF ordinati e ricercabili. Ricorda di testare l’output, regolare opzioni correlate come la compressione delle immagini e gestire i casi limite come SmartArt complesso.

Pronto per il passo successivo? Prova ad applicare la stessa tecnica per **esportare tabelle fluttuanti inline** o sperimenta PDF con CSS usando `HtmlSaveOptions` di Aspose. Lo stesso schema—carica, configura, salva—vale per quasi tutti gli scenari di conversione da documento a PDF.

Hai altre domande su **come impostare le opzioni pdf** o ti serve aiuto con **salvare word come pdf options** per un’altra libreria? Lascia un commento, e buona programmazione!

## Cosa Dovresti Imparare Dopo?


I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell’API e a esplorare approcci alternativi nei tuoi progetti.

- [Convert Word to PDF with Aspose.Words for Java](/words/english/java/document-converting/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Export Word Document Structure to PDF Document](/words/english/net/programming-with-pdfsaveoptions/export-document-structure/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}