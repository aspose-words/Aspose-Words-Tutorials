---
title: Rozdělení dokumentů na stránky v Aspose.Words pro Java
linktitle: Rozdělení dokumentů na stránky
second_title: Aspose.Words Java Document Processing API
description: Naučte se rozdělit dokumenty na stránky pomocí Aspose.Words for Java. Podrobný průvodce se zdrojovým kódem pro efektivní zpracování dokumentů.
weight: 23
url: /cs/java/document-manipulation/splitting-documents-into-pages/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rozdělení dokumentů na stránky v Aspose.Words pro Java


Pokud pracujete se zpracováním dokumentů v Javě, Aspose.Words for Java je výkonné API, které vám pomůže efektivně rozdělit dokumenty na samostatné stránky. V tomto tutoriálu krok za krokem vás provedeme procesem rozdělování dokumentů pomocí poskytnutého zdrojového kódu. Na konci tohoto kurzu budete schopni snadno rozdělit dokumenty a zlepšit tak své možnosti správy dokumentů.

## 1. Úvod

Aspose.Words for Java je knihovna Java, která vám umožňuje programově manipulovat s dokumenty aplikace Word. Jedním z běžných úkolů je rozdělení dokumentu na samostatné stránky, což může být užitečné pro různé účely, jako je archivace, tisk nebo zpracování dokumentů.

## 2. Předpoklady

Než se ponoříme do kódu, ujistěte se, že máte splněny následující předpoklady:

- Java Development Kit (JDK) nainstalovaný ve vašem systému.
-  Knihovna Aspose.Words for Java, kterou si můžete stáhnout[zde](https://releases.aspose.com/words/java/).

## 3. Nastavení vašeho prostředí

Chcete-li začít, nastavte vývojové prostředí následovně:

- Vytvořte projekt Java ve vašem preferovaném integrovaném vývojovém prostředí (IDE).
- Přidejte do projektu knihovnu Aspose.Words for Java. Můžete odkazovat na[dokumentace](https://reference.aspose.com/words/java/) pro podrobné pokyny.

## 4. Pochopení zdrojového kódu

Zdrojový kód, který jste poskytli, je navržen tak, aby rozdělil dokument na samostatné stránky. Pojďme si rozebrat klíčové komponenty:

```java
String fileName = FilenameUtils.getBaseName(docName);
String extensionName = FilenameUtils.getExtension(docName);
System.out.println("Processing document: " + fileName + "." + extensionName);
Document doc = new Document(docName);
```

- Extrahujeme základní název a příponu vstupního dokumentu.
- Dokument načteme pomocí Aspose.Words for Java.

## 5. Rozdělení dokumentů krok za krokem

### 5.1. Načítání dokumentu

```java
Document doc = new Document(docName);
```

 V tomto kroku načteme vstupní dokument do a`Document` objekt, který nám umožňuje pracovat s obsahem dokumentu.

### 5.2. Inicializace DocumentPageSplitter

```java
DocumentPageSplitter splitter = new DocumentPageSplitter(doc);
```

 Inicializujeme a`DocumentPageSplitter` objekt s naším načteným dokumentem. Tuto třídu poskytuje Aspose.Words for Java a pomáhá nám rozdělit dokument na stránky.

### 5.3. Ukládání každé stránky

```java
for (int page = 1; page <= doc.getPageCount(); page++) {
    Document pageDoc = splitter.getDocumentOfPage(page);
    pageDoc.save("Your Directory Path" + MessageFormat.format("{0} - page{1}.{2}", fileName, page, extensionName));
}
```

V tomto kroku iterujeme každou stránku dokumentu a uložíme ji jako samostatný dokument. Můžete zadat cestu k adresáři, kam budou rozdělené stránky uloženy.

## 6. Spuštění kodexu

Chcete-li tento kód úspěšně spustit, ujistěte se, že jste nastavili své prostředí a přidali do projektu knihovnu Aspose.Words for Java. Poté spusťte kód a budete mít dokument rozdělený na samostatné stránky.

## Zdrojový kód DocumentPageSplitter

```java
/// <souhrn>
/// Rozdělí dokument na více dokumentů, jeden na stránku.
/// </summary>
class DocumentPageSplitter
{
private PageNumberFinder pageNumberFinder;
/// <souhrn>
/// Inicializuje novou instanci třídy <viz cref="DocumentPageSplitter"/>.
/// Tato metoda rozdělí dokument na části tak, že každá stránka začíná a končí na hranici oddílu.
/// Doporučuje se dokument následně neupravovat.
/// </summary>
/// <param name="source">Zdrojový dokument</param>
public DocumentPageSplitter(Document source) throws Exception
{
	pageNumberFinder = PageNumberFinderFactory.create(source);
}
private Document getDocument() {
	return pageNumberFinder.getDocument();
}
/// <souhrn>
/// Získá dokument stránky.
/// </summary>
/// <param name="pageIndex">
/// index stránky založený na 1.
/// </param>
/// <vrací>
/// <viz cref="Dokument"/>.
/// </returns>
public Document getDocumentOfPage(int pageIndex) throws Exception {
	return getDocumentOfPageRange(pageIndex, pageIndex);
}
/// <souhrn>
//Získá dokument rozsahu stránek.
/// </summary>
/// <param name="startIndex">
/// 1-založený index úvodní stránky.
/// </param>
/// <param name="endIndex">
/// 1-založený index koncové stránky.
/// </param>
/// <vrací>
/// <viz cref="Dokument"/>.
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
/// <souhrn>
/// Poskytuje metody pro extrakci uzlů dokumentu, které jsou vykresleny na zadaných stránkách.
/// </summary>
class PageNumberFinder
{
// Mapuje uzel na čísla počáteční/koncové stránky.
// Používá se k přepsání čísel stránek účaří poskytnutých kolektorem při rozdělení dokumentu.
private Map<Node, Integer> nodeStartPageLookup = new HashMap<>();
private Map<Node, Integer> nodeEndPageLookup = new HashMap<>();
private LayoutCollector collector;
// Mapuje číslo stránky na seznam uzlů nalezených na této stránce.
private Map<Integer, ArrayList<Node>> reversePageLookup;
/// <souhrn>
/// Inicializuje novou instanci třídy <viz cref="PageNumberFinder"/>.
/// </summary>
/// <param name="collector">Instance kolektoru, která má záznamy modelu rozvržení pro dokument.</param>
public PageNumberFinder(LayoutCollector collector)
{
	this.collector = collector;
}
public Document getDocument()
{
	return collector.getDocument();
}
/// <souhrn>
/// Načte index stránky, na které uzel začíná, založený na 1.
/// </summary>
/// <param name="node">
/// Uzel.
/// </param>
/// <vrací>
/// Index stránky.
/// </returns>
public int getPage(Node node) throws Exception {
	return nodeStartPageLookup.containsKey(node)
		? nodeStartPageLookup.get(node)
		: collector.getStartPageIndex(node);
}
/// <souhrn>
/// Načte index stránky, na které uzel končí, založený na 1.
/// </summary>
/// <param name="node">
/// Uzel.
/// </param>
/// <vrací>
/// Index stránky.
/// </returns>
public int getPageEnd(Node node) throws Exception {
	return nodeEndPageLookup.containsKey(node)
		? nodeEndPageLookup.get(node)
		: collector.getEndPageIndex(node);
}
/// <souhrn>
//Vrátí počet stránek, které zadaný uzel zabírá. Vrátí 1, pokud je uzel obsažen na jedné stránce.
/// </summary>
/// <param name="node">
/// Uzel.
/// </param>
/// <vrací>
/// Index stránky.
/// </returns>
public int pageSpan(Node node) throws Exception {
	return getPageEnd(node) - getPage(node) + 1;
}
/// <souhrn>
/// Vrátí seznam uzlů, které jsou obsaženy kdekoli na zadané stránce, nebo stránek, které odpovídají zadanému typu uzlu.
/// </summary>
/// <param name="startPage">
/// Úvodní stránka.
/// </param>
/// <param name="endPage">
/// Závěrečná stránka.
/// </param>
/// <param name="nodeType">
/// Typ uzlu.
/// </param>
/// <vrací>
/// <viz cref="IList{T}"/>.
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
		// Některé stránky mohou být prázdné.
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
/// <souhrn>
/// Rozdělí uzly, které se objevují na dvou nebo více stránkách, do samostatných uzlů, takže se stále zobrazují stejným způsobem
/// ale již se na stránce nezobrazí.
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
	// Navštivte jakékoli kompozity, které jsou případně rozděleny na stránky, a rozdělte je do samostatných uzlů.
	collector.getDocument().accept(new SectionSplitter(this));
}
/// <souhrn>
/// Toto je voláno <viz cref="SectionSplitter"/> k aktualizaci čísel stránek rozdělených uzlů.
/// </summary>
/// <param name="node">
/// Uzel.
/// </param>
/// <param name="startPage">
/// Úvodní stránka.
/// </param>
/// <param name="endPage">
/// Závěrečná stránka.
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
	// Přidejte každý uzel do seznamu, který představuje uzly nalezené na každé stránce.
	for (Node node : (Iterable<Node>) collector.getDocument().getChildNodes(NodeType.ANY, true))
	{
		//Záhlaví/zápatí následují po částech a nejsou rozděleny samy o sobě.
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
/// <souhrn>
/// Rozdělí text zadaného běhu na dva běhy.
/// Vloží nový běh těsně za určený běh.
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
/// <souhrn>
/// Rozdělí dokument na více sekcí tak, že každá stránka začíná a končí na hranici sekce.
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
	// Pokud existuje předchozí sekce, pokuste se zkopírovat všechna propojená zápatí záhlaví.
	// V opačném případě se neobjeví v extrahovaném dokumentu, pokud předchozí oddíl chybí.
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
	// Pokud odstavec obsahuje pouze konec oddílu, přidejte falešný run do.
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
		// Odstraňte číslování seznamu z klonovaného odstavce, ale ponechte odsazení stejné
		// protože odstavec má být součástí předchozí položky.
		if (paragraph.isListItem())
		{
			double textPosition = clonePara.getListFormat().getListLevel().getTextPosition();
			clonePara.getListFormat().removeNumbers();
			clonePara.getParagraphFormat().setLeftIndent(textPosition);
		}
		// Resetujte mezery rozdělených odstavců v tabulkách, protože další mezery mohou způsobit, že budou vypadat jinak.
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
		// Opravuje konec stránky na konci sekce.
		SplitPageBreakCorrector.processSection(cloneSection);
	}
	SplitPageBreakCorrector.processSection(section);
	// Přidejte také nové číslování stránek do těla sekce.
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
	// Uzel může zahrnovat více stránek, takže je vrácen seznam rozdělených pozic.
	//Rozdělený uzel je prvním uzlem na další stránce.
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
		// Pokud se stránka podřízeného uzlu změnila, jedná se o dělenou pozici.
		// Přidejte toto do seznamu.
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
	// Rozdělte kompozity pozpátku, takže klonované uzly jsou vloženy ve správném pořadí.
	Collections.reverse(splitList);
	return splitList;
}
private CompositeNode splitCompositeAtNode(CompositeNode baseNode, Node targetNode) throws Exception {
	CompositeNode cloneNode = (CompositeNode) baseNode.deepClone(false);
	Node node = targetNode;
	int currentPageNum = pageNumberFinder.getPage(baseNode);
	// Přesuňte všechny uzly nalezené na další stránce do zkopírovaného uzlu. Řadové uzly zpracujte samostatně.
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
		// Pokud se zabýváme řádkem, musíme přidat fiktivní buňky pro klonovaný řádek.
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
	// Vložte rozdělený uzel za originál.
	baseNode.getParentNode().insertAfter(cloneNode, baseNode);
	// Aktualizujte nová čísla stránek základního uzlu a klonovaného uzlu, včetně jeho potomků.
	// Bude to pouze jedna stránka, protože klonovaný kompozit je rozdělen tak, aby byl na jedné stránce.
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

## Závěr

Nyní jste se naučili, jak rozdělit dokument na samostatné stránky pomocí Aspose.Words for Java. Tato příručka poskytuje komplexní výukový program krok za krokem s příklady zdrojového kódu. Tento kód můžete dále přizpůsobit a rozšířit tak, aby vyhovoval vašim specifickým požadavkům při práci s dokumenty.
Jistě! Pojďme přidat sekci FAQ do našeho průvodce rozdělením dokumentů na stránky pomocí Aspose.Words for Java.

## FAQ

### Jak přidám Aspose.Words for Java do svého projektu?

Chcete-li do projektu přidat Aspose.Words for Java, postupujte takto:

1.  Stáhněte si knihovnu Aspose.Words for Java z[zde](https://releases.aspose.com/words/java/).
2. Přidejte stažený soubor JAR do cesty třídy vašeho projektu.
3. Nyní můžete ve svém projektu začít používat Aspose.Words for Java.

### Mohu rozdělit dokumenty v jiných formátech, jako je PDF nebo DOCX?

Ne, tato příručka se konkrétně zabývá rozdělením dokumentů ve formátu DOC pomocí Aspose.Words for Java. Pokud potřebujete rozdělit dokumenty do jiných formátů, možná budete muset prozkoumat další knihovny nebo nástroje, které tyto formáty podporují.

### Je Aspose.Words for Java bezplatná knihovna?

 Ne, Aspose.Words for Java není bezplatná knihovna. Jedná se o komerční produkt s licenčním poplatkem. Můžete navštívit[Cenová stránka Aspose.Words for Java](https://purchase.aspose.com/words/java) pro více informací o licencích a podrobnostech o cenách.

### Mohu rozdělit dokumenty na vlastní velikosti a formáty stránek?

Ano, můžete upravit velikosti a formáty stránek rozdělených dokumentů úpravou vlastností nastavení stránky v Aspose.Words for Java. Podrobnosti o tom, jak upravit nastavení stránky podle vašich požadavků, najdete v dokumentaci Aspose.Words.

### Existují nějaká omezení ohledně počtu stránek, které lze rozdělit?

Aspose.Words for Java neukládá konkrétní omezení počtu stránek, které můžete rozdělit. Mějte však na paměti, že velmi velké dokumenty mohou vyžadovat více paměti a více času na zpracování. Při práci s velkými dokumenty mějte na paměti systémové prostředky.

### Jak mohu zpracovat záhlaví a zápatí při rozdělování dokumentů?

Záhlaví a zápatí lze zpracovat při rozdělování dokumentů pomocí knihovny Aspose.Words for Java. Obsah záhlaví a zápatí můžete zkopírovat z původního dokumentu do rozdělených dokumentů a zajistit, aby byly správně zachovány. Možná budete muset tento proces přizpůsobit na základě vašich konkrétních požadavků na záhlaví a zápatí.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
