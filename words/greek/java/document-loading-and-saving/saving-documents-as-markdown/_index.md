---
date: 2025-12-22
description: Μάθετε πώς να εξάγετε markdown μετατρέποντας έγγραφα Word σε Markdown
  με το Aspose.Words for Java. Αυτός ο οδηγός βήμα‑βήμα καλύπτει την ευθυγράμμιση
  πινάκων, τη διαχείριση εικόνων και πολλά άλλα.
linktitle: Saving Documents as Markdown
second_title: Aspose.Words Java Document Processing API
title: Πώς να εξάγετε Markdown με το Aspose.Words για Java
url: /el/java/document-loading-and-saving/saving-documents-as-markdown/
weight: 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να Εξάγετε Markdown με το Aspose.Words για Java

## Εισαγωγή στην Εξαγωγή Markdown με το Aspose.Words για Java

Σε αυτό το βήμα‑βήμα tutorial, **θα μάθετε πώς να εξάγετε markdown** από έγγραφα Word χρησιμοποιώντας το Aspose.Words για Java. Το Markdown είναι μια ελαφριά γλώσσα σήμανσης που είναι ιδανική για τεκμηρίωση, στατικούς δημιουργούς ιστοσελίδων και πολλές πλατφόρμες δημοσίευσης. Στο τέλος αυτού του οδηγού θα μπορείτε να **μετατρέψετε Word σε markdown**, να προσαρμόσετε τη στοίχιση των πινάκων και να **διαχειριστείτε εικόνες σε markdown** χωρίς κόπο.

## Γρήγορες Απαντήσεις
- **Ποια είναι η κύρια κλάση για αποθήκευση ως Markdown;** `MarkdownSaveOptions`
- **Μπορούν οι εικόνες να ενσωματωθούν αυτόματα;** Ναι – ορίστε το φάκελο εικόνων μέσω `setImagesFolder`.
- **Πώς ελέγχω την στοίχιση των πινάκων;** Χρησιμοποιήστε `TableContentAlignment` (LEFT, RIGHT, CENTER, AUTO).
- **Ποιες είναι οι ελάχιστες απαιτήσεις;** JDK 8+ και βιβλιοθήκη Aspose.Words για Java.
- **Υπάρχει διαθέσιμη δοκιμαστική έκδοση;** Ναι, κατεβάστε την από την ιστοσελίδα της Aspose.

## Τι σημαίνει «πώς να εξάγετε markdown»;
Η εξαγωγή markdown σημαίνει τη μετατροπή ενός πλούσιου εγγράφου Word (`.docx`) σε ένα απλό αρχείο κειμένου `.md` που διατηρεί τις επικεφαλίδες, τους πίνακες και τις εικόνες σε σύνταξη Markdown.

## Γιατί να χρησιμοποιήσετε το Aspose.Words για Java για τη μετατροπή docx με εικόνες;
Το Aspose.Words διαχειρίζεται πολύπλοκες διατάξεις, ενσωματωμένες εικόνες και δομές πινάκων χωρίς να χάνει την πιστότητα. Επιπλέον, σας παρέχει λεπτομερή έλεγχο της εξόδου Markdown, όπως η στοίχιση των πινάκων και η διαχείριση του φακέλου εικόνων.

## Προαπαιτούμενα

