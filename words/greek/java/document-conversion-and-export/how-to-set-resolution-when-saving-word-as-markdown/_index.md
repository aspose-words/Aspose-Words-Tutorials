---
category: general
date: 2026-05-04
description: Πώς να ορίσετε την ανάλυση για εξαγωγή σε Markdown από το Word. Μάθετε
  την ανάλυση των εικόνων στο markdown, πώς να εξάγετε εξισώσεις και πώς να αποθηκεύσετε
  το Word ως markdown σε Java.
draft: false
keywords:
- how to set resolution
- markdown image resolution
- how to use markdown
- how to export equations
- save word as markdown
language: el
og_description: Πώς να ορίσετε την ανάλυση για εξαγωγή Markdown από το Word. Αυτός
  ο οδηγός δείχνει την ανάλυση εικόνων σε markdown, την εξαγωγή εξισώσεων και την
  αποθήκευση του Word ως markdown.
og_title: Πώς να ορίσετε την ανάλυση κατά την αποθήκευση του Word ως Markdown
tags:
- Aspose.Words
- Java
- Markdown
- Document Export
title: Πώς να ορίσετε την ανάλυση κατά την αποθήκευση του Word σε μορφή Markdown
url: /el/java/document-conversion-and-export/how-to-set-resolution-when-saving-word-as-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να ορίσετε την ανάλυση κατά την αποθήκευση του Word ως Markdown

Έχετε αναρωτηθεί ποτέ **πώς να ορίσετε την ανάλυση** για τις εικόνες που εμφανίζονται σε ένα αρχείο Markdown που δημιουργείται από ένα έγγραφο Word; Δεν είστε μόνοι. Πολλοί προγραμματιστές αντιμετωπίζουν πρόβλημα όταν οι προεπιλεγμένες rasterized μαθηματικές εικόνες φαίνονται θολές, ειδικά σε οθόνες υψηλής ανάλυσης (DPI).

Σε αυτό το tutorial θα περάσουμε βήμα‑βήμα τις ακριβείς ενέργειες για να ελέγξετε την *markdown image resolution* ενώ θα δείξουμε επίσης **πώς να εξάγετε εξισώσεις** ως LaTeX και, τέλος, **πώς να αποθηκεύσετε το Word ως markdown** χρησιμοποιώντας το Aspose.Words for Java. Στο τέλος θα έχετε ένα καθαρό, έτοιμο για παραγωγή αρχείο Markdown που αποδίδει τις εξισώσεις με σαφήνεια και τις εικόνες στην ποιότητα που χρειάζεστε.

## Prerequisites

- Java 17 (ή οποιοδήποτε πρόσφατο JDK)  
- Aspose.Words for Java 23.6 ή νεότερο – μπορείτε να το κατεβάσετε από το Maven Central  
- Ένα έγγραφο Word (`.docx`) που περιέχει αντικείμενα OfficeMath (εξισώσεις) και πιθανώς raster εικόνες  
- Βασική εξοικείωση με Maven/Gradle και ένα IDE (IntelliJ IDEA, Eclipse, VS Code, κ.λπ.)

Δεν απαιτούνται πρόσθετες βιβλιοθήκες· όλα τα υπόλοιπα διαχειρίζονται από το Aspose.Words.

---

## How to Set Resolution for Markdown Export

> **Pro tip:** Η ανάλυση που επιλέγετε επηρεάζει άμεσα το μέγεθος του αρχείου των παραγόμενων εικόνων. Μια τιμή **300 dpi** είναι μια καλή ισορροπία για τους περισσότερους web‑βασισμένους προβολείς Markdown.

```java
// Step 1: Load the source Word document containing equations
Document doc = new Document("YOUR_DIRECTORY/Math.docx");

// Step 2: Create Markdown save options to control the export behavior
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();

// Step 3: Export OfficeMath objects as LaTeX expressions
saveOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);

// Step 4 (optional): Set image resolution for any rasterized Math images
saveOptions.setImageResolution(300);   // <-- this is where we set the resolution

// Step 5: Save the document as a Markdown file using the configured options
doc.save("YOUR_DIRECTORY/MathExport.md", saveOptions);
```

Η κλήση `setImageResolution(int dpi)` είναι η καρδιά του **πώς να ορίσετε την ανάλυση**. Λέει στο Aspose.Words να rasterize οποιεσδήποτε fallback εικόνες (π.χ., όταν μια εξίσωση δεν μπορεί να αναπαρασταθεί σε καθαρό LaTeX) με τα καθορισμένα dots‑per‑inch. Αν παραλείψετε αυτή τη γραμμή, η βιβλιοθήκη επιστρέφει στην προεπιλογή των 220 dpi, που μπορεί να φαίνεται θολή σε οθόνες retina.

