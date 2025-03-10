---
title: Разделение документов на страницы в Aspose.Words для Java
linktitle: Разделение документов на страницы
second_title: API обработки документов Java Aspose.Words
description: Узнайте, как разбить документы на страницы с помощью Aspose.Words для Java. Пошаговое руководство с исходным кодом для эффективной обработки документов.
weight: 23
url: /ru/java/document-manipulation/splitting-documents-into-pages/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Разделение документов на страницы в Aspose.Words для Java


Если вы работаете с обработкой документов в Java, Aspose.Words для Java — это мощный API, который поможет вам эффективно разбить документы на отдельные страницы. В этом пошаговом руководстве мы проведем вас через процесс разбиения документов с использованием предоставленного исходного кода. К концу этого руководства вы сможете легко разбивать документы, улучшая свои возможности управления документами.

## 1. Введение

Aspose.Words for Java — это библиотека Java, которая позволяет программно манипулировать документами Word. Одной из распространенных задач является разбиение документа на отдельные страницы, что может быть полезно для различных целей, таких как архивирование, печать или обработка документов.

## 2. Предпосылки

Прежде чем углубляться в код, убедитесь, что выполнены следующие предварительные условия:

- В вашей системе установлен Java Development Kit (JDK).
-  Библиотека Aspose.Words для Java, которую вы можете скачать[здесь](https://releases.aspose.com/words/java/).

## 3. Настройка вашей среды

Для начала настройте среду разработки следующим образом:

- Создайте проект Java в предпочитаемой вами интегрированной среде разработки (IDE).
- Добавьте библиотеку Aspose.Words for Java в свой проект. Вы можете обратиться к[документация](https://reference.aspose.com/words/java/) для получения подробных инструкций.

## 4. Понимание исходного кода

Исходный код, который вы предоставили, предназначен для разделения документа на отдельные страницы. Давайте разберем ключевые компоненты:

```java
String fileName = FilenameUtils.getBaseName(docName);
String extensionName = FilenameUtils.getExtension(docName);
System.out.println("Processing document: " + fileName + "." + extensionName);
Document doc = new Document(docName);
```

- Мы извлекаем базовое имя и расширение входного документа.
- Мы загружаем документ с помощью Aspose.Words для Java.

## 5. Разделение документов шаг за шагом

### 5.1 Загрузка документа

```java
Document doc = new Document(docName);
```

 На этом этапе мы загружаем входной документ в`Document` объект, который позволяет нам работать с содержимым документа.

### 5.2 Инициализация DocumentPageSplitter

```java
DocumentPageSplitter splitter = new DocumentPageSplitter(doc);
```

 Мы инициализируем`DocumentPageSplitter` объект с нашим загруженным документом. Этот класс предоставляется Aspose.Words для Java и помогает нам разбить документ на страницы.

### 5.3 Сохранение каждой страницы

```java
for (int page = 1; page <= doc.getPageCount(); page++) {
    Document pageDoc = splitter.getDocumentOfPage(page);
    pageDoc.save("Your Directory Path" + MessageFormat.format("{0} - page{1}.{2}", fileName, page, extensionName));
}
```

На этом этапе мы проходим по каждой странице документа и сохраняем ее как отдельный документ. Вы можете указать путь к каталогу, в котором будут сохранены разделенные страницы.

## 6. Запуск кода

Для успешного запуска этого кода убедитесь, что вы настроили свою среду и добавили библиотеку Aspose.Words for Java в свой проект. Затем выполните код, и ваш документ будет разделен на отдельные страницы.

## Исходный код DocumentPageSplitter

```java
/// <резюме>
/// Разбивает документ на несколько документов, по одному на страницу.
/// </резюме>
class DocumentPageSplitter
{
private PageNumberFinder pageNumberFinder;
/// <резюме>
/// Инициализирует новый экземпляр класса <see cref="DocumentPageSplitter"/>.
/// Этот метод разбивает документ на разделы таким образом, что каждая страница начинается и заканчивается на границе раздела.
/// Рекомендуется не изменять документ впоследствии.
/// </резюме>
/// <param name="source">Исходный документ</param>
public DocumentPageSplitter(Document source) throws Exception
{
	pageNumberFinder = PageNumberFinderFactory.create(source);
}
private Document getDocument() {
	return pageNumberFinder.getDocument();
}
/// <резюме>
/// Получает документ страницы.
/// </резюме>
/// <param name="pageIndex">
/// Индекс страницы, основанный на 1.
/// </параметр>
/// <возвращает>
/// <see cref="Документ"/>.
/// </возвращает>
public Document getDocumentOfPage(int pageIndex) throws Exception {
	return getDocumentOfPageRange(pageIndex, pageIndex);
}
/// <резюме>
//Получает документ диапазона страниц.
/// </резюме>
/// <param name="startIndex">
/// 1-й индекс стартовой страницы.
/// </параметр>
/// <param name="endIndex">
/// Индекс конечной страницы, основанный на 1.
/// </параметр>
/// <возвращает>
/// <see cref="Документ"/>.
/// </возвращает>
public Document getDocumentOfPageRange(int startIndex, int endIndex) throws Exception {
	Document result = (Document) getDocument().deepClone(false);
	for (Node section : pageNumberFinder.retrieveAllNodesOnPages(startIndex, endIndex, NodeType.SECTION))
	{
		result.appendChild(result.importNode(section, true));
	}
	return result;
}
}
/// <резюме>
/// Предоставляет методы для извлечения узлов документа, отображаемых на указанных страницах.
/// </резюме>
class PageNumberFinder
{
// Сопоставляет узел с номерами начальной/конечной страницы.
// Это используется для переопределения базовых номеров страниц, предоставленных сборщиком при разделении документа.
private Map<Node, Integer> nodeStartPageLookup = new HashMap<>();
private Map<Node, Integer> nodeEndPageLookup = new HashMap<>();
private LayoutCollector collector;
// Сопоставляет номер страницы со списком узлов, найденных на этой странице.
private Map<Integer, ArrayList<Node>> reversePageLookup;
/// <резюме>
/// Инициализирует новый экземпляр класса <see cref="PageNumberFinder"/>.
/// </резюме>
/// <param name="collector">Экземпляр коллектора, содержащий записи модели макета для документа.</param>
public PageNumberFinder(LayoutCollector collector)
{
	this.collector = collector;
}
public Document getDocument()
{
	return collector.getDocument();
}
/// <резюме>
/// Возвращает индекс страницы, на которой начинается узел, начиная с 1.
/// </резюме>
/// <имя параметра="узел">
/// Узел.
/// </параметр>
/// <возвращает>
/// Индекс страницы.
/// </возвращает>
public int getPage(Node node) throws Exception {
	return nodeStartPageLookup.containsKey(node)
		? nodeStartPageLookup.get(node)
		: collector.getStartPageIndex(node);
}
/// <резюме>
/// Возвращает индекс страницы, на которой заканчивается узел, начиная с 1.
/// </резюме>
/// <имя параметра="узел">
/// Узел.
/// </параметр>
/// <возвращает>
/// Индекс страницы.
/// </возвращает>
public int getPageEnd(Node node) throws Exception {
	return nodeEndPageLookup.containsKey(node)
		? nodeEndPageLookup.get(node)
		: collector.getEndPageIndex(node);
}
/// <резюме>
//Возвращает, сколько страниц охватывает указанный узел. Возвращает 1, если узел содержится в пределах одной страницы.
/// </резюме>
/// <имя параметра="узел">
/// Узел.
/// </параметр>
/// <возвращает>
/// Индекс страницы.
/// </возвращает>
public int pageSpan(Node node) throws Exception {
	return getPageEnd(node) - getPage(node) + 1;
}
/// <резюме>
/// Возвращает список узлов, содержащихся в любом месте указанной страницы или страниц, которые соответствуют указанному типу узла.
/// </резюме>
/// <param name="startPage">
/// Стартовая страница.
/// </параметр>
/// <имя параметра="endPage">
/// Последняя страница.
/// </параметр>
/// <param name="nodeType">
/// Тип узла.
/// </параметр>
/// <возвращает>
/// <see cref="IList{T}"/>.
/// </возвращает>
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
		// Некоторые страницы могут быть пустыми.
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
/// <резюме>
/// Разделяет узлы, которые отображаются на двух или более страницах, на отдельные узлы, так что они по-прежнему отображаются одинаково
/// но больше не появляются на странице.
/// </резюме>
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
	// Посетите все составные элементы, которые могут быть разделены на страницы, и разделите их на отдельные узлы.
	collector.getDocument().accept(new SectionSplitter(this));
}
/// <резюме>
/// Это вызывается <see cref="SectionSplitter"/> для обновления номеров страниц разделенных узлов.
/// </резюме>
/// <имя параметра="узел">
/// Узел.
/// </параметр>
/// <param name="startPage">
/// Стартовая страница.
/// </параметр>
/// <имя параметра="endPage">
/// Последняя страница.
/// </параметр>
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
	// Добавьте каждый узел в список, представляющий узлы, найденные на каждой странице.
	for (Node node : (Iterable<Node>) collector.getDocument().getChildNodes(NodeType.ANY, true))
	{
		//Верхние и нижние колонтитулы следуют за разделами и не разделяются сами по себе.
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
/// <резюме>
/// Разбивает текст указанного фрагмента на два фрагмента.
/// Вставляет новый прогон сразу после указанного прогона.
/// </резюме>
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
/// <резюме>
/// Разбивает документ на несколько разделов таким образом, что каждая страница начинается и заканчивается на границе раздела.
/// </резюме>
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
	// Если есть предыдущий раздел, попробуйте скопировать все связанные с ним верхние и нижние колонтитулы.
	// В противном случае они не будут отображаться в извлеченном документе, если предыдущий раздел отсутствует.
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
	// Если абзац содержит только разрыв раздела, добавьте фальшивый переход.
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
		// Удалить нумерацию списка из клонированного абзаца, но оставить отступ прежним.
		// поскольку абзац должен быть частью предыдущего пункта.
		if (paragraph.isListItem())
		{
			double textPosition = clonePara.getListFormat().getListLevel().getTextPosition();
			clonePara.getListFormat().removeNumbers();
			clonePara.getParagraphFormat().setLeftIndent(textPosition);
		}
		// Сбросьте интервалы между разделенными абзацами в таблицах, так как дополнительные интервалы могут привести к тому, что они будут выглядеть по-другому.
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
		// Исправляет разрыв страницы в конце раздела.
		SplitPageBreakCorrector.processSection(cloneSection);
	}
	SplitPageBreakCorrector.processSection(section);
	// Также добавьте новую нумерацию страниц для основной части раздела.
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
	// Узел может охватывать несколько страниц, поэтому возвращается список позиций разделения.
	//Разделенный узел — это первый узел на следующей странице.
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
		// Если страница дочернего узла изменилась, то это позиция разделения.
		// Добавьте это в список.
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
	// Разделите композиты в обратном порядке, чтобы клонированные узлы были вставлены в правильном порядке.
	Collections.reverse(splitList);
	return splitList;
}
private CompositeNode splitCompositeAtNode(CompositeNode baseNode, Node targetNode) throws Exception {
	CompositeNode cloneNode = (CompositeNode) baseNode.deepClone(false);
	Node node = targetNode;
	int currentPageNum = pageNumberFinder.getPage(baseNode);
	// Переместить все узлы, найденные на следующей странице, в скопированный узел. Обрабатывать узлы строк отдельно.
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
		// Если мы имеем дело со строкой, нам нужно добавить фиктивные ячейки для клонированной строки.
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
	// Вставьте разделенный узел после исходного.
	baseNode.getParentNode().insertAfter(cloneNode, baseNode);
	// Обновите новые номера страниц базового узла и клонированного узла, включая его потомков.
	// Это будет всего лишь одна страница, поскольку клонированный композит разделен на одну страницу.
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

## Заключение

Теперь вы узнали, как разделить документ на отдельные страницы с помощью Aspose.Words для Java. Это руководство содержит всеобъемлющее пошаговое руководство с примерами исходного кода. Вы можете дополнительно настроить и расширить этот код в соответствии с вашими конкретными требованиями при работе с документами.
Конечно! Давайте добавим раздел часто задаваемых вопросов в наше руководство по разделению документов на страницы с помощью Aspose.Words для Java.

## Часто задаваемые вопросы

### Как добавить Aspose.Words для Java в мой проект?

Чтобы добавить Aspose.Words для Java в свой проект, выполните следующие действия:

1.  Загрузите библиотеку Aspose.Words для Java с сайта[здесь](https://releases.aspose.com/words/java/).
2. Добавьте загруженный JAR-файл в classpath вашего проекта.
3. Теперь вы можете начать использовать Aspose.Words для Java в своем проекте.

### Можно ли разделять документы в других форматах, например PDF или DOCX?

Нет, это руководство специально охватывает разделение документов в формате DOC с использованием Aspose.Words для Java. Если вам нужно разделить документы в других форматах, вам может потребоваться изучить другие библиотеки или инструменты, которые поддерживают эти форматы.

### Является ли Aspose.Words для Java бесплатной библиотекой?

 Нет, Aspose.Words for Java — это не бесплатная библиотека. Это коммерческий продукт с лицензионной платой. Вы можете посетить[Страница с ценами на Aspose.Words для Java](https://purchase.aspose.com/words/java) для получения более подробной информации о лицензировании и ценах.

### Могу ли я разделить документы на страницы нестандартных размеров и форматов?

Да, вы можете настроить размеры и форматы страниц разделенных документов, изменив свойства настройки страницы в Aspose.Words для Java. Обратитесь к документации Aspose.Words за подробностями о том, как настроить параметры страницы в соответствии с вашими требованиями.

### Существуют ли ограничения на количество страниц, которые можно разделить?

Aspose.Words for Java не накладывает особых ограничений на количество страниц, которые можно разделить. Однако имейте в виду, что очень большие документы могут потребовать больше памяти и времени обработки. Будьте внимательны к системным ресурсам при работе с большими документами.

### Как обрабатывать верхние и нижние колонтитулы при разделении документов?

Верхние и нижние колонтитулы можно обрабатывать при разделении документов с помощью библиотеки Aspose.Words for Java. Вы можете копировать содержимое верхних и нижних колонтитулов из исходного документа в разделенные документы, гарантируя их корректное сохранение. Вам может потребоваться настроить этот процесс в соответствии с вашими конкретными требованиями к верхним и нижним колонтитулам.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
