---
date: 2026-02-24
description: Μάθετε πώς να μετατρέπετε το Word σε markdown χρησιμοποιώντας το Aspose.Words
  for Java. Αυτός ο οδηγός καλύπτει την ευθυγράμμιση πινάκων, τη διαχείριση εικόνων
  και πώς να αποθηκεύσετε το έγγραφο ως markdown.
linktitle: Saving Documents as Markdown
second_title: Aspose.Words Java Document Processing API
title: Μετατροπή Word σε Markdown με το Aspose.Words για Java
url: /el/java/document-loading-and-saving/saving-documents-as-markdown/
weight: 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Μετατροπή Word σε Markdown με Aspose.Words για Java

## Εισαγωγή στη Μετατροπή Word σε Markdown με Aspose.Words για Java

Σε αυτό το βήμα‑βήμα tutorial θα μάθετε **πώς να μετατρέψετε Word σε Markdown** χρησιμοποιώντας το ισχυρό API Aspose.Words for Java. Το Markdown είναι μια ελαφριά γλώσσα σήμανσης που πολλοί προγραμματιστές και πλατφόρμες περιεχομένου χρησιμοποιούν για καθαρή, ευανάγνωστη τεκμηρίωση. Στο τέλος αυτού του οδηγού θα μπορείτε να πάρτε οποιοδήποτε αρχείο `.docx`, να διατηρήσετε πίνακες, εικόνες και μορφοποίηση, και να το εξάγετε ως αρχείο `.md` έτοιμο για στατικούς‑site γεννήτορες, GitHub READMEs ή οποιαδήποτε ροή εργασίας φιλική προς το markdown.

## Γρήγορες Απαντήσεις
- **Ποια βιβλιοθήκη χρειάζομαι;** Aspose.Words for Java (`aspose-words.jar`).
- **Μπορώ να προσαρμόσω την ευθυγράμμιση των πινάκων;** Ναι – χρησιμοποιήστε το `TableContentAlignment` στο `MarkdownSaveOptions`.
- **Πώς διαχειρίζονται οι εικόνες;** Ορίστε έναν φάκελο εικόνων με `setImagesFolder()`· η βιβλιοθήκη δημιουργεί σχετικούς συνδέσμους.
- **Χρειάζομαι άδεια για παραγωγή;** Απαιτείται εμπορική άδεια για μη‑δοκιμαστική χρήση.
- **Είναι συμβατό με Java 17;** Ναι, η βιβλιοθήκη υποστηρίζει Java 8 και νεότερες.

## Τι είναι η μετατροπή Word σε Markdown;

Η μετατροπή Word σε Markdown σημαίνει ότι παίρνουμε τον πλούσιο μορφοποιημένο περιεχόμενο ενός εγγράφου Microsoft Word και τον μεταφράζουμε σε συντακτικό markdown απλού κειμένου. Αυτή η διαδικασία διατηρεί τίτλους, λίστες, πίνακες και αναφορές εικόνων ενώ αφαιρεί τη δυαδική μορφοποίηση, καθιστώντας το περιεχόμενο φορητό και φιλικό σε συστήματα ελέγχου εκδόσεων.

## Γιατί να χρησιμοποιήσετε το Aspose.Words για Java για αποθήκευση εγγράφου ως markdown;

* **Πλήρης πιστότητα** – πίνακες, εικόνες και σύνθετες διατάξεις διατηρούνται.
* **Λεπτομερής έλεγχος** – μπορείτε να προσαρμόσετε την ευθυγράμμιση των πινάκων, τις διαδρομές εικόνων κ.λπ.
* **Χωρίς εξωτερικές εξαρτήσεις** – η βιβλιοθήκη λειτουργεί αμέσως χωρίς ανάγκη εγκατάστασης του Office.
* **Δια‑πλατφόρμα** – λειτουργεί σε Windows, Linux και macOS με οποιοδήποτε Java runtime.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

