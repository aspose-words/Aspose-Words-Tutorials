---
category: general
date: 2026-04-28
description: Δημιουργήστε έγγραφο PDF UA χρησιμοποιώντας το Aspose.Words για Java.
  Μάθετε πώς να φορτώνετε docx με αποκατάσταση, να εξάγετε εξισώσεις σε LaTeX, να
  αποθηκεύετε markdown από το Word και να ανακτάτε ελλιπείς γραμματοσειρές.
draft: false
keywords:
- create PDF UA document
- retrieve missing fonts
- export equations to LaTeX
- save markdown from Word
- load docx with recovery
language: el
og_description: Δημιουργήστε έγγραφο PDF UA με το Aspose.Words for Java. Οδηγός βήμα‑βήμα
  που καλύπτει τη φόρτωση ανάκτησης, την εξαγωγή σε LaTeX, την αποθήκευση σε Markdown
  και την ανάκτηση ελλιπών γραμματοσειρών.
og_title: Δημιουργία εγγράφου PDF UA – Πλήρες μάθημα Java
tags:
- Aspose.Words
- Java
- PDF/UA
title: Δημιουργία εγγράφου PDF UA με το Aspose.Words – Πλήρης οδηγός Java
url: /el/java/document-conversion-and-export/create-pdf-ua-document-with-aspose-words-full-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία εγγράφου PDF UA – Πλήρες Java Tutorial

Χρειάζεστε **να δημιουργήσετε έγγραφο PDF UA** από ένα αρχείο Word ενώ διαχειρίζεστε κατεστραμμένο περιεχόμενο; Σε αυτό το tutorial θα σας καθοδηγήσουμε στη φόρτωση ενός DOCX με ανάκτηση, την εξαγωγή εξισώσεων σε LaTeX, την αποθήκευση Markdown από το Word και την ανάκτηση των ελλιπών γραμματοσειρών—όλα με το Aspose.Words for Java.  

Αν έχετε ποτέ κολλήσει σε ένα σπασμένο .docx και αναρωτηθήκατε γιατί το PDF σας δεν είναι προσβάσιμο, βρίσκεστε στο σωστό μέρος. Στο τέλος θα έχετε ένα πλήρως συμβατό αρχείο PDF/UA 1, μια έκδοση Markdown που περιέχει εξισώσεις LaTeX, και έναν σαφή κατάλογο τυχόν αντικαταστάσεων γραμματοσειρών που συνέβησαν κατά τη φόρτωση.

## Τι θα χρειαστείτε

- **Aspose.Words for Java** (τελευταία έκδοση έως 2026) – προσθέστε την εξάρτηση Maven/Gradle ή το JAR στο classpath σας.  
- Java 17 ή νεότερη (το API χρησιμοποιεί streams, επομένως συνιστάται πρόσφατο JDK).  
- Ένα δείγμα `input.docx` που μπορεί να περιέχει κατεστραμμένα τμήματα, εξισώσεις Office Math και αιωρούμενα σχήματα.  

Δεν απαιτούνται επιπλέον βιβλιοθήκες· όλα βρίσκονται μέσα στο Aspose.Words.

---

## Βήμα 1 – Φόρτωση DOCX με Λειτουργία Ανάκτησης  

Όταν ένα έγγραφο είναι μερικώς κατεστραμμένο, ο προεπιλεγμένος φορτωτής ρίχνει εξαίρεση. Ενεργοποιώντας τη λειτουργία ανάκτησης λέτε στο Aspose.Words να συνεχίσει και να εμφανίσει προειδοποιήσεις αντί για σφάλμα.

```java
import com.aspose.words.*;

public class LatestFeaturesDemo {

    public static void main(String[] args) throws Exception {

        // 1️⃣ Load the document with recovery to gracefully handle corruption
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.RECOVER_WITH_WARNINGS);
        Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

*Γιατί είναι σημαντικό:* Η λειτουργία ανάκτησης αποτρέπει το σπάσιμο ολόκληρης της αλυσίδας σας λόγω ενός μόνο κακού παραγράφου. Επίσης γεμίζει το `doc.getWarnings()` ώστε να μπορείτε αργότερα **να ανακτήσετε τις ελλιπείς γραμματοσειρές** και άλλα ζητήματα.

---

## Βήμα 2 – Εξαγωγή Εξισώσεων σε LaTeX μέσα σε Αρχείο Markdown  

Οι περισσότεροι προγραμματιστές αγαπούν το Markdown για τεκμηρίωση, αλλά οι ενσωματωμένες εξισώσεις του Word είναι δύσκολο να αντιγραφούν. Το Aspose.Words μπορεί να τις μεταφράσει απευθείας σε LaTeX.

```java
        // 2️⃣ Configure Markdown export with LaTeX for Office Math
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
        mdOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);

        // Store images in a sub‑folder so the Markdown stays tidy
        mdOptions.setResourceSavingCallback(resourceInfo -> {
            if (resourceInfo.getResourceType() == ResourceType.IMAGE) {
                resourceInfo.setResourceFileName("imgs/" + resourceInfo.getResourceFileName());
            }
        });

        // Save the Markdown file
        doc.save("YOUR_DIRECTORY/output.md", mdOptions);
