---
category: general
date: 2026-10-26
description: Μάθετε πώς να καθορίζετε την κωδικοποίηση στη Java χρησιμοποιώντας το
  LoadOptions. Αυτός ο οδηγός καλύπτει την κωδικοποίηση χαρακτήρων, τη μέθοδο setEncoding
  και τις επιλογές φόρτωσης εγγράφων.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to specify encoding
- character encoding in Java
- LoadOptions encoding
- setEncoding method
- document loading options
- Aspose.Words for Java
language: el
lastmod: 2026-10-26
og_description: Πώς να καθορίσετε την κωδικοποίηση στη Java χρησιμοποιώντας το Aspose.Words.
  Ακολουθήστε αυτό το πλήρες σεμινάριο για να φορτώσετε έγγραφα με το σωστό σύνολο
  χαρακτήρων.
og_image_alt: Screenshot showing how to specify encoding in Java LoadOptions
og_title: Πώς να καθορίσετε την κωδικοποίηση στη Java με το Aspose.Words – οδηγός
  βήμα‑βήμα
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn how to specify encoding in Java using LoadOptions. This guide
    covers character encoding, setEncoding method, and document loading options.
  headline: How to specify encoding when loading a document with Aspose.Words for
    Java
  type: TechArticle
- description: Learn how to specify encoding in Java using LoadOptions. This guide
    covers character encoding, setEncoding method, and document loading options.
  name: How to specify encoding when loading a document with Aspose.Words for Java
  steps:
  - name: 5.1 Loading from an `InputStream`
    text: 'Sometimes you receive a document as a stream (e.g., from a web service).
      You can still control the encoding by passing the stream together with `LoadOptions`:'
  - name: 5.2 Fallback when the encoding is unknown
    text: If you cannot determine the source file’s charset, you can attempt a detection
      library (such as ICU4J) before setting the encoding. Once you have a guess,
      invoke `setEncoding` with that value. This approach reduces the risk of mis‑decoded
      text.
  - name: 5.3 Dealing with unsupported encodings
    text: Java supports a wide range of code pages, but a few legacy encodings may
      be missing. In that case, consider converting the file to UTF‑8 externally (e.g.,
      using `iconv`) before loading it with Aspose.Words. After conversion, you can
      omit the `setEncoding` call because UTF‑8 is the default for most m
  type: HowTo
tags:
- Java
- Encoding
- Aspose.Words
title: Πώς να καθορίσετε την κωδικοποίηση κατά τη φόρτωση ενός εγγράφου με το Aspose.Words
  for Java
url: /el/java/document-loading-and-saving/how-to-specify-encoding-when-loading-a-document-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να καθορίσετε την κωδικοποίηση κατά τη φόρτωση ενός εγγράφου με το Aspose.Words for Java

Αν χρειάζεστε **πώς να καθορίσετε την κωδικοποίηση** για ένα αρχείο προέλευσης σε Java, αυτό το tutorial σας δείχνει τα ακριβή βήματα. Είτε το έγγραφο χρησιμοποιεί Big5, UTF‑8 ή κάποιο άλλο σύνολο χαρακτήρων, μπορείτε να ελέγξετε τη διαδικασία ανάγνωσης με το `LoadOptions`. Στο τέλος του οδηγού θα καταλάβετε γιατί η κωδικοποίηση χαρακτήρων είναι σημαντική, πώς να εφαρμόσετε τη μέθοδο `setEncoding` και πώς να επαληθεύσετε ότι το έγγραφο φορτώνεται σωστά.

Η φόρτωση ενός εγγράφου με τη σωστή κωδικοποίηση χαρακτήρων αποτρέπει το παραμορφωμένο κείμενο και εξασφαλίζει ότι το πολυγλωσσικό περιεχόμενο εμφανίζεται όπως προβλέπεται. Αυτό το tutorial καλύπτει:

* Το ρόλο της **character encoding in Java** κατά την ανάγνωση αρχείων.
* Πώς να διαμορφώσετε την **LoadOptions encoding** για το Aspose.Words.
* Πρακτικό κώδικα που μπορείτε να αντιγράψετε στο έργο σας.
* Συνηθισμένα προβλήματα όπως μη αντιστοιχίες κωδικοποιήσεων και πώς να τα αντιμετωπίσετε.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

* Java Development Kit (JDK) 8 ή νεότερο.
* Maven ή Gradle για τη διαχείριση εξαρτήσεων.
* Aspose.Words for Java 23.10 ή νεότερο (η έκδοση που χρησιμοποιείται σε αυτόν τον οδηγό).
* Ένα δείγμα κειμένου (`input.doc`) αποθηκευμένο με την επιθυμητή κωδικοποίηση (π.χ., Big5).

