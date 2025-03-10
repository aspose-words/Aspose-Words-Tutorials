---
title: Χρήση κεφαλίδων και υποσέλιδων στο Aspose.Words για Java
linktitle: Χρήση κεφαλίδων και υποσέλιδων
second_title: Aspose.Words Java Document Processing API
description: Μάθετε βήμα προς βήμα πώς να χρησιμοποιείτε κεφαλίδες και υποσέλιδα στο Aspose.Words για Java. Δημιουργήστε επαγγελματικά έγγραφα χωρίς κόπο.
weight: 16
url: /el/java/using-document-elements/using-headers-and-footers/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Χρήση κεφαλίδων και υποσέλιδων στο Aspose.Words για Java


Σε αυτόν τον περιεκτικό οδηγό, θα σας καθοδηγήσουμε στη διαδικασία εργασίας με κεφαλίδες και υποσέλιδα στο Aspose.Words για Java. Οι κεφαλίδες και τα υποσέλιδα είναι απαραίτητα στοιχεία στη μορφοποίηση εγγράφων και το Aspose.Words παρέχει ισχυρά εργαλεία για τη δημιουργία και την προσαρμογή τους σύμφωνα με τις ανάγκες σας.

Τώρα, ας βουτήξουμε σε καθένα από αυτά τα βήματα λεπτομερώς.

## 1. Εισαγωγή στο Aspose.Words

Το Aspose.Words είναι ένα ισχυρό Java API που σας επιτρέπει να δημιουργείτε, να χειρίζεστε και να αποδίδετε έγγραφα του Word μέσω προγραμματισμού. Παρέχει εκτεταμένες δυνατότητες για τη μορφοποίηση εγγράφων, συμπεριλαμβανομένων των κεφαλίδων και των υποσέλιδων.

