---
title: Φόρτωση αρχείων κειμένου με Aspose.Words για Java
linktitle: Φόρτωση αρχείων κειμένου με
second_title: Aspose.Words Java Document Processing API
description: Ξεκλειδώστε το Power of Aspose.Words για Java. Μάθετε να φορτώνετε έγγραφα κειμένου, να διαχειρίζεστε λίστες, να χειρίζεστε κενά και να ελέγχετε την κατεύθυνση κειμένου.
weight: 13
url: /el/java/document-loading-and-saving/loading-text-files/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Φόρτωση αρχείων κειμένου με Aspose.Words για Java


## Εισαγωγή στη φόρτωση αρχείων κειμένου με το Aspose.Words για Java

Σε αυτόν τον οδηγό, θα εξερευνήσουμε πώς να φορτώνουμε αρχεία κειμένου χρησιμοποιώντας το Aspose.Words για Java και να τα χειριζόμαστε ως έγγραφα του Word. Θα καλύψουμε διάφορες πτυχές, όπως τον εντοπισμό λιστών, τον χειρισμό των χώρων και τον έλεγχο της κατεύθυνσης του κειμένου.

## Βήμα 1: Ανίχνευση λιστών

Για να φορτώσετε ένα έγγραφο κειμένου και να εντοπίσετε λίστες, μπορείτε να ακολουθήσετε τα εξής βήματα:

```java
// Δημιουργήστε ένα έγγραφο απλού κειμένου με τη μορφή συμβολοσειράς με τμήματα που μπορούν να ερμηνευτούν ως λίστες.
// Κατά τη φόρτωση, οι τρεις πρώτες λίστες θα εντοπίζονται πάντα από το Aspose.Words,
// και τα αντικείμενα λίστας θα δημιουργηθούν για αυτούς μετά τη φόρτωση.
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
//Η τέταρτη λίστα, με κενό διάστημα μεταξύ του αριθμού λίστας και των περιεχομένων του στοιχείου λίστας,
// θα εντοπιστεί ως λίστα μόνο εάν το "DetectNumberingWithWhitespaces" σε ένα αντικείμενο LoadOptions έχει οριστεί σε true,
// για να αποφευχθεί η εσφαλμένη ανίχνευση παραγράφων που ξεκινούν με αριθμούς ως λίστες.
TxtLoadOptions loadOptions = new TxtLoadOptions();
{
    loadOptions.setDetectNumberingWithWhitespaces(true);
}
// Φορτώστε το έγγραφο ενώ εφαρμόζετε το LoadOptions ως παράμετρο και επαληθεύστε το αποτέλεσμα.
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

 Αυτός ο κώδικας δείχνει πώς να φορτώσετε ένα έγγραφο κειμένου με διάφορες μορφές λίστας και να χρησιμοποιήσετε το`DetectNumberingWithWhitespaces` επιλογή για τον σωστό εντοπισμό λιστών.

## Βήμα 2: Χειρισμός επιλογών χώρων

Για να ελέγξετε τα κύρια και τα τελικά κενά κατά τη φόρτωση ενός εγγράφου κειμένου, μπορείτε να χρησιμοποιήσετε τον ακόλουθο κώδικα:

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

 Σε αυτό το παράδειγμα, φορτώνουμε ένα έγγραφο κειμένου και περικόπτουμε τους κενούς και τους τελικούς χώρους χρησιμοποιώντας`TxtLeadingSpacesOptions.TRIM` και`TxtTrailingSpacesOptions.TRIM`.

## Βήμα 3: Έλεγχος κατεύθυνσης κειμένου

Για να καθορίσετε την κατεύθυνση κειμένου κατά τη φόρτωση ενός εγγράφου κειμένου, μπορείτε να χρησιμοποιήσετε τον ακόλουθο κώδικα:

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

Αυτός ο κωδικός ορίζει την κατεύθυνση του εγγράφου σε αυτόματη ανίχνευση (`DocumentDirection.AUTO`και φορτώνει ένα έγγραφο κειμένου με εβραϊκό κείμενο. Μπορείτε να προσαρμόσετε την κατεύθυνση του εγγράφου όπως απαιτείται.

## Ολοκληρώστε τον πηγαίο κώδικα για τη φόρτωση αρχείων κειμένου με το Aspose.Words για Java

```java
public void detectNumberingWithWhitespaces() throws Exception {
	// Δημιουργήστε ένα έγγραφο απλού κειμένου με τη μορφή συμβολοσειράς με τμήματα που μπορούν να ερμηνευτούν ως λίστες.
	// Κατά τη φόρτωση, οι τρεις πρώτες λίστες θα εντοπίζονται πάντα από το Aspose.Words,
	// και τα αντικείμενα λίστας θα δημιουργηθούν για αυτούς μετά τη φόρτωση.
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
	// Η τέταρτη λίστα, με κενό διάστημα μεταξύ του αριθμού λίστας και των περιεχομένων του στοιχείου λίστας,
	// θα εντοπιστεί ως λίστα μόνο εάν το "DetectNumberingWithWhitespaces" σε ένα αντικείμενο LoadOptions έχει οριστεί σε true,
	// για να αποφευχθεί η εσφαλμένη ανίχνευση παραγράφων που ξεκινούν με αριθμούς ως λίστες.
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDetectNumberingWithWhitespaces(true);
	}
	// Φορτώστε το έγγραφο ενώ εφαρμόζετε το LoadOptions ως παράμετρο και επαληθεύστε το αποτέλεσμα.
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

