---
"description": "Lär dig hur du skriver ut dokument med Aspose.Words för Java. Steg-för-steg-guide för sömlös utskrift i dina Java-program."
"linktitle": "Utskrift av dokument"
"second_title": "Aspose.Words Java-dokumentbehandlings-API"
"title": "Skriva ut dokument i Aspose.Words för Java"
"url": "/sv/java/printing-documents/printing-documents/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Skriva ut dokument i Aspose.Words för Java


Om du vill skriva ut dokument med Aspose.Words för Java har du kommit rätt. I den här steg-för-steg-guiden guidar vi dig genom processen att skriva ut dokument med Aspose.Words för Java med hjälp av den medföljande källkoden.

## Introduktion

Att skriva ut dokument är en vanlig uppgift i många applikationer. Aspose.Words för Java tillhandahåller ett kraftfullt API för att arbeta med Word-dokument, inklusive möjligheten att skriva ut dem. I den här handledningen guidar vi dig genom processen att skriva ut ett Word-dokument steg för steg.

## Konfigurera din miljö

Innan vi går in i koden, se till att du har följande förutsättningar på plats:

- Java Development Kit (JDK) installerat
- Aspose.Words för Java-biblioteket har laddats ner och lagts till i ditt projekt

## Läser in dokumentet

För att komma igång måste du ladda Word-dokumentet du vill skriva ut. Ersätt `"Your Document Directory"` med sökvägen till ditt dokument och `"Your Output Directory"` med önskad utdatakatalog.

```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Rendering.docx");
```

## Skapa ett utskriftsjobb

Nästa steg är att skapa ett utskriftsjobb för att skriva ut det inlästa dokumentet. Kodavsnittet nedan initierar utskriften och ställer in önskade skrivarinställningar.

```java
// Skapa ett utskriftsjobb för att skriva ut vårt dokument.
PrinterJob pj = PrinterJob.getPrinterJob();
// Initiera en attributuppsättning med antalet sidor i dokumentet.
PrintRequestAttributeSet attributes = new HashPrintRequestAttributeSet();
attributes.add(new PageRanges(1, doc.getPageCount()));
// Skicka skrivarinställningarna tillsammans med de andra parametrarna till utskriftsdokumentet.
MultipagePrintDocument awPrintDoc = new MultipagePrintDocument(doc, 4, true, attributes);
```

## Skriva ut dokumentet

Nu när vi har konfigurerat vårt utskriftsjobb är det dags att skriva ut dokumentet. Följande kodavsnitt associerar dokumentet med utskriftsjobbet och initierar utskriftsprocessen.

