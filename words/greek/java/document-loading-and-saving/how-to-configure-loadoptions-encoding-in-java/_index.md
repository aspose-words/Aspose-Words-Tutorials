---
category: general
date: 2026-10-20
description: Ρυθμίστε την κωδικοποίηση των LoadOptions στη Java για να διαβάζετε σωστά
  τα έγγραφα και αλλάξτε την κωδικοποίηση του εγγράφου σε UTF-8 με το Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- configure LoadOptions encoding
- change document encoding to utf-8
- Aspose.Words Java encoding
- Java document conversion
- character set handling Java
language: el
lastmod: 2026-10-20
og_description: Διαμορφώστε την κωδικοποίηση LoadOptions στη Java για να εξασφαλίσετε
  σωστή διαχείριση χαρακτήρων και μάθετε πώς να αλλάξετε την κωδικοποίηση του εγγράφου
  σε UTF-8 χρησιμοποιώντας το Aspose.Words.
og_image_alt: Screenshot showing Java code that configures LoadOptions encoding and
  saves a document
og_title: Διαμόρφωση κωδικοποίησης LoadOptions στη Java – πλήρης οδηγός
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Configure LoadOptions encoding in Java to correctly read documents
    and change document encoding to UTF-8 with Aspose.Words.
  headline: How to configure LoadOptions encoding in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Encoding
title: Πώς να ρυθμίσετε την κωδικοποίηση LoadOptions στη Java
url: /el/java/document-loading-and-saving/how-to-configure-loadoptions-encoding-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να διαμορφώσετε την κωδικοποίηση LoadOptions στη Java

Αν χρειάζεστε να **διαμορφώσετε την κωδικοποίηση LoadOptions** στη Java, αυτός ο οδηγός σας δείχνει πώς να ορίσετε το σωστό σύνολο χαρακτήρων και στη συνέχεια να **αλλάξετε την κωδικοποίηση του εγγράφου σε UTF-8** χρησιμοποιώντας το Aspose.Words. Η σωστή κωδικοποίηση αποτρέπει το παραμορφωμένο κείμενο κατά τη φόρτωση αρχείων που χρησιμοποιούν παλαιές κωδικοποιήσεις όπως Big5, Shift_JIS ή Windows‑1252.

Θα μάθετε πώς να:

* δημιουργήσετε μια παρουσία `LoadOptions` με συγκεκριμένη κωδικοποίηση,
* φορτώσετε ένα πηγαίο έγγραφο που χρησιμοποιεί αυτήν την κωδικοποίηση,
* αποθηκεύσετε το έγγραφο σε διαφορετική κωδικοποίηση (UTF‑8) χωρίς απώλεια δεδομένων,
* επαληθεύσετε ότι η μετατροπή ολοκληρώθηκε επιτυχώς.

Το tutorial υποθέτει ότι έχετε ένα βασικό περιβάλλον ανάπτυξης Java και μια έγκυρη άδεια Aspose.Words for Java. Δεν απαιτούνται εξωτερικά εργαλεία.

## Προαπαιτήσεις

| Απαίτηση | Γιατί είναι σημαντικό |
|-------------|----------------|
| Java 17 ή νεότερη | Παρέχει σύγχρονα χαρακτηριστικά της γλώσσας και μακροπρόθεσμη υποστήριξη. |
| Aspose.Words for Java (v23.9 ή νεότερη) | Η κλάση `LoadOptions` βρίσκεται σε αυτή τη βιβλιοθήκη. |
| Ένα πηγαίο έγγραφο κωδικοποιημένο με παλαιά κωδικοποίηση (π.χ., Big5) | Δείχνει την ανάγκη για προσαρμοσμένη κωδικοποίηση. |
| Ένα IDE ή εργαλείο κατασκευής (Maven/Gradle) | Καθιστά την μεταγλώττιση και εκτέλεση του παραδείγματος απλή. |

Προσθέστε την εξάρτηση Aspose.Words στο `pom.xml` εάν χρησιμοποιείτε Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## Διαμόρφωση κωδικοποίησης LoadOptions

Το πρώτο βήμα είναι να ενημερώσετε το Aspose.Words ποιο σύνολο χαρακτήρων να περιμένει όταν διαβάζει το αρχείο. Αυτό γίνεται διαμορφώνοντας το αντικείμενο `LoadOptions`.

```java
import com.aspose.words.Document;
import com.aspose.words.LoadOptions;
import java.nio.charset.Charset;

// Step 1: Create LoadOptions and set the desired encoding (Big5 in this example)
LoadOptions loadOptions = new LoadOptions();
loadOptions.setEncoding(Charset.forName("Big5"));
```

**Γιατί είναι σημαντικό:** Όταν ένα έγγραφο αποθηκεύεται με παλαιά κωδικοποίηση, ο προεπιλεγμένος φορτωτής υποθέτει UTF‑8. Ορίζοντας ρητά την κωδικοποίηση, αποφεύγετε το mojibake (παραμορφωμένους χαρακτήρες) και διατηρείτε το αρχικό κείμενο.

