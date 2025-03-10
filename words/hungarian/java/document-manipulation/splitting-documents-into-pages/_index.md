---
title: Dokumentumok felosztása oldalakra az Aspose.Words for Java programban
linktitle: Dokumentumok felosztása oldalakra
second_title: Aspose.Words Java Document Processing API
description: Ismerje meg, hogyan oszthat fel dokumentumokat oldalakra az Aspose.Words for Java használatával. Lépésről lépésre útmutató forráskóddal a hatékony dokumentumfeldolgozás érdekében.
weight: 23
url: /hu/java/document-manipulation/splitting-documents-into-pages/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Dokumentumok felosztása oldalakra az Aspose.Words for Java programban


Ha Java-alapú dokumentumfeldolgozással dolgozik, az Aspose.Words for Java egy hatékony API, amely segítségével hatékonyan oszthatja fel a dokumentumokat külön oldalakra. Ebben a lépésről lépésre bemutatott oktatóanyagban végigvezetjük a dokumentumok felosztásának folyamatán a megadott forráskód használatával. Az oktatóanyag végére könnyedén feloszthatja a dokumentumokat, javítva ezzel dokumentumkezelési képességeit.

## 1. Bevezetés

Az Aspose.Words for Java egy Java könyvtár, amely lehetővé teszi a Word dokumentumok programozott kezelését. Az egyik gyakori feladat a dokumentum különálló oldalakra való felosztása, amely különféle célokra hasznos lehet, például archiváláshoz, nyomtatáshoz vagy dokumentumfeldolgozáshoz.

## 2. Előfeltételek

Mielőtt belemerülnénk a kódba, győződjön meg arról, hogy a következő előfeltételek teljesülnek:

