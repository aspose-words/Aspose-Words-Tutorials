---
category: general
date: 2026-11-18
description: Το παράδειγμα σκιάς σχήματος Aspose.Words δείχνει πώς να προσθέσετε σκιά
  σε σχήμα Word χρησιμοποιώντας Python. Ακολουθήστε αυτόν τον οδηγό βήμα‑βήμα για
  να τροποποιήσετε και να αποθηκεύσετε το έγγραφο.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose.words shape shadow example
- python shape shadow
- Aspose.Words for Python
- modify shape shadow
- document manipulation Aspose
language: el
lastmod: 2026-11-18
og_description: Το παράδειγμα σκιάς σχήματος Aspose.Words δείχνει πώς να προσθέσετε
  σκιά σε σχήμα Word με Python. Μάθετε τον πλήρη κώδικα, γιατί κάθε βήμα είναι σημαντικό
  και πώς να το προσαρμόσετε.
og_image_alt: Aspose.Words shape shadow example – Word document displaying a shape
  with a shadow applied using Python
og_title: Παράδειγμα σκιάς σχήματος Aspose.Words – Οδηγός Python
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Aspose.Words shape shadow example shows how to add a shadow to a Word
    shape using Python. Follow this step‑by‑step guide to modify and save the document.
  headline: Aspose.Words shape shadow example in Python
  type: TechArticle
- description: Aspose.Words shape shadow example shows how to add a shadow to a Word
    shape using Python. Follow this step‑by‑step guide to modify and save the document.
  name: Aspose.Words shape shadow example in Python
  steps:
  - name: Expected outcome
    text: Open `output.docx` in Microsoft Word. The first shape you added should now
      display a soft shadow that is offset by 2 pt horizontally and vertically, with
      a blur radius of 5 pt. All other content remains unchanged.
  - name: 'Alternative: Find a shape by name'
    text: 'If your document contains several shapes, you might prefer to locate a
      specific one:'
  - name: Working with multiple shapes
    text: 'If you need to apply the same shadow to every shape, iterate over the node
      collection:'
  - name: Applying a shadow to a specific shape type
    text: You can filter by `ShapeType` (e.g., `aw.ShapeType.IMAGE`). This is useful
      when you only want to affect pictures, not AutoShapes.
  - name: Handling documents without shapes
    text: The script already raises a clear `ValueError` if no shape is found. In
      production code you might log the issue and continue processing other files.
  - name: Compatibility notes
    text: '* The code works with **Aspose.Words for Python via .NET** version 23.10
      and later. * The shadow effect is supported in Word 2007+ (`.docx`). Older formats
      (`.doc`) will lose the effect after conversion.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Word automation
title: Παράδειγμα σκιάς σχήματος Aspose.Words σε Python
url: /el/python/images-shapes/aspose-words-shape-shadow-example-in-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Παράδειγμα σκιάς σχήματος Aspose.Words σε Python

Το παράδειγμα σκιάς σχήματος Aspose.Words δείχνει πώς να προσθέσετε εφέ σκιάς σε ένα σχήμα σε έγγραφο Word χρησιμοποιώντας Python. Σε αυτό το tutorial θα λάβετε ένα πλήρες, εκτελέσιμο script που φορτώνει ένα έγγραφο, ρυθμίζει τη σκιά και αποθηκεύει το αποτέλεσμα.

Η προσθήκη σκιάς σε σχήμα είναι ένας συνηθισμένος τρόπος βελτίωσης της οπτικής ιεραρχίας σε αναφορές, φυλλάδια ή τιμολόγια. Ο κώδικας παρακάτω λειτουργεί με Aspose.Words for Python via .NET και δεν απαιτεί πρόσθετες βιβλιοθήκες τρίτων.

## Τι θα μάθετε

