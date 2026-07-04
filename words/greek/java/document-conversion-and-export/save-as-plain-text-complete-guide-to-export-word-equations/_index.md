---
category: general
date: 2026-05-30
description: Μάθετε πώς να αποθηκεύετε ως απλό κείμενο και να μετατρέπετε docx σε
  txt διατηρώντας τις εξισώσεις. Παράδειγμα Java βήμα‑προς‑βήμα με εξαγωγή εξισώσεων
  Word.
draft: false
keywords:
- save as plain text
- convert docx to txt
- export word equations
- save word as txt
- convert word with equations
language: el
og_description: 'Οδηγός αποθήκευσης ως απλό κείμενο: μετατροπή docx σε txt, εξαγωγή
  εξισώσεων Word και αποθήκευση Word ως txt χρησιμοποιώντας το Aspose.Words.'
og_title: αποθήκευση ως απλό κείμενο – Εξαγωγή εξισώσεων Word σε Java
schemas:
- author: Aspose
  dateModified: '2026-05-30'
  description: Learn how to save as plain text and convert docx to txt while preserving
    equations. Step‑by‑step Java example with export word equations.
  headline: save as plain text – Complete Guide to Export Word Equations
  type: TechArticle
- description: Learn how to save as plain text and convert docx to txt while preserving
    equations. Step‑by‑step Java example with export word equations.
  name: save as plain text – Complete Guide to Export Word Equations
  steps:
  - name: Expected Output
    text: 'Open `MathSample.txt` in any editor and you’ll see something like:'
  - name: What if the target system doesn’t support Unicode?
    text: 'If you need an ASCII‑only fallback, switch the export mode to `OfficeMathExportMode.TEXT`.
      The equations will be rendered as plain text approximations (e.g., “sum(i=1
      to n) i”). Just replace the line:'
  - name: Can I batch‑process a folder of DOCX files?
    text: Absolutely. Wrap the loading and saving logic inside a `File[] files = new
      File("inputFolder").listFiles();` loop. Remember to handle exceptions per file
      to avoid the whole batch stopping on a single corrupt document.
  - name: What about tables or images?
    text: '`TxtSaveOptions` strips non‑text elements by design. If you need a richer
      export (e.g., CSV for tables), consider `CsvSaveOptions` instead. Images are
      omitted because plain text cannot embed binary data.'
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Conversion
title: Αποθήκευση ως απλό κείμενο – Πλήρης οδηγός για την εξαγωγή εξισώσεων Word
url: /el/java/document-conversion-and-export/save-as-plain-text-complete-guide-to-export-word-equations/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# αποθήκευση ως απλό κείμενο – Πλήρης Εκπαιδευτικό Σεμινάριο για τη Μετατροπή DOCX με Εξισώσεις

Ποτέ χρειάστηκε να **αποθηκεύσετε ως απλό κείμενο** αλλά το αρχείο Word σας περιέχει μαθηματικούς τύπους που καταστρέφονται; Δεν είστε μόνοι. Είτε αρχειοθετείτε ερευνητικές εργασίες, τροφοδοτείτε έναν δείκτη αναζήτησης, είτε απλώς χρειάζεστε μια ελαφριά έκδοση μιας σύμβασης, η πρόκληση είναι να διατηρήσετε αυτά τα αντικείμενα OfficeMath αναγνώσιμα μετά τη μετατροπή.

Το θέμα είναι ότι οι περισσότεροι αφελείς μετατροπείς απορρίπτουν τα σύμβολα των εξισώσεων ως ακατανόητους χαρακτήρες. Σε αυτόν τον οδηγό θα σας δείξουμε ακριβώς πώς να **μετατρέψετε docx σε txt** διατηρώντας τις εξισώσεις ως Unicode, ουσιαστικά *εξάγοντας τις εξισώσεις του Word* σε καθαρή, αναζητήσιμη μορφή. Στο τέλος θα έχετε ένα έτοιμο κομμάτι κώδικα Java που **αποθηκεύει το Word ως txt** χωρίς να χάνει τα μαθηματικά.

## Τι Καλύπτει Αυτό το Σεμινάριο

- Απαιτούμενες εξαρτήσεις (Aspose.Words for Java)  
- Ρύθμιση του **TxtSaveOptions** για τον έλεγχο της λειτουργίας εξαγωγής  
- Ένα πλήρες, εκτελέσιμο πρόγραμμα Java που **μετατρέπει το Word με εξισώσεις** με ασφάλεια  
- Συνηθισμένα προβλήματα (ζητήματα γραμματοσειράς, έλλειψη υποστήριξης Unicode) και πώς να τα αποφύγετε  
- Επόμενα βήματα: προσαρμογή αλλαγών γραμμής, διαχείριση πινάκων και επεξεργασία σε παρτίδες  

Δεν χρειάζονται εξωτερικοί σύνδεσμοι τεκμηρίωσης — όλα όσα χρειάζεστε βρίσκονται εδώ.

## Προαπαιτούμενα

