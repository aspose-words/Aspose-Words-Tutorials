---
"description": "Μάθετε πώς να μετατρέπετε έγγραφα Word σε Markdown με το Aspose.Words για Java. Αυτός ο οδηγός βήμα προς βήμα καλύπτει την ευθυγράμμιση πινάκων, τον χειρισμό εικόνων και πολλά άλλα."
"linktitle": "Αποθήκευση εγγράφων ως Markdown"
"second_title": "API επεξεργασίας εγγράφων Java Aspose.Words"
"title": "Αποθήκευση εγγράφων ως Markdown στο Aspose.Words για Java"
"url": "/el/java/document-loading-and-saving/saving-documents-as-markdown/"
"weight": 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Αποθήκευση εγγράφων ως Markdown στο Aspose.Words για Java


## Εισαγωγή στην αποθήκευση εγγράφων ως Markdown στο Aspose.Words για Java

Σε αυτόν τον οδηγό βήμα προς βήμα, θα δείξουμε πώς να αποθηκεύετε έγγραφα ως Markdown χρησιμοποιώντας το Aspose.Words για Java. Το Markdown είναι μια ελαφριά γλώσσα σήμανσης που χρησιμοποιείται συνήθως για τη μορφοποίηση εγγράφων κειμένου. Με το Aspose.Words για Java, μπορείτε εύκολα να μετατρέψετε τα έγγραφά σας στο Word σε μορφή Markdown. Θα καλύψουμε διάφορες πτυχές της αποθήκευσης αρχείων Markdown, συμπεριλαμβανομένης της ευθυγράμμισης περιεχομένου πίνακα και του χειρισμού εικόνων.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε τις ακόλουθες προϋποθέσεις:

- Το Java Development Kit (JDK) είναι εγκατεστημένο στο σύστημά σας.
- Aspose.Words για βιβλιοθήκη Java. Μπορείτε να το κατεβάσετε από [εδώ](https://releases.aspose.com/words/java/).

## Βήμα 1: Δημιουργία εγγράφου Word

Ας ξεκινήσουμε δημιουργώντας ένα έγγραφο Word το οποίο αργότερα θα μετατρέψουμε σε μορφή Markdown. Μπορείτε να προσαρμόσετε αυτό το έγγραφο σύμφωνα με τις απαιτήσεις σας.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Εισαγωγή πίνακα με δύο κελιά
builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
builder.write("Cell1");

builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.write("Cell2");

// Αποθήκευση του εγγράφου ως Markdown
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
doc.save("output.md", saveOptions);
```

Σε αυτό το παράδειγμα, δημιουργούμε έναν απλό πίνακα με δύο κελιά και ορίζουμε τη στοίχιση των παραγράφων μέσα σε αυτά τα κελιά. Στη συνέχεια, αποθηκεύουμε το έγγραφο ως Markdown χρησιμοποιώντας το `MarkdownSaveOptions`.

## Βήμα 2: Προσαρμογή στοίχισης περιεχομένου πίνακα

Το Aspose.Words για Java σάς επιτρέπει να προσαρμόσετε την ευθυγράμμιση του περιεχομένου του πίνακα κατά την αποθήκευση ως Markdown. Μπορείτε να ευθυγραμμίσετε το περιεχόμενο του πίνακα αριστερά, δεξιά, στο κέντρο ή να το αφήσετε να καθορίζεται αυτόματα με βάση την πρώτη παράγραφο σε κάθε στήλη του πίνακα.

Δείτε πώς μπορείτε να προσαρμόσετε την στοίχιση περιεχομένου πίνακα:

```java
// Ορισμός της στοίχισης περιεχομένου πίνακα προς τα αριστερά
saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
doc.save("left_alignment.md", saveOptions);

// Ορισμός της στοίχισης περιεχομένου πίνακα προς τα δεξιά
saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
doc.save("right_alignment.md", saveOptions);

// Ορισμός της στοίχισης περιεχομένου πίνακα στο κέντρο
saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
doc.save("center_alignment.md", saveOptions);

// Ορισμός της στοίχισης περιεχομένου πίνακα σε αυτόματη (καθορίζεται από την πρώτη παράγραφο)
saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
doc.save("auto_alignment.md", saveOptions);
```

Αλλάζοντας το `TableContentAlignment` ιδιότητα, μπορείτε να ελέγξετε τον τρόπο ευθυγράμμισης του περιεχομένου μέσα στους πίνακες κατά τη μετατροπή σε Markdown.

## Βήμα 3: Χειρισμός εικόνων

Για να συμπεριλάβετε εικόνες στο έγγραφό σας Markdown, πρέπει να καθορίσετε τον φάκελο στον οποίο βρίσκονται οι εικόνες. Το Aspose.Words για Java σάς επιτρέπει να ορίσετε τον φάκελο εικόνων στο `MarkdownSaveOptions`.

Δείτε πώς μπορείτε να ορίσετε τον φάκελο εικόνων και να αποθηκεύσετε το έγγραφο με εικόνες:

```java
// Φόρτωση εγγράφου που περιέχει εικόνες
Document doc = new Document("document_with_images.docx");

// Ορίστε τη διαδρομή του φακέλου εικόνων
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Αποθήκευση του εγγράφου με εικόνες
doc.save("document_with_images.md", saveOptions);
```

Φροντίστε να αντικαταστήσετε `"document_with_images.docx"` με τη διαδρομή προς το έγγραφο του Word που περιέχει εικόνες και `"images_folder/"` με την πραγματική διαδρομή προς τον φάκελο όπου είναι αποθηκευμένες οι εικόνες σας.

## Πλήρης πηγαίος κώδικας για την αποθήκευση εγγράφων ως Markdown στο Aspose.Words για Java

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
	// Στοιχίζει όλες τις παραγράφους μέσα στον πίνακα.
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
	{
		saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
	}
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.LeftTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.RightTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.CenterTableContentAlignment.md", saveOptions);
	// Η ευθυγράμμιση σε αυτήν την περίπτωση θα ληφθεί από την πρώτη παράγραφο στην αντίστοιχη στήλη του πίνακα.
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

## Σύναψη

Σε αυτόν τον οδηγό, εξερευνήσαμε τον τρόπο αποθήκευσης εγγράφων ως Markdown χρησιμοποιώντας το Aspose.Words για Java. Καλύψαμε τη δημιουργία ενός εγγράφου Word, την προσαρμογή της στοίχισης περιεχομένου πίνακα και τον χειρισμό εικόνων σε αρχεία Markdown. Τώρα μπορείτε να μετατρέψετε αποτελεσματικά τα έγγραφά σας Word σε μορφή Markdown, καθιστώντας τα κατάλληλα για διάφορες πλατφόρμες δημοσίευσης και ανάγκες τεκμηρίωσης.

## Συχνές ερωτήσεις

### Πώς μπορώ να εγκαταστήσω το Aspose.Words για Java;

Το Aspose.Words για Java μπορεί να εγκατασταθεί συμπεριλαμβάνοντας τη βιβλιοθήκη στο έργο Java σας. Μπορείτε να κατεβάσετε τη βιβλιοθήκη από [εδώ](https://releases.aspose.com/words/java/) και ακολουθήστε τις οδηγίες εγκατάστασης που παρέχονται στην τεκμηρίωση.

### Μπορώ να μετατρέψω σύνθετα έγγραφα Word με πίνακες και εικόνες σε Markdown;

Ναι, το Aspose.Words για Java υποστηρίζει τη μετατροπή σύνθετων εγγράφων Word με πίνακες, εικόνες και διάφορα στοιχεία μορφοποίησης σε Markdown. Μπορείτε να προσαρμόσετε την έξοδο Markdown ανάλογα με την πολυπλοκότητα του εγγράφου σας.

### Πώς μπορώ να διαχειριστώ εικόνες σε αρχεία Markdown;

Για να συμπεριλάβετε εικόνες σε αρχεία Markdown, ορίστε τη διαδρομή του φακέλου εικόνων χρησιμοποιώντας το `setImagesFolder` μέθοδος σε `MarkdownSaveOptions`Βεβαιωθείτε ότι τα αρχεία εικόνας είναι αποθηκευμένα στον καθορισμένο φάκελο και το Aspose.Words για Java θα χειριστεί τις αναφορές εικόνας ανάλογα.

### Υπάρχει διαθέσιμη δοκιμαστική έκδοση του Aspose.Words για Java;

Ναι, μπορείτε να αποκτήσετε μια δοκιμαστική έκδοση του Aspose.Words για Java από τον ιστότοπο της Aspose. Η δοκιμαστική έκδοση σάς επιτρέπει να αξιολογήσετε τις δυνατότητες της βιβλιοθήκης πριν αγοράσετε μια άδεια χρήσης.

### Πού μπορώ να βρω περισσότερα παραδείγματα και τεκμηρίωση;

Για περισσότερα παραδείγματα, τεκμηρίωση και λεπτομερείς πληροφορίες σχετικά με το Aspose.Words για Java, επισκεφθείτε τη διεύθυνση [απόδειξη με έγγραφα](https://reference.aspose.com/words/java/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}