Δεν χρειάζεστε πρόσθετες βιβλιοθήκες· το παράδειγμα χρησιμοποιεί μόνο το βασικό API του Aspose.Words.

## Βήμα 1: Προσθέστε το Aspose.Words στο έργο σας

Αν χρησιμοποιείτε Maven, προσθέστε την ακόλουθη εξάρτηση στο `pom.xml` σας:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
    <classifier>jdk17</classifier>
</dependency>
```

Για Gradle, τοποθετήστε αυτή τη γραμμή στο `build.gradle` σας:

```gradle
implementation 'com.aspose:aspose-words:23.10:jdk17'
```

Η προσθήκη της βιβλιοθήκης καθιστά διαθέσιμες τις κλάσεις `LoadOptions`, `Document` και `Encoding`.

## Βήμα 2: Δημιουργήστε ένα αντικείμενο `LoadOptions`

`LoadOptions` σας επιτρέπει να προσαρμόσετε τον τρόπο με τον οποίο το Aspose.Words ανοίγει ένα αρχείο. Η δημιουργία του αντικειμένου είναι το πρώτο μέρος του **πώς να καθορίσετε την κωδικοποίηση**.

```java
// Step 2: Create load options to customize how the document is opened
LoadOptions loadOptions = new LoadOptions();
```

Το αντικείμενο `LoadOptions` ξεκινά με τις προεπιλεγμένες ρυθμίσεις. Θα προσαρμόσετε τις ιδιότητές του στο επόμενο βήμα.

## Βήμα 3: Ορίστε την επιθυμητή κωδικοποίηση χαρακτήρων

Η μέθοδος `setEncoding` ορίζει την **character encoding in Java** που πρέπει να χρησιμοποιήσει ο φορτωτής. Σε αυτό το παράδειγμα επιλέγουμε τη σελίδα κώδικα Big5, η οποία είναι κοινή για αρχεία κειμένου παραδοσιακής Κινέζικης.

```java
// Step 3: Specify the character encoding (Big5) for the source file
loadOptions.setEncoding(Encoding.getEncoding("Big5"));
```

*Γιατί είναι σημαντικό*: Αν τα byte του αρχείου ερμηνευτούν με τη λάθος σελίδα κώδικα, οι χαρακτήρες εμφανίζονται ως ερωτηματικά ή ακατανόητο κείμενο. Καλώντας ρητά το `setEncoding`, λέτε στο Aspose.Words να αποκωδικοποιήσει τη ροή byte χρησιμοποιώντας τον πίνακα αντιστοίχισης Big5.

Μπορείτε να αντικαταστήσετε το `"Big5"` με οποιοδήποτε όνομα charset αναγνωρίζεται από τη Java, όπως `"UTF-8"`, `"ISO-8859-1"` ή `"Windows-1252`. Η μέθοδος ρίχνει `UnsupportedEncodingException` εάν το όνομα είναι άκυρο, οπότε ίσως θελήσετε να πιάσετε αυτήν την εξαίρεση σε κώδικα παραγωγής.

## Βήμα 4: Φορτώστε το έγγραφο με τις ρυθμισμένες επιλογές

Τώρα που η **LoadOptions encoding** έχει οριστεί, περάστε τις επιλογές στον κατασκευαστή `Document`. Αυτό το βήμα ολοκληρώνει τη βασική ροή εργασίας **πώς να καθορίσετε την κωδικοποίηση**.

```java
// Step 4: Load the document using the configured options
Document doc = new Document("YOUR_DIRECTORY/input.doc", loadOptions);
```

Αντικαταστήστε το `YOUR_DIRECTORY` με την απόλυτη ή σχετική διαδρομή προς το αρχείο σας. Το αντικείμενο `Document` τώρα περιέχει το πλήρως αναλυμένο περιεχόμενο, σεβόμενος την κωδικοποίηση που δώσατε.

## Βήμα 5: Επαληθεύστε ότι το κείμενο φορτώνεται σωστά

Μια γρήγορη επαλήθευση σας βοηθά να βεβαιωθείτε ότι η κωδικοποίηση εφαρμόστηκε όπως αναμενόταν. Μπορείτε να εξάγετε το κείμενο του εγγράφου και να το εκτυπώσετε στην κονσόλα:

```java
// Step 5: Output the document text to verify correct decoding
System.out.println(doc.getText());
```