- Java Development Kit (JDK) εγκατεστημένο στο σύστημά σας.
- Βιβλιοθήκη Aspose.Words for Java. Μπορείτε να τη κατεβάσετε από [εδώ](https://releases.aspose.com/words/java/).

## Οδηγός Βήμα‑βήμα

### Βήμα 1: Δημιουργία εγγράφου Word που θα μετατραπεί

Πρώτα, δημιουργούμε ένα απλό έγγραφο Word που περιέχει έναν πίνακα δύο κελιών. Αυτό το παράδειγμα δείχνει πώς η ευθυγράμμιση παραγράφων μέσα στα κελιά του πίνακα τηρείται όταν αργότερα **αποθηκεύσουμε το έγγραφο ως markdown**.

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

### Βήμα 2: Προσαρμογή ευθυγράμμισης περιεχομένου πίνακα

Το Aspose.Words for Java σας επιτρέπει να ελέγχετε πώς ευθυγραμμίζονται τα κελιά του πίνακα στο παραγόμενο markdown. Χρησιμοποιήστε την ιδιότητα `TableContentAlignment` για να ορίσετε **προσαρμοσμένη ευθυγράμμιση πίνακα** στα αριστερά, δεξιά, κέντρο, ή αφήστε τη βιβλιοθήκη να αποφασίσει αυτόματα βάσει της πρώτης παραγράφου σε κάθε στήλη.

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

Με την εναλλαγή αυτής της ρύθμισης μπορείτε να **εξάγετε πίνακες Word σε markdown** με την ακριβή ευθυγράμμιση που χρειάζεστε για τις επόμενες μηχανές απόδοσης.

### Βήμα 3: Διαχείριση εικόνων κατά τη μετατροπή

Όταν το πηγαίο έγγραφο Word περιέχει εικόνες, πρέπει να ενημερώσετε το Aspose.Words πού θα τοποθετήσει τα εξαγόμενα αρχεία εικόνας. Η μέθοδος `setImagesFolder` στο `MarkdownSaveOptions` ορίζει το φάκελο που θα φιλοξενήσει τα αρχεία εικόνας, και το markdown θα περιέχει σχετικούς συνδέσμους προς αυτά τα αρχεία.

```java
// Load a document containing images
Document doc = new Document("document_with_images.docx");

// Set the images folder path
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Save the document with images
doc.save("document_with_images.md", saveOptions);
```

Αντικαταστήστε `"document_with_images.docx"` με τη διαδρομή του πηγαίου αρχείου σας και `"images_folder/"` με τον επιθυμητό φάκελο εξόδου για τις εικόνες.

### Πλήρης κώδικας πηγής για όλα τα σενάρια

Παρακάτω υπάρχει ένα ενοποιημένο παράδειγμα που δείχνει πώς να **αυτοματοποιήσετε την ευθυγράμμιση πίνακα**, **προσαρμόσετε την ευθυγράμμιση**, και **ορίσετε φάκελο εικόνων** σε μία μέθοδο. Αυτό το απόσπασμα αντικατοπτρίζει τον αρχικό κώδικα του tutorial και λειτουργεί αμετάβλητο.

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

| Πρόβλημα | Αιτία | Διόρθωση |
|----------|-------|----------|
| Οι εικόνες εμφανίζονται ως σπασμένοι σύνδεσμοι | `setImagesFolder` δεν έχει οριστεί ή η διαδρομή φακέλου είναι λανθασμένη | Επαληθεύστε ότι η διαδρομή του φακέλου είναι σωστή και ότι ο φάκελος είναι εγγράψιμος |
| Η ευθυγράμμιση του πίνακα φαίνεται λανθασμένη | Λάθος τιμή `TableContentAlignment` | Χρησιμοποιήστε `TableContentAlignment.AUTO` για να αφήσετε την πρώτη παράγραφο να αποφασίσει, ή ορίστε ρητά LEFT/RIGHT/CENTER |
| Το αρχείο εξόδου είναι κενό | Οι επιλογές αποθήκευσης δεν περνιούνται στο `doc.save()` | Βεβαιωθείτε ότι περνάτε το αντικείμενο `MarkdownSaveOptions` στη μέθοδο `save` |
| Μη υποστηριζόμενα χαρακτηριστικά Word (π.χ., SmartArt) | Το Markdown δεν μπορεί να αναπαραστήσει ορισμένα σύνθετα αντικείμενα | Μετατρέψτε αυτά τα στοιχεία σε εικόνες πριν την αποθήκευση, ή απλοποιήστε το πηγαίο έγγραφο |

## Συχνές Ερωτήσεις

**Ε: Πώς εγκαθιστώ το Aspose.Words για Java;**  
Α: Το Aspose.Words για Java μπορεί να εγκατασταθεί προσθέτοντας τη βιβλιοθήκη στο Java project σας. Μπορείτε να κατεβάσετε τη βιβλιοθήκη από [εδώ](https://releases.aspose.com/words/java/) και να ακολουθήσετε τις οδηγίες εγκατάστασης που παρέχονται στην τεκμηρίωση.

**Ε: Μπορώ να μετατρέψω σύνθετα έγγραφα Word με πίνακες και εικόνες σε Markdown;**  
Α: Ναι, το Aspose.Words για Java υποστηρίζει τη μετατροπή σύνθετων εγγράφων Word με πίνακες, εικόνες και διάφορα στοιχεία μορφοποίησης σε Markdown. Μπορείτε να προσαρμόσετε την έξοδο Markdown ανάλογα με την πολυπλοκότητα του εγγράφου σας.

**Ε: Πώς μπορώ να διαχειριστώ εικόνες σε αρχεία Markdown;**  
Α: Για να συμπεριλάβετε εικόνες σε αρχεία Markdown, ορίστε τη διαδρομή του φακέλου εικόνων χρησιμοποιώντας τη μέθοδο `setImagesFolder` στο `MarkdownSaveOptions`. Βεβαιωθείτε ότι τα αρχεία εικόνας αποθηκεύονται στον καθορισμένο φάκελο, και το Aspose.Words for Java θα διαχειριστεί τις αναφορές εικόνων αναλόγως.

**Ε: Υπάρχει δοκιμαστική έκδοση του Aspose.Words για Java;**  
Α: Ναι, μπορείτε να αποκτήσετε μια δοκιμαστική έκδοση του Aspose.Words για Java από την ιστοσελίδα της Aspose. Η δοκιμαστική έκδοση σας επιτρέπει να αξιολογήσετε τις δυνατότητες της βιβλιοθήκης πριν αγοράσετε άδεια.

**Ε: Πού μπορώ να βρω περισσότερα παραδείγματα και τεκμηρίωση;**  
Α: Για περισσότερα παραδείγματα, τεκμηρίωση και λεπτομερείς πληροφορίες σχετικά με το Aspose.Words για Java, επισκεφθείτε την [τεκμηρίωση](https://reference.aspose.com/words/java/).

## Συμπέρασμα

Σε αυτόν τον οδηγό καλύψαμε όλα όσα χρειάζεστε για να **μετατρέψετε Word σε Markdown** χρησιμοποιώντας το Aspose.Words for Java: δημιουργία πηγαίου εγγράφου, **προσαρμογή ευθυγράμμισης πίνακα**, και διαχείριση εικόνων με τη σωστή διαμόρφωση φακέλου. Με αυτές τις τεχνικές μπορείτε αξιόπιστα να εξάγετε περιεχόμενο Word σε markdown για blogs, ιστοσελίδες τεκμηρίωσης ή οποιαδήποτε πλατφόρμα που καταναλώνει markdown.

---

**Τελευταία ενημέρωση:** 2026-02-24  
**Δοκιμή με:** Aspose.Words for Java 24.12 (τελευταία έκδοση τη στιγμή της συγγραφής)  
**Συγγραφέας:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}