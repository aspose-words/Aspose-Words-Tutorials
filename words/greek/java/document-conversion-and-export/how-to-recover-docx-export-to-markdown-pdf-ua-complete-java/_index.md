---
category: general
date: 2026-02-18
description: Μάθετε πώς να ανακτήσετε αρχεία docx, να εξάγετε docx σε markdown με
  μαθηματικά LaTeX και να επιτύχετε συμμόρφωση PDF/UA σε Java.
draft: false
keywords:
- how to recover docx
- export docx to markdown
- markdown with latex math
- pdf ua compliance
- save as pdf ua
language: el
og_description: Πώς να ανακτήσετε αρχεία docx, να τα εξάγετε σε markdown με μαθηματικά
  LaTeX και να τα αποθηκεύσετε ως PDF/UA χρησιμοποιώντας Java.
og_title: Πώς να ανακτήσετε DOCX, να εξάγετε σε Markdown & PDF/UA – Εγχειρίδιο Java
tags:
- Aspose.Words
- Java
- Document Conversion
- PDF/UA
title: Πώς να ανακτήσετε DOCX, εξαγωγή σε Markdown & PDF/UA – Πλήρης οδηγός Java
url: /el/java/document-conversion-and-export/how-to-recover-docx-export-to-markdown-pdf-ua-complete-java/
---

The answer missing. We keep as is.

Now close shortcodes.

Let's craft final output.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να Επαναφέρετε DOCX, Εξαγωγή σε Markdown & PDF/UA – Πλήρης Οδηγός Java

Έχετε αναρωτηθεί ποτέ **πώς να επαναφέρετε docx** αρχεία που μπορεί να είναι κατεστραμμένα; Ίσως έχετε προσπαθήσει να ανοίξετε ένα έγγραφο Word μόνο για να λάβετε εκείνο το τρομακτικό μήνυμα “το αρχείο είναι κατεστραμμένο”. Κατά την εμπειρία μου, ο πόνος ενός σπασμένου DOCX μπορεί να αποφευχθεί με λίγες γραμμές κώδικα Java—ιδιαίτερα όταν χρησιμοποιείτε μια βιβλιοθήκη που υποστηρίζει λειτουργία ανάκτησης.  

Σε αυτό το tutorial δεν θα σας δείξουμε μόνο **πώς να επαναφέρετε docx**, αλλά θα σας καθοδηγήσουμε επίσης στη **εξαγωγή docx σε markdown** (με υποστήριξη μαθηματικών LaTeX) και τελικά στο **αποθήκευση ως pdf ua** για συμμόρφωση με PDF/UA. Στο τέλος θα έχετε ένα ενιαίο, εκτελέσιμο πρόγραμμα που μετατρέπει ένα ασταθές DOCX σε καθαρό Markdown και σε πλήρως συμβατό αρχείο PDF/UA.

> **Τι θα πάρετε:** μια βήμα‑βήμα λύση, πλήρες πηγαίο κώδικα, εξηγήσεις του *γιατί* κάθε κλήση API είναι σημαντική, και μια σειρά από επαγγελματικές συμβουλές ώστε να μην πέσετε σε κοινές παγίδες.

## Προαπαιτούμενα

- Java 17 ή νεότερη (ο κώδικας μεταγλωττίζεται με οποιοδήποτε πρόσφατο JDK).  
- Aspose.Words for Java 23.10 ή νεότερη – η βιβλιοθήκη που μας παρέχει `LoadOptions`, `MarkdownSaveOptions`, `PdfSaveOptions`, κ.λπ.  
- Ένα αρχείο DOCX που υποπτεύεστε ότι μπορεί να είναι κατεστραμμένο (θα το ονομάσουμε `input.docx`).  
- Βασική εξοικείωση με τη σύνταξη της Java—δεν απαιτούνται βαθιές γνώσεις εσωτερικών λειτουργιών.

