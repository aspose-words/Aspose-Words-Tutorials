---
category: general
date: 2026-06-24
description: Πώς να ορίσετε callback για εξαγωγή εικόνων από DOCX κατά την αποθήκευση
  ως Markdown. Μάθετε πώς να εξάγετε εικόνες, να εξάγετε SVG από το Word και να αποθηκεύσετε
  το DOCX ως Markdown με προσαρμοσμένη διαχείριση.
draft: false
keywords:
- how to set callback
- export images from docx
- how to extract images
- save docx as markdown
- extract svg from word
language: el
og_description: Πώς να ορίσετε callback για εξαγωγή εικόνων από DOCX κατά τη μετατροπή
  σε Markdown. Αυτός ο οδηγός σας δείχνει πώς να εξάγετε εικόνες και SVG αποδοτικά.
og_title: Πώς να ορίσετε την κλήση επιστροφής για την εξαγωγή εικόνων από DOCX
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: How to set callback to export images from DOCX when saving as Markdown.
    Learn how to extract images, extract SVG from Word, and save DOCX as Markdown
    with custom handling.
  headline: How to Set Callback for Exporting Images from DOCX
  type: TechArticle
- description: How to set callback to export images from DOCX when saving as Markdown.
    Learn how to extract images, extract SVG from Word, and save DOCX as Markdown
    with custom handling.
  name: How to Set Callback for Exporting Images from DOCX
  steps:
  - name: '**Deterministic names** – useful for version control or CDN publishing.'
    text: '**Deterministic names** – useful for version control or CDN publishing.'
  - name: '**Collision avoidance** – two images with the same original name won’t
      overwrite each other.'
    text: '**Collision avoidance** – two images with the same original name won’t
      overwrite each other.'
  - name: '**Custom folder structures** – maybe you want all assets under `/assets/docs/`.'
    text: '**Custom folder structures** – maybe you want all assets under `/assets/docs/`.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Document Conversion
title: Πώς να ορίσετε την κλήση επιστροφής για εξαγωγή εικόνων από DOCX
url: /el/python/content-extraction-and-manipulation/how-to-set-callback-for-exporting-images-from-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να ορίσετε Callback για την Εξαγωγή Εικόνων από DOCX

Έχετε αναρωτηθεί ποτέ **πώς να ορίσετε callback** ώστε να μπορείτε **να εξάγετε εικόνες από DOCX** κατά τη μετατροπή του σε Markdown; Δεν είστε οι μόνοι. Πολλοί προγραμματιστές συναντούν πρόβλημα όταν η προεπιλεγμένη μετατροπή αποθηκεύει όλες τις εικόνες σε έναν γενικό φάκελο ή, χειρότερα, χάνει εντελώς τα γραφικά SVG.  

Σε αυτό το tutorial θα περάσουμε βήμα‑βήμα από μια πλήρη, έτοιμη‑για‑εκτέλεση λύση που απαντά στην ερώτηση “πώς να ορίσετε callback”, δείχνει **πώς να εξάγετε εικόνες**, και ακόμη καλύπτει **την εξαγωγή SVG από το Word**. Στο τέλος θα μπορείτε να **αποθηκεύσετε DOCX ως Markdown** με ένα προσαρμοσμένο σχήμα ονοματοδοσίας για κάθε πόρο εικόνας — χωρίς χειροκίνητη παρέμβαση.

## Τι Θα Μάθετε

- Γιατί ένα callback είναι ο πιο καθαρός τρόπος για να ελέγχετε τα ονόματα αρχείων εικόνων κατά τη μετατροπή.  
- Πώς να συνδέσετε το `MarkdownSaveOptions.resource_saving_callback` του Aspose.Words.  
- Κώδικας βήμα‑βήμα που εξάγει **PNG**, **JPG**, **SVG**, και οποιονδήποτε άλλο ενσωματωμένο πόρο.  
- Συμβουλές για τη διαχείριση συγκρούσεων ονομάτων, μεγάλων αρχείων και ιδιωματισμών διαδρομών σε διαφορετικές πλατφόρμες.  

> **Pro tip:** Αν ήδη χρησιμοποιείτε το Aspose.Words σε μεγαλύτερο pipeline, μπορείτε να προσθέσετε αυτό το callback χωρίς να τροποποιήσετε το υπόλοιπο κώδικα.

---

