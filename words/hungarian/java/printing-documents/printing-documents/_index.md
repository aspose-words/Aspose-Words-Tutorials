---
"description": "Tanulja meg, hogyan nyomtathat dokumentumokat az Aspose.Words for Java segítségével. Lépésről lépésre útmutató a zökkenőmentes nyomtatáshoz Java-alkalmazásokban."
"linktitle": "Dokumentumok nyomtatása"
"second_title": "Aspose.Words Java dokumentumfeldolgozó API"
"title": "Dokumentumok nyomtatása Aspose.Words programban Java-ban"
"url": "/hu/java/printing-documents/printing-documents/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Dokumentumok nyomtatása Aspose.Words programban Java-ban


Ha az Aspose.Words for Java segítségével szeretne dokumentumokat nyomtatni, jó helyen jár. Ebben a lépésről lépésre bemutatjuk, hogyan nyomtathat dokumentumokat az Aspose.Words for Java segítségével a mellékelt forráskód felhasználásával.

## Bevezetés

dokumentumok nyomtatása gyakori feladat számos alkalmazásban. Az Aspose.Words for Java egy hatékony API-t biztosít a Word-dokumentumokkal való munkához, beleértve a nyomtatási lehetőségüket is. Ebben az oktatóanyagban lépésről lépésre végigvezetjük a Word-dokumentum nyomtatásának folyamatán.

## A környezet beállítása

Mielőtt belemerülnénk a kódba, győződjünk meg arról, hogy a következő előfeltételek teljesülnek:

- Telepített Java fejlesztőkészlet (JDK)
- Aspose.Words for Java könyvtár letöltve és hozzáadva a projekthez

## A dokumentum betöltése

A kezdéshez be kell töltenie a nyomtatni kívánt Word-dokumentumot. Csere `"Your Document Directory"` a dokumentum elérési útjával és `"Your Output Directory"` a kívánt kimeneti könyvtárral.

```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Rendering.docx");
```

## Nyomtatási feladat létrehozása

Ezután létrehozunk egy nyomtatási feladatot a betöltött dokumentum kinyomtatásához. Az alábbi kódrészlet inicializálja a nyomtatási feladatot, és beállítja a kívánt nyomtatóbeállításokat.

```java
// Hozz létre egy nyomtatási feladatot a dokumentumunk kinyomtatásához.
PrinterJob pj = PrinterJob.getPrinterJob();
// Inicializáljon egy attribútumkészletet a dokumentumban található oldalak számával.
PrintRequestAttributeSet attributes = new HashPrintRequestAttributeSet();
attributes.add(new PageRanges(1, doc.getPageCount()));
// Adja át a nyomtatóbeállításokat a többi paraméterrel együtt a nyomtatandó dokumentumnak.
MultipagePrintDocument awPrintDoc = new MultipagePrintDocument(doc, 4, true, attributes);
```

## A dokumentum nyomtatása

Most, hogy beállítottuk a nyomtatási feladatot, itt az ideje kinyomtatni a dokumentumot. A következő kódrészlet társítja a dokumentumot a nyomtatási feladathoz, és elindítja a nyomtatási folyamatot.

