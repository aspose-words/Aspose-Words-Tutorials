---
"description": "Naučte se, jak tisknout dokumenty pomocí Aspose.Words pro Javu. Podrobný návod pro bezproblémový tisk ve vašich Java aplikacích."
"linktitle": "Tisk dokumentů"
"second_title": "Rozhraní API pro zpracování dokumentů v Javě od Aspose.Words"
"title": "Tisk dokumentů v Aspose.Words pro Javu"
"url": "/cs/java/printing-documents/printing-documents/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Tisk dokumentů v Aspose.Words pro Javu


Pokud chcete tisknout dokumenty pomocí Aspose.Words pro Javu, jste na správném místě. V tomto podrobném návodu vás provedeme procesem tisku dokumentů pomocí Aspose.Words pro Javu s využitím poskytnutého zdrojového kódu.

## Zavedení

Tisk dokumentů je běžným úkolem v mnoha aplikacích. Aspose.Words pro Javu poskytuje výkonné API pro práci s dokumenty Wordu, včetně možnosti jejich tisku. V tomto tutoriálu vás krok za krokem provedeme procesem tisku dokumentu Wordu.

## Nastavení prostředí

Než se pustíme do kódu, ujistěte se, že máte splněny následující předpoklady:

- Nainstalovaná vývojářská sada Java (JDK)
- Knihovna Aspose.Words pro Javu stažena a přidána do vašeho projektu

## Načítání dokumentu

Chcete-li začít, budete muset načíst dokument aplikace Word, který chcete vytisknout. Nahraďte `"Your Document Directory"` s cestou k vašemu dokumentu a `"Your Output Directory"` s požadovaným výstupním adresářem.

```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Rendering.docx");
```

## Vytvoření tiskové úlohy

Dále vytvoříme tiskovou úlohu pro tisk načteného dokumentu. Následující úryvek kódu inicializuje tiskovou úlohu a nastaví požadované nastavení tiskárny.

```java
// Vytvořte tiskovou úlohu pro tisk našeho dokumentu.
PrinterJob pj = PrinterJob.getPrinterJob();
// Inicializujte sadu atributů s počtem stránek v dokumentu.
PrintRequestAttributeSet attributes = new HashPrintRequestAttributeSet();
attributes.add(new PageRanges(1, doc.getPageCount()));
// Předejte nastavení tiskárny spolu s dalšími parametry do tištěného dokumentu.
MultipagePrintDocument awPrintDoc = new MultipagePrintDocument(doc, 4, true, attributes);
```

## Tisk dokumentu

