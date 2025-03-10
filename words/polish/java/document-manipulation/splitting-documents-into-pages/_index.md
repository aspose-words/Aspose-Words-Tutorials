---
title: Dzielenie dokumentów na strony w Aspose.Words dla Java
linktitle: Dzielenie dokumentów na strony
second_title: Aspose.Words API przetwarzania dokumentów Java
description: Dowiedz się, jak dzielić dokumenty na strony za pomocą Aspose.Words for Java. Przewodnik krok po kroku z kodem źródłowym do wydajnego przetwarzania dokumentów.
weight: 23
url: /pl/java/document-manipulation/splitting-documents-into-pages/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Dzielenie dokumentów na strony w Aspose.Words dla Java


Jeśli pracujesz z przetwarzaniem dokumentów w Javie, Aspose.Words for Java to potężne API, które może pomóc Ci wydajnie dzielić dokumenty na oddzielne strony. W tym samouczku krok po kroku przeprowadzimy Cię przez proces dzielenia dokumentów przy użyciu dostarczonego kodu źródłowego. Pod koniec tego samouczka będziesz w stanie dzielić dokumenty z łatwością, co poprawi Twoje możliwości zarządzania dokumentami.

## 1. Wprowadzenie

Aspose.Words for Java to biblioteka Java, która umożliwia programowe manipulowanie dokumentami Word. Jednym z typowych zadań jest dzielenie dokumentu na oddzielne strony, co może być przydatne do różnych celów, takich jak archiwizacja, drukowanie lub przetwarzanie dokumentów.

## 2. Wymagania wstępne

Zanim zagłębimy się w kod, upewnij się, że spełnione są następujące wymagania wstępne:

