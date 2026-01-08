---
date: 2025-12-27
description: Μάθετε πώς να ορίζετε κατεύθυνση, να φορτώνετε αρχεία txt, να αφαιρείτε
  κενά και να μετατρέπετε txt σε docx χρησιμοποιώντας το Aspose.Words for Java.
linktitle: Loading Text Files with
second_title: Aspose.Words Java Document Processing API
title: Πώς να ορίσετε την κατεύθυνση και να φορτώσετε αρχεία κειμένου με το Aspose.Words
  για Java
url: /el/java/document-loading-and-saving/loading-text-files/
weight: 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να Ορίσετε Κατεύθυνση και να Φορτώσετε Αρχεία Κειμένου με το Aspose.Words for Java

## Εισαγωγή στη Φόρτωση Αρχείων Κειμένου με το Aspose.Words for Java

Σε αυτόν τον οδηγό, θα ανακαλύψετε **πώς να ορίσετε την κατεύθυνση** κατά τη φόρτωση αρχείων απλού κειμένου και θα δείτε πρακτικούς τρόπους για **φόρτωση txt**, **αφαίρεση κενών** και **μετατροπή txt σε docx** χρησιμοποιώντας το Aspose.Words for Java. Είτε δημιουργείτε μια υπηρεσία μετατροπής εγγράφων είτε χρειάζεστε λεπτομερή έλεγχο της ανίχνευσης λιστών, αυτό το tutorial σας οδηγεί βήμα‑βήμα με σαφείς εξηγήσεις και κώδικα έτοιμο προς εκτέλεση.

## Γρήγορες Απαντήσεις
- **Πώς ορίζω την κατεύθυνση κειμένου για ένα φορτωμένο αρχείο TXT;** Χρησιμοποιήστε `TxtLoadOptions.setDocumentDirection(DocumentDirection.AUTO)` ή καθορίστε `LEFT_TO_RIGHT` / `RIGHT_TO_LEFT`.
- **Μπορεί το Aspose.Words να ανιχνεύσει αριθμημένες λίστες σε απλό κείμενο;** Ναι – ενεργοποιήστε `DetectNumberingWithWhitespaces` στο `TxtLoadOptions`.
- **Πώς μπορώ να αφαιρέσω τα αρχικά και τελικά κενά;** Ορίστε `TxtLeadingSpacesOptions.TRIM` και `TxtTrailingSpacesOptions.TRIM`.
- **Μπορεί να γίνει η μετατροπή ενός αρχείου TXT σε DOCX με μία γραμμή;** Φορτώστε το TXT με `TxtLoadOptions` και καλέστε `Document.save("output.docx")`.
- **Ποια έκδοση της Java απαιτείται;** Η Java 8+ είναι επαρκής για το Aspose.Words 24.x.

## Τι είναι το “πώς να ορίσετε κατεύθυνση” στο Aspose.Words;
Όταν ένα αρχείο κειμένου περιέχει γραφές από δεξιά προς αριστερά (π.χ., εβραϊκά ή αραβικά), η βιβλιοθήκη πρέπει να γνωρίζει τη σειρά ανάγνωσης. Η απαρίθμηση `DocumentDirection` σας επιτρέπει να **ορίσετε την κατεύθυνση** χειροκίνητα ή να αφήσετε το Aspose να την ανιχνεύσει αυτόματα, εξασφαλίζοντας σωστή διάταξη και μορφοποίηση bidi.

## Γιατί να χρησιμοποιήσετε το Aspose.Words για τη φόρτωση αρχείων TXT;
- **Ακριβής ανίχνευση λιστών** – διαχειρίζεται αριθμημένες, με κουκκίδες και λίστες που ορίζονται με κενά.  
- **Λεπτομερής διαχείριση κενών** – αφαιρεί ή διατηρεί τα αρχικά/τελικά κενά.  
- **Αυτόματη ανίχνευση κατεύθυνσης κειμένου** – ιδανική για πολυγλωσσικά έγγραφα.  
- **Μετατροπή σε ένα βήμα** – φορτώστε ένα `.txt` και αποθηκεύστε το ως `.docx`, `.pdf` ή οποιαδήποτε υποστηριζόμενη μορφή.

## Προαπαιτούμενα
- Java 8 ή νεότερη.  
- Βιβλιοθήκη Aspose.Words for Java (προσθέστε την εξάρτηση Maven/Gradle ή το JAR στο πρόγραμμά σας).  
- Βασικές γνώσεις των ροών I/O της Java.

## Οδηγός Βήμα‑Βήμα

### Βήμα 1: Ανίχνευση Λιστών (πώς να φορτώσετε txt)
Για να φορτώσετε ένα έγγραφο κειμένου και να ανιχνεύσετε αυτόματα τις λίστες, δημιουργήστε μια παρουσία `TxtLoadOptions` και ενεργοποιήστε την ανίχνευση λιστών. Ο κώδικας παρακάτω δείχνει διάφορα στυλ λιστών και ενεργοποιεί την αρίθμηση με βάση τα κενά.