Αν λείπει το JAR του Aspose.Words, κατεβάστε το από το επίσημο αποθετήριο Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
</dependency>
```

Τώρα που τα θεμέλια είναι έτοιμα, ας βουτήξουμε στη διαδικασία ανάκτησης.

## Πώς να Επαναφέρετε DOCX – Φόρτωση με Λειτουργία Ανάκτησης

Όταν ένα DOCX είναι μερικώς κατεστραμμένο, το Aspose.Words μπορεί να το ανοίξει σε *recovery mode*. Αυτό λέει στη μηχανή να συνεχίσει ακόμη και αν αντιμετωπίσει προειδοποιήσεις, και να εμφανίσει αυτές τις προειδοποιήσεις για να τις ελέγξετε αργότερα.

```java
import com.aspose.words.*;

public class LatestFeaturesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Load a possibly corrupted document using recovery mode
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.RECOVER_WITH_WARNINGS);
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**Γιατί λειτουργία ανάκτησης;**  
Χωρίς αυτήν, ο κατασκευαστής `Document` θα ρίξει εξαίρεση τη στιγμή που εντοπίσει ένα κακοδιαμορφωμένο τμήμα, διακόπτοντας όλη τη διαδικασία. Επιλέγοντας `RECOVER_WITH_WARNINGS`, λαμβάνετε ένα χρήσιμο αντικείμενο `Document` και μια λίστα προειδοποιήσεων που μπορείτε να καταγράψετε ή να αγνοήσετε, ανάλογα με το πόσο κρίσιμα είναι τα σφάλματα.

> **Συμβουλή επαγγελματία:** Μετά τη φόρτωση, μπορείτε να διατρέξετε το `document.getWarnings()` για να καταγράψετε τυχόν προβλήματα. Αυτό είναι χρήσιμο για ιχνηλασιμότητα.

## Ρύθμιση της Σκιάς του Πρώτου Σχήματος (Προαιρετικό αλλά Εικονογραφικό)

Αν και δεν είναι απολύτως απαραίτητο για την ανάκτηση, η προσαρμογή ενός σχήματος δείχνει πώς μπορείτε να χειριστείτε το έγγραφο *μετά* την αποκατάσταση. Σε πολλές πραγματικές περιπτώσεις θα θέλετε να καθαρίσετε ή να επαναστυλιζάσετε στοιχεία που επέζησαν της κατεστραμμένης κατάστασης.

```java
        // Step 2: Fine‑tune the shadow of the first shape in the document
        Shape firstShape = (Shape) document.getChild(NodeType.SHAPE, 0, true);
        Shadow shapeShadow = firstShape.getShadow();
        shapeShadow.setBlurRadius(4);
        shapeShadow.setOffsetX(2);
        shapeShadow.setOffsetY(2);
        shapeShadow.setColor(Color.getRed());
        shapeShadow.setOpacity(0.5);
```

**Τι συμβαίνει εδώ;**  
Αναζητούμε τον πρώτο κόμβο `Shape` οπουδήποτε στο αρχείο (`true` σημαίνει βαθιά αναζήτηση). Στη συνέχεια τροποποιούμε τις ιδιότητες `Shadow`—θολότητα, μετατοπίσεις, χρώμα και αδιαφάνεια—για να του δώσουμε ένα διακριτικό εφέ σκιάς. Αν το αρχικό DOCX δεν περιείχε σχήματα, το `firstShape` θα είναι `null`; προστατέψτε τον κώδικά σας κατά την παραγωγή.

## Εξαγωγή DOCX σε Markdown – Υποστήριξη Μαθηματικών LaTeX

Τώρα που το έγγραφο είναι ζωντανό, ας **εξάγουμε docx σε markdown**. Η κλάση `MarkdownSaveOptions` μας δίνει έλεγχο πάνω στο πώς αποδίδονται οι εξισώσεις Office Math. Επιλέγοντας `OfficeMathExportMode.LATEX`, το αρχείο markdown θα περιέχει αποσπάσματα LaTeX που αποδίδονται όμορφα στα περισσότερα markdown viewers.

