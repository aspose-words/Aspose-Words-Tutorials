---
"description": "Tìm hiểu cách chia tài liệu thành các trang bằng Aspose.Words cho Java. Hướng dẫn từng bước với mã nguồn để xử lý tài liệu hiệu quả."
"linktitle": "Chia tài liệu thành các trang"
"second_title": "API xử lý tài liệu Java Aspose.Words"
"title": "Chia tài liệu thành các trang trong Aspose.Words cho Java"
"url": "/vi/java/document-manipulation/splitting-documents-into-pages/"
"weight": 23
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Chia tài liệu thành các trang trong Aspose.Words cho Java


Nếu bạn đang làm việc với xử lý tài liệu trong Java, Aspose.Words for Java là một API mạnh mẽ có thể giúp bạn chia tài liệu thành các trang riêng biệt một cách hiệu quả. Trong hướng dẫn từng bước này, chúng tôi sẽ hướng dẫn bạn quy trình chia tài liệu bằng mã nguồn được cung cấp. Đến cuối hướng dẫn này, bạn sẽ có thể chia tài liệu một cách dễ dàng, cải thiện khả năng quản lý tài liệu của mình.

## 1. Giới thiệu

Aspose.Words for Java là một thư viện Java cho phép bạn thao tác các tài liệu Word theo chương trình. Một tác vụ phổ biến là chia tài liệu thành các trang riêng biệt, có thể hữu ích cho nhiều mục đích khác nhau, chẳng hạn như lưu trữ, in ấn hoặc xử lý tài liệu.

## 2. Điều kiện tiên quyết

Trước khi tìm hiểu sâu hơn về mã, hãy đảm bảo bạn đã đáp ứng đủ các điều kiện tiên quyết sau:

- Bộ công cụ phát triển Java (JDK) được cài đặt trên hệ thống của bạn.
- Thư viện Aspose.Words cho Java, bạn có thể tải xuống [đây](https://releases.aspose.com/words/java/).

## 3. Thiết lập môi trường của bạn

Để bắt đầu, hãy thiết lập môi trường phát triển của bạn như sau:

- Tạo một dự án Java trong Môi trường phát triển tích hợp (IDE) mà bạn thích.
- Thêm thư viện Aspose.Words cho Java vào dự án của bạn. Bạn có thể tham khảo [tài liệu](https://reference.aspose.com/words/java/) để biết hướng dẫn chi tiết.

## 4. Hiểu mã nguồn

Mã nguồn bạn cung cấp được thiết kế để chia tài liệu thành các trang riêng biệt. Chúng ta hãy phân tích các thành phần chính:

```java
String fileName = FilenameUtils.getBaseName(docName);
String extensionName = FilenameUtils.getExtension(docName);
System.out.println("Processing document: " + fileName + "." + extensionName);
Document doc = new Document(docName);
```

- Chúng tôi trích xuất tên cơ sở và phần mở rộng của tài liệu đầu vào.
- Chúng tôi tải tài liệu bằng Aspose.Words cho Java.

## 5. Chia tách tài liệu từng bước

### 5.1. Tải Tài liệu

```java
Document doc = new Document(docName);
```

Trong bước này, chúng tôi tải tài liệu đầu vào vào một `Document` đối tượng cho phép chúng ta làm việc với nội dung của tài liệu.

### 5.2. Khởi tạo DocumentPageSplitter

```java
DocumentPageSplitter splitter = new DocumentPageSplitter(doc);
```

Chúng tôi khởi tạo một `DocumentPageSplitter` đối tượng với tài liệu đã tải của chúng tôi. Lớp này được cung cấp bởi Aspose.Words cho Java và giúp chúng tôi chia tài liệu thành các trang.

### 5.3. Lưu Mỗi Trang

```java
for (int page = 1; page <= doc.getPageCount(); page++) {
    Document pageDoc = splitter.getDocumentOfPage(page);
    pageDoc.save("Your Directory Path" + MessageFormat.format("{0} - page{1}.{2}", fileName, page, extensionName));
}
```

Trong bước này, chúng ta lặp lại từng trang của tài liệu và lưu dưới dạng một tài liệu riêng biệt. Bạn có thể chỉ định đường dẫn thư mục nơi các trang được chia sẽ được lưu.

## 6. Chạy mã

Để chạy mã này thành công, hãy đảm bảo bạn đã thiết lập môi trường và thêm thư viện Aspose.Words for Java vào dự án của mình. Sau đó, thực thi mã và bạn sẽ có tài liệu được chia thành các trang riêng biệt.

## Mã nguồn DocumentPageSplitter

```java
/// <tóm tắt>
/// Chia một tài liệu thành nhiều tài liệu, mỗi tài liệu trên một trang.
/// </tóm tắt>
class DocumentPageSplitter
{
private PageNumberFinder pageNumberFinder;
/// <tóm tắt>
/// Khởi tạo một phiên bản mới của lớp <xem cref="DocumentPageSplitter"/>.
/// Phương pháp này chia tài liệu thành nhiều phần sao cho mỗi trang bắt đầu và kết thúc tại một ranh giới phần.
/// Khuyến cáo không nên chỉnh sửa tài liệu sau đó.
/// </tóm tắt>
/// <param name="source">Tài liệu nguồn</param>
public DocumentPageSplitter(Document source) throws Exception
{
	pageNumberFinder = PageNumberFinderFactory.create(source);
}
private Document getDocument() {
	return pageNumberFinder.getDocument();
}
/// <tóm tắt>
/// Lấy nội dung tài liệu của một trang.
/// </tóm tắt>
/// <param name="pageIndex">
/// Chỉ mục dựa trên 1 trang.
/// </tham số>
/// <trở về>
/// <xem cref="Document"/>.
/// </trở về>
public Document getDocumentOfPage(int pageIndex) throws Exception {
	return getDocumentOfPageRange(pageIndex, pageIndex);
}
/// <tóm tắt>
/// Lấy tài liệu của một phạm vi trang.
/// </tóm tắt>
/// <param name="startIndex">
/// Chỉ mục dựa trên trang bắt đầu.
/// </tham số>
//<param name="endIndex">
/// Chỉ mục dựa trên trang cuối.
/// </tham số>
/// <trở về>
/// <xem cref="Document"/>.
/// </trở về>
public Document getDocumentOfPageRange(int startIndex, int endIndex) throws Exception {
	Document result = (Document) getDocument().deepClone(false);
	for (Node section : pageNumberFinder.retrieveAllNodesOnPages(startIndex, endIndex, NodeType.SECTION))
	{
		result.appendChild(result.importNode(section, true));
	}
	return result;
}
}
/// <tóm tắt>
/// Cung cấp các phương pháp trích xuất các nút của tài liệu được hiển thị trên các trang được chỉ định.
/// </tóm tắt>
class PageNumberFinder
{
// Ánh xạ nút tới số trang bắt đầu/kết thúc.
// Tính năng này được sử dụng để ghi đè số trang cơ sở do trình thu thập cung cấp khi tài liệu được chia nhỏ.
private Map<Node, Integer> nodeStartPageLookup = new HashMap<>();
private Map<Node, Integer> nodeEndPageLookup = new HashMap<>();
private LayoutCollector collector;
// Bản đồ số trang thành danh sách các nút tìm thấy trên trang đó.
private Map<Integer, ArrayList<Node>> reversePageLookup;
/// <tóm tắt>
/// Khởi tạo một phiên bản mới của lớp <xem cref="PageNumberFinder"/>.
/// </tóm tắt>
/// <param name="collector">Một thể hiện của trình thu thập có các bản ghi mô hình bố cục cho tài liệu.</param>
public PageNumberFinder(LayoutCollector collector)
{
	this.collector = collector;
}
public Document getDocument()
{
	return collector.getDocument();
}
/// <tóm tắt>
/// Truy xuất chỉ mục dựa trên 1 của trang mà nút bắt đầu.
/// </tóm tắt>
/// <param name="node">
/// Nút.
/// </tham số>
/// <trở về>
/// Mục lục trang.
/// </trở về>
public int getPage(Node node) throws Exception {
	return nodeStartPageLookup.containsKey(node)
		? nodeStartPageLookup.get(node)
		: collector.getStartPageIndex(node);
}
/// <tóm tắt>
/// Truy xuất chỉ mục dựa trên 1 của trang mà nút kết thúc.
/// </tóm tắt>
/// <param name="node">
/// Nút.
/// </tham số>
/// <trở về>
/// Mục lục trang.
/// </trở về>
public int getPageEnd(Node node) throws Exception {
	return nodeEndPageLookup.containsKey(node)
		? nodeEndPageLookup.get(node)
		: collector.getEndPageIndex(node);
}
/// <tóm tắt>
/// Trả về số trang mà nút được chỉ định trải dài. Trả về 1 nếu nút nằm trong một trang.
/// </tóm tắt>
/// <param name="node">
/// Nút.
/// </tham số>
/// <trở về>
/// Mục lục trang.
/// </trở về>
public int pageSpan(Node node) throws Exception {
	return getPageEnd(node) - getPage(node) + 1;
}
/// <tóm tắt>
/// Trả về danh sách các nút nằm ở bất kỳ đâu trên trang hoặc các trang được chỉ định khớp với loại nút được chỉ định.
/// </tóm tắt>
/// <param name="startPage">
/// Trang bắt đầu.
/// </tham số>
/// <param name="endPage">
/// Trang cuối.
/// </tham số>
/// <param name="nodeType">
/// Loại nút.
/// </tham số>
/// <trở về>
/// <xem cref="IList{T}"/>.
/// </trở về>
public ArrayList<Node> retrieveAllNodesOnPages(int startPage, int endPage, /*Kiểu nút*/int nodeType) throws Exception
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
		// Một số trang có thể trống.
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
/// <tóm tắt>
/// Chia các nút xuất hiện trên hai hoặc nhiều trang thành các nút riêng biệt để chúng vẫn xuất hiện theo cùng một cách
/// nhưng không còn xuất hiện trên toàn trang nữa.
/// </tóm tắt>
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
	// Truy cập bất kỳ nội dung tổng hợp nào có thể được chia thành nhiều trang và chia chúng thành các nút riêng biệt.
	collector.getDocument().accept(new SectionSplitter(this));
}
/// <tóm tắt>
/// Lệnh này được <xem cref="SectionSplitter"/> gọi để cập nhật số trang của các nút chia tách.
/// </tóm tắt>
/// <param name="node">
/// Nút.
/// </tham số>
/// <param name="startPage">
/// Trang bắt đầu.
/// </tham số>
/// <param name="endPage">
/// Trang cuối.
/// </tham số>
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
	// Thêm mỗi nút vào danh sách biểu diễn các nút có trên mỗi trang.
	for (Node node : (Iterable<Node>) collector.getDocument().getChildNodes(NodeType.ANY, true))
	{
		// Tiêu đề/Chân trang nằm theo các phần và không tách biệt riêng lẻ.
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
/// <tóm tắt>
/// Chia văn bản của chuỗi đã chỉ định thành hai chuỗi.
/// Chèn đoạn chạy mới ngay sau đoạn chạy đã chỉ định.
/// </tóm tắt>
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
/// <tóm tắt>
/// Chia một tài liệu thành nhiều phần sao cho mỗi trang bắt đầu và kết thúc tại một ranh giới phần.
/// </tóm tắt>
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
	// Nếu có phần trước, hãy thử sao chép bất kỳ phần đầu trang và chân trang nào được liên kết.
	// Nếu không, chúng sẽ không xuất hiện trong tài liệu được trích xuất nếu phần trước bị thiếu.
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
	// Nếu đoạn văn chỉ chứa ngắt phần, hãy thêm lệnh chạy vào giả.
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
		// Xóa số danh sách khỏi đoạn văn đã sao chép nhưng vẫn giữ nguyên thụt lề 
		// vì đoạn văn được cho là một phần của mục trước đó.
		if (paragraph.isListItem())
		{
			double textPosition = clonePara.getListFormat().getListLevel().getTextPosition();
			clonePara.getListFormat().removeNumbers();
			clonePara.getParagraphFormat().setLeftIndent(textPosition);
		}
		// Đặt lại khoảng cách giữa các đoạn văn được chia trong bảng vì khoảng cách bổ sung có thể khiến chúng trông khác đi.
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
		// Sửa lỗi ngắt trang ở cuối phần.
		SplitPageBreakCorrector.processSection(cloneSection);
	}
	SplitPageBreakCorrector.processSection(section);
	// Thêm số trang mới cho phần nội dung của phần này.
	pageNumberFinder.addPageNumbersForNode(section.getBody(), pageNumberFinder.getPage(section),
		pageNumberFinder.getPageEnd(section));
	return Hành động của khách truy cập.CONTINUE;
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
	// Một nút có thể trải dài trên nhiều trang, do đó danh sách các vị trí chia tách sẽ được trả về.
	// Nút chia tách là nút đầu tiên trên trang tiếp theo.
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
		// Nếu trang của nút con đã thay đổi thì đây là vị trí chia tách.
		// Thêm điều này vào danh sách.
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
	// Tách các hợp chất theo chiều ngược lại để các nút được sao chép được chèn theo đúng thứ tự.
	Collections.reverse(splitList);
	return splitList;
}
private CompositeNode splitCompositeAtNode(CompositeNode baseNode, Node targetNode) throws Exception {
	CompositeNode cloneNode = (CompositeNode) baseNode.deepClone(false);
	Node node = targetNode;
	int currentPageNum = pageNumberFinder.getPage(baseNode);
	// Di chuyển tất cả các nút được tìm thấy trên trang tiếp theo vào nút đã sao chép. Xử lý các nút hàng riêng biệt.
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
		// Nếu chúng ta đang xử lý một hàng, chúng ta cần thêm các ô giả cho hàng được sao chép.
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
	// Chèn nút chia tách vào sau nút gốc.
	baseNode.getParentNode().insertAfter(cloneNode, baseNode);
	// Cập nhật số trang mới của nút cơ sở và nút được sao chép, bao gồm cả nút con của nó.
	// Đây chỉ là một trang duy nhất vì bản sao tổng hợp được tách thành một trang.
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

## Phần kết luận

Bây giờ bạn đã học cách chia một tài liệu thành các trang riêng biệt bằng Aspose.Words for Java. Hướng dẫn này cung cấp hướng dẫn từng bước toàn diện với các ví dụ về mã nguồn. Bạn có thể tùy chỉnh và mở rộng thêm mã này để đáp ứng các yêu cầu cụ thể của mình khi làm việc với tài liệu.
Chắc chắn rồi! Chúng ta hãy thêm phần Câu hỏi thường gặp vào hướng dẫn của chúng tôi về cách chia tài liệu thành các trang bằng Aspose.Words cho Java.

## Câu hỏi thường gặp

### Làm thế nào để thêm Aspose.Words for Java vào dự án của tôi?

Để thêm Aspose.Words for Java vào dự án của bạn, hãy làm theo các bước sau:

1. Tải xuống thư viện Aspose.Words cho Java từ [đây](https://releases.aspose.com/words/java/).
2. Thêm tệp JAR đã tải xuống vào classpath của dự án.
3. Bây giờ bạn có thể bắt đầu sử dụng Aspose.Words cho Java trong dự án của mình.

### Tôi có thể tách tài liệu thành các định dạng khác như PDF hoặc DOCX không?

Không, hướng dẫn này đề cập cụ thể đến việc chia tách tài liệu ở định dạng DOC bằng Aspose.Words for Java. Nếu bạn cần chia tách tài liệu ở các định dạng khác, bạn có thể cần khám phá các thư viện hoặc công cụ khác hỗ trợ các định dạng đó.

### Aspose.Words cho Java có phải là thư viện miễn phí không?

Không, Aspose.Words for Java không phải là thư viện miễn phí. Đây là sản phẩm thương mại có phí cấp phép. Bạn có thể truy cập [Trang giá của Aspose.Words cho Java](https://purchase.aspose.com/words/java) để biết thêm thông tin về chi tiết cấp phép và giá cả.

### Tôi có thể chia tài liệu thành nhiều trang có kích thước và định dạng tùy chỉnh không?

Có, bạn có thể tùy chỉnh kích thước trang và định dạng của các tài liệu được chia nhỏ bằng cách sửa đổi các thuộc tính thiết lập trang trong Aspose.Words for Java. Tham khảo tài liệu Aspose.Words để biết chi tiết về cách tùy chỉnh cài đặt trang theo yêu cầu của bạn.

### Có giới hạn nào về số trang có thể tách không?

Aspose.Words for Java không áp đặt giới hạn cụ thể về số trang bạn có thể chia. Tuy nhiên, hãy nhớ rằng các tài liệu rất lớn có thể yêu cầu nhiều bộ nhớ và thời gian xử lý hơn. Hãy lưu ý đến tài nguyên hệ thống khi làm việc với các tài liệu lớn.

### Tôi có thể xử lý phần đầu trang và phần chân trang khi chia nhỏ tài liệu như thế nào?

Có thể xử lý tiêu đề và chân trang khi chia tài liệu bằng cách sử dụng thư viện Aspose.Words for Java. Bạn có thể sao chép nội dung tiêu đề và chân trang từ tài liệu gốc sang tài liệu đã chia, đảm bảo chúng được bảo quản đúng cách. Bạn có thể cần tùy chỉnh quy trình này dựa trên các yêu cầu tiêu đề và chân trang cụ thể của mình.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}