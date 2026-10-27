---
category: general
date: 2026-10-26
description: Πώς να εξάγετε markdown από αρχείο DOCX με το Aspose.Words για Python.
  Μάθετε πώς να μετατρέπετε docx σε markdown, να μετατρέπετε εξισώσεις σε LaTeX, να
  αποθηκεύετε το έγγραφο ως txt και πώς να αποθηκεύετε pdf.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to export markdown
- convert docx to markdown
- convert equations to latex
- save document as txt
- how to save pdf
language: el
lastmod: 2026-10-26
og_description: Πώς να εξάγετε markdown από αρχείο DOCX με το Aspose.Words για Python.
  Αυτός ο οδηγός σας δείχνει πώς να μετατρέψετε docx σε markdown, να εξάγετε εξισώσεις
  σε LaTeX, να αποθηκεύσετε το έγγραφο ως txt και πώς να αποθηκεύσετε pdf.
og_image_alt: Screenshot showing DOCX converted to markdown with equations rendered
  as LaTeX
og_title: Πώς να εξάγετε markdown από ένα DOCX – πλήρης οδηγός Python
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: How to export markdown from a DOCX file with Aspose.Words for Python.
    Learn to convert docx to markdown, convert equations to LaTeX, save document as
    txt, and how to save pdf.
  headline: How to export markdown from a DOCX using Aspose.Words for Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- document conversion
title: Πώς να εξάγετε markdown από ένα DOCX χρησιμοποιώντας το Aspose.Words για Python
url: /el/python/document-conversion/how-to-export-markdown-from-a-docx-using-aspose-words-for-py/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να εξάγετε markdown από ένα DOCX χρησιμοποιώντας το Aspose.Words για Python

Αν χρειάζεστε **how to export markdown** από ένα έγγραφο Word, αυτός ο οδηγός παρέχει μια έτοιμη προς εκτέλεση λύση. Θα δείτε πώς να **convert docx to markdown**, πώς να **convert equations to LaTeX**, πώς να **save document as txt**, και **how to save pdf** – όλα με ένα μόνο script Aspose.Words για Python.

Ο οδηγός περνάει από κάθε αντικείμενο επιλογής, εξηγεί γιατί κάθε ρύθμιση είναι σημαντική, και δείχνει τον ακριβή κώδικα που μπορείτε να επικολλήσετε στο πρόγραμμά σας. Δεν απαιτούνται εξωτερικές αναφορές· μόνο η βιβλιοθήκη Aspose.Words για Python και ένα αρχείο DOCX για δοκιμή.

## Προαπαιτούμενα

* Python 3.8+ εγκατεστημένο  
* `aspose-words` πακέτο (`pip install aspose-words`)  
* Ένα αρχείο DOCX (ονομασμένο `input.docx` στα παραδείγματα)  
* Δικαίωμα εγγραφής στον φάκελο εξόδου  

Αυτές οι προαπαιτήσεις εξασφαλίζουν ότι το script εκτελείται χωρίς σφάλματα δικαιωμάτων ή εξαρτήσεων.

## Βήμα 1: Φόρτωση του DOCX σε λειτουργία αποκατάστασης  

Η φόρτωση ενός πιθανώς κατεστραμμένου αρχείου σε **recovery mode** αποτρέπει εξαιρέσεις χρόνου εκτέλεσης και επιτρέπει στο Aspose.Words να προσπαθήσει να επισκευάσει το έγγραφο.

```python
import aspose.words as aw

# LoadOptions enables recovery mode to handle corrupted input files
load_opts = aw.loading.LoadOptions()
load_opts.recovery_mode = aw.loading.RecoveryMode.RECOVER

# The Document object represents the entire Word file
doc = aw.Document("YOUR_DIRECTORY/input.docx", load_opts)
```

*Γιατί recovery mode;*  
Όταν ένα DOCX περιέχει κατεστραμμένα τμήματα (π.χ., ελλιπείς σχέσεις), το `RecoveryMode.RECOVER` λέει στη βιβλιοθήκη να αγνοήσει αυτά τα σφάλματα και να δημιουργήσει ακόμη ένα χρήσιμο αντικείμενο `Document`. Αυτό είναι ιδιαίτερα χρήσιμο σε αυτοματοποιημένες γραμμές επεξεργασίας όπου δεν μπορείτε να ελέγξετε χειροκίνητα κάθε αρχείο.

## Βήμα 2: Εξαγωγή σε Markdown και μετατροπή εξισώσεων σε LaTeX  

Το Markdown είναι μια ελαφριά γλώσσα σήμανσης, αλλά οι εξισώσεις του Word χρειάζονται ειδική αναπαράσταση. Ορίζοντας το `office_math_export_mode` σε `LATEX` κάνει το Aspose.Words να αποδίδει κάθε εξίσωση ως απόσπασμα LaTeX μέσα στο αρχείο Markdown.

