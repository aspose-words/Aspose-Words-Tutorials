---
"description": "Java के लिए Aspose.Words का उपयोग करके दस्तावेज़ों को पृष्ठों में विभाजित करना सीखें। कुशल दस्तावेज़ प्रसंस्करण के लिए स्रोत कोड के साथ चरण-दर-चरण मार्गदर्शिका।"
"linktitle": "दस्तावेज़ों को पृष्ठों में विभाजित करना"
"second_title": "Aspose.Words जावा दस्तावेज़ प्रसंस्करण एपीआई"
"title": "Java के लिए Aspose.Words में दस्तावेज़ों को पृष्ठों में विभाजित करना"
"url": "/hi/java/document-manipulation/splitting-documents-into-pages/"
"weight": 23
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Java के लिए Aspose.Words में दस्तावेज़ों को पृष्ठों में विभाजित करना


यदि आप जावा में दस्तावेज़ प्रसंस्करण के साथ काम कर रहे हैं, तो जावा के लिए Aspose.Words एक शक्तिशाली API है जो आपको दस्तावेज़ों को अलग-अलग पृष्ठों में कुशलतापूर्वक विभाजित करने में मदद कर सकता है। इस चरण-दर-चरण ट्यूटोरियल में, हम आपको दिए गए स्रोत कोड का उपयोग करके दस्तावेज़ों को विभाजित करने की प्रक्रिया के माध्यम से मार्गदर्शन करेंगे। इस ट्यूटोरियल के अंत तक, आप आसानी से दस्तावेज़ों को विभाजित करने में सक्षम होंगे, जिससे आपकी दस्तावेज़ प्रबंधन क्षमताएँ बेहतर होंगी।

## 1 परिचय

Aspose.Words for Java एक जावा लाइब्रेरी है जो आपको Word दस्तावेज़ों को प्रोग्रामेटिक रूप से मैनिपुलेट करने की अनुमति देती है। एक सामान्य कार्य दस्तावेज़ को अलग-अलग पृष्ठों में विभाजित करना है, जो विभिन्न उद्देश्यों के लिए उपयोगी हो सकता है, जैसे संग्रह करना, मुद्रण करना या दस्तावेज़ प्रसंस्करण।

## 2. पूर्वापेक्षाएँ

इससे पहले कि हम कोड में उतरें, सुनिश्चित करें कि आपके पास निम्नलिखित पूर्वापेक्षाएँ मौजूद हैं:

- आपके सिस्टम पर जावा डेवलपमेंट किट (JDK) स्थापित है।
- Aspose.Words for Java लाइब्रेरी, जिसे आप डाउनलोड कर सकते हैं [यहाँ](https://releases.aspose.com/words/java/).

## 3. अपना वातावरण तैयार करना

आरंभ करने के लिए, अपना विकास वातावरण इस प्रकार सेट करें:

- अपने पसंदीदा एकीकृत विकास वातावरण (IDE) में एक जावा प्रोजेक्ट बनाएं।
- अपने प्रोजेक्ट में Aspose.Words for Java लाइब्रेरी जोड़ें। आप इसका संदर्भ ले सकते हैं [प्रलेखन](https://reference.aspose.com/words/java/) विस्तृत निर्देशों के लिए कृपया देखें.

## 4. सोर्स कोड को समझना

आपके द्वारा प्रदान किया गया स्रोत कोड किसी दस्तावेज़ को अलग-अलग पृष्ठों में विभाजित करने के लिए डिज़ाइन किया गया है। आइए मुख्य घटकों को तोड़ें:

```java
String fileName = FilenameUtils.getBaseName(docName);
String extensionName = FilenameUtils.getExtension(docName);
System.out.println("Processing document: " + fileName + "." + extensionName);
Document doc = new Document(docName);
```

- हम इनपुट दस्तावेज़ का आधार नाम और एक्सटेंशन निकालते हैं।
- हम Java के लिए Aspose.Words का उपयोग करके दस्तावेज़ लोड करते हैं।

## 5. दस्तावेजों को चरण दर चरण विभाजित करना

### 5.1. दस्तावेज़ लोड करना

```java
Document doc = new Document(docName);
```

इस चरण में, हम इनपुट दस्तावेज़ को लोड करते हैं `Document` ऑब्जेक्ट, जो हमें दस्तावेज़ की सामग्री के साथ काम करने की अनुमति देता है।

### 5.2. डॉक्यूमेंटपेजस्प्लिटर को आरंभ करना

```java
DocumentPageSplitter splitter = new DocumentPageSplitter(doc);
```

हम एक आरंभीकरण करते हैं `DocumentPageSplitter` हमारे लोड किए गए दस्तावेज़ के साथ ऑब्जेक्ट। यह क्लास जावा के लिए Aspose.Words द्वारा प्रदान की जाती है और दस्तावेज़ को पृष्ठों में विभाजित करने में हमारी मदद करती है।

### 5.3. प्रत्येक पृष्ठ को सहेजना

```java
for (int page = 1; page <= doc.getPageCount(); page++) {
    Document pageDoc = splitter.getDocumentOfPage(page);
    pageDoc.save("Your Directory Path" + MessageFormat.format("{0} - page{1}.{2}", fileName, page, extensionName));
}
```

इस चरण में, हम दस्तावेज़ के प्रत्येक पृष्ठ को दोहराते हैं और इसे एक अलग दस्तावेज़ के रूप में सहेजते हैं। आप निर्देशिका पथ निर्दिष्ट कर सकते हैं जहाँ विभाजित पृष्ठ सहेजे जाएँगे।

## 6. कोड चलाना

इस कोड को सफलतापूर्वक चलाने के लिए, सुनिश्चित करें कि आपने अपना वातावरण सेट कर लिया है और अपने प्रोजेक्ट में Aspose.Words for Java लाइब्रेरी जोड़ ली है। फिर, कोड निष्पादित करें, और आपका दस्तावेज़ अलग-अलग पृष्ठों में विभाजित हो जाएगा।

## दस्तावेज़पेजस्प्लिटर स्रोत कोड

```java
/// <सारांश>
/// किसी दस्तावेज़ को प्रति पृष्ठ एक, अनेक दस्तावेज़ों में विभाजित करता है।
/// </सारांश>
class DocumentPageSplitter
{
private PageNumberFinder pageNumberFinder;
/// <सारांश>
/// <see cref="DocumentPageSplitter"/> वर्ग का एक नया उदाहरण आरंभ करता है।
/// यह विधि दस्तावेज़ को खंडों में विभाजित करती है ताकि प्रत्येक पृष्ठ एक खंड सीमा पर शुरू और समाप्त हो।
/// यह अनुशंसा की जाती है कि इसके बाद दस्तावेज़ में कोई संशोधन न किया जाए।
/// </सारांश>
/// <param name="source">स्रोत दस्तावेज़</param>
public DocumentPageSplitter(Document source) throws Exception
{
	pageNumberFinder = PageNumberFinderFactory.create(source);
}
private Document getDocument() {
	return pageNumberFinder.getDocument();
}
/// <सारांश>
/// किसी पृष्ठ का दस्तावेज़ प्राप्त करता है.
/// </सारांश>
/// <पैरामीटर नाम="पेजइंडेक्स">
/// 1-आधारित पृष्ठ अनुक्रमणिका.
/// </पैरा>
/// <रिटर्न>
/// <देखें cref="दस्तावेज़"/>.
/// </रिटर्न>
public Document getDocumentOfPage(int pageIndex) throws Exception {
	return getDocumentOfPageRange(pageIndex, pageIndex);
}
/// <सारांश>
/// किसी पृष्ठ श्रेणी का दस्तावेज़ प्राप्त करता है.
/// </सारांश>
/// <पैरामीटर नाम="प्रारंभसूचकांक">
/// 1-आधारित आरंभिक पृष्ठ का सूचकांक.
/// </पैरा>
//<पैरामीटर नाम="endIndex">
/// 1-आधारित अंतिम पृष्ठ का सूचकांक.
/// </पैरा>
/// <रिटर्न>
/// <देखें cref="दस्तावेज़"/>.
/// </रिटर्न>
public Document getDocumentOfPageRange(int startIndex, int endIndex) throws Exception {
	Document result = (Document) getDocument().deepClone(false);
	for (Node section : pageNumberFinder.retrieveAllNodesOnPages(startIndex, endIndex, NodeType.SECTION))
	{
		result.appendChild(result.importNode(section, true));
	}
	return result;
}
}
/// <सारांश>
/// निर्दिष्ट पृष्ठों पर प्रस्तुत दस्तावेज़ के नोड्स को निकालने के लिए विधियाँ प्रदान करता है।
/// </सारांश>
class PageNumberFinder
{
// नोड को आरंभ/अंत पृष्ठ संख्या पर मैप करता है।
// इसका उपयोग दस्तावेज़ को विभाजित करते समय कलेक्टर द्वारा प्रदान की गई आधार रेखा पृष्ठ संख्या को ओवरराइड करने के लिए किया जाता है।
private Map<Node, Integer> nodeStartPageLookup = new HashMap<>();
private Map<Node, Integer> nodeEndPageLookup = new HashMap<>();
private LayoutCollector collector;
// पृष्ठ संख्या को उस पृष्ठ पर पाए जाने वाले नोड्स की सूची से मैप करता है।
private Map<Integer, ArrayList<Node>> reversePageLookup;
/// <सारांश>
/// <see cref="PageNumberFinder"/> वर्ग का एक नया उदाहरण आरंभ करता है।
/// </सारांश>
/// <param name="collector">एक कलेक्टर इंस्टेंस जिसमें दस्तावेज़ के लिए लेआउट मॉडल रिकॉर्ड हैं.</param>
public PageNumberFinder(LayoutCollector collector)
{
	this.collector = collector;
}
public Document getDocument()
{
	return collector.getDocument();
}
/// <सारांश>
/// नोड जिस पृष्ठ से आरंभ होता है, उसका 1-आधारित अनुक्रमणिका पुनर्प्राप्त करता है।
/// </सारांश>
/// <पैरामीटर नाम="नोड">
/// नोड.
/// </पैरा>
/// <रिटर्न>
/// पृष्ठ अनुक्रमणिका.
/// </रिटर्न>
public int getPage(Node node) throws Exception {
	return nodeStartPageLookup.containsKey(node)
		? nodeStartPageLookup.get(node)
		: collector.getStartPageIndex(node);
}
/// <सारांश>
/// उस पृष्ठ का 1-आधारित अनुक्रमणिका पुनर्प्राप्त करता है जिस पर नोड समाप्त होता है।
/// </सारांश>
/// <पैरामीटर नाम="नोड">
/// नोड.
/// </पैरा>
/// <रिटर्न>
/// पृष्ठ अनुक्रमणिका.
/// </रिटर्न>
public int getPageEnd(Node node) throws Exception {
	return nodeEndPageLookup.containsKey(node)
		? nodeEndPageLookup.get(node)
		: collector.getEndPageIndex(node);
}
/// <सारांश>
/// यह बताता है कि निर्दिष्ट नोड कितने पृष्ठों पर फैला हुआ है। यदि नोड एक पृष्ठ में समाहित है तो 1 लौटाता है।
/// </सारांश>
/// <पैरामीटर नाम="नोड">
/// नोड.
/// </पैरा>
/// <रिटर्न>
/// पृष्ठ अनुक्रमणिका.
/// </रिटर्न>
public int pageSpan(Node node) throws Exception {
	return getPageEnd(node) - getPage(node) + 1;
}
/// <सारांश>
/// निर्दिष्ट पृष्ठ या पृष्ठों पर कहीं भी मौजूद नोड्स की सूची लौटाता है जो निर्दिष्ट नोड प्रकार से मेल खाते हैं।
/// </सारांश>
/// <पैरामीटर नाम="प्रारंभपृष्ठ">
/// प्रारंभ पृष्ठ.
/// </पैरा>
/// <पैरामीटर नाम="endPage">
/// अंतिम पृष्ठ.
/// </पैरा>
/// <पैरामीटर नाम="नोडटाइप">
/// नोड प्रकार.
/// </पैरा>
/// <रिटर्न>
/// <देखें cref="IList{T}"/>.
/// </रिटर्न>
public ArrayList<Node> retrieveAllNodesOnPages(int startPage, int endPage, /*नोड प्रकार*/int nodeType) throws Exception
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
		// कुछ पृष्ठ रिक्त हो सकते हैं.
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
/// <सारांश>
/// दो या अधिक पृष्ठों पर दिखाई देने वाले नोड्स को अलग-अलग नोड्स में विभाजित करता है ताकि वे अभी भी एक ही तरह से दिखाई दें
/// लेकिन अब यह पूरे पृष्ठ पर दिखाई नहीं देगा।
/// </सारांश>
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
	// किसी भी ऐसे कंपोजिट पर जाएं जो संभवतः पृष्ठों में विभाजित हैं और उन्हें अलग-अलग नोड्स में विभाजित करें।
	collector.getDocument().accept(new SectionSplitter(this));
}
/// <सारांश>
/// इसे विभाजित नोड्स की पृष्ठ संख्या को अद्यतन करने के लिए <see cref="SectionSplitter"/> द्वारा बुलाया जाता है।
/// </सारांश>
/// <पैरामीटर नाम="नोड">
/// नोड.
/// </पैरा>
/// <पैरामीटर नाम="प्रारंभपृष्ठ">
/// प्रारंभ पृष्ठ.
/// </पैरा>
/// <पैरामीटर नाम="endPage">
/// अंतिम पृष्ठ.
/// </पैरा>
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
	// प्रत्येक नोड को एक सूची में जोड़ें जो प्रत्येक पृष्ठ पर पाए गए नोड्स का प्रतिनिधित्व करती है।
	for (Node node : (Iterable<Node>) collector.getDocument().getChildNodes(NodeType.ANY, true))
	{
		// शीर्षलेख/पादलेख अनुभागों का अनुसरण करते हैं तथा स्वयं विभाजित नहीं होते।
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
/// <सारांश>
/// निर्दिष्ट रन के पाठ को दो रन में विभाजित करता है।
/// निर्दिष्ट रन के ठीक बाद नया रन सम्मिलित करता है।
/// </सारांश>
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
/// <सारांश>
/// दस्तावेज़ को एकाधिक अनुभागों में विभाजित करता है ताकि प्रत्येक पृष्ठ एक अनुभाग सीमा पर शुरू और समाप्त हो।
/// </सारांश>
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
	// यदि कोई पिछला अनुभाग है, तो किसी भी लिंक किए गए हेडर फ़ुटर को कॉपी करने का प्रयास करें।
	// अन्यथा, यदि पिछला अनुभाग गायब है तो वे निकाले गए दस्तावेज़ में दिखाई नहीं देंगे।
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
	// यदि पैराग्राफ में केवल खंड विराम है, तो नकली रन जोड़ें।
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
		// क्लोन किए गए पैराग्राफ से सूची क्रमांकन हटा दें लेकिन इंडेंट को वही रहने दें 
		// क्योंकि यह पैराग्राफ़ पहले वाले आइटम का हिस्सा माना जाता है।
		if (paragraph.isListItem())
		{
			double textPosition = clonePara.getListFormat().getListLevel().getTextPosition();
			clonePara.getListFormat().removeNumbers();
			clonePara.getParagraphFormat().setLeftIndent(textPosition);
		}
		// तालिकाओं में विभाजित अनुच्छेदों के अंतर को पुनः निर्धारित करें क्योंकि अतिरिक्त अंतर के कारण वे भिन्न दिखाई दे सकते हैं।
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
		// अनुभाग के अंत में पृष्ठ विराम को सही करता है।
		SplitPageBreakCorrector.processSection(cloneSection);
	}
	SplitPageBreakCorrector.processSection(section);
	// अनुभाग के मुख्य भाग के लिए भी नई पृष्ठ संख्या जोड़ें।
	pageNumberFinder.addPageNumbersForNode(section.getBody(), pageNumberFinder.getPage(section),
		pageNumberFinder.getPageEnd(section));
	return विज़िटरएक्शन.CONTINUE;
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
	// एक नोड अनेक पृष्ठों में फैला हो सकता है, इसलिए विभाजित स्थितियों की एक सूची लौटाई जाती है।
	// विभाजित नोड अगले पृष्ठ पर पहला नोड है।
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
		// यदि चाइल्ड नोड का पृष्ठ बदल गया है, तो यह विभाजित स्थिति है।
		// इसे सूची में जोड़ें.
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
	// कंपोजिट को पीछे की ओर विभाजित करें, ताकि क्लोन किए गए नोड्स सही क्रम में सम्मिलित हो जाएं।
	Collections.reverse(splitList);
	return splitList;
}
private CompositeNode splitCompositeAtNode(CompositeNode baseNode, Node targetNode) throws Exception {
	CompositeNode cloneNode = (CompositeNode) baseNode.deepClone(false);
	Node node = targetNode;
	int currentPageNum = pageNumberFinder.getPage(baseNode);
	// अगले पृष्ठ पर पाए गए सभी नोड्स को कॉपी किए गए नोड में ले जाएँ। पंक्ति नोड्स को अलग से संभालें।
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
		// यदि हम किसी पंक्ति पर काम कर रहे हैं, तो हमें क्लोन पंक्ति के लिए डमी कोशिकाएं जोड़ने की आवश्यकता होगी।
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
	// मूल के बाद विभाजित नोड डालें.
	baseNode.getParentNode().insertAfter(cloneNode, baseNode);
	// आधार नोड और क्लोन नोड के नए पृष्ठ क्रमांक को उसके वंशजों सहित अद्यतन करें।
	// यह केवल एक ही पृष्ठ होगा क्योंकि क्लोन किए गए समग्र को एक पृष्ठ पर विभाजित किया गया है।
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

## निष्कर्ष

अब आप सीख चुके हैं कि Aspose.Words for Java का उपयोग करके किसी दस्तावेज़ को अलग-अलग पृष्ठों में कैसे विभाजित किया जाए। यह गाइड स्रोत कोड उदाहरणों के साथ एक व्यापक चरण-दर-चरण ट्यूटोरियल प्रदान करता है। दस्तावेज़ों के साथ काम करते समय आप अपनी विशिष्ट आवश्यकताओं को पूरा करने के लिए इस कोड को और अधिक अनुकूलित और विस्तारित कर सकते हैं।
ज़रूर! आइए Aspose.Words for Java का उपयोग करके दस्तावेज़ों को पृष्ठों में विभाजित करने के हमारे गाइड में एक FAQ अनुभाग जोड़ें।

## अक्सर पूछे जाने वाले प्रश्न

### मैं अपने प्रोजेक्ट में Aspose.Words for Java कैसे जोड़ूं?

अपने प्रोजेक्ट में Aspose.Words for Java जोड़ने के लिए, इन चरणों का पालन करें:

1. Aspose.Words for Java लाइब्रेरी को यहां से डाउनलोड करें [यहाँ](https://releases.aspose.com/words/java/).
2. डाउनलोड की गई JAR फ़ाइल को अपने प्रोजेक्ट के क्लासपाथ में जोड़ें।
3. अब आप अपने प्रोजेक्ट में Java के लिए Aspose.Words का उपयोग शुरू कर सकते हैं।

### क्या मैं दस्तावेज़ों को अन्य प्रारूपों, जैसे PDF या DOCX में विभाजित कर सकता हूँ?

नहीं, यह गाइड विशेष रूप से जावा के लिए Aspose.Words का उपयोग करके DOC प्रारूप में दस्तावेज़ों को विभाजित करने को कवर करता है। यदि आपको अन्य प्रारूपों में दस्तावेज़ों को विभाजित करने की आवश्यकता है, तो आपको उन प्रारूपों का समर्थन करने वाले अन्य पुस्तकालयों या उपकरणों का पता लगाने की आवश्यकता हो सकती है।

### क्या Aspose.Words for Java एक निःशुल्क लाइब्रेरी है?

नहीं, Aspose.Words for Java एक निःशुल्क लाइब्रेरी नहीं है। यह एक वाणिज्यिक उत्पाद है, जिस पर लाइसेंस शुल्क लगता है। आप यहाँ जा सकते हैं [Aspose.Words के लिए Java मूल्य निर्धारण पृष्ठ](https://purchase.aspose.com/words/java) लाइसेंसिंग और मूल्य निर्धारण विवरण पर अधिक जानकारी के लिए.

### क्या मैं दस्तावेज़ों को कस्टम पृष्ठ आकार और प्रारूपों में विभाजित कर सकता हूँ?

हां, आप Aspose.Words for Java में पेज सेटअप प्रॉपर्टी को संशोधित करके विभाजित दस्तावेज़ों के पेज आकार और प्रारूप को अनुकूलित कर सकते हैं। अपनी आवश्यकताओं के अनुसार पेज सेटिंग को अनुकूलित करने के तरीके के बारे में विवरण के लिए Aspose.Words दस्तावेज़ देखें।

### क्या विभाजित किये जा सकने वाले पृष्ठों की संख्या पर कोई सीमाएं हैं?

Aspose.Words for Java आपके द्वारा विभाजित किए जा सकने वाले पृष्ठों की संख्या पर कोई विशेष सीमाएँ नहीं लगाता है। हालाँकि, ध्यान रखें कि बहुत बड़े दस्तावेज़ों के लिए अधिक मेमोरी और प्रोसेसिंग समय की आवश्यकता हो सकती है। बड़े दस्तावेज़ों के साथ काम करते समय सिस्टम संसाधनों का ध्यान रखें।

### दस्तावेज़ों को विभाजित करते समय मैं शीर्षलेखों और पादलेखों को कैसे संभाल सकता हूँ?

Aspose.Words for Java लाइब्रेरी का उपयोग करके दस्तावेज़ों को विभाजित करते समय हेडर और फ़ुटर को नियंत्रित किया जा सकता है। आप मूल दस्तावेज़ से हेडर और फ़ुटर सामग्री को विभाजित दस्तावेज़ों में कॉपी कर सकते हैं, यह सुनिश्चित करते हुए कि वे सही तरीके से संरक्षित हैं। आपको अपनी विशिष्ट हेडर और फ़ुटर आवश्यकताओं के आधार पर इस प्रक्रिया को अनुकूलित करने की आवश्यकता हो सकती है।


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}