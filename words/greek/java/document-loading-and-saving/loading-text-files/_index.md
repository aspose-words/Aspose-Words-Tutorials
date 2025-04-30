---
"description": "Ξεκλειδώστε τη δύναμη του Aspose.Words για Java. Μάθετε να φορτώνετε έγγραφα κειμένου, να διαχειρίζεστε λίστες, να χειρίζεστε κενά και να ελέγχετε την κατεύθυνση κειμένου."
"linktitle": "Φόρτωση αρχείων κειμένου με"
"second_title": "API επεξεργασίας εγγράφων Java Aspose.Words"
"title": "Φόρτωση αρχείων κειμένου με Aspose.Words για Java"
"url": "/el/java/document-loading-and-saving/loading-text-files/"
"weight": 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Φόρτωση αρχείων κειμένου με Aspose.Words για Java


## Εισαγωγή στη φόρτωση αρχείων κειμένου με το Aspose.Words για Java

Σε αυτόν τον οδηγό, θα εξερευνήσουμε πώς να φορτώνουμε αρχεία κειμένου χρησιμοποιώντας το Aspose.Words για Java και να τα χειριζόμαστε ως έγγραφα Word. Θα καλύψουμε διάφορες πτυχές, όπως η ανίχνευση λιστών, ο χειρισμός κενών και ο έλεγχος της κατεύθυνσης του κειμένου.

## Βήμα 1: Εντοπισμός λιστών

Για να φορτώσετε ένα έγγραφο κειμένου και να εντοπίσετε λίστες, μπορείτε να ακολουθήσετε τα εξής βήματα:

```java
// Δημιουργήστε ένα έγγραφο απλού κειμένου με τη μορφή συμβολοσειράς με μέρη που μπορούν να ερμηνευτούν ως λίστες.
// Κατά τη φόρτωση, οι τρεις πρώτες λίστες θα ανιχνεύονται πάντα από το Aspose.Words,
// και τα αντικείμενα λίστας θα δημιουργηθούν για αυτά μετά τη φόρτωση.
final String TEXT_DOC = "Full stop delimiters:\n" +
        "1. First list item 1\n" +
        "2. First list item 2\n" +
        "3. First list item 3\n\n" +
        "Right bracket delimiters:\n" +
        "1) Second list item 1\n" +
        "2) Second list item 2\n" +
        "3) Second list item 3\n\n" +
        "Bullet delimiters:\n" +
        "• Third list item 1\n" +
        "• Third list item 2\n" +
        "• Third list item 3\n\n" +
        "Whitespace delimiters:\n" +
        "1 Fourth list item 1\n" +
        "2 Fourth list item 2\n" +
        "3 Fourth list item 3";
// Η τέταρτη λίστα, με κενό διάστημα μεταξύ του αριθμού της λίστας και των περιεχομένων του στοιχείου της λίστας,
// θα ανιχνευθεί μόνο ως λίστα εάν η παράμετρος "DetectNumberingWithWhitespaces" σε ένα αντικείμενο LoadOptions έχει οριστεί σε true,
// για να αποφευχθεί η εσφαλμένη ανίχνευση παραγράφων που ξεκινούν με αριθμούς ως λίστες.
TxtLoadOptions loadOptions = new TxtLoadOptions();
{
    loadOptions.setDetectNumberingWithWhitespaces(true);
}
// Φορτώστε το έγγραφο εφαρμόζοντας την παράμετρο LoadOptions και επαληθεύστε το αποτέλεσμα.
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

Αυτός ο κώδικας δείχνει πώς να φορτώσετε ένα έγγραφο κειμένου με διάφορες μορφές λίστας και να χρησιμοποιήσετε το `DetectNumberingWithWhitespaces` επιλογή για σωστή ανίχνευση λιστών.

## Βήμα 2: Χειρισμός επιλογών κενών χώρων

Για να ελέγξετε τα κενά στην αρχή και στο τέλος κατά τη φόρτωση ενός εγγράφου κειμένου, μπορείτε να χρησιμοποιήσετε τον ακόλουθο κώδικα:

```java
@Test
public void handleSpacesOptions() throws Exception {
    final String TEXT_DOC = "      Line 1 \n" +
            "    Line 2   \n" +
            " Line 3       ";
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    {
        loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
        loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);
    }
    Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
    doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.HandleSpacesOptions.docx");
}
```

Σε αυτό το παράδειγμα, φορτώνουμε ένα έγγραφο κειμένου και περικόπτουμε τα κενά στην αρχή και στο τέλος χρησιμοποιώντας `TxtLeadingSpacesOptions.TRIM` και `TxtTrailingSpacesOptions.TRIM`.

## Βήμα 3: Έλεγχος κατεύθυνσης κειμένου

Για να καθορίσετε την κατεύθυνση του κειμένου κατά τη φόρτωση ενός εγγράφου κειμένου, μπορείτε να χρησιμοποιήσετε τον ακόλουθο κώδικα:

```java
@Test
public void documentTextDirection() throws Exception {
    TxtLoadOptions loadOptions = new TxtLoadOptions();
    {
        loadOptions.setDocumentDirection(DocumentDirection.AUTO);
    }
    Document doc = new Document("Your Directory Path" + "Hebrew text.txt", loadOptions);
    Paragraph paragraph = doc.getFirstSection().getBody().getFirstParagraph();
    System.out.println(paragraph.getParagraphFormat().getBidi());
    doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
}
```

Αυτός ο κώδικας ορίζει την κατεύθυνση του εγγράφου σε αυτόματη ανίχνευση (`DocumentDirection.AUTO`) και φορτώνει ένα έγγραφο κειμένου με εβραϊκό κείμενο. Μπορείτε να προσαρμόσετε την κατεύθυνση του εγγράφου όπως απαιτείται.

## Πλήρης πηγαίος κώδικας για φόρτωση αρχείων κειμένου με Aspose.Words για Java

```java
public void detectNumberingWithWhitespaces() throws Exception {
	// Δημιουργήστε ένα έγγραφο απλού κειμένου με τη μορφή συμβολοσειράς με μέρη που μπορούν να ερμηνευτούν ως λίστες.
	// Κατά τη φόρτωση, οι τρεις πρώτες λίστες θα ανιχνεύονται πάντα από το Aspose.Words,
	// και τα αντικείμενα λίστας θα δημιουργηθούν για αυτά μετά τη φόρτωση.
	final String TEXT_DOC = "Full stop delimiters:\n" +
			"1. First list item 1\n" +
			"2. First list item 2\n" +
			"3. First list item 3\n\n" +
			"Right bracket delimiters:\n" +
			"1) Second list item 1\n" +
			"2) Second list item 2\n" +
			"3) Second list item 3\n\n" +
			"Bullet delimiters:\n" +
			"• Third list item 1\n" +
			"• Third list item 2\n" +
			"• Third list item 3\n\n" +
			"Whitespace delimiters:\n" +
			"1 Fourth list item 1\n" +
			"2 Fourth list item 2\n" +
			"3 Fourth list item 3";
	// Η τέταρτη λίστα, με κενό διάστημα μεταξύ του αριθμού της λίστας και των περιεχομένων του στοιχείου της λίστας,
	// θα ανιχνευθεί μόνο ως λίστα εάν η παράμετρος "DetectNumberingWithWhitespaces" σε ένα αντικείμενο LoadOptions έχει οριστεί σε true,
	// για να αποφευχθεί η εσφαλμένη ανίχνευση παραγράφων που ξεκινούν με αριθμούς ως λίστες.
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDetectNumberingWithWhitespaces(true);
	}
	// Φορτώστε το έγγραφο εφαρμόζοντας την παράμετρο LoadOptions και επαληθεύστε το αποτέλεσμα.
	Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
}
@Test
public void handleSpacesOptions() throws Exception {
	final String TEXT_DOC = "      Line 1 \n" +
			"    Line 2   \n" +
			" Line 3       ";
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setLeadingSpacesOptions(TxtLeadingSpacesOptions.TRIM);
		loadOptions.setTrailingSpacesOptions(TxtTrailingSpacesOptions.TRIM);
	}
	Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.HandleSpacesOptions.docx");
}
@Test
public void documentTextDirection() throws Exception {
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDocumentDirection(DocumentDirection.AUTO);
	}
	Document doc = new Document("Your Directory Path" + "Hebrew text.txt", loadOptions);
	Paragraph paragraph = doc.getFirstSection().getBody().getFirstParagraph();
	System.out.println(paragraph.getParagraphFormat().getBidi());
	doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DocumentTextDirection.docx");
	}
