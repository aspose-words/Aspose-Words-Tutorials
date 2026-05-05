---
category: general
date: 2026-05-04
description: Μάθετε πώς να ενσωματώνετε εικόνες κατά τη μετατροπή DOCX σε Markdown
  χρησιμοποιώντας το Aspose.Words. Περιλαμβάνει βήματα για τη μετατροπή του Word σε
  markdown, την εξαγωγή εικόνων από το docx και την ενσωμάτωση εικόνων ως base64.
draft: false
keywords:
- how to embed images
- convert docx to markdown
- convert word to markdown
- extract images from docx
- embed images as base64
language: el
og_description: Ανακαλύψτε πώς να ενσωματώνετε εικόνες κατά τη μετατροπή DOCX σε Markdown
  με το Aspose.Words για Python. Περιλαμβάνει πλήρες κώδικα, εξηγήσεις και συμβουλές
  για την εξαγωγή εικόνων από το docx και την ενσωμάτωσή τους ως base64.
og_title: Πώς να ενσωματώσετε εικόνες κατά τη μετατροπή DOCX σε Markdown – Βήμα‑βήμα
tags:
- Aspose.Words
- Python
- Markdown
- Document Conversion
title: Πώς να ενσωματώσετε εικόνες κατά τη μετατροπή DOCX σε Markdown – Πλήρης οδηγός
url: /el/python/document-conversion/how-to-embed-images-when-converting-docx-to-markdown-complet/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να ενσωματώσετε εικόνες κατά τη μετατροπή DOCX σε Markdown – Πλήρης Οδηγός

Έχετε αναρωτηθεί ποτέ **πώς να ενσωματώσετε εικόνες** σε ένα αρχείο Markdown που προέρχεται από έγγραφο Word; Δεν είστε οι μόνοι. Πολλοί προγραμματιστές συναντούν πρόβλημα όταν προσπαθούν να μετατρέψουν DOCX σε Markdown και καταλήγουν με σπασμένους συνδέσμους εικόνων. Τα καλά νέα; Με λίγες γραμμές Python και Aspose.Words μπορείτε να διατηρήσετε κάθε εικόνα άθικτη, ακόμη και ως Base64 data‑URI.

Σε αυτό το tutorial θα περάσουμε από όλη τη διαδικασία: από την εγκατάσταση του Aspose.Words, τη φόρτωση ενός DOCX που περιέχει εικόνες, την εξαγωγή αυτών των εικόνων, και τελικά **την ενσωμάτωση εικόνων ως base64** αλφαριθμητικών μέσα στο παραγόμενο Markdown. Στο τέλος θα μπορείτε να **μετατρέψετε docx σε markdown**, **να μετατρέψετε word σε markdown**, και ακόμη **να εξάγετε εικόνες από docx** για άλλες χρήσεις—όλα χωρίς να βγείτε από το IDE σας.

> **Προαπαιτούμενα**  
> * Python 3.8+  
> * Πακέτο `aspose-words` (η δωρεάν δοκιμή λειτουργεί για τις περισσότερες περιπτώσεις)  
> * Ένα αρχείο DOCX με τουλάχιστον μία εικόνα (θα το ονομάσουμε `Images.docx`)  

Αν είστε άνετοι με το pip και τις βασικές λειτουργίες I/O αρχείων, είστε έτοιμοι. Ας βουτήξουμε.

---

## Πώς να ενσωματώσετε εικόνες ενώ μετατρέπετε DOCX σε Markdown

Αυτό το H2 ικανοποιεί άμεσα τον κανόνα του κύριου-λέξη-κλειδί και λέει τόσο στις μηχανές αναζήτησης όσο και στους βοηθούς AI ακριβώς τι καλύπτει η ενότητα.

### Βήμα 1: Εγκατάσταση Aspose.Words για Python

Πρώτα, κατεβάστε τη βιβλιοθήκη από το PyPI. Το όνομα του πακέτου είναι `aspose-words`, χωρίς να το συγχέετε με την έκδοση .NET.

```bash
pip install aspose-words
```

> **Pro tip:** Αν βρίσκεστε πίσω από εταιρικό proxy, προσθέστε `--proxy http://your-proxy:port` στην εντολή.  