Σε αυτόν τον οδηγό, εξερευνήσαμε πώς να φορτώνουμε αρχεία κειμένου χρησιμοποιώντας το Aspose.Words για Java, να ανιχνεύουμε λίστες, να χειριζόμαστε κενά και να ελέγχουμε την κατεύθυνση του κειμένου. Αυτές οι τεχνικές σάς επιτρέπουν να χειρίζεστε αποτελεσματικά έγγραφα κειμένου στις εφαρμογές σας Java.

## Συχνές ερωτήσεις

### Τι είναι το Aspose.Words για Java;

Το Aspose.Words για Java είναι μια ισχυρή βιβλιοθήκη επεξεργασίας εγγράφων που επιτρέπει στους προγραμματιστές να δημιουργούν, να χειρίζονται και να μετατρέπουν έγγραφα του Word μέσω προγραμματισμού σε εφαρμογές Java. Παρέχει ένα ευρύ φάσμα δυνατοτήτων για εργασία με κείμενο, πίνακες, εικόνες και άλλα στοιχεία εγγράφου.

### Πώς μπορώ να ξεκινήσω με το Aspose.Words για Java;

Για να ξεκινήσετε με το Aspose.Words για Java, ακολουθήστε τα εξής βήματα:
1. Κάντε λήψη και εγκατάσταση της βιβλιοθήκης Aspose.Words για Java.
2.  Ανατρέξτε στην τεκμηρίωση στη διεύθυνση[Aspose.Words for Java API Reference](https://reference.aspose.com/words/java/) για λεπτομερείς πληροφορίες και παραδείγματα.
3. Εξερευνήστε το δείγμα κώδικα και τα μαθήματα για να μάθετε πώς να χρησιμοποιείτε τη βιβλιοθήκη αποτελεσματικά.

### Πώς μπορώ να φορτώσω ένα έγγραφο κειμένου χρησιμοποιώντας το Aspose.Words για Java;

 Για να φορτώσετε ένα έγγραφο κειμένου χρησιμοποιώντας το Aspose.Words για Java, μπορείτε να χρησιμοποιήσετε το`TxtLoadOptions` τάξη και το`Document` τάξη. Βεβαιωθείτε ότι έχετε καθορίσει τις κατάλληλες επιλογές για το χειρισμό των χώρων και την κατεύθυνση του κειμένου, όπως απαιτείται. Ανατρέξτε στον οδηγό βήμα προς βήμα σε αυτό το άρθρο για ένα λεπτομερές παράδειγμα.

### Μπορώ να μετατρέψω ένα φορτωμένο έγγραφο κειμένου σε άλλες μορφές;

 Ναι, το Aspose.Words για Java σάς επιτρέπει να μετατρέψετε ένα φορτωμένο έγγραφο κειμένου σε διάφορες μορφές, συμπεριλαμβανομένων των DOCX, PDF και άλλων. Μπορείτε να χρησιμοποιήσετε το`Document` τάξη για την εκτέλεση μετατροπών. Ελέγξτε την τεκμηρίωση για συγκεκριμένα παραδείγματα μετατροπών.

### Πώς χειρίζομαι τα κενά σε φορτωμένα έγγραφα κειμένου;

 Μπορείτε να ελέγξετε τον τρόπο χειρισμού των κενών και των τελικών χώρων στα φορτωμένα έγγραφα κειμένου χρησιμοποιώντας`TxtLoadOptions` . Επιλογές όπως`TxtLeadingSpacesOptions` και`TxtTrailingSpacesOptions`σας επιτρέπουν να κόψετε ή να διατηρήσετε κενά όπως χρειάζεται. Ανατρέξτε στην ενότητα "Επιλογές χειρισμού χώρων" σε αυτόν τον οδηγό για παράδειγμα.

### Ποια είναι η σημασία της κατεύθυνσης κειμένου στο Aspose.Words για Java;

Η κατεύθυνση κειμένου είναι απαραίτητη για έγγραφα που περιέχουν μικτές γραφές ή γλώσσες, όπως τα εβραϊκά ή τα αραβικά. Το Aspose.Words για Java παρέχει επιλογές για τον καθορισμό της κατεύθυνσης του κειμένου, διασφαλίζοντας τη σωστή απόδοση και μορφοποίηση του κειμένου σε αυτές τις γλώσσες. Η ενότητα "Έλεγχος κατεύθυνσης κειμένου" σε αυτόν τον οδηγό δείχνει πώς να ορίσετε την κατεύθυνση του κειμένου.

### Πού μπορώ να βρω περισσότερους πόρους και υποστήριξη για το Aspose.Words για Java;

 Για πρόσθετους πόρους, τεκμηρίωση και υποστήριξη, επισκεφθείτε τη διεύθυνση[Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/). Μπορείτε επίσης να συμμετάσχετε στα φόρουμ της κοινότητας του Aspose.Words ή να επικοινωνήσετε με την υποστήριξη της Aspose για βοήθεια με συγκεκριμένα ζητήματα ή απορίες.

### Είναι το Aspose.Words για Java κατάλληλο για εμπορικά έργα;

Ναι, το Aspose.Words για Java είναι κατάλληλο τόσο για προσωπικά όσο και για εμπορικά έργα. Προσφέρει επιλογές αδειοδότησης για να φιλοξενήσει διάφορα σενάρια χρήσης. Βεβαιωθείτε ότι έχετε διαβάσει τους όρους αδειοδότησης και την τιμολόγηση στον ιστότοπο της Aspose για να επιλέξετε την κατάλληλη άδεια χρήσης για το έργο σας.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