* Πώς να φορτώσετε ένα αρχείο `.docx` με **Aspose.Words for Python**.  
* Πώς να εντοπίσετε το πρώτο σχήμα (συμπεριλαμβανομένων των σχημάτων μέσα σε πίνακες ή ομάδες).  
* Πώς να ρυθμίσετε το θολό, την οριζόντια μετατόπιση και την κάθετη μετατόπιση της σκιάς.  
* Πώς να αποθηκεύσετε το τροποποιημένο έγγραφο διατηρώντας όλο το υπόλοιπο περιεχόμενο.  

**Προαπαιτούμενα**

* Python 3.8 ή νεότερη έκδοση.  
* Aspose.Words for Python via .NET εγκατεστημένο (`pip install aspose-words`).  
* Ένα έγγραφο Word (`input.docx`) που περιέχει τουλάχιστον ένα σχήμα (π.χ. εικόνα, AutoShape ή πλαίσιο κειμένου).  

Αν χρειάζεται να εγκαταστήσετε τη βιβλιοθήκη, εκτελέστε:

```bash
pip install aspose-words
```

## Παράδειγμα σκιάς σχήματος Aspose.Words – επισκόπηση

Το παρακάτω script είναι η πλήρης λύση. Ακολουθεί τα τέσσερα λογικά βήματα μιας τυπικής ροής εργασίας **document manipulation Aspose**: φόρτωση, εντοπισμός, τροποποίηση και αποθήκευση.

```python
import aspose.words as aw

# ----------------------------------------------------------------------
# Step 1: Load the Word document
# ----------------------------------------------------------------------
# Replace YOUR_DIRECTORY with the path that contains input.docx.
doc_path = "YOUR_DIRECTORY/input.docx"
doc = aw.Document(doc_path)

# ----------------------------------------------------------------------
# Step 2: Access the first shape (including descendants)
# ----------------------------------------------------------------------
# NodeType.SHAPE searches for any shape node. The third argument (True)
# tells Aspose.Words to search recursively through all child nodes.
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

# Verify that a shape was found; raise a clear error if not.
if shape is None:
    raise ValueError("No shape found in the document. Ensure input.docx contains a shape.")

# ----------------------------------------------------------------------
# Step 3: Configure the shape's shadow
# ----------------------------------------------------------------------
# The Shadow object controls visual appearance. Adjust the properties
# to achieve the desired effect.
shape.shadow.blur = 5          # Softness of the shadow (0‑15 is typical)
shape.shadow.offset_x = 2      # Horizontal displacement in points
shape.shadow.offset_y = 2      # Vertical displacement in points

# Optional: Change shadow color or transparency if needed.
# shape.shadow.color = aw.Color.black
# shape.shadow.transparency = 0.5

# ----------------------------------------------------------------------
# Step 4: Save the modified document
# ----------------------------------------------------------------------
output_path = "YOUR_DIRECTORY/output.docx"
doc.save(output_path)

print(f"Shadow applied successfully. Saved to {output_path}")
```

### Αναμενόμενο αποτέλεσμα

Ανοίξτε το `output.docx` στο Microsoft Word. Το πρώτο σχήμα που προσθέσατε θα πρέπει τώρα να εμφανίζει μια ήπια σκιά που είναι μετατοπισμένη κατά 2 pt οριζόντια και κάθετα, με ακτίνα θολώματος 5 pt. Όλο το υπόλοιπο περιεχόμενο παραμένει αμετάβλητο.

## Βήμα 1: Φόρτωση του εγγράφου Word

Η φόρτωση ενός εγγράφου είναι η πρώτη ενέργεια σε οποιαδήποτε ροή εργασίας **Aspose.Words for Python**. Η κλάση `Document` αναλύει το αρχείο και δημιουργεί ένα μοντέλο αντικειμένων στη μνήμη. Επειδή η βιβλιοθήκη λειτουργεί στην πλατφόρμα .NET, μπορεί να διαχειριστεί μεγάλα αρχεία αποδοτικά.

