---
category: general
date: 2026-08-07
description: πώς να ορίσετε επιλογές στο Aspose.Words for Java, να αποθηκεύσετε ως
  docx και να αλλάξετε την κωδικοποίηση του εγγράφου με την κωδικοποίηση πηγής, υποστήριξη
  Java.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to set options
- save as docx
- change document encoding
- set document encoding
- source encoding java
language: el
lastmod: 2026-08-07
og_description: πώς να ορίσετε επιλογές στο Aspose.Words for Java, στη συνέχεια να
  αποθηκεύσετε ως docx ενώ αλλάζετε την κωδικοποίηση του εγγράφου. Ακολουθήστε αυτόν
  τον οδηγό για να κατακτήσετε την κωδικοποίηση πηγαίου κώδικα Java.
og_image_alt: Screenshot of Java code that sets load options and saves a document
  as docx
og_title: Πώς να ορίσετε επιλογές στο Aspose.Words για Java – βήμα‑βήμα οδηγός
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: how to set options in Aspose.Words for Java, save as docx and change
    document encoding with source encoding java support.
  headline: How to set options in Aspose.Words for Java – complete guide
  type: TechArticle
- description: how to set options in Aspose.Words for Java, save as docx and change
    document encoding with source encoding java support.
  name: How to set options in Aspose.Words for Java – complete guide
  steps:
  - name: Using a different code page
    text: 'If your source files use a different legacy encoding (e.g., Windows‑1252
      or Shift_JIS), replace `"Big5"` with the appropriate charset name:'
  - name: Loading from a stream
    text: 'When you read a file from a network source or a database blob, pass an
      `InputStream` together with `LoadOptions`:'
  - name: Saving to other formats
    text: 'Aspose.Words supports PDF, HTML, RTF, and many more. To **save as docx**
      you already have the code; to save as PDF, change the file extension:'
  - name: Handling password‑protected files
    text: 'If the legacy document is encrypted, provide the password when constructing
      the `Document`:'
  - name: Performance tip
    text: When processing large batches, reuse a single `LoadOptions` instance. Creating
      a new object for each file adds negligible overhead, but reusing reduces garbage‑collection
      pressure.
  type: HowTo
tags:
- Aspose.Words
- Java
- Document processing
title: Πώς να ορίσετε επιλογές στο Aspose.Words για Java – πλήρης οδηγός
url: /el/java/document-loading-and-saving/how-to-set-options-in-aspose-words-for-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να ορίσετε επιλογές στο Aspose.Words for Java – πλήρης οδηγός

Αν χρειάζεστε **πώς να ορίσετε επιλογές** για τη φόρτωση ενός παλαιού αρχείου Word σε Java, αυτό το tutorial δείχνει τα ακριβή βήματα. Θα μάθετε πώς να αλλάζετε την κωδικοποίηση του εγγράφου, να ρυθμίζετε το **source encoding** java, και τελικά **να αποθηκεύσετε ως docx** με μια σύγχρονη μορφή αρχείου.

Ο οδηγός καλύπτει κάθε γραμμή κώδικα που πρέπει να γράψετε, εξηγεί γιατί κάθε επιλογή είναι σημαντική και παρέχει ένα έτοιμο‑για‑εκτέλεση παράδειγμα. Στο τέλος θα μπορείτε να επεξεργαστείτε οποιοδήποτε παλαιό έγγραφο που χρησιμοποιεί μη‑UTF‑8 κωδική σελίδα όπως η Big5.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

* Java Development Kit (JDK) 8 ή νεότερο εγκατεστημένο.  
* Maven ή Gradle για διαχείριση εξαρτήσεων, ή το Aspose.Words for Java JAR στο classpath.  
* Ένα παλαιό αρχείο Word (`input.docx`) κωδικοποιημένο με τη σελίδα κώδικα Big5.  
* Δικαίωμα εγγραφής στον φάκελο εξόδου.  

Όλος ο κώδικας σε αυτό το tutorial μεταγλωττίζεται με Java 17 και Aspose.Words 23.9.0.

## Πώς να ορίσετε επιλογές για τη φόρτωση ενός εγγράφου

Το πρώτο βήμα είναι να δημιουργήσετε μια παρουσία `LoadOptions` και να διαμορφώσετε την **source encoding** της. Η μέθοδος `setEncoding` λέει στο Aspose.Words πώς να ερμηνεύσει τα byte του εισερχόμενου αρχείου.

