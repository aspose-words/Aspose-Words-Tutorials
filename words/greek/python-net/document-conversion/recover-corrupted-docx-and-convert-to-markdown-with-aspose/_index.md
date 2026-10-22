---
category: general
date: 2026-08-04
description: Ανακτήστε κατεστραμμένα αρχεία docx χρησιμοποιώντας τη λειτουργία ανάκτησης
  του Aspose.Words και μετατρέψτε τα docx σε markdown, εξάγοντας τις εξισώσεις ως
  LaTeX.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- recover corrupted docx
- convert docx to markdown
- how to use recovery mode
- export equations latex
language: el
lastmod: 2026-08-04
og_description: Ανακτήστε κατεστραμμένα αρχεία docx με τη λειτουργία ανάκτησης του
  Aspose.Words, στη συνέχεια μετατρέψτε το docx σε markdown εξάγοντας τις εξισώσεις
  ως LaTeX. Ακολουθήστε αυτόν τον οδηγό βήμα‑βήμα για να δημιουργήσετε επίσης εξαγωγές
  PDF και TXT.
og_image_alt: Screenshot of Aspose.Words Python code converting a corrupted docx to
  markdown with LaTeX equations
og_title: Ανάκτηση κατεστραμμένου docx και μετατροπή σε markdown – Οδηγός Aspose
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Recover corrupted docx files using Aspose.Words recovery mode and convert
    docx to markdown, exporting equations as LaTeX.
  headline: Recover corrupted docx and convert to markdown with Aspose
  type: TechArticle
- description: Recover corrupted docx files using Aspose.Words recovery mode and convert
    docx to markdown, exporting equations as LaTeX.
  name: Recover corrupted docx and convert to markdown with Aspose
  steps:
  - name: Export floating shapes as inline tags
    text: Floating images or text boxes can cause layout issues when converting to
      PDF. Setting `export_floating_shapes_as_inline_tag` forces Aspose.Words to treat
      those shapes as regular inline elements, preserving the visual flow.
  - name: Adjust the shadow of the first shape
    text: You might want to enhance the appearance of a specific shape before saving
      the final PDF. The code below accesses the first `Shape` node, enables its shadow,
      and tweaks visual parameters.
  - name: Expected output
    text: '| File | Description | |------|-------------| | `output.md` | Markdown
      version of the original DOCX. All equations appear as LaTeX (`$...$` or `$$...$$`).
      | | `output.txt` | Plain‑text dump'
  type: HowTo
tags:
- Aspose.Words
- Python
- Document conversion
title: Ανάκτηση κατεστραμμένου docx και μετατροπή σε markdown με το Aspose
url: /el/python/document-conversion/recover-corrupted-docx-and-convert-to-markdown-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ανάκτηση κατεστραμμένου docx και μετατροπή σε markdown με Aspose

Αν χρειάζεστε **ανάκτηση κατεστραμμένων docx** αρχείων, το Aspose.Words παρέχει ενσωματωμένη λειτουργία ανάκτησης που μπορεί αυτόματα να επισκευάσει κατεστραμμένα έγγραφα Word. Μόλις το αρχείο αποκατασταθεί, μπορείτε να **μετατρέψετε docx σε markdown**, και ακόμη και να **εξάγετε εξισώσεις latex** για απρόσκοπτη χρήση σε επιστημονικά έγγραφα. Αυτό το tutorial σας δείχνει ακριβώς πώς να το κάνετε σε Python, καθώς και μερικές επιπλέον επιλογές για έξοδο PDF και απλού κειμένου.

Θα μάθετε πώς να:

* Φορτώσετε ένα πιθανώς κατεστραμμένο DOCX χρησιμοποιώντας τη λειτουργία ανάκτησης.  
* Αποθηκεύσετε το ανακτημένο έγγραφο ως Markdown με εξισώσεις μορφοποιημένες σε LaTeX.  
* Δημιουργήσετε μια έκδοση απλού κειμένου (TXT) που επίσης περιέχει εξισώσεις LaTeX.  
* Εξάγετε σε PDF ενώ ετικετοποιείτε τα αιωρούμενα σχήματα ως ενσωματωμένα στοιχεία.  
* Ρυθμίσετε τη σκιά ενός σχήματος και δημιουργήσετε το τελικό PDF.

Δεν απαιτούνται εξωτερικά εργαλεία—απλώς η δωρεάν βιβλιοθήκη Aspose.Words for Python.

## Προαπαιτούμενα

| Απαίτηση | Γιατί είναι σημαντικό |
|-------------|----------------|
| Python 3.8+ | Απαιτείται από το Aspose.Words για Python |
| `aspose-words` package (`pip install aspose-words`) | Παρέχει το χώρο ονομάτων `aw` που χρησιμοποιείται στον κώδικα |
| A DOCX file that may be damaged (e.g., `corrupted.docx`) | Δείχνει τη ροή εργασίας ανάκτησης |
| Write permission to the output directory | Το script γράφει πολλά αρχεία (`.md`, `.txt`, `.pdf`) |

