---
"description": "เรียนรู้วิธีแบ่งเอกสารออกเป็นหลายหน้าโดยใช้ Aspose.Words สำหรับ Java คำแนะนำทีละขั้นตอนพร้อมโค้ดต้นฉบับสำหรับการประมวลผลเอกสารอย่างมีประสิทธิภาพ"
"linktitle": "การแบ่งเอกสารออกเป็นหน้าต่างๆ"
"second_title": "API การประมวลผลเอกสาร Java ของ Aspose.Words"
"title": "การแบ่งเอกสารออกเป็นหน้าต่างๆ ใน Aspose.Words สำหรับ Java"
"url": "/th/java/document-manipulation/splitting-documents-into-pages/"
"weight": 23
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# การแบ่งเอกสารออกเป็นหน้าต่างๆ ใน Aspose.Words สำหรับ Java


หากคุณทำงานกับการประมวลผลเอกสารใน Java Aspose.Words สำหรับ Java คือ API ที่มีประสิทธิภาพที่จะช่วยให้คุณแบ่งเอกสารออกเป็นหน้าต่างๆ ได้อย่างมีประสิทธิภาพ ในบทช่วยสอนแบบทีละขั้นตอนนี้ เราจะแนะนำคุณตลอดกระบวนการแบ่งเอกสารโดยใช้โค้ดต้นฉบับที่ให้มา เมื่อจบบทช่วยสอนนี้ คุณจะสามารถแบ่งเอกสารได้อย่างง่ายดาย ซึ่งจะช่วยปรับปรุงความสามารถในการจัดการเอกสารของคุณ

## 1. บทนำ

Aspose.Words สำหรับ Java เป็นไลบรารี Java ที่ช่วยให้คุณสามารถจัดการเอกสาร Word ได้ด้วยโปรแกรม งานทั่วไปอย่างหนึ่งคือการแบ่งเอกสารออกเป็นหน้าต่างๆ ซึ่งอาจมีประโยชน์สำหรับวัตถุประสงค์ต่างๆ เช่น การจัดเก็บ การพิมพ์ หรือการประมวลผลเอกสาร

## 2. ข้อกำหนดเบื้องต้น

ก่อนที่จะเจาะลึกโค้ด โปรดตรวจสอบให้แน่ใจว่าคุณมีข้อกำหนดเบื้องต้นดังต่อไปนี้:

- Java Development Kit (JDK) ติดตั้งอยู่บนระบบของคุณ
- ไลบรารี Aspose.Words สำหรับ Java ซึ่งคุณสามารถดาวน์โหลดได้ [ที่นี่](https://releases-aspose.com/words/java/).

## 3. การตั้งค่าสภาพแวดล้อมของคุณ

ในการเริ่มต้น ให้ตั้งค่าสภาพแวดล้อมการพัฒนาของคุณดังต่อไปนี้:

- สร้างโครงการ Java ใน Integrated Development Environment (IDE) ที่คุณต้องการ
- เพิ่มไลบรารี Aspose.Words สำหรับ Java ลงในโปรเจ็กต์ของคุณ คุณสามารถดูได้ที่ [เอกสารประกอบ](https://reference.aspose.com/words/java/) สำหรับคำแนะนำโดยละเอียด

## 4. ทำความเข้าใจเกี่ยวกับซอร์สโค้ด

ซอร์สโค้ดที่คุณให้มาได้รับการออกแบบมาเพื่อแบ่งเอกสารออกเป็นหน้าต่างๆ กัน มาแยกส่วนประกอบหลักๆ กัน:

```java
String fileName = FilenameUtils.getBaseName(docName);
String extensionName = FilenameUtils.getExtension(docName);
System.out.println("Processing document: " + fileName + "." + extensionName);
Document doc = new Document(docName);
```

- เราแยกชื่อฐานและส่วนขยายของเอกสารอินพุต
- เราโหลดเอกสารโดยใช้ Aspose.Words สำหรับ Java

## 5. การแยกเอกสารทีละขั้นตอน

### 5.1. การโหลดเอกสาร

```java
Document doc = new Document(docName);
```

ในขั้นตอนนี้เราจะโหลดเอกสารอินพุตลงใน `Document` วัตถุที่ช่วยให้เราทำงานกับเนื้อหาของเอกสารได้

### 5.2. การเริ่มต้นใช้งาน DocumentPageSplitter

```java
DocumentPageSplitter splitter = new DocumentPageSplitter(doc);
```

เราเริ่มต้น `DocumentPageSplitter` วัตถุกับเอกสารที่เราโหลด คลาสนี้จัดทำโดย Aspose.Words สำหรับ Java และช่วยให้เราแบ่งเอกสารออกเป็นหน้าๆ

### 5.3. การบันทึกแต่ละหน้า

```java
for (int page = 1; page <= doc.getPageCount(); page++) {
    Document pageDoc = splitter.getDocumentOfPage(page);
    pageDoc.save("Your Directory Path" + MessageFormat.format("{0} - page{1}.{2}", fileName, page, extensionName));
}
```

ในขั้นตอนนี้ เราจะทำซ้ำในแต่ละหน้าของเอกสารและบันทึกเป็นเอกสารแยกกัน คุณสามารถระบุเส้นทางไดเรกทอรีที่จะบันทึกหน้าที่แยกได้

## 6. การรันโค้ด

หากต้องการเรียกใช้โค้ดนี้ให้สำเร็จ โปรดตรวจสอบว่าคุณได้ตั้งค่าสภาพแวดล้อมและเพิ่มไลบรารี Aspose.Words สำหรับ Java ลงในโปรเจ็กต์ของคุณแล้ว จากนั้นให้เรียกใช้โค้ด แล้วเอกสารของคุณจะถูกแบ่งออกเป็นหน้าต่างๆ

## รหัสต้นฉบับ DocumentPageSplitter

```java
/// <สรุป>
/// แบ่งเอกสารออกเป็นหลาย ๆ เอกสาร หนึ่งฉบับต่อหน้า
/// </สรุป>
class DocumentPageSplitter
{
private PageNumberFinder pageNumberFinder;
/// <สรุป>
/// เริ่มต้นอินสแตนซ์ใหม่ของคลาส <see cref="DocumentPageSplitter"/>
//วิธีการนี้จะแบ่งเอกสารออกเป็นส่วนๆ เพื่อให้แต่ละหน้าเริ่มต้นและสิ้นสุดที่ขอบเขตของส่วน
/// แนะนำให้ไม่แก้ไขเอกสารภายหลัง
/// </สรุป>
/// <param name="source">เอกสารต้นฉบับ</param>
public DocumentPageSplitter(Document source) throws Exception
{
	pageNumberFinder = PageNumberFinderFactory.create(source);
}
private Document getDocument() {
	return pageNumberFinder.getDocument();
}
/// <สรุป>
/// รับเอกสารของหน้า
/// </สรุป>
/// <param name="ดัชนีหน้า">
/// ดัชนีของหน้าแบบ 1
/// </พารามิเตอร์>
/// <กลับ>
/// <ดู cref="Document"/>
/// </กลับ>
public Document getDocumentOfPage(int pageIndex) throws Exception {
	return getDocumentOfPageRange(pageIndex, pageIndex);
}
/// <สรุป>
/// รับเอกสารของช่วงหน้า
/// </สรุป>
/// <param name="ดัชนีเริ่มต้น">
/// ดัชนีที่ 1 ของหน้าเริ่มต้น
/// </พารามิเตอร์>
//<param name="endIndex">
/// ดัชนีที่ 1 ของหน้าสุดท้าย
/// </พารามิเตอร์>
/// <กลับ>
/// <ดู cref="Document"/>
/// </กลับ>
public Document getDocumentOfPageRange(int startIndex, int endIndex) throws Exception {
	Document result = (Document) getDocument().deepClone(false);
	for (Node section : pageNumberFinder.retrieveAllNodesOnPages(startIndex, endIndex, NodeType.SECTION))
	{
		result.appendChild(result.importNode(section, true));
	}
	return result;
}
}
/// <สรุป>
/// ให้วิธีการในการแยกโหนดของเอกสารซึ่งจะแสดงผลบนหน้าที่ระบุ
/// </สรุป>
class PageNumberFinder
{
// โหนดแผนที่ไปยังหมายเลขหน้าเริ่มต้น/สิ้นสุด
// ใช้เพื่อแทนที่หมายเลขหน้าพื้นฐานที่ตัวรวบรวมให้ไว้เมื่อเอกสารถูกแยกออก
private Map<Node, Integer> nodeStartPageLookup = new HashMap<>();
private Map<Node, Integer> nodeEndPageLookup = new HashMap<>();
private LayoutCollector collector;
// แมปหมายเลขหน้าไปยังรายการโหนดที่พบในเพจนั้น
private Map<Integer, ArrayList<Node>> reversePageLookup;
/// <สรุป>
/// เริ่มต้นอินสแตนซ์ใหม่ของคลาส <see cref="PageNumberFinder"/>
/// </สรุป>
/// <param name="collector">อินสแตนซ์ตัวรวบรวมที่มีระเบียนโมเดลเค้าโครงสำหรับเอกสาร</param>
public PageNumberFinder(LayoutCollector collector)
{
	this.collector = collector;
}
public Document getDocument()
{
	return collector.getDocument();
}
/// <สรุป>
/// ดึงข้อมูลดัชนีแบบ 1 ของหน้าที่โหนดเริ่มต้น
/// </สรุป>
/// <param name="โหนด">
/// โหนด
/// </พารามิเตอร์>
/// <กลับ>
/// ดัชนีหน้า
/// </กลับ>
public int getPage(Node node) throws Exception {
	return nodeStartPageLookup.containsKey(node)
		? nodeStartPageLookup.get(node)
		: collector.getStartPageIndex(node);
}
/// <สรุป>
/// ดึงข้อมูลดัชนีพื้นฐาน 1 ของหน้าที่โหนดสิ้นสุด
/// </สรุป>
/// <param name="โหนด">
/// โหนด
/// </พารามิเตอร์>
/// <กลับ>
/// ดัชนีหน้า
/// </กลับ>
public int getPageEnd(Node node) throws Exception {
	return nodeEndPageLookup.containsKey(node)
		? nodeEndPageLookup.get(node)
		: collector.getEndPageIndex(node);
}
/// <สรุป>
/// ส่งคืนจำนวนหน้าที่โหนดที่ระบุครอบคลุม ส่งคืน 1 ถ้าโหนดอยู่ในหน้าเดียว
/// </สรุป>
/// <param name="โหนด">
/// โหนด
/// </พารามิเตอร์>
/// <กลับ>
/// ดัชนีหน้า
/// </กลับ>
public int pageSpan(Node node) throws Exception {
	return getPageEnd(node) - getPage(node) + 1;
}
/// <สรุป>
/// ส่งคืนรายการโหนดที่มีอยู่ในหน้าที่ระบุหรือหน้าต่างๆ ที่ตรงกับประเภทโหนดที่ระบุ
/// </สรุป>
/// <param name="หน้าเริ่มต้น">
/// หน้าเริ่มต้น
/// </พารามิเตอร์>
/// <param name="endPage">
/// หน้าจบ.
/// </พารามิเตอร์>
/// <param name="ประเภทโหนด">
/// ประเภทโหนด
/// </พารามิเตอร์>
/// <กลับ>
/// <ดู cref="IList{T}"/>.
/// </กลับ>
public ArrayList<Node> retrieveAllNodesOnPages(int startPage, int endPage, /*ประเภทโหนด*/int nodeType) throws Exception
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
		// บางหน้าอาจจะว่างเปล่า
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
/// <สรุป>
/// แยกโหนดที่ปรากฏบนเพจสองเพจหรือมากกว่าเป็นโหนดแยกกันเพื่อให้ยังคงปรากฏในลักษณะเดียวกัน
/// แต่ไม่ปรากฏข้ามหน้าอีกต่อไป
/// </สรุป>
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
	// เยี่ยมชมคอมโพสิตใดๆ ที่อาจแยกออกเป็นหลายหน้าและแยกออกเป็นโหนดแยกกัน
	collector.getDocument().accept(new SectionSplitter(this));
}
/// <สรุป>
/// เรียกโดย <see cref="SectionSplitter"/> เพื่ออัปเดตหมายเลขหน้าของโหนดที่แยก
/// </สรุป>
/// <param name="โหนด">
/// โหนด
/// </พารามิเตอร์>
/// <param name="หน้าเริ่มต้น">
/// หน้าเริ่มต้น
/// </พารามิเตอร์>
/// <param name="endPage">
/// หน้าจบ.
/// </พารามิเตอร์>
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
	// เพิ่มแต่ละโหนดลงในรายการที่แสดงถึงโหนดที่พบในแต่ละเพจ
	for (Node node : (Iterable<Node>) collector.getDocument().getChildNodes(NodeType.ANY, true))
	{
		// ส่วนหัว/ส่วนท้ายจะตามส่วนต่างๆ และไม่แยกโดยตัวของมันเอง
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
/// <สรุป>
/// แยกข้อความของการทำงานที่ระบุออกเป็นสองการทำงาน
/// แทรกการทำงานใหม่ทันทีหลังการทำงานที่ระบุ
/// </สรุป>
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
/// <สรุป>
/// แบ่งเอกสารออกเป็นหลายส่วนเพื่อให้แต่ละหน้าเริ่มต้นและสิ้นสุดที่ขอบเขตของส่วน
/// </สรุป>
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
	// หากมีส่วนก่อนหน้า ให้พยายามคัดลอกส่วนหัวส่วนท้ายที่เชื่อมโยงใดๆ
	// มิฉะนั้น จะไม่ปรากฏในเอกสารที่แยกออกมาถ้าส่วนก่อนหน้าหายไป
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
	// หากในย่อหน้ามีเพียงตัวแบ่งส่วน ให้เพิ่มการวิ่งปลอมเข้าไป
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
		// ลบการนับรายการออกจากย่อหน้าที่โคลน แต่ปล่อยให้การเยื้องเป็นเหมือนเดิม 
		// เนื่องจากย่อหน้าควรเป็นส่วนหนึ่งของรายการก่อนหน้านี้
		if (paragraph.isListItem())
		{
			double textPosition = clonePara.getListFormat().getListLevel().getTextPosition();
			clonePara.getListFormat().removeNumbers();
			clonePara.getParagraphFormat().setLeftIndent(textPosition);
		}
		// รีเซ็ตระยะห่างระหว่างย่อหน้าในตาราง เนื่องจากระยะห่างเพิ่มเติมอาจทำให้ตารางดูแตกต่างออกไป
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
		// แก้ไขการแบ่งหน้าที่ส่วนท้ายของส่วน
		SplitPageBreakCorrector.processSection(cloneSection);
	}
	SplitPageBreakCorrector.processSection(section);
	// เพิ่มการกำหนดหมายเลขหน้าใหม่สำหรับเนื้อหาของส่วนนั้นด้วย
	pageNumberFinder.addPageNumbersForNode(section.getBody(), pageNumberFinder.getPage(section),
		pageNumberFinder.getPageEnd(section));
	return การกระทำของผู้เยี่ยมชม.CONTINUE;
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
	// โหนดอาจขยายไปทั่วทั้งหลายหน้า ดังนั้นรายการตำแหน่งที่แยกจะถูกส่งคืน
	// โหนดที่แยกจะเป็นโหนดแรกในหน้าถัดไป
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
		// หากหน้าของโหนดย่อยมีการเปลี่ยนแปลง นี่คือตำแหน่งที่แยก
		// เพิ่มสิ่งนี้ลงในรายการ
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
	// แยกคอมโพสิตแบบถอยหลัง ดังนั้นโหนดโคลนจะถูกแทรกในลำดับที่ถูกต้อง
	Collections.reverse(splitList);
	return splitList;
}
private CompositeNode splitCompositeAtNode(CompositeNode baseNode, Node targetNode) throws Exception {
	CompositeNode cloneNode = (CompositeNode) baseNode.deepClone(false);
	Node node = targetNode;
	int currentPageNum = pageNumberFinder.getPage(baseNode);
	// ย้ายโหนดทั้งหมดที่พบในหน้าถัดไปไปยังโหนดที่คัดลอก จัดการโหนดแถวแยกกัน
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
		// หากเรากำลังจัดการกับแถว เราจะต้องเพิ่มเซลล์เสมือนให้กับแถวที่โคลน
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
	// แทรกโหนดแยกหลังต้นฉบับ
	baseNode.getParentNode().insertAfter(cloneNode, baseNode);
	// อัปเดตหมายเลขหน้าใหม่ของโหนดฐานและโหนดโคลน รวมถึงโหนดลูกหลานของมัน
	// นี่จะเป็นหน้าเดียวเท่านั้น เนื่องจากคอมโพสิตที่โคลนถูกแยกออกเพื่อให้อยู่ในหน้าเดียว
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

## บทสรุป

ตอนนี้คุณได้เรียนรู้วิธีแบ่งเอกสารออกเป็นหน้าต่างๆ โดยใช้ Aspose.Words สำหรับ Java แล้ว คู่มือนี้ประกอบด้วยบทช่วยสอนแบบทีละขั้นตอนอย่างครอบคลุมพร้อมตัวอย่างโค้ดต้นฉบับ คุณสามารถปรับแต่งและขยายโค้ดนี้เพิ่มเติมเพื่อตอบสนองความต้องการเฉพาะของคุณเมื่อทำงานกับเอกสาร
แน่นอน! มาเพิ่มส่วนคำถามที่พบบ่อยในคู่มือการแบ่งเอกสารออกเป็นหน้าต่างๆ โดยใช้ Aspose.Words สำหรับ Java กัน

## คำถามที่พบบ่อย

### ฉันจะเพิ่ม Aspose.Words สำหรับ Java ลงในโปรเจ็กต์ของฉันได้อย่างไร

หากต้องการเพิ่ม Aspose.Words สำหรับ Java ลงในโปรเจ็กต์ของคุณ ให้ทำตามขั้นตอนเหล่านี้:

1. ดาวน์โหลดไลบรารี Aspose.Words สำหรับ Java จาก [ที่นี่](https://releases-aspose.com/words/java/).
2. เพิ่มไฟล์ JAR ที่ดาวน์โหลดลงใน classpath ของโปรเจ็กต์ของคุณ
3. ตอนนี้คุณสามารถเริ่มใช้ Aspose.Words สำหรับ Java ในโปรเจ็กต์ของคุณได้แล้ว

### ฉันสามารถแยกเอกสารเป็นรูปแบบอื่นเช่น PDF หรือ DOCX ได้หรือไม่

ไม่ คู่มือนี้ครอบคลุมเฉพาะการแยกเอกสารในรูปแบบ DOC โดยใช้ Aspose.Words สำหรับ Java หากคุณจำเป็นต้องแยกเอกสารในรูปแบบอื่น คุณอาจต้องสำรวจไลบรารีหรือเครื่องมืออื่นที่รองรับรูปแบบเหล่านั้น

### Aspose.Words สำหรับ Java เป็นไลบรารีฟรีหรือไม่?

ไม่ Aspose.Words สำหรับ Java ไม่ใช่ไลบรารีฟรี มันเป็นผลิตภัณฑ์เชิงพาณิชย์ที่มีค่าธรรมเนียมใบอนุญาต คุณสามารถเยี่ยมชม [หน้าราคา Aspose.Words สำหรับ Java](https://purchase.aspose.com/words/java) เพื่อดูข้อมูลเพิ่มเติมเกี่ยวกับใบอนุญาตและรายละเอียดราคา

### ฉันสามารถแยกเอกสารให้เป็นขนาดและรูปแบบหน้าที่กำหนดเองได้หรือไม่

ใช่ คุณสามารถปรับแต่งขนาดและรูปแบบของหน้าเอกสารที่แยกได้โดยแก้ไขคุณสมบัติการตั้งค่าหน้าใน Aspose.Words สำหรับ Java โปรดดูเอกสาร Aspose.Words สำหรับรายละเอียดเกี่ยวกับวิธีการปรับแต่งการตั้งค่าหน้าตามความต้องการของคุณ

### มีข้อจำกัดใด ๆ เกี่ยวกับจำนวนหน้าที่สามารถแยกได้หรือไม่?

Aspose.Words สำหรับ Java ไม่มีข้อจำกัดเฉพาะเจาะจงเกี่ยวกับจำนวนหน้าที่คุณสามารถแบ่งได้ อย่างไรก็ตาม โปรดทราบว่าเอกสารขนาดใหญ่มากอาจต้องใช้หน่วยความจำและเวลาในการประมวลผลมากขึ้น โปรดคำนึงถึงทรัพยากรระบบเมื่อทำงานกับเอกสารขนาดใหญ่

### ฉันจะจัดการส่วนหัวและส่วนท้ายเมื่อแยกเอกสารได้อย่างไร

คุณสามารถจัดการส่วนหัวและส่วนท้ายได้เมื่อแบ่งเอกสารโดยใช้ไลบรารี Aspose.Words สำหรับ Java คุณสามารถคัดลอกเนื้อหาส่วนหัวและส่วนท้ายจากเอกสารต้นฉบับไปยังเอกสารที่แบ่งได้ เพื่อให้แน่ใจว่าเนื้อหาเหล่านั้นได้รับการรักษาไว้อย่างถูกต้อง คุณอาจต้องปรับแต่งกระบวนการนี้ตามความต้องการส่วนหัวและส่วนท้ายที่เฉพาะเจาะจงของคุณ


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}