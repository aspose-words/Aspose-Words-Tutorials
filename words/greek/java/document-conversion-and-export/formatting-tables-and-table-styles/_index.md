---
date: 2026-10-17
description: Μάθετε πώς να αλλάξετε τα borders σε table cells με Aspose.Words for
  Java, συμπεριλαμβανομένου του setting cell border styles, του applying first column
  style και του auto‑fit table contents.
keywords:
- how to change borders
- apply first column style
- Aspose.Words table styling
- Java document processing
lastmod: 2026-10-17
linktitle: Πώς να αλλάξετε τα borders σε table cells χρησιμοποιώντας Aspose.Words
  for Java
og_description: Πώς να αλλάξετε τα borders σε table cells χρησιμοποιώντας Aspose.Words
  for Java. Αυτός ο οδηγός σας δείχνει πώς να set cell border thickness, να apply
  first column style και να auto‑fit tables για επαγγελματικά έγγραφα.
og_image_alt: Screenshot of a Java table with customized cell borders using Aspose.Words
og_title: Πώς να αλλάξετε τα borders σε table cells – Aspose.Words for Java
schemas:
- author: Aspose
  dateModified: '2026-10-17'
  description: Learn how to change borders in table cells with Aspose.Words for Java,
    including setting cell border styles, applying first column style, and auto‑fit
    table contents.
  headline: How to change borders in table cells using Aspose.Words for Java
  type: TechArticle
