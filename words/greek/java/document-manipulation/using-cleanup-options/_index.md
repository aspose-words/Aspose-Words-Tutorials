---
title: Χρήση επιλογών εκκαθάρισης στο Aspose.Words για Java
linktitle: Χρήση επιλογών εκκαθάρισης
second_title: Aspose.Words Java Document Processing API
description: Βελτιώστε τη σαφήνεια του εγγράφου με το Aspose.Words for Java Cleanup Options. Μάθετε πώς να αφαιρείτε κενές παραγράφους, αχρησιμοποίητες περιοχές και πολλά άλλα.
weight: 10
url: /el/java/document-manipulation/using-cleanup-options/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Χρήση επιλογών εκκαθάρισης στο Aspose.Words για Java


## Εισαγωγή στη χρήση των επιλογών εκκαθάρισης στο Aspose.Words για Java

Σε αυτό το σεμινάριο, θα διερευνήσουμε πώς να χρησιμοποιήσετε τις επιλογές εκκαθάρισης στο Aspose.Words για Java για χειρισμό και καθαρισμό εγγράφων κατά τη διαδικασία συγχώνευσης αλληλογραφίας. Οι επιλογές εκκαθάρισης σάς επιτρέπουν να ελέγχετε διάφορες πτυχές της εκκαθάρισης εγγράφων, όπως η κατάργηση κενών παραγράφων, περιοχών που δεν χρησιμοποιούνται και πολλά άλλα.

## Προαπαιτούμενα

 Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε ενσωματωμένη τη βιβλιοθήκη Aspose.Words for Java στο έργο σας. Μπορείτε να το κατεβάσετε από[εδώ](https://releases.aspose.com/words/java/).

## Βήμα 1: Αφαίρεση κενών παραγράφων

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Εισαγάγετε πεδία συγχώνευσης
FieldMergeField mergeFieldOption1 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_1");
mergeFieldOption1.setFieldName("Option_1");
builder.write(" ? ");
FieldMergeField mergeFieldOption2 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_2");
mergeFieldOption2.setFieldName("Option_2");

// Ορίστε επιλογές καθαρισμού
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS);

// Ενεργοποιήστε τις παραγράφους καθαρισμού με σημεία στίξης
doc.getMailMerge().setCleanupParagraphsWithPunctuationMarks(true);

// Εκτέλεση συγχώνευσης αλληλογραφίας
doc.getMailMerge().execute(new String[] { "Option_1", "Option_2" }, new Object[] { null, null });

// Αποθηκεύστε το έγγραφο
doc.save("WorkingWithCleanupOptions.CleanupParagraphsWithPunctuationMarks.docx");
```

Σε αυτό το παράδειγμα, δημιουργούμε ένα νέο έγγραφο, εισάγουμε πεδία συγχώνευσης και ορίζουμε τις επιλογές εκκαθάρισης για να αφαιρέσουμε κενές παραγράφους. Επιπλέον, ενεργοποιούμε την αφαίρεση παραγράφων με σημεία στίξης. Μετά την εκτέλεση της συγχώνευσης αλληλογραφίας, το έγγραφο αποθηκεύεται με την εφαρμογή της καθορισμένης εκκαθάρισης.

## Βήμα 2: Κατάργηση μη συγχωνευμένων περιοχών

```java
Document doc = new Document("Your Directory Path" + "Mail merge destination - Northwind suppliers.docx");
DataSet data = new DataSet();

// Ορίστε επιλογές εκκαθάρισης για να αφαιρέσετε τις αχρησιμοποίητες περιοχές
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS);

// Εκτελέστε συγχώνευση αλληλογραφίας με περιοχές
doc.getMailMerge().executeWithRegions(data);

// Αποθηκεύστε το έγγραφο
doc.save("WorkingWithCleanupOptions.RemoveUnmergedRegions.docx");
```

Σε αυτό το παράδειγμα, ανοίγουμε ένα υπάρχον έγγραφο με περιοχές συγχώνευσης, ορίζουμε τις επιλογές εκκαθάρισης ώστε να καταργούν τις αχρησιμοποίητες περιοχές και, στη συνέχεια, εκτελούμε τη συγχώνευση αλληλογραφίας με κενά δεδομένα. Αυτή η διαδικασία αφαιρεί αυτόματα τις αχρησιμοποίητες περιοχές από το έγγραφο.

## Βήμα 3: Αφαίρεση κενών πεδίων

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Ορίστε επιλογές εκκαθάρισης για να αφαιρέσετε τα κενά πεδία
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_FIELDS);

// Εκτέλεση συγχώνευσης αλληλογραφίας
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Αποθηκεύστε το έγγραφο
doc.save("WorkingWithCleanupOptions.RemoveEmptyFields.docx");
```

