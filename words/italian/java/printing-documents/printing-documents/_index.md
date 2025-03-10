---
title: Stampa di documenti in Aspose.Words per Java
linktitle: Stampa di documenti
second_title: API di elaborazione dei documenti Java Aspose.Words
description: Scopri come stampare documenti usando Aspose.Words per Java. Guida passo passo per una stampa senza soluzione di continuità nelle tue applicazioni Java.
weight: 10
url: /it/java/printing-documents/printing-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Stampa di documenti in Aspose.Words per Java


Se stai cercando di stampare documenti usando Aspose.Words per Java, sei nel posto giusto. In questa guida passo passo, ti guideremo attraverso il processo di stampa di documenti con Aspose.Words per Java usando il codice sorgente fornito.

## Introduzione

La stampa di documenti è un'attività comune in molte applicazioni. Aspose.Words per Java fornisce una potente API per lavorare con i documenti Word, inclusa la possibilità di stamparli. In questo tutorial, ti guideremo passo dopo passo attraverso il processo di stampa di un documento Word.

## Impostazione dell'ambiente

Prima di immergerci nel codice, assicurati di avere i seguenti prerequisiti:

- Java Development Kit (JDK) installato
- Libreria Aspose.Words per Java scaricata e aggiunta al tuo progetto

## Caricamento del documento

 Per iniziare, dovrai caricare il documento Word che vuoi stampare. Sostituisci`"Your Document Directory"` con il percorso del tuo documento e`"Your Output Directory"` con la directory di output desiderata.

```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Rendering.docx");
```

## Creazione di un processo di stampa

Successivamente, creeremo un processo di stampa per stampare il nostro documento caricato. Il frammento di codice seguente inizializza un processo di stampa e imposta le impostazioni di stampa desiderate.

```java
// Creiamo un processo di stampa per stampare il nostro documento.
PrinterJob pj = PrinterJob.getPrinterJob();
// Inizializza un set di attributi con il numero di pagine del documento.
PrintRequestAttributeSet attributes = new HashPrintRequestAttributeSet();
attributes.add(new PageRanges(1, doc.getPageCount()));
// Passare le impostazioni della stampante insieme agli altri parametri al documento di stampa.
MultipagePrintDocument awPrintDoc = new MultipagePrintDocument(doc, 4, true, attributes);
```

## Stampa del documento

Ora che abbiamo impostato il nostro processo di stampa, è il momento di stampare il documento. Il seguente frammento di codice associa il documento al processo di stampa e avvia il processo di stampa.

