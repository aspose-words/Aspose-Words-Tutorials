---
"description": "Μάθετε πώς να εκτυπώνετε έγγραφα χρησιμοποιώντας το Aspose.Words για Java. Οδηγός βήμα προς βήμα για απρόσκοπτη εκτύπωση στις εφαρμογές Java που διαθέτετε."
"linktitle": "Εκτύπωση εγγράφων"
"second_title": "API επεξεργασίας εγγράφων Java Aspose.Words"
"title": "Εκτύπωση εγγράφων σε Aspose.Words για Java"
"url": "/el/java/printing-documents/printing-documents/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Εκτύπωση εγγράφων σε Aspose.Words για Java


Αν θέλετε να εκτυπώσετε έγγραφα χρησιμοποιώντας το Aspose.Words για Java, βρίσκεστε στο σωστό μέρος. Σε αυτόν τον οδηγό βήμα προς βήμα, θα σας καθοδηγήσουμε στη διαδικασία εκτύπωσης εγγράφων με το Aspose.Words για Java χρησιμοποιώντας τον παρεχόμενο πηγαίο κώδικα.

## Εισαγωγή

Η εκτύπωση εγγράφων είναι μια συνηθισμένη εργασία σε πολλές εφαρμογές. Το Aspose.Words για Java παρέχει ένα ισχυρό API για εργασία με έγγραφα του Word, συμπεριλαμβανομένης της δυνατότητας εκτύπωσής τους. Σε αυτό το σεμινάριο, θα σας καθοδηγήσουμε βήμα προς βήμα στη διαδικασία εκτύπωσης ενός εγγράφου του Word.

## Ρύθμιση του Περιβάλλοντός σας

Πριν εμβαθύνουμε στον κώδικα, βεβαιωθείτε ότι έχετε τις ακόλουθες προϋποθέσεις:

- Εγκατεστημένο το Java Development Kit (JDK)
- Λήψη και προσθήκη της βιβλιοθήκης Aspose.Words για Java στο έργο σας

## Φόρτωση του εγγράφου

Για να ξεκινήσετε, θα χρειαστεί να φορτώσετε το έγγραφο του Word που θέλετε να εκτυπώσετε. Αντικατάσταση `"Your Document Directory"` με τη διαδρομή προς το έγγραφό σας και `"Your Output Directory"` με τον επιθυμητό κατάλογο εξόδου.

```java
string dataDir = "Your Document Directory";
string outPath = "Your Output Directory";
Document doc = new Document(dataDir + "Rendering.docx");
```

## Δημιουργία εργασίας εκτύπωσης

Στη συνέχεια, θα δημιουργήσουμε μια εργασία εκτύπωσης για να εκτυπώσουμε το φορτωμένο έγγραφό μας. Το παρακάτω απόσπασμα κώδικα αρχικοποιεί μια εργασία εκτύπωσης και ορίζει τις επιθυμητές ρυθμίσεις εκτυπωτή.

```java
// Δημιουργήστε μια εργασία εκτύπωσης για να εκτυπώσετε το έγγραφό μας.
PrinterJob pj = PrinterJob.getPrinterJob();
// Αρχικοποιήστε ένα σύνολο χαρακτηριστικών με τον αριθμό των σελίδων στο έγγραφο.
PrintRequestAttributeSet attributes = new HashPrintRequestAttributeSet();
attributes.add(new PageRanges(1, doc.getPageCount()));
// Μεταβιβάστε τις ρυθμίσεις του εκτυπωτή μαζί με τις άλλες παραμέτρους στο έγγραφο εκτύπωσης.
MultipagePrintDocument awPrintDoc = new MultipagePrintDocument(doc, 4, true, attributes);
```

## Εκτύπωση του εγγράφου

Τώρα που έχουμε ρυθμίσει την εργασία εκτύπωσης, ήρθε η ώρα να εκτυπώσουμε το έγγραφο. Το ακόλουθο απόσπασμα κώδικα συσχετίζει το έγγραφο με την εργασία εκτύπωσης και ξεκινά τη διαδικασία εκτύπωσης.