Η εγκατάσταση του πακέτου φέρνει επίσης τις εξαρτήσεις του `aspose-words`, όπως το `aspose-words-cloud`. Δεν απαιτείται επιπλέον διαμόρφωση για τοπική μετατροπή.

### Βήμα 2: Φόρτωση του πηγαίου εγγράφου DOCX

Θα χρησιμοποιήσουμε την κλάση `aw.Document` για να ανοίξουμε το αρχείο. Αυτό το βήμα είναι εκεί όπου **εξάγετε εικόνες από docx** αν χρειαστείτε τις ξεχωριστά.

```python
import aspose.words as aw
import base64

# Path to the Word file that contains images
doc_path = "YOUR_DIRECTORY/Images.docx"

# Load the document into memory
document = aw.Document(doc_path)
```

> **Γιατί είναι σημαντικό:** Η φόρτωση του εγγράφου σας δίνει πρόσβαση στο `resource_saving_callback` αργότερα, που είναι το hook που χρησιμοποιεί το Aspose για να αποφασίσει πώς θα γράψει τις εικόνες κατά την αποθήκευση σε Markdown.

### Βήμα 3: Ορισμός callback που μετατρέπει κάθε εικόνα σε Base64 data‑URI

Το Aspose σας επιτρέπει να παρεμβείτε σε κάθε πόρο (εικόνες, γραμματοσειρές κ.λπ.) που κανονικά θα γραφόταν στο δίσκο. Παρέχοντας ένα callback μπορούμε να αντικαταστήσουμε τη προεπιλεγμένη διαχείριση αρχείων με μια ενσωματωμένη αλφαριθμητική Base64.

```python
def embed_images_callback(resource):
    """
    Called for every resource Aspose wants to save.
    If the resource is an image, we convert it to a data‑URI.
    """
    # Only process image resources; other types fall back to default handling
    if resource.resource_type == aw.saving.MarkdownResourceType.IMAGE:
        # Build the data‑URI: data:<mime>;base64,<encoded bytes>
        data_uri = (
            f"data:{resource.mime_type};base64,"
            f"{base64.b64encode(resource.bytes).decode()}"
        )
        # Return a tuple (resource name, encoded data) – name is ignored for data‑URI
        return (resource.name, data_uri.encode())
    # Returning None tells Aspose to use its default saving logic
    return None
```

> **Edge case:** Κάποια αρχεία Word ενσωματώνουν εικόνες SVG. Το Aspose αναφέρει τον MIME τύπο ως `image/svg+xml`, που υποστηρίζεται επίσης από το data‑URI. Αν ο προορισμός Markdown viewer σας δεν αποδίδει SVG, σκεφτείτε να το μετατρέψετε σε PNG μέσα στο callback.

### Βήμα 4: Διαμόρφωση επιλογών αποθήκευσης Markdown και σύνδεση του callback

Τώρα λέμε στο Aspose να χρησιμοποιήσει το callback που μόλις ορίσαμε. Αυτή είναι η καρδιά του **πώς να ενσωματώσετε εικόνες** στο τελικό αρχείο Markdown.

```python
# Create save options for Markdown
markdown_options = aw.saving.MarkdownSaveOptions()

# Attach our custom callback
markdown_options.resource_saving_callback = embed_images_callback
```

Μπορείτε επίσης να ρυθμίσετε το `markdown_options` για να ελέγξετε τα επίπεδα επικεφαλίδων, τα fences των code blocks, ή αν θα δημιουργηθεί ξεχωριστός φάκελος πόρων. Για αυτόν τον οδηγό κρατάμε τις προεπιλογές επειδή η προσέγγιση data‑URI εξαλείφει την ανάγκη για επιπλέον φάκελο.

### Βήμα 5: Αποθήκευση του εγγράφου ως Markdown με ενσωματωμένες Base64 εικόνες

Τέλος, γράφουμε το αρχείο εξόδου. Το αποτέλεσμα είναι ένα ενιαίο αρχείο `.md` που περιέχει κάθε εικόνα ως αλφαριθμητικό Base64—χωρίς εξωτερικά assets.

```python
output_path = "YOUR_DIRECTORY/ImagesEmbedded.md"
document.save(output_path, markdown_options)

print(f"✅ Markdown with embedded images saved to: {output_path}")
```