- Java 8 ή νεότερη εγκατεστημένη στον υπολογιστή σας  
- Maven ή Gradle για διαχείριση εξαρτήσεων (θα χρησιμοποιήσουμε Maven στο παράδειγμα)  
- Ένα αρχείο DOCX που περιέχει τουλάχιστον ένα αντικείμενο OfficeMath (εξίσωση)  

Αν έχετε όλα αυτά, ας ξεκινήσουμε.

## Βήμα 1: Προσθήκη Εξάρτησης Aspose.Words

Πρώτα, κατεβάστε τη βιβλιοθήκη Aspose.Words for Java. Είναι εμπορικό προϊόν, αλλά προσφέρουν δωρεάν προσωρινή άδεια που λειτουργεί για ανάπτυξη.

```xml
<!-- pom.xml -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

> **Pro tip:** Τοποθετήστε το `aspose-words-24.9.jar` στο classpath σας αν δεν χρησιμοποιείτε Maven.

## Βήμα 2: Φόρτωση του Πηγαίου Εγγράφου

Τώρα θα **φορτώσουμε το πηγαίο έγγραφο**. Η κλάση `Document` διαβάζει οποιαδήποτε μορφή Word, συμπεριλαμβανομένου του `.docx` με ενσωματωμένες εξισώσεις.

```java
import com.aspose.words.Document;
import com.aspose.words.SaveFormat;

public class DocxToTxtConverter {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the source document
        Document document = new Document("YOUR_DIRECTORY/input.docx");
        // ... we'll add the save logic next
    }
}
```

Παρατηρήστε πώς το όνομα μεταβλητής `document` αντικατοπτρίζει την έννοια ενός αρχείου Word, κάνοντας τον κώδικα αυτοεξηγηματικό.

## Βήμα 3: Ρύθμιση TxtSaveOptions για Εξαγωγή Εξισώσεων

Η καρδιά της ροής **εξαγωγής εξισώσεων Word** βρίσκεται στο `TxtSaveOptions`. Από προεπιλογή, το Aspose αφαιρεί το OfficeMath, αλλά μπορούμε να το αλλάξουμε με `OfficeMathExportMode.UNICODE`.

```java
import com.aspose.words.TxtSaveOptions;
import com.aspose.words.OfficeMathExportMode;

// Inside main after loading the document
TxtSaveOptions txtSaveOptions = new TxtSaveOptions();
txtSaveOptions.setOfficeMathExportMode(OfficeMathExportMode.UNICODE);
```

Ορίζοντας τη λειτουργία σε `UNICODE` λέμε στο Aspose να αποδίδει κάθε εξίσωση ως την Unicode αναπαράστασή της (π.χ., “∑”, “√”). Αυτό είναι που κάνει το αρχείο απλού κειμένου ακόμα *αναγνώσιμο* από ανθρώπους και αναζητήσιμο από εργαλεία.

## Βήμα 4: Αποθήκευση του Εγγράφου ως Απλό Κείμενο

Τέλος, **αποθηκεύουμε ως απλό κείμενο** χρησιμοποιώντας τις ρυθμισμένες επιλογές. Αυτό είναι το βήμα όπου η κύρια λέξη-κλειδί λάμπει πραγματικά.

```java
// Step 4: Save the document as a plain‑text file with the configured options
document.save("YOUR_DIRECTORY/MathSample.txt", txtSaveOptions);
System.out.println("Conversion complete! File saved as plain text.");
```

Αυτή η μία γραμμή κάνει το βαριά έργο: γράφει ένα αρχείο `.txt`, διατηρεί τις εξισώσεις και σέβεται τις αλλαγές γραμμής. Έχετε πλέον επιτυχώς **μετατρέψει docx σε txt** διατηρώντας τα μαθηματικά.

## Πλήρες Παράδειγμα Λειτουργίας

Συνδυάζοντας όλα τα παραπάνω, εδώ είναι το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε‑και‑επικολλήσετε στο IDE σας.

```java
import com.aspose.words.Document;
import com.aspose.words.TxtSaveOptions;
import com.aspose.words.OfficeMathExportMode;