```python
# MarkdownSaveOptions controls how the document is written as .md
md_opts = aw.saving.MarkdownSaveOptions()
md_opts.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX

# Save the document as Markdown
doc.save("YOUR_DIRECTORY/output.md", md_opts)
```

**Αποτέλεσμα:** Το παραγόμενο `output.md` περιέχει κανονικό κείμενο, επικεφαλίδες, και τυχόν εξισώσεις Office Math τυλιγμένες σε `$…$` ή `$$…$$` διαχωριστές LaTeX, έτοιμο για επεξεργαστές LaTeX ή γεννήτριες static‑site.

## Βήμα 3: Αποθήκευση ως απλό κείμενο ενώ εξακολουθεί να μετατρέπει τις εξισώσεις σε LaTeX  

Αν χρειάζεστε μόνο την ακατέργαστη κειμενική έκδοση του εγγράφου, το `TxtSaveOptions` κάνει τη δουλειά. Η ίδια σημαία `office_math_export_mode` διασφαλίζει ότι οι εξισώσεις εμφανίζονται ως LaTeX στο αρχείο `.txt`.

```python
txt_opts = aw.saving.TxtSaveOptions()
txt_opts.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX

doc.save("YOUR_DIRECTORY/output.txt", txt_opts)
```

*Συμβουλή:* Η έξοδος απλού κειμένου είναι ιδανική για αγωγούς ευρετηρίασης αναζήτησης επειδή αφαιρεί όλη τη μορφοποίηση ενώ διατηρεί το μαθηματικό περιεχόμενο σε αναγνώσιμη μορφή.

## Βήμα 4: Δημιουργία PDF και σήμανση αιωρούμενων σχημάτων ως ενσωματωμένα στοιχεία  

Κατά τη μετατροπή σε PDF, τα αιωρούμενα σχήματα (π.χ., εικόνες αγκυροβολημένες σε παράγραφο) μπορούν να προκαλέσουν μετατοπίσεις διάταξης. Η ενεργοποίηση του `export_floating_shapes_as_inline_tag` αναγκάζει αυτά τα σχήματα να αντιμετωπίζονται ως ενσωματωμένα, κάτι που συχνά προσφέρει πιο προβλέψιμη διάταξη PDF.

```python
pdf_opts = aw.saving.PdfSaveOptions()
pdf_opts.export_floating_shapes_as_inline_tag = True

doc.save("YOUR_DIRECTORY/output.pdf", pdf_opts)
```

**Γιατί είναι σημαντικό:** Κάποιοι προβολείς PDF ερμηνεύουν τα αιωρούμενα σχήματα διαφορετικά, οδηγώντας σε λανθασμένα τοποθετημένες εικόνες. Η σήμανσή τους ως ενσωματωμένα εξασφαλίζει ότι η οπτική σειρά ταιριάζει με το αρχικό έγγραφο Word.

## Πλήρες script – αντιγραφή, επικόλληση και εκτέλεση  

Παρακάτω βρίσκεται το πλήρες, εκτελέσιμο πρόγραμμα που συνδυάζει όλα τα τέσσερα βήματα. Αντικαταστήστε το `YOUR_DIRECTORY` με την πραγματική διαδρομή φακέλου στο σύστημά σας.

```python
import aspose.words as aw

# -------------------------------------------------
# 1. Load the DOCX with recovery mode
# -------------------------------------------------
load_opts = aw.loading.LoadOptions()
load_opts.recovery_mode = aw.loading.RecoveryMode.RECOVER
doc = aw.Document("YOUR_DIRECTORY/input.docx", load_opts)

# -------------------------------------------------
# 2. Export to Markdown (equations → LaTeX)
# -------------------------------------------------
md_opts = aw.saving.MarkdownSaveOptions()
md_opts.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.md", md_opts)

# -------------------------------------------------
# 3. Export to plain text (equations → LaTeX)
# -------------------------------------------------
txt_opts = aw.saving.TxtSaveOptions()
txt_opts.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
doc.save("YOUR_DIRECTORY/output.txt", txt_opts)

# -------------------------------------------------
# 4. Export to PDF (floating shapes → inline)
# -------------------------------------------------
pdf_opts = aw.saving.PdfSaveOptions()
pdf_opts.export_floating_shapes_as_inline_tag = True
doc.save("YOUR_DIRECTORY/output.pdf", pdf_opts)
```

### Αναμενόμενη έξοδος

