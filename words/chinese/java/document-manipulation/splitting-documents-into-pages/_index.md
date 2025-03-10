---
title: 在 Aspose.Words for Java 中将文档拆分为页面
linktitle: 将文档拆分为页面
second_title: Aspose.Words Java 文档处理 API
description: 了解如何使用 Aspose.Words for Java 将文档拆分为页面。带有源代码的分步指南，可实现高效的文档处理。
weight: 23
url: /zh/java/document-manipulation/splitting-documents-into-pages/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# 在 Aspose.Words for Java 中将文档拆分为页面


如果您使用 Java 进行文档处理，Aspose.Words for Java 是一个功能强大的 API，可以帮助您高效地将文档拆分为单独的页面。在本分步教程中，我们将指导您使用提供的源代码完成文档拆分过程。在本教程结束时，您将能够轻松拆分文档，从而提高您的文档管理能力。

## 1. 简介

Aspose.Words for Java 是一个 Java 库，允许您以编程方式操作 Word 文档。一项常见任务是将文档拆分为单独的页面，这可用于各种目的，例如存档、打印或文档处理。

## 2. 先决条件

在深入研究代码之前，请确保您已满足以下先决条件：

- 您的系统上安装了 Java 开发工具包 (JDK)。
- Aspose.Words for Java 库，您可以下载[这里](https://releases.aspose.com/words/java/).

## 3. 设置你的环境

首先，按如下方式设置您的开发环境：

- 在您首选的集成开发环境 (IDE) 中创建一个 Java 项目。
- 将 Aspose.Words for Java 库添加到您的项目中。您可以参考[文档](https://reference.aspose.com/words/java/)了解详细说明。

## 4. 理解源代码

您提供的源代码旨在将文档拆分为单独的页面。让我们分解一下关键组件：

```java
String fileName = FilenameUtils.getBaseName(docName);
String extensionName = FilenameUtils.getExtension(docName);
System.out.println("Processing document: " + fileName + "." + extensionName);
Document doc = new Document(docName);
```

- 我们提取输入文档的基本名称和扩展名。
- 我们使用 Aspose.Words for Java 加载文档。

## 5. 逐步拆分文档

### 5.1. 载入文档

```java
Document doc = new Document(docName);
```

在此步骤中，我们将输入文档加载到`Document`对象，它允许我们处理文档的内容。

### 5.2. 初始化 DocumentPageSplitter

```java
DocumentPageSplitter splitter = new DocumentPageSplitter(doc);
```

我们初始化一个`DocumentPageSplitter`对象与我们加载的文档。此类由 Aspose.Words for Java 提供，可帮助我们将文档拆分为页面。

### 5.3. 保存每一页

```java
for (int page = 1; page <= doc.getPageCount(); page++) {
    Document pageDoc = splitter.getDocumentOfPage(page);
    pageDoc.save("Your Directory Path" + MessageFormat.format("{0} - page{1}.{2}", fileName, page, extensionName));
}
```

在此步骤中，我们遍历文档的每一页并将其保存为单独的文档。您可以指定保存拆分页面的目录路径。

## 6.运行代码

要成功运行此代码，请确保您已设置环境并将 Aspose.Words for Java 库添加到您的项目中。然后，执行代码，您的文档将被拆分为单独的页面。

## DocumentPageSplitter 源代码

```java
//<摘要>
/// 将一个文档拆分为多个文档，每页一个。
/// </摘要>
class DocumentPageSplitter
{
private PageNumberFinder pageNumberFinder;
//<摘要>
/// 初始化 <see cref="DocumentPageSplitter"/> 类的新实例。
/// 此方法将文档分成几个部分，以便每个页面都以部分边界开始和结束。
/// 建议之后不要修改该文档。
/// </摘要>
/// <param name="source">源文档</param>
public DocumentPageSplitter(Document source) throws Exception
{
	pageNumberFinder = PageNumberFinderFactory.create(source);
}
private Document getDocument() {
	return pageNumberFinder.getDocument();
}
//<摘要>
/// 获取某一页的文档。
/// </摘要>
///<param name="pageIndex">
/// 1 为基础的页面索引。
/// </param>
/// <返回>
/// <see cref="文档"/>。
/// </返回>
public Document getDocumentOfPage(int pageIndex) throws Exception {
	return getDocumentOfPageRange(pageIndex, pageIndex);
}
//<摘要>
//获取某个页面范围的文档。
/// </摘要>
///<param name="startIndex">
/// 1 为基础的起始页索引。
/// </param>
///<param name="endIndex">
/// 结束页的基于 1 的索引。
/// </param>
/// <返回>
/// <see cref="文档"/>。
/// </返回>
public Document getDocumentOfPageRange(int startIndex, int endIndex) throws Exception {
	Document result = (Document) getDocument().deepClone(false);
	for (Node section : pageNumberFinder.retrieveAllNodesOnPages(startIndex, endIndex, NodeType.SECTION))
	{
		result.appendChild(result.importNode(section, true));
	}
	return result;
}
}
//<摘要>
/// 提供提取在指定页面上呈现的文档节点的方法。
/// </摘要>
class PageNumberFinder
{
//将节点映射到开始/结束页码。
//这用于在拆分文档时覆盖收集器提供的基线页码。
private Map<Node, Integer> nodeStartPageLookup = new HashMap<>();
private Map<Node, Integer> nodeEndPageLookup = new HashMap<>();
private LayoutCollector collector;
//将页码映射到该页面上找到的节点列表。
private Map<Integer, ArrayList<Node>> reversePageLookup;
//<摘要>
/// 初始化 <see cref="PageNumberFinder"/> 类的新实例。
/// </摘要>
/// <param name="collector">具有文档布局模型记录的收集器实例。</param>
public PageNumberFinder(LayoutCollector collector)
{
	this.collector = collector;
}
public Document getDocument()
{
	return collector.getDocument();
}
//<摘要>
/// 检索节点开始的页面的基于 1 的索引。
/// </摘要>
///<param name="节点">
/// 节点。
/// </param>
/// <返回>
/// 页面索引。
/// </返回>
public int getPage(Node node) throws Exception {
	return nodeStartPageLookup.containsKey(node)
		? nodeStartPageLookup.get(node)
		: collector.getStartPageIndex(node);
}
//<摘要>
/// 检索节点结束的页面的基于 1 的索引。
/// </摘要>
///<param name="节点">
/// 节点。
/// </param>
/// <返回>
/// 页面索引。
/// </返回>
public int getPageEnd(Node node) throws Exception {
	return nodeEndPageLookup.containsKey(node)
		? nodeEndPageLookup.get(node)
		: collector.getEndPageIndex(node);
}
//<摘要>
//返回指定节点跨越的页面数。如果节点包含在一页内，则返回 1。
/// </摘要>
///<param name="节点">
/// 节点。
/// </param>
/// <返回>
/// 页面索引。
/// </返回>
public int pageSpan(Node node) throws Exception {
	return getPageEnd(node) - getPage(node) + 1;
}
//<摘要>
/// 返回包含在指定页面或与指定节点类型匹配的页面上任何位置的节点列表。
/// </摘要>
///<param name="startPage">
/// 开始页。
/// </param>
///<param name="endPage">
/// 结束页面。
/// </param>
///<param name="节点类型">
/// 节点类型。
/// </param>
/// <返回>
/// <see cref="IList{T}"/>。
/// </返回>
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
		//有些页面可以是空的。
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
//<摘要>
/// 将出现在两个或更多页面上的节点拆分为单独的节点，以便它们仍然以相同的方式出现
///但不再出现在页面上。
/// </摘要>
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
	//访问可能跨页面拆分的任何复合体并将它们拆分为单独的节点。
	collector.getDocument().accept(new SectionSplitter(this));
}
//<摘要>
/// 这由 <see cref="SectionSplitter"/> 调用，以更新分割节点的页码。
/// </摘要>
///<param name="节点">
/// 节点。
/// </param>
///<param name="startPage">
/// 开始页。
/// </param>
///<param name="endPage">
/// 结束页面。
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
	//将每个节点添加到代表每个页面上的节点的列表中。
	for (Node node : (Iterable<Node>) collector.getDocument().getChildNodes(NodeType.ANY, true))
	{
		//页眉/页脚遵循章节并且不会自行分割。
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
//<摘要>
/// 将指定运行的文本拆分为两个运行。
/// 在指定运行之后插入新的运行。
/// </摘要>
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
//<摘要>
/// 将文档分成多个部分，以便每页以部分边界开始和结束。
/// </摘要>
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
	//如果有前一节，请尝试复制任何链接的页眉页脚。
	//否则，如果缺少前一节，它们将不会出现在提取的文档中。
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
	//如果段落仅包含分节符，则添加假分节符。
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
		//从克隆的段落中删除列表编号，但保留相同的缩进量
		//因为该段落应该是之前项目的一部分。
		if (paragraph.isListItem())
		{
			double textPosition = clonePara.getListFormat().getListLevel().getTextPosition();
			clonePara.getListFormat().removeNumbers();
			clonePara.getParagraphFormat().setLeftIndent(textPosition);
		}
		//重置表格中分割段落的间距，因为额外的间距可能会导致它们看起来不同。
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
		//更正该部分末尾的分页符。
		SplitPageBreakCorrector.processSection(cloneSection);
	}
	SplitPageBreakCorrector.processSection(section);
	//为章节正文添加新的页码。
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
	//一个节点可能跨越多个页面，因此会返回分割位置的列表。
	//拆分节点是下一页的第一个节点。
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
		//如果子节点的页面已经发生变化，那么这就是分裂的位置。
		//将其添加到列表中。
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
	//向后分割复合材料，以便克隆的节点按正确的顺序插入。
	Collections.reverse(splitList);
	return splitList;
}
private CompositeNode splitCompositeAtNode(CompositeNode baseNode, Node targetNode) throws Exception {
	CompositeNode cloneNode = (CompositeNode) baseNode.deepClone(false);
	Node node = targetNode;
	int currentPageNum = pageNumberFinder.getPage(baseNode);
	//将下一页找到的所有节点移至复制的节点中。单独处理行节点。
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
		//如果我们正在处理一行，我们需要为克隆的行添加虚拟单元格。
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
	//将分割节点插入到原节点之后。
	baseNode.getParentNode().insertAfter(cloneNode, baseNode);
	//更新基节点和克隆节点（包括其后代）的新页码。
	//由于克隆的复合页被拆分到一页上，因此这将仅仅是一页。
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

## 结论

您现在已经了解了如何使用 Aspose.Words for Java 将文档拆分为单独的页面。本指南提供了全面的分步教程和源代码示例。您可以进一步自定义和扩展此代码以满足处理文档时的特定要求。
当然！让我们在指南中添加一个常见问题解答部分，介绍如何使用 Aspose.Words for Java 将文档拆分为页面。

## 常见问题解答

### 如何将 Aspose.Words for Java 添加到我的项目中？

要将 Aspose.Words for Java 添加到您的项目，请按照以下步骤操作：

1. 从以下位置下载 Aspose.Words for Java 库[这里](https://releases.aspose.com/words/java/).
2. 将下载的 JAR 文件添加到项目的类路径。
3. 您现在可以在您的项目中开始使用 Aspose.Words for Java。

### 我可以拆分其他格式的文档吗，例如 PDF 或 DOCX？

不，本指南专门介绍如何使用 Aspose.Words for Java 拆分 DOC 格式的文档。如果您需要拆分其他格式的文档，则可能需要探索支持这些格式的其他库或工具。

### Aspose.Words for Java 是一个免费的库吗？

不，Aspose.Words for Java 不是免费库。它是一款需要许可费的商业产品。您可以访问[Aspose.Words for Java 定价页面](https://purchase.aspose.com/words/java)有关许可和定价细节的更多信息。

### 我可以将文档拆分为自定义页面大小和格式吗？

是的，您可以通过修改 Aspose.Words for Java 中的页面设置属性来自定义拆分文档的页面大小和格式。有关如何根据您的要求自定义页面设置的详细信息，请参阅 Aspose.Words 文档。

### 分割的页面数量有限制吗？

Aspose.Words for Java 对您可以拆分的页面数量没有具体限制。但是，请记住，非常大的文档可能需要更多内存和处理时间。处理大型文档时请注意系统资源。

### 拆分文档时如何处理页眉和页脚？

拆分文档时，可以使用 Aspose.Words for Java 库来处理页眉和页脚。您可以将页眉和页脚内容从原始文档复制到拆分的文档，确保它们正确保存。您可能需要根据特定的页眉和页脚要求自定义此过程。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
