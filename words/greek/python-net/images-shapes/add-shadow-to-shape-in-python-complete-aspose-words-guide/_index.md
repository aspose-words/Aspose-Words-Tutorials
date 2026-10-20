---
category: general
date: 2026-08-11
description: Προσθέστε σκιά σε σχήμα χρησιμοποιώντας το Aspose.Words για Python. Μάθετε
  πώς να προσθέσετε σκιά σε σχήμα, να εφαρμόσετε θόλωση στο σχήμα και να προσαρμόσετε
  την απόσταση και το χρώμα.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shadow to shape
- add shape shadow
- apply blur to shape
- Aspose.Words shadow effect
- Python Word shape styling
language: el
lastmod: 2026-08-11
og_description: Προσθέστε σκιά σε σχήμα με το Aspose.Words για Python. Αυτός ο οδηγός
  σας δείχνει πώς να εφαρμόσετε θόλωση σε σχήμα, να ορίσετε μετατοπίσεις και να επιλέξετε
  χρώματα σκιάς με λίγες μόνο γραμμές κώδικα.
og_image_alt: Word document screenshot showing a shape with a black shadow applied
og_title: Προσθήκη σκιάς σε σχήμα με Python – βήμα‑βήμα οδηγός Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-11'
  description: Add shadow to shape using Aspose.Words for Python. Learn how to add
    shape shadow, apply blur to shape, and customize offset and color.
  headline: Add shadow to shape in Python – complete Aspose.Words guide
  type: TechArticle
- description: Add shadow to shape using Aspose.Words for Python. Learn how to add
    shape shadow, apply blur to shape, and customize offset and color.
  name: Add shadow to shape in Python – complete Aspose.Words guide
  steps:
  - name: Adding shadow to a specific shape by name
    text: 'If your document contains several shapes, you may want to target one by
      its `name` property:'
  - name: Skipping non‑visual nodes
    text: Sometimes a shape node can be a placeholder (e.g., a drawing canvas without
      visual content). Guard against this by checking `shape.is_image` or `shape.is_picture_frame`
      before applying the shadow.
  - name: Working with grouped shapes
    text: When shapes are grouped, the group itself is a `Shape` node. To apply a
      shadow to each member, iterate through `shape.get_child_nodes(aw.NodeType.SHAPE,
      True)`.
  - name: What’s next?
    text: '- Explore **apply blur to shape** for other effects like glow or soft edges.
      - Combine shadows with **shape borders** or **reflection** to create richer
      graphics. - Convert the edited document to PDF (`doc.save("output.pdf", aw.SaveFormat.PDF)`)
      for distribution.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Word automation
title: Προσθήκη σκιάς σε σχήμα με Python – πλήρης οδηγός Aspose.Words
url: /el/python/images-shapes/add-shadow-to-shape-in-python-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Προσθήκη σκιάς σε σχήμα σε Python – πλήρης οδηγός Aspose.Words

Αν χρειάζεται να **προσθέσετε σκιά σε σχήμα** σε ένα έγγραφο Word, αυτό το tutorial σας δείχνει ακριβώς πώς να το κάνετε με το Aspose.Words for Python. Είτε δημιουργείτε έναν γεννήτορα αναφορών είτε μια υπηρεσία προτύπων εγγράφων, θα μάθετε πώς να προσθέτετε σκιά σε σχήμα, να εφαρμόζετε θολότητα και να ρυθμίζετε την εμφάνιση της σκιάς με λίγες μόνο γραμμές κώδικα.

Ο οδηγός καλύπτει όλα όσα χρειάζεστε: τις απαιτούμενες εισαγωγές, τον εντοπισμό του στόχου σχήματος (συμπεριλαμβανομένων των ενσωματωμένων κόμβων), τη διαμόρφωση των ιδιοτήτων της σκιάς, την αντιμετώπιση κοινών περιπτώσεων άκρων και την αποθήκευση του τροποποιημένου εγγράφου. Στο τέλος θα έχετε ένα επαναχρησιμοποιήσιμο απόσπασμα κώδικα που μπορείτε να ενσωματώσετε σε οποιοδήποτε έργο Python που δουλεύει με αρχεία .docx.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

