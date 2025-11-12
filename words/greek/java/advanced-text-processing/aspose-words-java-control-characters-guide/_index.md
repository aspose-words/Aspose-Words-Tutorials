---
date: '2025-11-12'
description: Μάθετε πώς να εισάγετε χαρακτήρες ελέγχου, να διαχειρίζεστε επιστροφές
  γραμμής και να προσθέτετε αλλαγές σελίδας ή στήλης στη Java χρησιμοποιώντας το Aspose.Words
  για ακριβή μορφοποίηση εγγράφων.
keywords:
- Aspose.Words control characters
- Java document formatting with Aspose.Words
- inserting control characters in Java
- insert control characters java
- manage carriage returns
- add page break aspose
- insert non‑breaking space
- create multi‑column layout
language: el
title: Εισαγωγή χαρακτήρων ελέγχου στη Java με το Aspose.Words
url: /java/advanced-text-processing/aspose-words-java-control-characters-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Εισαγωγή Χαρακτήρων Ελέγχου σε Java με το Aspose.Words
## Εισαγωγή
Χρειάζεστε απόλυτο έλεγχο πάνω σε αλλαγές γραμμής, tabs ή διαχωρισμούς σελίδας όταν δημιουργείτε τιμολόγια, αναφορές ή ενημερωτικά δελτία;  
Οι χαρακτήρες ελέγχου είναι τα αόρατα δομικά στοιχεία που σας επιτρέπουν να διαμορφώσετε τη διάταξη του εγγράφου προγραμματιστικά.  
Σε αυτό το tutorial θα μάθετε πώς να **εισάγετε**, **επαληθεύετε** και **διαχειρίζεστε** χαρακτήρες ελέγχου όπως επιστροφές καρτέλας, μη‑διασπώμενα διαστήματα και διαχωριστές στηλών χρησιμοποιώντας το Aspose.Words for Java API.

**Τι θα επιτύχετε:**
1. Εισαγωγή και επικύρωση επιστροφών καρτέλας, line feeds και διαχωριστών σελίδας.  
2. Προσθήκη διαστημάτων, tabs, μη‑διασπώμενων διαστημάτων και διαχωριστών στηλών για δημιουργία διατάξεων πολλαπλών στηλών.  
3. Εφαρμογή βέλτιστων πρακτικών απόδοσης για αυτοματοποίηση εγγράφων μεγάλης κλίμακας.

## Προαπαιτούμενα
Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε τα παρακάτω:

| Απαίτηση | Λεπτομέρειες |
|----------|--------------|
| **Aspose.Words for Java** | Έκδοση 25.3 ή νεότερη (το API παραμένει σταθερό σε μεταγενέστερες εκδόσεις). |
| **JDK** | Java 8 + (συνιστώνται Java 11 ή 17). |
| **IDE** | IntelliJ IDEA, Eclipse ή οποιοσδήποτε επεξεργαστής συμβατός με Java. |
| **Build tool** | Maven **ή** Gradle για διαχείριση εξαρτήσεων. |
| **License** | Ένα προσωρινό ή αγορασμένο αρχείο άδειας Aspose.Words. |

### Γρήγορος Κατάλογος Ελέγχου Περιβάλλοντος
1. Έχει εγκατασταθεί Maven **ή** Gradle.  
2. Το αρχείο άδειας είναι προσβάσιμο (π.χ., `src/main/resources/aspose.words.lic`).  
3. Το έργο έχει μεταγλωττιστεί χωρίς σφάλματα.

## Ρύθμιση του Aspose.Words
Αρχικά θα προσθέσουμε τη βιβλιοθήκη στο έργο, έπειτα θα φορτώσουμε την άδεια. Επιλέξτε το σύστημα κατασκευής που ταιριάζει στη ροή εργασίας σας.

### Maven Dependency
Προσθέστε το παρακάτω απόσπασμα στο `pom.xml` μέσα στο `<dependencies>`:

```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### Gradle Dependency
Εισάγετε αυτή τη γραμμή στο μπλοκ `dependencies` του `build.gradle`:

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### License Initialization (Java code)
```java
License license = new License();
license.setLicense("path/to/aspose.words.lic");
```

> **Σημείωση:** Αντικαταστήστε το `"path/to/aspose.words.lic"` με την πραγματική διαδρομή του αρχείου άδειας σας.

## Feature 1: Handle Carriage Returns and Page Breaks
Οι επιστροφές καρτέλας (`ControlChar.CR`) και οι διαχωριστές σελίδας (`ControlChar.PAGE_BREAK`) είναι απαραίτητες όταν χρειάζεται το κείμενο εξόδου να αντικατοπτρίζει τη οπτική διάταξη ενός εγγράφου.

### Step‑by‑Step Implementation
1. **Δημιουργήστε ένα νέο Document και DocumentBuilder.**  
2. **Γράψτε δύο παραγράφους.**  
3. **Επαληθεύστε ότι το παραγόμενο κείμενο περιέχει τους αναμενόμενους χαρακτήρες ελέγχου.**  
4. **Κόψτε το κείμενο και ελέγξτε ξανά το αποτέλεσμα.**

#### 1. Create a Document
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

#### 2. Insert Paragraphs
```java
builder.writeln("Hello world!");
builder.writeln("Hello again!");
```

#### 3. Verify Control Characters
```java
String expectedTextWithCR = MessageFormat.format("Hello world!{0}", ControlChar.CR) +
        MessageFormat.format("Hello again!{0}", ControlChar.CR) +
        ControlChar.PAGE_BREAK;
