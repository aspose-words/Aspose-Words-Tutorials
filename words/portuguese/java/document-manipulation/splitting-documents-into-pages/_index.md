---
title: Dividindo documentos em páginas no Aspose.Words para Java
linktitle: Dividindo documentos em páginas
second_title: API de processamento de documentos Java Aspose.Words
description: Aprenda como dividir documentos em páginas usando Aspose.Words para Java. Guia passo a passo com código-fonte para processamento eficiente de documentos.
weight: 23
url: /pt/java/document-manipulation/splitting-documents-into-pages/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Dividindo documentos em páginas no Aspose.Words para Java


Se você estiver trabalhando com processamento de documentos em Java, o Aspose.Words para Java é uma API poderosa que pode ajudar você a dividir documentos em páginas separadas de forma eficiente. Neste tutorial passo a passo, nós o guiaremos pelo processo de divisão de documentos usando o código-fonte fornecido. Ao final deste tutorial, você será capaz de dividir documentos com facilidade, melhorando seus recursos de gerenciamento de documentos.

## 1. Introdução

Aspose.Words para Java é uma biblioteca Java que permite que você manipule documentos do Word programaticamente. Uma tarefa comum é dividir um documento em páginas separadas, o que pode ser útil para vários propósitos, como arquivamento, impressão ou processamento de documentos.

## 2. Pré-requisitos

Antes de mergulharmos no código, certifique-se de ter os seguintes pré-requisitos em vigor:

- Java Development Kit (JDK) instalado no seu sistema.
-  Biblioteca Aspose.Words para Java, que você pode baixar[aqui](https://releases.aspose.com/words/java/).

## 3. Configurando seu ambiente

Para começar, configure seu ambiente de desenvolvimento da seguinte maneira:

- Crie um projeto Java no seu Ambiente de Desenvolvimento Integrado (IDE) preferido.
- Adicione a biblioteca Aspose.Words for Java ao seu projeto. Você pode consultar o[documentação](https://reference.aspose.com/words/java/) para obter instruções detalhadas.

## 4. Entendendo o código fonte

O código-fonte que você forneceu foi projetado para dividir um documento em páginas separadas. Vamos dividir os componentes principais:

```java
String fileName = FilenameUtils.getBaseName(docName);
String extensionName = FilenameUtils.getExtension(docName);
System.out.println("Processing document: " + fileName + "." + extensionName);
Document doc = new Document(docName);
```

- Extraímos o nome base e a extensão do documento de entrada.
- Carregamos o documento usando Aspose.Words para Java.

## 5. Dividindo documentos passo a passo

### 5.1. Carregando o documento

```java
Document doc = new Document(docName);
```

 Nesta etapa, carregamos o documento de entrada em um`Document` objeto, que nos permite trabalhar com o conteúdo do documento.

### 5.2. Inicializando o DocumentPageSplitter

```java
DocumentPageSplitter splitter = new DocumentPageSplitter(doc);
```

 Inicializamos um`DocumentPageSplitter` objeto com nosso documento carregado. Esta classe é fornecida por Aspose.Words para Java e nos ajuda a dividir o documento em páginas.

### 5.3. Salvando cada página

```java
for (int page = 1; page <= doc.getPageCount(); page++) {
    Document pageDoc = splitter.getDocumentOfPage(page);
    pageDoc.save("Your Directory Path" + MessageFormat.format("{0} - page{1}.{2}", fileName, page, extensionName));
}
```

Nesta etapa, iteramos por cada página do documento e salvamos como um documento separado. Você pode especificar o caminho do diretório onde as páginas divididas serão salvas.

## 6. Executando o código

Para executar este código com sucesso, certifique-se de ter configurado seu ambiente e adicionado a biblioteca Aspose.Words for Java ao seu projeto. Em seguida, execute o código, e você terá seu documento dividido em páginas separadas.

## Código fonte do DocumentPageSplitter

```java
/// <resumo>
/// Divide um documento em vários documentos, um por página.
/// </resumo>
class DocumentPageSplitter
{
private PageNumberFinder pageNumberFinder;
/// <resumo>
/// Inicializa uma nova instância da classe <see cref="DocumentPageSplitter"/>.
/// Este método divide o documento em seções para que cada página comece e termine em um limite de seção.
/// É recomendável não modificar o documento posteriormente.
/// </resumo>
/// <param name="source">Documento de origem</param>
public DocumentPageSplitter(Document source) throws Exception
{
	pageNumberFinder = PageNumberFinderFactory.create(source);
}
private Document getDocument() {
	return pageNumberFinder.getDocument();
}
/// <resumo>
/// Obtém o documento de uma página.
/// </resumo>
/// <param nome="pageIndex">
/// Índice de base 1 de uma página.
/// </param>
/// <retorna>
/// O <veja cref="Documento"/>.
/// </retorna>
public Document getDocumentOfPage(int pageIndex) throws Exception {
	return getDocumentOfPageRange(pageIndex, pageIndex);
}
/// <resumo>
//Obtém o documento de um intervalo de páginas.
/// </resumo>
/// <param nome="startIndex">
/// Índice de base 1 da página inicial.
/// </param>
/// <param nome="endIndex">
/// Índice de base 1 da página final.
/// </param>
/// <retorna>
/// O <veja cref="Documento"/>.
/// </retorna>
public Document getDocumentOfPageRange(int startIndex, int endIndex) throws Exception {
	Document result = (Document) getDocument().deepClone(false);
	for (Node section : pageNumberFinder.retrieveAllNodesOnPages(startIndex, endIndex, NodeType.SECTION))
	{
		result.appendChild(result.importNode(section, true));
	}
	return result;
}
}
/// <resumo>
/// Fornece métodos para extrair nós de um documento que são renderizados em páginas especificadas.
/// </resumo>
class PageNumberFinder
{
// Mapeia o nó para números de página inicial/final.
// Isso é usado para substituir os números de página de base fornecidos pelo coletor quando o documento é dividido.
private Map<Node, Integer> nodeStartPageLookup = new HashMap<>();
private Map<Node, Integer> nodeEndPageLookup = new HashMap<>();
private LayoutCollector collector;
// Mapeia o número da página para uma lista de nós encontrados naquela página.
private Map<Integer, ArrayList<Node>> reversePageLookup;
/// <resumo>
/// Inicializa uma nova instância da classe <see cref="PageNumberFinder"/>.
/// </resumo>
/// <param name="collector">Uma instância do coletor que possui registros de modelo de layout para o documento.</param>
public PageNumberFinder(LayoutCollector collector)
{
	this.collector = collector;
}
public Document getDocument()
{
	return collector.getDocument();
}
/// <resumo>
/// Recupera o índice de base 1 de uma página na qual o nó começa.
/// </resumo>
/// <param nome="nó">
/// O nó.
/// </param>
/// <retorna>
/// Índice da página.
/// </retorna>
public int getPage(Node node) throws Exception {
	return nodeStartPageLookup.containsKey(node)
		? nodeStartPageLookup.get(node)
		: collector.getStartPageIndex(node);
}
/// <resumo>
/// Recupera o índice de base 1 de uma página na qual o nó termina.
/// </resumo>
/// <param nome="nó">
/// O nó.
/// </param>
/// <retorna>
/// Índice da página.
/// </retorna>
public int getPageEnd(Node node) throws Exception {
	return nodeEndPageLookup.containsKey(node)
		? nodeEndPageLookup.get(node)
		: collector.getEndPageIndex(node);
}
/// <resumo>
//Retorna quantas páginas o nó especificado abrange. Retorna 1 se o nó estiver contido em uma página.
/// </resumo>
/// <param nome="nó">
/// O nó.
/// </param>
/// <retorna>
/// Índice da página.
/// </retorna>
public int pageSpan(Node node) throws Exception {
	return getPageEnd(node) - getPage(node) + 1;
}
/// <resumo>
/// Retorna uma lista de nós que estão contidos em qualquer lugar na página especificada ou páginas que correspondem ao tipo de nó especificado.
/// </resumo>
/// <param nome="startPage">
/// A página inicial.
/// </param>
/// <param nome="fim da página">
/// A página final.
/// </param>
/// <param nome="tipo de nó">
/// O tipo de nó.
/// </param>
/// <retorna>
/// O <veja cref="IList{T}"/>.
/// </retorna>
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
		// Algumas páginas podem estar em branco.
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
/// <resumo>
/// Divide nós que aparecem em duas ou mais páginas em nós separados para que eles ainda apareçam da mesma maneira
/// mas não aparecem mais em uma página.
/// </resumo>
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
	// Visite quaisquer compostos que possam estar divididos entre páginas e divida-os em nós separados.
	collector.getDocument().accept(new SectionSplitter(this));
}
/// <resumo>
/// Isso é chamado por <see cref="SectionSplitter"/> para atualizar os números de página dos nós divididos.
/// </resumo>
/// <param nome="nó">
/// O nó.
/// </param>
/// <param nome="startPage">
/// A página inicial.
/// </param>
/// <param nome="fim da página">
/// A página final.
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
	// Adicione cada nó a uma lista que representa os nós encontrados em cada página.
	for (Node node : (Iterable<Node>) collector.getDocument().getChildNodes(NodeType.ANY, true))
	{
		//Cabeçalhos/rodapés seguem seções e não são divididos por si mesmos.
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
/// <resumo>
/// Divide o texto da execução especificada em duas execuções.
/// Insere a nova execução logo após a execução especificada.
/// </resumo>
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
/// <resumo>
/// Divide um documento em várias seções para que cada página comece e termine em um limite de seção.
/// </resumo>
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
	// Se houver uma seção anterior, tente copiar todos os cabeçalhos e rodapés vinculados.
	// Caso contrário, eles não aparecerão em um documento extraído se a seção anterior estiver faltando.
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
	// Se o parágrafo contiver apenas quebra de seção, adicione uma quebra de seção falsa.
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
		// Remova a numeração da lista do parágrafo clonado, mas deixe o recuo igual
		// já que o parágrafo deveria fazer parte do item anterior.
		if (paragraph.isListItem())
		{
			double textPosition = clonePara.getListFormat().getListLevel().getTextPosition();
			clonePara.getListFormat().removeNumbers();
			clonePara.getParagraphFormat().setLeftIndent(textPosition);
		}
		// Redefina o espaçamento dos parágrafos divididos em tabelas, pois espaçamento adicional pode fazer com que eles pareçam diferentes.
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
		// Corrige quebra de página no final da seção.
		SplitPageBreakCorrector.processSection(cloneSection);
	}
	SplitPageBreakCorrector.processSection(section);
	// Adicione também uma nova numeração de página para o corpo da seção.
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
	// Um nó pode abranger várias páginas, então uma lista de posições divididas é retornada.
	// nó dividido é o primeiro nó na próxima página.
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
		// Se a página do nó filho tiver sido alterada, esta será a posição dividida.
		// Adicione isso à lista.
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
	// Divida os compostos para trás, para que os nós clonados sejam inseridos na ordem correta.
	Collections.reverse(splitList);
	return splitList;
}
private CompositeNode splitCompositeAtNode(CompositeNode baseNode, Node targetNode) throws Exception {
	CompositeNode cloneNode = (CompositeNode) baseNode.deepClone(false);
	Node node = targetNode;
	int currentPageNum = pageNumberFinder.getPage(baseNode);
	// Mova todos os nós encontrados na próxima página para o nó copiado. Manipule os nós de linha separadamente.
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
		// Se estivermos lidando com uma linha, precisamos adicionar células fictícias para a linha clonada.
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
	// Insira o nó dividido após o original.
	baseNode.getParentNode().insertAfter(cloneNode, baseNode);
	// Atualize os novos números de página do nó base e do nó clonado, incluindo seus descendentes.
	// Esta será apenas uma única página, pois o composto clonado será dividido em uma única página.
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

## Conclusão

Agora você aprendeu como dividir um documento em páginas separadas usando o Aspose.Words para Java. Este guia fornece um tutorial passo a passo abrangente com exemplos de código-fonte. Você pode personalizar e estender ainda mais este código para atender aos seus requisitos específicos ao trabalhar com documentos.
Certamente! Vamos adicionar uma seção de FAQ ao nosso guia sobre como dividir documentos em páginas usando Aspose.Words para Java.

## Perguntas frequentes

### Como adiciono o Aspose.Words para Java ao meu projeto?

Para adicionar Aspose.Words para Java ao seu projeto, siga estas etapas:

1.  Baixe a biblioteca Aspose.Words para Java em[aqui](https://releases.aspose.com/words/java/).
2. Adicione o arquivo JAR baixado ao classpath do seu projeto.
3. Agora você pode começar a usar o Aspose.Words para Java no seu projeto.

### Posso dividir documentos em outros formatos, como PDF ou DOCX?

Não, este guia aborda especificamente a divisão de documentos no formato DOC usando o Aspose.Words para Java. Se você precisar dividir documentos em outros formatos, talvez precise explorar outras bibliotecas ou ferramentas que suportem esses formatos.

### O Aspose.Words para Java é uma biblioteca gratuita?

 Não, Aspose.Words para Java não é uma biblioteca gratuita. É um produto comercial com uma taxa de licenciamento. Você pode visitar o[Página de preços do Aspose.Words para Java](https://purchase.aspose.com/words/java) para mais informações sobre licenciamento e detalhes de preços.

### Posso dividir documentos em tamanhos e formatos de página personalizados?

Sim, você pode personalizar os tamanhos e formatos de página dos documentos divididos modificando as propriedades de configuração de página no Aspose.Words para Java. Consulte a documentação do Aspose.Words para obter detalhes sobre como personalizar as configurações de página de acordo com seus requisitos.

### Há alguma limitação quanto ao número de páginas que podem ser divididas?

O Aspose.Words para Java não impõe limitações específicas sobre o número de páginas que você pode dividir. No entanto, tenha em mente que documentos muito grandes podem exigir mais memória e tempo de processamento. Esteja atento aos recursos do sistema ao trabalhar com documentos grandes.

### Como posso lidar com cabeçalhos e rodapés ao dividir documentos?

Cabeçalhos e rodapés podem ser manipulados ao dividir documentos usando a biblioteca Aspose.Words para Java. Você pode copiar o conteúdo do cabeçalho e rodapé do documento original para os documentos divididos, garantindo que eles sejam preservados corretamente. Talvez seja necessário personalizar esse processo com base em seus requisitos específicos de cabeçalho e rodapé.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