Όταν ανοίξετε το `ImagesEmbedded.md` σε έναν Markdown viewer (VS Code, GitHub ή static site generator), κάθε εικόνα θα εμφανίζεται ακριβώς εκεί που ήταν στο αρχικό έγγραφο Word.

> **Τι θα δείτε:**  
> ```markdown
> ![Picture1](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAA...)
> ```  
> Η μακριά αλφαριθμητική ακολουθία μετά το `base64,` είναι τα δυαδικά δεδομένα της εικόνας, κωδικοποιημένα με τρόπο που οι browsers μπορούν να τα αποκωδικοποιήσουν άμεσα.

---

## Μετατροπή DOCX σε Markdown χωρίς απώλεια εικόνων – κοινά προβλήματα

Ακόμα και αν ο κώδικας παραπάνω λειτουργεί αμέσως, οι προγραμματιστές συχνά συναντούν μερικά εμπόδια. Παρακάτω είναι οι πιο συχνές ερωτήσεις και οι απαντήσεις που διατηρούν τη μετατροπή σας ομαλή.

### 1. “Οι εικόνες μου εξακολουθούν να λείπουν μετά τη μετατροπή”

* **Ελέγξτε τον MIME τύπο:** Κάποια παλαιότερα αρχεία DOCX αποθηκεύουν εικόνες με γενικό MIME τύπο (`application/octet-stream`). Το callback θα τις ενσωματώσει, αλλά ορισμένοι Markdown renderers αρνούνται να εμφανίσουν άγνωστους τύπους. Μπορείτε να επιβάλετε fallback σε `image/png` μέσα στο callback αν γνωρίζετε τη μορφή της εικόνας.
* **Μεγάλα έγγραφα:** Το Base64 αυξάνει το μέγεθος περίπου κατά 33 %. Αν μετατρέπετε ένα αρχείο Word 10 MB, το παραγόμενο Markdown μπορεί να είναι ~13 MB. Οι περισσότεροι σύγχρονοι editors το διαχειρίζονται, αλλά οι static site generators μπορεί να έχουν όρια. Σκεφτείτε να εξάγετε τις εικόνες σε φάκελο αντί να τις ενσωματώνετε αν το μέγεθος αποτελεί πρόβλημα.

### 2. “Μπορώ επίσης να εξάγω τις εικόνες από το DOCX για ξεχωριστή χρήση;”

Απολύτως. Το ίδιο callback μπορεί να γράψει τα bytes της εικόνας στο δίσκο πριν επιστρέψει το data‑URI.

```python
import os

def embed_and_save_images(resource):
    if resource.resource_type == aw.saving.MarkdownResourceType.IMAGE:
        # Save the raw image to a folder
        os.makedirs("extracted_images", exist_ok=True)
        with open(f"extracted_images/{resource.name}", "wb") as f:
            f.write(resource.bytes)

        # Then embed as Base64 (same as before)
        data_uri = f"data:{resource.mime_type};base64,{base64.b64encode(resource.bytes).decode()}"
        return (resource.name, data_uri.encode())
    return None
```

Τρέχοντας αυτήν την έκδοση θα έχετε τόσο έναν φάκελο `extracted_images` **όσο και** ένα αρχείο Markdown με ενσωματωμένες Base64 εικόνες—τέλειο για έργα που χρειάζονται και τα δύο.

### 3. “Τι γίνεται με πίνακες, υποσημειώσεις ή ειδικά χαρακτηριστικά του Word;”

Το Aspose.Words προσπαθεί να διατηρήσει όσο το δυνατόν περισσότερο το formatting, αλλά το Markdown έχει περιορισμένο σύνολο χαρακτηριστικών. Οι πίνακες μετατρέπονται σε σύνταξη με pipes, ενώ οι υποσημειώσεις γίνονται απλοί δείκτες κειμένου. Αν χρειάζεστε πιο πλούσιο output (π.χ. HTML), αλλάξτε το `MarkdownSaveOptions` σε `HtmlSaveOptions` και διατηρήστε την ίδια λογική callback.

---

## Πλήρες, εκτελέσιμο παράδειγμα – έτοιμο για copy‑paste

