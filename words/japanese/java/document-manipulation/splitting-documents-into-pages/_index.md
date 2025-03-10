---
title: Aspose.Words for Java でドキュメントをページに分割する
linktitle: ドキュメントをページに分割する
second_title: Aspose.Words Java ドキュメント処理 API
description: Aspose.Words for Java を使用してドキュメントをページに分割する方法を学びます。効率的なドキュメント処理のためのソース コード付きのステップ バイ ステップ ガイド。
weight: 23
url: /ja/java/document-manipulation/splitting-documents-into-pages/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java でドキュメントをページに分割する


Java でドキュメント処理を行っている場合、Aspose.Words for Java は、ドキュメントを効率的に個別のページに分割するのに役立つ強力な API です。このステップバイステップのチュートリアルでは、提供されているソース コードを使用してドキュメントを分割するプロセスについて説明します。このチュートリアルを完了すると、ドキュメントを簡単に分割できるようになり、ドキュメント管理機能が向上します。

## 1. はじめに

Aspose.Words for Java は、Word 文書をプログラムで操作できる Java ライブラリです。一般的なタスクの 1 つは、文書を個別のページに分割することです。これは、アーカイブ、印刷、文書処理など、さまざまな目的に役立ちます。

## 2. 前提条件

コードに進む前に、次の前提条件が満たされていることを確認してください。