public class DocxToTxtConverter {
    public static void main(String[] args) throws Exception {
        // Load the DOCX that contains equations
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // Prepare TXT save options: export OfficeMath as Unicode
        TxtSaveOptions txtSaveOptions = new TxtSaveOptions();
        txtSaveOptions.setOfficeMathExportMode(OfficeMathExportMode.UNICODE);

        // Save as plain text
        document.save("YOUR_DIRECTORY/MathSample.txt", txtSaveOptions);

        System.out.println("Conversion complete! File saved as plain text.");
    }
}
```

### Αναμενόμενο Αποτέλεσμα

Ανοίξτε το `MathSample.txt` σε οποιονδήποτε επεξεργαστή και θα δείτε κάτι σαν:

```
This is a sample paragraph.
∑_{i=1}^{n} i = n(n+1)/2
Another line of text.
```

Η εξίσωση εμφανίζεται ως σωστό σύμβολο Unicode αθροίσματος, αποδεικνύοντας ότι η σημαία **εξαγωγής εξισώσεων Word** λειτούργησε.

## Συχνές Ερωτήσεις & Ακραίες Περιπτώσεις

### Τι γίνεται αν το σύστημα-στόχος δεν υποστηρίζει Unicode;

Αν χρειάζεστε εναλλακτική μόνο ASCII, αλλάξτε τη λειτουργία εξαγωγής σε `OfficeMathExportMode.TEXT`. Οι εξισώσεις θα αποδοθούν ως προσεγγίσεις απλού κειμένου (π.χ., “sum(i=1 to n) i”). Απλώς αντικαταστήστε τη γραμμή:

```java
txtSaveOptions.setOfficeMathExportMode(OfficeMathExportMode.TEXT);
```

### Μπορώ να επεξεργαστώ παρτίδες φακέλου DOCX;

Απολύτως. Τυλίξτε τη λογική φόρτωσης και αποθήκευσης μέσα σε έναν βρόχο `File[] files = new File("inputFolder").listFiles();`. Θυμηθείτε να διαχειρίζεστε εξαιρέσεις ανά αρχείο ώστε η ολόκληρη παρτίδα να μην σταματήσει λόγω ενός κατεστραμμένου εγγράφου.

### Τι γίνεται με πίνακες ή εικόνες;

Το `TxtSaveOptions` αφαιρεί στοιχεία μη‑κειμένου από προεπιλογή. Αν χρειάζεστε πιο πλούσια εξαγωγή (π.χ., CSV για πίνακες), σκεφτείτε το `CsvSaveOptions`. Οι εικόνες παραλείπονται επειδή το απλό κείμενο δεν μπορεί να ενσωματώσει δυαδικά δεδομένα.

## Pro Tips για Αξιόπιστες Μετατροπές

- **Άδεια νωρίς**: Το Aspose θα εμφανίσει προειδοποίηση αν τρέξετε χωρίς άδεια μετά από 30 ημέρες. Προσθέστε `License license = new License(); license.setLicense("Aspose.Words.lic");` στην αρχή του `main`.
- **Κωδικοποίηση UTF‑8**: Η βιβλιοθήκη γράφει UTF‑8 από προεπιλογή. Αν χρειάζεστε διαφορετική κωδικοσελίδα, ορίστε `txtSaveOptions.setEncoding(Encoding.getEncoding("windows-1252"));`.
- **Τέλη γραμμής**: Για στυλ Windows CRLF, καλέστε `txtSaveOptions.setSaveFormat(SaveFormat.TEXT);` (η προεπιλογή χρησιμοποιεί ήδη τις γραμμές του πλατφόρμας).

## Οπτική Επισκόπηση

![διάγραμμα ροής αποθήκευσης ως απλό κείμενο](placeholder.png){alt="διάγραμμα ροής αποθήκευσης ως απλό κείμενο που δείχνει βήματα φόρτωσης, ρύθμισης επιλογών και αποθήκευσης"}

Το διάγραμμα απεικονίζει την τρι‑βήματη αλυσίδα που μόλις κωδικοποιήσαμε: Φόρτωση → Ρύθμιση → Αποθήκευση.

## Συμπέρασμα

Τώρα ξέρετε πώς να **αποθηκεύσετε ως απλό κείμενο** ενώ **μετατρέπετε docx σε txt** και διατηρείτε κάθε εξίσωση άθικτη. Το κλειδί ήταν η ρύθμιση του `TxtSaveOptions` με `OfficeMathExportMode.UNICODE`, που σας επιτρέπει να **εξάγετε εξισώσεις Word** σε καθαρή, αναζητήσιμη μορφή. Με αυτή τη βάση μπορείτε εύκολα να **αποθηκεύσετε το Word ως txt**, να επεξεργαστείτε φακέλους σε παρτίδες ή να προσαρμόσετε τη λειτουργία εξαγωγής για διαφορετικά περιβάλλοντα.

Τι ακολουθεί; Δοκιμάστε να προσθέσετε διεπαφή γραμμής εντολών ώστε οι χρήστες να μπορούν να υποδείξουν οποιονδήποτε φάκελο, ή πειραματιστείτε με `CsvSaveOptions` για εξαγωγή πινάκων σε CSV. Οι δυνατότητες για **μετατροπή Word με εξισώσεις** είναι απεριόριστες, και τώρα έχετε ένα στέρεο, αξιόπιστο σημείο εκκίνησης.

Καλό κώδικα, και οι μετατροπές σας σε απλό κείμενο να είναι πάντα χωρίς απώλειες!

## Τι Θα Μάθετε Στη Σειρά Επόμενη;

- [Save Document as TXT – Quick Guide to Exporting Word Math](/words/english/java/document-conversion-and-export/save-document-as-txt-quick-guide-to-exporting-word-math/)
- [Convert docx to markdown – Export Math Equations to LaTeX with Aspose.Words](/words/english/java/document-conversion-and-export/convert-docx-to-markdown-export-math-equations-to-latex-with/)
- [How to Export LaTeX from Word: Convert DOCX to Markdown & Save as PDF](/words/english/java/document-conversion-and-export/how-to-export-latex-from-word-convert-docx-to-markdown-save/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}