- description: Learn how to change borders in table cells with Aspose.Words for Java,
    including setting cell border styles, applying first column style, and auto‑fit
    table contents.
  name: How to change borders in table cells using Aspose.Words for Java
  steps:
  - name: '**Java Development Kit (JDK) 8+** – ensure `java` is on your PATH.'
    text: '**Java Development Kit (JDK) 8+** – ensure `java` is on your PATH.'
  - name: '**IDE** – IntelliJ IDEA, Eclipse, or any editor you prefer.'
    text: '**IDE** – IntelliJ IDEA, Eclipse, or any editor you prefer.'
  - name: '**Aspose.Words for Java** – download the latest JAR from the [official
      site](https://releases.aspose.com/words/java/).'
    text: '**Aspose.Words for Java** – download the latest JAR from the [official
      site](https://releases.aspose.com/words/java/).'
  - name: '**Basic Java knowledge** – you should be comfortable creating a Maven/Gradle
      project and adding external JARs.'
    text: '**Basic Java knowledge** – you should be comfortable creating a Maven/Gradle
      project and adding external JARs.'
  type: HowTo
- questions:
  - answer: Yes, you can create and apply custom styles programmatically. See the
      [Aspose.Words documentation](https://reference.aspose.com/words/java/) for details.
    question: Can I use custom table styles not included in the default options?
  - answer: Use standard Java logic to inspect cell values, then call the appropriate
      formatting methods (e.g., change background colour if a value exceeds a threshold).
    question: How can I apply conditional formatting to cells?
  - answer: Absolutely. After merging cells, apply shading or borders using the same
      `CellFormat` APIs.
    question: Is it possible to format merged cells the same way as regular cells?
  - answer: Adjust column widths or call `autoFit` again after inserting new data
      to recalculate the layout.
    question: What if I need the table to resize dynamically based on user input?
  - answer: The official [Aspose.Words API documentation](https://reference.aspose.com/words/java/)
      contains a comprehensive set of samples.
    question: Where can I find more examples of table styling?
  type: FAQPage
second_title: Aspose.Words Java Document Processing API
tags:
- Aspose.Words
- Java tables
- document formatting
- border styling
title: Πώς να αλλάξετε τα borders σε table cells χρησιμοποιώντας Aspose.Words for
  Java
url: /el/java/document-conversion-and-export/formatting-tables-and-table-styles/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να αλλάξετε τα περιγράμματα στα κελιά πίνακα χρησιμοποιώντας το Aspose.Words για Java

## Εισαγωγή

Όταν χρειάζεται να παρουσιάσετε δεδομένα με καθαρή, επαγγελματική διάταξη, η **αλλαγή περιγραμμάτων κελιών** είναι μία από τις πρώτες οπτικές προσαρμογές που θα εφαρμόσετε. Στην Java, το Aspose.Words σας παρέχει ένα πλήρες API που σας επιτρέπει να μορφοποιείτε πίνακες, να ρυθμίζετε τα περιγράμματα μεμονωμένων κελιών, να ενεργοποιείτε το στυλ πρώτης στήλης και να προσαρμόζετε αυτόματα το περιεχόμενο ώστε ο πίνακας να μην υπερβαίνει τη σελίδα. Αυτό το tutorial σας οδηγεί βήμα‑βήμα, από τη δημιουργία ενός εγγράφου μέχρι τη λεπτομερή ρύθμιση κάθε περιγράμματος, και δείχνει γιατί αυτές οι δυνατότητες είναι σημαντικές σε πραγματικές αναφορές και τιμολόγια.

## Γρήγορες απαντήσεις

Η κλάση `DocumentBuilder` χρησιμοποιείται για την προγραμματιστική δημιουργία εγγράφων και πινάκων.  

- **Ποια είναι η κύρια κλάση για τη δημιουργία πινάκων;** `DocumentBuilder` δημιουργεί πίνακες και κελιά προγραμματιστικά.  
- **Πώς αλλάζω το πάχος του περιγράμματος ενός μόνο κελιού;** Χρησιμοποιήστε `builder.getCellFormat().getBorders().getLeft().setLineWidth(value)`.  
- **Μπορώ να εφαρμόσω προεπιλεγμένο στυλ πίνακα;** Ναι – καλέστε `table.setStyleIdentifier(StyleIdentifier.YOUR_STYLE)`.  
- **Ποια μέθοδος προσαρμόζει αυτόματα έναν πίνακα στο περιεχόμενό του;** `table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)`.  
- **Χρειάζομαι άδεια για παραγωγή;** Απαιτείται έγκυρη άδεια Aspose.Words για χρήση εκτός δοκιμής.

## Τι σημαίνει «πώς να αλλάξετε τα περιγράμματα κελιών» στο Aspose.Words;

Η αλλαγή των περιγραμμάτων κελιών σημαίνει προσαρμογή των οπτικών γραμμών που χωρίζουν τα κελιά—χρώμα, πλάτος και στυλ γραμμής. Το Aspose.Words για Java εκθέτει ένα λεπτομερές API που σας επιτρέπει να ορίσετε αυτές τις ιδιότητες σε επίπεδο πίνακα, γραμμής ή μεμονωμένου κελιού, παρέχοντάς σας ακριβή έλεγχο στην εμφάνιση των εγγράφων σας.

## Γιατί να χρησιμοποιήσετε το Aspose.Words για Java για τη μορφοποίηση πινάκων;

Το Aspose.Words υποστηρίζει **πάνω από 35 μορφές εισόδου και εξόδου** (DOCX, PDF, HTML, ODT κ.λπ.) και μπορεί να επεξεργαστεί **έγγραφα 500 σελίδων σε λιγότερο από 3 δευτερόλεπτα** σε τυπικό εξοπλισμό διακομιστή χωρίς να απαιτείται Microsoft Word. Η βιβλιοθήκη λειτουργεί σταθερά σε Windows, Linux και macOS, επιτρέποντάς σας να δημιουργείτε ή να τροποποιείτε έγγραφα στο διακομιστή, να εφαρμόζετε ενσωματωμένα στυλ πινάκων όπως το *στυλ πρώτης στήλης*, και να προσαρμόζετε αυτόματα τους πίνακες στο περιεχόμενο με μία κλήση μεθόδου.

## Προαπαιτούμενα

1. **Java Development Kit (JDK) 8+** – βεβαιωθείτε ότι το `java` βρίσκεται στο PATH σας.  
2. **IDE** – IntelliJ IDEA, Eclipse ή οποιονδήποτε επεξεργαστή προτιμάτε.  
3. **Aspose.Words for Java** – κατεβάστε το τελευταίο JAR από την [επίσημη ιστοσελίδα](https://releases.aspose.com/words/java/).  
4. **Βασικές γνώσεις Java** – θα πρέπει να είστε άνετοι με τη δημιουργία έργου Maven/Gradle και την προσθήκη εξωτερικών JAR.

## Εισαγωγή πακέτων

Οι κλάσεις `Document`, `DocumentBuilder`, `Table`, `StyleIdentifier` και οι σχετικές ζουν στον χώρο ονομάτων `com.aspose.words`. Η εισαγωγή αυτού του μοναδικού πακέτου σας δίνει πρόσβαση στο πλήρες σύνολο εργαλείων μορφοποίησης πινάκων. Η κλάση `DocumentBuilder` παρέχει μεθόδους για τη δημιουργία και τροποποίηση ενός εγγράφου προγραμματιστικά.

```java
import com.aspose.words.*;
```

## Πώς να αλλάξετε τα περιγράμματα κελιών

Παρακάτω βρίσκεται ένας σύντομος, βήμα‑βήμα οδηγός που δημιουργεί έναν πίνακα, εφαρμόζει ένα γενικό περίγραμμα και στη συνέχεια προσαρμόζει τις άκρες ενός μόνο κελιού.

### Άμεση απάντηση
Ένα `Document` αντιπροσωπεύει το αρχείο Word, ενώ το `DocumentBuilder` δημιουργεί περιεχόμενο όπως πίνακες. Φορτώστε ένα νέο `Document`, εισάγετε έναν `Table` με το `DocumentBuilder`, ορίστε ένα μαύρο περίγραμμα 2 σημείων για ολόκληρο τον πίνακα και, στη συνέχεια, αυξήστε τα αριστερά, δεξιά, πάνω και κάτω περιγράμματα του τρίτου κελιού σε 4 σημεία. Αυτή η προσέγγιση σας επιτρέπει να τονίσετε οποιοδήποτε κελί διατηρώντας το υπόλοιπο του πίνακα ομοιόμορφα μορφοποιημένο.

### Βήμα 1: φόρτωση νέου εγγράφου

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Βήμα 2: δημιουργία του πίνακα και ορισμός γενικών περιγραμμάτων

```java
Table table = builder.startTable();
builder.insertCell();

// Set the borders for the entire table.
table.setBorders(LineStyle.SINGLE, 2.0, Color.BLACK);
        
// Set the cell shading for this cell.
builder.getCellFormat().getShading().setBackgroundPatternColor(Color.RED);
builder.writeln("Cell #1");

builder.insertCell();
        
// Specify a different cell shading for the second cell.
builder.getCellFormat().getShading().setBackgroundPatternColor(Color.GREEN);
builder.writeln("Cell #2");

builder.endRow();
```

### Βήμα 3: αλλαγή περιγραμμάτων ενός μόνο κελιού

```java
// Clear the cell formatting from previous operations.
builder.getCellFormat().clearFormatting();

builder.insertCell();

// Create larger borders for the first cell of this row.
builder.getCellFormat().getBorders().getLeft().setLineWidth(4.0);
builder.getCellFormat().getBorders().getRight().setLineWidth(4.0);
builder.getCellFormat().getBorders().getTop().setLineWidth(4.0);
builder.getCellFormat().getBorders().getBottom().setLineWidth(4.0);
builder.writeln("Cell #3");

builder.insertCell();
builder.getCellFormat().clearFormatting();
builder.writeln("Cell #4");
        
doc.save("FormatTableAndCellWithDifferentBorders.docx");
```

#### Τι κάνει ο κώδικας
- **Γενικά περιγράμματα** – το `table.setBorders` δίνει σε ολόκληρο τον πίνακα μια μαύρη γραμμή 2 σημείων.  
- **Σκίαση κελιών** – Δείχνει πώς να χρωματίσετε μεμονωμένα κελιά (κόκκινο & πράσινο).  
- **Προσαρμοσμένα περιγράμματα κελιών** – Το τρίτο κελί λαμβάνει περίγραμμα 4 σημείων σε όλες τις πλευρές, καθιστώντας το πιο εμφανές.

## Εφαρμογή στυλ πινάκων (συμπεριλαμβανομένου του στυλ πρώτης στήλης)

Τα στυλ πινάκων σας επιτρέπουν να εφαρμόζετε μια συνεπή εμφάνιση με μία κλήση. Θα ενεργοποιήσουμε επίσης το *στυλ πρώτης στήλης* και θα προσαρμόσουμε αυτόματα τον πίνακα στο περιεχόμενό του.

### Άμεση απάντηση
Το `StyleIdentifier` απαριθμεί τα ενσωματωμένα στυλ πινάκων, και το `AutoFitBehavior` ελέγχει πώς ένας πίνακας προσαρμόζεται στο περιεχόμενό του. Δημιουργήστε ένα νέο `Document`, δημιουργήστε έναν `Table`, ορίστε το `StyleIdentifier` του σε `MEDIUM_SHADING_1_ACCENT_1`, ενεργοποιήστε το `FirstColumn` και το `RowBands`, και, στη συνέχεια, καλέστε `autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)` ώστε οι στήλες να συρρικνώνονται ή να επεκτείνονται αυτόματα ώστε να ταιριάζουν με τα εισαχθέντα δεδομένα.

### Βήμα 4: δημιουργία νέου εγγράφου για μορφοποίηση

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Table table = builder.startTable();
        
// We must insert at least one row first before setting any table formatting.
builder.insertCell();
```

### Βήμα 5: εφαρμογή προεπιλεγμένου στυλ και ενεργοποίηση μορφοποίησης πρώτης στήλης

```java
// Set the table style based on a unique style identifier.
table.setStyleIdentifier(StyleIdentifier.MEDIUM_SHADING_1_ACCENT_1);
        
// Apply which features should be formatted by the style.
table.setStyleOptions(TableStyleOptions.FIRST_COLUMN | TableStyleOptions.ROW_BANDS | TableStyleOptions.FIRST_ROW);

// Auto‑fit the table so columns shrink or expand to fit the content.
table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS);
```

### Βήμα 6: συμπλήρωση του πίνακα με δεδομένα

```java
builder.writeln("Item");
builder.getCellFormat().setRightPadding(40.0);
builder.insertCell();
builder.writeln("Quantity (kg)");
builder.endRow();

builder.insertCell();
builder.writeln("Apples");
builder.insertCell();
builder.writeln("20");
builder.endRow();

builder.insertCell();
builder.writeln("Bananas");
builder.insertCell();
builder.writeln("40");
builder.endRow();

builder.insertCell();
builder.writeln("Carrots");
builder.insertCell();
builder.writeln("50");
builder.endRow();

doc.save("BuildTableWithStyle.docx");
```

#### Γιατί είναι σημαντικό
- **Αναγνωριστικό στυλ** – το `MEDIUM_SHADING_1_ACCENT_1` δίνει στον πίνακα μια καθαρή, σκιασμένη εμφάνιση.  
- **Στυλ πρώτης στήλης** – Η επισήμανση της πρώτης στήλης βελτιώνει την αναγνωσιμότητα, ειδικά σε αναφορές.  
- **Ζώνες γραμμών** – Η εναλλαγή χρωμάτων γραμμών κάνει τους μεγάλους πίνακες πιο ευανάγνωστους.  
- **Αυτόματη προσαρμογή** – Εξασφαλίζει ότι το πλάτος του πίνακα προσαρμόζεται στο περιεχόμενο, αποτρέποντας την αποκοπή κειμένου.

## Κοινά προβλήματα & αντιμετώπιση

| Πρόβλημα | Τυπική αιτία | Γρήγορη διόρθωση |
|----------|--------------|-------------------|
| Τα περιγράμματα δεν εμφανίζονται | Χρήση του `clearFormatting()` μετά τον ορισμό των περιγραμμάτων | Ορίστε τα περιγράμματα **μετά** τον καθαρισμό μορφοποίησης, ή επαναεφαρμόστε τα. |
| Η σκίαση αγνοείται σε συγχωνευμένα κελιά | Η σκίαση εφαρμόστηκε πριν τη συγχώνευση | Εφαρμόστε τη σκίαση **μετά** τη συγχώνευση των κελιών. |
| Το πλάτος του πίνακα υπερβαίνει τα περιθώρια της σελίδας | Δεν έχει εφαρμοστεί αυτόματη προσαρμογή | Καλέστε `table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)` ή ορίστε σταθερό πλάτος. |
| Το στυλ δεν εφαρμόζεται | Λανθασμένη τιμή `StyleIdentifier` | Επαληθεύστε ότι το αναγνωριστικό υπάρχει στην έκδοση του Aspose.Words που χρησιμοποιείτε. |

## Συχνές ερωτήσεις

**Ε: Μπορώ να χρησιμοποιήσω προσαρμοσμένα στυλ πινάκων που δεν περιλαμβάνονται στις προεπιλεγμένες επιλογές;**  
Α: Ναι, μπορείτε να δημιουργήσετε και να εφαρμόσετε προσαρμοσμένα στυλ προγραμματιστικά. Δείτε την [τεκμηρίωση Aspose.Words](https://reference.aspose.com/words/java/) για λεπτομέρειες.

**Ε: Πώς μπορώ να εφαρμόσω υπό όρους μορφοποίηση σε κελιά;**  
Α: Χρησιμοποιήστε τυπική λογική Java για να ελέγξετε τις τιμές των κελιών, στη συνέχεια καλέστε τις κατάλληλες μεθόδους μορφοποίησης (π.χ., αλλάξτε το χρώμα φόντου αν μια τιμή υπερβαίνει ένα όριο).

**Ε: Είναι δυνατόν να μορφοποιήσετε συγχωνευμένα κελιά με τον ίδιο τρόπο όπως τα κανονικά κελιά;**  
Α: Απόλυτα. Μετά τη συγχώνευση των κελιών, εφαρμόστε σκίαση ή περιγράμματα χρησιμοποιώντας τις ίδιες APIs `CellFormat`.

**Ε: Τι γίνεται αν χρειαστεί ο πίνακας να αλλάζει μέγεθος δυναμικά βάσει εισόδου χρήστη;**  
Α: Προσαρμόστε το πλάτος των στηλών ή καλέστε ξανά το `autoFit` μετά την εισαγωγή νέων δεδομένων για να επαναϋπολογίσετε τη διάταξη.

**Ε: Πού μπορώ να βρω περισσότερα παραδείγματα μορφοποίησης πινάκων;**  
Α: Η επίσημη [τεκμηρίωση API Aspose.Words](https://reference.aspose.com/words/java/) περιέχει ένα ολοκληρωμένο σύνολο παραδειγμάτων.

## Συμπέρασμα

Τώρα έχετε ένα πλήρες σύνολο εργαλείων για **πώς να αλλάξετε τα περιγράμματα** στα κελιά πίνακα, να εφαρμόσετε το *στυλ πρώτης στήλης* και **να προσαρμόσετε αυτόματα το περιεχόμενο του πίνακα** χρησιμοποιώντας το Aspose.Words για Java. Με την εξοικείωση με αυτές τις τεχνικές μπορείτε να παράγετε έγγραφα που είναι τόσο πλούσια σε δεδομένα όσο και οπτικά επεξεργασμένα—ιδανικά για αναφορές, τιμολόγια και οποιαδήποτε επιχειρηματικά κρίσιμη έξοδο.

---

**Τελευταία ενημέρωση:** 2026-10-17  
**Δοκιμή με:** Aspose.Words for Java 24.12 (latest at time of writing)  
**Συγγραφέας:** Aspose

## Σχετικά μαθήματα

- [Aspose.Words Java Μαθήματα Μορφοποίησης & Στυλ - Βελτιώστε τα Έγγραφά σας](/words/java/formatting-styles/)
- [Προηγμένα Περιγράμματα Εγγράφου με Aspose.Words για Java: Ένας Πλήρης Οδηγός](/words/java/headers-footers-page-setup/advanced-document-borders-aspose-words-java/)
- [Προσθήκη υδατογραφήματος σε έγγραφο χρησιμοποιώντας Aspose.Words για Java](/words/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}