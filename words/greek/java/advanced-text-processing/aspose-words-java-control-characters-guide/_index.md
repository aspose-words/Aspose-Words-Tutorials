---
date: '2025-11-12'
description: Μάθετε βήμα‑προς‑βήμα πώς να εισάγετε αλλαγές σελίδας, στηλοθέτες, μη‑διασπώμενα
  κενά και διατάξεις πολλαπλών στηλών χρησιμοποιώντας το Aspose.Words for Java – ενισχύστε
  την αυτοματοποίηση εγγράφων σας σήμερα.
keywords:
- how to insert control characters
- add page break java
- manage carriage return aspose
- insert non breaking space
- create multi column layout
- Aspose.Words control characters
- Java document formatting
- text layout automation
- document generation Java
- Aspose.Words API
language: el
title: Εισαγωγή χαρακτήρων ελέγχου με το Aspose.Words για Java
url: /java/advanced-text-processing/aspose-words-java-control-characters-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Εισαγωγή χαρακτήρων ελέγχου με Aspose.Words για Java

## Γιατί οι χαρακτήρες ελέγχου είναι σημαντικοί σε έγγραφα Java
Όταν δημιουργείτε τιμολόγια, αναφορές ή ενημερωτικά δελτία προγραμματιστικά, η ακριβής διάταξη του κειμένου είναι αδιαπραγμάτευτη. Οι χαρακτήρες ελέγχου όπως **page breaks**, **tabs** και **non‑breaking spaces** σας επιτρέπουν να καθορίζετε ακριβώς πού εμφανίζεται το περιεχόμενο χωρίς χειροκίνητη επεξεργασία. Σε αυτό το tutorial θα δείτε πώς να διαχειρίζεστε αυτούς τους χαρακτήρες με το Aspose.Words for Java API, ώστε τα έγγραφά σας να φαίνονται επαγγελματικά από την πρώτη δημιουργία.

**Τι θα επιτύχετε με αυτόν τον οδηγό**
1. Εισαγωγή και επαλήθευση carriage returns, line feeds και page breaks.  
2. Προσθήκη κενών, tabs και non‑breaking spaces για ευθυγράμμιση κειμένου.  
3. Δημιουργία διατάξεων πολλαπλών στηλών χρησιμοποιώντας column breaks.  
4. Εφαρμογή βέλτιστων πρακτικών απόδοσης για μεγάλα έγγραφα.

## Προαπαιτούμενα
Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε τα παρακάτω:

| Απαίτηση | Λεπτομέρειες |
|-------------|---------|
| **Aspose.Words for Java** | Έκδοση 25.3 ή νεότερη (το API είναι συμβατό με παλαιότερες εκδόσεις). |
| **JDK** | 8 ή νεότερο. |
| **IDE** | IntelliJ IDEA, Eclipse ή οποιοδήποτε Java IDE προτιμάτε. |
| **Build Tool** | Maven **ή** Gradle για διαχείριση εξαρτήσεων. |
| **License** | Προσωρινό ή αγορασμένο αρχείο άδειας Aspose.Words (`aspose.words.lic`). |

### Λίστα ελέγχου περιβάλλοντος
1. Εγκαταστήστε Maven **ή** Gradle.  
2. Προσθέστε την εξάρτηση Aspose.Words (δείτε την επόμενη ενότητα).  
3. Τοποθετήστε το αρχείο άδειας σε ασφαλή θέση και σημειώστε τη διαδρομή.

## Προσθήκη Aspose.Words στο έργο σας

### Maven
Εισάγετε το παρακάτω απόσπασμα στο `pom.xml` σας:

```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### Gradle
Προσθέστε αυτή τη γραμμή στο `build.gradle`:

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### Αρχικοποίηση άδειας
Αφού αποκτήσετε άδεια, αρχικοποιήστε την στην αρχή της εφαρμογής σας:

```java
License license = new License();
license.setLicense("path/to/aspose.words.lic");
```

> **Σημείωση:** Χωρίς άδεια η βιβλιοθήκη λειτουργεί σε λειτουργία αξιολόγησης, η οποία προσθέτει υδατογραφήματα.

## Οδηγός υλοποίησης

Θα καλύψουμε δύο βασικά χαρακτηριστικά: **διαχείριση carriage‑return** και **εισαγωγή διαφόρων χαρακτήρων ελέγχου**. Κάθε χαρακτηριστικό χωρίζεται σε αριθμημένα βήματα, και ένα σύντομο επεξηγηματικό κείμενο προηγείται κάθε μπλοκ κώδικα.

### Χαρακτηριστικό 1 – Διαχείριση Carriage Return & Page Break
Οι χαρακτήρες ελέγχου όπως `ControlChar.CR` (carriage return) και `ControlChar.PAGE_BREAK` ορίζουν τη λογική ροή ενός εγγράφου. Το παρακάτω παράδειγμα δείχνει πώς να επαληθεύσετε ότι αυτοί οι χαρακτήρες τοποθετούνται σωστά.

#### Βήμα‑βήμα

1. **Δημιουργία νέου Document και DocumentBuilder**  
   Το αντικείμενο `Document` είναι ο container για όλο το περιεχόμενο· το `DocumentBuilder` παρέχει ένα fluent API για την προσθήκη κειμένου.

   ```java
   Document doc = new Document();
   DocumentBuilder builder = new DocumentBuilder(doc);
   ```

2. **Εισαγωγή δύο απλών παραγράφων**  
   Κάθε κλήση `writeln` προσθέτει αυτόματα ένα διάλειμμα παραγράφου.

   ```java
   builder.writeln("Hello world!");
   builder.writeln("Hello again!");
   ```

3. **Δημιουργία της αναμενόμενης συμβολοσειράς με χαρακτήρες ελέγχου**  
   Χρησιμοποιούμε το `MessageFormat` για να ενσωματώσουμε τα `ControlChar.CR` και `ControlChar.PAGE_BREAK` στο αναμενόμενο κείμενο.

   ```java
   String expectedTextWithCR = MessageFormat.format("Hello world!{0}", ControlChar.CR) +
           MessageFormat.format("Hello again!{0}", ControlChar.CR) +
           ControlChar.PAGE_BREAK;
   assert doc.getText().equals(expectedTextWithCR) :
           "Text does not match expected value with control characters.";
   ```

4. **Περικοπή του κειμένου του εγγράφου και επανεπαλήθευση**  
   Η περικοπή αφαιρεί τα τελικά κενά διατηρώντας τα σκόπιμα line breaks.

   ```java
   String expectedTrimmedText = MessageFormat.format("Hello world!{0}", ControlChar.CR) + "Hello again!";
   assert doc.getText().trim().equals(expectedTrimmedText) :
           "Trimmed text does not match expected value.";
   ```

> **Αποτέλεσμα:** Οι δηλώσεις επιβεβαιώνουν ότι η εσωτερική αναπαράσταση κειμένου του εγγράφου περιέχει ακριβώς τα carriage returns και το page break που περιμένατε.

### Χαρακτηριστικό 2 – Εισαγωγή Διαφόρων Χαρακτήρων Ελέγχου
Τώρα θα εξερευνήσουμε πώς να ενσωματώσουμε κενά, tabs, line feeds, paragraph breaks και column breaks απευθείας σε ένα έγγραφο.

#### Βήμα‑βήμα

1. **Αρχικοποίηση νέου DocumentBuilder**  
   Ξεκινώντας με ένα καθαρό έγγραφο εξασφαλίζουμε ότι τα παραδείγματα είναι απομονωμένα.

   ```java
   Document doc = new Document();
   DocumentBuilder builder = new DocumentBuilder(doc);
   ```

2. **Εισαγωγή χαρακτήρων σχετικών με κενά**  

   *Χαρακτήρας κενό (`ControlChar.SPACE_CHAR`)*  
   ```java
   builder.write("Before space." + ControlChar.SPACE_CHAR + "After space.");
   ```

   *Μη‑διασπώμενο κενό (`ControlChar.NON_BREAKING_SPACE`)*  
   ```java
   builder.write("Before NBSP." + ControlChar.NON_BREAKING_SPACE + "After NBSP.");
   ```

   *Χαρακτήρας Tab (`ControlChar.TAB`)*  
   ```java
   builder.write("Before tab." + ControlChar.TAB + "After tab.");
   ```

3. **Προσθήκη line και paragraph breaks**  

   *Το line feed δημιουργεί νέα γραμμή μέσα στην ίδια παράγραφο.*  
   ```java
   // Verify that we start with a single paragraph
   Assert.assertEquals(1, doc.getFirstSection().getBody()
           .getChildNodes(NodeType.PARAGRAPH, true).getCount());

   builder.write("Before line feed." + ControlChar.LINE_FEED + "After line feed.");

   // After inserting a line feed, a second paragraph should appear
   Assert.assertEquals(2, doc.getFirstSection().getBody()
           .getChildNodes(NodeType.PARAGRAPH, true).getCount());
   ```

   *Paragraph break (`ControlChar.PARAGRAPH_BREAK`)*  
   ```java
   builder.write("Before paragraph break." + ControlChar.PARAGRAPH_BREAK + "After paragraph break.");
   Assert.assertEquals(3, doc.getFirstSection().getBody()
           .getChildNodes(NodeType.PARAGRAPH, true).getCount());
   ```

   *Section break (`ControlChar.SECTION_BREAK`)*  
   ```java
   builder.write("Before section break." + ControlChar.SECTION_BREAK + "After section break.");
   assert doc.getSections().getCount() == 1 :
           "Section count mismatch after section break.";
   ```

4. **Δημιουργία διατάξεων πολλαπλών στηλών με column break**  

   Πρώτα, προσθέστε μια δεύτερη ενότητα και ενεργοποιήστε δύο στήλες:

   ```java
   doc.appendChild(new Section(doc));
   builder.moveToSection(1);
   builder.getCurrentSection().getPageSetup().getTextColumns().setCount(2);
   ```

   Στη συνέχεια, εισάγετε ένα column break για να μετακινήσετε το περιεχόμενο από τη στήλη 1 στη στήλη 2:

   ```java
   builder.write("Text at end of column 1." + ControlChar.COLUMN_BREAK + "Text at beginning of column 2.");
   ```

> **Αποτέλεσμα:** Μετά την εκτέλεση του κώδικα, το έγγραφο περιέχει σωστά τοποθετημένα κενά, tabs, line feeds, paragraph breaks, section breaks και μια διάταξη δύο στηλών—όλα δημιουργημένα με χαρακτήρες ελέγχου του Aspose.Words.

## Πραγματικές περιπτώσεις χρήσης
| Σενάριο | Πώς οι χαρακτήρες ελέγχου βοηθούν |
|----------|-----------------------------|
| **Δημιουργία τιμολογίων** | Εξαναγκάζει page breaks μετά από ορισμένο