```java
// Μεταβιβάστε το έγγραφο που θα εκτυπωθεί χρησιμοποιώντας την εργασία εκτύπωσης.
pj.setPrintable(awPrintDoc);
pj.print();
```
## Πλήρης Πηγαίος Κώδικας
```java
string dataDir = "Your Document Directory";
Document doc = new Document(dataDir + "Rendering.docx");
// Δημιουργήστε μια εργασία εκτύπωσης για να εκτυπώσετε το έγγραφό μας.
PrinterJob pj = PrinterJob.getPrinterJob();
// Αρχικοποιήστε ένα σύνολο χαρακτηριστικών με τον αριθμό των σελίδων στο έγγραφο.
PrintRequestAttributeSet attributes = new HashPrintRequestAttributeSet();
attributes.add(new PageRanges(1, doc.getPageCount()));
// Μεταβιβάστε τις ρυθμίσεις του εκτυπωτή μαζί με τις άλλες παραμέτρους στο έγγραφο εκτύπωσης.
MultipagePrintDocument awPrintDoc = new MultipagePrintDocument(doc, 4, true, attributes);
// Μεταβιβάστε το έγγραφο που θα εκτυπωθεί χρησιμοποιώντας την εργασία εκτύπωσης.
pj.setPrintable(awPrintDoc);
pj.print();
```
Πηγαίος κώδικας του MultipagePrintDocument
```java
class MultipagePrintDocument implements Printable
{
    private final Document mDocument;
    private final int mPagesPerSheet;
    private final boolean mPrintPageBorders;
    private final AttributeSet mAttributeSet;
    /// <σύνοψη>
    /// Ο κατασκευαστής της προσαρμοσμένης κλάσης PrintDocument.
    /// </σύνοψη> 
    public MultipagePrintDocument(Document document, int pagesPerSheet, boolean printPageBorders,
                                  AttributeSet attributes) {
        if (document == null)
            throw new IllegalArgumentException("document");
        mDocument = document;
        mPagesPerSheet = pagesPerSheet;
        mPrintPageBorders = printPageBorders;
        mAttributeSet = attributes;
    }
    public int print(Graphics g, PageFormat pf, int page) {
        // Οι δείκτες έναρξης και λήξης σελίδας όπως ορίζονται στο σύνολο χαρακτηριστικών.
        int[][] pageRanges = ((PageRanges) mAttributeSet.get(PageRanges.class)).getMembers();
        int fromPage = pageRanges[0][0] - 1;
        int toPage = pageRanges[0][1] - 1;
        Dimension thumbCount = getThumbCount(mPagesPerSheet, pf);
        // Υπολογίστε τον δείκτη σελίδας που θα αποδοθεί στη συνέχεια.
        int pagesOnCurrentSheet = (int) (page * (thumbCount.getWidth() * thumbCount.getHeight()));
        // Εάν ο δείκτης σελίδας είναι μεγαλύτερος από το συνολικό εύρος σελίδων, τότε δεν υπάρχει τίποτα
        // περισσότερα για απόδοση.
        if (pagesOnCurrentSheet > (toPage - fromPage))
            return Printable.NO_SUCH_PAGE;
        // Υπολογίστε το μέγεθος κάθε placeholder μικρογραφίας σε σημεία.
        Point2D.Float thumbSize = new Point2D.Float((float) (pf.getImageableWidth() / thumbCount.getWidth()),
                (float) (pf.getImageableHeight() / thumbCount.getHeight()));
        // Υπολογίστε τον αριθμό της πρώτης σελίδας που θα εκτυπωθεί σε αυτό το φύλλο χαρτιού.
        int startPage = pagesOnCurrentSheet + fromPage;
        // Επιλέξτε τον αριθμό της τελευταίας σελίδας που θα εκτυπωθεί σε αυτό το φύλλο χαρτιού.
        int pageTo = Math.max(startPage + mPagesPerSheet - 1, toPage);
        // Επανάληψη των επιλεγμένων σελίδων από την αποθηκευμένη τρέχουσα σελίδα έως τον υπολογισμό
        // τελευταία σελίδα.
        for (int pageIndex = startPage; pageIndex <= pageTo; pageIndex++) {
            // Υπολογίστε τους δείκτες στηλών και γραμμών.
            int rowIdx = (int) Math.floor((pageIndex - startPage) / thumbCount.getWidth());
            int columnIdx = (int) Math.floor((pageIndex - startPage) % thumbCount.getWidth());
            // Ορίστε τη θέση της μικρογραφίας σε συντεταγμένες κόσμου (σημεία σε αυτήν την περίπτωση).
            float thumbLeft = columnIdx * thumbSize.x;
            float thumbTop = rowIdx * thumbSize.y;
            try {
                // Υπολογίστε την αριστερή και την πάνω θέση εκκίνησης.
                int leftPos = (int) (thumbLeft + pf.getImageableX());
                int topPos = (int) (thumbTop + pf.getImageableY());
                // Απόδοση της σελίδας του εγγράφου στο αντικείμενο Graphics χρησιμοποιώντας υπολογισμένες συντεταγμένες
                // και μέγεθος κράτησης θέσης μικρογραφίας.
                // Η χρήσιμη τιμή επιστροφής είναι η κλίμακα στην οποία αποδόθηκε η σελίδα.
                float scale = mDocument.renderToSize(pageIndex, (Graphics2D) g, leftPos, topPos, (int) thumbSize.x,
                        (int) thumbSize.y);
                // Σχεδιάστε τα περιγράμματα της σελίδας (η μικρογραφία της σελίδας μπορεί να είναι μικρότερη από τη μικρογραφία)
                // μέγεθος κράτησης θέσης).
                if (mPrintPageBorders) {
                    // Αποκτήστε το πραγματικό 100% μέγεθος της σελίδας σε πόντους.
                    Point2D.Float pageSize = mDocument.getPageInfo(pageIndex).getSizeInPoints();
                    // Σχεδιάστε το περίγραμμα γύρω από την κλιμακωμένη σελίδα χρησιμοποιώντας τον γνωστό συντελεστή κλίμακας.
                    g.setColor(Color.black);
                    g.drawRect(leftPos, topPos, (int) (pageSize.x * scale), (int) (pageSize.y * scale));
                    // Σχεδιάστε το περίγραμμα γύρω από το σύμβολο κράτησης θέσης μικρογραφίας.
                    g.setColor(Color.red);
                    g.drawRect(leftPos, topPos, (int) thumbSize.x, (int) thumbSize.y);
                }
            } catch (Exception e) {
                // Εάν προκύψουν σφάλματα κατά την απόδοση, μην κάνετε τίποτα.
                // Αυτό θα σχεδιάσει μια κενή σελίδα εάν υπάρχουν σφάλματα κατά την απόδοση.
            }
        }
        return Printable.PAGE_EXISTS;
    }
    private Dimension getThumbCount(int pagesPerSheet, PageFormat pf) {
        Dimension size;
        // Ορίστε τον αριθμό των στηλών και των γραμμών στο φύλλο για το
        // Χαρτί με προσανατολισμό στο τοπίο.
        switch (pagesPerSheet) {
            case 16:
                size = new Dimension(4, 4);
                break;
            case 9:
                size = new Dimension(3, 3);
                break;
            case 8:
                size = new Dimension(4, 2);
                break;
            case 6:
                size = new Dimension(3, 2);
                break;
            case 4:
                size = new Dimension(2, 2);
                break;
            case 2:
                size = new Dimension(2, 1);
                break;
            default:
                size = new Dimension(1, 1);
                break;
        }
        // Αλλάξτε το πλάτος και το ύψος εάν το χαρτί έχει κατακόρυφο προσανατολισμό.
        if ((pf.getWidth() - pf.getImageableX()) < (pf.getHeight() - pf.getImageableY()))
            return new Dimension((int) size.getHeight(), (int) size.getWidth());
        return size;
	}
}
```