```java
        // Step 3: Save the document as Markdown with LaTeX math and custom resource handling
        MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions();
        markdownOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);
        markdownOptions.setResourceSavingCallback(args -> {
            String resourceFolder = "YOUR_DIRECTORY/md-res/";
            new java.io.File(resourceFolder).mkdirs();
            args.setOutputFileName(resourceFolder + args.getResourceFileName());
        });
        document.save("YOUR_DIRECTORY/demo.md", markdownOptions);
```

**Γιατί LaTeX;**  
Οι markdown επεξεργαστές όπως GitHub, GitLab ή στατικούς δημιουργούς ιστοσελίδων (Hugo, Jekyll) συχνά έχουν ενσωματωμένη υποστήριξη MathJax ή KaTeX. Η εξαγωγή εξισώσεων ως LaTeX εξασφαλίζει ότι παραμένουν ευκρινείς, κλιμακώσιμες και επεξεργάσιμες. Η παραπάνω κλήση επιστροφής (callback) διασφαλίζει ότι τυχόν εξαγόμενες εικόνες (π.χ. ενσωματωμένες φωτογραφίες) γράφονται σε έναν αφιερωμένο φάκελο, κρατώντας το markdown καθαρό.

### Αναμενόμενη Έξοδος Markdown

- Όλο το απλό κείμενο εμφανίζεται ως κανονικές παραγράφους markdown.  
- Οι εξισώσεις μετατρέπονται σε `$…$` για ενσωματωμένο ή `$$…$$` για προβολή μαθηματικών.  
- Οι εικόνες αναφέρονται με `![](md-res/image1.png)` που δείχνει στον φάκελο που δημιουργήσατε.

Ανοίξτε το `demo.md` στον αγαπημένο σας επεξεργαστή—θα πρέπει να δείτε κάτι όπως:

```markdown
Here is an inline equation $E = mc^2$ that renders nicely.

$$
\int_{a}^{b} f(x)\,dx = F(b) - F(a)
$$

![](md-res/shape1.png)
```

## Συμμόρφωση PDF/UA – Αποθήκευση ως PDF/UA

Τέλος, θα **αποθηκεύσουμε ως pdf ua** για να καλύψουμε το πρότυπο PDF/UA‑1, το οποίο είναι ουσιώδες για προσβασιμότητα. Η κλάση `PdfSaveOptions` μας επιτρέπει να εναλλάξουμε τη συμμόρφωση και να αποφασίσουμε πώς θα αντιμετωπίζονται τα αιωρούμενα σχήματα.

```java
        // Step 4: Save the document as PDF/UA, exporting floating shapes as inline tags
        PdfSaveOptions pdfOptions = new PdfSaveOptions();
        pdfOptions.setCompliance(PdfCompliance.PDF_UA_1);
        pdfOptions.setExportFloatingShapesAsInlineTag(true);
        document.save("YOUR_DIRECTORY/demo-ua.pdf", pdfOptions);
    }
}
```

**Τι κάνει η μέθοδος `setExportFloatingShapesAsInlineTag(true)`;**  
Τα αιωρούμενα σχήματα (όπως πλαίσια κειμένου) μπορούν να προκαλέσουν προβλήματα προσβασιμότητας επειδή οι αναγνώστες οθόνης μπορεί να τα παραλείψουν. Εξάγοντάς τα ως ενσωματωμένες ετικέτες, τα σχήματα γίνονται μέρος της σειράς ανάγνωσης, ικανοποιώντας τις απαιτήσεις **pdf ua compliance**.

### Επαλήθευση PDF/UA

Ανοίξτε το παραγόμενο `demo-ua.pdf` στο Adobe Acrobat Pro και εκτελέστε *Accessibility Check* → *Full Check*. Θα πρέπει να δείτε ένα πράσινο σημάδι ελέγχου για συμμόρφωση PDF/UA‑1. Αν εμφανιστούν προειδοποιήσεις, θα δείχνουν σε στοιχεία που χρειάζονται ακόμη προσοχή (π.χ. έλλειψη alt text για εικόνες).