- Java Development Kit (JDK) telepítve a rendszerére.
-  Aspose.Words for Java könyvtár, amelyet letölthet[itt](https://releases.aspose.com/words/java/).

## 3. A környezet beállítása

A kezdéshez állítsa be fejlesztői környezetét az alábbiak szerint:

- Hozzon létre egy Java-projektet a kívánt integrált fejlesztőkörnyezetben (IDE).
- Adja hozzá az Aspose.Words for Java könyvtárat a projekthez. Hivatkozhat a[dokumentáció](https://reference.aspose.com/words/java/) részletes utasításokért.

## 4. A forráskód megértése

Az Ön által megadott forráskód arra szolgál, hogy egy dokumentumot különálló oldalakra ossza fel. Bontsuk fel a legfontosabb összetevőket:

```java
String fileName = FilenameUtils.getBaseName(docName);
String extensionName = FilenameUtils.getExtension(docName);
System.out.println("Processing document: " + fileName + "." + extensionName);
Document doc = new Document(docName);
```

- Kivonjuk a bemeneti dokumentum alapnevét és kiterjesztését.
- A dokumentumot az Aspose.Words for Java segítségével töltjük be.

## 5. Dokumentumok felosztása lépésről lépésre

### 5.1. A dokumentum betöltése

```java
Document doc = new Document(docName);
```

 Ebben a lépésben betöltjük a bemeneti dokumentumot a`Document` objektum, amely lehetővé teszi számunkra, hogy a dokumentum tartalmával dolgozzunk.

### 5.2. A DocumentPageSplitter inicializálása

```java
DocumentPageSplitter splitter = new DocumentPageSplitter(doc);
```

 Inicializáljuk a`DocumentPageSplitter` objektumot a betöltött dokumentumunkkal. Ezt az osztályt az Aspose.Words for Java biztosítja, és segít nekünk oldalakra bontani a dokumentumot.

### 5.3. Minden oldal mentése

```java
for (int page = 1; page <= doc.getPageCount(); page++) {
    Document pageDoc = splitter.getDocumentOfPage(page);
    pageDoc.save("Your Directory Path" + MessageFormat.format("{0} - page{1}.{2}", fileName, page, extensionName));
}
```

Ebben a lépésben végigfutjuk a dokumentum minden oldalát, és elmentjük külön dokumentumként. Megadhatja a könyvtár elérési útját, ahová a felosztott oldalak mentésre kerülnek.

## 6. A kód futtatása

A kód sikeres futtatásához győződjön meg arról, hogy beállította a környezetet, és hozzáadta az Aspose.Words for Java könyvtárat a projekthez. Ezután hajtsa végre a kódot, és a dokumentum külön oldalakra oszlik.

## DocumentPageSplitter forráskód

```java
/// <összefoglaló>
/// Egy dokumentumot több dokumentumra oszt, oldalanként egyet.
/// </summary>
class DocumentPageSplitter
{
private PageNumberFinder pageNumberFinder;
/// <összefoglaló>
/// Inicializálja a <see cref="DocumentPageSplitter"/> osztály új példányát.
/// Ez a módszer szakaszokra osztja a dokumentumot úgy, hogy minden oldal egy szakaszhatárnál kezdődik és végződik.
/// Javasoljuk, hogy utólag ne módosítsa a dokumentumot.
/// </summary>
/// <param name="source">Forrásdokumentum</param>
public DocumentPageSplitter(Document source) throws Exception
{
	pageNumberFinder = PageNumberFinderFactory.create(source);
}
private Document getDocument() {
	return pageNumberFinder.getDocument();
}
/// <összefoglaló>
/// Beolvassa egy oldal dokumentumát.
/// </summary>
/// <param name="pageIndex">
/// 1 alapú oldal indexe.
/// </param>
/// <visszaad>
/// A <see cref="Dokumentum"/>.
/// </returns>
public Document getDocumentOfPage(int pageIndex) throws Exception {
	return getDocumentOfPageRange(pageIndex, pageIndex);
}
/// <összefoglaló>
//Lekéri egy oldaltartomány dokumentumát.
/// </summary>
/// <param name="startIndex">
/// A kezdőoldal 1 alapú indexe.
/// </param>
/// <param name="endIndex">
/// 1 alapú záróoldal indexe.
/// </param>
/// <visszaad>
/// A <see cref="Dokumentum"/>.
/// </returns>
public Document getDocumentOfPageRange(int startIndex, int endIndex) throws Exception {
	Document result = (Document) getDocument().deepClone(false);
	for (Node section : pageNumberFinder.retrieveAllNodesOnPages(startIndex, endIndex, NodeType.SECTION))
	{
		result.appendChild(result.importNode(section, true));
	}
	return result;
}
}
/// <összefoglaló>
/// Módszereket biztosít egy dokumentum csomópontjainak kibontására, amelyek meghatározott oldalakon jelennek meg.
/// </summary>
class PageNumberFinder
{
// Csomópontot képez le a kezdő/záró oldalszámokhoz.
// Ez a dokumentum felosztása során a gyűjtő által megadott alapoldalszámok felülbírálására szolgál.
private Map<Node, Integer> nodeStartPageLookup = new HashMap<>();
private Map<Node, Integer> nodeEndPageLookup = new HashMap<>();
private LayoutCollector collector;
// Az oldalszámot leképezi az azon az oldalon található csomópontok listájára.
private Map<Integer, ArrayList<Node>> reversePageLookup;
/// <összefoglaló>
/// Inicializálja a <see cref="PageNumberFinder"/> osztály új példányát.
/// </summary>
/// <param name="collector">Egy gyűjtőpéldány, amely elrendezési modellrekordokkal rendelkezik a dokumentumhoz.</param>
public PageNumberFinder(LayoutCollector collector)
{
	this.collector = collector;
}
public Document getDocument()
{
	return collector.getDocument();
}
/// <összefoglaló>
/// Lekéri annak az oldalnak az 1 alapú indexét, amelyen a csomópont kezdődik.
/// </summary>
/// <param name="node">
/// A csomópont.
/// </param>
/// <visszaad>
/// Oldalmutató.
/// </returns>
public int getPage(Node node) throws Exception {
	return nodeStartPageLookup.containsKey(node)
		? nodeStartPageLookup.get(node)
		: collector.getStartPageIndex(node);
}
/// <összefoglaló>
/// Lekéri annak az oldalnak az 1 alapú indexét, amelyre a csomópont véget ér.
/// </summary>
/// <param name="node">
/// A csomópont.
/// </param>
/// <visszaad>
/// Oldalmutató.
/// </returns>
public int getPageEnd(Node node) throws Exception {
	return nodeEndPageLookup.containsKey(node)
		? nodeEndPageLookup.get(node)
		: collector.getEndPageIndex(node);
}
/// <összefoglaló>
//Visszaadja, hogy a megadott csomópont hány oldalt ível át. 1-et ad vissza, ha a csomópont egy oldalon belül van.
/// </summary>
/// <param name="node">
/// A csomópont.
/// </param>
/// <visszaad>
/// Oldalmutató.
/// </returns>
public int pageSpan(Node node) throws Exception {
	return getPageEnd(node) - getPage(node) + 1;
}
/// <összefoglaló>
/// A megadott oldalon bárhol található csomópontok listáját adja vissza, vagy olyan oldalakat, amelyek megfelelnek a megadott csomóponttípusnak.
/// </summary>
/// <param name="startPage">
/// A kezdőoldal.
/// </param>
/// <param name="endPage">
/// A végoldal.
/// </param>
/// <param name="nodeType">
/// A csomópont típusa.
/// </param>
/// <visszaad>
/// A <see cref="IList{T}"/>.
/// </returns>
public ArrayList<Node> retrieveAllNodesOnPages(int startPage, int endPage, /*NodeType*/int nodeType) throws Exception
{
	if (startPage < 1 || startPage > collector.getDocument().getPageCount())
	{
		throw new IllegalStateException("'startPage' is out of range");
	}
	if (endPage < 1 || endPage > collector.getDocument().getPageCount() || endPage < startPage)
	{
		throw new IllegalStateException("'endPage' is out of range");
	}
	checkPageListsPopulated();
	ArrayList<Node> pageNodes = new ArrayList<>();
	for (int page = startPage; page <= endPage; page++)
	{
		// Néhány oldal üres lehet.
		if (!reversePageLookup.containsKey(page))
		{
			continue;
		}
		for (Node node : reversePageLookup.get(page))
		{
			if (node.getParentNode() != null
				&& (nodeType == NodeType.ANY || node.getNodeType() == nodeType)
				&& !pageNodes.contains(node))
			{
				pageNodes.add(node);
			}
		}
	}
	return pageNodes;
}
/// <összefoglaló>
/// A két vagy több oldalon megjelenő csomópontokat külön csomópontokra osztja fel, hogy továbbra is ugyanúgy jelenjenek meg
/// de már nem jelennek meg az oldalon.
/// </summary>
public void splitNodesAcrossPages() throws Exception
{
	for (Paragraph paragraph : (Iterable<Paragraph>) collector.getDocument().getChildNodes(NodeType.PARAGRAPH, true))
	{
		if (getPage(paragraph) != getPageEnd(paragraph))
		{
			splitRunsByWords(paragraph);
		}
	}
	clearCollector();
	// Látogassa meg az esetlegesen oldalakra felosztott kompozitokat, és ossza fel külön csomópontokra.
	collector.getDocument().accept(new SectionSplitter(this));
}
/// <összefoglaló>
/// Ezt a <lásd cref="SectionSplitter"/> hívja meg az osztott csomópontok oldalszámának frissítéséhez.
/// </summary>
/// <param name="node">
/// A csomópont.
/// </param>
/// <param name="startPage">
/// A kezdőoldal.
/// </param>
/// <param name="endPage">
/// A végoldal.
/// </param>
void addPageNumbersForNode(Node node, int startPage, int endPage)
{
	if (startPage > 0)
	{
		nodeStartPageLookup.put(node, startPage);
	}
	if (endPage > 0)
	{
		nodeEndPageLookup.put(node, endPage);
	}
}
private boolean isHeaderFooterType(Node node)
{
	return node.getNodeType() == NodeType.HEADER_FOOTER || node.getAncestor(NodeType.HEADER_FOOTER) != null;
}
private void checkPageListsPopulated() throws Exception {
	if (reversePageLookup != null)
	{
		return;
	}
	reversePageLookup = new HashMap<Integer, ArrayList<Node>>();
	// Adjon hozzá minden csomópontot egy listához, amely az egyes oldalakon található csomópontokat képviseli.
	for (Node node : (Iterable<Node>) collector.getDocument().getChildNodes(NodeType.ANY, true))
	{
		// fejlécek/láblécek követik a szakaszokat, és nem különülnek el egymástól.
		if (isHeaderFooterType(node))
		{
			continue;
		}
		int startPage = getPage(node);
		int endPage = getPageEnd(node);
		for (int page = startPage; page <= endPage; page++)
		{
			if (!reversePageLookup.containsKey(page))
			{
				reversePageLookup.put(page, new ArrayList<Node>());
			}
			reversePageLookup.get(page).add(node);
		}
	}
}
private void splitRunsByWords(Paragraph paragraph) throws Exception {
	for (Run run : paragraph.getRuns())
	{
		if (getPage(run) == getPageEnd(run))
		{
			continue;
		}
		splitRunByWords(run);
	}
}
private void splitRunByWords(Run run)
{
	String[] words = reverseWord(run.getText());
	for (String word : words)
	{
		int pos = run.getText().length() - word.length() - 1;
		if (pos > 1)
		{
			splitRun(run, run.getText().length() - word.length() - 1);
		}
	}
}
private static String[] reverseWord(String str) {
	String words[] = str.split(" ");
	String reverseWord = "";
	for (String w : words) {
		StringBuilder sb = new StringBuilder(w);
		sb.reverse();
		reverseWord += sb.toString() + " ";
	}
	return reverseWord.split(" ");
}
/// <összefoglaló>
/// A megadott futás szövegét két futtatásra osztja.
/// Közvetlenül a megadott futás után beszúrja az új futást.
/// </summary>
private void splitRun(Run run, int position)
{
	Run afterRun = (Run) run.deepClone(true);
	afterRun.setText(run.getText().substring(position));
	run.setText(run.getText().substring((0), (0) + (position)));
	run.getParentNode().insertAfter(afterRun, run);
}
private void clearCollector() throws Exception
{
	collector.clear();
	collector.getDocument().updatePageLayout();
	nodeStartPageLookup.clear();
	nodeEndPageLookup.clear();
}
}
class PageNumberFinderFactory
{
public static PageNumberFinder create(Document document) throws Exception
{
	LayoutCollector layoutCollector = new LayoutCollector(document);
	document.updatePageLayout();
	PageNumberFinder pageNumberFinder = new PageNumberFinder(layoutCollector);
	pageNumberFinder.splitNodesAcrossPages();
	return pageNumberFinder;
}
}
/// <összefoglaló>
/// Egy dokumentumot több részre oszt fel úgy, hogy minden oldal egy szakaszhatárnál kezdődik és végződik.
/// </summary>
class SectionSplitter extends DocumentVisitor
{
private PageNumberFinder pageNumberFinder;
public SectionSplitter(PageNumberFinder pageNumberFinder)
{
	this.pageNumberFinder = pageNumberFinder;
}
public int visitParagraphStart(Paragraph paragraph) throws Exception {
	return continueIfCompositeAcrossPageElseSkip(paragraph);
}
public int visitTableStart(Table table) throws Exception {
	return continueIfCompositeAcrossPageElseSkip(table);
}
public int visitRowStart(Row row) throws Exception {
	return continueIfCompositeAcrossPageElseSkip(row);
}
public int visitCellStart(Cell cell) throws Exception {
	return continueIfCompositeAcrossPageElseSkip(cell);
}
public int visitStructuredDocumentTagStart(StructuredDocumentTag sdt) throws Exception {
	return continueIfCompositeAcrossPageElseSkip(sdt);
}
public int visitSmartTagStart(SmartTag smartTag) throws Exception {
	return continueIfCompositeAcrossPageElseSkip(smartTag);
}
public int visitSectionStart(Section section) throws Exception {
	Section previousSection = (Section) section.getPreviousSibling();
	// Ha van egy korábbi szakasz, próbálja meg másolni a hivatkozott fejléc lábléceit.
	// Ellenkező esetben nem jelennek meg a kibontott dokumentumban, ha az előző rész hiányzik.
	if (previousSection != null)
	{
		HeaderFooterCollection previousHeaderFooters = previousSection.getHeadersFooters();
		if (!section.getPageSetup().getRestartPageNumbering())
		{
			section.getPageSetup().setRestartPageNumbering(true);
			section.getPageSetup().setPageStartingNumber(previousSection.getPageSetup().getPageStartingNumber() +
												   pageNumberFinder.pageSpan(previousSection));
		}
		for (HeaderFooter previousHeaderFooter : (Iterable<HeaderFooter>) previousHeaderFooters)
		{
			if (section.getHeadersFooters().getByHeaderFooterType(previousHeaderFooter.getHeaderFooterType()) == null)
			{
				HeaderFooter newHeaderFooter =
					(HeaderFooter) previousHeaderFooters.getByHeaderFooterType(previousHeaderFooter.getHeaderFooterType()).deepClone(true);
				section.getHeadersFooters().add(newHeaderFooter);
			}
		}
	}
	return continueIfCompositeAcrossPageElseSkip(section);
}
public int visitSmartTagEnd(SmartTag smartTag) throws Exception {
	splitComposite(smartTag);
	return VisitorAction.CONTINUE;
}
public int visitStructuredDocumentTagEnd(StructuredDocumentTag sdt) throws Exception {
	splitComposite(sdt);
	return VisitorAction.CONTINUE;
}
public int visitCellEnd(Cell cell) throws Exception {
	splitComposite(cell);
	return VisitorAction.CONTINUE;
}
public int visitRowEnd(Row row) throws Exception {
	splitComposite(row);
	return VisitorAction.CONTINUE;
}
public int visitTableEnd(Table table) throws Exception {
	splitComposite(table);
	return VisitorAction.CONTINUE;
}
public int visitParagraphEnd(Paragraph paragraph) throws Exception {
	// Ha a bekezdés csak szakasztörést tartalmaz, adjon hozzá hamis befutást.
	if (paragraph.isEndOfSection() && paragraph.getChildNodes().getCount() == 1 &&
		"\f".equals(paragraph.getChildNodes().get(0).getText()))
	{
		Run run = new Run(paragraph.getDocument());
		paragraph.appendChild(run);
		int currentEndPageNum = pageNumberFinder.getPageEnd(paragraph);
		pageNumberFinder.addPageNumbersForNode(run, currentEndPageNum, currentEndPageNum);
	}
	for (Node cloneNode : splitComposite(paragraph))
	{
		Paragraph clonePara = (Paragraph) cloneNode;
		// Távolítsa el a listaszámozást a klónozott bekezdésből, de a behúzást hagyja változatlan
		// mivel a bekezdésnek az előző tétel részét kell képeznie.
		if (paragraph.isListItem())
		{
			double textPosition = clonePara.getListFormat().getListLevel().getTextPosition();
			clonePara.getListFormat().removeNumbers();
			clonePara.getParagraphFormat().setLeftIndent(textPosition);
		}
		// Állítsa alaphelyzetbe a felosztott bekezdések térközét a táblázatokban, mivel a további szóközök miatt eltérő megjelenésűek lehetnek.
		if (paragraph.isInCell())
		{
			clonePara.getParagraphFormat().setSpaceBefore(0.0);
			paragraph.getParagraphFormat().setSpaceAfter(0.0);
		}
	}
	return VisitorAction.CONTINUE;
}
public int visitSectionEnd(Section section) throws Exception {
	for (Node cloneNode : splitComposite(section))
	{
		Section cloneSection = (Section) cloneNode;
		cloneSection.getPageSetup().setSectionStart(SectionStart.NEW_PAGE);
		cloneSection.getPageSetup().setRestartPageNumbering(true);
		cloneSection.getPageSetup().setPageStartingNumber(section.getPageSetup().getPageStartingNumber() +
													(section.getDocument().indexOf(cloneSection) -
													 section.getDocument().indexOf(section)));
		cloneSection.getPageSetup().setDifferentFirstPageHeaderFooter(false);
		// Javítja az oldaltörést a szakasz végén.
		SplitPageBreakCorrector.processSection(cloneSection);
	}
	SplitPageBreakCorrector.processSection(section);
	// Adjon hozzá új oldalszámozást a szakasz törzséhez is.
	pageNumberFinder.addPageNumbersForNode(section.getBody(), pageNumberFinder.getPage(section),
		pageNumberFinder.getPageEnd(section));
	return VisitorAction.CONTINUE;
}
private /*VisitorAction*/int continueIfCompositeAcrossPageElseSkip(CompositeNode composite) throws Exception {
	return pageNumberFinder.pageSpan(composite) > 1
		? VisitorAction.CONTINUE
		: VisitorAction.SKIP_THIS_NODE;
}
private ArrayList<Node> splitComposite(CompositeNode composite) throws Exception {
	ArrayList<Node> splitNodes = new ArrayList<>();
	for (Node splitNode : findChildSplitPositions(composite))
	{
		splitNodes.add(splitCompositeAtNode(composite, splitNode));
	}
	return splitNodes;
}
private Iterable<Node> findChildSplitPositions(CompositeNode node) throws Exception {
	// Egy csomópont több oldalon is átnyúlhat, ezért a rendszer a felosztott pozíciók listáját adja vissza.
	// felosztott csomópont az első csomópont a következő oldalon.
	ArrayList<Node> splitList = new ArrayList<Node>();
	int startingPage = pageNumberFinder.getPage(node);
	Node[] childNodes = node.getNodeType() == NodeType.SECTION
		? ((Section) node).getBody().getChildNodes().toArray()
		: node.getChildNodes().toArray();
	for (Node childNode : childNodes)
	{
		int pageNum = pageNumberFinder.getPage(childNode);
		if (childNode instanceof Run)
		{
			pageNum = pageNumberFinder.getPageEnd(childNode);
		}
		// Ha a gyermek csomópont oldala megváltozott, akkor ez a felosztási pozíció.
		// Adja hozzá ezt a listához.
		if (pageNum > startingPage)
		{
			splitList.add(childNode);
			startingPage = pageNum;
		}
		if (pageNumberFinder.pageSpan(childNode) > 1)
		{
			pageNumberFinder.addPageNumbersForNode(childNode, pageNum, pageNum);
		}
	}
	// A kompozitokat hátrafelé ossza fel, így a klónozott csomópontok a megfelelő sorrendben kerülnek beillesztésre.
	Collections.reverse(splitList);
	return splitList;
}
private CompositeNode splitCompositeAtNode(CompositeNode baseNode, Node targetNode) throws Exception {
	CompositeNode cloneNode = (CompositeNode) baseNode.deepClone(false);
	Node node = targetNode;
	int currentPageNum = pageNumberFinder.getPage(baseNode);
	// Helyezze át a következő oldalon található összes csomópontot a másolt csomópontba. A sor csomópontjait külön kezelje.
	if (baseNode.getNodeType() != NodeType.ROW)
	{
		CompositeNode composite = cloneNode;
		if (baseNode.getNodeType() == NodeType.SECTION)
		{
			cloneNode = (CompositeNode) baseNode.deepClone(true);
			Section section = (Section) cloneNode;
			section.getBody().removeAllChildren();
			composite = section.getBody();
		}
		while (node != null)
		{
			Node nextNode = node.getNextSibling();
			composite.appendChild(node);
			node = nextNode;
		}
	}
	else
	{
		// Ha sorral van dolgunk, akkor a klónozott sorhoz dummy cellákat kell hozzáadnunk.
		int targetPageNum = pageNumberFinder.getPage(targetNode);
		Node[] childNodes = baseNode.getChildNodes().toArray();
		for (Node childNode : childNodes)
		{
			int pageNum = pageNumberFinder.getPage(childNode);
			if (pageNum == targetPageNum)
			{
				if (cloneNode.getNodeType() == NodeType.ROW)
					((Row) cloneNode).ensureMinimum();
				if (cloneNode.getNodeType() == NodeType.CELL)
					((Cell) cloneNode).ensureMinimum();
				cloneNode.getLastChild().remove();
				cloneNode.appendChild(childNode);
			}
			else if (pageNum == currentPageNum)
			{
				cloneNode.appendChild(childNode.deepClone(false));
				if (cloneNode.getLastChild().getNodeType() != NodeType.CELL)
				{
					((CompositeNode) cloneNode.getLastChild()).appendChild(
						((CompositeNode) childNode).getFirstChild().deepClone(false));
				}
			}
		}
	}
	// Helyezze be az osztott csomópontot az eredeti után.
	baseNode.getParentNode().insertAfter(cloneNode, baseNode);
	// Frissítse az alapcsomópont és a klónozott csomópont új oldalszámait, beleértve a leszármazottait is.
	// Ez csak egyetlen oldal lesz, mivel a klónozott kompozit egy oldalra van felosztva.
	int currentEndPageNum = pageNumberFinder.getPageEnd(baseNode);
	pageNumberFinder.addPageNumbersForNode(baseNode, currentPageNum, currentEndPageNum - 1);
	pageNumberFinder.addPageNumbersForNode(cloneNode, currentEndPageNum, currentEndPageNum);
	for (Node childNode : (Iterable<Node>) cloneNode.getChildNodes(NodeType.ANY, true))
	{
		pageNumberFinder.addPageNumbersForNode(childNode, currentEndPageNum, currentEndPageNum);
	}
	return cloneNode;
}
}

class SplitPageBreakCorrector
{
private static final String PAGE_BREAK_STR = "\f";
private static final char PAGE_BREAK = '\f';
public static void processSection(Section section)
{
	if (section.getChildNodes().getCount() == 0)
	{
		return;
	}
	Body lastBody = (Body) Arrays.stream(new Iterator[]{section.getChildNodes().iterator()}).reduce((first, second) -> second)
		.orElse(null);
	RunCollection runs = (RunCollection) lastBody.getChildNodes(NodeType.RUN, true).iterator();
	Run run  = Arrays.stream(runs.toArray()).filter(p -> p.getText().endsWith(PAGE_BREAK_STR)).findFirst().get();
	if (run != null)
	{
		removePageBreak(run);
	}
}
public void removePageBreakFromParagraph(Paragraph paragraph)
{
	Run run = (Run) paragraph.getFirstChild();
	if (PAGE_BREAK_STR.equals(run.getText()))
	{
		paragraph.removeChild(run);
	}
}
private void processLastParagraph(Paragraph paragraph)
{
	Node lastNode = paragraph.getChildNodes().get(paragraph.getChildNodes().getCount() - 1);
	if (lastNode.getNodeType() != NodeType.RUN)
	{
		return;
	}
	Run run = (Run) lastNode;
	removePageBreak(run);
}
private static void removePageBreak(Run run)
{
	Paragraph paragraph = run.getParentParagraph();
	if (PAGE_BREAK_STR.equals(run.getText()))
	{
		paragraph.removeChild(run);
	}
	else if (run.getText().endsWith(PAGE_BREAK_STR))
	{
		run.setText(StringUtils.stripEnd(run.getText(), String.valueOf(PAGE_BREAK)));
	}
	if (paragraph.getChildNodes().getCount() == 0)
	{
		CompositeNode parent = paragraph.getParentNode();
		parent.removeChild(paragraph);
	}
}
}
```

## Következtetés

Most megtanulta, hogyan lehet egy dokumentumot külön oldalakra osztani az Aspose.Words for Java segítségével. Ez az útmutató egy átfogó, lépésről lépésre bemutatott oktatóanyagot tartalmaz forráskód-példákkal. Tovább szabhatja és kibővítheti ezt a kódot, hogy megfeleljen a dokumentumokkal végzett munka során felmerülő speciális követelményeknek.
Biztosan! Adjunk hozzá egy GYIK részt az útmutatónkhoz, amely az Aspose.Words for Java használatával oldalakra bontja a dokumentumokat.

## GYIK

### Hogyan adhatom hozzá az Aspose.Words for Java fájlt a projektemhez?

Az Aspose.Words for Java projekthez való hozzáadásához kövesse az alábbi lépéseket:

1.  Töltse le az Aspose.Words for Java könyvtárat innen[itt](https://releases.aspose.com/words/java/).
2. Adja hozzá a letöltött JAR-fájlt a projekt osztályútvonalához.
3. Most már használhatja az Aspose.Words for Java programot a projektben.

### Feloszthatok más formátumú dokumentumokat, például PDF vagy DOCX?

Nem, ez az útmutató kifejezetten a DOC formátumú dokumentumok felosztására vonatkozik az Aspose.Words for Java használatával. Ha más formátumú dokumentumokat kell felosztania, előfordulhat, hogy más könyvtárakat vagy eszközöket kell felfedeznie, amelyek támogatják ezeket a formátumokat.

### Az Aspose.Words for Java egy ingyenes könyvtár?

 Nem, az Aspose.Words for Java nem ingyenes könyvtár. Ez egy kereskedelmi termék, licencdíjjal. Meglátogathatja a[Aspose.Words for Java árképzési oldal](https://purchase.aspose.com/words/java) az engedélyezéssel és az árakkal kapcsolatos további információkért.

### Feloszthatom a dokumentumokat egyéni oldalméretekre és -formátumokra?

Igen, testreszabhatja a felosztott dokumentumok oldalméretét és formátumát az Aspose.Words for Java oldalbeállítási tulajdonságainak módosításával. Tekintse meg az Aspose.Words dokumentációját az oldalbeállítások igényeinek megfelelő testreszabásával kapcsolatos részletekért.

### Van-e korlátozás a felosztható oldalak számára?

Az Aspose.Words for Java nem ír elő konkrét korlátozásokat a felosztható oldalak számára. Ne feledje azonban, hogy a nagyon nagy dokumentumok több memóriát és feldolgozási időt igényelhetnek. Ha nagy dokumentumokkal dolgozik, ügyeljen a rendszererőforrásokra.

### Hogyan kezelhetem a fejléceket és a lábléceket a dokumentumok felosztása során?

fejlécek és láblécek a dokumentumok felosztása során kezelhetők az Aspose.Words for Java könyvtár használatával. A fejléc és lábléc tartalmát átmásolhatja az eredeti dokumentumból a felosztott dokumentumokba, biztosítva azok megfelelő megőrzését. Előfordulhat, hogy ezt a folyamatot testre kell szabnia az adott fejléc- és lábléc-követelmények alapján.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
