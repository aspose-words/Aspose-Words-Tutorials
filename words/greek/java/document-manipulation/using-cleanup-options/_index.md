---
"description": "Βελτιώστε τη σαφήνεια του εγγράφου με τις επιλογές καθαρισμού Aspose.Words για Java. Μάθετε πώς να αφαιρείτε κενές παραγράφους, αχρησιμοποίητες περιοχές και άλλα."
"linktitle": "Χρήση επιλογών καθαρισμού"
"second_title": "API επεξεργασίας εγγράφων Java Aspose.Words"
"title": "Χρήση επιλογών καθαρισμού στο Aspose.Words για Java"
"url": "/el/java/document-manipulation/using-cleanup-options/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Χρήση επιλογών καθαρισμού στο Aspose.Words για Java


## Εισαγωγή στη χρήση των επιλογών καθαρισμού στο Aspose.Words για Java

Σε αυτό το σεμινάριο, θα εξερευνήσουμε πώς να χρησιμοποιήσετε τις επιλογές καθαρισμού στο Aspose.Words για Java για να χειριστείτε και να καθαρίσετε έγγραφα κατά τη διάρκεια της διαδικασίας συγχώνευσης αλληλογραφίας. Οι επιλογές καθαρισμού σάς επιτρέπουν να ελέγχετε διάφορες πτυχές του καθαρισμού εγγράφων, όπως την αφαίρεση κενών παραγράφων, αχρησιμοποίητων περιοχών και άλλων.

## Προαπαιτούμενα

Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε ενσωματώσει στο έργο σας τη βιβλιοθήκη Aspose.Words για Java. Μπορείτε να την κατεβάσετε από [εδώ](https://releases.aspose.com/words/java/).

## Βήμα 1: Αφαίρεση κενών παραγράφων

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Εισαγωγή πεδίων συγχώνευσης
FieldMergeField mergeFieldOption1 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_1");
mergeFieldOption1.setFieldName("Option_1");
builder.write(" ? ");
FieldMergeField mergeFieldOption2 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_2");
mergeFieldOption2.setFieldName("Option_2");

// Ορισμός επιλογών καθαρισμού
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS);

// Ενεργοποίηση παραγράφων εκκαθάρισης με σημεία στίξης
doc.getMailMerge().setCleanupParagraphsWithPunctuationMarks(true);

// Εκτέλεση συγχώνευσης αλληλογραφίας
doc.getMailMerge().execute(new String[] { "Option_1", "Option_2" }, new Object[] { null, null });

// Αποθήκευση του εγγράφου
doc.save("WorkingWithCleanupOptions.CleanupParagraphsWithPunctuationMarks.docx");
```

Σε αυτό το παράδειγμα, δημιουργούμε ένα νέο έγγραφο, εισάγουμε πεδία συγχώνευσης και ορίζουμε τις επιλογές καθαρισμού για την αφαίρεση κενών παραγράφων. Επιπλέον, ενεργοποιούμε την αφαίρεση παραγράφων με σημεία στίξης. Μετά την εκτέλεση της συγχώνευσης αλληλογραφίας, το έγγραφο αποθηκεύεται με την καθορισμένη εκκαθάριση εφαρμοσμένη.

## Βήμα 2: Αφαίρεση μη συγχωνευμένων περιοχών

```java
Document doc = new Document("Your Directory Path" + "Mail merge destination - Northwind suppliers.docx");
DataSet data = new DataSet();

// Ορίστε επιλογές καθαρισμού για να καταργήσετε τις περιοχές που δεν χρησιμοποιούνται
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS);

// Εκτέλεση συγχώνευσης αλληλογραφίας με περιοχές
doc.getMailMerge().executeWithRegions(data);

// Αποθήκευση του εγγράφου
doc.save("WorkingWithCleanupOptions.RemoveUnmergedRegions.docx");
```

Σε αυτό το παράδειγμα, ανοίγουμε ένα υπάρχον έγγραφο με περιοχές συγχώνευσης, ορίζουμε τις επιλογές καθαρισμού για την κατάργηση των αχρησιμοποίητων περιοχών και, στη συνέχεια, εκτελούμε τη συγχώνευση αλληλογραφίας με κενά δεδομένα. Αυτή η διαδικασία καταργεί αυτόματα τις αχρησιμοποίητες περιοχές από το έγγραφο.

## Βήμα 3: Αφαίρεση κενών πεδίων

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Ορίστε επιλογές καθαρισμού για να καταργήσετε κενά πεδία
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_FIELDS);

// Εκτέλεση συγχώνευσης αλληλογραφίας
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Αποθήκευση του εγγράφου
doc.save("WorkingWithCleanupOptions.RemoveEmptyFields.docx");
```