- Java Development Kit (JDK) zainstalowany w Twoim systemie.
-  Biblioteka Aspose.Words dla Java, którą można pobrać[Tutaj](https://releases.aspose.com/words/java/).

## 3. Konfigurowanie środowiska

Aby rozpocząć, skonfiguruj środowisko programistyczne w następujący sposób:

- Utwórz projekt Java w preferowanym zintegrowanym środowisku programistycznym (IDE).
- Dodaj bibliotekę Aspose.Words for Java do swojego projektu. Możesz zapoznać się z[dokumentacja](https://reference.aspose.com/words/java/) Aby uzyskać szczegółowe instrukcje.

## 4. Zrozumienie kodu źródłowego

Podany przez Ciebie kod źródłowy ma na celu podzielenie dokumentu na oddzielne strony. Rozłóżmy kluczowe komponenty:

```java
String fileName = FilenameUtils.getBaseName(docName);
String extensionName = FilenameUtils.getExtension(docName);
System.out.println("Processing document: " + fileName + "." + extensionName);
Document doc = new Document(docName);
```

- Wyodrębniamy nazwę bazową i rozszerzenie dokumentu wejściowego.
- Dokument ładujemy za pomocą Aspose.Words dla Java.

## 5. Dzielenie dokumentów krok po kroku

### 5.1. Ładowanie dokumentu

```java
Document doc = new Document(docName);
```

 W tym kroku ładujemy dokument wejściowy do`Document` obiekt, który umożliwia pracę z treścią dokumentu.

### 5.2. Inicjalizacja DocumentPageSplitter

```java
DocumentPageSplitter splitter = new DocumentPageSplitter(doc);
```

 Inicjujemy`DocumentPageSplitter` obiekt z naszym załadowanym dokumentem. Ta klasa jest dostarczana przez Aspose.Words dla Javy i pomaga nam podzielić dokument na strony.

### 5.3. Zapisywanie każdej strony

```java
for (int page = 1; page <= doc.getPageCount(); page++) {
    Document pageDoc = splitter.getDocumentOfPage(page);
    pageDoc.save("Your Directory Path" + MessageFormat.format("{0} - page{1}.{2}", fileName, page, extensionName));
}
```

W tym kroku przechodzimy przez każdą stronę dokumentu i zapisujemy go jako osobny dokument. Możesz określić ścieżkę katalogu, w którym zostaną zapisane podzielone strony.

## 6. Uruchomienie kodu

Aby pomyślnie uruchomić ten kod, upewnij się, że skonfigurowałeś środowisko i dodałeś bibliotekę Aspose.Words for Java do swojego projektu. Następnie wykonaj kod, a Twój dokument zostanie podzielony na osobne strony.

## DocumentPageSplitter Kod źródłowy

```java
/// <podsumowanie>
/// Dzieli dokument na wiele dokumentów, po jednym na stronę.
/// </podsumowanie>
class DocumentPageSplitter
{
private PageNumberFinder pageNumberFinder;
/// <podsumowanie>
/// Inicjuje nowe wystąpienie klasy <see cref="DocumentPageSplitter"/>.
/// Ta metoda dzieli dokument na sekcje, tak że każda strona zaczyna się i kończy na granicy sekcji.
/// Zaleca się, aby nie modyfikować dokumentu później.
/// </podsumowanie>
/// <param name="source">Dokument źródłowy</param>
public DocumentPageSplitter(Document source) throws Exception
{
	pageNumberFinder = PageNumberFinderFactory.create(source);
}
private Document getDocument() {
	return pageNumberFinder.getDocument();
}
/// <podsumowanie>
/// Pobiera dokument strony.
/// </podsumowanie>
/// <parametr name="pageIndex">
/// 1-indeks strony.
/// </parametr>
/// <zwraca>
/// <patrz cref="Document"/>.
/// </zwroty>
public Document getDocumentOfPage(int pageIndex) throws Exception {
	return getDocumentOfPageRange(pageIndex, pageIndex);
}
/// <podsumowanie>
//Pobiera dokument z zakresu stron.
/// </podsumowanie>
/// <nazwa parametru="indeks początkowy">
/// 1-indeks strony startowej.
/// </parametr>
/// <nazwa parametru="endIndex">
/// 1-indeks strony końcowej.
/// </parametr>
/// <zwraca>
/// <patrz cref="Document"/>.
/// </zwroty>
public Document getDocumentOfPageRange(int startIndex, int endIndex) throws Exception {
	Document result = (Document) getDocument().deepClone(false);
	for (Node section : pageNumberFinder.retrieveAllNodesOnPages(startIndex, endIndex, NodeType.SECTION))
	{
		result.appendChild(result.importNode(section, true));
	}
	return result;
}
}
/// <podsumowanie>
/// Udostępnia metody wyodrębniania węzłów dokumentu, które są renderowane na określonych stronach.
/// </podsumowanie>
class PageNumberFinder
{
// Mapuje węzeł na numery stron początkowych/końcowych.
// Służy do zastępowania numerów stron bazowych podanych przez kolektor podczas dzielenia dokumentu.
private Map<Node, Integer> nodeStartPageLookup = new HashMap<>();
private Map<Node, Integer> nodeEndPageLookup = new HashMap<>();
private LayoutCollector collector;
// Mapuje numer strony na listę węzłów znajdujących się na tej stronie.
private Map<Integer, ArrayList<Node>> reversePageLookup;
/// <podsumowanie>
/// Inicjuje nowe wystąpienie klasy <see cref="PageNumberFinder"/>.
/// </podsumowanie>
/// <param name="collector">Instancja kolektora zawierająca rekordy modelu układu dla dokumentu.</param>
public PageNumberFinder(LayoutCollector collector)
{
	this.collector = collector;
}
public Document getDocument()
{
	return collector.getDocument();
}
/// <podsumowanie>
/// Pobiera indeks strony, na której rozpoczyna się węzeł, oparty na liczbie 1.
/// </podsumowanie>
/// <nazwa parametru="węzeł">
/// Węzeł.
/// </parametr>
/// <zwraca>
/// Indeks stron.
/// </zwroty>
public int getPage(Node node) throws Exception {
	return nodeStartPageLookup.containsKey(node)
		? nodeStartPageLookup.get(node)
		: collector.getStartPageIndex(node);
}
/// <podsumowanie>
/// Pobiera indeks strony, na której kończy się węzeł, oparty na liczbie 1.
/// </podsumowanie>
/// <nazwa parametru="węzeł">
/// Węzeł.
/// </parametr>
/// <zwraca>
/// Indeks stron.
/// </zwroty>
public int getPageEnd(Node node) throws Exception {
	return nodeEndPageLookup.containsKey(node)
		? nodeEndPageLookup.get(node)
		: collector.getEndPageIndex(node);
}
/// <podsumowanie>
//Zwraca liczbę stron, na których rozciąga się określony węzeł. Zwraca 1, jeśli węzeł znajduje się na jednej stronie.
/// </podsumowanie>
/// <nazwa parametru="węzeł">
/// Węzeł.
/// </parametr>
/// <zwraca>
/// Indeks stron.
/// </zwroty>
public int pageSpan(Node node) throws Exception {
	return getPageEnd(node) - getPage(node) + 1;
}
/// <podsumowanie>
/// Zwraca listę węzłów znajdujących się w dowolnym miejscu na określonej stronie lub stronach, które odpowiadają określonemu typowi węzła.
/// </podsumowanie>
/// <parametr name="stronapoczątkowa">
/// Strona startowa.
/// </parametr>
/// <nazwa parametru="koniecStrony">
/// Strona końcowa.
/// </parametr>
/// <parametr name="typwęzła">
/// Typ węzła.
/// </parametr>
/// <zwraca>
/// <patrz cref="IList{T}"/>.
/// </zwroty>
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
		// Niektóre strony mogą być puste.
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
/// <podsumowanie>
/// Dzieli węzły, które pojawiają się na dwóch lub więcej stronach, na osobne węzły, tak aby nadal pojawiały się w ten sam sposób
/// ale nie są już wyświetlane na stronie.
/// </podsumowanie>
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
	// Odwiedź wszystkie kompozyty, które mogą być podzielone na strony i podziel je na oddzielne węzły.
	collector.getDocument().accept(new SectionSplitter(this));
}
/// <podsumowanie>
/// Wywołuje tę funkcję <see cref="SectionSplitter"/> w celu aktualizacji numerów stron podzielonych węzłów.
/// </podsumowanie>
/// <nazwa parametru="węzeł">
/// Węzeł.
/// </parametr>
/// <parametr name="stronapoczątkowa">
/// Strona startowa.
/// </parametr>
/// <nazwa parametru="koniecStrony">
/// Strona końcowa.
/// </parametr>
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
	// Dodaj każdy węzeł do listy reprezentującej węzły znalezione na każdej stronie.
	for (Node node : (Iterable<Node>) collector.getDocument().getChildNodes(NodeType.ANY, true))
	{
		//Nagłówki/stopki następują po sekcjach i nie są rozdzielone.
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
/// <podsumowanie>
/// Dzieli tekst określonego przebiegu na dwa przebiegi.
/// Wstawia nowy przebieg tuż po określonym przebiegu.
/// </podsumowanie>
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
/// <podsumowanie>
/// Dzieli dokument na wiele sekcji tak, że każda strona zaczyna się i kończy na granicy sekcji.
/// </podsumowanie>
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
	// Jeśli istnieje poprzednia sekcja, spróbuj skopiować wszelkie połączone nagłówki i stopki.
	// W przeciwnym razie nie pojawią się one w wyodrębnionym dokumencie, jeśli brakuje poprzedniej sekcji.
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
	// Jeżeli akapit zawiera jedynie podział sekcji, należy dodać fałszywe włączenie.
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
		// Usuń numerację listy ze sklonowanego akapitu, ale pozostaw wcięcie takie samo
		// ponieważ akapit ma być częścią poprzedniego elementu.
		if (paragraph.isListItem())
		{
			double textPosition = clonePara.getListFormat().getListLevel().getTextPosition();
			clonePara.getListFormat().removeNumbers();
			clonePara.getParagraphFormat().setLeftIndent(textPosition);
		}
		// Zresetuj odstępy między podzielonymi akapitami w tabelach, ponieważ dodatkowe odstępy mogą powodować, że będą one wyglądać inaczej.
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
		// Poprawiono podział strony na końcu sekcji.
		SplitPageBreakCorrector.processSection(cloneSection);
	}
	SplitPageBreakCorrector.processSection(section);
	// Dodaj nową numerację stron również do treści sekcji.
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
	// Węzeł może rozciągać się na wiele stron, dlatego zwracana jest lista pozycji podziału.
	//Węzeł podzielony to pierwszy węzeł na następnej stronie.
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
		// Jeśli strona węzła podrzędnego uległa zmianie, to jest to pozycja podziału.
		// Dodaj to do listy.
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
	// Podziel kompozyty wstecz, aby sklonowane węzły zostały wstawione we właściwej kolejności.
	Collections.reverse(splitList);
	return splitList;
}
private CompositeNode splitCompositeAtNode(CompositeNode baseNode, Node targetNode) throws Exception {
	CompositeNode cloneNode = (CompositeNode) baseNode.deepClone(false);
	Node node = targetNode;
	int currentPageNum = pageNumberFinder.getPage(baseNode);
	// Przenieś wszystkie węzły znalezione na następnej stronie do skopiowanego węzła. Obsługuj węzły wierszy oddzielnie.
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
		// Jeżeli mamy do czynienia z wierszem, musimy dodać komórki fikcyjne dla sklonowanego wiersza.
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
	// Wstaw podzielony węzeł za oryginalnym.
	baseNode.getParentNode().insertAfter(cloneNode, baseNode);
	// Zaktualizuj nowe numery stron węzła bazowego i sklonowanego węzła, łącznie z jego potomkami.
	// Będzie to tylko pojedyncza strona, ponieważ sklonowany kompozyt zostanie podzielony, aby znaleźć się na jednej stronie.
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

## Wniosek

Teraz wiesz, jak podzielić dokument na osobne strony za pomocą Aspose.Words for Java. Ten przewodnik zawiera kompleksowy samouczek krok po kroku z przykładami kodu źródłowego. Możesz dalej dostosowywać i rozszerzać ten kod, aby spełniał Twoje specyficzne wymagania podczas pracy z dokumentami.
Oczywiście! Dodajmy sekcję FAQ do naszego przewodnika na temat dzielenia dokumentów na strony za pomocą Aspose.Words dla Java.

## Najczęściej zadawane pytania

### Jak dodać Aspose.Words for Java do mojego projektu?

Aby dodać Aspose.Words for Java do swojego projektu, wykonaj następujące kroki:

1.  Pobierz bibliotekę Aspose.Words dla Java ze strony[Tutaj](https://releases.aspose.com/words/java/).
2. Dodaj pobrany plik JAR do ścieżki klas swojego projektu.
3. Możesz teraz zacząć używać Aspose.Words for Java w swoim projekcie.

### Czy mogę dzielić dokumenty w innych formatach, np. PDF lub DOCX?

Nie, ten przewodnik dotyczy konkretnie dzielenia dokumentów w formacie DOC przy użyciu Aspose.Words for Java. Jeśli musisz dzielić dokumenty w innych formatach, możesz potrzebować innych bibliotek lub narzędzi, które obsługują te formaty.

### Czy Aspose.Words dla Java jest darmową biblioteką?

 Nie, Aspose.Words for Java nie jest darmową biblioteką. Jest to produkt komercyjny z opłatą licencyjną. Możesz odwiedzić[Strona cenowa Aspose.Words dla Java](https://purchase.aspose.com/words/java) Aby uzyskać więcej informacji na temat licencjonowania i cen.

### Czy mogę podzielić dokumenty na niestandardowe rozmiary i formaty stron?

Tak, możesz dostosować rozmiary i formaty stron podzielonych dokumentów, modyfikując właściwości ustawień strony w Aspose.Words dla Java. Zapoznaj się z dokumentacją Aspose.Words, aby uzyskać szczegółowe informacje na temat dostosowywania ustawień strony zgodnie z wymaganiami.

### Czy istnieją jakieś ograniczenia co do liczby stron, które można podzielić?

Aspose.Words for Java nie nakłada konkretnych ograniczeń na liczbę stron, które możesz podzielić. Pamiętaj jednak, że bardzo duże dokumenty mogą wymagać więcej pamięci i czasu przetwarzania. Uważaj na zasoby systemowe podczas pracy z dużymi dokumentami.

### Jak radzić sobie z nagłówkami i stopkami podczas dzielenia dokumentów?

Nagłówki i stopki można obsługiwać podczas dzielenia dokumentów za pomocą biblioteki Aspose.Words for Java. Możesz skopiować zawartość nagłówka i stopki z oryginalnego dokumentu do podzielonych dokumentów, zapewniając ich prawidłowe zachowanie. Może być konieczne dostosowanie tego procesu w oparciu o konkretne wymagania dotyczące nagłówka i stopki.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
