---
title: Dokumentumok nyomtatása Aspose.Words for Java nyelven
linktitle: Dokumentumok nyomtatása
second_title: Aspose.Words Java Document Processing API
description: Ismerje meg, hogyan nyomtathat dokumentumokat az Aspose.Words for Java használatával. Lépésről lépésre útmutató a zökkenőmentes nyomtatáshoz Java-alkalmazásaiban.
weight: 10
url: /hu/java/printing-documents/printing-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Dokumentumok nyomtatása Aspose.Words for Java nyelven


Ha az Aspose.Words for Java használatával szeretne dokumentumokat nyomtatni, akkor jó helyen jár. Ebben a lépésenkénti útmutatóban végigvezetjük a dokumentumok Aspose.Words for Java segítségével, a mellékelt forráskód használatával történő nyomtatásának folyamatán.

## Bevezetés

A dokumentumok nyomtatása sok alkalmazásban gyakori feladat. Az Aspose.Words for Java hatékony API-t biztosít a Word-dokumentumokkal való munkavégzéshez, beleértve a nyomtatás lehetőségét is. Ebben az oktatóanyagban lépésről lépésre végigvezetjük a Word-dokumentum nyomtatásának folyamatán.

## Környezetének beállítása

Mielőtt belemerülnénk a kódba, győződjön meg arról, hogy a következő előfeltételek teljesülnek:

- Java Development Kit (JDK) telepítve
- Aspose.Words for Java könyvtár letöltve és hozzáadva a projekthez

## A dokumentum betöltése

 A kezdéshez be kell töltenie a nyomtatni kívánt Word-dokumentumot. Cserélje ki`"Your Document Directory"` a dokumentum elérési útjával és`"Your Output Directory"` a kívánt kimeneti könyvtárral.

```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Rendering.docx");
```

## Nyomtatási feladat létrehozása

Ezután létrehozunk egy nyomtatási feladatot a betöltött dokumentumunk kinyomtatásához. Az alábbi kódrészlet inicializálja a nyomtatási feladatot, és beállítja a kívánt nyomtatóbeállításokat.

```java
// Hozzon létre egy nyomtatási feladatot a dokumentumunk nyomtatásához.
PrinterJob pj = PrinterJob.getPrinterJob();
// Inicializáljon egy attribútumkészletet a dokumentum oldalainak számával.
PrintRequestAttributeSet attributes = new HashPrintRequestAttributeSet();
attributes.add(new PageRanges(1, doc.getPageCount()));
// Adja át a nyomtató beállításait a többi paraméterrel együtt a nyomtatási dokumentumnak.
MultipagePrintDocument awPrintDoc = new MultipagePrintDocument(doc, 4, true, attributes);
```

## A dokumentum kinyomtatása

Most, hogy beállítottuk a nyomtatási feladatunkat, ideje kinyomtatni a dokumentumot. A következő kódrészlet társítja a dokumentumot a nyomtatási feladathoz, és elindítja a nyomtatási folyamatot.

