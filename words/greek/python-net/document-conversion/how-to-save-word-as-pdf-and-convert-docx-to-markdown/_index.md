---
category: general
date: 2026-10-23
description: Μάθετε πώς να αποθηκεύσετε το Word ως PDF και να μετατρέψετε το DOCX
  σε Markdown χρησιμοποιώντας το Aspose.Words για Python, με λειτουργία ανάκτησης
  και υποστήριξη μαθηματικών LaTeX.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save word as pdf
- convert docx to markdown
- enable recovery mode
- markdown latex math
- export equations latex
language: el
lastmod: 2026-10-23
og_description: Αποθηκεύστε το Word ως PDF και μετατρέψτε το DOCX σε Markdown με το
  Aspose.Words για Python. Ο οδηγός καλύπτει τη λειτουργία ανάκτησης, την εξαγωγή
  μαθηματικών LaTeX και τη διαχείριση σχημάτων PDF.
og_image_alt: Screenshot illustrating how to save Word as PDF using Aspose.Words in
  Python
og_title: Αποθήκευση Word ως PDF και Μετατροπή DOCX σε Markdown – Πλήρης Οδηγός Python
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Learn how to save Word as PDF and convert DOCX to Markdown using Aspose.Words
    for Python, with recovery mode and LaTeX math support.
  headline: How to save Word as PDF and convert DOCX to Markdown
  type: TechArticle
tags:
- Aspose.Words
- Python
- PDF conversion
- Markdown
- LaTeX
title: Πώς να αποθηκεύσετε το Word ως PDF και να μετατρέψετε το DOCX σε Markdown
url: /el/python/document-conversion/how-to-save-word-as-pdf-and-convert-docx-to-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να αποθηκεύσετε το Word ως PDF και να μετατρέψετε το DOCX σε Markdown

Αν χρειάζεστε να **αποθηκεύσετε το Word ως PDF** ενώ ταυτόχρονα μετατρέπετε το ίδιο αρχείο DOCX σε Markdown, αυτό το σεμινάριο σας δείχνει μια ενιαία, επαναλήψιμη ροή εργασίας. Θα δείτε πώς το Aspose.Words for Python μπορεί να διαχειριστεί κατεστραμμένα αρχεία προέλευσης, να εξάγει εξισώσεις ως LaTeX και να σας παρέχει λεπτομερή έλεγχο πάνω στα αιωρούμενα σχήματα στην έξοδο PDF.

Ο οδηγός περνάει από κάθε απαιτούμενη εισαγωγή, διαμόρφωση επιλογών και κλήση αποθήκευσης, ώστε να μπορείτε να αντιγράψετε‑επικολλήσετε ένα λειτουργικό script στο έργο σας σήμερα.

![Διάγραμμα που απεικονίζει πώς να αποθηκεύσετε το Word ως PDF χρησιμοποιώντας το Aspose.Words σε Python](image-placeholder.png "Διάγραμμα που δείχνει τη ροή εργασίας αποθήκευσης του Word ως PDF")

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

* Εγκατεστημένο Python 3.8+.
* Έγκυρη άδεια Aspose.Words for Python (ή δωρεάν δοκιμή).
* Πακέτο `aspose-words` εγκατεστημένο μέσω `pip install aspose-words`.
* Ένα αρχείο DOCX που θέλετε να επεξεργαστείτε (το παράδειγμα χρησιμοποιεί το `input.docx`).

Έχοντας αυτά έτοιμα εξασφαλίζει ότι ο κώδικας εκτελείται χωρίς πρόσθετα βήματα ρύθμισης.

## Βήμα 1: Φόρτωση του αρχικού εγγράφου

Η πρώτη ενέργεια είναι το άνοιγμα του αρχείου DOCX. Το Aspose.Words διαβάζει το αρχείο σε ένα αντικείμενο `Document`, το οποίο γίνεται η πηγή για όλες τις επόμενες αποθηκεύσεις.

```python
import aspose.words as aw

# Load the DOCX file from the file system
doc = aw.Document("YOUR_DIRECTORY/input.docx")
```

> **Γιατί είναι σημαντικό:** Η φόρτωση του εγγράφου δημιουργεί μια αναπαράσταση στη μνήμη που σας επιτρέπει να εφαρμόζετε διαφορετικές επιλογές αποθήκευσης χωρίς να ξαναδιαβάζετε το αρχείο.

## Βήμα 2: Ενεργοποίηση λειτουργίας ανάκτησης για ευγενική διαχείριση κατεστραμμένων εγγράφων