## Σύναψη

Συγχαρητήρια! Εκτυπώσατε με επιτυχία ένα έγγραφο του Word χρησιμοποιώντας το Aspose.Words για Java. Αυτός ο οδηγός βήμα προς βήμα θα σας βοηθήσει να ενσωματώσετε απρόσκοπτα την εκτύπωση εγγράφων στις εφαρμογές Java που χρησιμοποιείτε.

## Συχνές ερωτήσεις

### Ε1: Μπορώ να εκτυπώσω συγκεκριμένες σελίδες ενός εγγράφου χρησιμοποιώντας το Aspose.Words για Java;

Ναι, μπορείτε να καθορίσετε το εύρος σελίδων κατά την εκτύπωση ενός εγγράφου. Στο παράδειγμα κώδικα, χρησιμοποιήσαμε `attributes.add(new PageRanges(1, doc.getPageCount()))` για να εκτυπώσετε όλες τις σελίδες. Μπορείτε να προσαρμόσετε το εύρος σελίδων όπως απαιτείται.

### Ε2: Είναι το Aspose.Words για Java κατάλληλο για μαζική εκτύπωση;

Απολύτως! Το Aspose.Words για Java είναι ιδανικό για εργασίες μαζικής εκτύπωσης. Μπορείτε να περιηγηθείτε σε μια λίστα εγγράφων και να τα εκτυπώσετε ένα προς ένα χρησιμοποιώντας παρόμοιο κώδικα.

### Ε3: Πώς μπορώ να χειριστώ σφάλματα ή εξαιρέσεις εκτύπωσης;

Θα πρέπει να χειριστείτε τυχόν πιθανές εξαιρέσεις που ενδέχεται να προκύψουν κατά τη διαδικασία εκτύπωσης. Ανατρέξτε στην τεκμηρίωση του Aspose.Words για Java για πληροφορίες σχετικά με τον χειρισμό εξαιρέσεων.

### Ε4: Μπορώ να προσαρμόσω περαιτέρω τις ρυθμίσεις εκτύπωσης;

Ναι, μπορείτε να προσαρμόσετε τις ρυθμίσεις εκτύπωσης ώστε να ανταποκρίνονται στις συγκεκριμένες απαιτήσεις σας. Εξερευνήστε την τεκμηρίωση του Aspose.Words για Java για να μάθετε περισσότερα σχετικά με τις διαθέσιμες επιλογές εκτύπωσης.

### Ε5: Πού μπορώ να βρω περισσότερη βοήθεια και υποστήριξη για το Aspose.Words για Java;

Για επιπλέον υποστήριξη και βοήθεια, μπορείτε να επισκεφθείτε την [Aspose.Words για φόρουμ Java](https://forum.aspose.com/).

---

Τώρα που μάθατε με επιτυχία πώς να εκτυπώνετε έγγραφα χρησιμοποιώντας το Aspose.Words για Java, μπορείτε να ξεκινήσετε να εφαρμόζετε αυτήν τη λειτουργικότητα στις εφαρμογές Java που χρησιμοποιείτε. Καλή κωδικοποίηση!


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}