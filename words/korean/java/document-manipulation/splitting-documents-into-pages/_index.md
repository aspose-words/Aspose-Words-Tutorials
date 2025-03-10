---
title: Aspose.Words for Java에서 문서를 페이지로 분할하기
linktitle: 문서를 페이지로 분할
second_title: Aspose.Words Java 문서 처리 API
description: Aspose.Words for Java를 사용하여 문서를 페이지로 분할하는 방법을 알아보세요. 효율적인 문서 처리를 위한 소스 코드가 포함된 단계별 가이드.
weight: 23
url: /ko/java/document-manipulation/splitting-documents-into-pages/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java에서 문서를 페이지로 분할하기


Java에서 문서 처리를 하는 경우 Aspose.Words for Java는 문서를 효율적으로 개별 페이지로 분할하는 데 도움이 되는 강력한 API입니다. 이 단계별 튜토리얼에서는 제공된 소스 코드를 사용하여 문서를 분할하는 과정을 안내합니다. 이 튜토리얼을 마치면 문서를 쉽게 분할하여 문서 관리 기능을 향상시킬 수 있습니다.

## 1. 서론

Aspose.Words for Java는 Word 문서를 프로그래밍 방식으로 조작할 수 있는 Java 라이브러리입니다. 일반적인 작업 중 하나는 문서를 여러 페이지로 분할하는 것으로, 보관, 인쇄 또는 문서 처리와 같은 다양한 목적에 유용할 수 있습니다.

## 2. 필수 조건

코드를 살펴보기 전에 다음과 같은 전제 조건이 충족되었는지 확인하세요.