Σε αυτό το παράδειγμα, ανοίγουμε ένα έγγραφο με πεδία συγχώνευσης, ορίζουμε τις επιλογές καθαρισμού για την κατάργηση κενών πεδίων και εκτελούμε τη συγχώνευση αλληλογραφίας με δεδομένα. Μετά τη συγχώνευση, τυχόν κενά πεδία θα καταργηθούν από το έγγραφο.

## Βήμα 4: Αφαίρεση αχρησιμοποίητων πεδίων

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Ορίστε επιλογές καθαρισμού για να καταργήσετε τα αχρησιμοποίητα πεδία
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS);

// Εκτέλεση συγχώνευσης αλληλογραφίας
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Αποθήκευση του εγγράφου
doc.save("WorkingWithCleanupOptions.RemoveUnusedFields.docx");
```

Σε αυτό το παράδειγμα, ανοίγουμε ένα έγγραφο με πεδία συγχώνευσης, ορίζουμε τις επιλογές καθαρισμού για την κατάργηση των αχρησιμοποίητων πεδίων και εκτελούμε τη συγχώνευση αλληλογραφίας με δεδομένα. Μετά τη συγχώνευση, τυχόν αχρησιμοποίητα πεδία θα καταργηθούν από το έγγραφο.

## Βήμα 5: Αφαίρεση πεδίων που περιέχουν

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Ορίστε επιλογές καθαρισμού για να καταργήσετε τα πεδία που τα περιέχουν
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS);

// Εκτέλεση συγχώνευσης αλληλογραφίας
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Αποθήκευση του εγγράφου
doc.save("WorkingWithCleanupOptions.RemoveContainingFields.docx");
```

Σε αυτό το παράδειγμα, ανοίγουμε ένα έγγραφο με πεδία συγχώνευσης, ορίζουμε τις επιλογές καθαρισμού για να καταργήσουμε τα πεδία που τα περιέχουν και εκτελούμε τη συγχώνευση αλληλογραφίας με δεδομένα. Μετά τη συγχώνευση, τα ίδια τα πεδία θα καταργηθούν από το έγγραφο.

## Βήμα 6: Αφαίρεση κενών γραμμών πίνακα

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Ορισμός επιλογών καθαρισμού για την κατάργηση κενών γραμμών πίνακα
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS);