```java
// Skicka dokumentet som ska skrivas ut med hjälp av utskriftsjobbet.
pj.setPrintable(awPrintDoc);
pj.print();
```
## Komplett källkod
```java
string dataDir = "Your Document Directory";
Document doc = new Document(dataDir + "Rendering.docx");
// Skapa ett utskriftsjobb för att skriva ut vårt dokument.
PrinterJob pj = PrinterJob.getPrinterJob();
// Initiera en attributuppsättning med antalet sidor i dokumentet.
PrintRequestAttributeSet attributes = new HashPrintRequestAttributeSet();
attributes.add(new PageRanges(1, doc.getPageCount()));
// Skicka skrivarinställningarna tillsammans med de andra parametrarna till utskriftsdokumentet.
MultipagePrintDocument awPrintDoc = new MultipagePrintDocument(doc, 4, true, attributes);
// Skicka dokumentet som ska skrivas ut med hjälp av utskriftsjobbet.
pj.setPrintable(awPrintDoc);
pj.print();
```
Källkod för MultipagePrintDocument
```java
class MultipagePrintDocument implements Printable
{
    private final Document mDocument;
    private final int mPagesPerSheet;
    private final boolean mPrintPageBorders;
    private final AttributeSet mAttributeSet;
    /// <sammanfattning>
    /// Konstruktorn för den anpassade PrintDocument-klassen.
    /// </sammanfattning> 
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
        // Sidans start- och slutindex enligt definitionen i attributuppsättningen.
        int[][] pageRanges = ((PageRanges) mAttributeSet.get(PageRanges.class)).getMembers();
        int fromPage = pageRanges[0][0] - 1;
        int toPage = pageRanges[0][1] - 1;
        Dimension thumbCount = getThumbCount(mPagesPerSheet, pf);
        // Beräkna sidindexet som ska renderas härnäst.
        int pagesOnCurrentSheet = (int) (page * (thumbCount.getWidth() * thumbCount.getHeight()));
        // Om sidindexet är större än det totala sidintervallet finns det ingenting
        // mer att rendera.
        if (pagesOnCurrentSheet > (toPage - fromPage))
            return Printable.NO_SUCH_PAGE;
        // Beräkna storleken på varje platshållare för miniatyrbilder i punkter.
        Point2D.Float thumbSize = new Point2D.Float((float) (pf.getImageableWidth() / thumbCount.getWidth()),
                (float) (pf.getImageableHeight() / thumbCount.getHeight()));
        // Beräkna numret på den första sidan som ska skrivas ut på detta pappersark.
        int startPage = pagesOnCurrentSheet + fromPage;
        // Välj numret på den sista sidan som ska skrivas ut på detta pappersark.
        int pageTo = Math.max(startPage + mPagesPerSheet - 1, toPage);
        // Gå igenom de valda sidorna från den lagrade aktuella sidan till den beräknade
        // sista sidan.
        for (int pageIndex = startPage; pageIndex <= pageTo; pageIndex++) {
            // Beräkna kolumn- och radindex.
            int rowIdx = (int) Math.floor((pageIndex - startPage) / thumbCount.getWidth());
            int columnIdx = (int) Math.floor((pageIndex - startPage) % thumbCount.getWidth());
            // Definiera miniatyrbildens plats i världskoordinater (punkter i det här fallet).
            float thumbLeft = columnIdx * thumbSize.x;
            float thumbTop = rowIdx * thumbSize.y;
            try {
                // Beräkna startpositionerna till vänster och övre.
                int leftPos = (int) (thumbLeft + pf.getImageableX());
                int topPos = (int) (thumbTop + pf.getImageableY());
                // Rendera dokumentsidan till grafikobjektet med hjälp av beräknade koordinater
                // och platshållarstorlek för miniatyrbilder.
                // Det användbara returvärdet är den skala i vilken sidan renderades.
                float scale = mDocument.renderToSize(pageIndex, (Graphics2D) g, leftPos, topPos, (int) thumbSize.x,
                        (int) thumbSize.y);
                // Rita sidkanterna (sidans miniatyrbild kan vara mindre än miniatyrbilden
                // platshållarstorlek).
                if (mPrintPageBorders) {
                    // Få sidans verkliga 100 % storlek i punkter.
                    Point2D.Float pageSize = mDocument.getPageInfo(pageIndex).getSizeInPoints();
                    // Rita kanten runt den skalade sidan med hjälp av den kända skalfaktorn.
                    g.setColor(Color.black);
                    g.drawRect(leftPos, topPos, (int) (pageSize.x * scale), (int) (pageSize.y * scale));
                    // Rita ramen runt platshållaren för miniatyrbilden.
                    g.setColor(Color.red);
                    g.drawRect(leftPos, topPos, (int) thumbSize.x, (int) thumbSize.y);
                }
            } catch (Exception e) {
                // Om det uppstår några fel under renderingen, gör ingenting.
                // Detta kommer att rita en tom sida om det finns några fel under renderingen.
            }
        }
        return Printable.PAGE_EXISTS;
    }
    private Dimension getThumbCount(int pagesPerSheet, PageFormat pf) {
        Dimension size;
        // Definiera antalet kolumner och rader på arket för
        // Liggande orienterat papper.
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
        // Byt bredd och höjd om pappret är i stående orientering.
        if ((pf.getWidth() - pf.getImageableX()) < (pf.getHeight() - pf.getImageableY()))
            return new Dimension((int) size.getHeight(), (int) size.getWidth());
        return size;
	}
}
```

## Slutsats

Grattis! Du har skrivit ut ett Word-dokument med Aspose.Words för Java. Den här steg-för-steg-guiden bör hjälpa dig att integrera dokumentutskrift i dina Java-program sömlöst.

## Vanliga frågor

### F1: Kan jag skriva ut specifika sidor i ett dokument med Aspose.Words för Java?

Ja, du kan ange sidintervallet när du skriver ut ett dokument. I kodexemplet använde vi `attributes.add(new PageRanges(1, doc.getPageCount()))` för att skriva ut alla sidor. Du kan justera sidintervallet efter behov.

### F2: Är Aspose.Words för Java lämpligt för batchutskrift?

Absolut! Aspose.Words för Java är väl lämpat för batchutskrift. Du kan iterera igenom en lista med dokument och skriva ut dem ett i taget med liknande kod.

### F3: Hur kan jag hantera tryckfel eller undantag?

Du bör hantera eventuella undantag som kan uppstå under utskriftsprocessen. Se dokumentationen för Aspose.Words för Java för information om hur du hanterar undantag.

### F4: Kan jag anpassa utskriftsinställningarna ytterligare?

Ja, du kan anpassa utskriftsinställningarna efter dina specifika behov. Utforska dokumentationen för Aspose.Words för Java för att lära dig mer om tillgängliga utskriftsalternativ.

### F5: Var kan jag få mer hjälp och support för Aspose.Words för Java?

För ytterligare stöd och hjälp kan du besöka [Aspose.Words för Java-forum](https://forum.aspose.com/).

---

Nu när du har lärt dig hur man skriver ut dokument med Aspose.Words för Java kan du börja implementera den här funktionen i dina Java-applikationer. Lycka till med kodningen!


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}