| File | Description |
|------|-------------|
| `output.md` | Έκδοση Markdown του DOCX, με όλες τις εξισώσεις Office Math αποδομένες ως LaTeX (`$…$`). |
| `output.txt` | Έκδοση απλού κειμένου, επίσης περιέχει εξισώσεις LaTeX. |
| `output.pdf` | Αρχείο PDF όπου τα αιωρούμενα σχήματα εξαναγκάζονται ως ενσωματωμένα, διατηρώντας την πιστότητα της διάταξης. |

## Συνηθισμένες παραλλαγές και διαχείριση ακραίων περιπτώσεων  

| Situation | Adjustment |
|-----------|------------|
| **Χρειάζεστε HTML αντί για Markdown** | Χρησιμοποιήστε `aw.saving.HtmlSaveOptions()` και ορίστε το `office_math_export_mode` παρόμοια. |
| **Διατηρήστε την αρχική θέση εικόνας στο PDF** | Ορίστε `pdf_opts.export_floating_shapes_as_inline_tag = False`. |
| **Μεγάλα έγγραφα προκαλούν πίεση μνήμης** | Φορτώστε το αρχείο με `LoadOptions.memory_optimization = True`. |
| **Θέλετε να εξάγετε μόνο μία ενότητα** | Χρησιμοποιήστε `doc.select_nodes("//w:sectPr")` για να απομονώσετε την ενότητα πριν από την αποθήκευση. |

## Επαγγελματική συμβουλή: επεξεργασία πολλαπλών αρχείων DOCX σε παρτίδες  

Αν έχετε έναν φάκελο γεμάτο αρχεία Word, τυλίξτε το script σε έναν απλό βρόχο:

```python
import os, aspose.words as aw

input_folder = "YOUR_DIRECTORY/docs"
output_folder = "YOUR_DIRECTORY/converted"

for filename in os.listdir(input_folder):
    if filename.lower().endswith(".docx"):
        path = os.path.join(input_folder, filename)
        doc = aw.Document(path, aw.loading.LoadOptions(recovery_mode=aw.loading.RecoveryMode.RECOVER))

        base = os.path.splitext(filename)[0]

        # Markdown
        md_opts = aw.saving.MarkdownSaveOptions()
        md_opts.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
        doc.save(os.path.join(output_folder, f"{base}.md"), md_opts)

        # Text
        txt_opts = aw.saving.TxtSaveOptions()
        txt_opts.office_math_export_mode = aw.saving.OfficeMathExportMode.LATEX
        doc.save(os.path.join(output_folder, f"{base}.txt"), txt_opts)

        # PDF
        pdf_opts = aw.saving.PdfSaveOptions()
        pdf_opts.export_floating_shapes_as_inline_tag = True
        doc.save(os.path.join(output_folder, f"{base}.pdf"), pdf_opts)
```

Αυτό το μοτίβο κλιμακώνει τα βήματα **how to export markdown**, **convert docx to markdown**, **convert equations to latex**, **save document as txt**, και **how to save pdf** σε οποιονδήποτε αριθμό αρχείων με ελάχιστες αλλαγές κώδικα.

## Συμπέρασμα

Τώρα γνωρίζετε **how to export markdown** από ένα DOCX με το Aspose.Words για Python, πώς να **convert docx to markdown**, πώς να **convert equations to LaTeX**, πώς να **save document as txt**, και **how to save pdf** με επιλογές σήμανσης σχήματος. Το πλήρες script δείχνει μια παραγωγική ροή εργασίας, και οι πρόσθετες συμβουλές σας βοηθούν να προσαρμόσετε τη λύση σε έξοδο HTML, περιβάλλοντα με περιορισμένη μνήμη ή σενάρια επεξεργασίας σε παρτίδες.

Έτοιμοι να ενσωματώσετε αυτό στη ροή επεξεργασίας εγγράφων σας; Δοκιμάστε να αλλάξετε τις διαδρομές εξόδου, πειραματιστείτε με άλλες κλάσεις `SaveOptions`, και εξερευνήστε το πλούσιο σύνολο λειτουργιών του Aspose.Words για ακόμη περισσότερες μορφές μετατροπής. Καλό προγραμματισμό!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κατακτήσετε πρόσθετες δυνατότητες API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Πώς να αποθηκεύσετε docx ως markdown με LaTeX χρησιμοποιώντας το Aspose.Words](/words/english/python-net/document-conversion/how-to-save-docx-as-markdown-with-latex-using-aspose-words/)
- [Πώς να εξάγετε LaTeX από το Word – Μετατροπή DOCX σε Markdown](/words/english/python-net/document-conversion/how-to-export-latex-from-word-convert-docx-to-markdown/)
- [Πώς να αποθηκεύσετε PDF και να μετατρέψετε DOCX σε Markdown](/words/english/python-net/document-conversion/how-to-save-pdf-and-convert-docx-to-markdown/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}