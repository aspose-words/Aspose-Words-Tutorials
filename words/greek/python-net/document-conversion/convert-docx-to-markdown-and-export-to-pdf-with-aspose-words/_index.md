---
category: general
date: 2026-09-24
description: Μετατρέψτε docx σε markdown με το Aspose.Words για Python, εξάγετε εξισώσεις
  σε LaTeX, ανακτήστε κατεστραμμένα αρχεία και δημιουργήστε PDF—όλα σε ένα σενάριο.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- convert docx to markdown
- convert equations to latex
- export docx to pdf
- recover corrupted docx
- load document with recovery
language: el
lastmod: 2026-09-24
og_description: Μετατρέψτε το docx σε markdown χρησιμοποιώντας το Aspose.Words για
  Python, εξάγετε εξισώσεις σε LaTeX, ανακτήστε κατεστραμμένα αρχεία docx και δημιουργήστε
  έξοδο PDF σε ένα ενιαίο script.
og_image_alt: Python code converting a DOCX file to Markdown and PDF with Aspose.Words
og_title: Μετατροπή docx σε markdown και εξαγωγή σε PDF – Οδηγός Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Convert docx to markdown with Aspose.Words for Python, export equations
    to LaTeX, recover corrupted files, and generate PDF—all in one script.
  headline: Convert docx to markdown and export to PDF with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- Python
- Document conversion
title: Μετατροπή docx σε markdown και εξαγωγή σε PDF με το Aspose.Words
url: /el/python/document-conversion/convert-docx-to-markdown-and-export-to-pdf-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Μετατροπή docx σε markdown και εξαγωγή σε PDF με Aspose.Words

Αν χρειάζεστε **convert docx to markdown**, το Aspose.Words for Python κάνει ολόκληρη τη διαδικασία σε μία γραμμή κώδικα. Αυτός ο οδηγός σας δείχνει πώς να φορτώσετε ένα αρχείο DOCX, να το ανακτήσετε αν είναι κατεστραμμένο, να εξάγετε όλες τις εξισώσεις Office Math ως LaTeX και, τέλος, να δημιουργήσετε ένα PDF με σωστή διαχείριση σχήματος.

Θα αποκτήσετε ένα ενιαίο, εκτελέσιμο script που καλύπτει κάθε βήμα — από την ανάκτηση μέχρι το τελικό PDF — ώστε να το ενσωματώσετε σε οποιαδήποτε ροή αυτοματοποίησης.

## Τι θα χρειαστείτε

- Python 3.8 ή νεότερη  
- Πακέτο `aspose-words` (`pip install aspose-words`)  
- Ένα αρχείο DOCX που θέλετε να επεξεργαστείτε (κατεστραμμένο ή καθαρό)

Δεν απαιτούνται επιπλέον εργαλεία· το Aspose.Words διαχειρίζεται τη βαριά δουλειά εσωτερικά.

## Ανάκτηση κατεστραμμένων αρχείων docx κατά τη φόρτωση

Όταν ένα αρχείο DOCX είναι κατεστραμμένο, η προεπιλεγμένη λειτουργία φόρτωσης ρίχνει εξαίρεση. Με την αλλαγή σε **load document with recovery**, δίνετε στο Aspose.Words την ευκαιρία να επισκευάσει το αρχείο και να συνεχίσει την επεξεργασία.

```python
import aspose.words as aw

# Create LoadOptions and enable recovery mode
load_options = aw.loading.LoadOptions()
load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER   # or .REJECT to abort on errors

# Load the source DOCX; recovery will attempt to fix structural problems
doc = aw.Document("YOUR_DIRECTORY/input.docx", load_options)
```

**Γιατί είναι σημαντικό:**  
- `RECOVER` προσπαθεί να επαναδημιουργήσει τα ελλιπή μέρη, ώστε να μπορείτε ακόμη να εξάγετε περιεχόμενο.  
- `REJECT` είναι χρήσιμο όταν χρειάζεστε ένα αυστηρό βήμα επικύρωσης.

Επιλέξτε τη λειτουργία που ταιριάζει στην ανοχή σας για ελλιπή είσοδο.

## Μετατροπή docx σε markdown με Aspose.Words

Ο κύριος στόχος — **convert docx to markdown** — επιτυγχάνεται μέσω του `MarkdownSaveOptions`. Αυτή η επιλογή σας επιτρέπει επίσης να ελέγχετε πώς αποδίδονται οι εξισώσεις Office Math.