![Διάγραμμα ορισμού callback](https://example.com/images/how-to-set-callback.png "ορισμός callback")

## Προαπαιτούμενα

- Python 3.8+ (το παράδειγμα χρησιμοποιεί f‑strings, οπότε 3.6+ είναι εντάξει).  
- Πακέτο `aspose-words` εγκατεστημένο (`pip install aspose-words`).  
- Ένα αρχείο DOCX που περιέχει ραστερ εικόνες **και** διανυσματικά γραφικά (SVG).  
- Βασική εξοικείωση με συναρτήσεις Python και I/O αρχείων.

Αν έχετε όλα αυτά, ας βουτήξουμε.

---

## Πώς να ορίσετε Callback για την Εξαγωγή Εικόνων από DOCX

Ο πυρήνας της λύσης βρίσκεται σε ένα **resource‑saving callback**. Το Aspose.Words καλεί αυτόν τον delegate για κάθε εικόνα ή SVG που θέλει να γράψει όταν εκτελείτε `document.save`. Επιστρέφοντας ένα tuple `(new_name, data)` καθορίζετε τόσο το όνομα αρχείου όσο και το περιεχόμενο σε bytes.

```python
import aspose.words as aw
import os
import hashlib

# Step 1: Load the source document
document = aw.Document("YOUR_DIRECTORY/input.docx")
```

### Γιατί ένα Callback;

Χωρίς ένα callback, το Aspose.Words δημιουργεί αρχεία με ονόματα όπως `image1.png`, `image2.svg`, κ.λπ., και τα τοποθετεί σε φάκελο δίπλα στο αρχείο Markdown. Αυτό είναι αποδεκτό για γρήγορα demos, αλλά στην παραγωγή συχνά χρειάζεστε:

1. **Καθορισμένα ονόματα** – χρήσιμα για έλεγχο εκδόσεων ή δημοσίευση σε CDN.  
2. **Αποφυγή συγκρούσεων** – δύο εικόνες με το ίδιο αρχικό όνομα δεν θα αντικαταστήσουν η μία την άλλη.  
3. **Προσαρμοσμένες δομές φακέλων** – ίσως θέλετε όλα τα assets κάτω από `/assets/docs/`.

Το callback σας δίνει πλήρη έλεγχο πάνω σε αυτές τις τρεις απαιτήσεις.

---

## Εξαγωγή Εικόνων από DOCX Χρησιμοποιώντας Resource Callback

Παρακάτω βρίσκεται η υλοποίηση του callback. Υπολογίζει το hash των δυαδικών δεδομένων για να δημιουργήσει ένα μοναδικό επίθημα, διατηρεί την αρχική επέκταση αρχείου, και επιστρέφει το νέο όνομα αρχείου μαζί με τα ακατέργαστα bytes.

```python
def resource_callback(resource):
    """
    Called for every image/SVG that MarkdownSaveOptions wants to write.
    Returns a tuple (new_name, data) to control the saved file name.
    """
    # Preserve the original extension (.png, .svg, …)
    extension = os.path.splitext(resource.name)[1]

    # Compute a short hash of the image bytes – guarantees uniqueness
    hash_digest = hashlib.sha256(resource.data).hexdigest()[:10]

    # Build a deterministic, collision‑free filename
    new_name = f"img_{hash_digest}{extension}"
    return new_name, resource.data
```

#### Διαχείριση Edge‑Case

- **Μεγάλα αρχεία:** Το SHA‑256 λειτουργεί καλά για οποιοδήποτε μέγεθος· το hash υπολογίζεται στη μνήμη, οπότε προσέξτε τους περιορισμούς μνήμης αν επεξεργάζεστε τεράστια PDF.  
- **Απουσία επεκτάσεων:** Ορισμένα παλαιότερα αρχεία Word μπορεί να αποθηκεύουν εικόνες χωρίς ρητή επέκταση. Σε αυτήν την περίπτωση το `extension` θα είναι κενό· μπορείτε να ορίσετε προεπιλογή `.bin` ή να ελέγξετε τα πρώτα bytes για να μαντέψετε τη μορφή.  
- **Μη‑εικόνες πόροι:** Το callback καλείται για κάθε εξωτερικό πόρο (π.χ., OLE objects). Αν σας ενδιαφέρουν μόνο εικόνες/SVG, φιλτράρετε με βάση το `resource.type` πριν προχωρήσετε.

---

## Πώς να Εξάγετε Εικόνες και SVG από το Word

Τώρα ενσωματώνουμε το callback στη διαδικασία αποθήκευσης Markdown. Το αντικείμενο `MarkdownSaveOptions` εκθέτει την ιδιότητα `resource_saving_callback` ακριβώς για αυτόν τον σκοπό.

```python
# Step 2: Configure Markdown save options to use the callback
markdown_options = aw.saving.MarkdownSaveOptions()
markdown_options.resource_saving_callback = resource_callback

# Optional: set the folder where images will be placed relative to the .md file
markdown_options.resource_folder = "assets/images"
```

Ο ορισμός του `resource_folder` είναι προαιρετικός αλλά συχνά χρήσιμος. Αν το παραλείψετε, οι εικόνες θα καταλήξουν δίπλα στο αρχείο Markdown, κάτι που μπορεί να γεμίσει τη ρίζα του έργου σας.

### Αποθήκευση του Εγγράφου

```python
# Step 3: Save the document as Markdown, letting the callback store the resources
output_md_path = "YOUR_DIRECTORY/output.md"
document.save(output_md_path, markdown_options)
print(f"Markdown saved to {output_md_path}")
```

Όταν εκτελέσετε το script, θα δείτε μια σειρά αρχείων όπως:

```
assets/images/img_a1b2c3d4e5.png
assets/images/img_f6g7h8i9j0.svg
```

Και το παραγόμενο `output.md` θα περιέχει συνδέσμους εικόνων που δείχνουν ακριβώς σε αυτά τα ονόματα αρχείων:

```markdown
![Image](assets/images/img_a1b2c3d4e5.png)
```

Αυτό είναι το **πώς να εξάγετε εικόνες** σε δράση — κάθε εικόνα, ραστερ ή διανυσματική, είναι τώρα ένας ξεχωριστός, μοναδικά ονομασμένος πόρος.

---

## Αποθήκευση DOCX ως Markdown με Προσαρμοσμένη Διαχείριση Εικόνων

Συνδυάζοντας όλα τα παραπάνω, εδώ είναι το πλήρες script που μπορείτε να αντιγράψετε‑και‑επικολλήσετε σε ένα αρχείο με όνομα `convert_docx_to_md.py`:

```python
import aspose.words as aw
import os
import hashlib

def resource_callback(resource):
    """Control the naming of each exported image/SVG."""
    extension = os.path.splitext(resource.name)[1] or ".bin"
    hash_digest = hashlib.sha256(resource.data).hexdigest()[:10]
    new_name = f"img_{hash_digest}{extension}"
    return new_name, resource.data

def convert_docx_to_markdown(input_path, output_md_path, image_folder="assets/images"):
    # Load the DOCX
    document = aw.Document(input_path)

    # Set up Markdown options with our callback
    md_options = aw.saving.MarkdownSaveOptions()
    md_options.resource_saving_callback = resource_callback
    md_options.resource_folder = image_folder

    # Ensure the output directory exists
    os.makedirs(os.path.dirname(output_md_path), exist_ok=True)
    os.makedirs(os.path.join(os.path.dirname(output_md_path), image_folder), exist_ok=True)

    # Perform the conversion
    document.save(output_md_path, md_options)
    print(f"✅ Conversion complete! Markdown at: {output_md_path}")

if __name__ == "__main__":
    # Adjust these paths to your environment
    INPUT_DOCX = "YOUR_DIRECTORY/input.docx"
    OUTPUT_MD = "YOUR_DIRECTORY/output.md"
    convert_docx_to_markdown(INPUT_DOCX, OUTPUT_MD)
```

**Γιατί αυτό λειτουργεί:**  
- Το `resource_callback` εγγυάται ότι κάθε εικόνα λαμβάνει ένα μοναδικό, επαναλήψιμο όνομα.  
- Το `resource_folder` διατηρεί το Markdown καθαρό χωρίζοντας τα assets.  
- Οι κλήσεις `os.makedirs` σας προστατεύουν από σφάλματα “folder not found” όταν το script τρέχει σε νέο μηχάνημα.

## Εξαγωγή SVG από το Word – Τι γίνεται με τα Διανυσματικά Γραφικά;

Τα SVG αντιμετωπίζονται όπως τα PNG από το callback επειδή είναι απλώς ένας άλλος `resource`. Η μόνη διαφορά είναι ότι ορισμένες παλαιότερες εκδόσεις του Word ενσωματώνουν SVG ως αντικείμενα *OfficeArt*, τα οποία το Aspose.Words μετατρέπει αυτόματα σε ραστερ PNG εκτός αν ενεργοποιήσετε ρητά τη σημαία **preserve SVG**:

```python
md_options.export_svg = True  # Keep original SVG markup
```

Προσθέστε αυτή τη γραμμή πριν την αποθήκευση, και το callback θα λάβει πόρους με επέκταση `.svg`, διατηρώντας τα καθαρά διανυσματικά δεδομένα — ιδανικά για responsive web έγγραφα.

## Συχνές Ερωτήσεις & Παγίδες

| Ερώτηση | Απάντηση |
|----------|--------|
| **Τι γίνεται αν δύο εικόνες είναι πανομοιότυπες;** | Το SHA‑256 hash θα είναι ίδιο, οπότε τα ονόματα αρχείων συγκρούονται. Αν χρειάζεστε και τις δύο αντιγραφές, συμπεριλάβετε το αρχικό `resource.name` στον υπολογισμό του hash (π.χ., `hash(resource.name + resource.data)`). |
| **Μπορώ να αλλάξω τον φάκελο ανά τύπο αρχείου;** | Ναι. Μέσα στο `resource_callback` μπορείτε να ελέγξετε το `extension` και να επιστρέψετε διαδρομή όπως `f"png/{new_name}"` για ραστερ εικόνες και `f"svg/{new_name}"` για διανυσματικά. |
| **Λειτουργεί αυτό σε Linux/macOS;** | Απόλυτα. Ο κώδικας χρησιμοποιεί `os.path` που αφαιρεί τις διαφορές διαχωριστών διαδρομών. Απλώς βεβαιωθείτε ότι το αρχείο άδειας Aspose.Words (`aspose.words.lic`) είναι προσβάσιμο αν χρησιμοποιείτε την επί πληρωμή έκδοση. |
| **Τι γίνεται με τη χρήση μνήμης για τεράστια έγγραφα;** | Το callback λαμβάνει **το πλήρες byte array** για κάθε πόρο, πράγμα που σημαίνει ότι η εικόνα ζει προσωρινά στη μνήμη. Για αρχεία πολλαπλών gigabytes ίσως θελήσετε να ρέετε τα δεδομένα σε δίσκο μέσα στο callback αντί να τα επιστρέφετε. |

## Συμπέρασμα

Τώρα ξέρετε **πώς να ορίσετε callback** για να ελέγχετε την εξαγωγή εικόνων όταν **αποθηκεύετε DOCX ως Markdown**. Η προσέγγιση σας επιτρέπει να **εξάγετε εικόνες από DOCX**, **να εξάγετε SVG από το Word**, και να διατηρείτε το Markdown σας καθαρό και καθορισμένο.  

Σε ένα μόνο, αυτόνομο script καλύψαμε τη φόρτωση εγγράφου, τον ορισμό ενός resource‑saving callback, τη ρύθμιση του `MarkdownSaveOptions`, και τη διαχείριση edge‑case όπως συγκρούσεις ονομάτων και διανυσματικά γραφικά. Το αποτέλεσμα είναι ένα σύνολο μοναδικά ονομασμένων assets δίπλα σε ένα τέλεια συνδεδεμένο αρχείο Markdown — έτοιμο για static site generators, pipelines τεκμηρίωσης, ή οποιαδήποτε ροή εργασίας που χρειάζεται καθαρούς, επαναχρησιμοποιήσιμους πόρους.  

**Επόμενα βήματα;**  
- Δοκιμάστε να ενσωματώσετε αυτό το script με έναν static‑site generator όπως το MkDocs για αυτόματη δημοσίευση εγγράφων Word.  
- Πειραματιστείτε με `markdown_options.export_images_as_base64 = True` αν προτιμάτε ενσωματωμένες εικόνες αντί για εξωτερικά αρχεία.  
- Εμβαθύνετε στα άλλα callbacks του Aspose.Words (π.χ., `document_saving_callback`) για να ελέγξετε και την έξοδο του Markdown.

Έχετε περισσότερες ερωτήσεις για **πώς να εξάγετε εικόνες** από άλλες μορφές Office, ή χρειάζεστε βοήθεια για να προσαρμόσετε το callback σε συγκεκριμένο σχήμα ονοματοδοσίας; Αφήστε ένα σχόλιο παρακάτω, και καλή προγραμματιστική δουλειά!

## Τι Θα Μάθετε Στη Σειρά;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικά παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να κυριαρχήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Πώς να Μετονομάσετε Εικόνες Κατά τη Μετατροπή DOCX σε Markdown](/words/english/net/programming-with-markdownsaveoptions/how-to-rename-images-when-converting-docx-to-markdown/)
- [Πώς να Αποθηκεύσετε Markdown από DOCX – Οδηγός Βήμα‑Βήμα](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}