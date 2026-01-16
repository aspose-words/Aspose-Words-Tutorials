---
date: 2026-01-16
description: Μάθετε πώς να επισημαίνετε τα ορθογραφικά λάθη στο Word χρησιμοποιώντας
  το Aspose.Words for Java και ανακαλύψτε πώς να ορίζετε χαρακτήρες ανά γραμμή, να
  προσαρμόζετε τις επιλογές προβολής και να καθαρίζετε τα στυλ.
linktitle: Using Document Options and Settings
second_title: Aspose.Words Java Document Processing API
title: Επισήμανση ορθογραφικών λαθών στο Word με το Aspose.Words Java
url: /el/java/document-manipulation/using-document-options-and-settings/
weight: 31
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Χρήση Επιλογών και Ρυθμίσεων Εγγράφου στο Aspose.Words for Java

## Εισαγωγή στη Χρήση Επιλογών και Ρυθμίσεων Εγγράφου στο Aspose.Words for Java

Σε αυτόν τον ολοκληρωμένο οδηγό, θα μάθετε **πώς να επισημαίνετε ορθογραφικά λάθη στο Word** χρησιμοποιώντας το Aspose.Words for Java, ενώ ταυτόχρονα θα εξοικειωθείτε με σχετικές ρυθμίσεις όπως επιλογές προβολής, διάταξη σελίδας και καθαρισμό στυλ. Είτε είστε έμπειρος προγραμματιστής είτε μόλις ξεκινάτε, τα παραδείγματα παρακάτω θα σας βοηθήσουν να δημιουργήσετε ισχυρά, ευαίσθητα σε λάθη έγγραφα που λειτουργούν σε όλες τις εκδόσεις του Word.

## Γρήγορες Απαντήσεις
- **Πώς μπορώ να επισημάνω ορθογραφικά λάθη στο Word;** Χρησιμοποιήστε `setShowSpellingErrors(true)` στο αντικείμενο `Document`.  
- **Μπορώ επίσης να εμφανίσω γραμματικά λάθη;** Ναι—καλέστε `setShowGrammaticalErrors(true)`.  
- **Ποια μέθοδος ορίζει χαρακτήρες ανά γραμμή;** `getPageSetup().setCharactersPerLine(int)`.  
- **Ποιο API βελτιστοποιεί για συγκεκριμένη έκδοση του Word;** `doc.getCompatibilityOptions().optimizeFor(MsWordVersion)`.  
- **Υπάρχει τρόπος να καθαριστούν αχρησιμοποίητα στυλ;** Χρησιμοποιήστε `CleanupOptions` με `setUnusedStyles(true)` και καλέστε `doc.cleanup(options)`.

## Πώς να επισημάνετε ορθογραφικά λάθη στο Word;

Το Aspose.Words κάνει εύκολο το άνοιγμα της επισήμανσης ορθογραφικών λαθών. Όταν το έγγραφο ανοίξει στο Microsoft Word, οι λανθασμένες λέξεις εμφανίζονται με το γνωστό κόκκινο υπογράμμιση, βοηθώντας τους τελικούς χρήστες να εντοπίζουν τα προβλήματα αμέσως.

## Πώς να ορίσετε χαρακτήρες ανά γραμμή

Ο έλεγχος του αριθμού χαρακτήρων ανά γραμμή είναι ουσιώδης για διατάξεις σταθερού πλάτους (π.χ. λίστες κώδικα ή παλαιές φόρμες). Η κλάση `PageSetup` παρέχει τη μέθοδο `setCharactersPerLine(int)` που σας επιτρέπει να ορίσετε αυτήν την τιμή με ακρίβεια.

## Πώς να εμφανίσετε γραμματικά λάθη

Πέρα από την ορθογραφία, μπορείτε επίσης να ενεργοποιήσετε την εμφάνιση γραμματικών λαθών. Αυτό είναι χρήσιμο για τη σύνταξη περιεχομένου που πρέπει να τηρεί οδηγίες στυλ ή για την ανάπτυξη εργαλείων διόρθωσης.

