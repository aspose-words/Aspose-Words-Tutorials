---
category: general
date: 2026-10-04
description: Πώς να δημιουργήσετε έγγραφο σε Python και να προσθέσετε σκιά σε σχήμα
  χρησιμοποιώντας το Aspose.Words. Μάθετε πώς να ορίσετε το χρώμα της σκιάς, να εισάγετε
  σχήμα ορθογωνίου και να προσαρμόσετε την εξωτερική σκιά.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to create document
- add shadow to shape
- set shadow color
- insert rectangle shape
- how to add shadow
language: el
lastmod: 2026-10-04
og_description: Πώς να δημιουργήσετε ένα έγγραφο σε Python και να προσθέσετε σκιά
  σε σχήμα. Αυτός ο οδηγός σας δείχνει πώς να ορίσετε το χρώμα της σκιάς, να εισάγετε
  σχήμα ορθογωνίου και να εφαρμόσετε εξωτερική σκιά χρησιμοποιώντας το Aspose.Words.
og_image_alt: Python code inserting a rectangle shape with a visible shadow into a
  Word document
og_title: Πώς να δημιουργήσετε έγγραφο με σχήμα ορθογωνίου και σκιά σε Python
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: How to create document in Python and add shadow to shape using Aspose.Words.
    Learn to set shadow color, insert rectangle shape, and customize outer shadow.
  headline: How to create document with a rectangle shape and shadow in Python
  type: TechArticle
- description: How to create document in Python and add shadow to shape using Aspose.Words.
    Learn to set shadow color, insert rectangle shape, and customize outer shadow.
  name: How to create document with a rectangle shape and shadow in Python
  steps:
  - name: Why does the shadow sometimes appear invisible?
    text: The shadow is only rendered if `shadow.visible` is set to `True` **and**
      the shape’s `wrap_type` allows it to be displayed. An inline shape works reliably;
      floating shapes may require additional layout adjustments.
  - name: How can I change the shadow color to match a brand palette?
    text: 'Replace `aw.drawing.Color.black` with a custom RGB value:'
  - name: What if I need the shape to appear behind text?
    text: Set the wrap type to `WrapType.BEHIND` and adjust the `z_order_position`
      if necessary. Keep in mind that some viewers may render behind‑text shapes differently.
  - name: Can I apply the same shadow settings to multiple shapes?
    text: Yes. Create a helper function that configures the shadow and call it for
      each shape you insert. This promotes code reuse and ensures consistent styling.
  type: HowTo
tags:
- Aspose.Words
- Python
- Word automation
title: Πώς να δημιουργήσετε ένα έγγραφο με σχήμα ορθογωνίου και σκιά σε Python
url: /el/python/images-shapes/how-to-create-document-with-a-rectangle-shape-and-shadow-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να δημιουργήσετε έγγραφο με σχήμα ορθογωνίου και σκιά σε Python

Αν χρειάζεστε **πώς να δημιουργήσετε έγγραφο** που περιέχει ένα μορφοποιημένο ορθογώνιο, αυτός ο οδηγός παρέχει μια πλήρη λύση. Θα δείτε πώς να **προσθέσετε σκιά σε σχήμα**, να ορίσετε το χρώμα της σκιάς και να ελέγξετε την απόσταση και το θολό εφέ — όλα με το Aspose.Words for Python. Στο τέλος του tutorial θα μπορείτε να δημιουργήσετε ένα αρχείο `.docx` που φαίνεται επαγγελματικό και έτοιμο για διανομή.

Τα παρακάτω βήματα καλύπτουν τα πάντα, από την εγκατάσταση της βιβλιοθήκης μέχρι την προσαρμογή της εμφάνισης της σκιάς. Δεν απαιτείται εξωτερική τεκμηρίωση· ο κώδικας είναι έτοιμος για αντιγραφή, εκτέλεση και προσαρμογή στα δικά σας έργα. Θα μάθετε επίσης πώς να **εισάγετε σχήμα ορθογωνίου**, να επιλέξετε ένα **στυλ εξωτερικής σκιάς** και να αντιμετωπίσετε κοινά προβλήματα όπως αόρατες σκιές ή λανθασμένες ρυθμίσεις περιτύλιξης.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