assert doc.getText().equals(expectedTextWithCR) :
        "Text does not match expected value with control characters.";
```

#### 4. Trim and Check Text
```java
String expectedTrimmedText = MessageFormat.format("Hello world!{0}", ControlChar.CR) + "Hello again!";
assert doc.getText().trim().equals(expectedTrimmedText) :
        "Trimmed text does not match expected value.";
```

**Αποτέλεσμα:** Η συμβολοσειρά `doc.getText()` περιέχει τώρα ρητά σύμβολα CR και διαχωριστή σελίδας, διασφαλίζοντας ότι τα downstream συστήματα (π.χ., εξαγωγείς plain‑text) διατηρούν τη διάταξη.

## Feature 2: Insert Various Control Characters
Πέρα από τις επιστροφές καρτέλας, το Aspose.Words προσφέρει σταθερές για διαστήματα, tabs, line feeds, διαχωριστές παραγράφων και διαχωριστές στηλών. Αυτή η ενότητα δείχνει πώς να ενσωματώσετε καθέναν από αυτούς.

### Step‑by‑Step Implementation
1. **Αρχικοποιήστε έναν νέο DocumentBuilder.**  
2. **Γράψτε παραδείγματα για χαρακτήρες διαστήματος, μη‑διασπώμενου διαστήματος και tab.**  
3. **Προσθέστε line feeds, διαχωριστές παραγράφων και διαχωριστές ενοτήτων, στη συνέχεια επικυρώστε τους αριθμούς κόμβων.**  
4. **Δημιουργήστε διάταξη δύο στηλών και εισάγετε διαχωριστή στήλης.**

#### 1. Initialize DocumentBuilder
```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

#### 2. Insert Space‑Related Characters
- **Διάστημα (`ControlChar.SPACE_CHAR`)**  
```java
builder.write("Before space." + ControlChar.SPACE_CHAR + "After space.");
```
- **Μη‑διασπώμενο διάστημα (`ControlChar.NON_BREAKING_SPACE`)**  
```java
builder.write("Before NBSP." + ControlChar.NON_BREAKING_SPACE + "After NBSP.");
```
- **Tab (`ControlChar.TAB`)**  
```java
builder.write("Before tab." + ControlChar.TAB + "After tab.");
```

#### 3. Line, Paragraph, and Section Breaks
```java
// Verify initial paragraph count is 1
Assert.assertEquals(1, doc.getFirstSection().getBody()
        .getChildNodes(NodeType.PARAGRAPH, true).getCount());

// Insert a line feed (creates a new paragraph)
builder.write("Before line feed." + ControlChar.LINE_FEED + "After line feed.");
Assert.assertEquals(2, doc.getFirstSection().getBody()
        .getChildNodes(NodeType.PARAGRAPH, true).getCount());

// Insert a paragraph break
builder.write("Before paragraph break." + ControlChar.PARAGRAPH_BREAK + "After paragraph break.");
Assert.assertEquals(3, doc.getFirstSection().getBody()
        .getChildNodes(NodeType.PARAGRAPH, true).getCount());

// Insert a section break (still one Section object, but a break marker)
builder.write("Before section break." + ControlChar.SECTION_BREAK + "After section break.");
assert doc.getSections().getCount() == 1 :
        "Section count mismatch after section break.";
```

#### 4. Column Break in a Multi‑Column Layout
```java
// Add a second section to host two columns
doc.appendChild(new Section(doc));
builder.moveToSection(1);
builder.getCurrentSection().getPageSetup().getTextColumns().setCount(2);

// Insert a column break between the two columns
builder.write("Text at end of column 1." + ControlChar.COLUMN_BREAK + "Text at beginning of column 2.");
```

**Αποτέλεσμα:** Το έγγραφο περιέχει τώρα μια σελίδα δύο στηλών όπου το κείμενο ρέει αυτόματα από την πρώτη στήλη στη δεύτερη μετά το `COLUMN_BREAK`.

## Practical Applications
| Σενάριο | Πώς οι Χαρακτήρες Ελέγχου Βοηθούν |
|----------|-----------------------------------|
| **Δημιουργία Τιμολογίων** | Χρησιμοποιήστε `PAGE_BREAK` για να ξεκινάτε νέα σελίδα για κάθε παρτίδα τιμολογίων. |
| **Οικονομική Αναφορά** | Ευθυγραμμίστε αριθμούς με `TAB` και κρατήστε τις επικεφαλίδες μαζί χρησιμοποιώντας `NON_BREAKING_SPACE`. |
| **Διάταξη Ενημερωτικού Δελτίου** | Δημιουργήστε άρθρα δίπλα-δίπλα με `COLUMN_BREAK` σε ενότητα πολλαπλών στηλών. |
| **Εξαγωγή Περιεχομένου CMS** | Διατηρήστε τη δομή των γραμμών όταν μετατρέπετε πλούσιο κείμενο σε plain text μέσω `LINE_FEED`. |
| **Αυτόματες Προτύπες** | Εισάγετε δυναμικά `PARAGRAPH_BREAK` ή `SECTION_BREAK` ανάλογα με την είσοδο του χρήστη. |

## Performance Considerations
* **Batch Inserts:** Ομαδοποιήστε πολλαπλές κλήσεις `write` σε μία ενέργεια για μείωση εσωτερικών reflows.  
* **Avoid Frequent Node Traversal:** Κρατήστε σε cache τα αποτελέ