```java
import com.aspose.words.*;
import java.nio.charset.Charset;

public class EncodingDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create load options and set the source encoding to Big5
        LoadOptions loadOptions = new LoadOptions();
        // source encoding java – Big5 is a traditional Chinese code page
        loadOptions.setEncoding(Charset.forName("Big5"));

        // Step 2: Load the legacy document using the configured options
        Document legacyDoc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // Step 3: Save the document in the modern format
        legacyDoc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

**Γιατί λειτουργεί αυτό:**  
`LoadOptions` επηρεάζει μόνο τη φάση ανάγνωσης. Αναθέτοντας `Charset.forName("Big5")` υποδεικνύετε στη βιβλιοθήκη να θεωρήσει τα ακατέργαστα byte ως χαρακτήρες Big5. Αν παραλείψετε αυτήν την κλήση, το Aspose.Words υποθέτει UTF‑8, κάτι που καταστρέφει τους κινέζιους χαρακτήρες σε πολλά παλαιά αρχεία.

## Αποθήκευση ως docx μετά την αλλαγή της κωδικοποίησης

Μόλις το έγγραφο φορτωθεί με τη σωστή **set document encoding**, μπορείτε να το εξάγετε σε οποιαδήποτε μορφή υποστηρίζεται από το Aspose.Words. Το παραπάνω παράδειγμα χρησιμοποιεί `Document.save` με όνομα αρχείου `.docx`, το οποίο ενεργοποιεί τη λειτουργία **save as docx**.

```java
// Save the document in the modern format (DOCX)
legacyDoc.save("YOUR_DIRECTORY/output.docx");
```

Το παραγόμενο `output.docx` περιέχει κείμενο Unicode, οπότε εμφανίζεται σωστά σε οποιαδήποτε πλατφόρμα χωρίς να απαιτείται συγκεκριμένη κωδική σελίδα.

## Επαλήθευση της μετατροπής

Για να επιβεβαιώσετε ότι η μετατροπή πέτυχε, ανοίξτε το `output.docx` στο Microsoft Word, LibreOffice ή σε οποιονδήποτε προβολέα DOCX. Οι κινέζικοι χαρακτήρες πρέπει να εμφανίζονται ακατάσχετοι, και το μέγεθος του αρχείου θα είναι συγκρίσιμο με ένα έγγραφο που δημιουργήθηκε απευθείας σε σύγχρονο επεξεργαστή.

Αν προτιμάτε προγραμματιστική επαλήθευση, μπορείτε να διαβάσετε το αποθηκευμένο αρχείο ξανά σε ένα αντικείμενο `Document` και να ελέγξετε το κείμενο:

```java
Document verify = new Document("YOUR_DIRECTORY/output.docx");
System.out.println(verify.getText().substring(0, 100)); // prints first 100 characters
```

Η έξοδος της κονσόλας θα εμφανίσει σωστά αποκωδικοποιημένους χαρακτήρες, αποδεικνύοντας ότι η **change document encoding** ήταν αποτελεσματική.

## Συχνές παραλλαγές και ειδικές περιπτώσεις

### Χρήση διαφορετικής σελίδας κώδικα

Αν τα πηγαία αρχεία σας χρησιμοποιούν διαφορετική κωδικοποίηση (π.χ., Windows‑1252 ή Shift_JIS), αντικαταστήστε το `"Big5"` με το κατάλληλο όνομα charset:

```java
loadOptions.setEncoding(Charset.forName("Shift_JIS"));
```

### Φόρτωση από ροή

Όταν διαβάζετε ένα αρχείο από πηγή δικτύου ή από BLOB βάσης δεδομένων, περάστε ένα `InputStream` μαζί με το `LoadOptions`:

```java
try (InputStream stream = Files.newInputStream(Paths.get("input.docx"))) {
    Document doc = new Document(stream, loadOptions);
    doc.save("output.docx");
}
```

### Αποθήκευση σε άλλες μορφές

Το Aspose.Words υποστηρίζει PDF, HTML, RTF και πολλά άλλα. Για **save as docx** έχετε ήδη τον κώδικα· για αποθήκευση ως PDF, αλλάξτε την επέκταση του αρχείου:

```java
legacyDoc.save("output.pdf");
```

Η ίδια διαμόρφωση `LoadOptions` ισχύει ανεξάρτητα από τη μορφή προορισμού.

### Διαχείριση αρχείων με κωδικό πρόσβασης

Αν το παλαιό έγγραφο είναι κρυπτογραφημένο, παρέχετε τον κωδικό πρόσβασης κατά τη δημιουργία του `Document`:

```java
loadOptions.setPassword("mySecret");
Document protectedDoc = new Document("protected.docx", loadOptions);
```

### Συμβουλή απόδοσης

Κατά την επεξεργασία μεγάλων παρτίδων, επαναχρησιμοποιήστε ένα μόνο αντικείμενο `LoadOptions`. Η δημιουργία νέου αντικειμένου για κάθε αρχείο προσθέτει αμελητέο κόστος, αλλά η επαναχρήση μειώνει την πίεση στην garbage‑collection.

## Πλήρες, εκτελέσιμο έργο

Παρακάτω βρίσκεται ένα πλήρες Maven `pom.xml` που φέρνει την απαιτούμενη εξάρτηση Aspose.Words. Αντιγράψτε την κλάση `EncodingDemo.java` στο `src/main/java` και εκτελέστε `mvn compile exec:java`.

```xml
<!-- pom.xml -->
<project xmlns="http://maven.apache.org/POM/4.0.0" 
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 
                             http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>encoding-demo</artifactId>
    <version>1.0.0</version>
    <properties>
        <maven.compiler.source>17</maven.compiler.source>
        <maven.compiler.target>17</maven.compiler.target>
    </properties>

    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>23.9.0</version>
            <classifier>jdk17</classifier>
        </dependency>
    </dependencies>

    <build>
        <plugins>
            <plugin>
                <groupId>org.codehaus.mojo</groupId>
                <artifactId>exec-maven-plugin</artifactId>
                <version>3.1.0</version>
                <configuration>
                    <mainClass>EncodingDemo</mainClass>
                </configuration>
            </plugin>
        </plugins>
    </build>