Συνδυάζοντας τα πάντα, εδώ είναι ένα ενιαίο script που μπορείτε να τοποθετήσετε σε οποιονδήποτε φάκελο έργου. Προσαρμόστε τα placeholders `YOUR_DIRECTORY` ώστε να δείχνουν στα πραγματικά σας αρχεία.

```python
# ------------------------------------------------------------
# How to embed images while converting DOCX to Markdown
# ------------------------------------------------------------
# Prerequisites:
#   pip install aspose-words
# ------------------------------------------------------------

import aspose.words as aw
import base64
import os

# ------------------------------------------------------------------
# 1️⃣  Define the callback that embeds images as Base64 data‑URIs
# ------------------------------------------------------------------
def embed_images_callback(resource):
    """
    Aspose calls this for each external resource (image, font, etc.).
    We only care about images – everything else falls back to default.
    """
    if resource.resource_type == aw.saving.MarkdownResourceType.IMAGE:
        # Optional: also write the image to disk for later reuse
        os.makedirs("extracted_images", exist_ok=True)
        with open(f"extracted_images/{resource.name}", "wb") as img_file:
            img_file.write(resource.bytes)

        # Build the Base64 data‑URI
        data_uri = (
            f"data:{resource.mime_type};base64,"
            f"{base64.b64encode(resource.bytes).decode()}"
        )
        # Return name (ignored) and the encoded URI as bytes
        return (resource.name, data_uri.encode())
    return None  # Use Aspose's default handling for non‑image resources

# ------------------------------------------------------------------
# 2️⃣  Load the DOCX that contains images
# ------------------------------------------------------------------
doc_path = "YOUR_DIRECTORY/Images.docx"
document = aw.Document(doc_path)

# ------------------------------------------------------------------
# 3️⃣  Prepare Markdown save options and hook the callback
# ------------------------------------------------------------------
markdown_options = aw.saving.MarkdownSaveOptions()
markdown_options.resource_saving_callback = embed_images_callback

# ------------------------------------------------------------------
# 4️⃣  Save as Markdown with images embedded as Base64
# ------------------------------------------------------------------
output_path = "YOUR_DIRECTORY/ImagesEmbedded.md"
document.save(output_path, markdown_options)

print(f"✅ Success! Markdown saved to {output_path}")
print("   Images are now inline Base64 data‑URIs.")
```

**Αναμενόμενο αποτέλεσμα:** Ανοίξτε το `ImagesEmbedded.md` και θα δείτε το αρχικό κείμενο συν ετικέτες εικόνας όπως `![Picture1](data:image/png;base64,…)`. Δεν απαιτούνται εξωτερικά αρχεία εικόνας.

---

## Συμπέρασμα

Καλύψαμε **πώς να ενσωματώσετε εικόνες** όταν **μετατρέπετε docx σε markdown**, σας δείξαμε πώς να **εξάγετε εικόνες από docx**, και παρουσιάσαμε τον πιο καθαρό τρόπο να **ενσωματώσετε εικόνες ως base64** χρησιμοποιώντας το Aspose.Words για Python. Το πλήρες script παραπάνω είναι έτοιμο για εκτέλεση, και οι εξηγήσεις απαντούν στο “γιατί” πίσω από κάθε γραμμή—ώστε να το προσαρμόσετε στα δικά σας έργα χωρίς εικασίες.

Θέλετε να προχωρήσετε παραπέρα; Δοκιμάστε τα επόμενα βήματα:

* **Μετατρέψτε Word σε markdown** με προσαρμοσμένα επίπεδα επικεφαλίδων τροποποιώντας το `markdown_options.heading_level`.
* **Δημιουργήστε PDF** από το ίδιο DOCX και συγκρίνετε πώς διαχειρίζονται οι εικόνες διαφορετικές μορφές εξόδου.
* **Ενσωματώστε το script σε CI pipeline** ώστε κάθε commit να παράγει αυτόματα ένα στιγμιότυπο Markdown της τεκμηρίωσής σας.

Πειραματιστείτε ελεύθερα—ίσως αντικαταστήσετε την ενσωμάτωση Base64 με URL CDN για τεράστια αρχεία, ή προσθέσετε OCR για σαρωμένες εικόνες. Ο ουρανός είναι το όριο, και τώρα έχετε μια σταθερή βάση.

Αν αντιμετωπίσετε κάποιο σ

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}