* Python 3.8 ή νεότερο εγκατεστημένο.
* Ένα ενεργό license του Aspose.Words for Python (ή ένα δωρεάν κλειδί αξιολόγησης).
* Βασική εξοικείωση με το scripting σε Python.
* Πρόσβαση σε τοποθεσία του συστήματος αρχείων όπου θα αποθηκευτεί το παραγόμενο έγγραφο.

Μπορείτε να εγκαταστήσετε το SDK με pip:

```bash
pip install aspose-words
```

## Βήμα 1: Εισαγωγή της βιβλιοθήκης και δημιουργία νέου κενού εγγράφου

Η δημιουργία ενός νέου εγγράφου είναι η πρώτη ενέργεια σε κάθε σενάριο αυτοματοποίησης του Word. Ο κατασκευαστής `aw.Document()` σας δίνει ένα κενό αρχείο που μπορείτε να γεμίσετε με κείμενο, εικόνες ή σχήματα.

```python
import aspose.words as aw

# Create a new blank document
document = aw.Document()
builder = aw.DocumentBuilder(document)
```

Το αντικείμενο `DocumentBuilder` απλοποιεί την εισαγωγή περιεχομένου. Παρακολουθεί τη θέση του τρέχοντος δρομέα, ώστε να μπορείτε να προσθέτετε στοιχεία διαδοχικά χωρίς να διαχειρίζεστε χειροκίνητα τις ενότητες.

## Βήμα 2: Εισαγωγή σχήματος ορθογωνίου του επιθυμητού μεγέθους

Ένα σχήμα ορθογωνίου λειτουργεί ως δοχείο για οπτικά στοιχεία. Μπορείτε να ορίσετε το πλάτος και το ύψος του σε points (1 pt ≈ 1/72 in).

```python
# Insert a rectangle shape that is 150 pt wide and 80 pt tall
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)
```

Σε αυτό το σημείο το σχήμα δεν έχει οπτική μορφοποίηση, επομένως εμφανίζεται ως απλό περίγραμμα. Τα επόμενα βήματα θα του δώσουν βάθος και χρώμα.

## Βήμα 3: Ορισμός του σχήματος ώστε να ρέει ενσωματωμένο με το κείμενο

Όταν ένα σχήμα είναι **inline**, συμπεριφέρεται όπως ένας χαρακτήρας σε παράγραφο. Αυτό εξασφαλίζει ότι το ορθογώνιο παραμένει εκεί που το περιμένετε στη διάταξη του εγγράφου.

```python
# Make the shape inline so it follows the text flow
rectangle_shape.wrap_type = aw.drawing.WrapType.INLINE
```

Αν προτιμάτε το σχήμα να «πλέει» πάνω από το κείμενο, μπορείτε να χρησιμοποιήσετε `WrapType.SQUARE` ή `WrapType.TOP_BOTTOM`, αλλά για τις περισσότερες αναφορές ένα ενσωματωμένο σχήμα διατηρεί την διάταξη προβλέψιμη.

## Βήμα 4: Κατάσταση της σκιάς σε ορατή και επιλογή χρώματος

Μια σκιά που δεν είναι ορατή δεν προσφέρει οπτικό όφελος. Η σημαία `visible` ενεργοποιεί το εφέ, και η ιδιότητα `color` καθορίζει την απόχρωση. Η χρήση του μαύρου δίνει κλασικό, διακριτικό βάθος.

```python
# Enable the shadow and set its color to black
rectangle_shape.shadow.visible = True
rectangle_shape.shadow.color = aw.drawing.Color.black
```

Μπορείτε να αντικαταστήσετε το `aw.drawing.Color.black` με οποιοδήποτε άλλο χρώμα, όπως `aw.drawing.Color.gray` ή μια προσαρμοσμένη τιμή RGB (`aw.drawing.Color.from_argb(255, 128, 128, 128)`).

## Βήμα 5: Ορισμός της απόστασης και του θολώματος της σκιάς για βάθος

Η απόσταση ελέγχει πόσο μακριά μετατοπίζεται η σκιά από το σχήμα, ενώ η ακτίνα θολώματος μαλακώνει τις άκρες. Μικρές τιμές δημιουργούν καθαρή σκιά· μεγαλύτερες τιμές παράγουν πιο απαλό αποτέλεσμα.