### Συμβουλή επαγγελματία
Αν δεν είστε σίγουροι ποια κωδικοποίηση χρησιμοποιεί ένα αρχείο, μπορείτε να ελέγξετε το byte‑order mark (BOM) ή να ρωτήσετε τον πάροχο του εγγράφου. Συνηθισμένες παλαιές κωδικοποιήσεις περιλαμβάνουν `Big5`, `Shift_JIS` και `Windows-1252`.

## Φόρτωση του εγγράφου με τις διαμορφωμένες επιλογές

Τώρα που το `LoadOptions` είναι έτοιμο, φορτώστε το πηγαίο αρχείο. Ο κατασκευαστής που δέχεται διαδρομή αρχείου και μια παρουσία `LoadOptions` εξασφαλίζει ότι η προσαρμοσμένη κωδικοποίηση εφαρμόζεται.

```java
// Step 2: Load the document using the configured LoadOptions
String sourcePath = "C:/Docs/big5_doc.docx";
Document doc = new Document(sourcePath, loadOptions);
```

**Γιατί είναι σημαντικό:** Το αντικείμενο `Document` τώρα περιέχει το κείμενο ακριβώς όπως εμφανίζεται στο αρχικό αρχείο, επειδή ο φορτωτής σεβάστηκε τη σελίδα κώδικα Big5 που παρείχατε.

## Αλλαγή κωδικοποίησης εγγράφου σε UTF-8

Το Aspose.Words αποθηκεύει το κείμενο εσωτερικά ως Unicode, έτσι η ενέργεια της αποθήκευσης του εγγράφου καθορίζει την εξωτερική κωδικοποίηση. Για να δημιουργήσετε ένα αρχείο UTF‑8, απλώς αποθηκεύστε χωρίς να καθορίσετε επιπλέον κωδικοποίηση — το UTF‑8 είναι η προεπιλογή για σύγχρονα φορμά Office Open XML. Ωστόσο, μπορείτε να το επιβάλετε ρητά για σαφήνεια.

```java
// Step 3: Save the document using UTF-8 encoding (default for .docx)
String outputPath = "C:/Docs/Converted.docx";
doc.save(outputPath);
```

Αν χρειάζεστε να δημιουργήσετε μια αναπαράσταση απλού κειμένου (π.χ., `.txt`) με UTF‑8, περάστε ένα αντικείμενο `SaveOptions`:

```java
import com.aspose.words.TxtSaveOptions;

// Save as UTF-8 encoded plain text
TxtSaveOptions txtOptions = new TxtSaveOptions();
txtOptions.setEncoding(Charset.forName("UTF-8"));
doc.save("C:/Docs/Converted.txt", txtOptions);
```

**Γιατί είναι σημαντικό:** Η αποθήκευση ως UTF‑8 εγγυάται ότι οποιοδήποτε σύστημα-παραλήπτης — web services, βάσεις δεδομένων ή σύγχρονοι επεξεργαστές — μπορεί να διαβάσει το αρχείο χωρίς επιπλέον βήματα μετατροπής.

## Επαλήθευση της μετατροπής

Ένας γρήγορος τρόπος για να επιβεβαιώσετε ότι η αλλαγή κωδικοποίησης ολοκληρώθηκε είναι να διαβάσετε ξανά το αποθηκευμένο αρχείο με έναν αναγνώστη UTF‑8 και να εκτυπώσετε μερικούς χαρακτήρες.

```java
import java.nio.file.Files;
import java.nio.file.Paths;

byte[] utf8Bytes = Files.readAllBytes(Paths.get(outputPath));
String content = new String(utf8Bytes, Charset.forName("UTF-8"));
System.out.println("First 200 characters of the converted file:");
System.out.println(content.substring(0, Math.min(200, content.length())));
```

Αν η έξοδος εμφανίζει αναγνώσιμους χαρακτήρες (χωρίς σύμβολα �), η μετατροπή λειτούργησε όπως αναμενόταν.

## Πλήρες εκτελέσιμο παράδειγμα

Παρακάτω υπάρχει ένα αυτόνομο πρόγραμμα που συνδυάζει όλα τα βήματα. Αντικαταστήστε τις διαδρομές αρχείων με τις δικές σας τοποθεσίες.

```java
import com.aspose.words.Document;
import com.aspose.words.LoadOptions;
import com.aspose.words.TxtSaveOptions;
import java.nio.charset.Charset;
import java.nio.file.Files;
import java.nio.file.Paths;

public class EncodingDemo {
    public static void main(String[] args) throws Exception {
        // 1. Configure LoadOptions with the source encoding (Big5)
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setEncoding(Charset.forName("Big5"));

        // 2. Load the legacy‑encoded document
        String sourcePath = "C:/Docs/big5_doc.docx";
        Document doc = new Document(sourcePath, loadOptions);

        // 3. Save as UTF‑8 encoded .docx (default) and .txt for verification
        String docxOutput = "C:/Docs/Converted.docx";
        doc.save(docxOutput); // UTF‑8 by default

        String txtOutput = "C:/Docs/Converted.txt";
        TxtSaveOptions txtOptions = new TxtSaveOptions();
        txtOptions.setEncoding(Charset.forName("UTF-8"));
        doc.save(txtOutput, txtOptions);

        // 4. Verify the .txt file content
        byte[] utf8Bytes = Files.readAllBytes(Paths.get(txtOutput));
        String content = new String(utf8Bytes, Charset.forName("UTF-8"));
        System.out.println("First 200 characters of the UTF‑8 text file:");
        System.out.println(content.substring(0, Math.min(200, content.length())));
    }
}
```