```java
// Create a plaintext document in the form of a string with parts that may be interpreted as lists.
// Upon loading, the first three lists will always be detected by Aspose.Words,
// and List objects will be created for them after loading.
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
// The fourth list, with whitespace in between the list number and list item contents,
// will only be detected as a list if "DetectNumberingWithWhitespaces" in a LoadOptions object is set to true,
// to avoid paragraphs that start with numbers being mistakenly detected as lists.
TxtLoadOptions loadOptions = new TxtLoadOptions();
{
    loadOptions.setDetectNumberingWithWhitespaces(true);
}
// Load the document while applying LoadOptions as a parameter and verify the result.
Document doc = new Document(new ByteArrayInputStream(TEXT_DOC.getBytes()), loadOptions);
doc.save("Your Directory Path" + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

> **Συμβουλή:** Εάν χρειάζεστε μόνο βασική ανίχνευση λιστών, μπορείτε να παραλείψετε την επιλογή κενών – το Aspose θα αναγνωρίσει ακόμη τα τυπικά πρότυπα `1.` και `1)`.

### Βήμα 2: Διαχείριση Επιλογών Κενών (πώς να αφαιρέσετε κενά)
Τα αρχικά και τελικά κενά συχνά προκαλούν προβλήματα μορφοποίησης. Χρησιμοποιήστε `TxtLeadingSpacesOptions` και `TxtTrailingSpacesOptions` για να ελέγξετε αυτή τη συμπεριφορά.

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

> **Γιατί είναι σημαντικό:** Η αφαίρεση κενών αποτρέπει ανεπιθύμητη εσοχή στο τελικό DOCX, κάνοντας το έγγραφο καθαρό χωρίς χειροκίνητη επεξεργασία.

### Βήμα 3: Έλεγχος Κατεύθυνσης Κειμένου (πώς να ορίσετε κατεύθυνση)
Για γλώσσες από δεξιά προς αριστερά, ορίστε την κατεύθυνση του εγγράφου πριν τη φόρτωση. Το παρακάτω παράδειγμα φορτώνει ένα εβραϊκό αρχείο κειμένου και εκτυπώνει τη σημαία bidi για να επιβεβαιώσει την κατεύθυνση.

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

> **Κοινό λάθος:** Η παράλειψη του ορισμού `DocumentDirection` μπορεί να οδηγήσει σε ακατάστατο αραβικό/εβραϊκό κείμενο όπου οι χαρακτήρες εμφανίζονται με λάθος σειρά.

## Πλήρης Πηγαίος Κώδικας για τη Φόρτωση Αρχείων Κειμένου με το Aspose.Words for Java
Παρακάτω βρίσκεται ο πλήρης, έτοιμος για εκτέλεση κώδικας που συνδυάζει την ανίχνευση λιστών, τη διαχείριση κενών και τον έλεγχο κατεύθυνσης. Μπορείτε να τον αντιγράψετε σε μία κλάση και να εκτελέσετε τις τρεις μεθόδους δοκιμής ξεχωριστά.

```java
public void detectNumberingWithWhitespaces() throws Exception {
	// Create a plaintext document in the form of a string with parts that may be interpreted as lists.
	// Upon loading, the first three lists will always be detected by Aspose.Words,
	// and List objects will be created for them after loading.
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
	// The fourth list, with whitespace inbetween the list number and list item contents,
	// will only be detected as a list if "DetectNumberingWithWhitespaces" in a LoadOptions object is set to true,
	// to avoid paragraphs that start with numbers being mistakenly detected as lists.
	TxtLoadOptions loadOptions = new TxtLoadOptions();
	{
		loadOptions.setDetectNumberingWithWhitespaces(true);
	}
	// Load the document while applying LoadOptions as a parameter and verify the result.
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

## Συχνά Προβλήματα και Λύσεις

| Πρόβλημα | Αιτία | Διόρθωση |
|----------|-------|----------|
| Λίστες δεν ανιχνεύονται | `DetectNumberingWithWhitespaces` παραμένει `false` για λίστες που ορίζονται με κενά | Ενεργοποιήστε `loadOptions.setDetectNumberingWithWhitespaces(true)` |
| Επιπλέον εσοχή μετά τη φόρτωση | Τα αρχικά κενά διατηρήθηκαν | Ορίστε `TxtLeadingSpacesOptions.TRIM` |
| Το εβραϊκό κείμενο εμφανίζεται ανάποδα | Η κατεύθυνση του εγγράφου δεν ορίστηκε ή ορίστηκε σε `LEFT_TO_RIGHT` | Χρησιμοποιήστε `DocumentDirection.AUTO` ή `RIGHT_TO_LEFT` |
| Το παραγόμενο DOCX είναι κενό | Η ροή εισόδου δεν επαναφέρθηκε πριν τη δεύτερη φόρτωση | Δημιουργήστε ξανά `ByteArrayInputStream` για κάθε κλήση φόρτωσης |

## Συχνές Ερωτήσεις

### Ε: Τι είναι το Aspose.Words for Java;
Το Aspose.Words for Java είναι μια ισχυρή βιβλιοθήκη επεξεργασίας εγγράφων που επιτρέπει στους προγραμματιστές να δημιουργούν, να τροποποιούν και να μετατρέπουν έγγραφα Word προγραμματιστικά σε εφαρμογές Java. Υποστηρίζει ένα ευρύ φάσμα λειτουργιών, από απλή φόρτωση κειμένου μέχρι σύνθετη μορφοποίηση και μετατροπή.

### Ε: Πώς μπορώ να ξεκινήσω με το Aspose.Words for Java;
1. Κατεβάστε και εγκαταστήστε τη βιβλιοθήκη Aspose.Words for Java.  
2. Ανατρέξτε στην τεκμηρίωση στο [Aspose.Words for Java API Reference](https://reference.aspose.com/words/java/) για λεπτομερείς πληροφορίες και παραδείγματα.  
3. Εξερευνήστε τα παραδείγματα κώδικα και τα tutorials για να μάθετε πώς να χρησιμοποιείτε αποτελεσματικά τη βιβλιοθήκη.

### Ε: Πώς φορτώνω ένα έγγραφο κειμένου χρησιμοποιώντας το Aspose.Words for Java;
Χρησιμοποιήστε την κλάση `TxtLoadOptions` μαζί με τον κατασκευαστή `Document`. Καθορίστε επιλογές όπως ανίχνευση λιστών, διαχείριση κενών ή κατεύθυνση κειμένου όπως φαίνεται στις παραπάνω ενότητες βήμα‑βήμα.

### Ε: Μπορώ να μετατρέψω ένα φορτωμένο έγγραφο κειμένου σε άλλες μορφές;
Ναι. Αφού φορτώσετε το αρχείο TXT σε ένα αντικείμενο `Document`, καλέστε `doc.save("output.pdf")`, `doc.save("output.docx")` ή οποιαδήποτε άλλη υποστηριζόμενη μορφή.

### Ε: Πώς διαχειρίζομαι τα κενά σε φορτωμένα έγγραφα κειμένου;
Διαχειριστείτε τα αρχικά και τελικά κενά με `TxtLeadingSpacesOptions` και `TxtTrailingSpacesOptions`. Ορίστε τα σε `TRIM` για να αφαιρέσετε ανεπιθύμητα κενά, ή σε `PRESERVE` εάν χρειάζεται να διατηρήσετε την αρχική διάταξη.

### Ε: Ποια είναι η σημασία της κατεύθυνσης κειμένου στο Aspose.Words for Java;
Η κατεύθυνση κειμένου εξασφαλίζει τη σωστή απόδοση των γραφών από δεξιά προς αριστερά (εβραϊκά, αραβικά κ.λπ.). Ορίζοντας το `DocumentDirection`, εγγυάστε ότι το κείμενο bidi εμφανίζεται σωστά στο παραγόμενο έγγραφο.

### Ε: Πού μπορώ να βρω περισσότερους πόρους και υποστήριξη για το Aspose.Words for Java;
Επισκεφθείτε την [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/) για αναφορές API, παραδείγματα κώδικα και λεπτομερείς οδηγούς. Μπορείτε επίσης να συμμετάσχετε στα φόρουμ της κοινότητας Aspose ή να επικοινωνήσετε με την υποστήριξη Aspose για συγκεκριμένες ερωτήσεις.

### Ε: Είναι το Aspose.Words for Java κατάλληλο για εμπορικά έργα;
Ναι. Προσφέρει επιλογές αδειοδότησης για προσωπική και εμπορική χρήση. Εξετάστε τους όρους αδειοδότησης στην ιστοσελίδα της Aspose για να επιλέξετε το κατάλληλο πρόγραμμα για το έργο σας.

## Συμπέρασμα
Τώρα διαθέτετε ένα πλήρες σύνολο εργαλείων για **φόρτωση αρχείων txt**, **ανίχνευση λιστών**, **αφαίρεση κενών** και **ορισμό κατεύθυνσης** κατά τη μετατροπή απλού κειμένου σε πλούσια έγγραφα Word με το Aspose.Words for Java. Εφαρμόστε αυτά τα πρότυπα για να αυτοματοποιήσετε τις ροές εργασίας εγγράφων, να βελτιώσετε την πολυγλωσσία και να εξασφαλίσετε καθαρό, επαγγελματικό αποτέλεσμα κάθε φορά.

---

**Last Updated:** 2025-12-27  
**Tested With:** Aspose.Words for Java 24.12  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}