- **Python 3.8+** εγκατεστημένο.
- **Aspose.Words for Python via .NET** (εγκατάσταση με `pip install aspose-words`).
- Ένα έγγραφο Word (`input.docx`) που περιέχει τουλάχιστον ένα σχήμα (π.χ. ένα ορθογώνιο, εικόνα ή SmartArt).
- Βασική εξοικείωση με την Python και το μοντέλο αντικειμένων Aspose.Words.

## Βήμα 1: Εισαγωγή του Aspose.Words και άνοιγμα του εγγράφου

Το πρώτο βήμα είναι η εισαγωγή του πακέτου `aspose.words` (συνήθως με ψευδώνυμο `aw`) και η φόρτωση του πηγαίου εγγράφου.

```python
import aspose.words as aw

# Load the Word document from the file system
doc_path = "YOUR_DIRECTORY/input.docx"
doc = aw.Document(doc_path)
```

*Γιατί είναι σημαντικό*: Το άνοιγμα του εγγράφου σας δίνει πρόσβαση στο δέντρο κόμβων όπου ζουν τα σχήματα. Η κλάση `aw.Document` είναι το σημείο εισόδου για όλες τις περαιτέρω επεμβάσεις.

## Βήμα 2: Εντοπισμός του πρώτου σχήματος (συμπεριλαμβανομένων των ενσωματωμένων κόμβων)

Τα σχήματα μπορεί να είναι άμεσα παιδιά μιας `Paragraph` ή να είναι ενσωματωμένα σε άλλους containers (όπως πίνακες). Η χρήση του `get_child` με τη σημαία `is_deep` ορισμένη σε `True` εξασφαλίζει ότι θα ανακτήσετε το πρώτο σχήμα ανεξάρτητα από την εσοχή.

```python
# Retrieve the first shape in the document, searching recursively
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

if shape is None:
    raise ValueError("No shape found in the document. Add a shape before applying a shadow.")
```

*Γιατί είναι σημαντικό*: Η λειτουργία `add shape shadow` απαιτεί ένα αντικείμενο `Shape`. Η βαθιά αναζήτηση αποτρέπει το να χάσετε σχήματα που κρύβονται μέσα σε πίνακες ή ομάδες.

## Βήμα 3: Ενεργοποίηση της σκιάς και ορισμός βασικών ιδιοτήτων

Το Aspose.Words αντιπροσωπεύει μια σκιά με πολλές ιδιότητες. Πρώτα, ενεργοποιήστε τη σκιά ορίζοντας το `shadow_visible` σε `True`.

```python
# Enable the shadow effect
shape.shadow_visible = True
```

Τώρα μπορείτε να ρυθμίσετε την ακτίνα θολώματος, τις μετατοπίσεις και το χρώμα.

## Βήμα 4: Εφαρμογή θολώματος στο σχήμα και ορισμός τιμών μετατόπισης

Η ακτίνα θολώματος ελέγχει πόσο μαλακή φαίνεται η σκιά. Μια τιμή `5.0` δίνει ένα εμφανές αλλά όχι υπερβολικό θόλωμα. Οι μετατοπίσεις μετακινούν τη σκιά οριζόντια και κάθετα.

```python
# Apply blur to shape – this is the "apply blur to shape" part
shape.shadow_blur = 5.0          # Blur radius in points

# Define horizontal (X) and vertical (Y) offsets
shape.shadow_offset_x = 2.0     # Move shadow 2 points to the right
shape.shadow_offset_y = 2.0     # Move shadow 2 points down
```

*Γιατί είναι σημαντικό*: Η ρύθμιση του `shadow_blur` και των τιμών μετατόπισης σας επιτρέπει να δημιουργήσετε ρεαλιστικά εφέ βάθους που ταιριάζουν με το οπτικό στυλ του εγγράφου σας.

## Βήμα 5: Επιλογή χρώματος σκιάς (add shape shadow with custom color)