Nyní, když jsme nastavili tiskovou úlohu, je čas vytisknout dokument. Následující úryvek kódu přiřadí dokument k tiskové úloze a zahájí proces tisku.

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
// Předejte nastavení tiskárny spolu s dalšími parametry do tištěného dokumentu.
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
    /// </summary> 
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
        // Indexy začátku a konce stránky, jak jsou definovány v sadě atributů.
        int[][] pageRanges = ((PageRanges) mAttributeSet.get(PageRanges.class)).getMembers();
        int fromPage = pageRanges[0][0] - 1;
        int toPage = pageRanges[0][1] - 1;
        Dimension thumbCount = getThumbCount(mPagesPerSheet, pf);
        // Vypočítejte index stránky, která se má vykreslit dále.
        int pagesOnCurrentSheet = (int) (page * (thumbCount.getWidth() * thumbCount.getHeight()));
        // Pokud je index stránky větší než celkový rozsah stránek, pak se nic neděje.
        // více k vykreslení.
        if (pagesOnCurrentSheet > (toPage - fromPage))
            return Printable.NO_SUCH_PAGE;
        // Vypočítejte velikost každého zástupného symbolu miniatury v bodech.
        Point2D.Float thumbSize = new Point2D.Float((float) (pf.getImageableWidth() / thumbCount.getWidth()),
                (float) (pf.getImageableHeight() / thumbCount.getHeight()));
        // Vypočítejte počet prvních stránek, které se mají na tento list papíru vytisknout.
        int startPage = pagesOnCurrentSheet + fromPage;
        // Vyberte číslo poslední stránky, která se má na tento list papíru vytisknout.
        int pageTo = Math.max(startPage + mPagesPerSheet - 1, toPage);
        // Procházet vybrané stránky od uložené aktuální stránky až po vypočítanou
        // poslední stránka.
        for (int pageIndex = startPage; pageIndex <= pageTo; pageIndex++) {
            // Vypočítejte indexy sloupců a řádků.
            int rowIdx = (int) Math.floor((pageIndex - startPage) / thumbCount.getWidth());
            int columnIdx = (int) Math.floor((pageIndex - startPage) % thumbCount.getWidth());
            // Definujte umístění miniatury ve světových souřadnicích (v tomto případě v bodech).
            float thumbLeft = columnIdx * thumbSize.x;
            float thumbTop = rowIdx * thumbSize.y;
            try {
                // Vypočítejte levou a horní počáteční pozici.
                int leftPos = (int) (thumbLeft + pf.getImageableX());
                int topPos = (int) (thumbTop + pf.getImageableY());
                // Vykreslení stránky dokumentu do objektu Graphics pomocí vypočítaných souřadnic
                // a velikost zástupného symbolu miniatury.
                // Užitečnou návratovou hodnotou je měřítko, ve kterém byla stránka vykreslena.
                float scale = mDocument.renderToSize(pageIndex, (Graphics2D) g, leftPos, topPos, (int) thumbSize.x,
                        (int) thumbSize.y);
                // Nakreslete okraje stránky (miniatura stránky může být menší než miniatura
                // velikost zástupného symbolu).
                if (mPrintPageBorders) {
                    // Získejte skutečnou 100% velikost stránky v bodech.
                    Point2D.Float pageSize = mDocument.getPageInfo(pageIndex).getSizeInPoints();
                    // Nakreslete okraj kolem stránky se změněným měřítkem pomocí známého faktoru měřítka.
                    g.setColor(Color.black);
                    g.drawRect(leftPos, topPos, (int) (pageSize.x * scale), (int) (pageSize.y * scale));
                    // Nakreslete ohraničení kolem zástupného symbolu miniatury.
                    g.setColor(Color.red);
                    g.drawRect(leftPos, topPos, (int) thumbSize.x, (int) thumbSize.y);
                }
            } catch (Exception e) {
                // Pokud se během renderování vyskytnou nějaké chyby, nedělejte nic.
                // Pokud se během vykreslování vyskytnou nějaké chyby, vykreslí se prázdná stránka.
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
        // Pokud je papír v orientaci na výšku, prohoďte šířku a výšku.
        if ((pf.getWidth() - pf.getImageableX()) < (pf.getHeight() - pf.getImageableY()))
            return new Dimension((int) size.getHeight(), (int) size.getWidth());
        return size;
	}
}
```

## Závěr

Gratulujeme! Úspěšně jste vytiskli dokument Wordu pomocí Aspose.Words pro Javu. Tento podrobný návod by vám měl pomoci bezproblémově integrovat tisk dokumentů do vašich aplikací Java.

## Často kladené otázky

### Q1: Mohu tisknout konkrétní stránky dokumentu pomocí Aspose.Words pro Javu?

Ano, při tisku dokumentu můžete zadat rozsah stránek. V příkladu kódu jsme použili `attributes.add(new PageRanges(1, doc.getPageCount()))` vytisknout všechny stránky. Rozsah stránek můžete podle potřeby upravit.

### Q2: Je Aspose.Words pro Javu vhodný pro dávkový tisk?

Rozhodně! Aspose.Words pro Javu se skvěle hodí pro dávkový tisk. Můžete procházet seznam dokumentů a tisknout je jeden po druhém pomocí podobného kódu.

### Q3: Jak mohu řešit tiskové chyby nebo výjimky?

Měli byste ošetřit všechny potenciální výjimky, které mohou nastat během procesu tisku. Informace o ošetření výjimek naleznete v dokumentaci k Aspose.Words pro Javu.

### Q4: Mohu si dále přizpůsobit nastavení tisku?

Ano, nastavení tisku si můžete přizpůsobit podle svých specifických požadavků. Prostudujte si dokumentaci k Aspose.Words pro Javu, kde se dozvíte více o dostupných možnostech tisku.

### Q5: Kde mohu získat další pomoc a podporu pro Aspose.Words pro Javu?

Pro další podporu a pomoc můžete navštívit [Fórum Aspose.Words pro Javu](https://forum.aspose.com/).

---

Nyní, když jste se úspěšně naučili tisknout dokumenty pomocí Aspose.Words pro Javu, můžete začít implementovat tuto funkci ve svých Java aplikacích. Přejeme vám šťastné programování!


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}