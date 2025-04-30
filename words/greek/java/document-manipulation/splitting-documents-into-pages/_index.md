---
"description": "Μάθετε πώς να χωρίζετε έγγραφα σε σελίδες χρησιμοποιώντας το Aspose.Words για Java. Οδηγός βήμα προς βήμα με πηγαίο κώδικα για αποτελεσματική επεξεργασία εγγράφων."
"linktitle": "Διαχωρισμός εγγράφων σε σελίδες"
"second_title": "API επεξεργασίας εγγράφων Java Aspose.Words"
"title": "Διαχωρισμός εγγράφων σε σελίδες στο Aspose.Words για Java"
"url": "/el/java/document-manipulation/splitting-documents-into-pages/"
"weight": 23
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Διαχωρισμός εγγράφων σε σελίδες στο Aspose.Words για Java


Εάν εργάζεστε με την επεξεργασία εγγράφων σε Java, το Aspose.Words για Java είναι ένα ισχυρό API που μπορεί να σας βοηθήσει να διαχωρίσετε έγγραφα σε ξεχωριστές σελίδες αποτελεσματικά. Σε αυτό το βήμα προς βήμα σεμινάριο, θα σας καθοδηγήσουμε στη διαδικασία διαχωρισμού εγγράφων χρησιμοποιώντας τον παρεχόμενο πηγαίο κώδικα. Μέχρι το τέλος αυτού του σεμιναρίου, θα μπορείτε να διαχωρίζετε έγγραφα με ευκολία, βελτιώνοντας τις δυνατότητες διαχείρισης εγγράφων σας.

## 1. Εισαγωγή

Το Aspose.Words για Java είναι μια βιβλιοθήκη Java που σας επιτρέπει να χειρίζεστε έγγραφα του Word μέσω προγραμματισμού. Μια συνηθισμένη εργασία είναι η διαίρεση ενός εγγράφου σε ξεχωριστές σελίδες, η οποία μπορεί να είναι χρήσιμη για διάφορους σκοπούς, όπως αρχειοθέτηση, εκτύπωση ή επεξεργασία εγγράφων.

## 2. Προαπαιτούμενα

Πριν εμβαθύνουμε στον κώδικα, βεβαιωθείτε ότι έχετε τις ακόλουθες προϋποθέσεις:

- Το Java Development Kit (JDK) είναι εγκατεστημένο στο σύστημά σας.
- Aspose.Words για τη βιβλιοθήκη Java, την οποία μπορείτε να κατεβάσετε [εδώ](https://releases.aspose.com/words/java/).

## 3. Ρύθμιση του Περιβάλλοντός σας

Για να ξεκινήσετε, ρυθμίστε το περιβάλλον ανάπτυξής σας ως εξής:

- Δημιουργήστε ένα έργο Java στο Ολοκληρωμένο Περιβάλλον Ανάπτυξης (IDE) της προτίμησής σας.
- Προσθέστε τη βιβλιοθήκη Aspose.Words για Java στο έργο σας. Μπορείτε να ανατρέξετε στο [απόδειξη με έγγραφα](https://reference.aspose.com/words/java/) για λεπτομερείς οδηγίες.

## 4. Κατανόηση του πηγαίου κώδικα

Ο πηγαίος κώδικας που παρείχατε έχει σχεδιαστεί για να χωρίζει ένα έγγραφο σε ξεχωριστές σελίδες. Ας αναλύσουμε τα βασικά στοιχεία:

```java
String fileName = FilenameUtils.getBaseName(docName);
String extensionName = FilenameUtils.getExtension(docName);
System.out.println("Processing document: " + fileName + "." + extensionName);
Document doc = new Document(docName);
```

- Εξάγουμε το βασικό όνομα και την επέκταση του εγγράφου εισόδου.
- Φορτώνουμε το έγγραφο χρησιμοποιώντας το Aspose.Words για Java.

## 5. Διαχωρισμός εγγράφων βήμα προς βήμα

### 5.1. Φόρτωση του εγγράφου

```java
Document doc = new Document(docName);
```

Σε αυτό το βήμα, φορτώνουμε το έγγραφο εισόδου σε ένα `Document` αντικείμενο, το οποίο μας επιτρέπει να εργαστούμε με το περιεχόμενο του εγγράφου.

### 5.2. Αρχικοποίηση του DocumentPageSplitter

```java
DocumentPageSplitter splitter = new DocumentPageSplitter(doc);
```

Αρχικοποιούμε ένα `DocumentPageSplitter` αντικείμενο με το φορτωμένο έγγραφό μας. Αυτή η κλάση παρέχεται από το Aspose.Words για Java και μας βοηθά να χωρίσουμε το έγγραφο σε σελίδες.

### 5.3. Αποθήκευση κάθε σελίδας

```java
for (int page = 1; page <= doc.getPageCount(); page++) {
    Document pageDoc = splitter.getDocumentOfPage(page);
    pageDoc.save("Your Directory Path" + MessageFormat.format("{0} - page{1}.{2}", fileName, page, extensionName));
}
```

Σε αυτό το βήμα, εξετάζουμε κάθε σελίδα του εγγράφου και το αποθηκεύουμε ως ξεχωριστό έγγραφο. Μπορείτε να καθορίσετε τη διαδρομή καταλόγου όπου θα αποθηκευτούν οι διαχωρισμένες σελίδες.

## 6. Εκτέλεση του Κώδικα

Για να εκτελέσετε αυτόν τον κώδικα με επιτυχία, βεβαιωθείτε ότι έχετε ρυθμίσει το περιβάλλον σας και έχετε προσθέσει τη βιβλιοθήκη Aspose.Words για Java στο έργο σας. Στη συνέχεια, εκτελέστε τον κώδικα και το έγγραφό σας θα χωριστεί σε ξεχωριστές σελίδες.

## Πηγαίος κώδικας DocumentPageSplitter

```java
/// <σύνοψη>
/// Διαχωρίζει ένα έγγραφο σε πολλά έγγραφα, ένα ανά σελίδα.
/// </σύνοψη>
class DocumentPageSplitter
{
private PageNumberFinder pageNumberFinder;
/// <σύνοψη>
/// Αρχικοποιεί μια νέα παρουσία της κλάσης <see cref="DocumentPageSplitter"/>.
/// Αυτή η μέθοδος χωρίζει το έγγραφο σε ενότητες έτσι ώστε κάθε σελίδα να ξεκινά και να τελειώνει σε ένα όριο ενότητας.
/// Συνιστάται να μην τροποποιήσετε το έγγραφο αργότερα.
/// </σύνοψη>
/// <param name="source">Έγγραφο πηγής</param>
public DocumentPageSplitter(Document source) throws Exception
{
	pageNumberFinder = PageNumberFinderFactory.create(source);
}
private Document getDocument() {
	return pageNumberFinder.getDocument();
}
/// <σύνοψη>
/// Λαμβάνει το έγγραφο μιας σελίδας.
/// </σύνοψη>
/// <param name="pageIndex">
//Ευρετήριο μιας σελίδας με βάση / 1.
/// </param>
/// <επιστρέφει>
/// Το <βλ. cref="Έγγραφο"/>.
/// </returns>
public Document getDocumentOfPage(int pageIndex) throws Exception {
	return getDocumentOfPageRange(pageIndex, pageIndex);
}
/// <σύνοψη>
/// Λαμβάνει το έγγραφο μιας περιοχής σελίδων.
/// </σύνοψη>
/// <param name="startIndex">
//Ευρετήριο της αρχικής σελίδας με βάση / 1.
/// </param>
//<param name="endIndex">
//Ευρετήριο της τελικής σελίδας με βάση / 1.
/// </param>
/// <επιστρέφει>
/// Το <βλ. cref="Έγγραφο"/>.
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
/// <σύνοψη>
/// Παρέχει μεθόδους για την εξαγωγή κόμβων ενός εγγράφου που αποδίδονται σε συγκεκριμένες σελίδες.
/// </σύνοψη>
class PageNumberFinder
{
// Αντιστοιχίζει έναν κόμβο σε αριθμούς αρχικής/τελικής σελίδας.
// Αυτό χρησιμοποιείται για την παράκαμψη των αριθμών σελίδων βάσης που παρέχονται από τον συλλέκτη κατά τη διαίρεση του εγγράφου.
private Map<Node, Integer> nodeStartPageLookup = new HashMap<>();
private Map<Node, Integer> nodeEndPageLookup = new HashMap<>();
private LayoutCollector collector;
// Αντιστοιχίζει τον αριθμό σελίδας σε μια λίστα κόμβων που βρίσκονται σε αυτήν τη σελίδα.
private Map<Integer, ArrayList<Node>> reversePageLookup;
/// <σύνοψη>
/// Αρχικοποιεί μια νέα παρουσία της κλάσης <see cref="PageNumberFinder"/>.
/// </σύνοψη>
/// <param name="collector">Μια παρουσία συλλέκτη που έχει εγγραφές μοντέλου διάταξης για το έγγραφο.</param>
public PageNumberFinder(LayoutCollector collector)
{
	this.collector = collector;
}
public Document getDocument()
{
	return collector.getDocument();
}
/// <σύνοψη>
/// Ανακτά το ευρετήριο που βασίζεται σε 1 μιας σελίδας από την οποία ξεκινά ο κόμβος.
/// </σύνοψη>
/// <param name="node">
/// Ο κόμβος.
/// </param>
/// <επιστρέφει>
/// Ευρετήριο σελίδων.
/// </returns>
public int getPage(Node node) throws Exception {
	return nodeStartPageLookup.containsKey(node)
		? nodeStartPageLookup.get(node)
		: collector.getStartPageIndex(node);
}
/// <σύνοψη>
/// Ανακτά το ευρετήριο που βασίζεται στο 1 μιας σελίδας στην οποία καταλήγει ο κόμβος.
/// </σύνοψη>
/// <param name="node">
/// Ο κόμβος.
/// </param>
/// <επιστρέφει>
/// Ευρετήριο σελίδων.
/// </returns>
public int getPageEnd(Node node) throws Exception {
	return nodeEndPageLookup.containsKey(node)
		? nodeEndPageLookup.get(node)
		: collector.getEndPageIndex(node);
}
/// <σύνοψη>
/// Επιστρέφει τον αριθμό των σελίδων που εκτείνεται ο καθορισμένος κόμβος. Επιστρέφει 1 εάν ο κόμβος περιέχεται σε μία σελίδα.
/// </σύνοψη>
/// <param name="node">
/// Ο κόμβος.
/// </param>
/// <επιστρέφει>
/// Ευρετήριο σελίδων.
/// </returns>
public int pageSpan(Node node) throws Exception {
	return getPageEnd(node) - getPage(node) + 1;
}
/// <σύνοψη>
/// Επιστρέφει μια λίστα κόμβων που περιέχονται οπουδήποτε στην καθορισμένη σελίδα ή σελίδες που ταιριάζουν με τον καθορισμένο τύπο κόμβου.
/// </σύνοψη>
/// <param name="startPage">
/// Η αρχική σελίδα.
/// </param>
/// <param name="endPage">
/// Η τελευταία σελίδα.
/// </param>
/// <param name="τύπος κόμβου">
/// Ο Τύπος κόμβου.
/// </param>
/// <επιστρέφει>
/// Το <βλέπε cref="IList{T}"/>.
/// </returns>
public ArrayList<Node> retrieveAllNodesOnPages(int startPage, int endPage, /*Τύπος κόμβου*/int nodeType) throws Exception
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
/// <σύνοψη>
/// Διαχωρίζει τους κόμβους που εμφανίζονται σε δύο ή περισσότερες σελίδες σε ξεχωριστούς κόμβους, έτσι ώστε να εξακολουθούν να εμφανίζονται με τον ίδιο τρόπο
/// αλλά δεν εμφανίζονται πλέον σε μια σελίδα.
/// </σύνοψη>
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
	// Επισκεφθείτε τυχόν σύνθετα στοιχεία που ενδεχομένως είναι χωρισμένα σε σελίδες και χωρίστε τα σε ξεχωριστούς κόμβους.
	collector.getDocument().accept(new SectionSplitter(this));
}
/// <σύνοψη>
/// Αυτό καλείται από το <see cref="SectionSplitter"/> για την ενημέρωση των αριθμών σελίδων των διαιρεμένων κόμβων.
/// </σύνοψη>
/// <param name="node">
/// Ο κόμβος.
/// </param>
/// <param name="startPage">
/// Η αρχική σελίδα.
/// </param>
/// <param name="endPage">
/// Η τελευταία σελίδα.
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
		// Οι κεφαλίδες/υποσέλιδα ακολουθούν τις ενότητες και δεν χωρίζονται μόνα τους.
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
/// <σύνοψη>
/// Διαχωρίζει το κείμενο της καθορισμένης εκτέλεσης σε δύο εκτελέσεις.
/// Εισάγει τη νέα εκτέλεση αμέσως μετά την καθορισμένη εκτέλεση.
/// </σύνοψη>
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
/// <σύνοψη>
/// Χωρίζει ένα έγγραφο σε πολλές ενότητες έτσι ώστε κάθε σελίδα να ξεκινά και να τελειώνει σε ένα όριο ενότητας.
/// </σύνοψη>
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
	// Εάν υπάρχει προηγούμενη ενότητα, προσπαθήστε να αντιγράψετε τυχόν συνδεδεμένα υποσέλιδα κεφαλίδας.
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
	// Εάν η παράγραφος περιέχει μόνο αλλαγή ενότητας, προσθέστε ψεύτικη εκτέλεση.
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
		// Αφαίρεση αρίθμησης λίστας από την κλωνοποιημένη παράγραφο, αλλά αφήσιμο της ίδιας εσοχής 
		// καθώς η παράγραφος υποτίθεται ότι αποτελεί μέρος του προηγούμενου στοιχείου.
		if (paragraph.isListItem())
		{
			double textPosition = clonePara.getListFormat().getListLevel().getTextPosition();
			clonePara.getListFormat().removeNumbers();
			clonePara.getParagraphFormat().setLeftIndent(textPosition);
		}
		// Επαναφέρετε την απόσταση μεταξύ των διαχωρισμένων παραγράφων σε πίνακες, καθώς η επιπλέον απόσταση μπορεί να τις κάνει να φαίνονται διαφορετικές.
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
	// Προσθέστε επίσης νέα αρίθμηση σελίδων για το κυρίως μέρος της ενότητας.
	pageNumberFinder.addPageNumbersForNode(section.getBody(), pageNumberFinder.getPage(section),
		pageNumberFinder.getPageEnd(section));
	return Δράση Επισκεπτών.CONTINUE;
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
	// Ένας κόμβος μπορεί να εκτείνεται σε πολλές σελίδες, επομένως επιστρέφεται μια λίστα με διαχωρισμένες θέσεις.
	// Ο διαιρεμένος κόμβος είναι ο πρώτος κόμβος στην επόμενη σελίδα.
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
		// Εάν η σελίδα του θυγατρικού κόμβου έχει αλλάξει, τότε αυτή είναι η θέση διαίρεσης.
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
	// Διαχωρίστε τα σύνθετα στοιχεία προς τα πίσω, έτσι ώστε οι κλωνοποιημένοι κόμβοι να εισάγονται με τη σωστή σειρά.
	Collections.reverse(splitList);
	return splitList;
}
private CompositeNode splitCompositeAtNode(CompositeNode baseNode, Node targetNode) throws Exception {
	CompositeNode cloneNode = (CompositeNode) baseNode.deepClone(false);
	Node node = targetNode;
	int currentPageNum = pageNumberFinder.getPage(baseNode);
	// Μετακινήστε όλους τους κόμβους που βρίσκονται στην επόμενη σελίδα στον αντιγραμμένο κόμβο. Χειριστείτε τους κόμβους της γραμμής ξεχωριστά.
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
		// Αν έχουμε να κάνουμε με μια γραμμή, πρέπει να προσθέσουμε εικονικά κελιά για την κλωνοποιημένη γραμμή.
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
	// Εισαγάγετε τον διαιρεμένο κόμβο μετά τον αρχικό.
	baseNode.getParentNode().insertAfter(cloneNode, baseNode);
	// Ενημερώστε τους νέους αριθμούς σελίδων του βασικού κόμβου και του κλωνοποιημένου κόμβου, συμπεριλαμβανομένων των απογόνων του.
	// Αυτή θα είναι μόνο μία σελίδα, καθώς το κλωνοποιημένο σύνθετο υλικό χωρίζεται σε μία σελίδα.
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

Τώρα μάθατε πώς να χωρίσετε ένα έγγραφο σε ξεχωριστές σελίδες χρησιμοποιώντας το Aspose.Words για Java. Αυτός ο οδηγός παρέχει ένα ολοκληρωμένο βήμα προς βήμα σεμινάριο με παραδείγματα πηγαίου κώδικα. Μπορείτε να προσαρμόσετε και να επεκτείνετε περαιτέρω αυτόν τον κώδικα ώστε να ανταποκρίνεται στις συγκεκριμένες απαιτήσεις σας κατά την εργασία με έγγραφα.
Σίγουρα! Ας προσθέσουμε μια ενότητα με Συχνές Ερωτήσεις στον οδηγό μας σχετικά με τη διαίρεση εγγράφων σε σελίδες χρησιμοποιώντας το Aspose.Words για Java.

## Συχνές ερωτήσεις

### Πώς μπορώ να προσθέσω το Aspose.Words για Java στο έργο μου;

Για να προσθέσετε το Aspose.Words για Java στο έργο σας, ακολουθήστε τα εξής βήματα:

1. Κατεβάστε τη βιβλιοθήκη Aspose.Words για Java από [εδώ](https://releases.aspose.com/words/java/).
2. Προσθέστε το ληφθέν αρχείο JAR στη διαδρομή κλάσεων του έργου σας.
3. Τώρα μπορείτε να ξεκινήσετε να χρησιμοποιείτε το Aspose.Words για Java στο έργο σας.

### Μπορώ να διαχωρίσω έγγραφα σε άλλες μορφές, όπως PDF ή DOCX;

Όχι, αυτός ο οδηγός καλύπτει συγκεκριμένα τον διαχωρισμό εγγράφων σε μορφή DOC χρησιμοποιώντας το Aspose.Words για Java. Εάν χρειάζεται να διαχωρίσετε έγγραφα σε άλλες μορφές, ίσως χρειαστεί να εξερευνήσετε άλλες βιβλιοθήκες ή εργαλεία που υποστηρίζουν αυτές τις μορφές.

### Είναι το Aspose.Words για Java μια δωρεάν βιβλιοθήκη;

Όχι, το Aspose.Words για Java δεν είναι μια δωρεάν βιβλιοθήκη. Είναι ένα εμπορικό προϊόν με χρέωση αδειοδότησης. Μπορείτε να επισκεφθείτε το [Σελίδα τιμολόγησης Aspose.Words για Java](https://purchase.aspose.com/words/java) για περισσότερες πληροφορίες σχετικά με τις άδειες χρήσης και τις λεπτομέρειες τιμολόγησης.

### Μπορώ να χωρίσω έγγραφα σε προσαρμοσμένα μεγέθη σελίδων και μορφές;

Ναι, μπορείτε να προσαρμόσετε τα μεγέθη και τις μορφές σελίδων των διαιρεμένων εγγράφων τροποποιώντας τις ιδιότητες διαμόρφωσης σελίδας στο Aspose.Words για Java. Ανατρέξτε στην τεκμηρίωση του Aspose.Words για λεπτομέρειες σχετικά με τον τρόπο προσαρμογής των ρυθμίσεων σελίδας σύμφωνα με τις απαιτήσεις σας.

### Υπάρχουν περιορισμοί στον αριθμό των σελίδων που μπορούν να διαχωριστούν;

Το Aspose.Words για Java δεν επιβάλλει συγκεκριμένους περιορισμούς στον αριθμό των σελίδων που μπορείτε να διαχωρίσετε. Ωστόσο, λάβετε υπόψη ότι τα πολύ μεγάλα έγγραφα ενδέχεται να απαιτούν περισσότερη μνήμη και χρόνο επεξεργασίας. Να είστε προσεκτικοί με τους πόρους του συστήματος όταν εργάζεστε με μεγάλα έγγραφα.

### Πώς μπορώ να χειριστώ κεφαλίδες και υποσέλιδα κατά τον διαχωρισμό εγγράφων;

Οι κεφαλίδες και τα υποσέλιδα μπορούν να αντιμετωπιστούν κατά τον διαχωρισμό εγγράφων χρησιμοποιώντας τη βιβλιοθήκη Aspose.Words για Java. Μπορείτε να αντιγράψετε το περιεχόμενο της κεφαλίδας και του υποσέλιδου από το αρχικό έγγραφο στα διαιρεμένα έγγραφα, διασφαλίζοντας ότι διατηρούνται σωστά. Ενδέχεται να χρειαστεί να προσαρμόσετε αυτήν τη διαδικασία με βάση τις συγκεκριμένες απαιτήσεις σας για την κεφαλίδα και το υποσέλιδο.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}