- システムに Java 開発キット (JDK) がインストールされています。
- Aspose.Words for Javaライブラリはダウンロードできます[ここ](https://releases.aspose.com/words/java/).

## 3. 環境の設定

まず、開発環境を次のように設定します。

- 好みの統合開発環境 (IDE) で Java プロジェクトを作成します。
- Aspose.Words for Javaライブラリをプロジェクトに追加します。[ドキュメント](https://reference.aspose.com/words/java/)詳細な手順については、こちらをご覧ください。

## 4. ソースコードの理解

提供されたソース コードは、ドキュメントを個別のページに分割するように設計されています。主要なコンポーネントを分解してみましょう。

```java
String fileName = FilenameUtils.getBaseName(docName);
String extensionName = FilenameUtils.getExtension(docName);
System.out.println("Processing document: " + fileName + "." + extensionName);
Document doc = new Document(docName);
```

- 入力ドキュメントのベース名と拡張子を抽出します。
- Aspose.Words for Java を使用してドキュメントを読み込みます。

## 5. ドキュメントを段階的に分割する

### 5.1. ドキュメントの読み込み

```java
Document doc = new Document(docName);
```

このステップでは、入力文書を`Document`オブジェクトを使用すると、ドキュメントのコンテンツを操作できます。

### 5.2. DocumentPageSplitter の初期化

```java
DocumentPageSplitter splitter = new DocumentPageSplitter(doc);
```

初期化する`DocumentPageSplitter`読み込まれたドキュメントのオブジェクト。このクラスは Aspose.Words for Java によって提供され、ドキュメントをページに分割するのに役立ちます。

### 5.3. 各ページの保存

```java
for (int page = 1; page <= doc.getPageCount(); page++) {
    Document pageDoc = splitter.getDocumentOfPage(page);
    pageDoc.save("Your Directory Path" + MessageFormat.format("{0} - page{1}.{2}", fileName, page, extensionName));
}
```

このステップでは、ドキュメントの各ページを反復処理し、個別のドキュメントとして保存します。分割されたページが保存されるディレクトリ パスを指定できます。

## 6. コードの実行

このコードを正常に実行するには、環境を設定し、Aspose.Words for Java ライブラリをプロジェクトに追加していることを確認してください。その後、コードを実行すると、ドキュメントが個別のページに分割されます。

## DocumentPageSplitter ソースコード

```java
//<要約>
/// ドキュメントをページごとに複数のドキュメントに分割します。
/// </要約>
class DocumentPageSplitter
{
private PageNumberFinder pageNumberFinder;
//<要約>
/// <see cref="DocumentPageSplitter"/> クラスの新しいインスタンスを初期化します。
/// この方法では、ドキュメントをセクションに分割し、各ページがセクション境界で始まり、セクション境界で終わるようにします。
/// 後でドキュメントを変更しないことをお勧めします。
/// </要約>
/// <param name="source">ソースドキュメント</param>
public DocumentPageSplitter(Document source) throws Exception
{
	pageNumberFinder = PageNumberFinderFactory.create(source);
}
private Document getDocument() {
	return pageNumberFinder.getDocument();
}
//<要約>
/// ページのドキュメントを取得します。
/// </要約>
/// <param name="ページインデックス">
/// ページの 1 から始まるインデックス。
/// </パラメータ>
/// <戻る>
/// <see cref="Document"/> を参照してください。
/// </returns>
public Document getDocumentOfPage(int pageIndex) throws Exception {
	return getDocumentOfPageRange(pageIndex, pageIndex);
}
//<要約>
//ページ範囲のドキュメントを取得します。
/// </要約>
/// <param name="開始インデックス">
/// スタートページの 1 から始まるインデックス。
/// </パラメータ>
/// <param name="endIndex">
/// 終了ページの 1 から始まるインデックス。
/// </パラメータ>
/// <戻る>
/// <see cref="Document"/> を参照してください。
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
//<要約>
/// 指定されたページにレンダリングされるドキュメントのノードを抽出するためのメソッドを提供します。
/// </要約>
class PageNumberFinder
{
//ノードを開始/終了ページ番号にマップします。
//これは、ドキュメントが分割されるときにコレクターによって提供されるベースライン ページ番号をオーバーライドするために使用されます。
private Map<Node, Integer> nodeStartPageLookup = new HashMap<>();
private Map<Node, Integer> nodeEndPageLookup = new HashMap<>();
private LayoutCollector collector;
//ページ番号をそのページで見つかったノードのリストにマップします。
private Map<Integer, ArrayList<Node>> reversePageLookup;
//<要約>
/// <see cref="PageNumberFinder"/> クラスの新しいインスタンスを初期化します。
/// </要約>
/// <param name="collector">ドキュメントのレイアウト モデル レコードを持つコレクター インスタンス。</param>
public PageNumberFinder(LayoutCollector collector)
{
	this.collector = collector;
}
public Document getDocument()
{
	return collector.getDocument();
}
//<要約>
/// ノードが始まるページの 1 から始まるインデックスを取得します。
/// </要約>
/// <パラメータ名="ノード">
/// ノード。
/// </パラメータ>
/// <戻る>
/// ページインデックス。
/// </returns>
public int getPage(Node node) throws Exception {
	return nodeStartPageLookup.containsKey(node)
		? nodeStartPageLookup.get(node)
		: collector.getStartPageIndex(node);
}
//<要約>
/// ノードが終了するページの 1 から始まるインデックスを取得します。
/// </要約>
/// <パラメータ名="ノード">
/// ノード。
/// </パラメータ>
/// <戻る>
/// ページインデックス。
/// </returns>
public int getPageEnd(Node node) throws Exception {
	return nodeEndPageLookup.containsKey(node)
		? nodeEndPageLookup.get(node)
		: collector.getEndPageIndex(node);
}
//<要約>
//指定されたノードが何ページにわたっているかを返します。ノードが 1 ページ内に含まれている場合は 1 を返します。
/// </要約>
/// <パラメータ名="ノード">
/// ノード。
/// </パラメータ>
/// <戻る>
/// ページインデックス。
/// </returns>
public int pageSpan(Node node) throws Exception {
	return getPageEnd(node) - getPage(node) + 1;
}
//<要約>
/// 指定されたページまたは指定されたノード タイプに一致するページの任意の場所に含まれるノードのリストを返します。
/// </要約>
/// <param name="スタートページ">
/// スタートページ。
/// </パラメータ>
/// <パラメータ名="endPage">
/// 終了ページ。
/// </パラメータ>
/// <パラメータ名="ノードタイプ">
/// ノード タイプ。
/// </パラメータ>
/// <戻る>
/// <see cref="IList{T}"/>。
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
		//一部のページは空になる場合があります。
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
//<要約>
/// 2ページ以上に表示されるノードを別々のノードに分割して、同じように表示されるようにします。
/// はページ全体に表示されなくなりました。
/// </要約>
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
	//ページ間で分割されている可能性のある複合体にアクセスし、それらを個別のノードに分割します。
	collector.getDocument().accept(new SectionSplitter(this));
}
//<要約>
/// これは、分割ノードのページ番号を更新するために <see cref="SectionSplitter"/> によって呼び出されます。
/// </要約>
/// <パラメータ名="ノード">
/// ノード。
/// </パラメータ>
/// <param name="スタートページ">
/// スタートページ。
/// </パラメータ>
/// <パラメータ名="endPage">
/// 終了ページ。
/// </パラメータ>
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
	//各ページで見つかったノードを表すリストに各ノードを追加します。
	for (Node node : (Iterable<Node>) collector.getDocument().getChildNodes(NodeType.ANY, true))
	{
		//ヘッダー/フッターはセクションに続き、それ自体では分割されません。
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
//<要約>
/// 指定された実行のテキストを 2 つの実行に分割します。
/// 指定された実行の直後に新しい実行を挿入します。
/// </要約>
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
//<要約>
/// 各ページがセクション境界で始まり、セクション境界で終わるように、ドキュメントを複数のセクションに分割します。
/// </要約>
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
	//前のセクションがある場合は、リンクされたヘッダー フッターをコピーしてみます。
	//そうしないと、前のセクションが欠落している場合、抽出されたドキュメントに表示されません。
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
	//段落にセクション区切りのみが含まれる場合は、偽の run into を追加します。
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
		//複製された段落からリスト番号を削除しますが、インデントはそのままにします
		//段落は前の項目の一部であるはずだからです。
		if (paragraph.isListItem())
		{
			double textPosition = clonePara.getListFormat().getListLevel().getTextPosition();
			clonePara.getListFormat().removeNumbers();
			clonePara.getParagraphFormat().setLeftIndent(textPosition);
		}
		//追加の間隔によって見た目が変わる可能性があるため、表内の分割された段落の間隔をリセットします。
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
		//セクションの末尾のページ区切りを修正します。
		SplitPageBreakCorrector.processSection(cloneSection);
	}
	SplitPageBreakCorrector.processSection(section);
	//セクションの本文にも新しいページ番号を追加します。
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
	//ノードは複数のページにまたがる場合があるため、分割された位置のリストが返されます。
	//分割ノードは次のページの最初のノードになります。
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
		//子ノードのページが変更された場合、これが分割位置になります。
		//これをリストに追加します。
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
	//複合物を後方に分割して、複製されたノードが正しい順序で挿入されるようにします。
	Collections.reverse(splitList);
	return splitList;
}
private CompositeNode splitCompositeAtNode(CompositeNode baseNode, Node targetNode) throws Exception {
	CompositeNode cloneNode = (CompositeNode) baseNode.deepClone(false);
	Node node = targetNode;
	int currentPageNum = pageNumberFinder.getPage(baseNode);
	//次のページで見つかったすべてのノードをコピーしたノードに移動します。行ノードは個別に処理します。
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
		//行を扱う場合は、複製された行にダミー セルを追加する必要があります。
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
	//元のノードの後に分割ノードを挿入します。
	baseNode.getParentNode().insertAfter(cloneNode, baseNode);
	//ベース ノードとクローン ノード (およびその子孫) の新しいページ番号を更新します。
	//複製された複合ページは 1 ページに分割されるため、これは 1 ページのみになります。
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

## 結論

Aspose.Words for Java を使用してドキュメントを個別のページに分割する方法を学習しました。このガイドでは、ソース コードの例を含む包括的なステップ バイ ステップのチュートリアルを提供します。ドキュメントを操作するときに、特定の要件を満たすようにこのコードをさらにカスタマイズおよび拡張できます。
もちろんです! Aspose.Words for Java を使用してドキュメントをページに分割する方法に関するガイドに FAQ セクションを追加しましょう。

## よくある質問

### Aspose.Words for Java をプロジェクトに追加するにはどうすればよいですか?

Aspose.Words for Java をプロジェクトに追加するには、次の手順に従います。

1.  Aspose.Words for Javaライブラリを以下からダウンロードしてください。[ここ](https://releases.aspose.com/words/java/).
2. ダウンロードした JAR ファイルをプロジェクトのクラスパスに追加します。
3. これで、プロジェクトで Aspose.Words for Java の使用を開始できます。

### PDF や DOCX などの他の形式でドキュメントを分割できますか?

いいえ、このガイドでは、Aspose.Words for Java を使用して DOC 形式のドキュメントを分割する方法について説明します。他の形式のドキュメントを分割する必要がある場合は、それらの形式をサポートする他のライブラリまたはツールを調べる必要がある場合があります。

### Aspose.Words for Java は無料のライブラリですか?

いいえ、Aspose.Words for Javaは無料ライブラリではありません。ライセンス料がかかる商用製品です。[Aspose.Words for Java の価格ページ](https://purchase.aspose.com/words/java)ライセンスと価格の詳細については、こちらをご覧ください。

### ドキュメントをカスタムのページ サイズと形式に分割できますか?

はい、Aspose.Words for Java のページ設定プロパティを変更することで、分割されたドキュメントのページ サイズと形式をカスタマイズできます。要件に応じてページ設定をカスタマイズする方法の詳細については、Aspose.Words のドキュメントを参照してください。

### 分割できるページ数に制限はありますか?

Aspose.Words for Java では、分割できるページ数に特別な制限はありません。ただし、非常に大きなドキュメントでは、より多くのメモリと処理時間が必要になる場合があることに注意してください。大きなドキュメントを扱うときは、システム リソースに注意してください。

### ドキュメントを分割するときにヘッダーとフッターをどのように処理すればよいですか?

Aspose.Words for Java ライブラリを使用すると、ドキュメントを分割するときにヘッダーとフッターを処理できます。元のドキュメントから分割されたドキュメントにヘッダーとフッターの内容をコピーして、正しく保持されるようにすることができます。特定のヘッダーとフッターの要件に基づいて、このプロセスをカスタマイズする必要がある場合があります。
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