```python
# Horizontal and vertical offset of 5 pt each
rectangle_shape.shadow.offset_x = 5
rectangle_shape.shadow.offset_y = 5

# Blur radius of 3 pt for a gentle feather
rectangle_shape.shadow.blur = 3
```

Πειραματιστείτε με αυτούς τους αριθμούς ώστε να ταιριάζουν με τις οδηγίες σχεδίασής σας. Για έντονη πτώση σκιάς μπορείτε να αυξήσετε τόσο την απόσταση όσο και το θόλωμα.

## Βήμα 6: Επιλογή στυλ εξωτερικής σκιάς

Το Aspose.Words προσφέρει διάφορα στυλ σκιάς, όπως `INNER`, `OUTER` και `PERSPECTIVE`. Το **outer** στυλ τοποθετεί τη σκιά έξω από το περίγραμμα του σχήματος, κάτι που είναι ιδανικό για καθαρή, επαγγελματική εμφάνιση.

```python
# Apply an outer shadow style
rectangle_shape.shadow.style = aw.drawing.ShadowStyle.OUTER
```

Αν χρειάζεστε πιο δραματικό εφέ, δοκιμάστε το `ShadowStyle.PERSPECTIVE` — προσθέτει τρισδιάστατη κλίση.

## Βήμα 7: Αποθήκευση του εγγράφου με τη σχήμα-σκιά

Η αποθήκευση ολοκληρώνει το αρχείο και γράφει όλη τη μορφοποίηση στο δίσκο. Επιλέξτε έναν φάκελο για τον οποίο έχετε δικαιώματα εγγραφής και δώστε στο αρχείο ένα περιγραφικό όνομα.

```python
# Save the document to the desired location
output_path = "output/ShapeWithShadow.docx"
document.save(output_path)
print(f"Document saved to {output_path}")
```

Η εκτέλεση του script παράγει ένα αρχείο Word που περιέχει ένα ορθογώνιο με ορατή, χρωματιστή σκιά. Ανοίξτε το αρχείο στο Microsoft Word ή στο LibreOffice για να επαληθεύσετε το αποτέλεσμα.

## Πλήρες εκτελέσιμο παράδειγμα

Ακολουθεί το πλήρες script που ενσωματώνει κάθε βήμα που συζητήθηκε. Αντιγράψτε τον κώδικα σε ένα αρχείο με όνομα `create_shadowed_shape.py` και εκτελέστε το με `python create_shadowed_shape.py`.

```python
import aspose.words as aw
import os

def main():
    # Ensure the output directory exists
    output_dir = "output"
    os.makedirs(output_dir, exist_ok=True)

    # Step 1: Create a new blank document
    document = aw.Document()
    builder = aw.DocumentBuilder(document)

    # Step 2: Insert a rectangle shape of the desired size
    rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)

    # Step 3: Set the shape to be inline with the text flow
    rectangle_shape.wrap_type = aw.drawing.WrapType.INLINE

    # Step 4: Make the shadow visible and choose its color
    rectangle_shape.shadow.visible = True
    rectangle_shape.shadow.color = aw.drawing.Color.black

    # Step 5: Define the shadow's offset and blur to give it depth
    rectangle_shape.shadow.offset_x = 5   # horizontal offset in points
    rectangle_shape.shadow.offset_y = 5   # vertical offset in points
    rectangle_shape.shadow.blur = 3       # blur radius in points

    # Step 6: Choose an outer shadow style
    rectangle_shape.shadow.style = aw.drawing.ShadowStyle.OUTER

    # Step 7: Save the document with the shaped shadow
    output_path = os.path.join(output_dir, "ShapeWithShadow.docx")
    document.save(output_path)
    print(f"Document saved to {output_path}")

if __name__ == "__main__":
    main()
```

**Αναμενόμενο αποτέλεσμα**

