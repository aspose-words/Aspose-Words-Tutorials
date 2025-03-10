---
title: Aufteilen von Dokumenten in Seiten in Aspose.Words für Java
linktitle: Aufteilen von Dokumenten in Seiten
second_title: Aspose.Words Java-API zur Dokumentverarbeitung
description: Erfahren Sie, wie Sie Dokumente mit Aspose.Words für Java in Seiten aufteilen. Schritt-für-Schritt-Anleitung mit Quellcode für eine effiziente Dokumentverarbeitung.
weight: 23
url: /de/java/document-manipulation/splitting-documents-into-pages/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aufteilen von Dokumenten in Seiten in Aspose.Words für Java


Wenn Sie mit der Dokumentenverarbeitung in Java arbeiten, ist Aspose.Words für Java eine leistungsstarke API, mit der Sie Dokumente effizient in einzelne Seiten aufteilen können. In diesem Schritt-für-Schritt-Tutorial führen wir Sie mithilfe des bereitgestellten Quellcodes durch den Prozess des Aufteilens von Dokumenten. Am Ende dieses Tutorials können Sie Dokumente problemlos aufteilen und so Ihre Dokumentenverwaltungsfunktionen verbessern.

## 1. Einleitung

Aspose.Words für Java ist eine Java-Bibliothek, mit der Sie Word-Dokumente programmgesteuert bearbeiten können. Eine häufige Aufgabe ist das Aufteilen eines Dokuments in einzelne Seiten, was für verschiedene Zwecke nützlich sein kann, z. B. zum Archivieren, Drucken oder zur Dokumentverarbeitung.

## 2. Voraussetzungen

Bevor wir uns in den Code vertiefen, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:

- Auf Ihrem System ist Java Development Kit (JDK) installiert.
-  Aspose.Words für Java-Bibliothek, die Sie herunterladen können[Hier](https://releases.aspose.com/words/java/).

## 3. Einrichten Ihrer Umgebung

Richten Sie zunächst Ihre Entwicklungsumgebung wie folgt ein:

- Erstellen Sie ein Java-Projekt in Ihrer bevorzugten integrierten Entwicklungsumgebung (IDE).
- Fügen Sie Ihrem Projekt die Bibliothek Aspose.Words für Java hinzu. Weitere Informationen finden Sie unter[Dokumentation](https://reference.aspose.com/words/java/) für detaillierte Anweisungen.

## 4. Den Quellcode verstehen

Der von Ihnen bereitgestellte Quellcode ist dafür gedacht, ein Dokument in einzelne Seiten aufzuteilen. Lassen Sie uns die wichtigsten Komponenten aufschlüsseln:

```java
String fileName = FilenameUtils.getBaseName(docName);
String extensionName = FilenameUtils.getExtension(docName);
System.out.println("Processing document: " + fileName + "." + extensionName);
Document doc = new Document(docName);
```

- Wir extrahieren den Basisnamen und die Erweiterung des Eingabedokuments.
- Wir laden das Dokument mit Aspose.Words für Java.

## 5. Dokumente Schritt für Schritt aufteilen

### 5.1. Laden des Dokuments

```java
Document doc = new Document(docName);
```

 In diesem Schritt laden wir das Eingabedokument in ein`Document` Objekt, das uns ermöglicht, mit dem Inhalt des Dokuments zu arbeiten.

### 5.2. Initialisieren des DocumentPageSplitters

```java
DocumentPageSplitter splitter = new DocumentPageSplitter(doc);
```

 Wir initialisieren eine`DocumentPageSplitter` Objekt mit unserem geladenen Dokument. Diese Klasse wird von Aspose.Words für Java bereitgestellt und hilft uns, das Dokument in Seiten aufzuteilen.

### 5.3. Jede Seite speichern

```java
for (int page = 1; page <= doc.getPageCount(); page++) {
    Document pageDoc = splitter.getDocumentOfPage(page);
    pageDoc.save("Your Directory Path" + MessageFormat.format("{0} - page{1}.{2}", fileName, page, extensionName));
}
```

In diesem Schritt durchlaufen wir jede Seite des Dokuments und speichern sie als separates Dokument. Sie können den Verzeichnispfad angeben, in dem die aufgeteilten Seiten gespeichert werden.

## 6. Ausführen des Codes

Um diesen Code erfolgreich auszuführen, stellen Sie sicher, dass Sie Ihre Umgebung eingerichtet und die Bibliothek Aspose.Words für Java zu Ihrem Projekt hinzugefügt haben. Führen Sie dann den Code aus, und Ihr Dokument wird in einzelne Seiten aufgeteilt.

## DocumentPageSplitter-Quellcode

```java
/// <Zusammenfassung>
/// Teilt ein Dokument in mehrere Dokumente auf, eines pro Seite.
/// </summary>
class DocumentPageSplitter
{
private PageNumberFinder pageNumberFinder;
/// <Zusammenfassung>
/// Initialisiert eine neue Instanz der Klasse <see cref="DocumentPageSplitter"/>.
/// Diese Methode teilt das Dokument in Abschnitte auf, sodass jede Seite an einer Abschnittsgrenze beginnt und endet.
/// Es wird empfohlen, das Dokument nachträglich nicht zu ändern.
/// </summary>
/// <param name="source">Quelldokument</param>
public DocumentPageSplitter(Document source) throws Exception
{
	pageNumberFinder = PageNumberFinderFactory.create(source);
}
private Document getDocument() {
	return pageNumberFinder.getDocument();
}
/// <Zusammenfassung>
/// Ruft das Dokument einer Seite ab.
/// </summary>
/// <param name="Seitenindex">
/// 1-basierter Index einer Seite.
/// </param>
/// <Rückgabe>
/// Das <see cref="Dokument"/>.
/// </returns>
public Document getDocumentOfPage(int pageIndex) throws Exception {
	return getDocumentOfPageRange(pageIndex, pageIndex);
}
/// <Zusammenfassung>
//Ruft das Dokument eines Seitenbereichs ab.
/// </summary>
/// <param name="startIndex">
/// 1-basierter Index der Startseite.
/// </param>
/// <param name="endIndex">
/// 1-basierter Index der Endseite.
/// </param>
/// <Rückgabe>
/// Das <see cref="Dokument"/>.
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
/// <Zusammenfassung>
/// Bietet Methoden zum Extrahieren von Knoten eines Dokuments, die auf bestimmten Seiten gerendert werden.
/// </summary>
class PageNumberFinder
{
// Ordnet den Knoten den Start-/Endseitenzahlen zu.
// Dies wird verwendet, um die vom Collector bereitgestellten Basisseitenzahlen beim Aufteilen des Dokuments zu überschreiben.
private Map<Node, Integer> nodeStartPageLookup = new HashMap<>();
private Map<Node, Integer> nodeEndPageLookup = new HashMap<>();
private LayoutCollector collector;
// Ordnet die Seitennummer einer Liste der auf dieser Seite gefundenen Knoten zu.
private Map<Integer, ArrayList<Node>> reversePageLookup;
/// <Zusammenfassung>
/// Initialisiert eine neue Instanz der Klasse <see cref="PageNumberFinder"/>.
/// </summary>
/// <param name="collector">Eine Collector-Instanz, die Layoutmodell-Datensätze für das Dokument enthält.</param>
public PageNumberFinder(LayoutCollector collector)
{
	this.collector = collector;
}
public Document getDocument()
{
	return collector.getDocument();
}
/// <Zusammenfassung>
/// Ruft den 1-basierten Index einer Seite ab, auf der der Knoten beginnt.
/// </summary>
/// <param name="Knoten">
/// Der Knoten.
/// </param>
/// <Rückgabe>
/// Seitenindex.
/// </returns>
public int getPage(Node node) throws Exception {
	return nodeStartPageLookup.containsKey(node)
		? nodeStartPageLookup.get(node)
		: collector.getStartPageIndex(node);
}
/// <Zusammenfassung>
/// Ruft den 1-basierten Index einer Seite ab, auf der der Knoten endet.
/// </summary>
/// <param name="Knoten">
/// Der Knoten.
/// </param>
/// <Rückgabe>
/// Seitenindex.
/// </returns>
public int getPageEnd(Node node) throws Exception {
	return nodeEndPageLookup.containsKey(node)
		? nodeEndPageLookup.get(node)
		: collector.getEndPageIndex(node);
}
/// <Zusammenfassung>
//Gibt zurück, über wie viele Seiten sich der angegebene Knoten erstreckt. Gibt 1 zurück, wenn der Knoten auf einer Seite liegt.
/// </summary>
/// <param name="Knoten">
/// Der Knoten.
/// </param>
/// <Rückgabe>
/// Seitenindex.
/// </returns>
public int pageSpan(Node node) throws Exception {
	return getPageEnd(node) - getPage(node) + 1;
}
/// <Zusammenfassung>
/// Gibt eine Liste von Knoten zurück, die irgendwo auf der angegebenen Seite oder den angegebenen Seiten enthalten sind und dem angegebenen Knotentyp entsprechen.
/// </summary>
/// <param name="Startseite">
/// Die Startseite.
/// </param>
/// <param name="endPage">
/// Die letzte Seite.
/// </param>
/// <param name="Knotentyp">
/// Der Knotentyp.
/// </param>
/// <Rückgabe>
/// Die <see cref="IList{T}"/>.
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
		// Einige Seiten können leer sein.
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
/// <Zusammenfassung>
/// Teilt Knoten, die über zwei oder mehr Seiten hinweg erscheinen, in separate Knoten auf, so dass sie immer noch auf die gleiche Weise erscheinen
/// werden aber nicht mehr auf einer Seite angezeigt.
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
	// Besuchen Sie alle möglicherweise auf mehrere Seiten verteilten Komposite und teilen Sie sie in separate Knoten auf.
	collector.getDocument().accept(new SectionSplitter(this));
}
/// <Zusammenfassung>
/// Dies wird von <see cref="SectionSplitter"/> aufgerufen, um die Seitennummern der geteilten Knoten zu aktualisieren.
/// </summary>
/// <param name="Knoten">
/// Der Knoten.
/// </param>
/// <param name="Startseite">
/// Die Startseite.
/// </param>
/// <param name="endPage">
/// Die letzte Seite.
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
	// Fügen Sie jeden Knoten zu einer Liste hinzu, die die auf jeder Seite gefundenen Knoten darstellt.
	for (Node node : (Iterable<Node>) collector.getDocument().getChildNodes(NodeType.ANY, true))
	{
		//Kopf-/Fußzeilen folgen den Abschnitten und sind nicht in sich selbst unterteilt.
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
/// <Zusammenfassung>
/// Teilt den Text des angegebenen Laufs in zwei Läufe auf.
/// Fügt den neuen Lauf direkt nach dem angegebenen Lauf ein.
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
/// <Zusammenfassung>
/// Teilt ein Dokument in mehrere Abschnitte auf, sodass jede Seite an einer Abschnittsgrenze beginnt und endet.
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
	// Wenn es einen vorherigen Abschnitt gibt, versuchen Sie, alle verknüpften Kopf- und Fußzeilen zu kopieren.
	// Andernfalls erscheinen sie nicht in einem extrahierten Dokument, wenn der vorherige Abschnitt fehlt.
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
	// Wenn der Absatz nur einen Abschnittsumbruch enthält, fügen Sie einen falschen „run into“ hinzu.
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
		// Entfernen Sie die Listennummerierung aus dem geklonten Absatz, lassen Sie den Einzug jedoch unverändert
		// da der Absatz Teil des vorhergehenden Punkts sein soll.
		if (paragraph.isListItem())
		{
			double textPosition = clonePara.getListFormat().getListLevel().getTextPosition();
			clonePara.getListFormat().removeNumbers();
			clonePara.getParagraphFormat().setLeftIndent(textPosition);
		}
		// Setzen Sie den Abstand geteilter Absätze in Tabellen zurück, da zusätzlicher Abstand zu einem anderen Erscheinungsbild führen kann.
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
		// Korrigiert den Seitenumbruch am Ende des Abschnitts.
		SplitPageBreakCorrector.processSection(cloneSection);
	}
	SplitPageBreakCorrector.processSection(section);
	// Fügen Sie auch für den Hauptteil des Abschnitts eine neue Seitennummerierung hinzu.
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
	// Ein Knoten kann sich über mehrere Seiten erstrecken, daher wird eine Liste der geteilten Positionen zurückgegeben.
	//Der geteilte Knoten ist der erste Knoten auf der nächsten Seite.
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
		// Wenn sich die Seite des untergeordneten Knotens geändert hat, ist dies die Teilungsposition.
		// Fügen Sie dies der Liste hinzu.
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
	// Teilen Sie Verbundwerkstoffe rückwärts auf, sodass die geklonten Knoten in der richtigen Reihenfolge eingefügt werden.
	Collections.reverse(splitList);
	return splitList;
}
private CompositeNode splitCompositeAtNode(CompositeNode baseNode, Node targetNode) throws Exception {
	CompositeNode cloneNode = (CompositeNode) baseNode.deepClone(false);
	Node node = targetNode;
	int currentPageNum = pageNumberFinder.getPage(baseNode);
	// Verschieben Sie alle auf der nächsten Seite gefundenen Knoten in den kopierten Knoten. Behandeln Sie Zeilenknoten separat.
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
		// Wenn wir mit einer Zeile arbeiten, müssen wir Dummyzellen für die geklonte Zeile hinzufügen.
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
	// Fügen Sie den geteilten Knoten nach dem Original ein.
	baseNode.getParentNode().insertAfter(cloneNode, baseNode);
	// Aktualisieren Sie die neuen Seitennummern des Basisknotens und des geklonten Knotens, einschließlich seiner Nachkommen.
	// Dies wird nur eine einzelne Seite sein, da die geklonte Zusammenstellung auf eine Seite aufgeteilt wird.
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

## Abschluss

Sie haben nun gelernt, wie Sie ein Dokument mit Aspose.Words für Java in einzelne Seiten aufteilen. Dieses Handbuch bietet eine umfassende Schritt-für-Schritt-Anleitung mit Quellcodebeispielen. Sie können diesen Code weiter anpassen und erweitern, um ihn Ihren spezifischen Anforderungen bei der Arbeit mit Dokumenten anzupassen.
Sicherlich! Fügen wir unserem Leitfaden zum Aufteilen von Dokumenten in Seiten mit Aspose.Words für Java einen FAQ-Abschnitt hinzu.

## Häufig gestellte Fragen

### Wie füge ich Aspose.Words für Java zu meinem Projekt hinzu?

Um Aspose.Words für Java zu Ihrem Projekt hinzuzufügen, folgen Sie diesen Schritten:

1.  Laden Sie die Aspose.Words für Java-Bibliothek herunter von[Hier](https://releases.aspose.com/words/java/).
2. Fügen Sie die heruntergeladene JAR-Datei zum Klassenpfad Ihres Projekts hinzu.
3. Sie können jetzt Aspose.Words für Java in Ihrem Projekt verwenden.

### Kann ich Dokumente in andere Formate wie PDF oder DOCX aufteilen?

Nein, dieses Handbuch behandelt speziell das Aufteilen von Dokumenten im DOC-Format mit Aspose.Words für Java. Wenn Sie Dokumente in anderen Formaten aufteilen müssen, müssen Sie möglicherweise andere Bibliotheken oder Tools erkunden, die diese Formate unterstützen.

### Ist Aspose.Words für Java eine kostenlose Bibliothek?

 Nein, Aspose.Words für Java ist keine kostenlose Bibliothek. Es ist ein kommerzielles Produkt mit einer Lizenzgebühr. Sie können die[Aspose.Words für Java-Preisseite](https://purchase.aspose.com/words/java) für weitere Informationen zu Lizenzierung und Preisen.

### Kann ich Dokumente in benutzerdefinierte Seitengrößen und Formate aufteilen?

Ja, Sie können die Seitengrößen und -formate der geteilten Dokumente anpassen, indem Sie die Seiteneinrichtungseigenschaften in Aspose.Words für Java ändern. Weitere Informationen zum Anpassen der Seiteneinstellungen entsprechend Ihren Anforderungen finden Sie in der Aspose.Words-Dokumentation.

### Gibt es Beschränkungen hinsichtlich der Anzahl der Seiten, die aufgeteilt werden können?

Aspose.Words für Java legt keine spezifischen Beschränkungen für die Anzahl der Seiten fest, die Sie aufteilen können. Bedenken Sie jedoch, dass sehr große Dokumente möglicherweise mehr Speicher und Verarbeitungszeit benötigen. Achten Sie bei der Arbeit mit großen Dokumenten auf die Systemressourcen.

### Wie kann ich beim Aufteilen von Dokumenten mit Kopf- und Fußzeilen umgehen?

Kopf- und Fußzeilen können beim Aufteilen von Dokumenten mithilfe der Bibliothek Aspose.Words für Java verarbeitet werden. Sie können Kopf- und Fußzeileninhalte aus dem Originaldokument in die aufgeteilten Dokumente kopieren und dabei sicherstellen, dass sie korrekt erhalten bleiben. Möglicherweise müssen Sie diesen Prozess basierend auf Ihren spezifischen Kopf- und Fußzeilenanforderungen anpassen.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