*Γιατί είναι σημαντικό:* Η φόρτωση του εγγράφου μία φορά και η διατήρηση μιας αναφοράς (`doc`) αποφεύγει επαναλαμβανόμενες I/O λειτουργίες, βελτιώνοντας την απόδοση όταν χρειάζεται να εφαρμόσετε πολλαπλές τροποποιήσεις.

## Βήμα 2: Πρόσβαση στο σχήμα

Τα σχήματα μπορούν να είναι άμεσα παιδιά του σώματος του εγγράφου, ή να είναι ενσωματωμένα μέσα σε πίνακες, ομάδες ή καμβάδες σχεδίασης. Η χρήση του `get_child(NodeType.SHAPE, 0, True)` ψάχνει αναδρομικά και επιστρέφει το πρώτο ταιριαστό σχήμα.

*Γιατί είναι σημαντικό:* Η σημαία `True` εξασφαλίζει ότι δεν θα χάσετε σχήματα που είναι κρυμμένα μέσα σε άλλους κόμβους. Αν την παραλείψετε, θα ληφθούν υπόψη μόνο τα σχήματα του ανώτερου επιπέδου, και πολλά πραγματικά έγγραφα θα επιστρέψουν `None`.

### Εναλλακτική: Εύρεση σχήματος με όνομα

Αν το έγγραφό σας περιέχει πολλά σχήματα, ίσως προτιμήσετε να εντοπίσετε ένα συγκεκριμένο:

```python
shape = doc.get_child(aw.NodeType.SHAPE, lambda n: n.name == "MyLogo", True)
```

Αυτό το απόσπασμα δείχνει μια **python shape shadow** παραλλαγή που φιλτράρει με βάση την ιδιότητα `name` του σχήματος.

## Βήμα 3: Ρύθμιση της σκιάς του σχήματος

Η ιδιότητα `shadow` ενός αντικειμένου `Shape` σας δίνει λεπτομερή έλεγχο του οπτικού εφέ. Τα τρία πιο συχνά ρυθμιζόμενα χαρακτηριστικά είναι:

| Ιδιότητα | Τυπικό εύρος | Οπτική επίδραση |
|----------|---------------|-----------------|
| `blur`   | 0 – 15        | Μεγαλύτερες τιμές δημιουργούν πιο απαλό άκρο. |
| `offset_x` | –10 – 10   | Θετικές τιμές μετακινούν τη σκιά προς τα δεξιά. |
| `offset_y` | –10 – 10   | Θετικές τιμές μετακινούν τη σκιά προς τα κάτω. |

Μπορείτε επίσης να τροποποιήσετε `color`, `transparency`, `visible` και `style`. Το παράδειγμα ορίζει ήπιο θόλωμα και μικρή μετατόπιση ώστε η σκιά να παραμένει διακριτική.

**Συμβουλή:** Όταν ένα σχήμα έχει ήδη σκιά, οι παραπάνω ιδιότητες αντικαθιστούν τις υπάρχουσες ρυθμίσεις. Αν χρειάζεται να διατηρήσετε το αρχικό στυλ, διαβάστε τις τρέχουσες τιμές πριν τις αλλάξετε.

## Βήμα 4: Αποθήκευση του τροποποιημένου εγγράφου

Η κλήση `doc.save()` γράφει την αναπαράσταση στη μνήμη πίσω σε ένα αρχείο `.docx`. Το Aspose.Words ενημερώνει αυτόματα όλες τις εσωτερικές σχέσεις, ώστε το αρχείο εξόδου να παραμένει πλήρως συμβατό με το Microsoft Word.

*Γιατί είναι σημαντικό:* Η αποθήκευση μόνο μία φορά στο τέλος της διαδικασίας μειώνει τον κίνδυνο διαφθοράς του αρχείου και βελτιώνει τη συνολική ταχύτητα, ειδικά όταν επεξεργάζεστε πολλά έγγραφα σε batch job.