Αν η κονσόλα εμφανίζει αναγνώσιμους Κινέζικους χαρακτήρες (ή τη γλώσσα που αναμένετε), η κωδικοποίηση ήταν επιτυχής. Αν εξακολουθείτε να βλέπετε παραμορφωμένο αποτέλεσμα, ελέγξτε ξανά την κωδικοποίηση του αρχικού αρχείου και βεβαιωθείτε ότι το όνομα charset ταιριάζει ακριβώς.

## Διαχείριση κοινών περιπτώσεων άκρων

### 5.1 Φόρτωση από `InputStream`

Μερικές φορές λαμβάνετε ένα έγγραφο ως ροή (π.χ., από υπηρεσία web). Μπορείτε ακόμη να ελέγξετε την κωδικοποίηση περνώντας τη ροή μαζί με το `LoadOptions`:

```java
try (InputStream stream = new FileInputStream("YOUR_DIRECTORY/input.doc")) {
    Document docFromStream = new Document(stream, loadOptions);
    System.out.println(docFromStream.getText());
}
```

Οι ίδιες **document loading options** ισχύουν, και η κλήση `setEncoding` παραμένει αμετάβλητη.

### 5.2 Εναλλακτική όταν η κωδικοποίηση είναι άγνωστη

Αν δεν μπορείτε να προσδιορίσετε το charset του αρχείου προέλευσης, μπορείτε να δοκιμάσετε μια βιβλιοθήκη ανίχνευσης (όπως η ICU4J) πριν ορίσετε την κωδικοποίηση. Μόλις έχετε μια εκτίμηση, καλέστε το `setEncoding` με αυτήν την τιμή. Αυτή η προσέγγιση μειώνει τον κίνδυνο λανθασμένης αποκωδικοποίησης του κειμένου.

### 5.3 Αντιμετώπιση μη υποστηριζόμενων κωδικοποιήσεων

Η Java υποστηρίζει ένα ευρύ φάσμα σελίδων κώδικα, αλλά μερικές παλαιές κωδικοποιήσεις μπορεί να λείπουν. Σε αυτήν την περίπτωση, σκεφτείτε να μετατρέψετε το αρχείο σε UTF‑8 εξωτερικά (π.χ., χρησιμοποιώντας `iconv`) πριν το φορτώσετε με το Aspose.Words. Μετά τη μετατροπή, μπορείτε να παραλείψετε την κλήση `setEncoding` επειδή το UTF‑8 είναι η προεπιλογή για τις περισσότερες σύγχρονες API.

## Συμβουλή: Επαναχρησιμοποίηση του `LoadOptions` για επεξεργασία παρτίδας

Αν χρειάζεται να φορτώσετε πολλά έγγραφα που μοιράζονται το ίδιο charset, δημιουργήστε ένα μόνο αντικείμενο `LoadOptions` και επαναχρησιμοποιήστε το:

```java
LoadOptions sharedOptions = new LoadOptions();
sharedOptions.setEncoding(Encoding.getEncoding("Big5"));

String[] files = {"doc1.doc", "doc2.doc", "doc3.doc"};
for (String file : files) {
    Document d = new Document("YOUR_DIRECTORY/" + file, sharedOptions);
    // Process each document...
}
```

Η επαναχρησιμοποίηση του αντικειμένου μειώνει το κόστος δημιουργίας αντικειμένων και εγγυάται συνεπή κωδικοποίηση σε όλη τη παρτίδα.

## Πλήρες εκτελέσιμο παράδειγμα

Παρακάτω βρίσκεται το πλήρες πρόγραμμα που ενσωματώνει όλα τα βήματα, περιλαμβάνει τις απαραίτητες εισαγωγές και διαχειρίζεται πιθανές εξαιρέσεις.

```java
import com.aspose.words.Document;
import com.aspose.words.LoadOptions;
import com.aspose.words.Encoding;

import java.io.FileInputStream;
import java.io.InputStream;
import java.io.UnsupportedEncodingException;

public class LoadDocumentWithEncoding {
    public static void main(String[] args) {
        // Path to the input document
        String inputPath = "YOUR_DIRECTORY/input.doc";

        try {
            // Create LoadOptions and set the desired charset (Big5 in this case)
            LoadOptions loadOptions = new LoadOptions();
            loadOptions.setEncoding(Encoding.getEncoding("Big5"));

            // Load the document using the configured options
            Document doc = new Document(inputPath, loadOptions);

            // Output the document text to verify correct decoding
            System.out.println("Document text:");
            System.out.println(doc.getText());

            // Optional: load from InputStream using the same options
            try (InputStream stream = new FileInputStream(inputPath)) {
                Document docFromStream = new Document(stream, loadOptions);
                System.out.println("Text from stream:");
                System.out.println(docFromStream.getText());
            }

        } catch (UnsupportedEncodingException e) {
            System.err.println("The specified encoding is not supported: " + e.getMessage());
        } catch (Exception e) {
            System.err.println("Error loading document: " + e.getMessage());
        }
    }
}
```