Βεβαιωθείτε ότι η άδεια Aspose.Words (δωρεάν δοκιμή ή αγορασμένη) είναι σωστά ρυθμισμένη εάν υπερβείτε τα όρια αξιολόγησης.

## Ανάκτηση κατεστραμμένου docx χρησιμοποιώντας Aspose.Words

Το πρώτο βήμα είναι να πείτε στο Aspose.Words να αντιμετωπίσει το αρχείο εισόδου ως πιθανώς κατεστραμμένο. Αυτό γίνεται με το `LoadOptions.recovery_mode`.

```python
import aspose.words as aw

# Step 1: Load a possibly corrupted document using recovery mode
load_options = aw.loading.LoadOptions()
load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER   # Enables automatic recovery of damaged files
doc = aw.Document("YOUR_DIRECTORY/corrupted.docx", load_options)
```

**Γιατί λειτουργεί αυτό:**  
`RecoveryMode.RECOVER` αναγκάζει τον φορτωτή να αγνοήσει δομικά σφάλματα και να προσπαθήσει να ξαναχτίσει το δέντρο του εγγράφου. Εάν το αρχείο είναι μόνο εν μέρει κατεστραμμένο, το μεγαλύτερο μέρος του περιεχομένου—συμπεριλαμβανομένου κειμένου, εικόνων και εξισώσεων—θα αποκατασταθεί.

**Συμβουλή:** Εάν θέλετε μόνο να επικυρώσετε ένα έγγραφο χωρίς να το επισκευάσετε, χρησιμοποιήστε `RecoveryMode.NO_RECOVERY`. Για πλήρη ανάκτηση, διατηρήστε τη ρύθμιση όπως φαίνεται.

## Μετατροπή docx σε markdown με εξισώσεις LaTeX

Μόλις το έγγραφο είναι στη μνήμη, μπορείτε να το αποθηκεύσετε ως Markdown. Ορίζοντας το `office_math_export_mode` σε `LATEX` λέτε στο Aspose.Words να αποδώσει κάθε εξίσωση Word ως συμβολοσειρά LaTeX.

```python
# Step 2: Save the document as Markdown while exporting equations in LaTeX format
markdown_save_options = aw.saving.MarkdownSaveOptions()
markdown_save_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.md", markdown_save_options)
```

Το παραγόμενο `output.md` θα μοιάζει με ένα κανονικό αρχείο Markdown, αλλά κάθε εξίσωση εμφανίζεται ως `$...$` (ενσωματωμένη) ή `$$...$$` (εμφάνιση) κώδικας LaTeX. Αυτό είναι απαραίτητο για εργαλεία downstream όπως το Pandoc ή τα Jupyter notebooks που κατανοούν τη σύνταξη LaTeX.

## Πώς να χρησιμοποιήσετε τη λειτουργία ανάκτησης για κατεστραμμένα αρχεία

Η λειτουργία ανάκτησης μπορεί να επαναχρησιμοποιηθεί για οποιαδήποτε λειτουργία φόρτωσης. Παρακάτω υπάρχει ένα συμπαγές πρότυπο που μπορείτε να αντιγράψετε σε άλλα scripts:

```python
def load_with_recovery(path: str) -> aw.Document:
    opts = aw.loading.LoadOptions()
    opts.recovery_mode = aw.loading.RecoveryMode.RECOVER
    return aw.Document(path, opts)
```

Καλώντας `load_with_recovery("myfile.docx")` επιστρέφει ένα αντικείμενο `Document` που το Aspose.Words έχει ήδη προσπαθήσει να διορθώσει. Αυτή η συνάρτηση ενσωματώνει **πώς να χρησιμοποιήσετε τη λειτουργία ανάκτησης** με ασφάλεια σε διάφορα έργα.

## Εξαγωγή εξισώσεων latex κατά την αποθήκευση σε markdown και txt

Εάν χρειάζεστε επίσης μια έκδοση απλού κειμένου, η ίδια σημαία `office_math_export_mode` λειτουργεί με το `TxtSaveOptions`.

```python
# Step 3: Save the same document as plain‑text (TXT) with LaTeX equations
txt_save_options = aw.saving.TxtSaveOptions()
txt_save_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.txt", txt_save_options)
```

Το αρχείο `.txt` περιέχει το ακατέργαστο κείμενο του εγγράφου Word, και κάθε εξίσωση αντιπροσωπεύεται ως κώδικας LaTeX. Αυτή η μορφή είναι χρήσιμη για ευρετηρίαση ή τροφοδοσία του περιεχομένου σε μηχανές αναζήτησης που κατανοούν LaTeX.

## Πρόσθετες επιλογές: PDF με ενσωματωμένα σχήματα και σκιά σχήματος

### Εξαγωγή αιωρούμενων σχημάτων ως ενσωματωμένες ετικέτες

