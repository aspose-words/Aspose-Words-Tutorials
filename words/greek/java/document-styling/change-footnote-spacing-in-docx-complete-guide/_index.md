---
category: general
date: 2026-07-20
description: Αλλάξτε εύκολα το διάστημα των υποσημειώσεων σε αρχεία DOCX. Μάθετε πώς
  να ορίζετε το διάστημα, να ρυθμίζετε το διαχωριστικό υποσημειώσεων και να ορίζετε
  το διάστημα γραμμής παραγράφου με τη Java.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- change footnote spacing
- how to set spacing
- adjust footnote separator
- set paragraph line spacing
- change line spacing docx
language: el
lastmod: 2026-07-20
og_description: Αλλάξτε γρήγορα το διάστημα των υποσημειώσεων σε αρχεία DOCX. Αυτός
  ο οδηγός δείχνει πώς να ορίσετε το διάστημα, να προσαρμόσετε το διαχωριστικό υποσημειώσεων
  και να προσαρμόσετε το διάστημα γραμμής παραγράφου σε Java.
og_image_alt: Screenshot showing Java code that changes footnote spacing in a DOCX
  document
og_title: Αλλαγή απόστασης υποσημειώσεων σε DOCX – Οδηγός βήμα‑προς‑βήμα
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Change footnote spacing in DOCX files easily. Learn how to set spacing,
    adjust footnote separator, and set paragraph line spacing with Java.
  headline: Change footnote spacing in DOCX – Complete Guide
  type: TechArticle
tags:
- footnote
- docx
- java
- spacing
title: Αλλαγή απόστασης υποσημειώσεων σε DOCX – Πλήρης Οδηγός
url: /el/java/document-styling/change-footnote-spacing-in-docx-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Αλλαγή απόστασης υποσημειώσεων σε DOCX – Πλήρης Οδηγός

Έχετε ποτέ χρειαστεί να **αλλάξετε την απόσταση υποσημειώσεων** σε ένα έγγραφο Word αλλά δεν ήξερες από πού να ξεκινήσεις; Δεν είστε μόνοι. Είτε βελτιώνετε μια διπλωματική εργασία είτε προσαρμόζετε ένα συμβόλαιο, η σωστή ρύθμιση του διαχωριστικού υποσημειώσεων μπορεί να κάνει μεγάλη διαφορά.  

Σε αυτό το tutorial θα δούμε **πώς να ορίσουμε την απόσταση**, να προσαρμόσουμε το διαχωριστικό υποσημειώσεων και **να ορίσουμε την απόσταση γραμμής παραγράφου** χρησιμοποιώντας βιβλιοθήκες βασισμένες σε Java. Στο τέλος θα έχετε ένα έτοιμο παράδειγμα που μπορείτε να ενσωματώσετε σε οποιοδήποτε έργο.

## Τι Θα Χρειαστείτε

- Java 17 ή νεότερη (ο κώδικας χρησιμοποιεί τις σύγχρονες δυνατότητες της γλώσσας)
- Maven ή Gradle για διαχείριση εξαρτήσεων
- Ένα αρχείο DOCX με τουλάχιστον μία υποσημείωση (ή μπορείτε να δημιουργήσετε μία χειροκίνητα)
- Η βιβλιοθήκη **Aspose.Words for Java** (ή οποιοδήποτε συμβατό API· θα χρησιμοποιήσουμε το Aspose στο παράδειγμα)

Αυτό είναι όλο—χωρίς βαριά πλαίσια, μόνο καθαρή Java και μία βιβλιοθήκη.

![Change footnote spacing in DOCX example](/images/footnote-spacing.png){alt="Παράδειγμα αλλαγής απόστασης υποσημειώσεων σε DOCX"}

## Βήμα 1: Φόρτωση του εγγράφου DOCX (Αλλαγή απόστασης υποσημειώσεων)

Το πρώτο που πρέπει να κάνετε είναι να ανοίξετε το αρχείο Word. Αυτό σας παρέχει ένα αντικείμενο `Document` που μπορείτε να επεξεργαστείτε.

```java
import com.aspose.words.*;

public class FootnoteSpacingDemo {
    public static void main(String[] args) throws Exception {
        // Load the DOCX file – change the path to your own file
        Document doc = new Document("input.docx");
        
        // Continue with spacing adjustments...
        adjustFootnoteSeparator(doc);
        
        // Save the updated document
        doc.save("output.docx");
    }
}
```

