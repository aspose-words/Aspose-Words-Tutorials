---
title: Diviser des documents en pages dans Aspose.Words pour Java
linktitle: Diviser des documents en pages
second_title: API de traitement de documents Java Aspose.Words
description: Apprenez à diviser des documents en pages à l'aide d'Aspose.Words pour Java. Guide étape par étape avec code source pour un traitement efficace des documents.
weight: 23
url: /fr/java/document-manipulation/splitting-documents-into-pages/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Diviser des documents en pages dans Aspose.Words pour Java


Si vous travaillez avec le traitement de documents en Java, Aspose.Words pour Java est une API puissante qui peut vous aider à diviser efficacement des documents en pages distinctes. Dans ce didacticiel étape par étape, nous vous guiderons tout au long du processus de division de documents à l'aide du code source fourni. À la fin de ce didacticiel, vous serez en mesure de diviser des documents en toute simplicité, améliorant ainsi vos capacités de gestion de documents.

## 1. Introduction

Aspose.Words for Java est une bibliothèque Java qui vous permet de manipuler des documents Word par programmation. Une tâche courante consiste à diviser un document en pages distinctes, ce qui peut être utile à diverses fins, telles que l'archivage, l'impression ou le traitement de documents.

## 2. Conditions préalables

Avant de plonger dans le code, assurez-vous que les conditions préalables suivantes sont remplies :

