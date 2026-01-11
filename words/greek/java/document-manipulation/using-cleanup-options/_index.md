---
date: 2026-01-11
description: Μάθετε πώς να καθαρίζετε ένα έγγραφο Word χρησιμοποιώντας τις επιλογές
  καθαρισμού του Aspose.Words for Java, συμπεριλαμβανομένης της αφαίρεσης κενών παραγράφων,
  κενών γραμμών πίνακα και αχρησιμοποίητων πεδίων.
linktitle: Using Cleanup Options
second_title: Aspose.Words Java Document Processing API
title: Καθαρισμός εγγράφου Word χρησιμοποιώντας τις επιλογές καθαρισμού του Aspose.Words
  (Java)
url: /el/java/document-manipulation/using-cleanup-options/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Καθαρισμός Εγγράφου Word Χρησιμοποιώντας τις Επιλογές Καθαρισμού Aspose.Words (Java)

Σε αυτό το tutorial θα ανακαλύψετε πώς να **καθαρίσετε αρχεία Word** με το Aspose.Words για Java. Είτε δημιουργείτε τιμολόγια, συμβάσεις ή μαζικές αναφορές συγχώνευσης αλληλογραφίας, ανεπιθύμητες κενές παραγράφους, αχρησιμοποίητα πεδία ή κενές γραμμές πίνακα μπορούν να κάνουν το τελικό αποτέλεσμα να φαίνεται μη επαγγελματικό. Θα περάσουμε από κάθε επιλογή καθαρισμού βήμα‑βήμα, θα σας δείξουμε τον ακριβή κώδικα που χρειάζεστε και θα εξηγήσουμε *γιατί* κάθε ρύθμιση είναι σημαντική ώστε να παράγετε άψογα έγγραφα κάθε φορά.

## Γρήγορες Απαντήσεις
- **Τι σημαίνει “καθαρισμός εγγράφου Word”;** Αφαίρεση κενών παραγράφων, αχρησιμοποίητων περιοχών συγχώνευσης, κενών γραμμών πίνακα και άλλων περιττών στοιχείων μετά από μια λειτουργία συγχώνευσης αλληλογραφίας.  
- **Ποια επιλογή καθαρισμού αφαιρεί κενές παραγράφους;** `MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS`.  
- **Πώς μπορώ να διαγράψω κενές γραμμές πίνακα;** Χρησιμοποιήστε `MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS`.  
- **Μπορώ να απαλλαγώ από πεδία που δεν συμπληρώθηκαν ποτέ;** Ναι – `MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS` ή `REMOVE_EMPTY_FIELDS`.  
- **Χρειάζομαι άδεια για να εκτελέσω αυτά τα παραδείγματα;** Μια δωρεάν δοκιμή λειτουργεί για αξιολόγηση· απαιτείται εμπορική άδεια για χρήση σε παραγωγή.

## Τι Είναι το “Καθαρισμός Εγγράφου Word” στο Πλαίσιο της Συγχώνευσης Αλληλογραφίας;
Όταν εκτελείτε μια συγχώνευση αλληλογραφίας, το Aspose.Words εισάγει δεδομένα σε πεδία και περιοχές συγχώνευσης. Εάν κάποια πεδία λάβουν `null` ή κενές συμβολοσειρές, το έγγραφο μπορεί να καταλήξει με αχρησιμοποίητες παραγράφους, κενά τραπέζια ή περιοχές κράτησης θέσης. Οι **επιλογές καθαρισμού** αφαιρούν αυτόματα αυτά τα υπολείμματα, αφήνοντας ένα καθαρό, έτοιμο για εκτύπωση έγγραφο.