Αν το αρχικό DOCX μπορεί να είναι κατεστραμμένο — λείπουν μέρη, σπασμένο XML ή απρόσμενα ρεύματα — ενεργοποιήστε τη **λειτουργία ανάκτησης**. Αυτό λέει στο Aspose.Words να αγνοεί μη‑κριτικά σφάλματα και να παράγει ακόμη και έξοδο.

```python
# Configure load options for recovery
load_opts = aw.LoadOptions()
load_opts.recovery_mode = aw.LoadOptions.RecoveryMode.RECOVER
# Re‑load the document using the recovery options
doc = aw.Document("YOUR_DIRECTORY/input.docx", load_opts)
```

> **Η ενεργοποίηση της λειτουργίας ανάκτησης** είναι ιδιαίτερα χρήσιμη σε δέσμες επεξεργασίας όπου ένα μόνο κατεστραμμένο αρχείο δεν πρέπει να σταματήσει όλη τη διαδικασία.

## Βήμα 3: Προετοιμασία επιλογών αποθήκευσης Markdown – εξαγωγή εξισώσεων Office Math ως LaTeX

Όταν **μετατρέπετε DOCX σε Markdown**, συχνά θέλετε οι εξισώσεις να εμφανίζονται ως LaTeX ώστε τα επόμενα εργαλεία (π.χ., Jupyter, γεννήτριες στατικών ιστοσελίδων) να τις αποδίδουν σωστά.

```python
# Markdown options with LaTeX export for equations
md_opts = aw.saving.MarkdownSaveOptions()
md_opts.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
```

> **Η υποστήριξη Markdown LaTeX math** εξασφαλίζει ότι σύνθετοι τύποι παραμένουν αμετάβλητοι κατά τη μετατροπή, διατηρώντας την επιστημονική ακεραιότητα.

## Βήμα 4: Προετοιμασία επιλογών αποθήκευσης απλού κειμένου – επίσης εξαγωγή Office Math ως LaTeX

Ακόμα και αν χρειάζεστε μόνο μια έκδοση `.txt`, η διατήρηση των εξισώσεων ως LaTeX μπορεί να είναι χρήσιμη για επόμενη ανάλυση.

```python
# Plain‑text options with LaTeX export
txt_opts = aw.saving.TxtSaveOptions()
txt_opts.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
```

## Βήμα 5: Προετοιμασία επιλογών αποθήκευσης PDF – έλεγχος του τρόπου ετικετοποίησης αιωρούμενων σχημάτων

Τα αιωρούμενα σχήματα (πλαίσια κειμένου, εικόνες) μπορούν να αναπαρασταθούν στο PDF είτε ως ετικέτες ενσωματωμένες (inline) είτε ως ξεχωριστά αντικείμενα. Η παρακάτω επιλογή τα διατηρεί ενσωματωμένα, κάτι που προτιμούν πολλά εργαλεία προσβασιμότητας.

```python
# PDF options controlling floating shape handling
pdf_opts = aw.saving.PdfSaveOptions()
pdf_opts.export_floating_shapes_as_inline_tag = True  # Set to False to keep separate
```

> **Η εξαγωγή εξισώσεων latex** διαχειρίζεται αυτόματα από τη μηχανή PDF· δεν χρειάζεστε ξεχωριστή σημαία για LaTeX στη διαδρομή PDF.

## Βήμα 6: Αποθήκευση του εγγράφου σε όλες τις επιθυμητές μορφές

Τώρα έχετε τρία πλήρως διαμορφωμένα αντικείμενα επιλογών. Μία ενιαία κλήση `doc.save` ανά μορφή γράφει τα αρχεία εξόδου.

```python
# Save as Markdown (with LaTeX math)
doc.save("YOUR_DIRECTORY/output.md", md_opts)

# Save as plain text (with LaTeX math)
doc.save("YOUR_DIRECTORY/output.txt", txt_opts)

# Save as PDF (with inline‑tagged floating shapes)
doc.save("YOUR_DIRECTORY/output.pdf", pdf_opts)
```

### Αναμενόμενα αποτελέσματα

| Αρχείο εξόδου | Κύρια χαρακτηριστικά |
|---------------|-----------------------|
| `output.md`  | Κείμενο Markdown, οι εξισώσεις εμφανίζονται ως μπλοκ LaTeX `$$...$$` |
| `output.txt` | Αναπαράσταση απλού κειμένου, εξισώσεις LaTeX ενσωματωμένες |
| `output.pdf` | Απόδοση PDF της αρχικής διάταξης, τα αιωρούμενα σχήματα ετικετοποιημένα ενσωματωμένα |