```java
// Adja át a nyomtatandó dokumentumot a nyomtatási feladat segítségével.
pj.setPrintable(awPrintDoc);
pj.print();
```
## Teljes forráskód
```java
string dataDir = "Your Document Directory";
Document doc = new Document(dataDir + "Rendering.docx");
// Hozzon létre egy nyomtatási feladatot a dokumentumunk nyomtatásához.
PrinterJob pj = PrinterJob.getPrinterJob();
// Inicializáljon egy attribútumkészletet a dokumentum oldalainak számával.
PrintRequestAttributeSet attributes = new HashPrintRequestAttributeSet();
attributes.add(new PageRanges(1, doc.getPageCount()));
// Adja át a nyomtató beállításait a többi paraméterrel együtt a nyomtatási dokumentumnak.
MultipagePrintDocument awPrintDoc = new MultipagePrintDocument(doc, 4, true, attributes);
// Adja át a nyomtatandó dokumentumot a nyomtatási feladat segítségével.
pj.setPrintable(awPrintDoc);
pj.print();
```
A MultipagePrintDocument forráskódja
```java
class MultipagePrintDocument implements Printable
{
    private final Document mDocument;
    private final int mPagesPerSheet;
    private final boolean mPrintPageBorders;
    private final AttributeSet mAttributeSet;
    /// <összefoglaló>
    /// Az egyedi PrintDocument osztály konstruktora.
    // / </summary>
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
        //Az oldal kezdő és záró indexei az attribútumkészletben meghatározottak szerint.
        int[][] pageRanges = ((PageRanges) mAttributeSet.get(PageRanges.class)).getMembers();
        int fromPage = pageRanges[0][0] - 1;
        int toPage = pageRanges[0][1] - 1;
        Dimension thumbCount = getThumbCount(mPagesPerSheet, pf);
        // Számítsa ki a következő oldalindexet.
        int pagesOnCurrentSheet = (int) (page * (thumbCount.getWidth() * thumbCount.getHeight()));
        // Ha az oldalindex nagyobb, mint a teljes oldaltartomány, akkor nincs semmi
        // többet kell megjeleníteni.
        if (pagesOnCurrentSheet > (toPage - fromPage))
            return Printable.NO_SUCH_PAGE;
        // Számítsa ki az egyes miniatűr-helyőrzők méretét pontokban.
        Point2D.Float thumbSize = new Point2D.Float((float) (pf.getImageableWidth() / thumbCount.getWidth()),
                (float) (pf.getImageableHeight() / thumbCount.getHeight()));
        // Számítsa ki az erre a papírlapra nyomtatandó első oldal számát.
        int startPage = pagesOnCurrentSheet + fromPage;
        // Válassza ki az erre a papírlapra nyomtatandó utolsó oldal számát.
        int pageTo = Math.max(startPage + mPagesPerSheet - 1, toPage);
        // Lapozás a kiválasztott oldalakon a tárolt aktuális oldaltól a számítottig
        // utolsó oldal.
        for (int pageIndex = startPage; pageIndex <= pageTo; pageIndex++) {
            // Számítsa ki az oszlop- és sorindexeket!
            int rowIdx = (int) Math.floor((pageIndex - startPage) / thumbCount.getWidth());
            int columnIdx = (int) Math.floor((pageIndex - startPage) % thumbCount.getWidth());
            // Határozza meg a miniatűrök helyét a világ koordinátáiban (ebben az esetben pontokban).
            float thumbLeft = columnIdx * thumbSize.x;
            float thumbTop = rowIdx * thumbSize.y;
            try {
                // Számítsa ki a bal és a felső kiindulási helyzetet.
                int leftPos = (int) (thumbLeft + pf.getImageableX());
                int topPos = (int) (thumbTop + pf.getImageableY());
                // Számított koordináták segítségével jelenítse meg a dokumentum oldalát a Graphics objektumnak
                // és a miniatűr helyőrző mérete.
                // A hasznos visszatérési érték az a lépték, amelyen az oldal renderelésre került.
                float scale = mDocument.renderToSize(pageIndex, (Graphics2D) g, leftPos, topPos, (int) thumbSize.x,
                        (int) thumbSize.y);
                //Rajzolja meg az oldalszegélyeket (az oldal bélyegképe kisebb lehet, mint a miniatűr
                // helyőrző mérete).
                if (mPrintPageBorders) {
                    // Szerezze meg az oldal valódi 100%-os méretét pontokban.
                    Point2D.Float pageSize = mDocument.getPageInfo(pageIndex).getSizeInPoints();
                    // Rajzolja meg a szegélyt a méretezett oldal köré az ismert léptéktényezővel.
                    g.setColor(Color.black);
                    g.drawRect(leftPos, topPos, (int) (pageSize.x * scale), (int) (pageSize.y * scale));
                    // Rajzolja meg a szegélyt az indexkép helyőrzője köré.
                    g.setColor(Color.red);
                    g.drawRect(leftPos, topPos, (int) thumbSize.x, (int) thumbSize.y);
                }
            } catch (Exception e) {
                // Ha bármilyen hiba történik a renderelés során, akkor ne tegyen semmit.
                // Ez üres oldalt rajzol, ha a renderelés során hiba történik.
            }
        }
        return Printable.PAGE_EXISTS;
    }
    private Dimension getThumbCount(int pagesPerSheet, PageFormat pf) {
        Dimension size;
        // Határozza meg az oszlopok és sorok számát a lapon a
        // Fekvő tájolású papír.
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
        // Cserélje fel a szélességet és a magasságot, ha a papír álló tájolású.
        if ((pf.getWidth() - pf.getImageableX()) < (pf.getHeight() - pf.getImageableY()))
            return new Dimension((int) size.getHeight(), (int) size.getWidth());
        return size;
	}
}
```

## Következtetés

Gratulálok! Sikeresen kinyomtatott egy Word-dokumentumot az Aspose.Words for Java használatával. Ez a lépésenkénti útmutató segít abban, hogy a dokumentumnyomtatást zökkenőmentesen integrálja Java-alkalmazásaiba.

## GYIK

### 1. kérdés: Kinyomtathatok egy dokumentum bizonyos oldalait az Aspose.Words for Java használatával?

 Igen, dokumentum nyomtatásakor megadhatja az oldaltartományt. A kódpéldában használtuk`attributes.add(new PageRanges(1, doc.getPageCount()))`az összes oldal kinyomtatásához. Igény szerint módosíthatja az oldaltartományt.

### 2. kérdés: Az Aspose.Words for Java alkalmas kötegelt nyomtatásra?

Teljesen! Az Aspose.Words for Java kiválóan alkalmas kötegelt nyomtatási feladatokra. Ismételheti a dokumentumok listáját, és egyenként nyomtathatja ki őket hasonló kóddal.

### 3. kérdés: Hogyan kezelhetem a nyomtatási hibákat vagy kivételeket?

A nyomtatási folyamat során esetlegesen előforduló kivételeket kezelnie kell. A kivételek kezelésével kapcsolatos információkért tekintse meg az Aspose.Words for Java dokumentációját.

### 4. kérdés: Testreszabhatom a nyomtatási beállításokat?

Igen, testreszabhatja a nyomtatási beállításokat, hogy megfeleljenek az egyedi követelményeknek. Fedezze fel az Aspose.Words for Java dokumentációját, hogy többet megtudjon az elérhető nyomtatási lehetőségekről.

### 5. kérdés: Hol kaphatok további segítséget és támogatást az Aspose.Words for Java-hoz?

 További támogatásért és segítségért látogassa meg a[Aspose.Words for Java fórum](https://forum.aspose.com/).

---

Most, hogy sikeresen megtanulta, hogyan nyomtathat dokumentumokat az Aspose.Words for Java használatával, megkezdheti ennek a funkciónak a megvalósítását Java-alkalmazásaiban. Boldog kódolást!
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