### Why Use LaTeX for Equations?

Όταν εξάγετε εξισώσεις ως LaTeX (`OfficeMathExportMode.LATEX`), το παραγόμενο Markdown περιέχει ακατέργαστο κώδικα LaTeX τυλιγμένο σε `$…$` ή `$$…$$`. Οι περισσότεροι σύγχρονοι προβολείς Markdown (GitHub, GitLab, MkDocs με MathJax) θα τα αποδώσουν ως καθαρές, κλιμακώσιμες διανυσματικές γραφικές παραστάσεις—χωρίς ανησυχίες για ανάλυση. Η ρύθμιση ανάλυσης αφορά μόνο την **markdown image resolution** των raster fallback εικόνων, όπως ενσωματωμένα διαγράμματα ή φωτογραφίες που δεν υποστηρίζονται εγγενώς στο Markdown.

---

## How to Use Markdown Image Resolution Effectively

Αν χρειάζεται να ενσωματώσετε κανονικές εικόνες (π.χ., screenshots) μέσα στο αρχείο Word, αυτές θα μετατραπούν σε PNG από το Aspose.Words. Η ίδια μέθοδος `setImageResolution` εφαρμόζεται, εξασφαλίζοντας ότι τα PNG κληρονομούν το DPI που καθορίζετε. Εδώ είναι ένας σύντομος κατάλογος ελέγχου:

1. **Επιλέξτε DPI που ταιριάζει στην πλατφόρμα-στόχο** – 72 dpi για παλαιά web, 150 dpi για τυπικές οθόνες, 300 dpi για εκτυπώσεις‑ποιότητας PDF.  
2. **Δοκιμάστε το αποτέλεσμα** – ανοίξτε το παραγόμενο `.md` αρχείο στον αγαπημένο σας προβολέα και κάντε ζουμ για να επαληθεύσετε την ευκρίνεια.  
3. **Λάβετε υπόψη το μέγεθος αρχείου** – υψηλότερο DPI δημιουργεί μεγαλύτερα PNG· αν η ταχύτητα δικτύου είναι πρόβλημα, πειραματιστείτε με 200 dpi και συγκρίνετε.

---

## How to Export Equations as LaTeX

Η γραμμή `saveOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);` λέει στο Aspose.Words να μεταφράσει κάθε αντικείμενο OfficeMath σε LaTeX. Αυτή είναι η προτεινόμενη προσέγγιση επειδή:

- **Scalability** – Το LaTeX αποδίδει σε οποιοδήποτε μέγεθος χωρίς να χάνει ποιότητα.  
- **Editability** – Μπορείτε αργότερα να τροποποιήσετε το LaTeX απευθείας στο αρχείο Markdown.  
- **Compatibility** – Οι περισσότεροι static site generators και εργαλεία τεκμηρίωσης υποστηρίζουν ήδη την απόδοση LaTeX.

Αν ποτέ χρειαστείτε την παλιά fallback με εικόνα, απλώς αλλάξτε σε `OfficeMathExportMode.IMAGE`. Σε αυτήν την περίπτωση, η ανάλυση που έχετε ορίσει γίνεται ακόμη πιο κρίσιμη.

---

## Save Word as Markdown – Full End‑to‑End Example

Παρακάτω υπάρχει ένα πλήρες, εκτελέσιμο απόσπασμα Maven project που δείχνει ολόκληρη τη ροή, από τη δήλωση εξαρτήσεων μέχρι την εκτέλεση.

```xml
<!-- pom.xml -->
<project xmlns="http://maven.apache.org/POM/4.0.0" ...>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>markdown-export</artifactId>
    <version>1.0.0</version>
    <properties>
        <maven.compiler.source>17</maven.compiler.source>
        <maven.compiler.target>17</maven.compiler.target>
    </properties>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>23.6</version>
        </dependency>
    </dependencies>
</project>
```