## Πλήρες Παράδειγμα Εργασίας (Έτοιμο για Αντιγραφή‑Επικόλληση)

```java
import com.aspose.words.*;
import java.awt.Color;
import java.io.File;

public class LatestFeaturesDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Recover the possibly corrupted DOCX
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.RECOVER_WITH_WARNINGS);
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // 2️⃣ (Optional) Tweak the first shape’s shadow
        Shape firstShape = (Shape) document.getChild(NodeType.SHAPE, 0, true);
        if (firstShape != null) {
            Shadow shapeShadow = firstShape.getShadow();
            shapeShadow.setBlurRadius(4);
            shapeShadow.setOffsetX(2);
            shapeShadow.setOffsetY(2);
            shapeShadow.setColor(Color.getRed());
            shapeShadow.setOpacity(0.5);
        }

        // 3️⃣ Export to Markdown with LaTeX math
        MarkdownSaveOptions markdownOptions = new MarkdownSaveOptions();
        markdownOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);
        markdownOptions.setResourceSavingCallback(args -> {
            String resourceFolder = "YOUR_DIRECTORY/md-res/";
            new File(resourceFolder).mkdirs();
            args.setOutputFileName(resourceFolder + args.getResourceFileName());
        });
        document.save("YOUR_DIRECTORY/demo.md", markdownOptions);

        // 4️⃣ Save as PDF/UA compliant file
        PdfSaveOptions pdfOptions = new PdfSaveOptions();
        pdfOptions.setCompliance(PdfCompliance.PDF_UA_1);
        pdfOptions.setExportFloatingShapesAsInlineTag(true);
        document.save("YOUR_DIRECTORY/demo-ua.pdf", pdfOptions);
    }
}
```

Τρέξτε αυτήν την κλάση από το IDE ή τη γραμμή εντολών—βεβαιωθείτε ότι τα placeholders `YOUR_DIRECTORY` δείχνουν σε έναν υπάρχοντα φάκελο στο σύστημά σας. Αν όλα πάνε καλά, θα έχετε:

- `demo.md` – καθαρό markdown που περιέχει εξισώσεις LaTeX.  
- `md-res/` – φάκελος με τυχόν εξαγόμενες εικόνες.  
- `demo-ua.pdf` – PDF/UA‑1 συμβατό αρχείο PDF έτοιμο για διανομή.

## Συχνές Ερωτήσεις & Ακραίες Περιπτώσεις

| Ερώτηση | Απάντηση |
|----------|--------|
| **Τι γίνεται αν το DOCX είναι εντελώς μη αναγνώσιμο;** | Η λειτουργία ανάκτησης θα προσπαθήσει όσο μπορεί, αλλά μπορεί να καταλήξετε με έγγραφο που λείπουν μεγάλες ενότητες. Σε τέτοιες περιπτώσεις, σκεφτείτε πρώτα τη χρήση εργαλείου τρίτου μέρους για επισκευή, και μετά φορτώστε με Aspose. |
| **Μπορώ να εξάγω σε άλλες γεύσεις markdown;** | Ναι—το `MarkdownSaveOptions` υποστηρίζει επίσης GitHub‑flavored markdown μέσω `setSaveFormat(SaveFormat.MARKDOWN)`. Η εξαγωγή LaTeX παραμένει η ίδια. |
| **Πρέπει να ορίσω alt text για τις εικόνες ώστε να ικανοποιηθεί το PDF/UA;** | Απόλυτα. Μετά τη φόρτωση, διατρέξτε τους κόμβους `Shape` τύπου `IMAGE` και καλέστε `setAlternativeText("Description")`. Αυτό εξασφαλίζει ότι το PDF περνάει τον έλεγχο *alternative text*. |
| **Πώς να διαχειριστώ μεγάλα έγγραφα χωρίς να εξαντλήσω τη μνήμη;** |

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}