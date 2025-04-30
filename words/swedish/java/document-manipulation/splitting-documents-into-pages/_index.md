---
"description": "Lär dig hur du delar upp dokument i sidor med Aspose.Words för Java. Steg-för-steg-guide med källkod för effektiv dokumenthantering."
"linktitle": "Dela upp dokument i sidor"
"second_title": "Aspose.Words Java-dokumentbehandlings-API"
"title": "Dela upp dokument i sidor i Aspose.Words för Java"
"url": "/sv/java/document-manipulation/splitting-documents-into-pages/"
"weight": 23
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Dela upp dokument i sidor i Aspose.Words för Java


Om du arbetar med dokumenthantering i Java är Aspose.Words för Java ett kraftfullt API som kan hjälpa dig att dela upp dokument i separata sidor effektivt. I den här steg-för-steg-handledningen guidar vi dig genom processen att dela dokument med hjälp av den medföljande källkoden. I slutet av handledningen kommer du att kunna dela upp dokument med lätthet och förbättra dina dokumenthanteringsfunktioner.

## 1. Introduktion

Aspose.Words för Java är ett Java-bibliotek som låter dig manipulera Word-dokument programmatiskt. En vanlig uppgift är att dela upp ett dokument i separata sidor, vilket kan vara användbart för olika ändamål, till exempel arkivering, utskrift eller dokumentbehandling.

## 2. Förkunskapskrav

Innan vi går in i koden, se till att du har följande förutsättningar på plats:

- Java Development Kit (JDK) installerat på ditt system.
- Aspose.Words för Java-biblioteket, som du kan ladda ner [här](https://releases.aspose.com/words/java/).

## 3. Konfigurera din miljö

För att komma igång, konfigurera din utvecklingsmiljö enligt följande:

- Skapa ett Java-projekt i din föredragna integrerade utvecklingsmiljö (IDE).
- Lägg till Aspose.Words för Java-biblioteket i ditt projekt. Du kan referera till [dokumentation](https://reference.aspose.com/words/java/) för detaljerade instruktioner.

## 4. Förstå källkoden

Källkoden du angav är utformad för att dela upp ett dokument i separata sidor. Låt oss bryta ner de viktigaste komponenterna:

```java
String fileName = FilenameUtils.getBaseName(docName);
String extensionName = FilenameUtils.getExtension(docName);
System.out.println("Processing document: " + fileName + "." + extensionName);
Document doc = new Document(docName);
```

- Vi extraherar basnamnet och tillägget för indatadokumentet.
- Vi laddar dokumentet med hjälp av Aspose.Words för Java.

## 5. Dela dokument steg för steg

### 5.1. Läsa in dokumentet

```java
Document doc = new Document(docName);
```

I det här steget laddar vi inmatningsdokumentet till en `Document` objekt, vilket låter oss arbeta med dokumentets innehåll.

### 5.2. Initiera DocumentPageSplitter

```java
DocumentPageSplitter splitter = new DocumentPageSplitter(doc);
```

Vi initierar en `DocumentPageSplitter` objekt med vårt laddade dokument. Den här klassen tillhandahålls av Aspose.Words för Java och hjälper oss att dela upp dokumentet i sidor.

### 5.3. Spara varje sida

```java
for (int page = 1; page <= doc.getPageCount(); page++) {
    Document pageDoc = splitter.getDocumentOfPage(page);
    pageDoc.save("Your Directory Path" + MessageFormat.format("{0} - page{1}.{2}", fileName, page, extensionName));
}
```

I det här steget itererar vi igenom varje sida i dokumentet och sparar det som ett separat dokument. Du kan ange sökvägen till katalogen där de delade sidorna ska sparas.

## 6. Köra koden

För att köra den här koden korrekt, se till att du har konfigurerat din miljö och lagt till Aspose.Words för Java-biblioteket i ditt projekt. Kör sedan koden så att ditt dokument är uppdelat i separata sidor.

## Källkod för DocumentPageSplitter

```java
/// <sammanfattning>
/// Delar upp ett dokument i flera dokument, ett per sida.
/// </sammanfattning>
class DocumentPageSplitter
{
private PageNumberFinder pageNumberFinder;
/// <sammanfattning>
/// Initierar en ny instans av <see cref="DocumentPageSplitter"/>-klassen.
/// Den här metoden delar upp dokumentet i avsnitt så att varje sida börjar och slutar vid en avsnittsgräns.
/// Det rekommenderas att inte ändra dokumentet i efterhand.
/// </sammanfattning>
/// <param name="source">Källdokument</param>
public DocumentPageSplitter(Document source) throws Exception
{
	pageNumberFinder = PageNumberFinderFactory.create(source);
}
private Document getDocument() {
	return pageNumberFinder.getDocument();
}
/// <sammanfattning>
/// Hämtar dokumentet för en sida.
/// </sammanfattning>
/// <param namn="sidaindex">
/// 1-baserat index för en sida.
/// </parameter>
/// <returnerar>
/// <see cref="Dokumentet"/>.
/// </returns>
public Document getDocumentOfPage(int pageIndex) throws Exception {
	return getDocumentOfPageRange(pageIndex, pageIndex);
}
/// <sammanfattning>
/// Hämtar dokumentet för ett sidintervall.
/// </sammanfattning>
/// <param namn="startindex">
/// 1-baserat index för startsidan.
/// </parameter>
//<param namn="slutindex">
/// 1-baserat index för slutsidan.
/// </parameter>
/// <returnerar>
/// <see cref="Dokumentet"/>.
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
/// <sammanfattning>
/// Tillhandahåller metoder för att extrahera noder i ett dokument som renderas på specifika sidor.
/// </sammanfattning>
class PageNumberFinder
{
// Mappar nod till ett start-/slutsidnummer.
// Detta används för att åsidosätta sidnummer för baslinjer som anges av samlaren när dokumentet delas.
private Map<Node, Integer> nodeStartPageLookup = new HashMap<>();
private Map<Node, Integer> nodeEndPageLookup = new HashMap<>();
private LayoutCollector collector;
// Mappar sidnumret till en lista över noder som finns på den sidan.
private Map<Integer, ArrayList<Node>> reversePageLookup;
/// <sammanfattning>
/// Initierar en ny instans av <see cref="PageNumberFinder"/>-klassen.
/// </sammanfattning>
/// <param name="collector">En samlarinstans som har layoutmodellposter för dokumentet.</param>
public PageNumberFinder(LayoutCollector collector)
{
	this.collector = collector;
}
public Document getDocument()
{
	return collector.getDocument();
}
/// <sammanfattning>
/// Hämtar 1-baserat index för en sida där noden börjar.
/// </sammanfattning>
/// <param namn="nod">
/// Noden.
/// </parameter>
/// <returnerar>
/// Sidindex.
/// </returns>
public int getPage(Node node) throws Exception {
	return nodeStartPageLookup.containsKey(node)
		? nodeStartPageLookup.get(node)
		: collector.getStartPageIndex(node);
}
/// <sammanfattning>
/// Hämtar 1-baserat index för en sida där noden slutar.
/// </sammanfattning>
/// <param namn="nod">
/// Noden.
/// </parameter>
/// <returnerar>
/// Sidindex.
/// </returns>
public int getPageEnd(Node node) throws Exception {
	return nodeEndPageLookup.containsKey(node)
		? nodeEndPageLookup.get(node)
		: collector.getEndPageIndex(node);
}
/// <sammanfattning>
/// Returnerar hur många sidor den angivna noden sträcker sig över. Returnerar 1 om noden finns inom en sida.
/// </sammanfattning>
/// <param namn="nod">
/// Noden.
/// </parameter>
/// <returnerar>
/// Sidindex.
/// </returns>
public int pageSpan(Node node) throws Exception {
	return getPageEnd(node) - getPage(node) + 1;
}
/// <sammanfattning>
/// Returnerar en lista över noder som finns någonstans på den angivna sidan eller sidorna som matchar den angivna nodtypen.
/// </sammanfattning>
/// <param namn="startsida">
/// Startsidan.
/// </parameter>
/// <param namn="slutsida">
/// Slutsidan.
/// </parameter>
/// <param namn="nodtyp">
/// Nodtypen.
/// </parameter>
/// <returnerar>
/// <see cref="IList{T}"/>.
/// </returns>
public ArrayList<Node> retrieveAllNodesOnPages(int startPage, int endPage, /*Nodtyp*/int nodeType) throws Exception
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
		// Vissa sidor kan vara tomma.
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
/// <sammanfattning>
/// Delar upp noder som visas över två eller fler sidor i separata noder så att de fortfarande visas på samma sätt
/// men visas inte längre över en sida.
/// </sammanfattning>
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
	// Besök alla kompositer som eventuellt är uppdelade över sidor och dela upp dem i separata noder.
	collector.getDocument().accept(new SectionSplitter(this));
}
/// <sammanfattning>
//Detta anropas av <see cref="SectionSplitter"/> för att uppdatera sidnummer för delade noder.
/// </sammanfattning>
/// <param namn="nod">
/// Noden.
/// </parameter>
/// <param namn="startsida">
/// Startsidan.
/// </parameter>
/// <param namn="slutsida">
/// Slutsidan.
/// </parameter>
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
	// Lägg till varje nod i en lista som representerar noderna som finns på varje sida.
	for (Node node : (Iterable<Node>) collector.getDocument().getChildNodes(NodeType.ANY, true))
	{
		// Sidhuvuden/sidfot följer avsnitt och delas inte upp av sig själva.
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
/// <sammanfattning>
/// Delar upp texten i den angivna körningen i två körningar.
/// Infogar den nya körningen precis efter den angivna körningen.
/// </sammanfattning>
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
/// <sammanfattning>
/// Delar upp ett dokument i flera avsnitt så att varje sida börjar och slutar vid en avsnittsgräns.
/// </sammanfattning>
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
	// Om det finns ett tidigare avsnitt, försök att kopiera alla länkade sidhuvudsfötter.
	// Annars kommer de inte att visas i ett extraherat dokument om föregående avsnitt saknas.
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
	// Om stycket bara innehåller en avsnittsbrytning, lägg till en falsk run into.
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
		// Ta bort listnumreringen från det klonade stycket men lämna indraget detsamma 
		// eftersom stycket ska vara en del av det föregående.
		if (paragraph.isListItem())
		{
			double textPosition = clonePara.getListFormat().getListLevel().getTextPosition();
			clonePara.getListFormat().removeNumbers();
			clonePara.getParagraphFormat().setLeftIndent(textPosition);
		}
		// Återställ avståndet för delade stycken i tabeller eftersom ytterligare avstånd kan få dem att se annorlunda ut.
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
		// Korrigerar sidbrytningen i slutet av avsnittet.
		SplitPageBreakCorrector.processSection(cloneSection);
	}
	SplitPageBreakCorrector.processSection(section);
	// Lägg även till ny sidnumrering för avsnittets brödtext.
	pageNumberFinder.addPageNumbersForNode(section.getBody(), pageNumberFinder.getPage(section),
		pageNumberFinder.getPageEnd(section));
	return Besökaråtgärd.CONTINUE;
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
	// En nod kan sträcka sig över flera sidor, så en lista med delade positioner returneras.
	// Den delade noden är den första noden på nästa sida.
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
		// Om sidan för den underordnade noden har ändrats är detta den delade positionen.
		// Lägg till detta i listan.
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
	// Dela kompositer baklänges, så att de klonade noderna infogas i rätt ordning.
	Collections.reverse(splitList);
	return splitList;
}
private CompositeNode splitCompositeAtNode(CompositeNode baseNode, Node targetNode) throws Exception {
	CompositeNode cloneNode = (CompositeNode) baseNode.deepClone(false);
	Node node = targetNode;
	int currentPageNum = pageNumberFinder.getPage(baseNode);
	// Flytta alla noder som hittas på nästa sida till den kopierade noden. Hantera radnoder separat.
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
		// Om vi har att göra med en rad måste vi lägga till dummy-celler för den klonade raden.
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
	// Infoga den delade noden efter originalet.
	baseNode.getParentNode().insertAfter(cloneNode, baseNode);
	// Uppdatera de nya sidnumren för basnoden och den klonade noden, inklusive dess underordnade noder.
	// Detta kommer bara att vara en enda sida eftersom den klonade kompositen är uppdelad för att vara på en sida.
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

## Slutsats

Du har nu lärt dig hur du delar upp ett dokument i separata sidor med hjälp av Aspose.Words för Java. Den här guiden ger en omfattande steg-för-steg-handledning med exempel på källkod. Du kan ytterligare anpassa och utöka den här koden för att möta dina specifika behov när du arbetar med dokument.
Absolut! Låt oss lägga till en FAQ-sektion i vår guide om hur man delar upp dokument i sidor med Aspose.Words för Java.

## Vanliga frågor

### Hur lägger jag till Aspose.Words för Java i mitt projekt?

För att lägga till Aspose.Words för Java i ditt projekt, följ dessa steg:

1. Ladda ner Aspose.Words för Java-biblioteket från [här](https://releases.aspose.com/words/java/).
2. Lägg till den nedladdade JAR-filen i ditt projekts klassväg.
3. Du kan nu börja använda Aspose.Words för Java i ditt projekt.

### Kan jag dela dokument i andra format, till exempel PDF eller DOCX?

Nej, den här guiden behandlar specifikt hur man delar dokument i DOC-format med Aspose.Words för Java. Om du behöver dela dokument i andra format kan du behöva utforska andra bibliotek eller verktyg som stöder dessa format.

### Är Aspose.Words för Java ett gratis bibliotek?

Nej, Aspose.Words för Java är inte ett gratis bibliotek. Det är en kommersiell produkt med en licensavgift. Du kan besöka [Aspose.Words för Java prissida](https://purchase.aspose.com/words/java) för mer information om licenser och prisuppgifter.

### Kan jag dela upp dokument i anpassade sidstorlekar och format?

Ja, du kan anpassa sidstorlekar och format för de delade dokumenten genom att ändra sidinställningarna i Aspose.Words för Java. Se Aspose.Words-dokumentationen för mer information om hur du anpassar sidinställningarna efter dina behov.

### Finns det några begränsningar för hur många sidor som kan delas upp?

Aspose.Words för Java har inga specifika begränsningar för antalet sidor du kan dela. Tänk dock på att mycket stora dokument kan kräva mer minne och bearbetningstid. Var uppmärksam på systemresurser när du arbetar med stora dokument.

### Hur kan jag hantera sidhuvuden och sidfot när jag delar dokument?

Sidhuvuden och sidfot kan hanteras vid delning av dokument med hjälp av Aspose.Words för Java-biblioteket. Du kan kopiera innehållet i sidhuvuden och sidfoten från originaldokumentet till de delade dokumenten och säkerställa att de bevaras korrekt. Du kan behöva anpassa den här processen baserat på dina specifika krav för sidhuvuden och sidfoten.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}