```

*Συμβουλή:* Η callback εξασφαλίζει ότι κάθε εξαγόμενο εικόνα τοποθετείται στο `imgs/`. Αυτό αντικατοπτρίζει τον τρόπο που το GitHub αποδίδει το Markdown – καθαρό και φορητό.

---

## Βήμα 3 – Δημιουργία εγγράφου PDF / UA με Σωστή Ετικετοποίηση  

Η συμμόρφωση PDF/UA (Universal Accessibility) είναι υποχρεωτική για πολλά δημόσια έργα. Οι παρακάτω επιλογές κάνουν το Aspose.Words να ετικετοποιεί σωστά τα αιωρούμενα σχήματα και να θέτει τη σημαία συμμόρφωσης PDF/UA.

```java
        // 3️⃣ Prepare PDF/UA export options
        PdfSaveOptions pdfOptions = new PdfSaveOptions();
        pdfOptions.setCompliance(PdfCompliance.PDF_UA_1);          // Enforce PDF/UA‑1
        pdfOptions.setExportFloatingShapesAsInlineTag(true);      // Tag floating shapes

        // Save the accessible PDF
        doc.save("YOUR_DIRECTORY/output.pdf", pdfOptions);
```

*Τι θα δείτε:* Ανοίγοντας το `output.pdf` στο Adobe Acrobat Pro θα εμφανιστεί “PDF/UA‑1 compliant” στις ιδιότητες του εγγράφου. Όλα τα αιωρούμενα σχήματα (πλαίσια κειμένου, εικόνες) θα έχουν τις κατάλληλες ετικέτες για αναγνώστες οθόνης.

---

## Βήμα 4 – Προσαρμογή Σκιάς Σχήματος (Προαιρετικό Στυλ)  

Αν και δεν απαιτείται για προσβασιμότητα, η προσαρμογή οπτικών στοιχείων μπορεί να φανεί χρήσιμη για εσωτερικές αναφορές.

```java
        // 4️⃣ Grab the first shape and modify its shadow
        Shape firstShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        ShadowFormat shadow = firstShape.getShadowFormat();
        shadow.setBlurRadius(4);
        shadow.setDistanceX(2);
        shadow.setDistanceY(2);
        shadow.setColor(java.awt.Color.GRAY);
```

*Γιατί να το κάνετε;* Αν το PDF είναι επίσης διαφημιστικό υλικό, μια διακριτική σκιά κάνει τη διάταξη πιο επαγγελματική χωρίς να παραβιάζει τη συμμόρφωση.

---

## Βήμα 5 – Ανάκτηση Ελλιπών Γραμματοσειρών και Άλλων Προειδοποιήσεων  

Κατά τη φόρτωση με ανάκτηση, το Aspose.Words καταγράφει τυχόν αντικαταστάσεις γραμματοσειρών. Η λίστα τους σας βοηθά να αποφασίσετε αν θα ενσωματώσετε τη σωστή γραμματοσειρά ή θα αποδεχθείτε την εναλλακτική.

```java
        // 5️⃣ Enumerate font‑substitution warnings
        System.out.println("=== Font Substitution Report ===");
        for (WarningInfo warning : doc.getWarnings()) {
            if (warning instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fsw = (FontSubstitutionWarning) warning;
                System.out.println("Missing: " + fsw.getMissingFontName() +
                                   " → substituted: " + fsw.getSubstitutedFontName());
            }
        }

        // You can also handle other warning types here (e.g., content loss)
    }
}
```

*Τυπική έξοδος* (η κονσόλα σας θα εμφανίσει κάτι σαν):

```
=== Font Substitution Report ===
Missing: Calibri → substituted: Arial
Missing: Times New Roman → substituted: Liberation Serif
```

Αν δείτε κρίσιμες γραμματοσειρές που λείπουν, σκεφτείτε να τις εγκαταστήσετε στον διακομιστή ή να τις ενσωματώσετε μέσω `PdfSaveOptions.setEmbedFullFonts(true)`.

---

## Πλήρες Παράδειγμα Εργασίας  

Παρακάτω βρίσκεται η πλήρης, έτοιμη προς εκτέλεση κλάση Java. Επικολλήστε την στο IDE σας, προσαρμόστε τις διαδρομές και πατήστε **Run**.

```java
import com.aspose.words.*;
import java.awt.Color;

/**
 * Demonstrates how to:
 *  • load a DOCX with recovery,
 *  • export equations to LaTeX inside Markdown,
 *  • create a PDF/UA‑1 compliant PDF,
 *  • modify shape shadows,
 *  • and list any font‑substitution warnings.
 */