Σε αυτό το παράδειγμα, ανοίγουμε ένα έγγραφο με πεδία συγχώνευσης, ορίζουμε τις επιλογές εκκαθάρισης ώστε να αφαιρούν τα κενά πεδία και εκτελούμε τη συγχώνευση αλληλογραφίας με δεδομένα. Μετά τη συγχώνευση, τυχόν κενά πεδία θα αφαιρεθούν από το έγγραφο.

## Βήμα 4: Αφαίρεση αχρησιμοποίητων πεδίων

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Ορίστε επιλογές εκκαθάρισης για να αφαιρέσετε τα αχρησιμοποίητα πεδία
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS);

// Εκτέλεση συγχώνευσης αλληλογραφίας
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Αποθηκεύστε το έγγραφο
doc.save("WorkingWithCleanupOptions.RemoveUnusedFields.docx");
```

Σε αυτό το παράδειγμα, ανοίγουμε ένα έγγραφο με πεδία συγχώνευσης, ορίζουμε τις επιλογές εκκαθάρισης ώστε να αφαιρούν τα αχρησιμοποίητα πεδία και εκτελούμε τη συγχώνευση αλληλογραφίας με δεδομένα. Μετά τη συγχώνευση, τυχόν αχρησιμοποίητα πεδία θα αφαιρεθούν από το έγγραφο.

## Βήμα 5: Αφαίρεση πεδίων που περιέχουν

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Ορίστε τις επιλογές εκκαθάρισης για να αφαιρέσετε τα πεδία που περιέχουν
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS);

// Εκτέλεση συγχώνευσης αλληλογραφίας
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Αποθηκεύστε το έγγραφο
doc.save("WorkingWithCleanupOptions.RemoveContainingFields.docx");
```

Σε αυτό το παράδειγμα, ανοίγουμε ένα έγγραφο με πεδία συγχώνευσης, ορίζουμε τις επιλογές εκκαθάρισης να καταργούν τα πεδία που περιέχουν και εκτελούμε τη συγχώνευση αλληλογραφίας με δεδομένα. Μετά τη συγχώνευση, τα ίδια τα πεδία θα αφαιρεθούν από το έγγραφο.

## Βήμα 6: Αφαίρεση κενών σειρών πίνακα

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Ορίστε επιλογές εκκαθάρισης για να αφαιρέσετε κενές σειρές πίνακα
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS);