</project>
```

Η εκτέλεση του `mvn exec:java` παράγει το `output.docx` στον καθορισμένο φάκελο. Το πρόγραμμα δείχνει **πώς να ορίσετε επιλογές**, **πώς να αλλάξετε την κωδικοποίηση του εγγράφου**, και **πώς να αποθηκεύσετε ως docx** σε μια ενιαία, συνοπτική ροή.

## Επαγγελματικές συμβουλές και παγίδες

* **Μην παραλείπετε το charset** όταν η πηγή χρησιμοποιεί μη‑UTF‑8 κωδική σελίδα· η προεπιλεγμένη υπόθεση οδηγεί σε ακατάλληλο κείμενο.  
* **Επικυρώστε το αποτέλεσμα** σε μηχάνημα που υποστηρίζει τη γλώσσα-στόχο· η οπτική επιθεώρηση είναι ο πιο γρήγορος τρόπος ελέγχου.  
* **Αποφύγετε την σκληρή κωδικοποίηση διαδρομών αρχείων** σε κώδικα παραγωγής. Χρησιμοποιήστε αρχεία ρυθμίσεων ή μεταβλητές περιβάλλοντος για να διατηρήσετε τον κώδικα φορητό.  
* **Κρατήστε την έκδοση του Aspose.Words ενημερωμένη**. Οι νέες κυκλοφορίες προσθέτουν υποστήριξη για επιπλέον κωδικοποιήσεις και βελτιώνουν την απόδοση για μεγάλα έγγραφα.

## Συμπέρασμα

Τώρα γνωρίζετε **πώς να ορίσετε επιλογές** στο Aspose.Words for Java, να διαμορφώσετε το **source encoding java**, να **αλλάξετε την κωδικοποίηση του εγγράφου**, και να **αποθηκεύσετε ως docx** σε μια σύγχρονη, Unicode‑ασφαλή μορφή. Το πλήρες παράδειγμα, η ρύθμιση Maven και οι οδηγίες για ειδικές περιπτώσεις σας δίνουν μια σταθερή βάση για την επεξεργασία παλαιών αρχείων Word σε οποιαδήποτε εφαρμογή Java.

Τα επόμενα βήματα περιλαμβάνουν την εξερεύνηση άλλων μορφών εξόδου όπως PDF, την ενσωμάτωση της μετατροπής σε μια γραμμή επεξεργασίας παρτίδων, και τη δοκιμή προσαρμοσμένων `LoadOptions` όπως `Password` ή `LoadFormat`. Καλό κώδικα!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικά παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Using Document Options and Settings in Aspose.Words for Java](/words/english/java/document-manipulation/using-document-options-and-settings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}