- Kit de développement Java (JDK) installé sur votre système.
-  Bibliothèque Aspose.Words pour Java, que vous pouvez télécharger[ici](https://releases.aspose.com/words/java/).

## 3. Configuration de votre environnement

Pour commencer, configurez votre environnement de développement comme suit :

- Créez un projet Java dans votre environnement de développement intégré (IDE) préféré.
- Ajoutez la bibliothèque Aspose.Words pour Java à votre projet. Vous pouvez vous référer à la[documentation](https://reference.aspose.com/words/java/) pour des instructions détaillées.

## 4. Comprendre le code source

Le code source que vous avez fourni est conçu pour diviser un document en pages distinctes. Décomposons les composants clés :

```java
String fileName = FilenameUtils.getBaseName(docName);
String extensionName = FilenameUtils.getExtension(docName);
System.out.println("Processing document: " + fileName + "." + extensionName);
Document doc = new Document(docName);
```

- Nous extrayons le nom de base et l’extension du document d’entrée.
- Nous chargeons le document en utilisant Aspose.Words pour Java.

## 5. Fractionnement des documents étape par étape

### 5.1. Chargement du document

```java
Document doc = new Document(docName);
```

 Dans cette étape, nous chargeons le document d'entrée dans un`Document` objet qui nous permet de travailler avec le contenu du document.

### 5.2. Initialisation du DocumentPageSplitter

```java
DocumentPageSplitter splitter = new DocumentPageSplitter(doc);
```

 Nous initialisons un`DocumentPageSplitter` objet avec notre document chargé. Cette classe est fournie par Aspose.Words pour Java et nous aide à diviser le document en pages.

### 5.3. Sauvegarde de chaque page

```java
for (int page = 1; page <= doc.getPageCount(); page++) {
    Document pageDoc = splitter.getDocumentOfPage(page);
    pageDoc.save("Your Directory Path" + MessageFormat.format("{0} - page{1}.{2}", fileName, page, extensionName));
}
```

Dans cette étape, nous parcourons chaque page du document et l'enregistrons en tant que document distinct. Vous pouvez spécifier le chemin du répertoire dans lequel les pages séparées seront enregistrées.

## 6. Exécution du code

Pour exécuter ce code avec succès, assurez-vous d'avoir configuré votre environnement et ajouté la bibliothèque Aspose.Words pour Java à votre projet. Ensuite, exécutez le code et votre document sera divisé en pages distinctes.

## Code source de DocumentPageSplitter

```java
/// <résumé>
/// Divise un document en plusieurs documents, un par page.
/// </summary>
class DocumentPageSplitter
{
private PageNumberFinder pageNumberFinder;
/// <résumé>
/// Initialise une nouvelle instance de la classe <see cref="DocumentPageSplitter"/>.
/// Cette méthode divise le document en sections de sorte que chaque page commence et se termine à une limite de section.
/// Il est recommandé de ne pas modifier le document par la suite.
/// </summary>
/// <param name="source">Document source</param>
public DocumentPageSplitter(Document source) throws Exception
{
	pageNumberFinder = PageNumberFinderFactory.create(source);
}
private Document getDocument() {
	return pageNumberFinder.getDocument();
}
/// <résumé>
/// Obtient le document d'une page.
/// </summary>
/// <param name="pageIndex">
/// index basé sur 1 d'une page.
/// </param>
/// <retourne>
/// Le <see cref="Document"/>.
/// </retours>
public Document getDocumentOfPage(int pageIndex) throws Exception {
	return getDocumentOfPageRange(pageIndex, pageIndex);
}
/// <résumé>
//Obtient le document d'une plage de pages.
/// </summary>
/// <param name="startIndex">
/// Index basé sur 1 de la page de démarrage.
/// </param>
/// <param name="endIndex">
/// Index basé sur 1 de la page de fin.
/// </param>
/// <retourne>
/// Le <see cref="Document"/>.
/// </retours>
public Document getDocumentOfPageRange(int startIndex, int endIndex) throws Exception {
	Document result = (Document) getDocument().deepClone(false);
	for (Node section : pageNumberFinder.retrieveAllNodesOnPages(startIndex, endIndex, NodeType.SECTION))
	{
		result.appendChild(result.importNode(section, true));
	}
	return result;
}
}
/// <résumé>
/// Fournit des méthodes pour extraire les nœuds d'un document qui sont rendus sur des pages spécifiées.
/// </summary>
class PageNumberFinder
{
// Mappe le nœud vers les numéros de page de début/fin.
// Ceci est utilisé pour remplacer les numéros de page de base fournis par le collecteur lorsque le document est divisé.
private Map<Node, Integer> nodeStartPageLookup = new HashMap<>();
private Map<Node, Integer> nodeEndPageLookup = new HashMap<>();
private LayoutCollector collector;
// Associe le numéro de page à une liste de nœuds trouvés sur cette page.
private Map<Integer, ArrayList<Node>> reversePageLookup;
/// <résumé>
/// Initialise une nouvelle instance de la classe <see cref="PageNumberFinder"/>.
/// </summary>
/// <param name="collector">Une instance de collecteur qui possède des enregistrements de modèle de mise en page pour le document.</param>
public PageNumberFinder(LayoutCollector collector)
{
	this.collector = collector;
}
public Document getDocument()
{
	return collector.getDocument();
}
/// <résumé>
/// Récupère l'index basé sur 1 d'une page sur laquelle le nœud commence.
/// </summary>
/// <param name="node">
/// Le nœud.
/// </param>
/// <retourne>
/// Index des pages.
/// </retours>
public int getPage(Node node) throws Exception {
	return nodeStartPageLookup.containsKey(node)
		? nodeStartPageLookup.get(node)
		: collector.getStartPageIndex(node);
}
/// <résumé>
/// Récupère l'index basé sur 1 d'une page sur laquelle se termine le nœud.
/// </summary>
/// <param name="node">
/// Le nœud.
/// </param>
/// <retourne>
/// Index des pages.
/// </retours>
public int getPageEnd(Node node) throws Exception {
	return nodeEndPageLookup.containsKey(node)
		? nodeEndPageLookup.get(node)
		: collector.getEndPageIndex(node);
}
/// <résumé>
//Renvoie le nombre de pages sur lesquelles s'étend le nœud spécifié. Renvoie 1 si le nœud est contenu dans une seule page.
/// </summary>
/// <param name="node">
/// Le nœud.
/// </param>
/// <retourne>
/// Index des pages.
/// </retours>
public int pageSpan(Node node) throws Exception {
	return getPageEnd(node) - getPage(node) + 1;
}
/// <résumé>
/// Renvoie une liste de nœuds contenus n'importe où sur la page spécifiée ou les pages qui correspondent au type de nœud spécifié.
/// </summary>
/// <param name="startPage">
/// La page de démarrage.
/// </param>
/// <param name="endPage">
/// La page de fin.
/// </param>
/// <param name="nodeType">
/// Le type de nœud.
/// </param>
/// <retourne>
/// Le <see cref="IList{T}"/>.
/// </retours>
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
		// Certaines pages peuvent être vides.
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
/// <résumé>
/// Divise les nœuds qui apparaissent sur deux pages ou plus en nœuds distincts afin qu'ils apparaissent toujours de la même manière
/// mais n'apparaissent plus sur une page.
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
	// Visitez tous les composites qui sont éventuellement divisés sur plusieurs pages et divisez-les en nœuds distincts.
	collector.getDocument().accept(new SectionSplitter(this));
}
/// <résumé>
/// Ceci est appelé par <see cref="SectionSplitter"/> pour mettre à jour les numéros de page des nœuds divisés.
/// </summary>
/// <param name="node">
/// Le nœud.
/// </param>
/// <param name="startPage">
/// La page de démarrage.
/// </param>
/// <param name="endPage">
/// La page de fin.
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
	// Ajoutez chaque nœud à une liste qui représente les nœuds trouvés sur chaque page.
	for (Node node : (Iterable<Node>) collector.getDocument().getChildNodes(NodeType.ANY, true))
	{
		//Les en-têtes/pieds de page suivent les sections et ne sont pas divisés par eux-mêmes.
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
/// <résumé>
/// Divise le texte de l'exécution spécifiée en deux exécutions.
/// Insère la nouvelle exécution juste après l'exécution spécifiée.
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
/// <résumé>
/// Divise un document en plusieurs sections afin que chaque page commence et se termine à une limite de section.
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
	// S'il existe une section précédente, essayez de copier tous les en-têtes et pieds de page liés.
	// Sinon, ils n'apparaîtront pas dans un document extrait si la section précédente est manquante.
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
	// Si le paragraphe contient uniquement un saut de section, ajoutez un faux saut.
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
		// Supprimer la numérotation de la liste du paragraphe cloné mais laisser le retrait identique
		// car le paragraphe est censé faire partie de l'élément précédent.
		if (paragraph.isListItem())
		{
			double textPosition = clonePara.getListFormat().getListLevel().getTextPosition();
			clonePara.getListFormat().removeNumbers();
			clonePara.getParagraphFormat().setLeftIndent(textPosition);
		}
		// Réinitialisez l'espacement des paragraphes divisés dans les tableaux, car un espacement supplémentaire peut les rendre différents.
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
		// Corrige le saut de page à la fin de la section.
		SplitPageBreakCorrector.processSection(cloneSection);
	}
	SplitPageBreakCorrector.processSection(section);
	// Ajoutez également une nouvelle numérotation de page pour le corps de la section.
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
	// Un nœud peut s'étendre sur plusieurs pages, une liste de positions divisées est donc renvoyée.
	//Le nœud divisé est le premier nœud de la page suivante.
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
		// Si la page du nœud enfant a changé, il s'agit de la position de division.
		// Ajoutez ceci à la liste.
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
	// Divisez les composites vers l'arrière, de sorte que les nœuds clonés soient insérés dans le bon ordre.
	Collections.reverse(splitList);
	return splitList;
}
private CompositeNode splitCompositeAtNode(CompositeNode baseNode, Node targetNode) throws Exception {
	CompositeNode cloneNode = (CompositeNode) baseNode.deepClone(false);
	Node node = targetNode;
	int currentPageNum = pageNumberFinder.getPage(baseNode);
	// Déplacez tous les nœuds trouvés sur la page suivante dans le nœud copié. Gérez les nœuds de ligne séparément.
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
		// Si nous avons affaire à une ligne, nous devons ajouter des cellules factices pour la ligne clonée.
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
	// Insérer le nœud divisé après l’original.
	baseNode.getParentNode().insertAfter(cloneNode, baseNode);
	// Mettez à jour les nouveaux numéros de page du nœud de base et du nœud cloné, y compris ses descendants.
	// Il ne s'agira que d'une seule page car le composite cloné est divisé pour figurer sur une seule page.
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

## Conclusion

Vous avez maintenant appris à diviser un document en pages distinctes à l'aide d'Aspose.Words pour Java. Ce guide fournit un didacticiel complet étape par étape avec des exemples de code source. Vous pouvez personnaliser et étendre davantage ce code pour répondre à vos besoins spécifiques lorsque vous travaillez avec des documents.
Bien sûr ! Ajoutons une section FAQ à notre guide sur la division de documents en pages à l'aide d'Aspose.Words pour Java.

## FAQ

### Comment ajouter Aspose.Words pour Java à mon projet ?

Pour ajouter Aspose.Words pour Java à votre projet, suivez ces étapes :

1.  Téléchargez la bibliothèque Aspose.Words pour Java depuis[ici](https://releases.aspose.com/words/java/).
2. Ajoutez le fichier JAR téléchargé au classpath de votre projet.
3. Vous pouvez maintenant commencer à utiliser Aspose.Words pour Java dans votre projet.

### Puis-je diviser des documents dans d’autres formats, tels que PDF ou DOCX ?

Non, ce guide traite spécifiquement du fractionnement de documents au format DOC à l'aide d'Aspose.Words pour Java. Si vous devez fractionner des documents dans d'autres formats, vous devrez peut-être explorer d'autres bibliothèques ou outils prenant en charge ces formats.

### Aspose.Words pour Java est-elle une bibliothèque gratuite ?

 Non, Aspose.Words for Java n'est pas une bibliothèque gratuite. Il s'agit d'un produit commercial avec des frais de licence. Vous pouvez visiter le site[Page de tarification d'Aspose.Words pour Java](https://purchase.aspose.com/words/java) pour plus d'informations sur les détails des licences et des prix.

### Puis-je diviser des documents en tailles et formats de page personnalisés ?

Oui, vous pouvez personnaliser les tailles et les formats de page des documents fractionnés en modifiant les propriétés de configuration de page dans Aspose.Words pour Java. Reportez-vous à la documentation Aspose.Words pour plus de détails sur la personnalisation des paramètres de page en fonction de vos besoins.

### Existe-t-il des limites quant au nombre de pages pouvant être divisées ?

Aspose.Words pour Java n'impose pas de limites spécifiques quant au nombre de pages que vous pouvez diviser. Cependant, gardez à l'esprit que les documents très volumineux peuvent nécessiter davantage de mémoire et de temps de traitement. Soyez attentif aux ressources système lorsque vous travaillez avec des documents volumineux.

### Comment puis-je gérer les en-têtes et les pieds de page lors du fractionnement de documents ?

Les en-têtes et les pieds de page peuvent être gérés lors du fractionnement de documents à l'aide de la bibliothèque Aspose.Words pour Java. Vous pouvez copier le contenu de l'en-tête et du pied de page du document d'origine vers les documents fractionnés, en vous assurant qu'ils sont correctement conservés. Vous devrez peut-être personnaliser ce processus en fonction de vos exigences spécifiques en matière d'en-tête et de pied de page.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