```java
// Adja át a nyomtatandó dokumentumot a nyomtatási feladat segítségével.
pj.setPrintable(awPrintDoc);
pj.print();
```
## Teljes forráskód
```java
string dataDir = "Your Document Directory";
Document doc = new Document(dataDir + "Rendering.docx");
// Hozz létre egy nyomtatási feladatot a dokumentumunk kinyomtatásához.
PrinterJob pj = PrinterJob.getPrinterJob();
// Inicializáljon egy attribútumkészletet a dokumentumban található oldalak számával.
PrintRequestAttributeSet attributes = new HashPrintRequestAttributeSet();
attributes.add(new PageRanges(1, doc.getPageCount()));
// Adja át a nyomtatóbeállításokat a többi paraméterrel együtt a nyomtatandó dokumentumnak.
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
    /// Az egyéni PrintDocument osztály konstruktora.
    /// </összefoglaló> 
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
        // Az oldal kezdő és záró indexei az attribútumkészletben meghatározottak szerint.
        int[][] pageRanges = ((PageRanges) mAttributeSet.get(PageRanges.class)).getMembers();
        int fromPage = pageRanges[0][0] - 1;
        int toPage = pageRanges[0][1] - 1;
        Dimension thumbCount = getThumbCount(mPagesPerSheet, pf);
        // Számítsa ki a következőként megjelenítendő oldal indexét.
        int pagesOnCurrentSheet = (int) (page * (thumbCount.getWidth() * thumbCount.getHeight()));
        // Ha az oldalindex nagyobb, mint a teljes oldaltartomány, akkor nincs semmi.
        // többet kell megjeleníteni.
        if (pagesOnCurrentSheet > (toPage - fromPage))
            return Printable.NO_SUCH_PAGE;
        // Számítsa ki az egyes bélyegkép-helyőrzők méretét pontokban.
        Point2D.Float thumbSize = new Point2D.Float((float) (pf.getImageableWidth() / thumbCount.getWidth()),
                (float) (pf.getImageableHeight() / thumbCount.getHeight()));
        // Számítsd ki az első oldal számát, amelyet erre a papírlapra kell nyomtatni.
        int startPage = pagesOnCurrentSheet + fromPage;
        // Válassza ki az erre a papírlapra nyomtatandó utolsó oldal számát.
        int pageTo = Math.max(startPage + mPagesPerSheet - 1, toPage);
        // Végigmegy a kiválasztott oldalakon a tárolt aktuális oldaltól a számított oldalig
        // utolsó oldal.
        for (int pageIndex = startPage; pageIndex <= pageTo; pageIndex++) {
            // Számítsd ki az oszlop- és sorindexeket.
            int rowIdx = (int) Math.floor((pageIndex - startPage) / thumbCount.getWidth());
            int columnIdx = (int) Math.floor((pageIndex - startPage) % thumbCount.getWidth());
            // Adja meg a miniatűr helyét világkoordinátákban (jelen esetben pontokban).
            float thumbLeft = columnIdx * thumbSize.x;
            float thumbTop = rowIdx * thumbSize.y;
            try {
                // Számítsd ki a bal és a felső kiindulási pozíciókat.
                int leftPos = (int) (thumbLeft + pf.getImageableX());
                int topPos = (int) (thumbTop + pf.getImageableY());
                // A dokumentumoldal renderelése a Grafikus objektumhoz számított koordináták használatával
                // és a bélyegkép helyőrzőjének mérete.
                // A hasznos visszatérési érték az a méretarány, amelyben az oldal megjelenítésre került.
                float scale = mDocument.renderToSize(pageIndex, (Graphics2D) g, leftPos, topPos, (int) thumbSize.x,
                        (int) thumbSize.y);
                // Rajzolja meg az oldal szegélyeit (az oldal bélyegképe lehet kisebb, mint a bélyegkép)
                // helyőrző méret).
                if (mPrintPageBorders) {
                    // A lap valós 100%-os méretét kapod meg pontokban.
                    Point2D.Float pageSize = mDocument.getPageInfo(pageIndex).getSizeInPoints();
                    // Rajzolja meg a szegélyt a méretezett oldal köré az ismert méretarányt használva.
                    g.setColor(Color.black);
                    g.drawRect(leftPos, topPos, (int) (pageSize.x * scale), (int) (pageSize.y * scale));
                    // Rajzolj keretet a bélyegkép helyőrzője köré.
                    g.setColor(Color.red);
                    g.drawRect(leftPos, topPos, (int) thumbSize.x, (int) thumbSize.y);
                }
            } catch (Exception e) {
                // Ha bármilyen hiba történik a renderelés során, akkor ne tegyen semmit.
                // Ez üres lapot rajzol, ha bármilyen hiba történik a renderelés során.
            }
        }
        return Printable.PAGE_EXISTS;
    }
    private Dimension getThumbCount(int pagesPerSheet, PageFormat pf) {
        Dimension size;
        // Határozza meg az oszlopok és sorok számát a munkalapon a
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

Gratulálunk! Sikeresen kinyomtatott egy Word dokumentumot az Aspose.Words for Java segítségével. Ez a lépésről lépésre szóló útmutató segít zökkenőmentesen integrálni a dokumentumnyomtatást a Java alkalmazásokba.

## GYIK

### 1. kérdés: Kinyomtathatok egy dokumentum bizonyos oldalait az Aspose.Words for Java használatával?

Igen, megadhatja az oldaltartományt egy dokumentum nyomtatásakor. A kódpéldában ezt használtuk `attributes.add(new PageRanges(1, doc.getPageCount()))` az összes oldal kinyomtatásához. Az oldaltartományt szükség szerint módosíthatja.

### 2. kérdés: Alkalmas-e az Aspose.Words Java-ban kötegelt nyomtatásra?

Abszolút! Az Aspose.Words for Java kiválóan alkalmas kötegelt nyomtatási feladatokra. Végignézhetsz egy dokumentumlistán, és egyenként kinyomtathatod őket hasonló kóddal.

### 3. kérdés: Hogyan kezelhetem a nyomtatási hibákat vagy kivételeket?

A nyomtatási folyamat során felmerülő esetleges kivételeket kezelnie kell. A kivételek kezelésével kapcsolatos információkért tekintse meg az Aspose.Words for Java dokumentációját.

### 4. kérdés: Testreszabhatom a nyomtatási beállításokat?

Igen, testreszabhatja a nyomtatási beállításokat az Ön igényei szerint. Az elérhető nyomtatási beállításokról bővebben az Aspose.Words for Java dokumentációjában olvashat.

### 5. kérdés: Hol kaphatok további segítséget és támogatást az Aspose.Words for Java-hoz?

További támogatásért és segítségért látogassa meg a következőt: [Aspose.Words Java fórumhoz](https://forum.aspose.com/).

---

Most, hogy sikeresen megtanultad, hogyan kell dokumentumokat nyomtatni az Aspose.Words for Java használatával, elkezdheted implementálni ezt a funkciót a Java alkalmazásaidban. Jó kódolást!


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}