**Αναμενόμενη έξοδος**

```
First 200 characters of the UTF-8 text file:
[Readable Chinese characters from the original Big5 document...]
```

Αν οι χαρακτήρες εμφανίζονται σωστά, έχετε επιτυχώς **διαμορφώσει την κωδικοποίηση LoadOptions** και **αλλάξει την κωδικοποίηση του εγγράφου σε UTF-8**.

## Συνηθισμένα προβλήματα και πώς να τα αποφύγετε

| Σύμπτωμα | Αιτία | Διόρθωση |
|---------|-------|-----|
| Παραμορφωμένοι χαρακτήρες μετά τη φόρτωση | `LoadOptions` δεν έχει οριστεί ή λανθασμένο όνομα charset | Βεβαιωθείτε ότι το `loadOptions.setEncoding(Charset.forName("Big5"))` ταιριάζει με τη σελίδα κώδικα του πηγαίου αρχείου. |
| `UnsupportedEncodingException` | Λανθασμένο όνομα charset | Χρησιμοποιήστε το ακριβές όνομα που εμφανίζεται στο `Charset.availableCharsets()`. |
| Το αρχείο εξόδου εξακολουθεί να εμφανίζει mojibake | Αποθηκεύτηκε ως παλαιό φορμά (π.χ., `.rtf`) χωρίς επιλογές UTF‑8 | Χρησιμοποιήστε `TxtSaveOptions` με `setEncoding("UTF-8")` ή αποθηκεύστε ως `.docx`. |
| Μείωση απόδοσης σε μεγάλα αρχεία | Δημιουργία ξανά του `LoadOptions` για κάθε έγγραφο | Επαναχρησιμοποιήστε μια μόνο παρουσία `LoadOptions` όταν επεξεργάζεστε πολλά αρχεία με την ίδια πηγαία κωδικοποίηση. |

## Συμπέρασμα

Τώρα ξέρετε πώς να **διαμορφώσετε την κωδικοποίηση LoadOptions** στη Java για να διαβάζετε έγγραφα με κωδικοποίηση κληρονομιάς και πώς να **αλλάξετε την κωδικοποίηση του εγγράφου σε UTF-8** για ασφαλή χρήση από επόμενα συστήματα. Η προσέγγιση λειτουργεί για οποιαδήποτε σελίδα κώδικα υποστηρίζεται από την κλάση `Charset` της Java, καθιστώντας την μια ευέλικτη λύση για πολυγλωσσικές εφαρμογές.

Στη συνέχεια, μπορείτε να εξερευνήσετε:

* **Μετατροπή κατά παρτίδες** – επανάληψη σε έναν φάκελο εγγράφων και εφαρμογή της ίδιας λογικής κωδικοποίησης.
* **Ανίχνευση κωδικοποίησης** – χρησιμοποιήστε βιβλιοθήκες όπως το juniversalchardet για αυτόματη ανίχνευση του πηγαίου charset πριν διαμορφώσετε το `LoadOptions`.
* **Διατήρηση μορφοποίησης** – πειραματιστείτε με την αποθήκευση σε PDF ή HTML διατηρώντας τη συμμόρφωση με UTF‑8.

Μη διστάσετε να προσαρμόσετε τον κώδικα στην αρχιτεκτονική του έργου σας, και αφήστε το ισχυρό API του Aspose.Words να αναλάβει το βαριά δουλειά της διαχείρισης εγγράφων.

![Απόσπασμα κώδικα που δείχνει τη διαμόρφωση της κωδικοποίησης LoadOptions και την αποθήκευση του εγγράφου](/images/encoding-demo.png){: .align-center alt="Διαμόρφωση κωδικοποίησης LoadOptions σε παράδειγμα κώδικα Java"}

## Τι Θα Μάθετε Στη Σειρά;

Τα παρακάτω tutorials καλύπτουν στενά σχετικά θέματα που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετα χαρακτηριστικά του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Πώς να Ορίσετε το LoadOptions στο Aspose.Words για Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Πώς να Μετατρέψετε Κείμενο RTF με Κωδικοποίηση UTF-8 σε Java Χρησιμοποιώντας το Aspose.Words](/words/english/java/document-operations/load-rtf-with-utf8-java-asposewords/)
- [Ανάκτηση Κατεστραμμένου Εγγράφου DOCX Word Χρησιμοποιώντας το Aspose.Words LoadOptions – Οδηγός Java](/words/english/java/document-loading-and-saving/recover-corrupted-word-document-using-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}