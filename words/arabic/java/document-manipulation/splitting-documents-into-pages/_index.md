---
title: تقسيم المستندات إلى صفحات في Aspose.Words لـ Java
linktitle: تقسيم المستندات إلى صفحات
second_title: واجهة برمجة تطبيقات معالجة المستندات في Java Aspose.Words
description: تعرف على كيفية تقسيم المستندات إلى صفحات باستخدام Aspose.Words for Java. دليل خطوة بخطوة مع الكود المصدر لمعالجة المستندات بكفاءة.
weight: 23
url: /ar/java/document-manipulation/splitting-documents-into-pages/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# تقسيم المستندات إلى صفحات في Aspose.Words لـ Java


إذا كنت تعمل على معالجة المستندات في Java، فإن Aspose.Words for Java عبارة عن واجهة برمجة تطبيقات قوية يمكنها مساعدتك في تقسيم المستندات إلى صفحات منفصلة بكفاءة. في هذا البرنامج التعليمي خطوة بخطوة، سنرشدك خلال عملية تقسيم المستندات باستخدام الكود المصدر المقدم. بحلول نهاية هذا البرنامج التعليمي، ستتمكن من تقسيم المستندات بسهولة، مما يحسن من قدرات إدارة المستندات لديك.

## 1. المقدمة

Aspose.Words for Java هي مكتبة Java تتيح لك التعامل مع مستندات Word برمجيًا. إحدى المهام الشائعة هي تقسيم المستند إلى صفحات منفصلة، والتي يمكن أن تكون مفيدة لأغراض مختلفة، مثل الأرشفة أو الطباعة أو معالجة المستندات.

## 2. المتطلبات الأساسية

قبل أن نتعمق في الكود، تأكد من توفر المتطلبات الأساسية التالية:

- تم تثبيت Java Development Kit (JDK) على نظامك.
-  مكتبة Aspose.Words لـ Java، والتي يمكنك تنزيلها[هنا](https://releases.aspose.com/words/java/).

## 3. إعداد البيئة الخاصة بك

للبدء، قم بإعداد بيئة التطوير الخاصة بك على النحو التالي:

- قم بإنشاء مشروع Java في بيئة التطوير المتكاملة (IDE) المفضلة لديك.
- أضف مكتبة Aspose.Words for Java إلى مشروعك. يمكنك الرجوع إلى[التوثيق](https://reference.aspose.com/words/java/) للحصول على تعليمات مفصلة.

## 4. فهم الكود المصدر

تم تصميم الكود المصدر الذي قدمته لتقسيم المستند إلى صفحات منفصلة. دعنا نحلل المكونات الرئيسية:

```java
String fileName = FilenameUtils.getBaseName(docName);
String extensionName = FilenameUtils.getExtension(docName);
System.out.println("Processing document: " + fileName + "." + extensionName);
Document doc = new Document(docName);
```

- نقوم باستخراج الاسم الأساسي والامتداد للمستند المدخل.
- نقوم بتحميل المستند باستخدام Aspose.Words لـ Java.

## 5. تقسيم المستندات خطوة بخطوة

### 5.1. تحميل المستند

```java
Document doc = new Document(docName);
```

 في هذه الخطوة، نقوم بتحميل مستند الإدخال إلى`Document` الكائن الذي يسمح لنا بالعمل مع محتوى المستند.

### 5.2. تهيئة DocumentPageSplitter

```java
DocumentPageSplitter splitter = new DocumentPageSplitter(doc);
```

 نحن نقوم بتهيئة`DocumentPageSplitter` الكائن مع المستند الذي قمنا بتحميله. يتم توفير هذه الفئة بواسطة Aspose.Words لـ Java وتساعدنا في تقسيم المستند إلى صفحات.

### 5.3. حفظ كل صفحة

```java
for (int page = 1; page <= doc.getPageCount(); page++) {
    Document pageDoc = splitter.getDocumentOfPage(page);
    pageDoc.save("Your Directory Path" + MessageFormat.format("{0} - page{1}.{2}", fileName, page, extensionName));
}
```

في هذه الخطوة، نقوم بتكرار كل صفحة من المستند وحفظها كمستند منفصل. يمكنك تحديد مسار الدليل الذي سيتم حفظ الصفحات المقسمة فيه.

## 6. تشغيل الكود

لتشغيل هذا الكود بنجاح، تأكد من إعداد البيئة الخاصة بك وإضافة مكتبة Aspose.Words for Java إلى مشروعك. ثم قم بتنفيذ الكود، وستتمكن من تقسيم مستندك إلى صفحات منفصلة.

## كود مصدر DocumentPageSplitter

```java
/// <ملخص>
///تقسيم المستند إلى مستندات متعددة، مستند واحد لكل صفحة.
/// </ملخص>
class DocumentPageSplitter
{
private PageNumberFinder pageNumberFinder;
/// <ملخص>
//يقوم بتهيئة مثيل جديد لفئة <see cref="DocumentPageSplitter"/>.
//تقوم هذه الطريقة بتقسيم المستند إلى أقسام بحيث تبدأ كل صفحة وتنتهي عند حدود القسم.
///من المستحسن عدم تعديل المستند بعد ذلك.
/// </ملخص>
/// <param name="source">وثيقة المصدر</param>
public DocumentPageSplitter(Document source) throws Exception
{
	pageNumberFinder = PageNumberFinderFactory.create(source);
}
private Document getDocument() {
	return pageNumberFinder.getDocument();
}
/// <ملخص>
/// يحصل على مستند الصفحة.
/// </ملخص>
/// <param name="pageIndex">
/// 1-فهرس الصفحة.
/// </param>
/// <العودة>
/// <see cref="Document"/>.
/// </إرجاع>
public Document getDocumentOfPage(int pageIndex) throws Exception {
	return getDocumentOfPageRange(pageIndex, pageIndex);
}
/// <ملخص>
//يحصل على مستند نطاق الصفحات.
/// </ملخص>
/// <param name="startIndex">
/// 1-فهرس يعتمد على صفحة البداية.
/// </param>
/// <param name="endIndex">
/// 1-فهرس الصفحة النهائية.
/// </param>
/// <العودة>
/// <see cref="Document"/>.
/// </إرجاع>
public Document getDocumentOfPageRange(int startIndex, int endIndex) throws Exception {
	Document result = (Document) getDocument().deepClone(false);
	for (Node section : pageNumberFinder.retrieveAllNodesOnPages(startIndex, endIndex, NodeType.SECTION))
	{
		result.appendChild(result.importNode(section, true));
	}
	return result;
}
}
/// <ملخص>
/// توفر طرقًا لاستخراج عقد المستند التي يتم عرضها على صفحات محددة.
/// </ملخص>
class PageNumberFinder
{
// تعيين العقدة إلى أرقام الصفحة البداية/النهاية.
// يتم استخدام هذا لتجاوز أرقام الصفحات الأساسية التي يوفرها المجمع عند تقسيم المستند.
private Map<Node, Integer> nodeStartPageLookup = new HashMap<>();
private Map<Node, Integer> nodeEndPageLookup = new HashMap<>();
private LayoutCollector collector;
// تعيين رقم الصفحة إلى قائمة العقد الموجودة على تلك الصفحة.
private Map<Integer, ArrayList<Node>> reversePageLookup;
/// <ملخص>
//يقوم بتهيئة مثيل جديد لفئة <see cref="PageNumberFinder"/>.
/// </ملخص>
/// <param name="collector">مثال جامع يحتوي على سجلات نموذج التخطيط للمستند.</param>
public PageNumberFinder(LayoutCollector collector)
{
	this.collector = collector;
}
public Document getDocument()
{
	return collector.getDocument();
}
/// <ملخص>
/// يقوم باسترجاع الفهرس 1-based للصفحة التي تبدأ فيها العقدة.
/// </ملخص>
/// <param name="عقدة">
///العقدة.
/// </param>
/// <العودة>
/// فهرس الصفحة.
/// </إرجاع>
public int getPage(Node node) throws Exception {
	return nodeStartPageLookup.containsKey(node)
		? nodeStartPageLookup.get(node)
		: collector.getStartPageIndex(node);
}
/// <ملخص>
/// يقوم باسترجاع الفهرس 1-based للصفحة التي تنتهي بها العقدة.
/// </ملخص>
/// <param name="عقدة">
///العقدة.
/// </param>
/// <العودة>
/// فهرس الصفحة.
/// </إرجاع>
public int getPageEnd(Node node) throws Exception {
	return nodeEndPageLookup.containsKey(node)
		? nodeEndPageLookup.get(node)
		: collector.getEndPageIndex(node);
}
/// <ملخص>
//يُرجع عدد الصفحات التي تمتد عبرها العقدة المحددة. يُرجع 1 إذا كانت العقدة موجودة داخل صفحة واحدة.
/// </ملخص>
/// <param name="عقدة">
///العقدة.
/// </param>
/// <العودة>
/// فهرس الصفحة.
/// </إرجاع>
public int pageSpan(Node node) throws Exception {
	return getPageEnd(node) - getPage(node) + 1;
}
/// <ملخص>
///إرجاع قائمة بالعقد الموجودة في أي مكان على الصفحة أو الصفحات المحددة التي تطابق نوع العقدة المحدد.
/// </ملخص>
/// <param name="startPage">
/// صفحة البداية.
/// </param>
/// <param name="endPage">
/// الصفحة النهائية.
/// </param>
/// <param name="nodeType">
/// نوع العقدة.
/// </param>
/// <العودة>
/// <see cref="IList{T}"/>.
/// </إرجاع>
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
		// قد تكون بعض الصفحات فارغة.
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
/// <ملخص>
/// تقسيم العقد التي تظهر على صفحتين أو أكثر إلى عقد منفصلة بحيث تظل تظهر بنفس الطريقة
/// ولكنها لم تعد تظهر عبر الصفحة.
/// </ملخص>
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
	// قم بزيارة أي مركبات من الممكن تقسيمها عبر الصفحات وقم بتقسيمها إلى عقد منفصلة.
	collector.getDocument().accept(new SectionSplitter(this));
}
/// <ملخص>
//يتم استدعاء هذا بواسطة <see cref="SectionSplitter"/> لتحديث أرقام الصفحات الخاصة بالعقد المنقسمة.
/// </ملخص>
/// <param name="عقدة">
///العقدة.
/// </param>
/// <param name="startPage">
/// صفحة البداية.
/// </param>
/// <param name="endPage">
/// الصفحة النهائية.
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
	// أضف كل عقدة إلى القائمة التي تمثل العقد الموجودة في كل صفحة.
	for (Node node : (Iterable<Node>) collector.getDocument().getChildNodes(NodeType.ANY, true))
	{
		//تتبع الرؤوس والتذييلات الأقسام ولا يتم تقسيمها على حدة.
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
/// <ملخص>
///تقسيم نص التشغيل المحدد إلى تشغيلين.
/// يقوم بإدراج التشغيل الجديد بعد التشغيل المحدد مباشرةً.
/// </ملخص>
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
/// <ملخص>
/// تقسيم المستند إلى أقسام متعددة بحيث تبدأ كل صفحة وتنتهي عند حدود القسم.
/// </ملخص>
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
	// إذا كان هناك قسم سابق، حاول نسخ أي تذييلات ورؤوس صفحات مرتبطة.
	// وإلا فلن تظهر في المستند المستخرج إذا كان القسم السابق مفقودًا.
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
	// إذا كانت الفقرة تحتوي على فاصل قسم فقط، أضف فاصلًا وهميًا إليها.
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
		// قم بإزالة ترقيم القائمة من الفقرة المستنسخة ولكن اترك المسافة البادئة كما هي
		// حيث أن الفقرة من المفترض أن تكون جزءًا من العنصر السابق.
		if (paragraph.isListItem())
		{
			double textPosition = clonePara.getListFormat().getListLevel().getTextPosition();
			clonePara.getListFormat().removeNumbers();
			clonePara.getParagraphFormat().setLeftIndent(textPosition);
		}
		// قم بإعادة تعيين المسافات بين الفقرات المقسمة في الجداول، حيث أن المسافات الإضافية قد تؤدي إلى اختلاف مظهرها.
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
		// تصحيح كسر الصفحة في نهاية القسم.
		SplitPageBreakCorrector.processSection(cloneSection);
	}
	SplitPageBreakCorrector.processSection(section);
	// أضف ترقيمًا جديدًا للصفحات لجسم القسم أيضًا.
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
	// قد تمتد العقدة عبر صفحات متعددة، لذا يتم إرجاع قائمة بالمواضع المنقسمة.
	//العقدة المنقسمة هي العقدة الأولى في الصفحة التالية.
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
		// إذا تغيرت صفحة العقدة الفرعية، فهذا هو موضع الانقسام.
		// أضف هذا إلى القائمة.
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
	// تقسيم المركبات إلى الخلف، بحيث يتم إدراج العقد المستنسخة بالترتيب الصحيح.
	Collections.reverse(splitList);
	return splitList;
}
private CompositeNode splitCompositeAtNode(CompositeNode baseNode, Node targetNode) throws Exception {
	CompositeNode cloneNode = (CompositeNode) baseNode.deepClone(false);
	Node node = targetNode;
	int currentPageNum = pageNumberFinder.getPage(baseNode);
	// انقل جميع العقد الموجودة في الصفحة التالية إلى العقدة المنسوخة. تعامل مع عقد الصفوف بشكل منفصل.
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
		// إذا كنا نتعامل مع صف، فنحن بحاجة إلى إضافة خلايا وهمية للصف المستنسخ.
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
	// أدخل العقدة المنقسمة بعد الأصلية.
	baseNode.getParentNode().insertAfter(cloneNode, baseNode);
	// قم بتحديث أرقام الصفحات الجديدة للعقدة الأساسية والعقدة المستنسخة، بما في ذلك أحفادها.
	// ستكون هذه صفحة واحدة فقط حيث تم تقسيم المركب المستنسخ ليكون في صفحة واحدة.
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

## خاتمة

لقد تعلمت الآن كيفية تقسيم مستند إلى صفحات منفصلة باستخدام Aspose.Words for Java. يوفر هذا الدليل برنامجًا تعليميًا شاملاً خطوة بخطوة مع أمثلة على التعليمات البرمجية المصدرية. يمكنك تخصيص هذا الكود وتوسيعه بشكل أكبر لتلبية متطلباتك المحددة عند العمل مع المستندات.
بالتأكيد! دعنا نضيف قسم الأسئلة الشائعة إلى دليلنا حول تقسيم المستندات إلى صفحات باستخدام Aspose.Words for Java.

## الأسئلة الشائعة

### كيف أضيف Aspose.Words for Java إلى مشروعي؟

لإضافة Aspose.Words for Java إلى مشروعك، اتبع الخطوات التالية:

1.  قم بتنزيل مكتبة Aspose.Words لـ Java من[هنا](https://releases.aspose.com/words/java/).
2. أضف ملف JAR الذي تم تنزيله إلى مسار مشروعك.
3. يمكنك الآن البدء في استخدام Aspose.Words لـ Java في مشروعك.

### هل يمكنني تقسيم المستندات إلى تنسيقات أخرى، مثل PDF أو DOCX؟

لا، يتناول هذا الدليل على وجه التحديد تقسيم المستندات بتنسيق DOC باستخدام Aspose.Words for Java. إذا كنت بحاجة إلى تقسيم المستندات بتنسيقات أخرى، فقد تحتاج إلى استكشاف مكتبات أو أدوات أخرى تدعم هذه التنسيقات.

### هل Aspose.Words for Java مكتبة مجانية؟

 لا، Aspose.Words for Java ليست مكتبة مجانية. إنها منتج تجاري يتطلب رسوم ترخيص. يمكنك زيارة[صفحة تسعير Aspose.Words لـ Java](https://purchase.aspose.com/words/java) لمزيد من المعلومات حول تفاصيل الترخيص والتسعير.

### هل يمكنني تقسيم المستندات إلى أحجام وتنسيقات صفحات مخصصة؟

نعم، يمكنك تخصيص أحجام الصفحات وتنسيقات المستندات المقسمة عن طريق تعديل خصائص إعداد الصفحة في Aspose.Words for Java. راجع وثائق Aspose.Words للحصول على تفاصيل حول كيفية تخصيص إعدادات الصفحة وفقًا لمتطلباتك.

### هل هناك أي قيود على عدد الصفحات التي يمكن تقسيمها؟

لا يفرض Aspose.Words for Java قيودًا محددة على عدد الصفحات التي يمكنك تقسيمها. ومع ذلك، ضع في اعتبارك أن المستندات الكبيرة جدًا قد تتطلب مزيدًا من الذاكرة ووقت المعالجة. كن حريصًا على موارد النظام عند العمل مع مستندات كبيرة.

### كيف يمكنني التعامل مع الرؤوس والتذييلات عند تقسيم المستندات؟

يمكن التعامل مع الرؤوس والتذييلات عند تقسيم المستندات باستخدام مكتبة Aspose.Words for Java. يمكنك نسخ محتوى الرؤوس والتذييلات من المستند الأصلي إلى المستندات المقسمة، مع التأكد من حفظها بشكل صحيح. قد تحتاج إلى تخصيص هذه العملية بناءً على متطلبات الرؤوس والتذييلات الخاصة بك.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