## Βελτιστοποίηση Εγγράφων για Συμβατότητα

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.OptimizeForMsWord.docx");
```

Ένα βασικό στοιχείο της διαχείρισης εγγράφων είναι η εξασφάλιση συμβατότητας με διαφορετικές εκδόσεις του Microsoft Word. Το Aspose.Words for Java παρέχει έναν απλό τρόπο βελτιστοποίησης εγγράφων για συγκεκριμένες εκδόσεις του Word. Στο παραπάνω παράδειγμα, βελτιστοποιούμε ένα έγγραφο για το Word 2016, εξασφαλίζοντας απρόσκοπτη συμβατότητα.

## Αναγνώριση Γραμματικών και Ορθογραφικών Λαθών

```java
@Test
public void showGrammaticalAndSpellingErrors() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    doc.setShowGrammaticalErrors(true);
    doc.setShowSpellingErrors(true);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.ShowGrammaticalAndSpellingErrors.docx");
}
```

Η ακρίβεια είναι υψίστης σημασίας όταν εργάζεστε με έγγραφα. Το Aspose.Words for Java σας επιτρέπει να επισημαίνετε γραμματικά και ορθογραφικά λάθη στα έγγραφά σας, καθιστώντας τη διόρθωση και την επεξεργασία πιο αποδοτικές.

## Καθαρισμός Αχρησιμοποίητων Στυλ και Λιστών

```java
@Test
public void cleanupUnusedStylesAndLists() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Unused styles.docx");
    // Define cleanup options
    CleanupOptions cleanupOptions = new CleanupOptions();
    cleanupOptions.setUnusedLists(false);
    cleanupOptions.setUnusedStyles(true);
    doc.cleanup(cleanupOptions);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.CleanupUnusedStylesAndLists.docx");
}
```

Η αποτελεσματική διαχείριση των στυλ και των λιστών ενός εγγράφου είναι απαραίτητη για τη διατήρηση της συνέπειας. Το Aspose.Words for Java σας επιτρέπει να καθαρίζετε αχρησιμοποίητα στυλ και λίστες, εξασφαλίζοντας μια απλή και οργανωμένη δομή εγγράφου.

## Αφαίρεση Διπλών Στυλ

```java
@Test
public void cleanupDuplicateStyle() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    // Clean duplicate styles
    CleanupOptions options = new CleanupOptions();
    options.setDuplicateStyle(true);
    doc.cleanup(options);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.CleanupDuplicateStyle.docx");
}
```

Τα διπλά στυλ μπορούν να προκαλέσουν σύγχυση και ασυνέπεια στα έγγραφά σας. Με το Aspose.Words for Java, μπορείτε εύκολα να αφαιρέσετε τα διπλά στυλ, διατηρώντας την καθαρότητα και τη συνοχή του εγγράφου.

## Προσαρμογή Επιλογών Προβολής Εγγράφου

```java
@Test
public void viewOptions() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    // Customize viewing options
    doc.getViewOptions().setViewType(ViewType.PAGE_LAYOUT);
    doc.getViewOptions().setZoomPercent(50);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.ViewOptions.docx");
}
```

Η προσαρμογή της εμπειρίας προβολής των εγγράφων είναι κρίσιμη. Το Aspose.Words for Java σας επιτρέπει να ορίσετε διάφορες επιλογές προβολής, όπως διάταξη σελίδας και ποσοστό ζουμ, για να βελτιώσετε την αναγνωσιμότητα του εγγράφου.

## Διαμόρφωση Ρυθμίσεων Σελίδας Εγγράφου

```java
@Test
public void documentPageSetup() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Document.docx");
    // Configure page setup options
    doc.getFirstSection().getPageSetup().setLayoutMode(SectionLayoutMode.GRID);
    doc.getFirstSection().getPageSetup().setCharactersPerLine(30);
    doc.getFirstSection().getPageSetup().setLinesPerPage(10);
    doc.save("Your Directory Path" + "WorkingWithDocumentOptionsAndSettings.DocumentPageSetup.docx");
}
```

Η ακριβής ρύθμιση σελίδας είναι καθοριστική για τη μορφοποίηση εγγράφων. Το Aspose.Words for Java σας δίνει τη δυνατότητα να ορίσετε λειτουργίες διάταξης, **χαρακτήρες ανά γραμμή** και γραμμές ανά σελίδα, εξασφαλίζοντας ότι τα έγγραφά σας είναι οπτικά ελκυστικά.

## Ορισμός Γλωσσών Επεξεργασίας

```java
@Test
public void addJapaneseAsEditingLanguages() throws Exception
{
    LoadOptions loadOptions = new LoadOptions();
    // Set language preferences for editing
    loadOptions.getLanguagePreferences().addEditingLanguage(EditingLanguage.JAPANESE);
    Document doc = new Document("Your Directory Path" + "No default editing language.docx", loadOptions);
    // Check the overridden editing language
    int localeIdFarEast = doc.getStyles().getDefaultFont().getLocaleIdFarEast();
    System.out.println(localeIdFarEast == (int) EditingLanguage.JAPANESE
            ? "The document either has no any FarEast language set in defaults or it was set to Japanese originally."
            : "The document default FarEast language was set to another than Japanese language originally, so it is not overridden.");
}
```

Οι γλώσσες επεξεργασίας παίζουν σημαντικό ρόλο στην επεξεργασία εγγράφων. Με το Aspose.Words for Java, μπορείτε να ορίσετε και να προσαρμόσετε τις γλώσσες επεξεργασίας ώστε να ανταποκρίνονται στις γλωσσικές ανάγκες του εγγράφου σας.

## Συμπέρασμα

Σε αυτόν τον οδηγό, εξετάσαμε τις διάφορες επιλογές και ρυθμίσεις εγγράφου που διατίθενται στο Aspose.Words for Java. Από τη βελτιστοποίηση και την εμφάνιση λαθών μέχρι τον καθαρισμό στυλ και τις επιλογές προβολής, αυτή η ισχυρή βιβλιοθήκη προσφέρει εκτενείς δυνατότητες για τη διαχείριση και προσαρμογή των εγγράφων σας.

## Συχνές Ερωτήσεις

### Πώς βελτιστοποιώ ένα έγγραφο για συγκεκριμένη έκδοση του Word;

Για να βελτιστοποιήσετε ένα έγγραφο για συγκεκριμένη έκδοση του Word, χρησιμοποιήστε τη μέθοδο `optimizeFor` και καθορίστε την επιθυμητή έκδοση. Για παράδειγμα, για βελτιστοποίηση για Word 2016:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
doc.save("Your Directory Path" + "OptimizedForWord2016.docx");
```