Οι αιωρούμενες εικόνες ή πλαίσια κειμένου μπορούν να προκαλέσουν προβλήματα διάταξης κατά τη μετατροπή σε PDF. Ορίζοντας το `export_floating_shapes_as_inline_tag` αναγκάζει το Aspose.Words να αντιμετωπίσει αυτά τα σχήματα ως κανονικά ενσωματωμένα στοιχεία, διατηρώντας τη ροή του οπτικού περιεχομένου.

```python
# Step 4: Export the document to PDF and tag floating shapes as inline elements
pdf_save_options = aw.saving.PdfSaveOptions()
pdf_save_options.export_floating_shapes_as_inline_tag = True
doc.save("YOUR_DIRECTORY/output.pdf", pdf_save_options)
```

### Ρύθμιση της σκιάς του πρώτου σχήματος

Μπορεί να θέλετε να βελτιώσετε την εμφάνιση ενός συγκεκριμένου σχήματος πριν αποθηκεύσετε το τελικό PDF. Ο κώδικας παρακάτω προσπελάζει τον πρώτο κόμβο `Shape`, ενεργοποιεί τη σκιά του και ρυθμίζει οπτικές παραμέτρους.

```python
# Step 5: Adjust the shadow of the first shape and save the result
first_shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
shape_shadow = first_shape.shadow_format
shape_shadow.visible = True
shape_shadow.blur = 5.0          # Controls shadow softness
shape_shadow.distance = 3.0      # Distance from the shape
shape_shadow.angle = 45          # Direction of the light source
shape_shadow.color = aw.Color.black

doc.save("YOUR_DIRECTORY/shadowed.pdf")
```

**Αποτέλεσμα:** Το `shadowed.pdf` φαίνεται ταυτόσημο με το `output.pdf`, αλλά το πρώτο σχήμα τώρα ρίχνει μια διακριτική μαύρη σκιά, η οποία μπορεί να βελτιώσει την αναγνωσιμότητα σε παρουσιάσεις.

## Πλήρες εκτελέσιμο script

Παρακάτω βρίσκεται το πλήρες script που συνδυάζει όλα τα βήματα. Αντιγράψτε το σε ένα αρχείο με όνομα `recover_and_convert.py`, αντικαταστήστε το `YOUR_DIRECTORY` με μια πραγματική διαδρομή, και τρέξτε `python recover_and_convert.py`.

```python
import aspose.words as aw

# -------------------------------------------------
# 1. Load the possibly corrupted DOCX using recovery mode
# -------------------------------------------------
load_options = aw.loading.LoadOptions()
load_options.recovery_mode = aw.loading.RecoveryMode.RECOVER
doc = aw.Document("YOUR_DIRECTORY/corrupted.docx", load_options)

# -------------------------------------------------
# 2. Save as Markdown with LaTeX equations
# -------------------------------------------------
markdown_save_options = aw.saving.MarkdownSaveOptions()
markdown_save_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.md", markdown_save_options)

# -------------------------------------------------
# 3. Save as plain‑text (TXT) with LaTeX equations
# -------------------------------------------------
txt_save_options = aw.saving.TxtSaveOptions()
txt_save_options.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.txt", txt_save_options)

# -------------------------------------------------
# 4. Export to PDF, converting floating shapes to inline
# -------------------------------------------------
pdf_save_options = aw.saving.PdfSaveOptions()
pdf_save_options.export_floating_shapes_as_inline_tag = True
doc.save("YOUR_DIRECTORY/output.pdf", pdf_save_options)

# -------------------------------------------------
# 5. Add a shadow to the first shape and save a new PDF
# -------------------------------------------------
first_shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
shape_shadow = first_shape.shadow_format
shape_shadow.visible = True
shape_shadow.blur = 5.0
shape_shadow.distance = 3.0
shape_shadow.angle = 45
shape_shadow.color = aw.Color.black

doc.save("YOUR_DIRECTORY/shadowed.pdf")
```

### Αναμενόμενη έξοδος

| Αρχείο | Περιγραφή |
|------|-------------|
| `output.md` | Έκδοση Markdown του αρχικού DOCX. Όλες οι εξισώσεις εμφανίζονται ως LaTeX (`$...$` ή `$$...$$`). |
| `output.txt` | Απλό κείμενο (dump) |

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικά παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε πρόσθετες δυνατότητες API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Πώς να χρησιμοποιήσετε Markdown: Μετατροπή DOCX σε Markdown με εξισώσεις LaTeX](/words/english/net/programming-with-markdownsaveoptions/how-to-use-markdown-convert-docx-to-markdown-with-latex-equa/)
- [πώς να ανακτήσετε docx με Aspose.Words – βήμα προς βήμα](/words/english/net/programming-with-loadoptions/how-to-recover-docx-with-aspose-words-step-by-step/)
- [Ανάκτηση Κατεστραμμένου DOCX & Μετατροπή Word σε Markdown](/words/english/python-net/document-conversion/recover-corrupted-docx-convert-word-to-markdown/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}