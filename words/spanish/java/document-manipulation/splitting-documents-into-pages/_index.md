---
"description": "Aprenda a dividir documentos en páginas con Aspose.Words para Java. Guía paso a paso con código fuente para un procesamiento eficiente de documentos."
"linktitle": "Dividir documentos en páginas"
"second_title": "API de procesamiento de documentos Java de Aspose.Words"
"title": "División de documentos en páginas en Aspose.Words para Java"
"url": "/es/java/document-manipulation/splitting-documents-into-pages/"
"weight": 23
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# División de documentos en páginas en Aspose.Words para Java


Si trabaja con el procesamiento de documentos en Java, Aspose.Words para Java es una potente API que le ayuda a dividir documentos en páginas independientes de forma eficiente. En este tutorial paso a paso, le guiaremos en el proceso de división de documentos utilizando el código fuente proporcionado. Al finalizar este tutorial, podrá dividir documentos fácilmente, mejorando así sus capacidades de gestión documental.

## 1. Introducción

Aspose.Words para Java es una biblioteca de Java que permite manipular documentos de Word mediante programación. Una tarea común es dividir un documento en páginas independientes, lo cual puede ser útil para diversos fines, como archivar, imprimir o procesar documentos.

## 2. Requisitos previos

Antes de sumergirnos en el código, asegúrese de tener los siguientes requisitos previos:

- Java Development Kit (JDK) instalado en su sistema.
- Biblioteca Aspose.Words para Java, que puedes descargar [aquí](https://releases.aspose.com/words/java/).

## 3. Configuración de su entorno

Para comenzar, configure su entorno de desarrollo de la siguiente manera:

- Cree un proyecto Java en su entorno de desarrollo integrado (IDE) preferido.
- Agregue la biblioteca Aspose.Words para Java a su proyecto. Puede consultar la [documentación](https://reference.aspose.com/words/java/) para obtener instrucciones detalladas.

## 4. Comprensión del código fuente

El código fuente que proporcionaste está diseñado para dividir un documento en páginas separadas. Analicemos los componentes clave:

```java
String fileName = FilenameUtils.getBaseName(docName);
String extensionName = FilenameUtils.getExtension(docName);
System.out.println("Processing document: " + fileName + "." + extensionName);
Document doc = new Document(docName);
```

- Extraemos el nombre base y la extensión del documento de entrada.
- Cargamos el documento usando Aspose.Words para Java.

## 5. División de documentos paso a paso

### 5.1. Carga del documento

```java
Document doc = new Document(docName);
```

En este paso, cargamos el documento de entrada en un `Document` objeto, que nos permite trabajar con el contenido del documento.

### 5.2. Inicialización de DocumentPageSplitter

```java
DocumentPageSplitter splitter = new DocumentPageSplitter(doc);
```

Inicializamos un `DocumentPageSplitter` Objeto con nuestro documento cargado. Esta clase la proporciona Aspose.Words para Java y nos ayuda a dividir el documento en páginas.

### 5.3. Guardar cada página

```java
for (int page = 1; page <= doc.getPageCount(); page++) {
    Document pageDoc = splitter.getDocumentOfPage(page);
    pageDoc.save("Your Directory Path" + MessageFormat.format("{0} - page{1}.{2}", fileName, page, extensionName));
}
```

En este paso, iteramos cada página del documento y lo guardamos como un documento independiente. Puede especificar la ruta del directorio donde se guardarán las páginas divididas.

## 6. Ejecución del código

Para ejecutar este código correctamente, asegúrese de haber configurado su entorno y de haber añadido la biblioteca Aspose.Words para Java a su proyecto. A continuación, ejecute el código y su documento se dividirá en páginas independientes.

## Código fuente de DocumentPageSplitter

```java
/// <resumen>
/// Divide un documento en varios documentos, uno por página.
/// </summary>
class DocumentPageSplitter
{
private PageNumberFinder pageNumberFinder;
/// <resumen>
/// Inicializa una nueva instancia de la clase <see cref="DocumentPageSplitter"/>.
//Este método divide el documento en secciones de modo que cada página comienza y termina en un límite de sección.
//Se recomienda no modificar el documento posteriormente.
/// </summary>
/// <param name="source">Documento fuente</param>
public DocumentPageSplitter(Document source) throws Exception
{
	pageNumberFinder = PageNumberFinderFactory.create(source);
}
private Document getDocument() {
	return pageNumberFinder.getDocument();
}
/// <resumen>
/// Obtiene el documento de una página.
/// </summary>
/// <param name="índice de página">
/// Índice basado en 1 de una página.
/// </param>
/// <retornos>
/// El <see cref="Documento"/>.
/// </returns>
public Document getDocumentOfPage(int pageIndex) throws Exception {
	return getDocumentOfPageRange(pageIndex, pageIndex);
}
/// <resumen>
/// Obtiene el documento de un rango de páginas.
/// </summary>
/// <param name="índice de inicio">
/// Índice basado en 1 de la página de inicio.
/// </param>
//<param name="endIndex">
/// Índice basado en 1 de la página final.
/// </param>
/// <retornos>
/// El <see cref="Documento"/>.
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
/// <resumen>
/// Proporciona métodos para extraer nodos de un documento que se representan en páginas específicas.
/// </summary>
class PageNumberFinder
{
// Asigna un nodo a un número de página de inicio/fin.
// Esto se utiliza para anular los números de página de referencia proporcionados por el recopilador cuando se divide el documento.
private Map<Node, Integer> nodeStartPageLookup = new HashMap<>();
private Map<Node, Integer> nodeEndPageLookup = new HashMap<>();
private LayoutCollector collector;
// Asigna el número de página a una lista de nodos encontrados en esa página.
private Map<Integer, ArrayList<Node>> reversePageLookup;
/// <resumen>
/// Inicializa una nueva instancia de la clase <see cref="PageNumberFinder"/>.
/// </summary>
/// <param name="collector">Una instancia de recopilador que tiene registros del modelo de diseño para el documento.</param>
public PageNumberFinder(LayoutCollector collector)
{
	this.collector = collector;
}
public Document getDocument()
{
	return collector.getDocument();
}
/// <resumen>
/// Recupera el índice basado en 1 de una página en la que comienza el nodo.
/// </summary>
/// <param name="nodo">
///El nodo.
/// </param>
/// <retornos>
/// Índice de páginas.
/// </returns>
public int getPage(Node node) throws Exception {
	return nodeStartPageLookup.containsKey(node)
		? nodeStartPageLookup.get(node)
		: collector.getStartPageIndex(node);
}
/// <resumen>
/// Recupera el índice basado en 1 de una página en la que finaliza el nodo.
/// </summary>
/// <param name="nodo">
///El nodo.
/// </param>
/// <retornos>
/// Índice de páginas.
/// </returns>
public int getPageEnd(Node node) throws Exception {
	return nodeEndPageLookup.containsKey(node)
		? nodeEndPageLookup.get(node)
		: collector.getEndPageIndex(node);
}
/// <resumen>
/// Devuelve la cantidad de páginas que abarca el nodo especificado. Devuelve 1 si el nodo está contenido en una página.
/// </summary>
/// <param name="nodo">
///El nodo.
/// </param>
/// <retornos>
/// Índice de páginas.
/// </returns>
public int pageSpan(Node node) throws Exception {
	return getPageEnd(node) - getPage(node) + 1;
}
/// <resumen>
/// Devuelve una lista de nodos que están contenidos en cualquier parte de la página o páginas especificadas que coinciden con el tipo de nodo especificado.
/// </summary>
/// <param name="página de inicio">
/// La página de inicio.
/// </param>
/// <param name="endPage">
/// La página final.
/// </param>
/// <param name="tipo de nodo">
/// El tipo de nodo.
/// </param>
/// <retornos>
/// El <see cref="IList{T}"/>.
/// </returns>
public ArrayList<Node> retrieveAllNodesOnPages(int startPage, int endPage, /*Tipo de nodo*/int nodeType) throws Exception
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
		// Algunas páginas pueden estar vacías.
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
/// <resumen>
/// Divide los nodos que aparecen en dos o más páginas en nodos separados para que sigan apareciendo de la misma manera
/// pero ya no aparecen en ninguna página.
/// </summary>
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
	// Visita todos los compuestos que posiblemente estén divididos en páginas y divídelos en nodos separados.
	collector.getDocument().accept(new SectionSplitter(this));
}
/// <resumen>
//<see cref="SectionSplitter"/> llama a esto para actualizar los números de página de los nodos divididos.
/// </summary>
/// <param name="nodo">
///El nodo.
/// </param>
/// <param name="página de inicio">
/// La página de inicio.
/// </param>
/// <param name="endPage">
/// La página final.
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
	// Agregue cada nodo a una lista que represente los nodos encontrados en cada página.
	for (Node node : (Iterable<Node>) collector.getDocument().getChildNodes(NodeType.ANY, true))
	{
		// Los encabezados y pies de página siguen a las secciones y no están divididos por sí mismos.
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
/// <resumen>
/// Divide el texto de la ejecución especificada en dos ejecuciones.
/// Inserta la nueva ejecución justo después de la ejecución especificada.
/// </summary>
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
/// <resumen>
/// Divide un documento en varias secciones para que cada página comience y termine en un límite de sección.
/// </summary>
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
	// Si hay una sección anterior, intente copiar cualquier encabezado y pie de página vinculados.
	// De lo contrario, no aparecerán en un documento extraído si falta la sección anterior.
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
	// Si el párrafo contiene solo un salto de sección, agregue un salto falso.
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
		// Eliminar la numeración de lista del párrafo clonado, pero dejar la sangría igual 
		// ya que se supone que el párrafo es parte del artículo anterior.
		if (paragraph.isListItem())
		{
			double textPosition = clonePara.getListFormat().getListLevel().getTextPosition();
			clonePara.getListFormat().removeNumbers();
			clonePara.getParagraphFormat().setLeftIndent(textPosition);
		}
		// Restablezca el espaciado de los párrafos divididos en las tablas, ya que el espaciado adicional puede provocar que se vean diferentes.
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
		// Corrige el salto de página al final de la sección.
		SplitPageBreakCorrector.processSection(cloneSection);
	}
	SplitPageBreakCorrector.processSection(section);
	// Añade también una nueva numeración de página para el cuerpo de la sección.
	pageNumberFinder.addPageNumbersForNode(section.getBody(), pageNumberFinder.getPage(section),
		pageNumberFinder.getPageEnd(section));
	return Acción del visitante.CONTINUE;
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
	// Un nodo puede abarcar varias páginas, por lo que se devuelve una lista de posiciones divididas.
	// El nodo dividido es el primer nodo en la página siguiente.
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
		// Si la página del nodo secundario ha cambiado, esta es la posición dividida.
		// Añade esto a la lista.
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
	// Divida los compuestos hacia atrás, de modo que los nodos clonados se inserten en el orden correcto.
	Collections.reverse(splitList);
	return splitList;
}
private CompositeNode splitCompositeAtNode(CompositeNode baseNode, Node targetNode) throws Exception {
	CompositeNode cloneNode = (CompositeNode) baseNode.deepClone(false);
	Node node = targetNode;
	int currentPageNum = pageNumberFinder.getPage(baseNode);
	// Mueva todos los nodos de la página siguiente al nodo copiado. Trate los nodos de fila por separado.
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
		// Si estamos tratando con una fila, necesitamos agregar celdas ficticias para la fila clonada.
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
	// Inserte el nodo dividido después del original.
	baseNode.getParentNode().insertAfter(cloneNode, baseNode);
	// Actualice los nuevos números de página del nodo base y del nodo clonado, incluidos sus descendientes.
	// Esta solo será una página única, ya que el compuesto clonado está dividido para estar en una sola página.
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

## Conclusión

Ya ha aprendido a dividir un documento en páginas independientes con Aspose.Words para Java. Esta guía ofrece un tutorial completo paso a paso con ejemplos de código fuente. Puede personalizar y ampliar este código para adaptarlo a sus necesidades específicas al trabajar con documentos.
¡Por supuesto! Añadamos una sección de preguntas frecuentes a nuestra guía sobre cómo dividir documentos en páginas con Aspose.Words para Java.

## Preguntas frecuentes

### ¿Cómo agrego Aspose.Words para Java a mi proyecto?

Para agregar Aspose.Words para Java a su proyecto, siga estos pasos:

1. Descargue la biblioteca Aspose.Words para Java desde [aquí](https://releases.aspose.com/words/java/).
2. Agregue el archivo JAR descargado al classpath de su proyecto.
3. Ahora puede comenzar a utilizar Aspose.Words para Java en su proyecto.

### ¿Puedo dividir documentos en otros formatos, como PDF o DOCX?

No, esta guía trata específicamente sobre la división de documentos en formato DOC con Aspose.Words para Java. Si necesita dividir documentos en otros formatos, quizá deba explorar otras bibliotecas o herramientas compatibles con dichos formatos.

### ¿Es Aspose.Words para Java una biblioteca gratuita?

No, Aspose.Words para Java no es una biblioteca gratuita. Es un producto comercial con licencia. Puede visitar el sitio web. [Página de precios de Aspose.Words para Java](https://purchase.aspose.com/words/java) Para obtener más información sobre licencias y precios.

### ¿Puedo dividir documentos en tamaños de página y formatos personalizados?

Sí, puede personalizar el tamaño y el formato de página de los documentos divididos modificando las propiedades de configuración de página en Aspose.Words para Java. Consulte la documentación de Aspose.Words para obtener más información sobre cómo personalizar la configuración de página según sus necesidades.

### ¿Existe algún límite en el número de páginas que se pueden dividir?

Aspose.Words para Java no impone límites específicos en el número de páginas que se pueden dividir. Sin embargo, tenga en cuenta que los documentos muy grandes pueden requerir más memoria y tiempo de procesamiento. Tenga en cuenta los recursos del sistema al trabajar con documentos grandes.

### ¿Cómo puedo manejar encabezados y pies de página al dividir documentos?

Los encabezados y pies de página se pueden gestionar al dividir documentos mediante la biblioteca Aspose.Words para Java. Puede copiar el contenido del encabezado y pie de página del documento original a los documentos divididos, garantizando su correcta conservación. Es posible que deba personalizar este proceso según sus requisitos específicos de encabezado y pie de página.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}