- Java Development Kit (JDK) εγκατεστημένο στο σύστημά σας.  
- Βιβλιοθήκη Aspose.Words για Java. Μπορείτε να την κατεβάσετε από [εδώ](https://releases.aspose.com/words/java/).

## Βήμα 1: Δημιουργήστε ένα απλό έγγραφο Word

Πρώτα, θα δημιουργήσουμε ένα μικρό έγγραφο που περιέχει έναν πίνακα. Αυτό θα μας επιτρέψει να δείξουμε αργότερα την **προσαρμογή της στοίχισης του πίνακα**.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table with two cells
builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
builder.write("Cell1");

builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.write("Cell2");

// Save the document as Markdown
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
doc.save("output.md", saveOptions);
```

Στο παραπάνω απόσπασμα κάνουμε:

1. Δημιουργούμε ένα νέο `Document`.  
2. Χρησιμοποιούμε το `DocumentBuilder` για να εισάγουμε έναν πίνακα με δύο κελιά.  
3. Εφαρμόζουμε **δεξιά** και **κεντρική** στοίχιση παραγράφου μέσα σε κάθε κελί.  
4. Αποθηκεύουμε το αρχείο ως Markdown χρησιμοποιώντας το `MarkdownSaveOptions`.

## Βήμα 2: Προσαρμόστε τη στοίχιση του περιεχομένου του πίνακα

Το Aspose.Words σας επιτρέπει να καθορίσετε πώς θα αποδοθούν τα κελιά του πίνακα στο τελικό Markdown. Μπορείτε να επιβάλετε αριστερή, δεξιά ή κεντρική στοίχιση, ή να αφήσετε τη βιβλιοθήκη να αποφασίσει αυτόματα με βάση την πρώτη παράγραφο σε κάθε στήλη.

```java
// Set the table content alignment to left
saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
doc.save("left_alignment.md", saveOptions);

// Set the table content alignment to right
saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
doc.save("right_alignment.md", saveOptions);

// Set the table content alignment to center
saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
doc.save("center_alignment.md", saveOptions);

// Set the table content alignment to auto (determined by first paragraph)
saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
doc.save("auto_alignment.md", saveOptions);
```

Αλλάζοντας την ιδιότητα `TableContentAlignment` ελέγχετε την **προσαρμογή της στοίχισης του πίνακα** για την έξοδο Markdown.

## Βήμα 3: Διαχειριστείτε τις εικόνες κατά την εξαγωγή σε markdown

Όταν ένα έγγραφο περιέχει εικόνες, θέλετε αυτές οι εικόνες να εμφανίζονται σωστά στο παραγόμενο αρχείο `.md`. Ορίστε το φάκελο όπου το Aspose.Words θα αποθηκεύσει τις εξαγόμενες εικόνες.

```java
// Load a document containing images
Document doc = new Document("document_with_images.docx");

// Set the images folder path
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Save the document with images
doc.save("document_with_images.md", saveOptions);
```

Αντικαταστήστε το `"document_with_images.docx"` με τη διαδρομή του πηγαίου αρχείου σας και το `"images_folder/"` με την τοποθεσία όπου θέλετε να αποθηκευτούν οι εικόνες. Το παραγόμενο Markdown θα περιέχει συνδέσμους εικόνας που δείχνουν σε αυτόν το φάκελο, επιτρέποντάς σας να **διαχειριστείτε εικόνες σε markdown** απρόσκοπτα.

## Πλήρης Πηγαίος Κώδικας για την Αποθήκευση Εγγράφων ως Markdown με το Aspose.Words για Java

```java
public void autoTableContentAlignment() throws Exception
{
	Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);
	builder.insertCell();
	builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
	builder.write("Cell1");
	builder.insertCell();
	builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
	builder.write("Cell2");
	// Makes all paragraphs inside the table to be aligned.
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
	{
		saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
	}
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.LeftTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.RightTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.CenterTableContentAlignment.md", saveOptions);
	// The alignment in this case will be taken from the first paragraph in corresponding table column.
	saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.AutoTableContentAlignment.md", saveOptions);
}
@Test
public void setImagesFolder() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Image bullet points.docx");
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions(); { saveOptions.setImagesFolder("Your Directory Path" + "Images"); }
	try(ByteArrayOutputStream stream = new ByteArrayOutputStream())
	{
		doc.save(stream, saveOptions);
	}
}
```

## Κοινά Προβλήματα και Λύσεις

| Πρόβλημα | Λύση |
|----------|------|
| Οι εικόνες δεν εμφανίζονται στο αρχείο `.md` | Βεβαιωθείτε ότι το `setImagesFolder` δείχνει σε έναν εγγράψιμο φάκελο και ότι ο φάκελος αναφέρεται σωστά στο παραγόμενο Markdown. |
| Η στοίχιση του πίνακα φαίνεται λανθασμένη | Χρησιμοποιήστε `TableContentAlignment.AUTO` για να αφήσετε το Aspose.Words να καθορίσει την καλύτερη στοίχιση βάσει της πρώτης παραγράφου κάθε στήλης. |
| Το αρχείο εξόδου είναι κενό | Εξασφαλίστε ότι το αντικείμενο `Document` περιέχει πραγματικό περιεχόμενο πριν καλέσετε τη μέθοδο `save`. |

## Συχνές Ερωτήσεις

**Ε: Πώς εγκαθιστώ το Aspose.Words για Java;**  
Α: Το Aspose.Words για Java μπορεί να εγκατασταθεί προσθέτοντας τη βιβλιοθήκη στο έργο σας Java. Μπορείτε να κατεβάσετε τη βιβλιοθήκη από [εδώ](https://releases.aspose.com/words/java/) και να ακολουθήσετε τις οδηγίες εγκατάστασης που παρέχονται στην τεκμηρίωση.

**Ε: Μπορώ να μετατρέψω πολύπλοκα έγγραφα Word με πίνακες και εικόνες σε Markdown;**  
Α: Ναι, το Aspose.Words για Java υποστηρίζει τη μετατροπή πολύπλοκων εγγράφων Word με πίνακες, εικόνες και διάφορα στοιχεία μορφοποίησης σε Markdown. Μπορείτε να προσαρμόσετε την έξοδο Markdown ανάλογα με την πολυπλοκότητα του εγγράφου σας.

**Ε: Πώς μπορώ να διαχειριστώ εικόνες σε αρχεία Markdown;**  
Α: Ορίστε τη διαδρομή του φακέλου εικόνων χρησιμοποιώντας τη μέθοδο `setImagesFolder` στο `MarkdownSaveOptions`. Βεβαιωθείτε ότι τα αρχεία εικόνας αποθηκεύονται στον καθορισμένο φάκελο· το Aspose.Words θα δημιουργήσει τους κατάλληλους συνδέσμους εικόνας στο Markdown.

**Ε: Υπάρχει διαθέσιμη δοκιμαστική έκδοση του Aspose.Words για Java;**  
Α: Ναι, μπορείτε να αποκτήσετε μια δοκιμαστική έκδοση του Aspose.Words για Java από την ιστοσελίδα της Aspose. Η δοκιμαστική έκδοση σας επιτρέπει να αξιολογήσετε τις δυνατότητες της βιβλιοθήκης πριν αγοράσετε άδεια.

**Ε: Πού μπορώ να βρω περισσότερα παραδείγματα και τεκμηρίωση;**  
Α: Για περισσότερα παραδείγματα, τεκμηρίωση και λεπτομερείς πληροφορίες σχετικά με το Aspose.Words για Java, επισκεφθείτε το [documentation](https://reference.aspose.com/words/java/).

---

**Τελευταία ενημέρωση:** 2025-12-22  
**Δοκιμάστηκε με:** Aspose.Words για Java 24.12 (τελευταία έκδοση τη στιγμή της συγγραφής)  
**Συγγραφέας:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}