```python
# Prepare Markdown options and export equations as LaTeX
markdown_options = aw.saving.MarkdownSaveOptions()
markdown_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX

# Save the document as Markdown
doc.save("YOUR_DIRECTORY/output.md", markdown_options)
```

**Αποτέλεσμα:**  
- Όλο το κανονικό κείμενο, οι επικεφαλίδες, οι πίνακες και οι εικόνες μετατρέπονται σε τυπική σύνταξη Markdown.  
- Κάθε εξίσωση αντιπροσωπεύεται από ένα τμήμα LaTeX, το οποίο είναι ιδανικό για επιστημονική δημοσίευση.

## Μετατροπή εξισώσεων σε LaTeX κατά την αποθήκευση άλλων μορφών

Αν χρειάζεστε επίσης μια έκδοση απλού κειμένου που περιέχει τις ίδιες εξισώσεις LaTeX, χρησιμοποιήστε ξανά το ίδιο `OfficeMathExportMode`.

```python
txt_options = aw.saving.TxtSaveOptions()
txt_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.txt", txt_options)
```

Αυτό δείχνει ότι η **convert equations to latex** λειτουργεί σε πολλαπλές μορφές αποθήκευσης, όχι μόνο στο Markdown.

## Εξαγωγή docx σε PDF με σωστή διαχείριση σχήματος

Η δημιουργία ενός PDF είναι συχνά το τελικό βήμα μιας αλυσίδας επεξεργασίας εγγράφων. Το Aspose.Words προσφέρει λεπτομερή έλεγχο του τρόπου με τον οποίο αντιμετωπίζονται τα αιωρούμενα σχήματα. Η ρύθμιση `export_floating_shapes_as_inline_tag` εξασφαλίζει ότι τα σχήματα διατηρούνται ως ετικέτες inline, κάτι που πολλοί προβολείς PDF αποδίδουν πιο προβλέψιμα.

```python
pdf_options = aw.saving.PdfSaveOptions()
pdf_options.export_floating_shapes_as_inline_tag = True
doc.save("YOUR_DIRECTORY/output.pdf", pdf_options)
```

Τώρα έχετε ένα PDF υψηλής πιστότητας που αντικατοπτρίζει την αρχική διάταξη ενώ διατηρεί τα σύνθετα αντικείμενα αμετάβλητα — ακριβώς αυτό που περιμένετε όταν **export docx to pdf**.

## Προαιρετικό: λεπτομερής ρύθμιση σκιών σχήματος

Μερικές φορές η οπτική εμφάνιση ενός σχήματος έχει σημασία (π.χ., όταν το PDF θα εκτυπωθεί). Το παρακάτω απόσπασμα δείχνει πώς να προσαρμόσετε το εφέ σκιάς του πρώτου σχήματος στο έγγραφο.

```python
# Retrieve the first shape in the document tree
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

# Apply a custom shadow
shape.shadow = aw.drawing.Shadow()
shape.shadow.blur = 5.0        # blur radius in points
shape.shadow.distance = 3.0   # distance from the shape in points
```

Μπορείτε να επαναλάβετε αυτό το μπλοκ για οποιοδήποτε σχήμα χρειάζεται να τροποποιήσετε. Οι αλλαγές αντικατοπτρίζονται στην επόμενη εξαγωγή PDF.

## Πλήρες script για γρήγορη αντιγραφή‑επικόλληση

Παρακάτω βρίσκεται το πλήρες, αυτόνομο script που ενσωματώνει κάθε βήμα που περιγράφηκε παραπάνω. Αντικαταστήστε το `YOUR_DIRECTORY` με την πραγματική διαδρομή προς τα αρχεία σας.

```python
import aspose.words as aw

# -------------------------------------------------
# 1️⃣ Load the document with recovery (handles corrupted DOCX)
# -------------------------------------------------
load_options = aw.loading.LoadOptions()
load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER   # Change to .REJECT if you prefer strict validation
doc = aw.Document("YOUR_DIRECTORY/input.docx", load_options)

# -------------------------------------------------
# 2️⃣ Save as Markdown – equations become LaTeX
# -------------------------------------------------
md_opts = aw.saving.MarkdownSaveOptions()
md_opts.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.md", md_opts)

# -------------------------------------------------
# 3️⃣ Save as plain text – also with LaTeX equations
# -------------------------------------------------
txt_opts = aw.saving.TxtSaveOptions()
txt_opts.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.txt", txt_opts)

# -------------------------------------------------
# 4️⃣ Export to PDF – inline tags for floating shapes
# -------------------------------------------------
pdf_opts = aw.saving.PdfSaveOptions()
pdf_opts.export_floating_shapes_as_inline_tag = True
doc.save("YOUR_DIRECTORY/output.pdf", pdf_opts)

# -------------------------------------------------
# 5️⃣ (Optional) Adjust the first shape's shadow
# -------------------------------------------------
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
if shape is not None:
    shape.shadow = aw.drawing.Shadow()
    shape.shadow.blur = 5.0
    shape.shadow.distance = 3.0
    # Re‑save PDF to capture the shadow change
    doc.save("YOUR_DIRECTORY/output_with_shadow.pdf", pdf_opts)
```

