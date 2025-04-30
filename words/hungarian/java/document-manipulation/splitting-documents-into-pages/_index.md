---
"description": "Tanuld meg, hogyan oszthatod fel a dokumentumokat oldalakra az Aspose.Words for Java használatával. Lépésről lépésre útmutató forráskóddal a hatékony dokumentumfeldolgozáshoz."
"linktitle": "Dokumentumok oldalakra osztása"
"second_title": "Aspose.Words Java dokumentumfeldolgozó API"
"title": "Dokumentumok oldalakra osztása az Aspose.Words for Java programban"
"url": "/hu/java/document-manipulation/splitting-documents-into-pages/"
"weight": 23
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Dokumentumok oldalakra osztása az Aspose.Words for Java programban


Ha Java nyelven dolgozol dokumentumfeldolgozással, az Aspose.Words for Java egy hatékony API, amely segíthet a dokumentumok hatékony felosztásában különálló oldalakra. Ebben a lépésről lépésre bemutató útmutatóban végigvezetünk a dokumentumok felosztásának folyamatán a mellékelt forráskód segítségével. A bemutató végére könnyedén feloszthatod a dokumentumokat, javítva ezzel a dokumentumkezelési képességeidet.

## 1. Bevezetés

Az Aspose.Words for Java egy Java könyvtár, amely lehetővé teszi a Word dokumentumok programozott kezelését. Az egyik gyakori feladat a dokumentumok különálló oldalakra osztása, ami hasznos lehet különféle célokra, például archiválásra, nyomtatásra vagy dokumentumfeldolgozásra.

## 2. Előfeltételek

Mielőtt belemerülnénk a kódba, győződjünk meg arról, hogy a következő előfeltételek teljesülnek:

- Java fejlesztőkészlet (JDK) telepítve van a rendszerére.
- Aspose.Words Java könyvtárhoz, amely letölthető [itt](https://releases.aspose.com/words/java/).

## 3. A környezet beállítása

A kezdéshez állítsa be a fejlesztői környezetet az alábbiak szerint:

- Hozz létre egy Java projektet a kívánt integrált fejlesztői környezetben (IDE).
- Add hozzá az Aspose.Words for Java könyvtárat a projektedhez. A következőre hivatkozhatsz: [dokumentáció](https://reference.aspose.com/words/java/) részletes utasításokért.

## 4. A forráskód megértése

A megadott forráskód úgy lett kialakítva, hogy egy dokumentumot különálló oldalakra osszon. Nézzük meg a főbb összetevőket:

```java
String fileName = FilenameUtils.getBaseName(docName);
String extensionName = FilenameUtils.getExtension(docName);
System.out.println("Processing document: " + fileName + "." + extensionName);
Document doc = new Document(docName);
```

- Kinyerjük a bemeneti dokumentum alapnevét és kiterjesztését.
- A dokumentumot az Aspose.Words for Java használatával töltjük be.

## 5. Dokumentumok felosztása lépésről lépésre

### 5.1. A dokumentum betöltése

```java
Document doc = new Document(docName);
```

Ebben a lépésben betöltjük a bemeneti dokumentumot egy `Document` objektum, amely lehetővé teszi számunkra, hogy a dokumentum tartalmával dolgozzunk.

### 5.2. A DocumentPageSplitter inicializálása

```java
DocumentPageSplitter splitter = new DocumentPageSplitter(doc);
```

Inicializálunk egy `DocumentPageSplitter` objektumot a betöltött dokumentumunkkal. Ezt az osztályt az Aspose.Words for Java biztosítja, és segít a dokumentum oldalakra osztásában.

### 5.3. Az egyes oldalak mentése

```java
for (int page = 1; page <= doc.getPageCount(); page++) {
    Document pageDoc = splitter.getDocumentOfPage(page);
    pageDoc.save("Your Directory Path" + MessageFormat.format("{0} - page{1}.{2}", fileName, page, extensionName));
}
```

Ebben a lépésben végigmegyünk a dokumentum minden egyes oldalán, és külön dokumentumként mentjük el azokat. Megadhatja a könyvtár elérési útját, ahová a felosztott oldalak mentésre kerülnek.

## 6. A kód futtatása

A kód sikeres futtatásához győződj meg róla, hogy beállítottad a környezetet, és hozzáadtad az Aspose.Words for Java könyvtárat a projektedhez. Ezután futtasd a kódot, és a dokumentumod külön oldalakra lesz osztva.

## DocumentPageSplitter forráskód

```java
/// <összefoglaló>
/// Egy dokumentumot több dokumentumra oszt fel, oldalanként egyet.
/// </összefoglaló>
class DocumentPageSplitter
{
private PageNumberFinder pageNumberFinder;
/// <összefoglaló>
/// Inicializálja a <see cref="DocumentPageSplitter"/> osztály egy új példányát.
/// Ez a metódus részekre osztja a dokumentumot úgy, hogy minden oldal egy szakaszhatárnál kezdődik és végződik.
/// Nem ajánlott utólag módosítani a dokumentumot.
/// </összefoglaló>
/// <param name="source">Forrásdokumentum</param>
public DocumentPageSplitter(Document source) throws Exception
{
	pageNumberFinder = PageNumberFinderFactory.create(source);
}
private Document getDocument() {
	return pageNumberFinder.getDocument();
}
/// <összefoglaló>
/// Lekéri egy oldal dokumentumát.
/// </összefoglaló>
/// <param name="oldalIndex">
/// Egy oldal 1-alapú indexe.
/// </param>
/// <visszaadási érték>
/// A <see cref="Dokumentum"/>.
/// </returns>
public Document getDocumentOfPage(int pageIndex) throws Exception {
	return getDocumentOfPageRange(pageIndex, pageIndex);
}
/// <összefoglaló>
/// Lekéri egy oldaltartomány dokumentumát.
/// </összefoglaló>
/// <param name="startIndex">
/// A kezdőlap 1-alapú indexe.
/// </param>
//<param name="endIndex">
/// A záróoldal 1-alapú indexe.
/// </param>
/// <visszaadási érték>
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
/// Metódusokat biztosít egy dokumentum azon csomópontjainak kinyerésére, amelyek egy megadott oldalon jelennek meg.
/// </összefoglaló>
class PageNumberFinder
{
// A csomópontot egy kezdő/záró oldalszámhoz rendeli.
// Ez a gyűjtő által megadott alap oldalszámok felülbírálására szolgál a dokumentum felosztásakor.
private Map<Node, Integer> nodeStartPageLookup = new HashMap<>();
private Map<Node, Integer> nodeEndPageLookup = new HashMap<>();
private LayoutCollector collector;
// Az oldalszámot az adott oldalon található csomópontok listájához rendeli.
private Map<Integer, ArrayList<Node>> reversePageLookup;
/// <összefoglaló>
/// Inicializálja a <see cref="PageNumberFinder"/> osztály egy új példányát.
/// </összefoglaló>
/// <param name="collector">Egy gyűjtőpéldány, amely elrendezési modellrekordokat tartalmaz a dokumentumhoz.</param>
public PageNumberFinder(LayoutCollector collector)
{
	this.collector = collector;
}
public Document getDocument()
{
	return collector.getDocument();
}
/// <összefoglaló>
/// Lekéri annak az oldalnak az 1-alapú indexét, amelyen a csomópont kezdődik.
/// </összefoglaló>
/// <paraméter neve="csomópont">
/// A csomópont.
/// </param>
/// <visszaadási érték>
/// Oldalindex.
/// </returns>
public int getPage(Node node) throws Exception {
	return nodeStartPageLookup.containsKey(node)
		? nodeStartPageLookup.get(node)
		: collector.getStartPageIndex(node);
}
/// <összefoglaló>
/// Lekéri annak az oldalnak az 1-alapú indexét, amelyen a csomópont végződik.
/// </összefoglaló>
/// <paraméter neve="csomópont">
/// A csomópont.
/// </param>
/// <visszaadási érték>
/// Oldalindex.
/// </returns>
public int getPageEnd(Node node) throws Exception {
	return nodeEndPageLookup.containsKey(node)
		? nodeEndPageLookup.get(node)
		: collector.getEndPageIndex(node);
}
/// <összefoglaló>
/// Visszaadja, hogy a megadott csomópont hány oldalt foglal magában. 1-et ad vissza, ha a csomópont egy oldalon belül található.
/// </összefoglaló>
/// <paraméter neve="csomópont">
/// A csomópont.
/// </param>
/// <visszaadási érték>
/// Oldalindex.
/// </returns>
public int pageSpan(Node node) throws Exception {
	return getPageEnd(node) - getPage(node) + 1;
}
/// <összefoglaló>
/// Visszaadja a megadott oldalon vagy oldalakon bárhol található, a megadott csomóponttípusnak megfelelő csomópontok listáját.
/// </összefoglaló>
/// <param name="kezdőoldal">
/// A kezdőlap.
/// </param>
/// <param name="oldal vége">
/// Az utolsó oldal.
/// </param>
/// <paraméter neve="csomópontTípus">
/// A csomópont típusa.
/// </param>
/// <visszaadási érték>
/// A <see cref="IList{T}"/>.
/// </returns>
public ArrayList<Node> retrieveAllNodesOnPages(int startPage, int endPage, /*Csomóponttípus*/int nodeType) throws Exception
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
/// A két vagy több oldalon megjelenő csomópontokat különálló csomópontokra osztja, hogy azok továbbra is ugyanúgy jelenjenek meg
/// de már nem jelennek meg egy oldalon keresztül.
/// </összefoglaló>
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
	// Látogasson el minden olyan összetett elemre, amely esetleg több oldalra van osztva, és ossza fel őket különálló csomópontokra.
	collector.getDocument().accept(new SectionSplitter(this));
}
/// <összefoglaló>
/// Ezt a <see cref="SectionSplitter"/> hívja meg a felosztott csomópontok oldalszámainak frissítéséhez.
/// </összefoglaló>
/// <paraméter neve="csomópont">
/// A csomópont.
/// </param>
/// <param name="kezdőoldal">
/// A kezdőlap.
/// </param>
/// <param name="oldal vége">
/// Az utolsó oldal.
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
	// Adja hozzá az egyes csomópontokat egy listához, amely az egyes oldalakon található csomópontokat jelöli.
	for (Node node : (Iterable<Node>) collector.getDocument().getChildNodes(NodeType.ANY, true))
	{
		// A fejlécek/láblécek szakaszokat követnek, és önmagukban nem oszlanak el.
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
/// A megadott futtatás szövegét két futtatásra osztja.
/// Az új futtatást közvetlenül a megadott futtatás után szúrja be.
/// </összefoglaló>
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
/// </összefoglaló>
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
	// Ha van egy korábbi szakasz, próbálja meg lemásolni a hivatkozott fejléc-lábléceket.
	// Ellenkező esetben nem jelennek meg a kinyert dokumentumban, ha az előző szakasz hiányzik.
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
	// Ha a bekezdés csak szakasztörést tartalmaz, adj hozzá álbefejezést.
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
		// A klónozott bekezdés listaszámozásának eltávolítása a behúzás változatlanul hagyásával 
		// mivel a bekezdésnek az előző elem részének kellene lennie.
		if (paragraph.isListItem())
		{
			double textPosition = clonePara.getListFormat().getListLevel().getTextPosition();
			clonePara.getListFormat().removeNumbers();
			clonePara.getParagraphFormat().setLeftIndent(textPosition);
		}
		// Állítsa vissza a táblázatokban a bekezdések közötti térközt, mivel a további térközök eltérő megjelenést okozhatnak.
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
		// Kijavítja az oldaltörést a szakasz végén.
		SplitPageBreakCorrector.processSection(cloneSection);
	}
	SplitPageBreakCorrector.processSection(section);
	// Adjon hozzá új oldalszámozást a szakasz törzséhez is.
	pageNumberFinder.addPageNumbersForNode(section.getBody(), pageNumberFinder.getPage(section),
		pageNumberFinder.getPageEnd(section));
	return Látogatói művelet.CONTINUE;
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
	// Egy csomópont több oldalra is kiterjedhet, így a felosztott pozíciók listája kerül visszaadásra.
	// A szétválasztott csomópont az első csomópont a következő oldalon.
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
		// Ha a gyermekcsomópont oldala megváltozott, akkor ez a felosztási pozíció.
		// Add hozzá ezt a listához.
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
	// A kompozitokat visszafelé bontja szét, hogy a klónozott csomópontok a megfelelő sorrendben kerüljenek beillesztésre.
	Collections.reverse(splitList);
	return splitList;
}
private CompositeNode splitCompositeAtNode(CompositeNode baseNode, Node targetNode) throws Exception {
	CompositeNode cloneNode = (CompositeNode) baseNode.deepClone(false);
	Node node = targetNode;
	int currentPageNum = pageNumberFinder.getPage(baseNode);
	// Helyezze át a következő oldalon található összes csomópontot a másolt csomópontba. A sorcsomópontokat külön kezelje.
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
		// Ha egy sorral foglalkozunk, akkor hozzá kell adnunk a klónozott sorhoz tartozó üres cellákat.
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
	// Illeszd be az elválasztott csomópontot az eredeti után.
	baseNode.getParentNode().insertAfter(cloneNode, baseNode);
	// Frissítse az alapcsomópont és a klónozott csomópont új oldalszámait, beleértve a leszármazottait is.
	// Ez csak egyetlen oldal lesz, mivel a klónozott kompozit egy oldalra van osztva.
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

Most már megtanultad, hogyan oszthatsz fel egy dokumentumot különálló oldalakra az Aspose.Words for Java segítségével. Ez az útmutató egy átfogó, lépésről lépésre bemutatott oktatóanyagot tartalmaz forráskódpéldákkal. A kódot tovább testreszabhatod és bővítheted, hogy megfeleljen az igényeidnek a dokumentumokkal való munka során.
Természetesen! Adjunk hozzá egy GYIK részt az Aspose.Words for Java használatával dokumentumok oldalakra osztásáról szóló útmutatónkhoz.

## GYIK

### Hogyan adhatom hozzá az Aspose.Words for Java-t a projektemhez?

Az Aspose.Words for Java hozzáadásához a projektedhez kövesd az alábbi lépéseket:

1. Töltsd le az Aspose.Words for Java könyvtárat innen: [itt](https://releases.aspose.com/words/java/).
2. Adja hozzá a letöltött JAR fájlt a projekt osztályútvonalához.
3. Most már elkezdheti használni az Aspose.Words for Java-t a projektjében.

### Feloszthatom a dokumentumokat más formátumokban, például PDF-ben vagy DOCX-ben?

Nem, ez az útmutató kifejezetten a DOC formátumú dokumentumok Aspose.Words for Java használatával történő felosztását tárgyalja. Ha más formátumú dokumentumokat kell felosztania, érdemes lehet más, ezeket a formátumokat támogató könyvtárakat vagy eszközöket is megvizsgálnia.

### Az Aspose.Words for Java egy ingyenes könyvtár?

Nem, az Aspose.Words for Java nem egy ingyenes könyvtár. Ez egy kereskedelmi termék, licencdíj ellenében. Meglátogathatja a következőt: [Aspose.Words Java-hoz – árképzési oldal](https://purchase.aspose.com/words/java) további információkért a licencelésről és az árakról.

### Feloszthatom a dokumentumokat egyéni oldalméretek és formátumok szerint?

Igen, testreszabhatja a felosztott dokumentumok oldalméreteit és formátumait az Aspose.Words for Java oldalbeállítási tulajdonságainak módosításával. Az Aspose.Words dokumentációjában részletesen tájékozódhat arról, hogyan testreszabhatja az oldalbeállításokat az igényeinek megfelelően.

### Vannak-e korlátozások a felosztható oldalak számára vonatkozóan?

Az Aspose.Words for Java nem szab meg konkrét korlátozásokat a felosztható oldalak számára vonatkozóan. Ne feledje azonban, hogy a nagyon nagy dokumentumok több memóriát és feldolgozási időt igényelhetnek. Nagy dokumentumokkal való munka során ügyeljen a rendszer erőforrásaira.

### Hogyan kezelhetem a fejléceket és lábléceket dokumentumok felosztásakor?

A fejlécek és láblécek kezelése dokumentumok felosztásakor az Aspose.Words for Java könyvtár segítségével lehetséges. A fejléc és lábléc tartalmát átmásolhatja az eredeti dokumentumból a felosztott dokumentumokba, biztosítva azok megfelelő megőrzését. Előfordulhat, hogy ezt a folyamatot a fejléc és lábléc igényei alapján kell testre szabnia.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}