Μπορείτε να χρησιμοποιήσετε οποιοδήποτε `aw.Color`. Εδώ επιλέγουμε το μαύρο, αλλά μπορείτε να το αντικαταστήσετε με `aw.Color.red`, `aw.Color.from_argb(255, 0, 120, 215)`, κ.λπ.

```python
# Set the shadow color – black in this example
shape.shadow_color = aw.Color.black
```

*Γιατί είναι σημαντικό*: Το χρώμα καθορίζει πώς η σκιά αλληλεπιδρά με το περιεχόμενο γύρω της. Σκοτεινότερες σκιές είναι πιο ορατές σε ανοιχτά φόντα, ενώ πιο ανοιχτές αποχρώσεις λειτουργούν καλύτερα σε σκοτεινές σελίδες.

## Βήμα 6: Αποθήκευση του ενημερωμένου εγγράφου

Τέλος, γράψτε τις αλλαγές πίσω στο δίσκο. Μπορείτε να αντικαταστήσετε το αρχικό αρχείο ή να δημιουργήσετε ένα νέο.

```python
output_path = "YOUR_DIRECTORY/output_with_shadow.docx"
doc.save(output_path)

print(f"Shadow applied successfully. Saved to {output_path}")
```

Όταν ανοίξετε το `output_with_shadow.docx` στο Microsoft Word, το πρώτο σχήμα θα εμφανίζει μια ήπια μαύρη σκιά με το καθορισμένο θόλωμα και τη μετατόπιση.

## Πλήρες, εκτελέσιμο παράδειγμα

Συνδυάζοντας όλα τα παραπάνω, εδώ είναι ένα αυτόνομο script που μπορείτε να τρέξετε αμέσως:

```python
import aspose.words as aw

def add_shadow_to_first_shape(input_path: str, output_path: str,
                              blur: float = 5.0,
                              offset_x: float = 2.0,
                              offset_y: float = 2.0,
                              color: aw.Color = aw.Color.black) -> None:
    """
    Loads a Word document, finds the first shape (deep search),
    and applies a shadow effect.

    Parameters
    ----------
    input_path : str
        Path to the source .docx file.
    output_path : str
        Path where the modified document will be saved.
    blur : float, optional
        Blur radius for the shadow. Default is 5.0 points.
    offset_x : float, optional
        Horizontal offset of the shadow. Default is 2.0 points.
    offset_y : float, optional
        Vertical offset of the shadow. Default is 2.0 points.
    color : aw.Color, optional
        Shadow color. Default is black.
    """
    # Load the document
    doc = aw.Document(input_path)

    # Retrieve the first shape, searching recursively
    shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

    if shape is None:
        raise ValueError("No shape found in the document. Insert a shape before calling this function.")

    # Enable shadow and configure its appearance
    shape.shadow_visible = True
    shape.shadow_blur = blur
    shape.shadow_offset_x = offset_x
    shape.shadow_offset_y = offset_y
    shape.shadow_color = color

    # Save the result
    doc.save(output_path)

if __name__ == "__main__":
    INPUT_DOC = "YOUR_DIRECTORY/input.docx"
    OUTPUT_DOC = "YOUR_DIRECTORY/output_with_shadow.docx"
    add_shadow_to_first_shape(INPUT_DOC, OUTPUT_DOC)
```

**Αναμενόμενο αποτέλεσμα**: Το άνοιγμα του `output_with_shadow.docx` δείχνει το πρώτο σχήμα με μια διακριτική μαύρη σκιά που είναι θολή, μετατοπισμένη κατά 2 pt οριζόντια και κάθετα, σύμφωνα με τις παραμέτρους που περάσατε.

## Διαχείριση πολλαπλών σχημάτων και περιπτώσεων άκρων

### Προσθήκη σκιάς σε συγκεκριμένο σχήμα με βάση το όνομα

Αν το έγγραφό σας περιέχει πολλά σχήματα, ίσως θέλετε να στοχεύσετε ένα με την ιδιότητα `name` του:

```python
target_name = "MyRectangle"
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)  # start with first shape
while shape is not None and shape.name != target_name:
    shape = shape.next_sibling(aw.NodeType.SHAPE)

if shape is None:
    raise ValueError(f"Shape named '{target_name}' not found.")
```

### Παράλειψη μη‑οπτικών κόμβων

Μερικές φορές ένας κόμβος σχήματος μπορεί να είναι placeholder (π.χ. ένας καμβάς σχεδίασης χωρίς οπτικό περιεχόμενο). Προστατέψτε τον κώδικά σας ελέγχοντας `shape.is_image` ή `shape.is_picture_frame` πριν εφαρμόσετε τη σκιά.

```python
if not shape.is_image and not shape.is_picture_frame:
    # Proceed only if the shape can display a shadow
    shape.shadow_visible = True
```

### Εργασία με ομαδοποιημένα σχήματα

Όταν τα σχήματα είναι ομαδοποιημένα, η ομάδα αυτή καθαυτή είναι ένας κόμβος `Shape`. Για να εφαρμόσετε σκιά σε κάθε μέλος, επαναλάβετε μέσω `shape.get_child_nodes(aw.NodeType.SHAPE, True)`.

```python
if shape.is_group:
    for child in shape.get_child_nodes(aw.NodeType.SHAPE, True):
        child.shadow_visible = True
        child.shadow_blur = blur
        child.shadow_offset_x = offset_x
        child.shadow_offset_y = offset_y
        child.shadow_color = color
```

Αυτές οι παραλλαγές διασφαλίζουν ότι ο κώδικάς σας λειτουργεί αξιόπιστα σε διαφορετικές διατάξεις εγγράφων.

## Pro tips για τέλειες σκιές

- **Συνέπεια**: Χρησιμοποιήστε την ίδια ακτίνα θολώματος και μετατόπιση για όλα τα σχήματα σε μια αναφορά ώστε η οπτική γλώσσα να παραμένει συνεπής.
- **Απόδοση**: Η εφαρμογή σκιών σε δεκάδες εικόνες υψηλής ανάλυσης μπορεί να αυξήσει το μέγεθος του αρχείου. Δοκιμάστε το μέγεθος εξόδου αν σκοπεύετε να δημιουργήσετε PDF αργότερα.
- **Αντίθεση χρωμάτων**: Σε σκοτεινά φόντα σελίδας, σκεφτείτε μια πιο ανοιχτή σκιά (`aw.Color.gray`) για να διατηρήσετε την ορατότητα.
- **Προεπισκόπηση**: Η διεπαφή “Shadow” του Word αντικατοπτρίζει τις ιδιότητες του Aspose.Words, οπότε μπορείτε να πειραματιστείτε χειροκίνητα και μετά να αντιγράψετε τις τιμές στο script σας.

## Συμπέρασμα

Τώρα ξέρετε πώς να **προσθέσετε σκιά σε σχήμα** σε ένα έγγραφο Word χρησιμοποιώντας το Aspose.Words for Python. Ο οδηγός κάλυψε τον εντοπισμό σχήματος, την ενεργοποίηση της σκιάς, το **add shape shadow** με προσαρμοσμένο θόλωμα, μετατοπίσεις και χρώμα, καθώς και την αποθήκευση του αποτελέσματος. Με τη λειτουργία που δημιουργήσατε παραπάνω, μπορείτε να ενσωματώσετε αυτό το εφέ σε οποιοδήποτε pipeline δημιουργίας εγγράφων.

### Τι ακολουθεί;

- Εξερευνήστε το **apply blur to shape** για άλλα εφέ όπως glow ή soft edges.
- Συνδυάστε σκιές με **shape borders** ή **reflection** για πιο πλούσια γραφικά.
- Μετατρέψτε το επεξεργασμένο έγγραφο σε PDF (`doc.save("output.pdf", aw.SaveFormat.PDF)`) για διανομή.

Μη διστάσετε να πειραματιστείτε με διαφορετικά χρώματα, επίπεδα θολώματος και τιμές μετατόπισης ώστε να ταιριάζουν με τις οδηγίες branding σας. Καλό coding!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετικές θεματικές που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}