*Γιατί είναι σημαντικό*: Η φόρτωση του εγγράφου είναι το σημείο εισόδου για **την αλλαγή απόστασης υποσημειώσεων**. Χωρίς ένα στιγμιότυπο `Document` δεν μπορείτε να φτάσετε στο διαχωριστικό υποσημειώσεων ή σε οποιεσδήποτε μορφές παραγράφων.

## Βήμα 2: Ανάκτηση και Προσαρμογή του Διαχωριστικού Υποσημειώσεων (Προσαρμογή διαχωριστικού υποσημειώσεων)

Το διαχωριστικό υποσημειώσεων είναι μια κρυφή παράγραφος που βρίσκεται μεταξύ του κυρίως κειμένου και της λίστας υποσημειώσεων. Για να αλλάξετε την απόσταση γραμμής του, πρέπει να πιάσετε αυτήν την παράγραφο και να τροποποιήσετε τη μορφή της.

```java
private static void adjustFootnoteSeparator(Document doc) throws Exception {
    // Get the footnote separator (the first one is usually the default separator)
    FootnoteSeparator separator = doc.getFootnoteSeparator();
    
    // If the document has no separator (rare), create one
    if (separator == null) {
        separator = new FootnoteSeparator(doc);
        doc.getFootnotes().add(separator);
    }
    
    // Access the underlying paragraph and set line spacing
    Paragraph sepParagraph = separator.getSeparatorParagraph();
    ParagraphFormat fmt = sepParagraph.getParagraphFormat();
    
    // Set line spacing to 12 points – this is the core of "change footnote spacing"
    fmt.setLineSpacing(12.0);
    
    // Optional: also adjust spacing before/after if needed
    fmt.setSpaceBefore(0);
    fmt.setSpaceAfter(0);
}
```

### Πώς αυτό λύνει το πρόβλημα

- **Ανάκτηση του διαχωριστικού υποσημειώσεων** – αυτό είναι το τμήμα που πραγματικά θέλετε να τροποποιήσετε, ικανοποιώντας την απαίτηση *προσαρμογής διαχωριστικού υποσημειώσεων*.
- **Ορισμός απόστασης γραμμής** – `setLineSpacing(12.0)` απαντά άμεσα στο *πώς να ορίσετε την απόσταση* για αυτήν τη κρυφή παράγραφο.
- **Διαχείριση ειδικών περιπτώσεων** – εάν το έγγραφο δεν έχει διαχωριστικό, δημιουργούμε ένα άμεσα, αποτρέποντας ένα `NullPointerException`.

## Βήμα 3: Επαλήθευση της Αλλαγής και Αποθήκευση (Ορισμός απόστασης γραμμής παραγράφου)

Αφού τροποποιήσετε το διαχωριστικό, θα θέλετε να βεβαιωθείτε ότι η αλλαγή διατηρήθηκε. Το άνοιγμα του αποθηκευμένου αρχείου στο Word θα εμφανίσει τη νέα απόσταση, αλλά μπορείτε επίσης να το ελέγξετε προγραμματιστικά.

```java
private static void verifySpacing(Document doc) throws Exception {
    FootnoteSeparator sep = doc.getFootnoteSeparator();
    double spacing = sep.getSeparatorParagraph().getParagraphFormat().getLineSpacing();
    System.out.println("Current footnote separator line spacing: " + spacing);
}
```

Προσθέστε μια κλήση στο `verifySpacing(doc);` ακριβώς πριν από το `doc.save(...)` στο `main`. Όταν εκτελέσετε το πρόγραμμα, θα πρέπει να δείτε:

```
Current footnote separator line spacing: 12.0
```

Αυτό επιβεβαιώνει ότι η λειτουργία **αλλαγής απόστασης γραμμής σε docx** ολοκληρώθηκε με επιτυχία.

## Συνηθισμένα Πιθανά Προβλήματα & Επαγγελματικές Συμβουλές

- **Πιθανό πρόβλημα**: Χρήση του `setLineSpacing` με τιμή που φαίνεται “12” αλλά ερμηνεύεται ως “12 pts” αντί για “12 lines”. Το Aspose αναμένει μονάδες σημείων, έτσι 12 σημαίνει 12 pt. Για διπλή απόσταση χρησιμοποιήστε `24.0`.
- **Συμβουλή**: Εάν χρειάζεστε ενιαία εμφάνιση σε όλους τους τύπους υποσημειώσεων (διαχωριστικό, διαχωριστικό συνέχειας κ.λπ.), επαναλάβετε τα ίδια βήματα για `doc.getFootnoteContinuationSeparator()` και `doc.getFootnoteContinuationNotice()`.
- **Πιθανό πρόβλημα**: Ξεχάτε να καλέσετε το `save()` μετά τις τροποποιήσεις. Το έγγραφο στη μνήμη αλλάζει, αλλά το αρχείο στο δίσκο παραμένει το ίδιο.
- **Συμβουλή**: Συνδυάστε τις αλλαγές απόστασης με ενημερώσεις στυλ (`ParagraphStyle`) για μια πλήρως επεξεργασμένη ενότητα υποσημειώσεων.