// Εκτέλεση συγχώνευσης αλληλογραφίας
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Αποθηκεύστε το έγγραφο
doc.save("WorkingWithCleanupOptions.RemoveEmptyTableRows.docx");
```

Σε αυτό το παράδειγμα, ανοίγουμε ένα έγγραφο με πίνακα και συγχωνεύουμε πεδία, ορίζουμε τις επιλογές εκκαθάρισης για να αφαιρέσουμε κενές σειρές πίνακα και εκτελούμε τη συγχώνευση αλληλογραφίας με δεδομένα. Μετά τη συγχώνευση, τυχόν κενές σειρές πίνακα θα αφαιρεθούν από το έγγραφο.

## Σύναψη

Σε αυτό το σεμινάριο, μάθατε πώς να χρησιμοποιείτε τις επιλογές εκκαθάρισης στο Aspose.Words για Java για χειρισμό και καθαρισμό εγγράφων κατά τη διαδικασία συγχώνευσης αλληλογραφίας. Αυτές οι επιλογές παρέχουν λεπτομερή έλεγχο του καθαρισμού εγγράφων, επιτρέποντάς σας να δημιουργείτε γυαλισμένα και προσαρμοσμένα έγγραφα με ευκολία.

## Συχνές ερωτήσεις

### Ποιες είναι οι επιλογές εκκαθάρισης στο Aspose.Words για Java;

Οι επιλογές εκκαθάρισης στο Aspose.Words για Java είναι ρυθμίσεις που σας επιτρέπουν να ελέγχετε διάφορες πτυχές της εκκαθάρισης εγγράφων κατά τη διαδικασία συγχώνευσης αλληλογραφίας. Σας δίνουν τη δυνατότητα να αφαιρέσετε περιττά στοιχεία, όπως κενές παραγράφους, αχρησιμοποίητες περιοχές και άλλα, διασφαλίζοντας ότι το τελικό έγγραφό σας είναι καλά δομημένο και γυαλισμένο.

### Πώς μπορώ να αφαιρέσω κενές παραγράφους από το έγγραφό μου;

 Για να αφαιρέσετε κενές παραγράφους από το έγγραφό σας χρησιμοποιώντας το Aspose.Words για Java, μπορείτε να ορίσετε το`MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS` επιλογή σε αληθινό. Αυτό θα εξαλείψει αυτόματα τις παραγράφους που δεν έχουν περιεχόμενο, με αποτέλεσμα ένα πιο καθαρό έγγραφο.

###  Ποιος είναι ο σκοπός του`REMOVE_UNUSED_REGIONS` cleanup option?

 Ο`MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS` Η επιλογή χρησιμοποιείται για την κατάργηση περιοχών σε ένα έγγραφο που δεν έχουν αντίστοιχα δεδομένα κατά τη διαδικασία συγχώνευσης αλληλογραφίας. Βοηθά να διατηρήσετε το έγγραφό σας τακτοποιημένο, εξαλείφοντας τα αχρησιμοποίητα σύμβολα κράτησης θέσης.

### Μπορώ να αφαιρέσω κενές σειρές πίνακα από ένα έγγραφο χρησιμοποιώντας το Aspose.Words για Java;

 Ναι, μπορείτε να αφαιρέσετε κενές σειρές πίνακα από ένα έγγραφο ορίζοντας το`MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS`επιλογή καθαρισμού σε αληθινό. Αυτό θα διαγράψει αυτόματα τυχόν σειρές πίνακα που δεν περιέχουν δεδομένα, διασφαλίζοντας έναν καλά δομημένο πίνακα στο έγγραφό σας.

###  Τι συμβαίνει όταν ρυθμίζω το`REMOVE_CONTAINING_FIELDS` option?

 Ρύθμιση του`MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS` Η επιλογή θα αφαιρέσει ολόκληρο το πεδίο συγχώνευσης, συμπεριλαμβανομένης της παραγράφου που περιέχει, από το έγγραφο κατά τη διαδικασία συγχώνευσης αλληλογραφίας. Αυτό είναι χρήσιμο όταν θέλετε να εξαλείψετε τα πεδία συγχώνευσης και το σχετικό κείμενο.

### Πώς μπορώ να αφαιρέσω τα αχρησιμοποίητα πεδία συγχώνευσης από το έγγραφό μου;

 Για να αφαιρέσετε τα αχρησιμοποίητα πεδία συγχώνευσης από ένα έγγραφο, μπορείτε να ορίσετε το`MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS` επιλογή σε αληθινό. Αυτό θα εξαλείψει αυτόματα τα πεδία συγχώνευσης που δεν συμπληρώνονται κατά τη συγχώνευση αλληλογραφίας, με αποτέλεσμα ένα πιο καθαρό έγγραφο.

###  Ποια είναι η διαφορά μεταξύ`REMOVE_EMPTY_FIELDS` and `REMOVE_UNUSED_FIELDS` cleanup options?

 Ο`REMOVE_EMPTY_FIELDS` Η επιλογή καταργεί τα πεδία συγχώνευσης που δεν έχουν δεδομένα ή είναι κενά κατά τη διαδικασία συγχώνευσης αλληλογραφίας. Από την άλλη πλευρά, το`REMOVE_UNUSED_FIELDS`Η επιλογή καταργεί τα πεδία συγχώνευσης που δεν συμπληρώνονται με δεδομένα κατά τη συγχώνευση. Η επιλογή μεταξύ τους εξαρτάται από το αν θέλετε να αφαιρέσετε πεδία χωρίς περιεχόμενο ή αυτά που δεν χρησιμοποιούνται στη συγκεκριμένη λειτουργία συγχώνευσης.

### Πώς μπορώ να ενεργοποιήσω την αφαίρεση παραγράφων με σημεία στίξης;

 Για να ενεργοποιήσετε την αφαίρεση παραγράφων με σημεία στίξης, μπορείτε να ορίσετε το`cleanupParagraphsWithPunctuationMarks` επιλογή true και καθορίστε τα σημεία στίξης που θα ληφθούν υπόψη για την εκκαθάριση. Αυτό σας επιτρέπει να δημιουργήσετε ένα πιο εκλεπτυσμένο έγγραφο αφαιρώντας περιττές παραγράφους μόνο με σημεία στίξης.

### Μπορώ να προσαρμόσω τις επιλογές εκκαθάρισης στο Aspose.Words για Java;

Ναι, μπορείτε να προσαρμόσετε τις επιλογές καθαρισμού σύμφωνα με τις συγκεκριμένες ανάγκες σας. Μπορείτε να επιλέξετε ποιες επιλογές εκκαθάρισης θα εφαρμόσετε και να τις διαμορφώσετε σύμφωνα με τις απαιτήσεις καθαρισμού εγγράφων σας, διασφαλίζοντας ότι το τελικό έγγραφό σας πληροί τα επιθυμητά πρότυπα.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