### Πώς μπορώ να επισημάνω γραμματικά και ορθογραφικά λάθη σε ένα έγγραφο;

Μπορείτε να ενεργοποιήσετε την εμφάνιση γραμματικών και ορθογραφικών λαθών σε ένα έγγραφο χρησιμοποιώντας τον ακόλουθο κώδικα:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.setShowGrammaticalErrors(true);
doc.setShowSpellingErrors(true);
doc.save("Your Directory Path" + "ShowErrors.docx");
```

### Ποιος είναι ο σκοπός του καθαρισμού αχρησιμοποίητων στυλ και λιστών;

Ο καθαρισμός αχρησιμοποίητων στυλ και λιστών βοηθά στη διατήρηση μιας καθαρής και οργανωμένης δομής εγγράφου. Αφαιρεί περιττά στοιχεία, βελτιώνοντας την αναγνωσιμότητα και τη συνέπεια του εγγράφου.

### Πώς μπορώ να αφαιρέσω διπλά στυλ από ένα έγγραφο;

Για να αφαιρέσετε διπλά στυλ από ένα έγγραφο, χρησιμοποιήστε τη μέθοδο `cleanup` με την επιλογή `duplicateStyle` ορισμένη σε `true`. Δείτε ένα παράδειγμα:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
CleanupOptions options = new CleanupOptions();
options.setDuplicateStyle(true);
doc.cleanup(options);
doc.save("Your Directory Path" + "CleanedDocument.docx");
```

### Πώς προσαρμόζω τις επιλογές προβολής για ένα έγγραφο;

Μπορείτε να προσαρμόσετε τις επιλογές προβολής εγγράφου χρησιμοποιώντας την κλάση `ViewOptions`. Για παράδειγμα, για να ορίσετε τον τύπο προβολής σε διάταξη σελίδας και ζουμ στο 50%:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
doc.getViewOptions().setViewType(ViewType.PAGE_LAYOUT);
doc.getViewOptions().setZoomPercent(50);
doc.save("Your Directory Path" + "CustomView.docx");
```

## Πρόσθετες Συμβουλές & Συνηθισμένα Πιθανά Σφάλματα

- **Ενεργοποιήστε και τον ορθογραφικό και τον γραμματικό έλεγχο** όταν χρειάζεστε ολοκληρωμένη διόρθωση. Η παράλειψη μιας από τις σημαίες (`setShowGrammaticalErrors` ή `setShowSpellingErrors`) μπορεί να αφήσει λάθη αθέατα.
- **Κατά τον ορισμό χαρακτήρων ανά γραμμή**, θυμηθείτε ότι η τιμή αλληλεπιδρά με τη γραμματοσειρά και τα περιθώρια της σελίδας. Δοκιμάστε με την πραγματική διάταξη του εγγράφου για να αποφύγετε απρόσμενες αλλαγές γραμμής.
- **Οι λειτουργίες καθαρισμού είναι μη αναστρέψιμες** στο αρχικό αρχείο. Πάντα εργάζεστε σε αντίγραφο ή χρησιμοποιήστε σύστημα ελέγχου εκδόσεων για να διατηρήσετε το αρχικό στυλ.
- **Οι προτιμήσεις γλώσσας επεξεργασίας** επηρεάζουν τη συμπεριφορά του ελέγχου ορθογραφίας. Αν στοχεύετε σε πολυγλωσσικά έγγραφα, προσθέστε όλες τις σχετικές γλώσσες στο `LanguagePreferences`.

---

**Τελευταία ενημέρωση:** 2026-01-16  
**Δοκιμασμένο με:** Aspose.Words for Java 24.12  
**Συγγραφέας:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}