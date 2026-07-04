---
category: general
date: 2026-05-30
description: Μάθετε πώς να ανακτήσετε αρχεία docx, να ρυθμίσετε σκιά και να μετατρέψετε
  docx markdown τόσο σε markdown όσο και σε PDF χρησιμοποιώντας το Aspose.Words για
  Python. Συμπεριλαμβάνεται κώδικας βήμα‑βήμα.
draft: false
keywords:
- how to recover docx
- convert docx markdown
- save as markdown
- save as pdf
- how to set shadow
language: el
og_description: Πώς να ανακτήσετε ένα docx, να ορίσετε σκιά και να αποθηκεύσετε ως
  markdown ή pdf με το Aspose.Words. Πλήρης οδηγός για προγραμματιστές.
og_title: Πώς να ανακτήσετε DOCX και να το μετατρέψετε σε Markdown & PDF – Εκμάθηση
  Python
schemas:
- author: Aspose
  dateModified: '2026-05-30'
  description: Learn how to recover docx, set shadow, and convert docx markdown to
    both markdown and pdf using Aspose.Words for Python. Step‑by‑step code included.
  headline: How to Recover DOCX and Convert It to Markdown and PDF – Complete Python
    Guide
  type: TechArticle
tags:
- Aspose.Words
- Python
- Document Conversion
title: Πώς να ανακτήσετε ένα DOCX και να το μετατρέψετε σε Markdown και PDF – Πλήρης
  οδηγός Python
url: /el/python/document-conversion/how-to-recover-docx-and-convert-it-to-markdown-and-pdf-compl/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να Ανακτήσετε DOCX και να το Μετατρέψετε σε Markdown και PDF – Πλήρης Οδηγός Python

Έχετε αναρωτηθεί ποτέ **πώς να ανακτήσετε docx** αρχεία που αρνούνται να ανοίξουν στο Word; Ίσως λάβατε μια κατεστραμμένη αναφορά από έναν πελάτη, ή μια νυχτερινή εργασία παρτίδας παρήγαγε ένα ημιτελές έγγραφο. Σε αυτές τις στιγμές δεν θέλετε απλώς ένα κουμπί “προσπάθησε ξανά” — χρειάζεστε έναν αξιόπιστο τρόπο να εξάγετε τα καλά τμήματα, να προσαρμόσετε την εμφάνιση, και στη συνέχεια να παραδώσετε το αποτέλεσμα στις μορφές που οι ενδιαφερόμενοι σας χρησιμοποιούν πραγματικά.

Ακριβώς αυτό θα κάνουμε σε αυτό το tutorial. Θα σας δείξουμε πώς να ανακτήσετε ένα DOCX, **πώς να ορίσετε σκιά** στο πρώτο σχήμα, μετά **να μετατρέψετε docx markdown**, **να αποθηκεύσετε ως markdown**, και τέλος **να αποθηκεύσετε ως pdf** — όλα με τη δυνατή βιβλιοθήκη Aspose.Words for Python. Στο τέλος θα έχετε ένα ενιαίο script που μετατρέπει ένα κατεστραμμένο αρχείο Word σε καθαρά Markdown και PDF, με ένα διακριτικό εφέ σκιάς σε οποιαδήποτε γραφικά.

> **Συμβουλή:** Ο κώδικας λειτουργεί με Aspose.Words 22.12 ή νεότερη έκδοση· παλαιότερες εκδόσεις ενδέχεται να λείπουν ορισμένες από τις νεότερες σημαίες συμμόρφωσης PDF/UA.

---

## Τι Θα Χρειαστεί

Πριν βουτήξουμε, βεβαιωθείτε ότι έχετε τα παρακάτω:

| Απαίτηση | Λόγος |
|-------------|--------|
| Python 3.8+ | Σύγχρονη σύνταξη και type hints |
| `aspose-words` package (`pip install aspose-words`) | Κύρια βιβλιοθήκη για φόρτωση, επεξεργασία και αποθήκευση |
| A DOCX file (even a corrupted one) | Το αρχικό έγγραφο |
| Basic familiarity with Python functions | Για εύκολη παρακολούθηση της ροής |

Αυτό είναι όλο—χωρίς επιπλέον DLLs, χωρίς εγκατάσταση Office, και χωρίς ασαφείς κλήσεις συστήματος. Το Aspose.Words διαχειρίζεται το βαρέως φορτίου εσωτερικά.

## ## Πώς να Ανακτήσετε DOCX και να Συνεχίσετε να Εργάζεστε με Αυτό

Το πρώτο πράγμα που πρέπει να κάνουμε είναι να φορτώσουμε το πιθανώς κατεστραμμένο έγγραφο σε **recovery mode**. Το Aspose.Words προσφέρει μια κλάση `DocumentLoadOptions` όπου μπορείτε να ενεργοποιήσετε το `RecoveryMode`. Όταν οριστεί σε `RECOVER`, η βιβλιοθήκη προσπαθεί να ξαναχτίσει το εσωτερικό δέντρο κόμβων, απορρίπτοντας μόνο τα τμήματα που είναι ακατάσχετα.