```java
// src/main/java/com/example/MarkdownMathExport.java
package com.example;

import com.aspose.words.*;

public class MarkdownMathExport {
    public static void main(String[] args) throws Exception {
        // Load the source Word document containing equations and images
        Document doc = new Document("src/main/resources/Math.docx");

        // Configure Markdown export options
        MarkdownSaveOptions options = new MarkdownSaveOptions();
        options.setOfficeMathExportMode(OfficeMathExportMode.LATEX); // export equations as LaTeX
        options.setImageResolution(300); // set resolution for rasterized images

        // Save as Markdown
        doc.save("output/MathExport.md", options);

        System.out.println("✅ Markdown export complete! Check output/MathExport.md");
    }
}
```

**Expected result:** `MathExport.md` θα περιέχει LaTeX blocks για κάθε εξίσωση, και τυχόν ενσωματωμένες εικόνες θα εμφανίζονται ως PNG συνδέσμους των οποίων το DPI είναι 300. Ανοίξτε το αρχείο σε έναν προβολέα Markdown που υποστηρίζει MathJax (π.χ., VS Code με την επέκταση Markdown Preview Enhanced) και θα δείτε τέλεια καθαρές εξισώσεις και εικόνες.

---

## Common Questions & Edge Cases

### What if I need a different DPI for only one image?

Το Aspose.Words εφαρμόζει το DPI καθολικά μέσω του `setImageResolution`. Για να διαχειριστείτε DPI ανά‑εικόνα, θα πρέπει να επεξεργαστείτε μετά το παραγόμενο Markdown: αντικαταστήστε τα PNG με εκδόσεις υψηλότερης ανάλυσης και προσαρμόστε χειροκίνητα τους συνδέσμους εικόνας. Δεν είναι ιδανικό, αλλά εφικτό για λίγες ειδικές περιπτώσεις.

### Does this work on Linux/macOS?

Απόλυτα. Η βιβλιοθήκη είναι καθαρά Java, οπότε ο ίδιος κώδικας τρέχει οπουδήποτε τρέχει το JDK. Απλώς βεβαιωθείτε ότι οι διαδρομές αρχείων χρησιμοποιούν forward slashes ή `Paths.get(...)` για ανεξαρτησία πλατφόρμας.

### What about SVG output?

Αν προτιμάτε διανυσματικές εικόνες για διαγράμματα, μπορείτε να ορίσετε `saveOptions.setExportImagesAsSvg(true);`. Τα SVG αγνοούν το DPI, οπότε το ζήτημα της **markdown image resolution** εξαφανίζεται. Ωστόσο, δεν υποστηρίζουν όλοι οι προβολείς Markdown SVG άψογα, οπότε δοκιμάστε πρώτα την πλατφόρμα-στόχο.

### Can I embed the generated Markdown into a static site generator?

Ναι. Η έξοδος είναι απλό `.md` με τυπική σύνταξη Markdown συν τους διαχωριστές LaTeX. Οι περισσότεροι generators (Jekyll, Hugo, MkDocs) το δέχονται αμέσως. Απλώς θυμηθείτε να ενεργοποιήσετε το MathJax ή KaTeX στη ρύθμιση του site σας.

---

## Conclusion

Καλύψαμε **πώς να ορίσετε την ανάλυση** για εικόνες όταν **αποθηκεύετε το Word ως markdown**, εξετάσαμε τις αποχρώσεις της **markdown image resolution**, δείξαμε **πώς να εξάγετε εξισώσεις** ως LaTeX και παρουσιάσαμε την πλήρη υλοποίηση σε Java. Με την προσαρμογή του `setImageResolution` και την επιλογή του κατάλληλου `OfficeMathExportMode`, αποκτάτε ακριβή έλεγχο τόσο της οπτικής πιστότητας όσο και του μεγέθους του αρχείου.

Έτοιμοι για το επόμενο βήμα; Δοκιμάστε να συνδυάσετε αυτήν την προσέγγιση με το Aspose.PDF για να μετατρέψετε την ίδια πηγή Word απευθείας σε PDF, ή πειραματιστείτε με `setExportImagesAsSvg(true)` για διανυσματικά γραφικά. Οι τεχνικές που μάθατε εδώ είναι δομικά στοιχεία για οποιοδήποτε αυτοματοποιημένο pipeline τεκμηρίωσης.

Αν βρήκατε αυτόν τον οδηγό χρήσιμο, δώστε του ένα αστέρι στο GitHub, μοιραστείτε το με συναδέλφους, ή αφήστε ένα σχόλιο παρακάτω με τις δικές σας συμβουλές. Καλή προγραμματιστική!

![How to set resolution example](resolution.png "Πώς να ορίσετε την ανάλυση κατά την αποθήκευση του Word ως Markdown")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}