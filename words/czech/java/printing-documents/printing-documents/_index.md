---
title: Tisk dokumentů v Aspose.Words pro Java
linktitle: Tisk dokumentů
second_title: Aspose.Words Java Document Processing API
description: Naučte se tisknout dokumenty pomocí Aspose.Words for Java. Podrobný průvodce pro bezproblémový tisk ve vašich aplikacích Java.
weight: 10
url: /cs/java/printing-documents/printing-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tisk dokumentů v Aspose.Words pro Java


Pokud chcete tisknout dokumenty pomocí Aspose.Words for Java, jste na správném místě. V tomto podrobném průvodci vás provedeme procesem tisku dokumentů pomocí Aspose.Words for Java pomocí poskytnutého zdrojového kódu.

## Zavedení

Tisk dokumentů je běžným úkolem mnoha aplikací. Aspose.Words for Java poskytuje výkonné API pro práci s dokumenty Wordu, včetně možnosti je tisknout. V tomto tutoriálu vás krok za krokem provedeme procesem tisku dokumentu aplikace Word.

## Nastavení vašeho prostředí

Než se ponoříme do kódu, ujistěte se, že máte splněny následující předpoklady:

- Java Development Kit (JDK) nainstalován
- Knihovna Aspose.Words for Java byla stažena a přidána do vašeho projektu

## Načítání dokumentu

 Chcete-li začít, musíte načíst dokument aplikace Word, který chcete vytisknout. Nahradit`"Your Document Directory"` s cestou k vašemu dokumentu a`"Your Output Directory"` s požadovaným výstupním adresářem.

```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Rendering.docx");
```

## Vytvoření tiskové úlohy

Dále vytvoříme tiskovou úlohu pro tisk našeho načteného dokumentu. Níže uvedený fragment kódu inicializuje tiskovou úlohu a nastaví požadovaná nastavení tiskárny.

```java
// Vytvořte tiskovou úlohu pro tisk našeho dokumentu.
PrinterJob pj = PrinterJob.getPrinterJob();
// Inicializujte sadu atributů s počtem stránek v dokumentu.
PrintRequestAttributeSet attributes = new HashPrintRequestAttributeSet();
attributes.add(new PageRanges(1, doc.getPageCount()));
// Předejte nastavení tiskárny spolu s ostatními parametry do tiskového dokumentu.
MultipagePrintDocument awPrintDoc = new MultipagePrintDocument(doc, 4, true, attributes);
```

## Tisk dokumentu

Nyní, když jsme nastavili tiskovou úlohu, je čas vytisknout dokument. Následující fragment kódu přidruží dokument k tiskové úloze a zahájí proces tisku.