```python
import aspose.words as aw

# -------------------------------------------------
# Step 1 – Load the DOCX with recovery enabled
# -------------------------------------------------
load_opts = aw.loading.DocumentLoadOptions()
load_opts.recovery_mode = aw.loading.RecoveryMode.RECOVER

# Replace YOUR_DIRECTORY with the real path to your file
doc = aw.Document("YOUR_DIRECTORY/input.docx", load_opts)

print("Document loaded. Nodes recovered:", doc.get_child_nodes(aw.NodeType.ANY, True).get_count())
```

**Γιατί είναι σημαντικό:** Αν παραλείψετε την ανάκτηση, ο κατασκευαστής `Document` θα ρίξει μια εξαίρεση τη στιγμή που εντοπίσει κατεστραμμένα δεδομένα, σταματώντας ολόκληρη τη διαδικασία. Ενεργοποιώντας την ανάκτηση λαμβάνετε ένα χρησιμοποιήσιμο αντικείμενο `Document` ακόμα και όταν το Word θα αρνιόταν να ανοίξει το αρχείο.

## ## Πώς να Ορίσετε Σκιά στο Πρώτο Σχήμα

Μια διακριτική σκιά μπορεί να κάνει ένα λογότυπο ή διάγραμμα να ξεχωρίσει, ειδικά όταν αργότερα εξάγετε σε PDF/UA όπου ισχύουν κανόνες προσβασιμότητας. Το παρακάτω απόσπασμα παίρνει τον πρώτο κόμβο `Shape` στο έγγραφο και ρυθμίζει το `ShadowFormat` του.

```python
# -------------------------------------------------
# Step 2 – Find the first shape and apply a shadow
# -------------------------------------------------
first_shape = doc.get_child(aw.NodeType.SHAPE, 0, True).as_shape()
shadow = first_shape.shadow_format

# Enable the shadow and tweak its appearance
shadow.visible = True
shadow.distance = 4          # distance of the shadow from the shape (points)
shadow.blur = 6              # blur radius (points)
shadow.color = aw.Color.gray
shadow.opacity = 0.7         # 70% opacity for a soft look

print("Shadow applied to shape:", first_shape.name)
```

**Κοινό λάθος:** Αν το έγγραφο δεν περιέχει σχήματα, το `get_child` επιστρέφει `None` και το script καταρρέει. Μια γρήγορη προφυλακτική δήλωση μπορεί να σας σώσει:

```python
if first_shape is not None:
    # apply shadow (as above)
else:
    print("No shapes found – skipping shadow step.")
```

## ## Μετατροπή DOCX σε Markdown (Αποθήκευση ως Markdown)

Τώρα που το έγγραφο είναι υγιές και η οπτική τροποποίηση είναι σε θέση, ας **μετατρέψουμε docx markdown**. Το Aspose.Words μπορεί να εκδώσει Markdown ενώ διαχειρίζεται επίσης εξισώσεις Office Math, τις οποίες θα εξάγουμε ως LaTeX για μέγιστη πιστότητα.

```python
# -------------------------------------------------
# Step 3 – Export to Markdown, preserving Math as LaTeX
# -------------------------------------------------
md_options = aw.saving.MarkdownSaveOptions()
md_options.office_math_export_mode = aw.saving.MarkdownOfficeMathExportMode.LATEX

# Again, replace the path with your desired output location
md_path = "YOUR_DIRECTORY/Combined.md"
doc.save(md_path, md_options)

print("Markdown file saved to:", md_path)
```

**Τι θα δείτε:** Το παραγόμενο αρχείο `.md` περιέχει κανονική σύνταξη Markdown για παραγράφους, επικεφαλίδες και λίστες, ενώ τυχόν ενσωματωμένες εξισώσεις εμφανίζονται ως μπλοκ LaTeX περιτυλιγμένα σε `$$ … $$`. Ανοίξτε το σε VS Code ή οποιονδήποτε προβολέα Markdown για να το επαληθεύσετε.

## ## Αποθήκευση ως PDF με Προσβασιμότητα (Αποθήκευση ως PDF)

Τέλος, θα **αποθηκεύσουμε ως pdf** διασφαλίζοντας ότι τα αιωρούμενα σχήματα που τροποποιήσαμε νωρίτερα εξάγονται ως στοιχεία inline‑tag. Αυτό διατηρεί τη διάταξη συνεπή σε όλους τους προβολείς και ικανοποιεί τη συμμόρφωση PDF/UA 1 για προσβασιμότητα.

```python
# -------------------------------------------------
# Step 4 – Export to PDF/UA with inline‑tagged floating shapes
# -------------------------------------------------
pdf_options = aw.saving.PdfSaveOptions()
pdf_options.export_floating_shapes_as_inline_tag = True
pdf_options.compliance = aw.saving.PdfCompliance.PDF_UA_1

pdf_path = "YOUR_DIRECTORY/Combined.pdf"
doc.save(pdf_path, pdf_options)

print("PDF file saved to:", pdf_path)
```