Όταν ανοίξετε το `ShapeWithShadow.docx`, θα δείτε ένα μόνο ορθογώνιο κεντραρισμένο στη σελίδα. Το ορθογώνιο συνοδεύεται από μια διακριτική μαύρη σκιά μετατοπισμένη προς τα κάτω‑δεξιά, ελαφρώς θολή για να δημιουργήσει βάθος. Η σκιά σέβεται το εξωτερικό στυλ, έτσι δεν διασχίζει το εσωτερικό του ορθογωνίου.

## Συχνές ερωτήσεις και ειδικές περιπτώσεις

### Γιατί η σκιά μερικές φορές εμφανίζεται αόρατη;

Η σκιά αποδίδεται μόνο αν το `shadow.visible` είναι ορισμένο σε `True` **και** ο `wrap_type` του σχήματος το επιτρέπει. Ένα ενσωματωμένο σχήμα λειτουργεί αξιόπιστα· τα «πλωτά» σχήματα μπορεί να απαιτούν πρόσθετες ρυθμίσεις διάταξης.

### Πώς μπορώ να αλλάξω το χρώμα της σκιάς ώστε να ταιριάζει με την παλέτα της μάρκας;

Αντικαταστήστε το `aw.drawing.Color.black` με μια προσαρμοσμένη τιμή RGB:

```python
rectangle_shape.shadow.color = aw.drawing.Color.from_argb(255, 0, 120, 215)  # corporate blue
```

### Τι γίνεται αν θέλω το σχήμα να εμφανίζεται πίσω από το κείμενο;

Ορίστε τον τύπο περιτύλιξης σε `WrapType.BEHIND` και προσαρμόστε το `z_order_position` αν χρειάζεται. Λάβετε υπόψη ότι ορισμένοι προβολείς μπορεί να αποδίδουν διαφορετικά τα σχήματα πίσω από το κείμενο.

### Μπορώ να εφαρμόσω τις ίδιες ρυθμίσεις σκιάς σε πολλαπλά σχήματα;

Ναι. Δημιουργήστε μια βοηθητική συνάρτηση που διαμορφώνει τη σκιά και καλέστε την για κάθε σχήμα που εισάγετε. Αυτό προάγει την επαναχρησιμοποίηση κώδικα και εξασφαλίζει συνεπή μορφοποίηση.

```python
def apply_shadow(shape, color=aw.drawing.Color.black, offset=5, blur=3):
    shape.shadow.visible = True
    shape.shadow.color = color
    shape.shadow.offset_x = offset
    shape.shadow.offset_y = offset
    shape.shadow.blur = blur
    shape.shadow.style = aw.drawing.ShadowStyle.OUTER
```

## Συμπέρασμα

Τώρα ξέρετε **πώς να δημιουργήσετε έγγραφα** που περιέχουν ένα σχήμα ορθογωνίου με προσαρμοσμένη σκιά χρησιμοποιώντας το Aspose.Words for Python. Ο οδηγός κάλυψε την εισαγωγή ορθογωνίου, τη ρύθμιση του σχήματος ως inline, την ενεργοποίηση της σκιάς, τον καθορισμό του χρώματος, της απόστασης, του θολώματος και του στυλ, και τέλος την αποθήκευση του αρχείου.

Από εδώ μπορείτε να εξερευνήσετε σχετικούς τομείς όπως **add shadow to shape** για άλλα είδη σχημάτων, **set shadow color** δυναμικά βάσει δεδομένων, ή **how to add shadow** σε εικόνες και πλαίσια κειμένου. Πειραματιστείτε με διαφορετικές διαστάσεις, χρώματα και στυλ σκιάς ώστε να ταιριάζουν με τις οδηγίες της μάρκας ή του συστήματος σχεδίασής σας.

Έτοιμοι να αυτοματοποιήσετε περισσότερα έγγραφα Word; Δοκιμάστε την προσθήκη πινάκων, κεφαλίδων ή δυναμικού περιεχομένου — κάθε βήμα βασίζεται στις ίδιες αρχές που παρουσιάστηκαν εδώ. Καλή προγραμματιστική δουλειά!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικά παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να κατακτήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στην υλοποίηση των δικών σας έργων.

- [Create rectangle shape, add shadow & save PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [How to Manage Document Variables with Aspose.Words in Python&#58; A Complete Guide](/words/english/python-net/document-properties-metadata/aspose-words-python-manage-document-variables/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}