## Γιατί να Χρησιμοποιήσετε τις Επιλογές Καθαρισμού;
- **Επαγγελματική εμφάνιση:** Χωρίς κενές γραμμές ή ορφανά πίνακες.  
- **Μικρότερο μέγεθος αρχείου:** Η αφαίρεση αχρησιμοποίητων στοιχείων μειώνει το βάρος του εγγράφου.  
- **Απλοποιημένη επεξεργασία downstream:** Τα καθαρά έγγραφα είναι πιο εύκολο να μετατραπούν σε PDF, HTML ή άλλες μορφές.  
- **Εξοικονόμηση χρόνου:** Ρυθμίσεις μίας γραμμής αντικαθιστούν χειροκίνητα scripts μετα‑επεξεργασίας.

## Προαπαιτούμενα
- Περιβάλλον ανάπτυξης Java (JDK 8+).  
- Βιβλιοθήκη Aspose.Words για Java – κατεβάστε την από [εδώ](https://releases.aspose.com/words/java/).  
- Βασική εξοικείωση με τις έννοιες της συγχώνευσης αλληλογραφίας.

## Οδηγός Βήμα‑Βήμα

### Βήμα 1: Πώς να Αφαιρέσετε Κενές Παραγράφους (Java)
Αρχικά, θα δείξουμε πώς να αφαιρέσετε παραγράφους που δεν περιέχουν ορατό κείμενο. Αυτό είναι ιδιαίτερα χρήσιμο όταν ένα πεδίο συγχώνευσης επιστρέφει `null`.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert merge fields
FieldMergeField mergeFieldOption1 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_1");
mergeFieldOption1.setFieldName("Option_1");
builder.write(" ? ");
FieldMergeField mergeFieldOption2 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_2");
mergeFieldOption2.setFieldName("Option_2");

// Set cleanup options
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS);

// Enable cleanup of paragraphs that contain only punctuation marks
doc.getMailMerge().setCleanupParagraphsWithPunctuationMarks(true);

// Execute mail merge (both fields are null, so they become empty)
doc.getMailMerge().execute(new String[] { "Option_1", "Option_2" }, new Object[] { null, null });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.CleanupParagraphsWithPunctuationMarks.docx");
```

**Τι συμβαίνει εδώ;**  
- `REMOVE_EMPTY_PARAGRAPHS` λέει στο Aspose.Words να αφαιρέσει οποιαδήποτε παράγραφο που καταλήγει κενή μετά τη συγχώνευση.  
- Η ενεργοποίηση του `cleanupParagraphsWithPunctuationMarks` αφαιρεί επίσης παραγράφους που αποτελούνται μόνο από σημεία στίξης (π.χ., “?”).

### Βήμα 2: Πώς να Αφαιρέσετε Μη Συγχωνευμένες Περιοχές
Εάν μια περιοχή συγχώνευσης δεν έχει αντίστοιχα δεδομένα, μπορείτε να την απορρίψετε εντελώς.

```java
Document doc = new Document("Your Directory Path" + "Mail merge destination - Northwind suppliers.docx");
DataSet data = new DataSet();

// Set cleanup options to remove unused regions
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS);

// Execute mail merge with regions (the DataSet is empty)
doc.getMailMerge().executeWithRegions(data);

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveUnmergedRegions.docx");
```

**Γιατί είναι σημαντικό:**  
- Οι αχρησιμοποίητες περιοχές συχνά αφήνουν κενές ενότητες ή αχρείαστα επικεφαλίδες. Η σημαία `REMOVE_UNUSED_REGIONS` τις καθαρίζει αυτόματα.

### Βήμα 3: Πώς να Αφαιρέσετε Κενά Πεδία

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove empty fields
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_FIELDS);

// Execute mail merge with a mix of populated and empty values
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveEmptyFields.docx");
```

### Βήμα 4: Πώς να Αφαιρέσετε Αχρησιμοποίητα Πεδία

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove unused fields
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS);

// Execute mail merge
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveUnusedFields.docx");
```

### Βήμα 5: Πώς να Αφαιρέσετε Πεδία που Περιέχονται

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove containing fields
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS);

// Execute mail merge
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveContainingFields.docx");
```