**Αναμενόμενο αποτέλεσμα** (υποθέτοντας ότι το αρχείο προέλευσης περιέχει Κινέζικο κείμενο κωδικοποιημένο σε Big5):

```
Document text:
【此處顯示正確的中文內容】...
Text from stream:
【此處顯示正確的中文內容】...
```

Αν το αποτέλεσμα εμφανίζει μη αναγνώσιμα σύμβολα, επανεξετάστε το όνομα charset ή ελέγξτε την αρχική κωδικοποίηση του αρχείου.

## Συχνές ερωτήσεις

**Λειτουργεί αυτό με άλλες μορφές εγγράφων (DOCX, RTF, HTML);**  
Ναι. Το ίδιο αντικείμενο `LoadOptions` ισχύει για οποιαδήποτε μορφή υποστηρίζεται από το Aspose.Words. Η μόνη απαίτηση είναι το υποκείμενο αρχείο να χρησιμοποιεί πραγματικά το καθορισμένο charset.

**Τι γίνεται αν χρειαστεί να αλλάξω την κωδικοποίηση μετά τη φόρτωση του εγγράφου;**  
Η κωδικοποίηση επηρεάζει μόνο τη φάση ανάγνωσης. Μόλις υπάρχει το αντικείμενο `Document`, η εσωτερική του αναπαράσταση Unicode είναι ανεξάρτητη από το αρχικό charset. Για να αλλάξετε την κωδικοποίηση εξόδου, προσαρμόστε το `SaveOptions` όταν γράφετε το αρχείο.

**Μπορώ να χρησιμοποιήσω αυτήν την προσέγγιση με άλλες βιβλιοθήκες (π.χ., Apache POI);**  
Το Apache POI διαχειρίζεται τη δική του ανίχνευση charset για παλαιότερες δυαδικές μορφές, αλλά η ιδέα της παροχής charset σε έναν φορτωτή είναι παρόμοια. Για το Aspose.Words, το `LoadOptions` είναι ο επίσημος τρόπος ελέγχου **πώς να καθορίσετε την κωδικοποίηση**.

## Συμπέρασμα

Τώρα γνωρίζετε **πώς να καθορίσετε την κωδικοποίηση** κατά τη φόρτωση ενός εγγράφου με το Aspose.Words for Java. Δημιουργώντας ένα αντικείμενο `LoadOptions`, καλώντας τη μέθοδο `setEncoding` και περνώντας τις επιλογές στον κατασκευαστή `Document`, εξασφαλίζετε ότι τα byte του αρχείου ερμηνεύονται σωστά. Αυτή η πρακτική εξαλείφει το παραμορφωμένο κείμενο, υποστηρίζει πολυγλωσσικό περιεχόμενο και ενσωματώνεται ομαλά σε επεξεργασία παρτίδας ή ροές.

Εξερευνήστε συναφή θέματα όπως **document loading options**, **saving with specific encodings**, και **handling Unicode in Java** για να εμβαθύνετε τη γνώση σας στην επεξεργασία κειμένου. Πειραματιστείτε με διαφορετικά ονόματα charset, συνδυάστε την προσέγγιση με μετατροπή σε PDF ή ενσωματώστε την σε μια υπηρεσία web που δέχεται μεταφορτώσεις σε διάφορες κωδικοποιήσεις.

Καλό κώδικα!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε σε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Πώς να μετατρέψετε κείμενο RTF με κωδικοποίηση UTF-8 σε Java χρησιμοποιώντας το Aspose.Words](/words/english/java/document-operations/load-rtf-with-utf8-java-asposewords/)
- [Πώς να ορίσετε επιλογές στο Aspose.Words for Java – πλήρης οδηγός](/words/english/java/document-loading-and-saving/how-to-set-options-in-aspose-words-for-java-complete-guide/)
- [Ανάκτηση κατεστραμμένου εγγράφου DOCX Word χρησιμοποιώντας Aspose.Words LoadOptions – Οδηγός Java](/words/english/java/document-loading-and-saving/recover-corrupted-word-document-using-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}