**Αναμενόμενο αποτέλεσμα**

- `output.md` – ένα αρχείο Markdown όπου κάθε εξίσωση εμφανίζεται ως κώδικας LaTeX `$$ ... $$`.  
- `output.txt` – έκδοση απλού κειμένου με τα ίδια τμήματα LaTeX.  
- `output.pdf` – ένα πιστό PDF που αποτυπώνει το αρχικό DOCX, συμπεριλαμβανομένων τυχόν προσαρμογών σχήματος.  
- `output_with_shadow.pdf` – (εάν εκτελεστεί το βήμα 5) PDF που δείχνει τη τροποποιημένη σκιά στο πρώτο σχήμα.

## Συχνές ερωτήσεις & αντιμετώπιση ειδικών περιπτώσεων

| Ερώτηση | Απάντηση |
|----------|--------|
| *Τι γίνεται αν το DOCX είναι ακατάλληλο για επισκευή;* | Χρησιμοποιήστε `load_options.recovery_mode = aw.loading.RecoveryMode.REJECT` για να προκαλέσετε εξαίρεση, στη συνέχεια καταγράψτε το αρχείο για χειροκίνητη επανεξέταση. |
| *Μπορώ να εξάγω σε άλλες μορφές (π.χ., HTML) με εξισώσεις LaTeX;* | Ναι. Ορίστε `office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX` στο `HtmlSaveOptions` με τον ίδιο τρόπο. |
| *Χρειάζεται να εγκαταστήσω εξωτερικά εργαλεία LaTeX;* | Όχι. Το Aspose.Words γράφει τον κώδικα LaTeX απευθείας· η απόδοση εξαρτάται από τον καταναλωτή (π.χ., MathJax σε ιστοσελίδα). |
| *Πώς επεξεργάζομαι πολλά αρχεία σε έναν φάκελο;* | Τυλίξτε το script σε έναν βρόχο `for` που διατρέχει το `os.listdir()` και εφαρμόζει τα ίδια βήματα σε κάθε αρχείο. |
| *Είναι η αλλαγή σκιάς ορατή στις προεπισκοπήσεις του Word;* | Η σκιά είναι ιδιότητα σχεδίασης· εμφανίζεται στο αποθηκευμένο PDF αλλά όχι στο αρχικό DOCX, εκτός αν τροποποιήσετε επίσης την πηγή. |

## Συμπέρασμα

Τώρα έχετε μια ισχυρή, ολοκληρωμένη λύση για **convert docx to markdown**, **convert equations to latex**, **recover corrupted docx**, και **export docx to pdf** χρησιμοποιώντας το Aspose.Words for Python. Το script δείχνει τις βέλτιστες πρακτικές για φόρτωση με ανάκτηση, λεπτομερή ρύθμιση οπτικών στοιχείων και διαχείριση πολλαπλών μορφών εξόδου σε μία μόνο εκτέλεση.

**Επόμενα βήματα**  
- Εξερευνήστε άλλες `SaveOptions` όπως `HtmlSaveOptions` ή `EpubSaveOptions`.  
- Συνδυάστε αυτή τη ροή εργασίας με έναν επεξεργαστή παρτίδας για να μετατρέψετε ολόκληρες βιβλιοθήκες εγγράφων

## Τι θα πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετικές θεματικές που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Μετατροπή DOCX σε Markdown – Πλήρης Οδηγός με χρήση Aspose.Words](/words/english/net/programming-with-markdownsaveoptions/convert-docx-to-markdown-complete-guide-using-aspose-words/)
- [Ανάκτηση Κατεστραμμένου DOCX – Πλήρης Οδηγός για Διόρθωση, Εξαγωγή PDF & Markdown](/words/english/net/basic-conversions/recover-corrupted-docx-full-guide-to-fix-pdf-markdown-export/)
- [Μετατροπή docx σε markdown και εξαγωγή εικόνων με Aspose.Words – Πλήρης οδηγός C#](/words/english/net/programming-with-markdownsaveoptions/save-docx-as-markdown-extract-images-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}