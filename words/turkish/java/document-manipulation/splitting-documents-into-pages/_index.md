---
"description": "Java için Aspose.Words'ü kullanarak belgeleri sayfalara nasıl böleceğinizi öğrenin. Verimli belge işleme için kaynak kodlu adım adım kılavuz."
"linktitle": "Belgeleri Sayfalara Bölme"
"second_title": "Aspose.Words Java Belge İşleme API'si"
"title": "Java için Aspose.Words'de Belgeleri Sayfalara Bölme"
"url": "/tr/java/document-manipulation/splitting-documents-into-pages/"
"weight": 23
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Java için Aspose.Words'de Belgeleri Sayfalara Bölme


Java'da belge işlemeyle çalışıyorsanız, Aspose.Words for Java, belgeleri ayrı sayfalara verimli bir şekilde bölmenize yardımcı olabilecek güçlü bir API'dir. Bu adım adım eğitimde, sağlanan kaynak kodunu kullanarak belgeleri bölme sürecinde size rehberlik edeceğiz. Bu eğitimin sonunda, belgeleri kolayca bölebilecek ve belge yönetimi yeteneklerinizi geliştirebileceksiniz.

## 1. Giriş

Aspose.Words for Java, Word belgelerini programatik olarak düzenlemenize olanak tanıyan bir Java kütüphanesidir. Yaygın görevlerden biri, arşivleme, yazdırma veya belge işleme gibi çeşitli amaçlar için yararlı olabilen bir belgeyi ayrı sayfalara bölmektir.

## 2. Önkoşullar

Koda dalmadan önce aşağıdaki ön koşulların mevcut olduğundan emin olun:

- Sisteminizde Java Development Kit (JDK) yüklü.
- İndirebileceğiniz Java kütüphanesi için Aspose.Words [Burada](https://releases.aspose.com/words/java/).

## 3. Ortamınızı Ayarlama

Başlamak için geliştirme ortamınızı aşağıdaki şekilde ayarlayın:

- Tercih ettiğiniz Entegre Geliştirme Ortamında (IDE) bir Java projesi oluşturun.
- Projenize Aspose.Words for Java kütüphanesini ekleyin. Şuraya başvurabilirsiniz: [belgeleme](https://reference.aspose.com/words/java/) Ayrıntılı talimatlar için.

## 4. Kaynak Kodunu Anlamak

Sağladığınız kaynak kodu bir belgeyi ayrı sayfalara bölmek için tasarlanmıştır. Temel bileşenleri parçalayalım:

```java
String fileName = FilenameUtils.getBaseName(docName);
String extensionName = FilenameUtils.getExtension(docName);
System.out.println("Processing document: " + fileName + "." + extensionName);
Document doc = new Document(docName);
```

- Giriş belgesinin temel adını ve uzantısını çıkarıyoruz.
- Belgeyi Java için Aspose.Words'ü kullanarak yüklüyoruz.

## 5. Belgeleri Adım Adım Bölme

### 5.1. Belgenin Yüklenmesi

```java
Document doc = new Document(docName);
```

Bu adımda, giriş belgesini bir `Document` Belgenin içeriğiyle çalışmamızı sağlayan nesne.

### 5.2. DocumentPageSplitter'ı Başlatma

```java
DocumentPageSplitter splitter = new DocumentPageSplitter(doc);
```

Birini başlatıyoruz `DocumentPageSplitter` yüklenen belgemizle nesne. Bu sınıf Java için Aspose.Words tarafından sağlanır ve belgeyi sayfalara bölmemize yardımcı olur.

### 5.3. Her Sayfanın Kaydedilmesi

```java
for (int page = 1; page <= doc.getPageCount(); page++) {
    Document pageDoc = splitter.getDocumentOfPage(page);
    pageDoc.save("Your Directory Path" + MessageFormat.format("{0} - page{1}.{2}", fileName, page, extensionName));
}
```

Bu adımda, belgenin her sayfasını yineliyoruz ve ayrı bir belge olarak kaydediyoruz. Bölünmüş sayfaların kaydedileceği dizin yolunu belirtebilirsiniz.

## 6. Kodu Çalıştırma

Bu kodu başarıyla çalıştırmak için ortamınızı ayarladığınızdan ve projenize Aspose.Words for Java kütüphanesini eklediğinizden emin olun. Ardından kodu yürütün ve belgeniz ayrı sayfalara bölünecektir.

## DocumentPageSplitter Kaynak Kodu

```java
/// <özet>
/// Bir belgeyi her sayfada bir tane olacak şekilde birden fazla belgeye böler.
/// </özet>
class DocumentPageSplitter
{
private PageNumberFinder pageNumberFinder;
/// <özet>
/// <see cref="DocumentPageSplitter"/> sınıfının yeni bir örneğini başlatır.
/// Bu yöntem belgeyi bölümlere ayırır, böylece her sayfa bir bölüm sınırında başlar ve biter.
/// Daha sonra belge üzerinde değişiklik yapılmaması önerilir.
/// </özet>
/// <param name="source">Kaynak belge</param>
public DocumentPageSplitter(Document source) throws Exception
{
	pageNumberFinder = PageNumberFinderFactory.create(source);
}
private Document getDocument() {
	return pageNumberFinder.getDocument();
}
/// <özet>
/// Bir sayfanın belgesini alır.
/// </özet>
/// <param name="sayfaIndeksi">
/// 1 tabanlı bir sayfanın indeksi.
/// </param>
/// <geri döner>
/// <bkz. cref="Belge"/>.
/// </döndürür>
public Document getDocumentOfPage(int pageIndex) throws Exception {
	return getDocumentOfPageRange(pageIndex, pageIndex);
}
/// <özet>
/// Bir sayfa aralığının belgesini alır.
/// </özet>
/// <param name="startIndex">
/// Başlangıç sayfasının 1 tabanlı indeksi.
/// </param>
//<param name="endIndex">
/// 1-son sayfanın indeksi.
/// </param>
/// <geri döner>
/// <bkz. cref="Belge"/>.
/// </döndürür>
public Document getDocumentOfPageRange(int startIndex, int endIndex) throws Exception {
	Document result = (Document) getDocument().deepClone(false);
	for (Node section : pageNumberFinder.retrieveAllNodesOnPages(startIndex, endIndex, NodeType.SECTION))
	{
		result.appendChild(result.importNode(section, true));
	}
	return result;
}
}
/// <özet>
/// Belirtilen sayfalarda işlenen bir belgenin düğümlerini çıkarmak için yöntemler sağlar.
/// </özet>
class PageNumberFinder
{
// Harita düğümünü başlangıç/bitiş sayfa numaralarına göre ayarlar.
// Bu, belge bölündüğünde toplayıcı tarafından sağlanan temel sayfa numaralarını geçersiz kılmak için kullanılır.
private Map<Node, Integer> nodeStartPageLookup = new HashMap<>();
private Map<Node, Integer> nodeEndPageLookup = new HashMap<>();
private LayoutCollector collector;
// Sayfa numarasını, o sayfada bulunan düğümlerin listesine eşler.
private Map<Integer, ArrayList<Node>> reversePageLookup;
/// <özet>
/// <see cref="PageNumberFinder"/> sınıfının yeni bir örneğini başlatır.
/// </özet>
/// <param name="collector">Belge için düzen modeli kayıtlarına sahip bir toplayıcı örneği.</param>
public PageNumberFinder(LayoutCollector collector)
{
	this.collector = collector;
}
public Document getDocument()
{
	return collector.getDocument();
}
/// <özet>
/// Düğümün başladığı sayfanın 1 tabanlı dizinini alır.
/// </özet>
/// <param name="node">
/// Düğüm.
/// </param>
/// <geri döner>
/// Sayfa dizini.
/// </döndürür>
public int getPage(Node node) throws Exception {
	return nodeStartPageLookup.containsKey(node)
		? nodeStartPageLookup.get(node)
		: collector.getStartPageIndex(node);
}
/// <özet>
/// Düğümün sonlandığı sayfanın 1 tabanlı dizinini alır.
/// </özet>
/// <param name="node">
/// Düğüm.
/// </param>
/// <geri döner>
/// Sayfa dizini.
/// </döndürür>
public int getPageEnd(Node node) throws Exception {
	return nodeEndPageLookup.containsKey(node)
		? nodeEndPageLookup.get(node)
		: collector.getEndPageIndex(node);
}
/// <özet>
/// Belirtilen düğümün kaç sayfaya yayıldığını döndürür. Düğüm bir sayfada yer alıyorsa 1 döndürür.
/// </özet>
/// <param name="node">
/// Düğüm.
/// </param>
/// <geri döner>
/// Sayfa dizini.
/// </döndürür>
public int pageSpan(Node node) throws Exception {
	return getPageEnd(node) - getPage(node) + 1;
}
/// <özet>
/// Belirtilen sayfadaki veya sayfalardaki herhangi bir yerde bulunan ve belirtilen düğüm türüyle eşleşen düğümlerin listesini döndürür.
/// </özet>
/// <param name="başlangıçSayfası">
/// Başlangıç Sayfası.
/// </param>
/// <param name="endPage">
/// Son Sayfa.
/// </param>
/// <param name="nodeType">
/// Düğüm Türü.
/// </param>
/// <geri döner>
/// <bkz. cref="IList{T}"/>.
/// </döndürür>
public ArrayList<Node> retrieveAllNodesOnPages(int startPage, int endPage, /*Düğüm Türü*/int nodeType) throws Exception
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
		// Bazı sayfalar boş olabilir.
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
/// <özet>
/// İki veya daha fazla sayfada görünen düğümleri, aynı şekilde görünmeye devam etmeleri için ayrı düğümlere ayırır
/// ancak artık bir sayfada görünmüyor.
/// </özet>
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
	// Sayfalar arasında bölünmüş olabilecek tüm kompozitleri ziyaret edin ve bunları ayrı düğümlere bölün.
	collector.getDocument().accept(new SectionSplitter(this));
}
/// <özet>
/// Bu, bölünmüş düğümlerin sayfa numaralarını güncellemek için <see cref="SectionSplitter"/> tarafından çağrılır.
/// </özet>
/// <param name="node">
/// Düğüm.
/// </param>
/// <param name="başlangıçSayfası">
/// Başlangıç Sayfası.
/// </param>
/// <param name="endPage">
/// Son Sayfa.
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
	// Her düğümü, her sayfada bulunan düğümleri temsil eden bir listeye ekleyin.
	for (Node node : (Iterable<Node>) collector.getDocument().getChildNodes(NodeType.ANY, true))
	{
		// Üstbilgiler/Altbilgiler bölümleri takip eder ve kendi başlarına bölünmezler.
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
/// <özet>
/// Belirtilen çalışmanın metnini iki çalışmaya böler.
/// Belirtilen çalıştırmanın hemen sonrasına yeni çalıştırmayı ekler.
/// </özet>
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
/// <özet>
/// Bir belgeyi birden fazla bölüme ayırır, böylece her sayfa bir bölüm sınırında başlar ve biter.
/// </özet>
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
	// Önceki bir bölüm varsa, bağlantılı üstbilgi ve altbilgileri kopyalamayı deneyin.
	// Aksi takdirde, önceki bölüm eksikse çıkarılan belgede görünmezler.
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
	// Eğer paragraf sadece bölüm sonu içeriyorsa, sahte giriş ekleyin.
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
		// Klonlanmış paragraftan liste numaralandırmasını kaldırın ancak girintiyi aynı bırakın 
		// çünkü paragrafın kendisinden önceki maddenin bir parçası olması gerekiyor.
		if (paragraph.isListItem())
		{
			double textPosition = clonePara.getListFormat().getListLevel().getTextPosition();
			clonePara.getListFormat().removeNumbers();
			clonePara.getParagraphFormat().setLeftIndent(textPosition);
		}
		// Tablolardaki bölünmüş paragrafların aralıklarını sıfırlayın; çünkü ek aralıklar paragrafların farklı görünmesine neden olabilir.
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
		// Bölümün sonundaki sayfa sonunu düzeltir.
		SplitPageBreakCorrector.processSection(cloneSection);
	}
	SplitPageBreakCorrector.processSection(section);
	// Bölümün gövdesi için de yeni sayfa numaralandırması ekleyin.
	pageNumberFinder.addPageNumbersForNode(section.getBody(), pageNumberFinder.getPage(section),
		pageNumberFinder.getPageEnd(section));
	return ZiyaretçiEylemi.CONTINUE;
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
	// Bir düğüm birden fazla sayfaya yayılabilir, bu nedenle bölünmüş konumların bir listesi döndürülür.
	// Bölünmüş düğüm bir sonraki sayfadaki ilk düğümdür.
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
		// Eğer çocuk düğümün sayfası değiştiyse bu, bölünme pozisyonudur.
		// Bunu da listeye ekleyin.
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
	// Kompozitleri geriye doğru böl, böylece klonlanmış düğümler doğru sırayla eklenir.
	Collections.reverse(splitList);
	return splitList;
}
private CompositeNode splitCompositeAtNode(CompositeNode baseNode, Node targetNode) throws Exception {
	CompositeNode cloneNode = (CompositeNode) baseNode.deepClone(false);
	Node node = targetNode;
	int currentPageNum = pageNumberFinder.getPage(baseNode);
	// Sonraki sayfada bulunan tüm düğümleri kopyalanan düğüme taşıyın. Satır düğümlerini ayrı ayrı işleyin.
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
		// Eğer bir satırla uğraşıyorsak klonlanan satır için kukla hücreler eklememiz gerekir.
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
	// Bölünmüş düğümü orijinalin arkasına ekle.
	baseNode.getParentNode().insertAfter(cloneNode, baseNode);
	// Temel düğümün ve klonlanmış düğümün yeni sayfa numaralarını, alt düğümleri de dahil olmak üzere güncelleyin.
	// Klonlanmış bileşik tek bir sayfada olacak şekilde bölündüğünden bu yalnızca tek bir sayfa olacaktır.
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

## Çözüm

Artık Aspose.Words for Java kullanarak bir belgeyi ayrı sayfalara nasıl böleceğinizi öğrendiniz. Bu kılavuz, kaynak kod örnekleriyle kapsamlı bir adım adım eğitim sağlar. Belgelerle çalışırken özel gereksinimlerinizi karşılamak için bu kodu daha da özelleştirebilir ve genişletebilirsiniz.
Elbette! Aspose.Words for Java kullanarak belgeleri sayfalara bölmeye ilişkin kılavuzumuza bir SSS bölümü ekleyelim.

## SSS

### Aspose.Words for Java'yı projeme nasıl eklerim?

Projenize Aspose.Words for Java'yı eklemek için şu adımları izleyin:

1. Java için Aspose.Words kitaplığını şu adresten indirin: [Burada](https://releases.aspose.com/words/java/).
2. İndirdiğiniz JAR dosyasını projenizin sınıf yoluna ekleyin.
3. Artık projenizde Aspose.Words for Java'yı kullanmaya başlayabilirsiniz.

### PDF veya DOCX gibi diğer formatlardaki belgeleri bölebilir miyim?

Hayır, bu kılavuz özellikle Aspose.Words for Java kullanarak DOC formatındaki belgeleri bölmeyi ele alır. Belgeleri başka formatlarda bölmeniz gerekiyorsa, bu formatları destekleyen diğer kütüphaneleri veya araçları keşfetmeniz gerekebilir.

### Aspose.Words for Java ücretsiz bir kütüphane midir?

Hayır, Aspose.Words for Java ücretsiz bir kütüphane değildir. Lisans ücreti olan ticari bir üründür. Şurayı ziyaret edebilirsiniz: [Aspose.Words for Java fiyatlandırma sayfası](https://purchase.aspose.com/words/java) Lisanslama ve fiyatlandırma ayrıntıları hakkında daha fazla bilgi için.

### Belgeleri özel sayfa boyutlarına ve biçimlerine bölebilir miyim?

Evet, Aspose.Words for Java'daki sayfa kurulum özelliklerini değiştirerek bölünmüş belgelerin sayfa boyutlarını ve biçimlerini özelleştirebilirsiniz. Sayfa ayarlarını gereksinimlerinize göre nasıl özelleştireceğinizle ilgili ayrıntılar için Aspose.Words belgelerine bakın.

### Bölünebilecek sayfa sayısında herhangi bir sınırlama var mı?

Java için Aspose.Words bölebileceğiniz sayfa sayısı konusunda belirli sınırlamalar getirmez. Ancak, çok büyük belgelerin daha fazla bellek ve işlem süresi gerektirebileceğini unutmayın. Büyük belgelerle çalışırken sistem kaynaklarını göz önünde bulundurun.

### Belgeleri böldüğümde üstbilgi ve altbilgileri nasıl işleyebilirim?

Belgeleri bölerken Aspose.Words for Java kütüphanesini kullanarak başlıklar ve altbilgiler işlenebilir. Başlık ve altbilgi içeriğini orijinal belgeden bölünen belgelere kopyalayabilir ve bunların doğru şekilde korunduğundan emin olabilirsiniz. Bu işlemi belirli başlık ve altbilgi gereksinimlerinize göre özelleştirmeniz gerekebilir.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}