```java
// Předejte dokument k tisku pomocí tiskové úlohy.
pj.setPrintable(awPrintDoc);
pj.print();
```
## Kompletní zdrojový kód
```java
string dataDir = "Your Document Directory";
Document doc = new Document(dataDir + "Rendering.docx");
// Vytvořte tiskovou úlohu pro tisk našeho dokumentu.
PrinterJob pj = PrinterJob.getPrinterJob();
// Inicializujte sadu atributů s počtem stránek v dokumentu.
PrintRequestAttributeSet attributes = new HashPrintRequestAttributeSet();
attributes.add(new PageRanges(1, doc.getPageCount()));
// Předejte nastavení tiskárny spolu s ostatními parametry do tiskového dokumentu.
MultipagePrintDocument awPrintDoc = new MultipagePrintDocument(doc, 4, true, attributes);
// Předejte dokument k tisku pomocí tiskové úlohy.
pj.setPrintable(awPrintDoc);
pj.print();
```
Zdrojový kód MultipagePrintDocument
```java
class MultipagePrintDocument implements Printable
{
    private final Document mDocument;
    private final int mPagesPerSheet;
    private final boolean mPrintPageBorders;
    private final AttributeSet mAttributeSet;
    /// <souhrn>
    /// Konstruktor vlastní třídy PrintDocument.
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
        //Indexy začátku a konce stránky, jak jsou definovány v sadě atributů.
        int[][] pageRanges = ((PageRanges) mAttributeSet.get(PageRanges.class)).getMembers();
        int fromPage = pageRanges[0][0] - 1;
        int toPage = pageRanges[0][1] - 1;
        Dimension thumbCount = getThumbCount(mPagesPerSheet, pf);
        // Vypočítejte index stránky, který se má vykreslit jako další.
        int pagesOnCurrentSheet = (int) (page * (thumbCount.getWidth() * thumbCount.getHeight()));
        // Pokud je index stránky větší než celkový rozsah stránek, pak není nic
        // více k vykreslení.
        if (pagesOnCurrentSheet > (toPage - fromPage))
            return Printable.NO_SUCH_PAGE;
        // Vypočítejte velikost každého zástupného symbolu miniatury v bodech.
        Point2D.Float thumbSize = new Point2D.Float((float) (pf.getImageableWidth() / thumbCount.getWidth()),
                (float) (pf.getImageableHeight() / thumbCount.getHeight()));
        // Vypočítejte číslo první stránky, která se má vytisknout na tento list papíru.
        int startPage = pagesOnCurrentSheet + fromPage;
        // Vyberte číslo poslední stránky, která se má vytisknout na tento list papíru.
        int pageTo = Math.max(startPage + mPagesPerSheet - 1, toPage);
        // Procházejte vybrané stránky od uložené aktuální stránky k vypočtené
        // poslední stránka.
        for (int pageIndex = startPage; pageIndex <= pageTo; pageIndex++) {
            // Vypočítejte sloupcové a řádkové indexy.
            int rowIdx = (int) Math.floor((pageIndex - startPage) / thumbCount.getWidth());
            int columnIdx = (int) Math.floor((pageIndex - startPage) % thumbCount.getWidth());
            // Definujte umístění miniatury ve světových souřadnicích (v tomto případě body).
            float thumbLeft = columnIdx * thumbSize.x;
            float thumbTop = rowIdx * thumbSize.y;
            try {
                // Vypočítejte levou a horní výchozí pozici.
                int leftPos = (int) (thumbLeft + pf.getImageableX());
                int topPos = (int) (thumbTop + pf.getImageableY());
                // Vykreslete stránku dokumentu do grafického objektu pomocí vypočítaných souřadnic
                // a velikost zástupného symbolu miniatur.
                // Užitečná návratová hodnota je měřítko, ve kterém byla stránka vykreslena.
                float scale = mDocument.renderToSize(pageIndex, (Graphics2D) g, leftPos, topPos, (int) thumbSize.x,
                        (int) thumbSize.y);
                //Nakreslete okraje stránky (miniatura stránky může být menší než miniatura
                // velikost zástupného symbolu).
                if (mPrintPageBorders) {
                    // Získejte skutečnou 100% velikost stránky v bodech.
                    Point2D.Float pageSize = mDocument.getPageInfo(pageIndex).getSizeInPoints();
                    // Nakreslete ohraničení kolem stránky s měřítkem pomocí známého měřítka.
                    g.setColor(Color.black);
                    g.drawRect(leftPos, topPos, (int) (pageSize.x * scale), (int) (pageSize.y * scale));
                    // Nakreslete ohraničení kolem zástupného symbolu miniatury.
                    g.setColor(Color.red);
                    g.drawRect(leftPos, topPos, (int) thumbSize.x, (int) thumbSize.y);
                }
            } catch (Exception e) {
                // Pokud se během vykreslování vyskytnou nějaké chyby, nedělejte nic.
                // Pokud během vykreslování dojde k nějakým chybám, vykreslí se prázdná stránka.
            }
        }
        return Printable.PAGE_EXISTS;
    }
    private Dimension getThumbCount(int pagesPerSheet, PageFormat pf) {
        Dimension size;
        // Definujte počet sloupců a řádků na listu pro
        // Papír orientovaný na šířku.
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
        // Pokud je papír orientován na výšku, vyměňte šířku a výšku.
        if ((pf.getWidth() - pf.getImageableX()) < (pf.getHeight() - pf.getImageableY()))
            return new Dimension((int) size.getHeight(), (int) size.getWidth());
        return size;
	}
}
```

## Závěr

Gratuluji! Úspěšně jste vytiskli dokument aplikace Word pomocí Aspose.Words for Java. Tento podrobný průvodce by vám měl pomoci bezproblémově integrovat tisk dokumentů do vašich aplikací Java.

## Nejčastější dotazy

### Q1: Mohu vytisknout konkrétní stránky dokumentu pomocí Aspose.Words for Java?

 Ano, při tisku dokumentu můžete určit rozsah stránek. V příkladu kódu jsme použili`attributes.add(new PageRanges(1, doc.getPageCount()))`vytisknout všechny stránky. Rozsah stránek můžete upravit podle potřeby.

### Q2: Je Aspose.Words for Java vhodný pro dávkový tisk?

Absolutně! Aspose.Words for Java se dobře hodí pro úlohy dávkového tisku. Můžete iterovat seznam dokumentů a tisknout je jeden po druhém pomocí podobného kódu.

### Q3: Jak mohu zpracovat tiskové chyby nebo výjimky?

Měli byste ošetřit všechny potenciální výjimky, které se mohou vyskytnout během procesu tisku. Informace o zpracování výjimek naleznete v dokumentaci Aspose.Words for Java.

### Q4: Mohu dále upravit nastavení tisku?

Ano, nastavení tisku můžete upravit tak, aby vyhovovalo vašim specifickým požadavkům. Prozkoumejte dokumentaci Aspose.Words for Java, kde se dozvíte více o dostupných možnostech tisku.

### Q5: Kde mohu získat další pomoc a podporu pro Aspose.Words for Java?

 Pro další podporu a pomoc můžete navštívit stránku[Aspose.Words for Java forum](https://forum.aspose.com/).

---

Nyní, když jste se úspěšně naučili tisknout dokumenty pomocí Aspose.Words for Java, můžete začít implementovat tuto funkci do svých aplikací Java. Šťastné kódování!
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