## Πλήρες Παράδειγμα Εργασίας (Όλα τα Βήματα σε Ένα Αρχείο)

```java
import com.aspose.words.*;

public class FootnoteSpacingDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the DOCX document
        Document doc = new Document("input.docx");

        // 2️⃣ Adjust the footnote separator – this is where we "change footnote spacing"
        adjustFootnoteSeparator(doc);

        // 3️⃣ Verify the new line spacing (optional but handy for debugging)
        verifySpacing(doc);

        // 4️⃣ Save the result – now your footnotes have the desired spacing
        doc.save("output.docx");
        System.out.println("Footnote spacing updated and saved to output.docx");
    }

    private static void adjustFootnoteSeparator(Document doc) throws Exception {
        FootnoteSeparator separator = doc.getFootnoteSeparator();
        if (separator == null) {
            separator = new FootnoteSeparator(doc);
            doc.getFootnotes().add(separator);
        }
        Paragraph sepParagraph = separator.getSeparatorParagraph();
        ParagraphFormat fmt = sepParagraph.getParagraphFormat();

        // Core operation: "set paragraph line spacing" for the separator
        fmt.setLineSpacing(12.0);   // 12 pt line spacing
        fmt.setSpaceBefore(0);
        fmt.setSpaceAfter(0);
    }

    private static void verifySpacing(Document doc) throws Exception {
        FootnoteSeparator sep = doc.getFootnoteSeparator();
        double spacing = sep.getSeparatorParagraph().getParagraphFormat().getLineSpacing();
        System.out.println("Current footnote separator line spacing: " + spacing);
    }
}
```

Αντιγράψτε τον παραπάνω κώδικα σε μια νέα κλάση Java, προσθέστε την εξάρτηση Aspose.Words Maven και εκτελέστε το. Το `output.docx` σας θα έχει τώρα την απόσταση γραμμής του διαχωριστικού υποσημειώσεων ορισμένη σε **12 pt**, αλλάζοντας αποτελεσματικά την **απόσταση υποσημειώσεων**.

### Εξάρτηση Maven

Προσθέστε αυτό το απόσπασμα στο `pom.xml` σας:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest stable version -->
</dependency>
```

Αν προτιμάτε Gradle, το ισοδύναμο είναι:

```gradle
implementation 'com.aspose:aspose-words:24.9'
```

## Συμπέρασμα

Μόλις μάθατε πώς να **αλλάξετε την απόσταση υποσημειώσεων** σε ένα αρχείο DOCX χρησιμοποιώντας Java. Φορτώνοντας το έγγραφο, ανακτώντας το **διαχωριστικό υποσημειώσεων** και εφαρμόζοντας **ορισμό απόστασης γραμμής παραγράφου**, αποκτάτε ακριβή έλεγχο της εμφάνισης των υποσημειώσεων.  

Από εδώ μπορείτε να εξερευνήσετε σχετικές προσαρμογές, όπως η τροποποίηση του στυλ κειμένου υποσημειώσεων, η προσθήκη προσαρμοσμένων διαχωριστικών ή ακόμη η αυτοματοποίηση μαζικών ενημερώσεων σε πολλά έγγραφα.  

Έχετε περισσότερες ερωτήσεις σχετικά με την **προσαρμογή διαχωριστικού υποσημειώσεων** ή άλλες εργασίες αυτοματοποίησης Word; Αφήστε ένα σχόλιο και καλή προγραμματιστική δουλειά!

## Τι Θα Μάθετε Στη Σειρά;

Οι παρακάτω οδηγίες καλύπτουν στενά σχετικά θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Αλλαγή απόστασης και εσοχών ασιατικών παραγράφων σε έγγραφο Word](/words/english/net/document-formatting/change-asian-paragraph-spacing-and-indents/)
- [Αλλαγή απόστασης και εσοχών ασιατικών παραγράφων](/words/german/net/document-formatting/change-asian-paragraph-spacing-and-indents/)
- [Αλλαγή απόστασης και εσοχών ασιατικών παραγράφων](/words/french/net/document-formatting/change-asian-paragraph-spacing-and-indents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}