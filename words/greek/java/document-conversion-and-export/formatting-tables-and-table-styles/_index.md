---
date: 2025-11-28
description: Μάθετε πώς να αλλάζετε τα περιγράμματα των κελιών και να μορφοποιείτε
  πίνακες χρησιμοποιώντας το Aspose.Words for Java. Αυτός ο οδηγός βήμα‑βήμα καλύπτει
  τον καθορισμό περιγραμμάτων, την εφαρμογή του στυλ πρώτης στήλης, την αυτόματη προσαρμογή
  του περιεχομένου του πίνακα και την εφαρμογή στυλ πινάκων.
linktitle: How to Change Cell Borders in Tables – Aspose.Words for Java
second_title: Aspose.Words Java Document Processing API
title: Πώς να αλλάξετε τα περιγράμματα των κελιών σε πίνακες – Aspose.Words for Java
url: /el/java/document-conversion-and-export/formatting-tables-and-table-styles/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να Αλλάξετε τα Όρια των Κελιών σε Πίνακες – Aspose.Words for Java

## Εισαγωγή

Όταν πρόκειται για μορφοποίηση εγγράφων, οι πίνακες παίζουν κρίσιμο ρόλο, και η **γνώση του πώς να αλλάξετε τα όρια των κελιών** είναι απαραίτητη για τη δημιουργία καθαρών, επαγγελματικών διατάξεων. Εάν αναπτύσσετε με Java και Aspose.Words, έχετε ήδη ένα ισχυρό σύνολο εργαλείων στα χέρια σας. Σε αυτό το tutorial θα περάσουμε από τη διαδικασία μορφοποίησης πινάκων, αλλαγής ορίων κελιών, εφαρμογής του *στυλ πρώτης στήλης* και χρήσης του *auto‑fit table contents* για να κάνετε τα έγγραφά σας να φαίνονται άψογα.

## Σύντομες Απαντήσεις
- **Ποια είναι η κύρια κλάση για τη δημιουργία πινάκων;** `DocumentBuilder` δημιουργεί πίνακες και κελιά προγραμματιστικά.  
- **Πώς αλλάζω το πάχος του ορίου ενός μεμονωμένου κελιού;** Χρησιμοποιήστε `builder.getCellFormat().getBorders().getLeft().setLineWidth(value)`.  
- **Μπορώ να εφαρμόσω προεπιλεγμένο στυλ πίνακα;** Ναι – καλέστε `table.setStyleIdentifier(StyleIdentifier.YOUR_STYLE)`.  
- **Ποια μέθοδος προσαρμόζει αυτόματα έναν πίνακα στο περιεχόμενό του;** `table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)`.  
- **Χρειάζεται άδεια για παραγωγική χρήση;** Απαιτείται έγκυρη άδεια Aspose.Words για χρήση εκτός δοκιμής.

## Τι σημαίνει «πώς να αλλάξετε τα όρια των κελιών» στο Aspose.Words;

Η αλλαγή των ορίων κελιών σημαίνει προσαρμογή των οπτικών γραμμών που χωρίζουν τα κελιά—χρώμα, πλάτος και στυλ γραμμής. Το Aspose.Words παρέχει ένα πλούσιο API που σας επιτρέπει να ρυθμίσετε αυτές τις ιδιότητες σε επίπεδο πίνακα, γραμμής ή μεμονωμένου κελιού, προσφέροντας λεπτομερή έλεγχο της εμφάνισης των εγγράφων σας.

## Γιατί να χρησιμοποιήσετε το Aspose.Words for Java για το στυλ πινάκων;

- **Συνεπές αποτέλεσμα σε όλες τις πλατφόρμες** – ο ίδιος κώδικας στυλ λειτουργεί σε Windows, Linux και macOS.  
- **Χωρίς εξάρτηση από το Microsoft Word** – δημιουργήστε ή τροποποιήστε έγγραφα στο διακομιστή.  
- **Πλούσια βιβλιοθήκη στυλ** – ενσωματωμένα στυλ πινάκων (π.χ. *στυλ πρώτης στήλης*) και πλήρεις δυνατότητες auto‑fit.  