// Εκτέλεση συγχώνευσης αλληλογραφίας
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Αποθήκευση του εγγράφου
doc.save("WorkingWithCleanupOptions.RemoveEmptyTableRows.docx");
```

Σε αυτό το παράδειγμα, ανοίγουμε ένα έγγραφο με έναν πίνακα και πεδία συγχώνευσης, ορίζουμε τις επιλογές καθαρισμού για την κατάργηση κενών γραμμών πίνακα και εκτελούμε τη συγχώνευση αλληλογραφίας με δεδομένα. Μετά τη συγχώνευση, τυχόν κενές γραμμές πίνακα θα καταργηθούν από το έγγραφο.

## Σύναψη

Σε αυτό το σεμινάριο, μάθατε πώς να χρησιμοποιείτε επιλογές καθαρισμού στο Aspose.Words για Java για να χειρίζεστε και να καθαρίζετε έγγραφα κατά τη διάρκεια της διαδικασίας συγχώνευσης αλληλογραφίας. Αυτές οι επιλογές παρέχουν λεπτομερή έλεγχο στον καθαρισμό εγγράφων, επιτρέποντάς σας να δημιουργείτε εύκολα βελτιστοποιημένα και προσαρμοσμένα έγγραφα.

## Συχνές ερωτήσεις

### Ποιες είναι οι επιλογές καθαρισμού στο Aspose.Words για Java;

Οι επιλογές καθαρισμού στο Aspose.Words για Java είναι ρυθμίσεις που σας επιτρέπουν να ελέγχετε διάφορες πτυχές του καθαρισμού εγγράφων κατά τη διάρκεια της διαδικασίας συγχώνευσης αλληλογραφίας. Σας επιτρέπουν να αφαιρέσετε περιττά στοιχεία, όπως κενές παραγράφους, αχρησιμοποίητες περιοχές και άλλα, διασφαλίζοντας ότι το τελικό σας έγγραφο είναι καλά δομημένο και κομψό.

### Πώς μπορώ να αφαιρέσω κενές παραγράφους από το έγγραφό μου;

Για να αφαιρέσετε κενές παραγράφους από το έγγραφό σας χρησιμοποιώντας το Aspose.Words για Java, μπορείτε να ορίσετε το `MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS` επιλογή σε true. Αυτό θα εξαλείψει αυτόματα τις παραγράφους που δεν έχουν περιεχόμενο, με αποτέλεσμα ένα πιο καθαρό έγγραφο.

### Ποιος είναι ο σκοπός του `REMOVE_UNUSED_REGIONS` επιλογή καθαρισμού;

Ο `MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS` Η επιλογή χρησιμοποιείται για την κατάργηση περιοχών σε ένα έγγραφο που δεν έχουν αντίστοιχα δεδομένα κατά τη διάρκεια της διαδικασίας συγχώνευσης αλληλογραφίας. Βοηθά στη διατήρηση της τάξης στο έγγραφό σας, απαλλαγόμενοι από αχρησιμοποίητα σύμβολα κράτησης θέσης.

### Μπορώ να αφαιρέσω κενές γραμμές πίνακα από ένα έγγραφο χρησιμοποιώντας το Aspose.Words για Java;

Ναι, μπορείτε να αφαιρέσετε κενές γραμμές πίνακα από ένα έγγραφο ορίζοντας το `MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS` ορίστε την επιλογή καθαρισμού σε true. Αυτό θα διαγράψει αυτόματα τυχόν γραμμές πίνακα που δεν περιέχουν δεδομένα, διασφαλίζοντας έναν καλά δομημένο πίνακα στο έγγραφό σας.

### Τι συμβαίνει όταν ορίσω το `REMOVE_CONTAINING_FIELDS` επιλογή;

Ρύθμιση του `MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS` Η επιλογή θα καταργήσει ολόκληρο το πεδίο συγχώνευσης, συμπεριλαμβανομένης της παραγράφου που το περιέχει, από το έγγραφο κατά τη διάρκεια της διαδικασίας συγχώνευσης αλληλογραφίας. Αυτό είναι χρήσιμο όταν θέλετε να καταργήσετε τα πεδία συγχώνευσης και το σχετικό κείμενο.

### Πώς μπορώ να καταργήσω τα αχρησιμοποίητα πεδία συγχώνευσης από το έγγραφό μου;

Για να καταργήσετε τα αχρησιμοποίητα πεδία συγχώνευσης από ένα έγγραφο, μπορείτε να ορίσετε το `MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS` ορίστε την επιλογή σε true. Αυτό θα εξαλείψει αυτόματα τα πεδία συγχώνευσης που δεν συμπληρώνονται κατά τη συγχώνευση αλληλογραφίας, με αποτέλεσμα ένα πιο καθαρό έγγραφο.

### Ποια είναι η διαφορά μεταξύ `REMOVE_EMPTY_FIELDS` και `REMOVE_UNUSED_FIELDS` επιλογές καθαρισμού;

Ο `REMOVE_EMPTY_FIELDS` Η επιλογή καταργεί τα πεδία συγχώνευσης που δεν έχουν δεδομένα ή είναι κενά κατά τη διάρκεια της διαδικασίας συγχώνευσης αλληλογραφίας. Από την άλλη πλευρά, το `REMOVE_UNUSED_FIELDS` Η επιλογή καταργεί τα πεδία συγχώνευσης που δεν συμπληρώνονται με δεδομένα κατά τη συγχώνευση. Η επιλογή μεταξύ τους εξαρτάται από το αν θέλετε να καταργήσετε πεδία χωρίς περιεχόμενο ή εκείνα που δεν χρησιμοποιούνται στη συγκεκριμένη λειτουργία συγχώνευσης.

### Πώς μπορώ να ενεργοποιήσω την αφαίρεση παραγράφων με σημεία στίξης;

Για να ενεργοποιήσετε την αφαίρεση παραγράφων με σημεία στίξης, μπορείτε να ορίσετε το `cleanupParagraphsWithPunctuationMarks` επιλέξτε την επιλογή σε true και καθορίστε τα σημεία στίξης που θα ληφθούν υπόψη για καθαρισμό. Αυτό σας επιτρέπει να δημιουργήσετε ένα πιο εκλεπτυσμένο έγγραφο αφαιρώντας τις περιττές παραγράφους που περιέχουν μόνο σημεία στίξης.

### Μπορώ να προσαρμόσω τις επιλογές καθαρισμού στο Aspose.Words για Java;

Ναι, μπορείτε να προσαρμόσετε τις επιλογές καθαρισμού ανάλογα με τις συγκεκριμένες ανάγκες σας. Μπορείτε να επιλέξετε ποιες επιλογές καθαρισμού θα εφαρμόσετε και να τις διαμορφώσετε σύμφωνα με τις απαιτήσεις καθαρισμού του εγγράφου σας, διασφαλίζοντας ότι το τελικό σας έγγραφο πληροί τα επιθυμητά πρότυπα.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}