### Βήμα 6: Πώς να Αφαιρέσετε Κενές Γραμμές Πίνακα

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove empty table rows
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS);

// Execute mail merge
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveEmptyTableRows.docx");
```

## Συχνά Προβλήματα & Αντιμετώπιση
- **Οι παράγραφοι δεν αφαιρούνται:** Βεβαιωθείτε ότι το `setCleanupParagraphsWithPunctuationMarks(true)` καλείται *μετά* τον ορισμό της επιλογής καθαρισμού.  
- **Οι κενές γραμμές πίνακα παραμένουν:** Επαληθεύστε ότι τα κελιά του πίνακα περιέχουν πραγματικά κενές συμβολοσειρές (όχι κενά διαστήματα).  
- **Τα αχρησιμοποίητα πεδία παραμένουν:** Ελέγξτε ξανά ότι χρησιμοποιείτε το σωστό enum (`REMOVE_UNUSED_FIELDS`) και ότι τα πεδία συγχώνευσης δεν έχουν συμπληρωθεί κατά λάθος αλλού.

## Συχνές Ερωτήσεις

**Ε: Ποια είναι η διαφορά μεταξύ `REMOVE_EMPTY_FIELDS` και `REMOVE_UNUSED_FIELDS`;**  
Α: Το `REMOVE_EMPTY_FIELDS` διαγράφει πεδία που λαμβάνουν κενή συμβολοσειρά ή `null` κατά τη συγχώνευση, ενώ το `REMOVE_UNUSED_FIELDS` αφαιρεί πεδία που δεν αναφέρθηκαν ποτέ από τη λειτουργία συγχώνευσης.

**Ε: Μπορώ να συνδυάσω πολλαπλές επιλογές καθαρισμού;**  
Α: Ναι. Η μέθοδος `setCleanupOptions` δέχεται ένα bitwise OR των τιμών του enum, επιτρέποντάς σας να καθαρίσετε παραγράφους, πίνακες και περιοχές με μία κλήση.

**Ε: Η ενεργοποίηση του `cleanupParagraphsWithPunctuationMarks` επηρεάζει το κανονικό κείμενο;**  
Α: Αφαιρεί μόνο παραγράφους που αποτελούνται αποκλειστικά από χαρακτήρες στίξης (π.χ., “?” ή “---”). Οι κανονικές προτάσεις παραμένουν αμετάβλητες.

**Ε: Είναι δυνατόν να προσαρμόσετε ποιοι χαρακτήρες στίξης θεωρούνται;**  
Α: Το τρέχον API χρησιμοποιεί ένα προκαθορισμένο σύνολο χαρακτήρων στίξης. Για προσαρμοσμένη συμπεριφορά, θα πρέπει να επεξεργαστείτε το έγγραφο μετά τη συγχώνευση.

**Ε: Λειτουργούν αυτές οι επιλογές καθαρισμού με τη μετατροπή σε PDF;**  
Α: Απόλυτα. Μόλις το έγγραφο Word καθαριστεί, μπορείτε να το μετατρέψετε σε PDF, HTML ή οποιαδήποτε άλλη υποστηριζόμενη μορφή χωρίς να μεταφερθούν τα ανεπιθύμητα στοιχεία.

## Συμπέρασμα
Τώρα έχετε ένα πλήρες σύνολο εργαλείων για **καθαρισμό αρχείων Word** κατά τη διάρκεια της συγχώνευσης αλληλογραφίας με το Aspose.Words για Java. Επιλέγοντας τις κατάλληλες `MailMergeCleanupOptions`, μπορείτε αυτόματα να αφαιρέσετε κενές παραγράφους, κενές γραμμές πίνακα, αχρησιμοποίητα πεδία και πολλά άλλα—σας αφήνοντας με ένα κομψό, έτοιμο για παραγωγή έγγραφο κάθε φορά.

---

**Τελευταία Ενημέρωση:** 2026-01-11  
**Δοκιμή Με:** Aspose.Words for Java 24.11  
**Συγγραφέας:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}