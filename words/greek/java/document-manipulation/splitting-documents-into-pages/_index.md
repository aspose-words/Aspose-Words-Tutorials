---
title: Διαχωρισμός εγγράφων σε σελίδες στο Aspose.Words για Java
linktitle: Διαχωρισμός εγγράφων σε σελίδες
second_title: Aspose.Words Java Document Processing API
description: Μάθετε πώς να χωρίζετε έγγραφα σε σελίδες χρησιμοποιώντας το Aspose.Words για Java. Οδηγός βήμα προς βήμα με πηγαίο κώδικα για αποτελεσματική επεξεργασία εγγράφων.
weight: 23
url: /el/java/document-manipulation/splitting-documents-into-pages/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Διαχωρισμός εγγράφων σε σελίδες στο Aspose.Words για Java


Εάν εργάζεστε με την επεξεργασία εγγράφων σε Java, το Aspose.Words για Java είναι ένα ισχυρό API που μπορεί να σας βοηθήσει να χωρίσετε τα έγγραφα σε ξεχωριστές σελίδες αποτελεσματικά. Σε αυτό το βήμα προς βήμα σεμινάριο, θα σας καθοδηγήσουμε στη διαδικασία διαχωρισμού εγγράφων χρησιμοποιώντας τον παρεχόμενο πηγαίο κώδικα. Μέχρι το τέλος αυτού του σεμιναρίου, θα μπορείτε να χωρίζετε εύκολα έγγραφα, βελτιώνοντας τις δυνατότητες διαχείρισης εγγράφων σας.

## 1. Εισαγωγή

Το Aspose.Words for Java είναι μια βιβλιοθήκη Java που σας επιτρέπει να χειρίζεστε έγγραφα του Word μέσω προγραμματισμού. Μια κοινή εργασία είναι ο διαχωρισμός ενός εγγράφου σε ξεχωριστές σελίδες, οι οποίες μπορεί να είναι χρήσιμες για διάφορους σκοπούς, όπως αρχειοθέτηση, εκτύπωση ή επεξεργασία εγγράφων.

## 2. Προαπαιτούμενα

Πριν βουτήξουμε στον κώδικα, βεβαιωθείτε ότι έχετε τις ακόλουθες προϋποθέσεις:

- Το Java Development Kit (JDK) είναι εγκατεστημένο στο σύστημά σας.
-  Βιβλιοθήκη Aspose.Words for Java, την οποία μπορείτε να κατεβάσετε[εδώ](https://releases.aspose.com/words/java/).

## 3. Ρύθμιση του περιβάλλοντος σας

Για να ξεκινήσετε, ρυθμίστε το περιβάλλον ανάπτυξής σας ως εξής:

- Δημιουργήστε ένα έργο Java στο ενσωματωμένο περιβάλλον ανάπτυξης (IDE) που προτιμάτε.
- Προσθέστε τη βιβλιοθήκη Aspose.Words for Java στο έργο σας. Μπορείτε να ανατρέξετε στο[απόδειξη με έγγραφα](https://reference.aspose.com/words/java/) για αναλυτικές οδηγίες.

## 4. Κατανόηση του Πηγαίου Κώδικα

Ο πηγαίος κώδικας που παρείχατε έχει σχεδιαστεί για να χωρίζει ένα έγγραφο σε ξεχωριστές σελίδες. Ας αναλύσουμε τα βασικά στοιχεία:

```java
String fileName = FilenameUtils.getBaseName(docName);
String extensionName = FilenameUtils.getExtension(docName);
System.out.println("Processing document: " + fileName + "." + extensionName);
Document doc = new Document(docName);
```

- Εξάγουμε το όνομα βάσης και την επέκταση του εγγράφου εισόδου.
- Φορτώνουμε το έγγραφο χρησιμοποιώντας το Aspose.Words για Java.

## 5. Διαχωρισμός εγγράφων βήμα προς βήμα

### 5.1. Φόρτωση του εγγράφου

```java
Document doc = new Document(docName);
```

 Σε αυτό το βήμα, φορτώνουμε το έγγραφο εισόδου στο a`Document` αντικείμενο, το οποίο μας επιτρέπει να εργαστούμε με το περιεχόμενο του εγγράφου.

### 5.2. Εκκίνηση του DocumentPageSplitter

```java
DocumentPageSplitter splitter = new DocumentPageSplitter(doc);
```

 Αρχικοποιούμε α`DocumentPageSplitter` αντικείμενο με το φορτωμένο έγγραφό μας. Αυτή η κλάση παρέχεται από το Aspose.Words για Java και μας βοηθά να χωρίσουμε το έγγραφο σε σελίδες.

### 5.3. Αποθήκευση κάθε σελίδας

```java
for (int page = 1; page <= doc.getPageCount(); page++) {
    Document pageDoc = splitter.getDocumentOfPage(page);
    pageDoc.save("Your Directory Path" + MessageFormat.format("{0} - page{1}.{2}", fileName, page, extensionName));
}
```

Σε αυτό το βήμα, επαναλαμβάνουμε κάθε σελίδα του εγγράφου και το αποθηκεύουμε ως ξεχωριστό έγγραφο. Μπορείτε να καθορίσετε τη διαδρομή καταλόγου όπου θα αποθηκευτούν οι διαχωρισμένες σελίδες.

## 6. Εκτέλεση του Κώδικα

Για να εκτελέσετε αυτόν τον κώδικα με επιτυχία, βεβαιωθείτε ότι έχετε ρυθμίσει το περιβάλλον σας και έχετε προσθέσει τη βιβλιοθήκη Aspose.Words for Java στο έργο σας. Στη συνέχεια, εκτελέστε τον κώδικα και θα χωρίσετε το έγγραφό σας σε ξεχωριστές σελίδες.

## Πηγαίος κώδικας DocumentPageSplitter

```java
/// <περίληψη>
/// Διαχωρίζει ένα έγγραφο σε πολλά έγγραφα, ένα ανά σελίδα.
/// </summary>
class DocumentPageSplitter
{
private PageNumberFinder pageNumberFinder;
/// <περίληψη>
/// Αρχικοποιεί μια νέα παρουσία της κλάσης <δείτε cref="DocumentPageSplitter"/>.
/// Αυτή η μέθοδος χωρίζει το έγγραφο σε ενότητες έτσι ώστε κάθε σελίδα να ξεκινά και να τελειώνει σε ένα όριο ενότητας.
/// Συνιστάται να μην τροποποιήσετε το έγγραφο στη συνέχεια.
/// </summary>
/// <param name="source">Έγγραφο πηγής</param>
public DocumentPageSplitter(Document source) throws Exception
{
	pageNumberFinder = PageNumberFinderFactory.create(source);
}
private Document getDocument() {
	return pageNumberFinder.getDocument();
}
/// <περίληψη>
/// Λαμβάνει το έγγραφο μιας σελίδας.
/// </summary>
/// <param name="pageIndex">
/// Ευρετήριο μιας σελίδας βάσει 1.
/// </param>
/// <επιστρέφει>
/// Το <δείτε cref="Document"/>.
/// </returns>
public Document getDocumentOfPage(int pageIndex) throws Exception {
	return getDocumentOfPageRange(pageIndex, pageIndex);
}
/// <περίληψη>
//Λαμβάνει το έγγραφο μιας περιοχής σελίδων.
/// </summary>
/// <param name="startIndex">
/// Ευρετήριο βασισμένο σε 1 της αρχικής σελίδας.
/// </param>
/// <param name="endIndex">
/// Ευρετήριο βάσει 1 της τελικής σελίδας.
/// </param>
/// <επιστρέφει>
/// Το <δείτε cref="Document"/>.
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
/// <περίληψη>
/// Παρέχει μεθόδους για την εξαγωγή κόμβων ενός εγγράφου που αποδίδονται σε καθορισμένες σελίδες.
/// </summary>
class PageNumberFinder
{
// Χαρτίζει τον κόμβο σε αριθμούς σελίδας έναρξης/τελικού.
// Αυτό χρησιμοποιείται για την παράκαμψη των αριθμών σελίδων βάσης που παρέχονται από τον συλλέκτη όταν το έγγραφο χωρίζεται.
private Map<Node, Integer> nodeStartPageLookup = new HashMap<>();
private Map<Node, Integer> nodeEndPageLookup = new HashMap<>();
private LayoutCollector collector;
// Αντιστοιχίζει τον αριθμό σελίδας σε μια λίστα κόμβων που βρίσκονται σε αυτήν τη σελίδα.
private Map<Integer, ArrayList<Node>> reversePageLookup;
/// <περίληψη>
/// Αρχικοποιεί μια νέα παρουσία της κλάσης <δείτε cref="PageNumberFinder"/>.
/// </summary>
/// <param name="collector">Ένα στιγμιότυπο συλλέκτη που διαθέτει εγγραφές μοντέλου διάταξης για το έγγραφο.</param>
public PageNumberFinder(LayoutCollector collector)
{
	this.collector = collector;
}
public Document getDocument()
{
	return collector.getDocument();
}
/// <περίληψη>
/// Ανακτά ευρετήριο βάσει 1 μιας σελίδας από την οποία ξεκινά ο κόμβος.
/// </summary>
/// <param name="node">
/// Ο κόμβος.
/// </param>
/// <επιστρέφει>
/// Ευρετήριο σελίδας.
/// </returns>
public int getPage(Node node) throws Exception {
	return nodeStartPageLookup.containsKey(node)
		? nodeStartPageLookup.get(node)
		: collector.getStartPageIndex(node);
}
/// <περίληψη>
/// Ανακτά ευρετήριο βάσει 1 μιας σελίδας στην οποία τελειώνει ο κόμβος.
/// </summary>
/// <param name="node">
/// Ο κόμβος.
/// </param>
/// <επιστρέφει>
/// Ευρετήριο σελίδας.
/// </returns>
public int getPageEnd(Node node) throws Exception {
	return nodeEndPageLookup.containsKey(node)
		? nodeEndPageLookup.get(node)
		: collector.getEndPageIndex(node);
}
/// <περίληψη>
//Επιστρέφει πόσες σελίδες εκτείνεται ο καθορισμένος κόμβος. Επιστρέφει 1 εάν ο κόμβος περιέχεται σε μία σελίδα.
/// </summary>
/// <param name="node">
/// Ο κόμβος.
/// </param>
/// <επιστρέφει>
/// Ευρετήριο σελίδας.
/// </returns>
public int pageSpan(Node node) throws Exception {
	return getPageEnd(node) - getPage(node) + 1;
}
/// <περίληψη>
/// Επιστρέφει μια λίστα με κόμβους που περιέχονται οπουδήποτε στην καθορισμένη σελίδα ή σελίδες που ταιριάζουν με τον καθορισμένο τύπο κόμβου.
/// </summary>
/// <param name="startPage">
/// Η αρχική σελίδα.
/// </param>
/// <param name="endPage">
/// Η τελική σελίδα.
/// </param>
/// <param name="nodeType">
/// Ο κόμβος Τύπος.
/// </param>
/// <επιστρέφει>
/// Το <δείτε cref="IList{T}"/>.
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
		// Ορισμένες σελίδες μπορεί να είναι κενές.
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
/// <περίληψη>
/// Διαχωρίζει τους κόμβους που εμφανίζονται σε δύο ή περισσότερες σελίδες σε ξεχωριστούς κόμβους, ώστε να εξακολουθούν να εμφανίζονται με τον ίδιο τρόπο
/// αλλά δεν εμφανίζονται πλέον σε μια σελίδα.
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
	// Επισκεφτείτε τυχόν σύνθετα υλικά που πιθανώς χωρίζονται σε σελίδες και χωρίστε τα σε ξεχωριστούς κόμβους.
	collector.getDocument().accept(new SectionSplitter(this));
}
/// <περίληψη>
/// Αυτό καλείται από το <δείτε cref="SectionSplitter"/> για να ενημερώσει τους αριθμούς σελίδων των διαχωρισμένων κόμβων.
/// </summary>
/// <param name="node">
/// Ο κόμβος.
/// </param>
/// <param name="startPage">
/// Η αρχική σελίδα.
/// </param>
/// <param name="endPage">
/// Η τελική σελίδα.
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
	// Προσθέστε κάθε κόμβο σε μια λίστα που αντιπροσωπεύει τους κόμβους που βρίσκονται σε κάθε σελίδα.
	for (Node node : (Iterable<Node>) collector.getDocument().getChildNodes(NodeType.ANY, true))
	{
		//Οι κεφαλίδες/τα υποσέλιδα ακολουθούν ενότητες και δεν χωρίζονται από μόνα τους.
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
/// <περίληψη>
/// Διαχωρίζει το κείμενο της καθορισμένης εκτέλεσης σε δύο εκτελέσεις.
/// Εισάγει τη νέα εκτέλεση αμέσως μετά την καθορισμένη εκτέλεση.
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
/// <περίληψη>
/// Διαχωρίζει ένα έγγραφο σε πολλαπλές ενότητες, έτσι ώστε κάθε σελίδα να αρχίζει και να τελειώνει σε ένα όριο ενότητας.
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
	// Εάν υπάρχει προηγούμενη ενότητα, προσπαθήστε να αντιγράψετε τυχόν συνδεδεμένα υποσέλιδα κεφαλίδων.
	// Διαφορετικά, δεν θα εμφανίζονται σε ένα εξαγόμενο έγγραφο εάν λείπει η προηγούμενη ενότητα.
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
	// Εάν η παράγραφος περιέχει μόνο αλλαγή ενότητας, προσθέστε το fake run in.
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
		// Καταργήστε την αρίθμηση λίστας από την κλωνοποιημένη παράγραφο, αλλά αφήστε την ίδια εσοχή
		// καθώς η παράγραφος υποτίθεται ότι αποτελεί μέρος του στοιχείου πριν.
		if (paragraph.isListItem())
		{
			double textPosition = clonePara.getListFormat().getListLevel().getTextPosition();
			clonePara.getListFormat().removeNumbers();
			clonePara.getParagraphFormat().setLeftIndent(textPosition);
		}
		// Επαναφέρετε τα κενά των διαχωρισμένων παραγράφων σε πίνακες, καθώς τα πρόσθετα κενά μπορεί να τους κάνουν να φαίνονται διαφορετικά.
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
		// Διορθώνει την αλλαγή σελίδας στο τέλος της ενότητας.
		SplitPageBreakCorrector.processSection(cloneSection);
	}
	SplitPageBreakCorrector.processSection(section);
	// Προσθέστε νέα αρίθμηση σελίδων και για το σώμα της ενότητας.
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
	// Ένας κόμβος μπορεί να εκτείνεται σε πολλές σελίδες, επομένως επιστρέφεται μια λίστα διαχωρισμένων θέσεων.
	//Ο διαχωρισμένος κόμβος είναι ο πρώτος κόμβος στην επόμενη σελίδα.
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
		// Εάν η σελίδα του θυγατρικού κόμβου έχει αλλάξει, τότε αυτή είναι η θέση διαχωρισμού.
		// Προσθέστε αυτό στη λίστα.
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
	// Διαχωρίστε τα σύνθετα υλικά προς τα πίσω, έτσι ώστε οι κλωνοποιημένοι κόμβοι να εισάγονται με τη σωστή σειρά.
	Collections.reverse(splitList);
	return splitList;
}
private CompositeNode splitCompositeAtNode(CompositeNode baseNode, Node targetNode) throws Exception {
	CompositeNode cloneNode = (CompositeNode) baseNode.deepClone(false);
	Node node = targetNode;
	int currentPageNum = pageNumberFinder.getPage(baseNode);
	// Μετακινήστε όλους τους κόμβους που βρέθηκαν στην επόμενη σελίδα στον αντιγραμμένο κόμβο. Χειριστείτε τους κόμβους σειρών ξεχωριστά.
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
		// Αν έχουμε να κάνουμε με μια σειρά, πρέπει να προσθέσουμε εικονικά κελιά για την κλωνοποιημένη σειρά.
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
	// Εισαγάγετε τον διαχωρισμένο κόμβο μετά το πρωτότυπο.
	baseNode.getParentNode().insertAfter(cloneNode, baseNode);
	// Ενημερώστε τους νέους αριθμούς σελίδων του κόμβου βάσης και του κλωνοποιημένου κόμβου, συμπεριλαμβανομένων των απογόνων του.
	// Αυτή θα είναι μόνο μία σελίδα, καθώς το κλωνοποιημένο σύνθετο στοιχείο χωρίζεται σε μία σελίδα.
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

## Σύναψη

Τώρα έχετε μάθει πώς να χωρίζετε ένα έγγραφο σε ξεχωριστές σελίδες χρησιμοποιώντας το Aspose.Words για Java. Αυτός ο οδηγός παρέχει έναν περιεκτικό οδηγό βήμα προς βήμα με παραδείγματα πηγαίου κώδικα. Μπορείτε να προσαρμόσετε περαιτέρω και να επεκτείνετε αυτόν τον κωδικό ώστε να ανταποκρίνεται στις συγκεκριμένες απαιτήσεις σας όταν εργάζεστε με έγγραφα.
Σίγουρα! Ας προσθέσουμε μια ενότητα Συνήθεις Ερωτήσεις στον οδηγό μας σχετικά με τον διαχωρισμό εγγράφων σε σελίδες χρησιμοποιώντας το Aspose.Words για Java.

## Συχνές ερωτήσεις

### Πώς μπορώ να προσθέσω το Aspose.Words για Java στο έργο μου;

Για να προσθέσετε Aspose.Words για Java στο έργο σας, ακολουθήστε τα εξής βήματα:

1.  Κατεβάστε τη βιβλιοθήκη Aspose.Words για Java από[εδώ](https://releases.aspose.com/words/java/).
2. Προσθέστε το ληφθέν αρχείο JAR στη διαδρομή τάξης του έργου σας.
3. Τώρα μπορείτε να αρχίσετε να χρησιμοποιείτε το Aspose.Words για Java στο έργο σας.

### Μπορώ να χωρίσω έγγραφα σε άλλες μορφές, όπως PDF ή DOCX;

Όχι, αυτός ο οδηγός καλύπτει συγκεκριμένα τον διαχωρισμό εγγράφων σε μορφή DOC χρησιμοποιώντας Aspose.Words για Java. Εάν χρειάζεται να χωρίσετε έγγραφα σε άλλες μορφές, ίσως χρειαστεί να εξερευνήσετε άλλες βιβλιοθήκες ή εργαλεία που υποστηρίζουν αυτές τις μορφές.

### Είναι το Aspose.Words για Java μια δωρεάν βιβλιοθήκη;

 Όχι, το Aspose.Words για Java δεν είναι δωρεάν βιβλιοθήκη. Είναι ένα εμπορικό προϊόν με τέλος αδειοδότησης. Μπορείτε να επισκεφθείτε το[Aspose.Words for Java σελίδα τιμολόγησης](https://purchase.aspose.com/words/java) για περισσότερες πληροφορίες σχετικά με τις λεπτομέρειες αδειοδότησης και τιμολόγησης.

### Μπορώ να χωρίσω έγγραφα σε προσαρμοσμένα μεγέθη και μορφές σελίδας;

Ναι, μπορείτε να προσαρμόσετε τα μεγέθη και τις μορφές σελίδας των διαχωρισμένων εγγράφων τροποποιώντας τις ιδιότητες ρύθμισης σελίδας στο Aspose.Words για Java. Ανατρέξτε στην τεκμηρίωση του Aspose.Words για λεπτομέρειες σχετικά με τον τρόπο προσαρμογής των ρυθμίσεων σελίδας σύμφωνα με τις απαιτήσεις σας.

### Υπάρχουν περιορισμοί στον αριθμό των σελίδων που μπορούν να διαχωριστούν;

Το Aspose.Words για Java δεν επιβάλλει συγκεκριμένους περιορισμούς στον αριθμό των σελίδων που μπορείτε να χωρίσετε. Ωστόσο, έχετε υπόψη σας ότι τα πολύ μεγάλα έγγραφα ενδέχεται να απαιτούν περισσότερη μνήμη και χρόνο επεξεργασίας. Έχετε υπόψη σας τους πόρους του συστήματος όταν εργάζεστε με μεγάλα έγγραφα.

### Πώς μπορώ να χειριστώ τις κεφαλίδες και τα υποσέλιδα κατά τον διαχωρισμό εγγράφων;

Οι κεφαλίδες και τα υποσέλιδα μπορούν να χειριστούν κατά τον διαχωρισμό εγγράφων χρησιμοποιώντας τη βιβλιοθήκη Aspose.Words για Java. Μπορείτε να αντιγράψετε περιεχόμενο κεφαλίδας και υποσέλιδου από το πρωτότυπο έγγραφο στα διαιρεμένα έγγραφα, διασφαλίζοντας ότι διατηρούνται σωστά. Ίσως χρειαστεί να προσαρμόσετε αυτήν τη διαδικασία με βάση τις συγκεκριμένες απαιτήσεις κεφαλίδας και υποσέλιδου.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