## Κοινές παραλλαγές και ακραίες περιπτώσεις

### Εργασία με πολλαπλά σχήματα

Αν χρειάζεται να εφαρμόσετε την ίδια σκιά σε κάθε σχήμα, επαναλάβετε πάνω στη συλλογή κόμβων:

```python
for shp in doc.get_child_nodes(aw.NodeType.SHAPE, True):
    shp.shadow.blur = 5
    shp.shadow.offset_x = 2
    shp.shadow.offset_y = 2
```

### Εφαρμογή σκιάς σε συγκεκριμένο τύπο σχήματος

Μπορείτε να φιλτράρετε με `ShapeType` (π.χ. `aw.ShapeType.IMAGE`). Αυτό είναι χρήσιμο όταν θέλετε να επηρεάσετε μόνο εικόνες, όχι AutoShapes.

```python
for shp in doc.get_child_nodes(aw.NodeType.SHAPE, True):
    if shp.shape_type == aw.ShapeType.IMAGE:
        shp.shadow.blur = 4
```

### Διαχείριση εγγράφων χωρίς σχήματα

Το script ήδη εγείρει ένα σαφές `ValueError` αν δεν βρεθεί σχήμα. Σε κώδικα παραγωγής μπορείτε να καταγράψετε το πρόβλημα και να συνεχίσετε την επεξεργασία άλλων αρχείων.

### Σημειώσεις συμβατότητας

* Ο κώδικας λειτουργεί με **Aspose.Words for Python via .NET** έκδοση 23.10 και νεότερη.  
* Το εφέ σκιάς υποστηρίζεται σε Word 2007+ (`.docx`). Παλαιότερες μορφές (`.doc`) θα χάσουν το εφέ μετά τη μετατροπή.

## Συμπέρασμα

Αυτό το **aspose.words shape shadow example** σας καθοδηγεί βήμα‑βήμα στη φόρτωση ενός αρχείου Word, τον εντοπισμό ενός σχήματος, τη ρύθμιση της σκιάς του και την αποθήκευση του αποτελέσματος με **Aspose.Words for Python**. Διαθέτετε πλέον ένα επαναχρησιμοποιήσιμο πρότυπο για οποιοδήποτε σενάριο **document manipulation Aspose** που περιλαμβάνει οπτικές βελτιώσεις.

Στη συνέχεια, μπορείτε να εξερευνήσετε:

* Προσθήκη διαβαθμισμένων γεμισμάτων ή στυλ γραμμής σε σχήματα (`modify shape shadow` και άλλες οπτικές ιδιότητες).  
* Συνδυασμό ρύθμισης σκιάς με μορφοποίηση κειμένου για δημιουργία πλήρως στιλιζαρισμένων προτύπων.  
* Αυτοματοποίηση της διαδικασίας για μια δέσμη εγγράφων χρησιμοποιώντας `os.listdir` και το μοτίβο που φαίνεται παραπάνω.

Μη διστάσετε να πειραματιστείτε με διαφορετικά επίπεδα θολώματος, μετατοπίσεις και χρώματα ώστε να ταιριάζουν με τις οδηγίες της εταιρικής σας ταυτότητας. Καλή προγραμματιστική!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στην υλοποίηση των δικών σας έργων.

- [Προσθήκη σκιάς σε σχήμα σε Python – Πλήρες tutorial Aspose.Words](/words/english/python-net/images-shapes/add-shadow-to-shape-in-python-complete-aspose-words-tutorial/)
- [Πώς να ορίσετε σκιά σε σχήμα στο Aspose.Words for Python](/words/english/python-net/images-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-for-python/)
- [Πώς να αποθηκεύσετε PNG και να προσθέσετε σκιά σε σχήμα με Aspose.Words](/words/english/python-net/images-shapes/how-to-save-png-and-add-shadow-to-shape-with-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}