## 2. Ρύθμιση του περιβάλλοντος Java σας

 Πριν ξεκινήσετε να χρησιμοποιείτε το Aspose.Words, βεβαιωθείτε ότι έχετε ρυθμίσει σωστά το περιβάλλον ανάπτυξης Java. Μπορείτε να βρείτε τις απαραίτητες οδηγίες ρύθμισης στη σελίδα τεκμηρίωσης του Aspose.Words:[Aspose.Words Java Documentation](https://reference.aspose.com/words/java/).

## 3. Δημιουργία νέου εγγράφου

Για να εργαστείτε με κεφαλίδες και υποσέλιδα, πρέπει να δημιουργήσετε ένα νέο έγγραφο χρησιμοποιώντας το Aspose.Words. Ο παρακάτω κώδικας δείχνει πώς να το κάνετε αυτό:

```java
// Κώδικας Java για τη δημιουργία νέου εγγράφου
string dataDir = "Your Document Directory";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 4. Κατανόηση της ρύθμισης σελίδας

 Η ρύθμιση της σελίδας είναι ζωτικής σημασίας για τον έλεγχο της διάταξης του εγγράφου σας. Μπορείτε να καθορίσετε διάφορες ιδιότητες που σχετίζονται με κεφαλίδες και υποσέλιδα χρησιμοποιώντας το`PageSetup` τάξη. Για παράδειγμα:

```java
// Ρύθμιση ιδιοτήτων σελίδας
Section currentSection = builder.getCurrentSection();
PageSetup pageSetup = currentSection.getPageSetup();
pageSetup.setDifferentFirstPageHeaderFooter(true);
pageSetup.setHeaderDistance(20.0);
```

## 5. Διαφορετική κεφαλίδα/υποσέλιδο πρώτης σελίδας

Το Aspose.Words σάς επιτρέπει να έχετε διαφορετικές κεφαλίδες και υποσέλιδα για την πρώτη σελίδα του εγγράφου σας. Χρήση`pageSetup.setDifferentFirstPageHeaderFooter(true);` για να ενεργοποιήσετε αυτήν τη δυνατότητα.

## 6. Εργασία με κεφαλίδες

### 6.1. Προσθήκη κειμένου στις κεφαλίδες

 Μπορείτε να προσθέσετε κείμενο στις κεφαλίδες χρησιμοποιώντας το`DocumentBuilder`. Εδώ είναι ένα παράδειγμα:

```java
// Προσθήκη κειμένου στην κεφαλίδα της πρώτης σελίδας
builder.moveToHeaderFooter(HeaderFooterType.HEADER_FIRST);
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.getFont().setName("Arial");
builder.getFont().setBold(true);
builder.getFont().setSize(14.0);
builder.write("Aspose.Words Header/Footer Creation Primer - Title Page.");
```

### 6.2. Εισαγωγή εικόνων σε κεφαλίδες

 Για να εισαγάγετε εικόνες σε κεφαλίδες, μπορείτε να χρησιμοποιήσετε το`insertImage` μέθοδος. Εδώ είναι ένα παράδειγμα:

```java
// Εισαγωγή εικόνας στην κεφαλίδα
builder.insertImage(getImagesDir() + "Graphics Interchange Format.gif", RelativeHorizontalPosition.PAGE, 10.0,
    RelativeVerticalPosition.PAGE, 10.0, 50.0, 50.0, WrapType.THROUGH);
```

### 6.3. Προσαρμογή στυλ κεφαλίδων

Μπορείτε να προσαρμόσετε τα στυλ κεφαλίδας ορίζοντας διάφορες ιδιότητες όπως γραμματοσειρά, στοίχιση και άλλα, όπως φαίνεται στα παραπάνω παραδείγματα.

## 7. Εργασία με υποσέλιδα

### 7.1. Προσθήκη κειμένου στα υποσέλιδα

 Παρόμοια με τις κεφαλίδες, μπορείτε να προσθέσετε κείμενο στα υποσέλιδα χρησιμοποιώντας το`DocumentBuilder`. Εδώ είναι ένα παράδειγμα:

```java
// Προσθήκη κειμένου στο κύριο υποσέλιδο
builder.moveToHeaderFooter(HeaderFooterType.FOOTER_PRIMARY);
// Εισαγάγετε κείμενο και πεδία όπως απαιτείται
```

### 7.2. Εισαγωγή εικόνων στα υποσέλιδα

 Για να εισαγάγετε εικόνες στα υποσέλιδα, χρησιμοποιήστε το`insertImage` μέθοδο, ακριβώς όπως στις κεφαλίδες.

### 7.3. Προσαρμογή στυλ υποσέλιδου

 Προσαρμόστε τα στυλ υποσέλιδου χρησιμοποιώντας το`DocumentBuilder`παρόμοια με την προσαρμογή κεφαλίδων.

## 8. Αρίθμηση σελίδων

 Μπορείτε να συμπεριλάβετε αριθμούς σελίδων στις κεφαλίδες και τα υποσέλιδα σας χρησιμοποιώντας πεδία όπως`PAGE` και`NUMPAGES`. Αυτά τα πεδία ενημερώνονται αυτόματα καθώς προσθέτετε ή αφαιρείτε σελίδες.

## 9. Πληροφορίες πνευματικών δικαιωμάτων στα υποσέλιδα

Για να προσθέσετε πληροφορίες πνευματικών δικαιωμάτων στο υποσέλιδο του εγγράφου σας, μπορείτε να χρησιμοποιήσετε έναν πίνακα με δύο κελιά, στοιχίζοντας το ένα προς τα αριστερά και το άλλο προς τα δεξιά, όπως φαίνεται στο απόσπασμα κώδικα.

## 10. Εργασία με πολλαπλές ενότητες

Το Aspose.Words σάς επιτρέπει να εργάζεστε με πολλαπλές ενότητες σε ένα έγγραφο. Μπορείτε να ορίσετε διαφορετικές ρυθμίσεις σελίδας και κεφαλίδες/υποσέλιδα για κάθε ενότητα.

## 11. Προσανατολισμός Τοπίου

Μπορείτε να αλλάξετε τον προσανατολισμό συγκεκριμένων τμημάτων σε οριζόντια λειτουργία, εάν χρειάζεται.

## 12. Αντιγραφή Κεφαλίδων/Υποσέλιδων από Προηγούμενες Ενότητες

Η αντιγραφή κεφαλίδων και υποσέλιδων από προηγούμενες ενότητες μπορεί να εξοικονομήσει χρόνο κατά τη δημιουργία πολύπλοκων εγγράφων.

## 13. Αποθήκευση του εγγράφου σας

Αφού δημιουργήσετε και προσαρμόσετε το έγγραφό σας, μην ξεχάσετε να το αποθηκεύσετε χρησιμοποιώντας το`doc.save()` μέθοδος.

## Πλήρης Πηγαίος Κώδικας
```java
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        Section currentSection = builder.getCurrentSection();
        PageSetup pageSetup = currentSection.getPageSetup();
        // Καθορίστε εάν θέλουμε οι κεφαλίδες/υποσέλιδα της πρώτης σελίδας να διαφέρουν από άλλες σελίδες.
        // Μπορείτε επίσης να χρησιμοποιήσετε την ιδιότητα PageSetup.OddAndEvenPagesHeaderFooter για να καθορίσετε
        // διαφορετικές κεφαλίδες/υποσέλιδα για μονές και ζυγές σελίδες.
        pageSetup.setDifferentFirstPageHeaderFooter(true);
        pageSetup.setHeaderDistance(20.0);
        builder.moveToHeaderFooter(HeaderFooterType.HEADER_FIRST);
        builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
        builder.getFont().setName("Arial");
        builder.getFont().setBold(true);
        builder.getFont().setSize(14.0);
        builder.write("Aspose.Words Header/Footer Creation Primer - Title Page.");
        pageSetup.setHeaderDistance(20.0);
        builder.moveToHeaderFooter(HeaderFooterType.HEADER_PRIMARY);
        // Εισαγάγετε μια τοποθετημένη εικόνα στην επάνω/αριστερή γωνία της κεφαλίδας.
        // Η απόσταση από το επάνω/αριστερό άκρο της σελίδας έχει οριστεί σε 10 σημεία.
        builder.insertImage(getImagesDir() + "Graphics Interchange Format.gif", RelativeHorizontalPosition.PAGE, 10.0,
            RelativeVerticalPosition.PAGE, 10.0, 50.0, 50.0, WrapType.THROUGH);
        builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
        builder.write("Aspose.Words Header/Footer Creation Primer.");
        builder.moveToHeaderFooter(HeaderFooterType.FOOTER_PRIMARY);
        // Χρησιμοποιούμε έναν πίνακα με δύο κελιά για να δημιουργήσουμε ένα μέρος του κειμένου στη γραμμή (με αρίθμηση σελίδας).
        // Να ευθυγραμμιστεί αριστερά και το άλλο μέρος του κειμένου (με πνευματικά δικαιώματα) να ευθυγραμμιστεί δεξιά.
        builder.startTable();
        builder.getCellFormat().clearFormatting();
        builder.insertCell();
        builder.getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 / 3));
        // Χρησιμοποιεί τα πεδία PAGE και NUMPAGES για να υπολογίσει αυτόματα τον τρέχοντα αριθμό σελίδας και πολλές σελίδες.
        builder.write("Page ");
        builder.insertField("PAGE", "");
        builder.write(" of ");
        builder.insertField("NUMPAGES", "");
        builder.getCurrentParagraph().getParagraphFormat().setAlignment(ParagraphAlignment.LEFT);
        builder.insertCell();
        builder.getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 * 2 / 3));
        builder.write("(C) 2001 Aspose Pty Ltd. All rights reserved.");
        builder.getCurrentParagraph().getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
        builder.endRow();
        builder.endTable();
        builder.moveToDocumentEnd();
        // Κάντε μια αλλαγή σελίδας για να δημιουργήσετε μια δεύτερη σελίδα στην οποία θα εμφανίζονται οι κύριες κεφαλίδες/υποσέλιδα.
        builder.insertBreak(BreakType.PAGE_BREAK);
        builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
        currentSection = builder.getCurrentSection();
        pageSetup = currentSection.getPageSetup();
        pageSetup.setOrientation(Orientation.LANDSCAPE);
        // Αυτή η ενότητα δεν χρειάζεται διαφορετική κεφαλίδα/υποσέλιδο πρώτης σελίδας, χρειαζόμαστε μόνο μία σελίδα τίτλου στο έγγραφο,
        //και η κεφαλίδα/υποσέλιδο για αυτήν τη σελίδα έχει ήδη οριστεί στην προηγούμενη ενότητα.
        pageSetup.setDifferentFirstPageHeaderFooter(false);
        // Αυτή η ενότητα εμφανίζει κεφαλίδες/υποσέλιδα από την προηγούμενη ενότητα
        // από προεπιλογή καλέστε το currentSection.HeadersFooters.LinkToPrevious(false) για να ακυρώσετε αυτό το πλάτος σελίδας
        // είναι διαφορετικό για τη νέα ενότητα και επομένως πρέπει να ορίσουμε διαφορετικά πλάτη κελιών για έναν πίνακα υποσέλιδου.
        currentSection.getHeadersFooters().linkToPrevious(false);
        // Αν θέλουμε να χρησιμοποιήσουμε το ήδη υπάρχον σύνολο κεφαλίδας/υποσέλιδου για αυτήν την ενότητα.
        // Αλλά με κάποιες μικρές τροποποιήσεις, τότε μπορεί να είναι σκόπιμο να αντιγράψετε κεφαλίδες/υποσέλιδα
        // από την προηγούμενη ενότητα και εφαρμόζουμε τις απαραίτητες τροποποιήσεις όπου τις θέλουμε.
        copyHeadersFootersFromPreviousSection(currentSection);
        HeaderFooter primaryFooter = currentSection.getHeadersFooters().getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);
        Row row = primaryFooter.getTables().get(0).getFirstRow();
        row.getFirstCell().getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 / 3));
        row.getLastCell().getCellFormat().setPreferredWidth(PreferredWidth.fromPercent(100 * 2 / 3));
        doc.save("Your Directory Path" + "WorkingWithHeadersAndFooters.CreateHeaderFooter.docx");