public class LatestFeaturesDemo {
    public static void main(String[] args) throws Exception {

        // ---- Step 1: Load DOCX with recovery ----
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.RECOVER_WITH_WARNINGS);
        Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // ---- Step 2: Export equations to LaTeX in Markdown ----
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
        mdOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);
        mdOptions.setResourceSavingCallback(resourceInfo -> {
            if (resourceInfo.getResourceType() == ResourceType.IMAGE) {
                resourceInfo.setResourceFileName("imgs/" + resourceInfo.getResourceFileName());
            }
        });
        doc.save("YOUR_DIRECTORY/output.md", mdOptions);

        // ---- Step 3: Save as PDF/UA with proper tagging ----
        PdfSaveOptions pdfOptions = new PdfSaveOptions();
        pdfOptions.setCompliance(PdfCompliance.PDF_UA_1);
        pdfOptions.setExportFloatingShapesAsInlineTag(true);
        doc.save("YOUR_DIRECTORY/output.pdf", pdfOptions);

        // ---- Step 4: Optional – adjust the first shape’s shadow ----
        Shape firstShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        ShadowFormat shadow = firstShape.getShadowFormat();
        shadow.setBlurRadius(4);
        shadow.setDistanceX(2);
        shadow.setDistanceY(2);
        shadow.setColor(Color.getGray());

        // ---- Step 5: List any missing‑font warnings ----
        System.out.println("=== Font Substitution Report ===");
        for (WarningInfo warning : doc.getWarnings()) {
            if (warning instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fsw = (FontSubstitutionWarning) warning;
                System.out.println("Missing: " + fsw.getMissingFontName()
                                   + " → substituted: " + fsw.getSubstitutedFontName());
            }
        }
    }
}
```

**Αναμενόμενα αποτελέσματα**

| Έξοδος | Περιγραφή |
|--------|-------------|
| `output.md` | Αρχείο Markdown όπου κάθε εξίσωση Office Math εμφανίζεται ως LaTeX (`$…$`). Οι εικόνες αποθηκεύονται στο `imgs/`. |
| `output.pdf` | Έγγραφο PDF/UA‑1 συμβατό· ανοίξτε το στο Acrobat για να δείτε “PDF/UA‑1” στο File → Properties → Standards. |
| Console | Λίστα τυχόν ελλιπών γραμματοσειρών, π.χ. “Missing: Calibri → substituted: Arial”. |

---

## Συχνές Ερωτήσεις (FAQ)

**Ε: Λειτουργεί αυτό με παλαιότερες εκδόσεις Aspose.Words;**  
Α: Τα enums `RecoveryMode`, `OfficeMathExportMode.LATEX` και `PdfCompliance.PDF_UA_1` εισήχθησαν στην έκδοση 22.8. Αν χρησιμοποιείτε παλαιότερη έκδοση, κάντε αναβάθμιση – τα χαρακτηριστικά προσβασιμότητας δεν έχουν μεταφερθεί πίσω.

**Ε: Τι κάνω αν θέλω να ενσωματώσω τις αρχικές γραμματοσειρές αντί για αντικατάσταση;**  
Α: Ορίστε `pdfOptions.setEmbedFullFonts(true)` και βεβαιωθείτε ότι τα αρχεία γραμματοσειρών είναι προσβάσιμα στη διαδρομή γραμματοσειρών του JVM.

**Ε: Μπορώ να εξάγω σε άλλες μορφές markup (π.χ. HTML) διατηρώντας τις εξισώσεις LaTeX;**  
Α: Ναι. Χρησιμοποιήστε `HtmlSaveOptions` και ορίστε `setOfficeMathExportMode(OfficeMathExportMode.LATEX)` – το ίδιο enum λειτουργεί σε όλες τις μορφές.

**Ε: Το DOCX μου περιέχει πολλά αιωρούμενα σχήματα· θα ετικετοποιηθούν όλα;**  
Α: Με `setExportFloatingShapesAsInlineTag(true)`, το Aspose.Words τυλίγει κάθε αιωρούμενο σχήμα σε ετικέτα `<Figure>` για PDF/UA, ικανοποιώντας τις περισσότερες ελέγχους αναγνωστών οθόνης.

---

## Συμπεράσματα  

Σας δείξαμε πώς να **δημιουργήσετε έγγραφο PDF UA** από πηγή Word, ενώ επίσης **φορτώνετε docx με ανάκτηση**, **εξάγετε εξισώσεις σε LaTeX**, **αποθηκεύετε markdown από το Word**, και **ανακτάτε ελλιπείς γραμματοσειρές**. Ο κώδικας είναι πλήρως αυτόνομος, τρέχει σε οποιοδήποτε περιβάλλον Java 17+ και παράγει περιουσιακά στοιχεία έτοιμα τόσο για ελέγχους προσβασιμότητας όσο και για developer

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}