Μπορείτε να ανοίξετε κάθε αρχείο στον αντίστοιχο προβολέα του για να επαληθεύσετε ότι η μετατροπή ήταν επιτυχής.

## Πώς να αποθηκεύσετε το Word ως PDF με προσαρμοσμένες επιλογές

Αν ο μοναδικός σας στόχος είναι να **αποθηκεύσετε το Word ως PDF**, μπορείτε να παραλείψετε τα βήματα Markdown και TXT και να εστιάσετε στις επιλογές PDF:

```python
# Minimal script to save only PDF
import aspose.words as aw

doc = aw.Document("YOUR_DIRECTORY/input.docx")
pdf_opts = aw.saving.PdfSaveOptions()
pdf_opts.export_floating_shapes_as_inline_tag = True
doc.save("YOUR_DIRECTORY/output.pdf", pdf_opts)
```

Αυτό το απόσπασμα δείχνει τον πιο απλό τρόπο να **αποθηκεύσετε το Word ως PDF** ενώ εξακολουθεί να σας δίνει έλεγχο στην ετικετοποίηση σχημάτων.

## Ενεργοποίηση λειτουργίας ανάκτησης για μαζικές μετατροπές

Κατά την επεξεργασία πολλών αρχείων, τυλίξτε τη λογική φόρτωσης‑αποθήκευσης σε έναν βρόχο και επαναχρησιμοποιήστε το ίδιο αντικείμενο `LoadOptions`:

```python
import os
import aspose.words as aw

load_opts = aw.LoadOptions()
load_opts.recovery_mode = aw.LoadOptions.RecoveryMode.RECOVER

for filename in os.listdir("batch_input"):
    if filename.lower().endswith(".docx"):
        path = os.path.join("batch_input", filename)
        doc = aw.Document(path, load_opts)

        # Save PDF only (example)
        pdf_path = os.path.join("batch_output", filename.replace(".docx", ".pdf"))
        pdf_opts = aw.saving.PdfSaveOptions()
        pdf_opts.export_floating_shapes_as_inline_tag = True
        doc.save(pdf_path, pdf_opts)
```

> **Συμβουλή:** Καταγράψτε τυχόν μηνύματα `LoadWarning` που επιστρέφει το Aspose.Words· υποδεικνύουν ποια τμήματα ενός κατεστραμμένου αρχείου έχουν επισκευαστεί.

## Εξαγωγή εξισώσεων ως LaTeX σε Markdown και απλό κείμενο

Τanto `MarkdownSaveOptions` όσο και `TxtSaveOptions` εκθέτουν την ίδια ιδιότητα `office_math_export_mode`. Ορίζοντάς την σε `LATEX` λέτε στη μηχανή να μεταφράσει το Office Math XML σε σύνταξη LaTeX. Αν προτιμάτε εικόνες, αλλάξτε το enum σε `IMAGE`.

```python
md_opts.office_math_export_mode = aw.saving.OfficeMathExportMode.IMAGE  # Alternative
```

Επιλέξτε τη λειτουργία που ταιριάζει στην επόμενη αλυσίδα απόδοσης σας.

## Έλεγχος αιωρούμενων σχημάτων όταν αποθηκεύετε το Word ως PDF

Η σημαία `export_floating_shapes_as_inline_tag` καθορίζει αν τα σχήματα γίνονται μέρος της ροής κειμένου (`True`) ή παραμένουν ξεχωριστά (`False`). Η ενσωματωμένη ετικετοποίηση βελτιώνει την εξαγωγή κειμένου

## Τι Θα Μάθετε Στη Σειρά;

Οι παρακάτω οδηγίες καλύπτουν στενά σχετικές θεματικές που επεκτείνουν τις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Πώς να Εξάγετε LaTeX από το Word: Μετατροπή DOCX σε Markdown & Αποθήκευση ως PDF](/words/english/java/document-conversion-and-export/how-to-export-latex-from-word-convert-docx-to-markdown-save/)
- [Αποθήκευση Word ως PDF σε C# – Πλήρης Οδηγός για Μετατροπή DOCX σε PDF με Εξαγωγή Σχημάτων](/words/english/net/programming-with-pdfsaveoptions/save-word-as-pdf-in-c-full-guide-to-convert-docx-to-pdf-with/)
- [Πώς να εξάγετε LaTeX από το Word και να μετατρέψετε DOCX σε Markdown](/words/english/python-net/document-conversion/how-to-export-latex-from-word-and-convert-docx-to-markdown/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}