**Γιατί PDF/UA;** Το PDF/UA (Universal Accessibility) προσθέτει ετικέτες που μπορούν να ερμηνεύσουν τα προγράμματα ανάγνωσης οθόνης, καθιστώντας το έγγραφό σας πιο φιλικό σε χρήστες με αναπηρίες. Η σημαία `export_floating_shapes_as_inline_tag` αποτρέπει επίσης τα σχήματα από το να αποσπαστούν από το περιβάλλον κείμενο, που είναι κοινή πηγή μετατόπισης διάταξης.

## ## Πλήρες Script – Ολοκληρωμένη Λύση

Συνδυάζοντας όλα, εδώ είναι ένα έτοιμο‑να‑τρέξει script που καλύπτει **πώς να ανακτήσετε docx**, **πώς να ορίσετε σκιά**, **να μετατρέψετε docx markdown**, **να αποθηκεύσετε ως markdown**, και **να αποθηκεύσετε ως pdf**. Αντιγράψτε, επικολλήστε και προσαρμόστε τις διαδρομές αρχείων ώστε να ταιριάζουν στο περιβάλλον σας.

```python
import aspose.words as aw

def recover_and_convert(input_path: str, output_dir: str):
    # ---------- Load with recovery ----------
    load_opts = aw.loading.DocumentLoadOptions()
    load_opts.recovery_mode = aw.loading.RecoveryMode.RECOVER
    doc = aw.Document(input_path, load_opts)
    print(f"Loaded '{input_path}'. Node count:", doc.get_child_nodes(aw.NodeType.ANY, True).get_count())

    # ---------- Apply shadow to first shape ----------
    first_shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
    if first_shape is not None:
        shape = first_shape.as_shape()
        shadow = shape.shadow_format
        shadow.visible = True
        shadow.distance = 4
        shadow.blur = 6
        shadow.color = aw.Color.gray
        shadow.opacity = 0.7
        print(f"Shadow set on shape '{shape.name}'.")
    else:
        print("No shapes detected – shadow step skipped.")

    # ---------- Save as Markdown ----------
    md_options = aw.saving.MarkdownSaveOptions()
    md_options.office_math_export_mode = aw.saving.MarkdownOfficeMathExportMode.LATEX
    md_path = f"{output_dir}/Combined.md"
    doc.save(md_path, md_options)
    print("Markdown saved at:", md_path)

    # ---------- Save as PDF/UA ----------
    pdf_options = aw.saving.PdfSaveOptions()
    pdf_options.export_floating_shapes_as_inline_tag = True
    pdf_options.compliance = aw.saving.PdfCompliance.PDF_UA_1
    pdf_path = f"{output_dir}/Combined.pdf"
    doc.save(pdf_path, pdf_options)
    print("PDF saved at:", pdf_path)

# Example usage – replace with your actual paths
if __name__ == "__main__":
    recover_and_convert("YOUR_DIRECTORY/input.docx", "YOUR_DIRECTORY")
```

Εκτελέστε το script με `python recover_and_convert.py`. Αν όλα πάνε ομαλά, θα έχετε δύο αρχεία στο `YOUR_DIRECTORY`:

* **Combined.md** – καθαρό Markdown, LaTeX για τυχόν εξισώσεις, και η εικόνα με ενισχυμένη σκιά ενσωματωμένη ως κανονική ετικέτα εικόνας.
* **Combined.pdf** – συμβατό με PDF/UA, με τη σκιά του σχήματος διατηρημένη και τα αιωρούμενα σχήματα ενσωματωμένα inline.

## ## Αναμενόμενο Αποτέλεσμα & Επαλήθευση

| Αρχείο | Τι να Αναζητήσετε |
|------|------------------|
| `Combined.md` | Τυπικές επικεφαλίδες Markdown (`#`, `##`), λιστες bullet, και οποιαδήποτε μαθηματική έκφραση εμφανίζεται ως `$$ … $$`. Ανοίξτε σε προβολέα Markdown για να δείτε τη μορφοποίηση. |
| `Combined.pdf` | Ετικέτες προσβασιμότητας (χρησιμοποιήστε το “Read Out Loud” του Adobe Acrobat για δοκιμή), το πρώτο σχήμα πρέπει να εμφανίζει μια αχνή γκρι σκιά, και η διάταξη πρέπει να ταιριάζει όσο το δυνατόν πιο κοντά με το αρχικό DOCX. |

Αν το PDF ανοίξει χωρίς σφάλματα και το Markdown αποδοθεί σωστά, έχετε επιτυχώς **ανακτήσει το DOCX**, εφαρμόσει μια οπτική τροποποίηση, και εξάγει

## Τι Θα Πρέπει Να Μάθετε Στη Σύντομη Μελλοντική

- [πώς να ανακτήσετε docx με Aspose.Words – βήμα προς βήμα](/words/english/net/programming-with-loadoptions/how-to-recover-docx-with-aspose-words-step-by-step/)
- [Πώς να Αποθηκεύσετε Markdown από DOCX – Οδηγός Βήμα‑βήμα](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)
- [Αποθήκευση docx ως pdf με Aspose.Words – Πλήρης Οδηγός C#](/words/english/net/programming-with-pdfsaveoptions/save-docx-as-pdf-with-aspose-words-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}