- 시스템에 Java Development Kit(JDK)가 설치되어 있어야 합니다.
-  다운로드할 수 있는 Aspose.Words for Java 라이브러리[여기](https://releases.aspose.com/words/java/).

## 3. 환경 설정

시작하려면 다음과 같이 개발 환경을 설정하세요.

- 원하는 통합 개발 환경(IDE)에서 Java 프로젝트를 만듭니다.
- Aspose.Words for Java 라이브러리를 프로젝트에 추가하세요. 다음을 참조할 수 있습니다.[선적 서류 비치](https://reference.aspose.com/words/java/) 자세한 지침은 다음을 참조하세요.

## 4. 소스 코드 이해

제공하신 소스 코드는 문서를 여러 페이지로 분할하도록 설계되었습니다. 핵심 구성 요소를 분석해 보겠습니다.

```java
String fileName = FilenameUtils.getBaseName(docName);
String extensionName = FilenameUtils.getExtension(docName);
System.out.println("Processing document: " + fileName + "." + extensionName);
Document doc = new Document(docName);
```

- 입력 문서의 기본 이름과 확장자를 추출합니다.
- Java용 Aspose.Words를 사용하여 문서를 로드합니다.

## 5. 문서 분할 단계별

### 5.1. 문서 로딩

```java
Document doc = new Document(docName);
```

 이 단계에서는 입력 문서를 로드합니다.`Document` 문서의 내용을 다룰 수 있는 객체입니다.

### 5.2. DocumentPageSplitter 초기화

```java
DocumentPageSplitter splitter = new DocumentPageSplitter(doc);
```

 우리는 초기화합니다`DocumentPageSplitter` 로드된 문서가 있는 객체입니다. 이 클래스는 Aspose.Words for Java에서 제공하며 문서를 페이지로 분할하는 데 도움이 됩니다.

### 5.3. 각 페이지 저장하기

```java
for (int page = 1; page <= doc.getPageCount(); page++) {
    Document pageDoc = splitter.getDocumentOfPage(page);
    pageDoc.save("Your Directory Path" + MessageFormat.format("{0} - page{1}.{2}", fileName, page, extensionName));
}
```

이 단계에서는 문서의 각 페이지를 반복하고 이를 별도의 문서로 저장합니다. 분할된 페이지가 저장될 디렉토리 경로를 지정할 수 있습니다.

## 6. 코드 실행

이 코드를 성공적으로 실행하려면 환경을 설정하고 Aspose.Words for Java 라이브러리를 프로젝트에 추가했는지 확인하세요. 그런 다음 코드를 실행하면 문서가 별도의 페이지로 나뉩니다.

## DocumentPageSplitter 소스 코드

```java
/// <요약>
/// 문서를 페이지당 하나씩 여러 문서로 분할합니다.
/// </요약>
class DocumentPageSplitter
{
private PageNumberFinder pageNumberFinder;
/// <요약>
/// <see cref="DocumentPageSplitter"/> 클래스의 새 인스턴스를 초기화합니다.
/// 이 방법은 문서를 섹션으로 나누고 각 페이지가 섹션 경계에서 시작하고 끝나도록 합니다.
/// 이후에 문서를 수정하지 않는 것이 좋습니다.
/// </요약>
/// <param name="source">소스 문서</param>
public DocumentPageSplitter(Document source) throws Exception
{
	pageNumberFinder = PageNumberFinderFactory.create(source);
}
private Document getDocument() {
	return pageNumberFinder.getDocument();
}
/// <요약>
/// 페이지의 문서를 가져옵니다.
/// </요약>
/// <param name="pageIndex">
/// 페이지의 1 기반 인덱스.
/// </param>
/// <반환>
/// <see cref="Document"/>.
/// </반환>
public Document getDocumentOfPage(int pageIndex) throws Exception {
	return getDocumentOfPageRange(pageIndex, pageIndex);
}
/// <요약>
//페이지 범위의 문서를 가져옵니다.
/// </요약>
/// <param name="시작인덱스">
/// 시작 페이지의 1부터 시작하는 인덱스입니다.
/// </param>
/// <param name="endIndex">
/// 1부터 시작하는 마지막 페이지의 인덱스입니다.
/// </param>
/// <반환>
/// <see cref="Document"/>.
/// </반환>
public Document getDocumentOfPageRange(int startIndex, int endIndex) throws Exception {
	Document result = (Document) getDocument().deepClone(false);
	for (Node section : pageNumberFinder.retrieveAllNodesOnPages(startIndex, endIndex, NodeType.SECTION))
	{
		result.appendChild(result.importNode(section, true));
	}
	return result;
}
}
/// <요약>
/// 지정된 페이지에 렌더링되는 문서의 노드를 추출하는 방법을 제공합니다.
/// </요약>
class PageNumberFinder
{
// 노드를 시작/종료 페이지 번호에 매핑합니다.
// 이는 문서가 분할될 때 수집기에서 제공된 기준 페이지 번호를 재정의하는 데 사용됩니다.
private Map<Node, Integer> nodeStartPageLookup = new HashMap<>();
private Map<Node, Integer> nodeEndPageLookup = new HashMap<>();
private LayoutCollector collector;
// 페이지 번호를 해당 페이지에서 찾은 노드 목록에 매핑합니다.
private Map<Integer, ArrayList<Node>> reversePageLookup;
/// <요약>
/// <see cref="PageNumberFinder"/> 클래스의 새 인스턴스를 초기화합니다.
/// </요약>
/// <param name="collector">문서에 대한 레이아웃 모델 레코드가 있는 수집기 인스턴스입니다.</param>
public PageNumberFinder(LayoutCollector collector)
{
	this.collector = collector;
}
public Document getDocument()
{
	return collector.getDocument();
}
/// <요약>
/// 노드가 시작되는 페이지의 1부터 시작하는 인덱스를 검색합니다.
/// </요약>
/// <param 이름="노드">
/// 노드.
/// </param>
/// <반환>
/// 페이지 인덱스.
/// </반환>
public int getPage(Node node) throws Exception {
	return nodeStartPageLookup.containsKey(node)
		? nodeStartPageLookup.get(node)
		: collector.getStartPageIndex(node);
}
/// <요약>
/// 노드가 끝나는 페이지의 1부터 시작하는 인덱스를 검색합니다.
/// </요약>
/// <param 이름="노드">
/// 노드.
/// </param>
/// <반환>
/// 페이지 인덱스.
/// </반환>
public int getPageEnd(Node node) throws Exception {
	return nodeEndPageLookup.containsKey(node)
		? nodeEndPageLookup.get(node)
		: collector.getEndPageIndex(node);
}
/// <요약>
//지정된 노드가 몇 페이지에 걸쳐 있는지 반환합니다. 노드가 한 페이지에 포함되어 있으면 1을 반환합니다.
/// </요약>
/// <param 이름="노드">
/// 노드.
/// </param>
/// <반환>
/// 페이지 인덱스.
/// </반환>
public int pageSpan(Node node) throws Exception {
	return getPageEnd(node) - getPage(node) + 1;
}
/// <요약>
/// 지정된 페이지 또는 지정된 노드 유형과 일치하는 페이지의 아무 곳에나 포함된 노드 목록을 반환합니다.
/// </요약>
/// <param name="시작페이지">
/// 시작 페이지.
/// </param>
/// <param name="endPage">
/// 마지막 페이지.
/// </param>
/// <param 이름="노드 유형">
/// 노드 유형.
/// </param>
/// <반환>
/// <see cref="IList{T}"/>.
/// </반환>
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
		// 일부 페이지는 비어 있을 수 있습니다.
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
/// <요약>
/// 두 개 이상의 페이지에 나타나는 노드를 별도의 노드로 분할하여 동일한 방식으로 나타나도록 합니다.
/// 하지만 더 이상 전체 페이지에 나타나지 않습니다.
/// </요약>
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
	// 여러 페이지에 걸쳐 분할되어 있을 수 있는 합성물을 방문하여 이를 별도의 노드로 분할합니다.
	collector.getDocument().accept(new SectionSplitter(this));
}
/// <요약>
/// 이는 <see cref="SectionSplitter"/>에서 호출되어 분할 노드의 페이지 번호를 업데이트합니다.
/// </요약>
/// <param 이름="노드">
/// 노드.
/// </param>
/// <param name="시작페이지">
/// 시작 페이지.
/// </param>
/// <param name="endPage">
/// 마지막 페이지.
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
	// 각 페이지에서 발견된 노드를 나타내는 목록에 각 노드를 추가합니다.
	for (Node node : (Iterable<Node>) collector.getDocument().getChildNodes(NodeType.ANY, true))
	{
		//머리글/바닥글은 섹션 뒤에 오며 자체적으로 구분되지 않습니다.
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
/// <요약>
/// 지정된 실행의 텍스트를 두 개의 실행으로 분할합니다.
/// 지정된 실행 바로 뒤에 새로운 실행을 삽입합니다.
/// </요약>
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
/// <요약>
/// 문서를 여러 섹션으로 나누어 각 페이지가 섹션 경계에서 시작하고 끝나도록 합니다.
/// </요약>
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
	// 이전 섹션이 있는 경우 링크된 머리글과 바닥글을 모두 복사해 보세요.
	// 그렇지 않으면, 이전 섹션이 누락된 경우 추출된 문서에 나타나지 않습니다.
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
	// 문단에 섹션 나누기만 있는 경우, 가짜 런 인투를 추가합니다.
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
		// 복제된 문단에서 목록 번호를 제거하지만 들여쓰기는 그대로 둡니다.
		// 해당 문단은 이전 항목의 일부로 간주되기 때문입니다.
		if (paragraph.isListItem())
		{
			double textPosition = clonePara.getListFormat().getListLevel().getTextPosition();
			clonePara.getListFormat().removeNumbers();
			clonePara.getParagraphFormat().setLeftIndent(textPosition);
		}
		// 표에서 나뉜 문단의 간격을 다시 설정하세요. 간격을 늘리면 문단이 다르게 보일 수 있습니다.
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
		// 섹션의 끝에 있는 페이지 나누기를 수정합니다.
		SplitPageBreakCorrector.processSection(cloneSection);
	}
	SplitPageBreakCorrector.processSection(section);
	// 섹션 본문에도 새로운 페이지 번호를 추가합니다.
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
	// 노드는 여러 페이지에 걸쳐 있을 수 있으므로 분할된 위치 목록이 반환됩니다.
	//분할 노드는 다음 페이지의 첫 번째 노드입니다.
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
		// 자식 노드의 페이지가 변경된 경우 이는 분할 위치입니다.
		// 이 항목을 목록에 추가하세요.
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
	// 합성을 뒤로 분할하여 복제된 노드가 올바른 순서로 삽입되도록 합니다.
	Collections.reverse(splitList);
	return splitList;
}
private CompositeNode splitCompositeAtNode(CompositeNode baseNode, Node targetNode) throws Exception {
	CompositeNode cloneNode = (CompositeNode) baseNode.deepClone(false);
	Node node = targetNode;
	int currentPageNum = pageNumberFinder.getPage(baseNode);
	// 다음 페이지에서 찾은 모든 노드를 복사된 노드로 이동합니다. 행 노드를 별도로 처리합니다.
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
		// 행을 다루는 경우 복제된 행에 대한 더미 셀을 추가해야 합니다.
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
	// 원본 노드 뒤에 분할된 노드를 삽입합니다.
	baseNode.getParentNode().insertAfter(cloneNode, baseNode);
	// 기본 노드와 복제된 노드, 그리고 그 하위 노드의 새 페이지 번호를 업데이트합니다.
	// 복제된 합성물이 한 페이지로 분할되어 있으므로 이것은 단일 페이지만 됩니다.
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

## 결론

이제 Aspose.Words for Java를 사용하여 문서를 여러 페이지로 분할하는 방법을 배웠습니다. 이 가이드는 소스 코드 예제가 포함된 포괄적인 단계별 튜토리얼을 제공합니다. 문서 작업 시 특정 요구 사항을 충족하도록 이 코드를 추가로 사용자 지정하고 확장할 수 있습니다.
물론입니다! Aspose.Words for Java를 사용하여 문서를 페이지로 분할하는 방법에 대한 가이드에 FAQ 섹션을 추가해 보겠습니다.

## 자주 묻는 질문

### 내 프로젝트에 Aspose.Words for Java를 추가하려면 어떻게 해야 하나요?

프로젝트에 Aspose.Words for Java를 추가하려면 다음 단계를 따르세요.

1.  Java 라이브러리용 Aspose.Words를 다운로드하세요.[여기](https://releases.aspose.com/words/java/).
2. 다운로드한 JAR 파일을 프로젝트의 클래스 경로에 추가합니다.
3. 이제 프로젝트에서 Aspose.Words for Java를 사용할 수 있습니다.

### PDF나 DOCX 등 다른 형식의 문서를 분할할 수 있나요?

아니요, 이 가이드에서는 Aspose.Words for Java를 사용하여 DOC 형식의 문서를 분할하는 방법을 구체적으로 다룹니다. 다른 형식의 문서를 분할해야 하는 경우 해당 형식을 지원하는 다른 라이브러리나 도구를 탐색해야 할 수도 있습니다.

### Aspose.Words for Java는 무료 라이브러리인가요?

 아니요, Aspose.Words for Java는 무료 라이브러리가 아닙니다. 라이선스 수수료가 있는 상용 제품입니다. 다음을 방문할 수 있습니다.[Aspose.Words for Java 가격 페이지](https://purchase.aspose.com/words/java) 라이센싱 및 가격에 대한 자세한 내용은 여기를 참조하세요.

### 문서를 사용자 정의 페이지 크기와 형식으로 분할할 수 있나요?

네, Aspose.Words for Java에서 페이지 설정 속성을 수정하여 분할된 문서의 페이지 크기와 형식을 사용자 정의할 수 있습니다. 요구 사항에 따라 페이지 설정을 사용자 정의하는 방법에 대한 자세한 내용은 Aspose.Words 설명서를 참조하세요.

### 분할할 수 있는 페이지 수에 제한이 있나요?

Aspose.Words for Java는 분할할 수 있는 페이지 수에 대한 특정 제한을 부과하지 않습니다. 그러나 매우 큰 문서는 더 많은 메모리와 처리 시간이 필요할 수 있음을 명심하세요. 큰 문서로 작업할 때는 시스템 리소스를 염두에 두세요.

### 문서를 분할할 때 머리글과 바닥글을 어떻게 처리할 수 있나요?

Aspose.Words for Java 라이브러리를 사용하여 문서를 분할할 때 머리글과 바닥글을 처리할 수 있습니다. 원본 문서의 머리글과 바닥글 콘텐츠를 분할된 문서로 복사하여 올바르게 보존할 수 있습니다. 특정 머리글과 바닥글 요구 사항에 따라 이 프로세스를 사용자 지정해야 할 수도 있습니다.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
