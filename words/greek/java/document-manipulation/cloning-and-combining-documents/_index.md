---
"description": "Μάθετε πώς να κλωνοποιείτε και να συνδυάζετε έγγραφα στο Aspose.Words για Java. Οδηγός βήμα προς βήμα με παραδείγματα πηγαίου κώδικα."
"linktitle": "Κλωνοποίηση και Συνδυασμός Εγγράφων"
"second_title": "API επεξεργασίας εγγράφων Java Aspose.Words"
"title": "Κλωνοποίηση και συνδυασμός εγγράφων στο Aspose.Words για Java"
"url": "/el/java/document-manipulation/cloning-and-combining-documents/"
"weight": 27
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Κλωνοποίηση και συνδυασμός εγγράφων στο Aspose.Words για Java


## Εισαγωγή στην κλωνοποίηση και τον συνδυασμό εγγράφων στο Aspose.Words για Java

Σε αυτό το σεμινάριο, θα εξερευνήσουμε πώς να κλωνοποιήσουμε και να συνδυάσουμε έγγραφα χρησιμοποιώντας το Aspose.Words για Java. Θα καλύψουμε διάφορα σενάρια, όπως η κλωνοποίηση ενός εγγράφου, η εισαγωγή εγγράφων σε σημεία αντικατάστασης, οι σελιδοδείκτες και κατά τη διάρκεια λειτουργιών συγχώνευσης αλληλογραφίας.

## Βήμα 1: Κλωνοποίηση εγγράφου

Για να κλωνοποιήσετε ένα έγγραφο στο Aspose.Words για Java, μπορείτε να χρησιμοποιήσετε το `deepClone()` μέθοδος. Ακολουθεί ένα απλό παράδειγμα:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "CloneAndCombineDocuments.CloningDocument.docx");
```

Αυτός ο κώδικας θα δημιουργήσει ένα deep clone του αρχικού εγγράφου και θα το αποθηκεύσει ως νέο αρχείο.

## Βήμα 2: Εισαγωγή εγγράφων σε σημεία αντικατάστασης

Μπορείτε να εισαγάγετε έγγραφα σε συγκεκριμένα σημεία αντικατάστασης σε ένα άλλο έγγραφο. Δείτε πώς μπορείτε να το κάνετε:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
FindReplaceOptions options = new FindReplaceOptions();
options.setDirection(FindReplaceDirection.BACKWARD);
options.setReplacingCallback(new InsertDocumentAtReplaceHandler());
mainDoc.getRange().replace(Pattern.compile("\\[MY_DOCUMENT\\]"), "", options);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtReplace.docx");
```

Σε αυτό το παράδειγμα, χρησιμοποιούμε ένα `FindReplaceOptions` αντικείμενο για να καθορίσετε έναν χειριστή επανάκλησης για την αντικατάσταση. Το `InsertDocumentAtReplaceHandler` Η κλάση χειρίζεται τη λογική εισαγωγής.

## Βήμα 3: Εισαγωγή εγγράφων σε σελιδοδείκτες

Για να εισαγάγετε ένα έγγραφο σε έναν συγκεκριμένο σελιδοδείκτη σε ένα άλλο έγγραφο, μπορείτε να χρησιμοποιήσετε τον ακόλουθο κώδικα:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
Document subDoc = new Document("Your Directory Path" + "Document insertion 2.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("insertionPlace");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtBookmark.docx");
```

Εδώ, βρίσκουμε τον σελιδοδείκτη με βάση το όνομα και χρησιμοποιούμε το `insertDocument` μέθοδος για την εισαγωγή του περιεχομένου του `subDoc` έγγραφο στη θέση σελιδοδείκτη.

## Βήμα 4: Εισαγωγή εγγράφων κατά τη συγχώνευση αλληλογραφίας

Μπορείτε να εισαγάγετε έγγραφα κατά τη διάρκεια μιας λειτουργίας συγχώνευσης αλληλογραφίας στο Aspose.Words για Java. Δείτε πώς:

```java
Document mainDoc = new Document("Your Directory Path" + "Document insertion 1.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "Document_1" }, new Object[] { "Your Directory Path" + "Document insertion 2.docx" });
mainDoc.save("Your Directory Path" + "CloneAndCombineDocuments.InsertDocumentAtMailMerge.doc");
```

Σε αυτό το παράδειγμα, ορίζουμε μια ανάκληση συγχώνευσης πεδίων χρησιμοποιώντας το `InsertDocumentAtMailMergeHandler` κλάση για να χειριστεί την εισαγωγή του εγγράφου που καθορίζεται από το πεδίο "Έγγραφο_1".

## Σύναψη

Η κλωνοποίηση και ο συνδυασμός εγγράφων στο Aspose.Words για Java μπορεί να επιτευχθεί χρησιμοποιώντας διάφορες τεχνικές. Είτε χρειάζεται να κλωνοποιήσετε ένα έγγραφο, να εισαγάγετε περιεχόμενο σε σημεία αντικατάστασης, σελιδοδείκτες ή κατά τη συγχώνευση αλληλογραφίας, το Aspose.Words παρέχει ισχυρές λειτουργίες για τον απρόσκοπτο χειρισμό εγγράφων.

## Συχνές ερωτήσεις

### Πώς μπορώ να κλωνοποιήσω ένα έγγραφο στο Aspose.Words για Java;

Μπορείτε να κλωνοποιήσετε ένα έγγραφο στο Aspose.Words για Java χρησιμοποιώντας το `deepClone()` μέθοδος. Ακολουθεί ένα παράδειγμα:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
Document clone = doc.deepClone();
clone.save("Your Directory Path" + "ClonedDocument.docx");
```

### Πώς μπορώ να εισάγω ένα έγγραφο σε έναν σελιδοδείκτη;

Για να εισαγάγετε ένα έγγραφο σε έναν σελιδοδείκτη στο Aspose.Words για Java, μπορείτε να βρείτε τον σελιδοδείκτη με βάση το όνομα και στη συνέχεια να χρησιμοποιήσετε το `insertDocument` μέθοδος για την εισαγωγή του περιεχομένου. Ακολουθεί ένα παράδειγμα:

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
Document subDoc = new Document("Your Directory Path" + "SubDocument.docx");
Bookmark bookmark = mainDoc.getRange().getBookmarks().get("MyBookmark");
insertDocument(bookmark.getBookmarkStart().getParentNode(), subDoc);
mainDoc.save("Your Directory Path" + "CombinedDocument.docx");
```

### Πώς μπορώ να εισάγω έγγραφα κατά τη συγχώνευση αλληλογραφίας στο Aspose.Words για Java;

Μπορείτε να εισαγάγετε έγγραφα κατά τη συγχώνευση αλληλογραφίας στο Aspose.Words για Java ορίζοντας ένα πεδίο που συγχωνεύει την επανάκληση και καθορίζοντας το έγγραφο που θα εισαχθεί. Ακολουθεί ένα παράδειγμα:

```java
Document mainDoc = new Document("Your Directory Path" + "MainDocument.docx");
mainDoc.getMailMerge().setFieldMergingCallback(new InsertDocumentAtMailMergeHandler());
mainDoc.getMailMerge().execute(new String[] { "DocumentField" }, new Object[] { "Your Directory Path" + "DocumentToInsert.docx" });
mainDoc.save("Your Directory Path" + "MergedDocument.docx");
```

Σε αυτό το παράδειγμα, το `InsertDocumentAtMailMergeHandler` Η κλάση χειρίζεται τη λογική εισαγωγής για το "DocumentField" κατά τη συγχώνευση αλληλογραφίας.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}