```java
// Passare il documento da stampare utilizzando il processo di stampa.
pj.setPrintable(awPrintDoc);
pj.print();
```
## Codice sorgente completo
```java
string dataDir = "Your Document Directory";
Document doc = new Document(dataDir + "Rendering.docx");
// Creiamo un processo di stampa per stampare il nostro documento.
PrinterJob pj = PrinterJob.getPrinterJob();
// Inizializza un set di attributi con il numero di pagine del documento.
PrintRequestAttributeSet attributes = new HashPrintRequestAttributeSet();
attributes.add(new PageRanges(1, doc.getPageCount()));
// Passare le impostazioni della stampante insieme agli altri parametri al documento di stampa.
MultipagePrintDocument awPrintDoc = new MultipagePrintDocument(doc, 4, true, attributes);
// Passare il documento da stampare utilizzando il processo di stampa.
pj.setPrintable(awPrintDoc);
pj.print();
```
Codice sorgente di MultipagePrintDocument
```java
class MultipagePrintDocument implements Printable
{
    private final Document mDocument;
    private final int mPagesPerSheet;
    private final boolean mPrintPageBorders;
    private final AttributeSet mAttributeSet;
    /// <sommario>
    /// Il costruttore della classe personalizzata PrintDocument.
    // / </sommario>
    public MultipagePrintDocument(Document document, int pagesPerSheet, boolean printPageBorders,
                                  AttributeSet attributes) {
        if (document == null)
            throw new IllegalArgumentException("document");
        mDocument = document;
        mPagesPerSheet = pagesPerSheet;
        mPrintPageBorders = printPageBorders;
        mAttributeSet = attributes;
    }
    public int print(Graphics g, PageFormat pf, int page) {
        //Indici di inizio e fine pagina come definiti nel set di attributi.
        int[][] pageRanges = ((PageRanges) mAttributeSet.get(PageRanges.class)).getMembers();
        int fromPage = pageRanges[0][0] - 1;
        int toPage = pageRanges[0][1] - 1;
        Dimension thumbCount = getThumbCount(mPagesPerSheet, pf);
        // Calcola l'indice della pagina che verrà renderizzata successivamente.
        int pagesOnCurrentSheet = (int) (page * (thumbCount.getWidth() * thumbCount.getHeight()));
        // Se l'indice della pagina è maggiore dell'intervallo di pagine totale, non c'è nulla
        // altro da rendere.
        if (pagesOnCurrentSheet > (toPage - fromPage))
            return Printable.NO_SUCH_PAGE;
        // Calcola la dimensione di ciascun segnaposto della miniatura in punti.
        Point2D.Float thumbSize = new Point2D.Float((float) (pf.getImageableWidth() / thumbCount.getWidth()),
                (float) (pf.getImageableHeight() / thumbCount.getHeight()));
        // Calcola il numero della prima pagina da stampare su questo foglio di carta.
        int startPage = pagesOnCurrentSheet + fromPage;
        // Seleziona il numero dell'ultima pagina da stampare su questo foglio di carta.
        int pageTo = Math.max(startPage + mPagesPerSheet - 1, toPage);
        // Passa attraverso le pagine selezionate dalla pagina corrente memorizzata a quella calcolata
        // ultima pagina.
        for (int pageIndex = startPage; pageIndex <= pageTo; pageIndex++) {
            // Calcola gli indici di colonna e di riga.
            int rowIdx = (int) Math.floor((pageIndex - startPage) / thumbCount.getWidth());
            int columnIdx = (int) Math.floor((pageIndex - startPage) % thumbCount.getWidth());
            // Definisci la posizione della miniatura in coordinate mondiali (punti in questo caso).
            float thumbLeft = columnIdx * thumbSize.x;
            float thumbTop = rowIdx * thumbSize.y;
            try {
                // Calcola le posizioni di partenza a sinistra e in alto.
                int leftPos = (int) (thumbLeft + pf.getImageableX());
                int topPos = (int) (thumbTop + pf.getImageableY());
                // Renderizza la pagina del documento nell'oggetto Graphics utilizzando le coordinate calcolate
                // e la dimensione del segnaposto della miniatura.
                // Il valore utile restituito è la scala in cui è stata renderizzata la pagina.
                float scale = mDocument.renderToSize(pageIndex, (Graphics2D) g, leftPos, topPos, (int) thumbSize.x,
                        (int) thumbSize.y);
                //Disegna i bordi della pagina (la miniatura della pagina potrebbe essere più piccola della miniatura
                // dimensione segnaposto).
                if (mPrintPageBorders) {
                    // Ottieni la dimensione effettiva del 100% della pagina in punti.
                    Point2D.Float pageSize = mDocument.getPageInfo(pageIndex).getSizeInPoints();
                    // Traccia il bordo attorno alla pagina ridimensionata utilizzando il fattore di scala noto.
                    g.setColor(Color.black);
                    g.drawRect(leftPos, topPos, (int) (pageSize.x * scale), (int) (pageSize.y * scale));
                    // Traccia il bordo attorno al segnaposto della miniatura.
                    g.setColor(Color.red);
                    g.drawRect(leftPos, topPos, (int) thumbSize.x, (int) thumbSize.y);
                }
            } catch (Exception e) {
                // Se si verificano errori durante il rendering, non fare nulla.
                // Se si verificano errori durante il rendering, verrà creata una pagina vuota.
            }
        }
        return Printable.PAGE_EXISTS;
    }
    private Dimension getThumbCount(int pagesPerSheet, PageFormat pf) {
        Dimension size;
        // Definire il numero di colonne e righe sul foglio per l'
        // Carta con orientamento orizzontale.
        switch (pagesPerSheet) {
            case 16:
                size = new Dimension(4, 4);
                break;
            case 9:
                size = new Dimension(3, 3);
                break;
            case 8:
                size = new Dimension(4, 2);
                break;
            case 6:
                size = new Dimension(3, 2);
                break;
            case 4:
                size = new Dimension(2, 2);
                break;
            case 2:
                size = new Dimension(2, 1);
                break;
            default:
                size = new Dimension(1, 1);
                break;
        }
        // Inverti larghezza e altezza se la carta è in orientamento verticale.
        if ((pf.getWidth() - pf.getImageableX()) < (pf.getHeight() - pf.getImageableY()))
            return new Dimension((int) size.getHeight(), (int) size.getWidth());
        return size;
	}
}
```

## Conclusione

Congratulazioni! Hai stampato con successo un documento Word usando Aspose.Words per Java. Questa guida passo passo dovrebbe aiutarti a integrare la stampa di documenti nelle tue applicazioni Java senza problemi.

## Domande frequenti

### D1: Posso stampare pagine specifiche di un documento utilizzando Aspose.Words per Java?

 Sì, puoi specificare l'intervallo di pagine quando stampi un documento. Nell'esempio di codice, abbiamo usato`attributes.add(new PageRanges(1, doc.getPageCount()))`per stampare tutte le pagine. Puoi regolare l'intervallo di pagine come necessario.

### D2: Aspose.Words per Java è adatto alla stampa in batch?

Assolutamente! Aspose.Words per Java è molto adatto per le attività di stampa in batch. Puoi scorrere un elenco di documenti e stamparli uno alla volta usando codice simile.

### D3: Come posso gestire errori di stampa o eccezioni?

Dovresti gestire qualsiasi potenziale eccezione che potrebbe verificarsi durante il processo di stampa. Controlla la documentazione di Aspose.Words for Java per informazioni sulla gestione delle eccezioni.

### D4: Posso personalizzare ulteriormente le impostazioni di stampa?

Sì, puoi personalizzare le impostazioni di stampa per soddisfare i tuoi requisiti specifici. Esplora la documentazione di Aspose.Words for Java per saperne di più sulle opzioni di stampa disponibili.

### D5: Dove posso trovare ulteriore assistenza e supporto per Aspose.Words per Java?

 Per ulteriore supporto e assistenza, puoi visitare il[Forum di Aspose.Words per Java](https://forum.aspose.com/).

---

Ora che hai imparato con successo come stampare documenti usando Aspose.Words per Java, puoi iniziare a implementare questa funzionalità nelle tue applicazioni Java. Buona codifica!
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