```	
Πηγαίος κώδικας της μεθόδου copyHeadersFootersFromPreviousSection
```java
    /// <περίληψη>
    /// Οι κλώνοι και τα αντίγραφα κεφαλίδων/υποσέλιδων αποτελούν την προηγούμενη ενότητα στην καθορισμένη ενότητα.
    /// </summary>
    private void copyHeadersFootersFromPreviousSection(Section section)
    {
        Section previousSection = (Section)section.getPreviousSibling();
        if (previousSection == null)
            return;
        section.getHeadersFooters().clear();
        for (HeaderFooter headerFooter : (Iterable<HeaderFooter>) previousSection.getHeadersFooters())
            section.getHeadersFooters().add(headerFooter.deepClone(true));
	}
```

## Σύναψη

Σε αυτό το σεμινάριο, καλύψαμε τα βασικά της εργασίας με κεφαλίδες και υποσέλιδα στο Aspose.Words για Java. Έχετε μάθει πώς να δημιουργείτε, να προσαρμόζετε και να στυλ κεφαλίδες και υποσέλιδα, καθώς και άλλες βασικές τεχνικές μορφοποίησης εγγράφων.

 Για περισσότερες λεπτομέρειες και προηγμένες λειτουργίες, ανατρέξτε στο[Aspose.Words Java Documentation](https://reference.aspose.com/words/java/).

## Συχνές ερωτήσεις

### 1. Πώς μπορώ να προσθέσω αριθμούς σελίδων στο υποσέλιδο του εγγράφου μου;
 Μπορείτε να προσθέσετε αριθμούς σελίδων εισάγοντας το`PAGE` πεδίο στο υποσέλιδο χρησιμοποιώντας το Aspose.Words.

### 2. Είναι το Aspose.Words συμβατό με περιβάλλοντα ανάπτυξης Java;
Ναι, το Aspose.Words παρέχει υποστήριξη για ανάπτυξη Java. Βεβαιωθείτε ότι έχετε τοποθετήσει την απαραίτητη ρύθμιση.

### 3. Μπορώ να προσαρμόσω τη γραμματοσειρά και το στυλ των κεφαλίδων και των υποσέλιδων;
Οπωσδήποτε, μπορείτε να προσαρμόσετε τις γραμματοσειρές, τη στοίχιση και άλλα στυλ για να κάνετε τις κεφαλίδες και τα υποσέλιδα σας οπτικά ελκυστικά.

### 4. Είναι δυνατόν να υπάρχουν διαφορετικές κεφαλίδες για μονές και ζυγές σελίδες;
 Ναι, μπορείτε να χρησιμοποιήσετε`PageSetup.OddAndEvenPagesHeaderFooter` για να καθορίσετε διαφορετικές κεφαλίδες για μονές και ζυγές σελίδες.

### 5. Πώς μπορώ να ξεκινήσω με το Aspose.Words για Java;
 Για να ξεκινήσετε, επισκεφθείτε το[Aspose.Words Java Documentation](https://reference.aspose.com/words/java/) για ολοκληρωμένη καθοδήγηση σχετικά με τη χρήση του API.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