```

## Σύναψη

Σε αυτόν τον οδηγό, εξετάσαμε πώς να φορτώνουμε αρχεία κειμένου χρησιμοποιώντας το Aspose.Words για Java, να εντοπίζουμε λίστες, να χειριζόμαστε κενά και να ελέγχουμε την κατεύθυνση του κειμένου. Αυτές οι τεχνικές σάς επιτρέπουν να χειρίζεστε αποτελεσματικά έγγραφα κειμένου στις εφαρμογές Java που χρησιμοποιείτε.

## Συχνές ερωτήσεις

### Τι είναι το Aspose.Words για Java;

Το Aspose.Words για Java είναι μια ισχυρή βιβλιοθήκη επεξεργασίας εγγράφων που επιτρέπει στους προγραμματιστές να δημιουργούν, να χειρίζονται και να μετατρέπουν έγγραφα Word μέσω προγραμματισμού σε εφαρμογές Java. Παρέχει ένα ευρύ φάσμα λειτουργιών για εργασία με κείμενο, πίνακες, εικόνες και άλλα στοιχεία εγγράφων.

### Πώς μπορώ να ξεκινήσω με το Aspose.Words για Java;

Για να ξεκινήσετε με το Aspose.Words για Java, ακολουθήστε τα εξής βήματα:
1. Κατεβάστε και εγκαταστήστε τη βιβλιοθήκη Aspose.Words για Java.
2. Ανατρέξτε στην τεκμηρίωση στη διεύθυνση [Aspose.Words για αναφορά API Java](https://reference.aspose.com/words/java/) για λεπτομερείς πληροφορίες και παραδείγματα.
3. Εξερευνήστε το δείγμα κώδικα και τα εκπαιδευτικά βίντεο για να μάθετε πώς να χρησιμοποιείτε αποτελεσματικά τη βιβλιοθήκη.

### Πώς μπορώ να φορτώσω ένα έγγραφο κειμένου χρησιμοποιώντας το Aspose.Words για Java;

Για να φορτώσετε ένα έγγραφο κειμένου χρησιμοποιώντας το Aspose.Words για Java, μπορείτε να χρησιμοποιήσετε το `TxtLoadOptions` τάξη και το `Document` κλάση. Βεβαιωθείτε ότι έχετε καθορίσει τις κατάλληλες επιλογές για τον χειρισμό των κενών και την κατεύθυνση του κειμένου, όπως απαιτείται. Ανατρέξτε στον οδηγό βήμα προς βήμα σε αυτό το άρθρο για ένα λεπτομερές παράδειγμα.

### Μπορώ να μετατρέψω ένα φορτωμένο έγγραφο κειμένου σε άλλες μορφές;

Ναι, το Aspose.Words για Java σάς επιτρέπει να μετατρέψετε ένα φορτωμένο έγγραφο κειμένου σε διάφορες μορφές, όπως DOCX, PDF και άλλες. Μπορείτε να χρησιμοποιήσετε το `Document` κλάση για την εκτέλεση μετατροπών. Ελέγξτε την τεκμηρίωση για συγκεκριμένα παραδείγματα μετατροπών.

### Πώς μπορώ να χειριστώ τα κενά σε έγγραφα κειμένου που έχουν φορτωθεί;

Μπορείτε να ελέγξετε τον τρόπο χειρισμού των κενών στην αρχή και στο τέλος σε έγγραφα κειμένου που έχουν φορτωθεί χρησιμοποιώντας `TxtLoadOptions`Επιλογές όπως `TxtLeadingSpacesOptions` και `TxtTrailingSpacesOptions` σας επιτρέπουν να περικόψετε ή να διατηρήσετε κενά όπως απαιτείται. Ανατρέξτε στην ενότητα "Επιλογές χειρισμού χώρων" σε αυτόν τον οδηγό για ένα παράδειγμα.

### Ποια είναι η σημασία της κατεύθυνσης κειμένου στο Aspose.Words για Java;

Η κατεύθυνση του κειμένου είναι απαραίτητη για έγγραφα που περιέχουν μικτές γραφές ή γλώσσες, όπως τα Εβραϊκά ή τα Αραβικά. Το Aspose.Words για Java παρέχει επιλογές για τον καθορισμό της κατεύθυνσης του κειμένου, διασφαλίζοντας την σωστή απόδοση και μορφοποίηση του κειμένου σε αυτές τις γλώσσες. Η ενότητα "Έλεγχος κατεύθυνσης κειμένου" σε αυτόν τον οδηγό δείχνει πώς να ορίσετε την κατεύθυνση του κειμένου.

### Πού μπορώ να βρω περισσότερους πόρους και υποστήριξη για το Aspose.Words για Java;

Για πρόσθετους πόρους, τεκμηρίωση και υποστήριξη, επισκεφθείτε τη διεύθυνση [Aspose.Words για τεκμηρίωση Java](https://reference.aspose.com/words/java/)Μπορείτε επίσης να συμμετάσχετε στα φόρουμ της κοινότητας Aspose.Words ή να επικοινωνήσετε με την υποστήριξη της Aspose για βοήθεια σχετικά με συγκεκριμένα ζητήματα ή ερωτήσεις.

### Είναι το Aspose.Words για Java κατάλληλο για εμπορικά έργα;

Ναι, το Aspose.Words για Java είναι κατάλληλο τόσο για προσωπικά όσο και για εμπορικά έργα. Προσφέρει επιλογές αδειοδότησης για να καλύψει διάφορα σενάρια χρήσης. Βεβαιωθείτε ότι έχετε ελέγξει τους όρους και τις τιμές αδειοδότησης στον ιστότοπο της Aspose για να επιλέξετε την κατάλληλη άδεια χρήσης για το έργο σας.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}