## Προαπαιτούμενα

1. **Java Development Kit (JDK) 8+** – βεβαιωθείτε ότι το `java` βρίσκεται στο PATH.  
2. **IDE** – IntelliJ IDEA, Eclipse ή οποιοσδήποτε επεξεργαστής προτιμάτε.  
3. **Aspose.Words for Java** – κατεβάστε το τελευταίο JAR από την [official site](https://releases.aspose.com/words/java/).  
4. **Βασικές γνώσεις Java** – πρέπει να μπορείτε να δημιουργήσετε ένα έργο Maven/Gradle και να προσθέσετε εξωτερικά JAR.

## Εισαγωγή Πακέτων

Για να αρχίσετε να εργάζεστε με πίνακες χρειάζεστε τις βασικές κλάσεις του Aspose.Words:

```java
import com.aspose.words.*;
```

Αυτή η μοναδική εισαγωγή σας δίνει πρόσβαση στα `Document`, `DocumentBuilder`, `Table`, `StyleIdentifier` και πολλές άλλες βοηθητικές κλάσεις.

## Πώς να Αλλάξετε τα Όρια των Κελιών

Παρακάτω θα δημιουργήσουμε έναν απλό πίνακα, θα αλλάξουμε τα συνολικά του όρια, και στη συνέχεια θα προσαρμόσουμε μεμονωμένα κελιά.

### Βήμα 1: Φόρτωση Νέου Εγγράφου

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Βήμα 2: Δημιουργία Πίνακα και Ορισμός Καθολικών Ορίων

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

### Βήμα 3: Αλλαγή Ορίων ενός Μεμονωμένου Κελιού

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
- **Καθολικά όρια** – `table.setBorders` δίνει σε όλο τον πίνακα μια μαύρη γραμμή 2 σημείων.  
- **Σκίαση κελιών** – Δείχνει πώς να χρωματίσετε μεμονωμένα κελιά (κόκκινο & πράσινο).  
- **Προσαρμοσμένα όρια κελιού** – Το τρίτο κελί λαμβάνει όρια 4 σημείων σε όλες τις πλευρές, ώστε να ξεχωρίζει.

## Εφαρμογή Στυλ Πίνακα (συμπεριλαμβανομένου του Στυλ Πρώτης Στήλης)

Τα στυλ πινάκων σας επιτρέπουν να εφαρμόζετε μια συνεπή εμφάνιση με μία κλήση. Θα δείξουμε επίσης πώς να ενεργοποιήσετε το *στυλ πρώτης στήλης* και να προσαρμόσετε αυτόματα τον πίνακα στο περιεχόμενό του.

### Βήμα 4: Δημιουργία Νέου Εγγράφου για Στυλ

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Table table = builder.startTable();
        
// We must insert at least one row first before setting any table formatting.
builder.insertCell();
```

### Βήμα 5: Εφαρμογή Προκαθορισμένου Στυλ και Ενεργοποίηση Μορφοποίησης Πρώτης Στήλης

```java
// Set the table style based on a unique style identifier.
table.setStyleIdentifier(StyleIdentifier.MEDIUM_SHADING_1_ACCENT_1);
        
// Apply which features should be formatted by the style.
table.setStyleOptions(TableStyleOptions.FIRST_COLUMN | TableStyleOptions.ROW_BANDS | TableStyleOptions.FIRST_ROW);

// Auto‑fit the table so columns shrink or expand to fit the content.
table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS);
```

### Βήμα 6: Συμπλήρωση Πίνακα με Δεδομένα

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
- **Αναγνωριστικό στυλ** – `MEDIUM_SHADING_1_ACCENT_1` δίνει στον πίνακα μια καθαρή, σκιασμένη εμφάνιση.  
- **Στυλ πρώτης στήλης** – Η επισήμανση της πρώτης στήλης βελτιώνει την αναγνωσιμότητα, ειδικά σε αναφορές.  
- **Ζώνες γραμμών** – Εναλλασσόμενα χρώματα γραμμών κάνουν τους μεγάλους πίνακες πιο ευανάγνωστους.  
- **Auto‑fit** – Εξασφαλίζει ότι το πλάτος του πίνακα προσαρμόζεται στο περιεχόμενο, αποτρέποντας την αποκοπή κειμένου.

## Συχνά Προβλήματα & Επίλυση

| Πρόβλημα | Τυπική Αιτία | Γρήγορη Διόρθωση |
|----------|--------------|-------------------|
| Τα όρια δεν εμφανίζονται | Χρήση `clearFormatting()` μετά τον ορισμό των ορίων | Ορίστε τα όρια **μετά** τον καθαρισμό μορφοποίησης, ή επαναλάβετε την εφαρμογή τους. |
| Η σκίαση αγνοείται σε συγχωνευμένα κελιά | Η σκίαση εφαρμόστηκε πριν τη συγχώνευση | Εφαρμόστε τη σκίαση **μετά** τη συγχώνευση των κελιών. |
| Το πλάτος του πίνακα υπερβαίνει τα περιθώρια της σελίδας | Δεν εφαρμόστηκε auto‑fit | Καλέστε `table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)` ή ορίστε σταθερό πλάτος. |
| Το στυλ δεν εφαρμόστηκε | Λανθασμένη τιμή `StyleIdentifier` | Επαληθεύστε ότι το αναγνωριστικό υπάρχει στην έκδοση του Aspose.Words που χρησιμοποιείτε. |

## Συχνές Ερωτήσεις

**Μ: Μπορώ να χρησιμοποιήσω προσαρμοσμένα στυλ πίνακα που δεν περιλαμβάνονται στις προεπιλεγμένες επιλογές;**  
Α: Ναι, μπορείτε να δημιουργήσετε και να εφαρμόσετε προσαρμοσμένα στυλ προγραμματιστικά. Δείτε την [Aspose.Words documentation](https://reference.aspose.com/words/java/) για λεπτομέρειες.

**Μ: Πώς μπορώ να εφαρμόσω υπό όρους μορφοποίηση σε κελιά;**  
Α: Χρησιμοποιήστε τυπική λογική Java για να ελέγξετε τις τιμές των κελιών, στη συνέχεια καλέστε τις κατάλληλες μεθόδους μορφοποίησης (π.χ. αλλαγή χρώματος φόντου εάν η τιμή υπερβαίνει ένα όριο).

**Μ: Είναι δυνατόν να μορφοποιήσω συγχωνευμένα κελιά με τον ίδιο τρόπο όπως τα κανονικά;**  
Α: Απόλυτα. Μετά τη συγχώνευση των κελιών, εφαρμόστε σκίαση ή όρια χρησιμοποιώντας τις ίδιες API `CellFormat`.

**Μ: Τι γίνεται αν χρειαστεί ο πίνακας να αλλάζει μέγεθος δυναμικά βάσει εισόδου χρήστη;**  
Α: Προσαρμόστε το πλάτος των στηλών ή καλέστε ξανά το `autoFit` μετά την εισαγωγή νέων δεδομένων για επαναϋπολογισμό της διάταξης.

**Μ: Πού μπορώ να βρω περισσότερα παραδείγματα στυλ πινάκων;**  
Α: Η επίσημη [Aspose.Words API documentation](https://reference.aspose.com/words/java/) περιέχει ένα εκτενές σύνολο δειγμάτων.

## Συμπέρασμα

Τώρα διαθέτετε ένα πλήρες σύνολο εργαλείων για **το πώς να αλλάξετε τα όρια των κελιών**, την εφαρμογή του *στυλ πρώτης στήλης* και το **auto‑fit table contents** χρησιμοποιώντας το Aspose.Words for Java. Με την κατάκτηση αυτών των τεχνικών μπορείτε να παράγετε έγγραφα που είναι τόσο πλούσια σε δεδομένα όσο και οπτικά ελκυστικά—ιδανικά για αναφορές, τιμολόγια και κάθε άλλο επιχειρηματικό αποτέλεσμα.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Τελευταία Ενημέρωση:** 2025-11-28  
**Δοκιμασμένο με:** Aspose.Words for Java 24.12 (latest at time of writing)  
**Συγγραφέας:** Aspose