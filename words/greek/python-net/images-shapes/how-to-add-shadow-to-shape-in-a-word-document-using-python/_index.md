---
category: general
date: 2026-11-25
description: Προσθέστε σκιά σε σχήμα σε έγγραφο Word με Python. Μάθετε πώς να εισάγετε
  σχήμα ορθογωνίου στο Word και να εφαρμόσετε διαφανή σκιά χρησιμοποιώντας το Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shadow to shape
- insert rectangle shape word
- how to create word document python
- Aspose.Words Python
- shape formatting Python
language: el
lastmod: 2026-11-25
og_description: Προσθέστε σκιά σε σχήμα σε έγγραφο Word χρησιμοποιώντας Python. Αυτό
  το σεμινάριο δείχνει πώς να εισάγετε ένα σχήμα ορθογωνίου στο Word και να ορίσετε
  μια σκιά με διαφάνεια 30 % χρησιμοποιώντας το Aspose.Words.
og_image_alt: Add shadow to shape example in a Word document created by Python
og_title: Προσθήκη σκιάς σε σχήμα σε έγγραφο Word με Python – βήμα‑βήμα οδηγός
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Add shadow to shape in a Word document with Python. Learn how to insert
    rectangle shape in Word and apply a transparent shadow using Aspose.Words.
  headline: How to add shadow to shape in a Word document using Python
  type: TechArticle
tags:
- Python
- Aspose.Words
- Word automation
title: Πώς να προσθέσετε σκιά σε σχήμα σε έγγραφο Word χρησιμοποιώντας Python
url: /el/python/images-shapes/how-to-add-shadow-to-shape-in-a-word-document-using-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να προσθέσετε σκιά σε σχήμα σε έγγραφο Word χρησιμοποιώντας Python

Εάν χρειάζεται να **προσθέσετε σκιά σε σχήμα** σε έγγραφο Word, αυτός ο οδηγός σας παρουσιάζει μια πλήρη, εκτελέσιμη λύση. Θα δείτε πώς να δημιουργήσετε ένα αρχείο Word, να εισάγετε ένα σχήμα ορθογωνίου και να εφαρμόσετε σκιά με διαφάνεια 30 % — όλα με τη βιβλιοθήκη Aspose.Words for Python.

Η προγραμματιστική εργασία με έγγραφα Word σας εξοικονομεί τον χειροκίνητο μορφοποίηση και σας επιτρέπει να δημιουργείτε αναφορές, συμβόλαια ή διαφημιστικά φυλλάδια σε κλίμακα. Στο τέλος αυτού του tutorial θα μπορείτε να απαντήσετε στο ερώτημα “**πώς να δημιουργήσετε έγγραφο Word με Python**” με ένα έτοιμο παράδειγμα κώδικα.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

* Python 3.8 ή νεότερο εγκατεστημένο.
* Ένα ενεργό license του Aspose.Words for Python (η δωρεάν δοκιμή λειτουργεί για αξιολόγηση).
* Το πακέτο `aspose-words` εγκατεστημένο μέσω `pip install aspose-words`.
* Έναν φάκελο όπου μπορεί να γραφτεί το αρχείο εξόδου (αντικαταστήστε το `YOUR_DIRECTORY` στον κώδικα).

Δεν απαιτούνται πρόσθετες εξαρτήσεις.

## Βήμα 1: Δημιουργία νέου εγγράφου Word

Το πρώτο βήμα είναι η δημιουργία ενός αντικειμένου `Document`. Αυτό το αντικείμενο αντιπροσωπεύει ολόκληρο το αρχείο .docx στη μνήμη.

```python
import aspose.words as aw

# Create an empty Word document
doc = aw.Document()
# DocumentBuilder provides a convenient API for adding content
builder = aw.DocumentBuilder(doc)
```

Το `DocumentBuilder` λειτουργεί σαν εικονικός κέρσορας. Όταν καλείτε τις μεθόδους του, η βιβλιοθήκη εισάγει τα αντίστοιχα στοιχεία στη τρέχουσα θέση του κέρσορα.

## Βήμα 2: Εισαγωγή σχήματος ορθογωνίου

Στη συνέχεια **εισάγετε σχήμα ορθογωνίου** χρησιμοποιώντας τη μέθοδο `insert_shape` του builder. Η μέθοδος απαιτεί τον τύπο του σχήματος και το μέγεθός του σε points (1 point = 1/72 ίντσα).

```python
# Insert a rectangle shape that is 100 points wide and 50 points tall
shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 100, 50)
```

Μπορείτε να αλλάξετε τις διαστάσεις ώστε να ταιριάζουν με το σχέδιό σας. Το ορθογώνιο γίνεται μέρος της στρώσης σχεδίασης του εγγράφου, πράγμα που σημαίνει ότι μπορείτε αργότερα να τροποποιήσετε το γέμισμα, το περίγραμμα ή τη σκιά του.

## Βήμα 3: Πρόσβαση στη μορφή σκιάς του σχήματος

Κάθε αντικείμενο σχεδίασης εκθέτει μια ιδιότητα `shadow_format` που ελέγχει την εμφάνιση της σκιάς. Ανακτήστε την ώστε να μπορείτε να ρυθμίσετε τη διαφάνεια, την απόσταση, το θόλωμα και το χρώμα.

```python
# Get the ShadowFormat object for the rectangle
shadow = shape.shadow_format
```

Σε αυτό το σημείο το σχήμα έχει την προεπιλεγμένη σκιά (χωρίς σκιά). Το αντικείμενο `ShadowFormat` περιέχει όλες τις παραμέτρους που χρειάζεστε για να δημιουργήσετε ένα ρεαλιστικό εφέ.

## Βήμα 4: Κάντε τη σκιά 30 % διαφανή

Η διαφάνεια εκφράζεται ως τιμή μεταξύ `0` (πλήρως αδιαφανής) και `1` (πλήρως διαφανής). Ορίζοντάς την σε `0.3` λαμβάνετε σκιά 30 % διαφανή, που συνήθως είναι αρκετή για να προσθέσει βάθος χωρίς να υπερκαλύπτει το κείμενο.

```python
# Apply a 30 % transparent shadow
shadow.transparency = 0.3
# Optional: adjust other shadow properties for a nicer look
shadow.visible = True               # Ensure the shadow is turned on
shadow.distance = 4                 # Distance of the shadow from the shape (points)
shadow.blur = 4                     # Amount of blur applied to the shadow
shadow.color = aw.Color.black       # Shadow color
```

Αυτές οι πρόσθετες ιδιότητες δεν είναι απαραίτητες, αλλά δείχνουν πώς μπορείτε να ρυθμίσετε λεπτομερώς το εφέ. Η σημαία `visible` είναι κρίσιμη· αν τη ξεχάσετε, η σκιά δεν θα εμφανιστεί παρόλο που οι άλλες ρυθμίσεις είναι ενεργές.

## Βήμα 5: Αποθήκευση του εγγράφου για προβολή του αποτελέσματος

Τέλος, γράψτε το έγγραφο στο δίσκο. Ανοίγοντας το παραγόμενο αρχείο `.docx` στο Microsoft Word ή σε οποιονδήποτε συμβατό προβολέα, θα δείτε το ορθογώνιο με την διαφανή σκιά που εφαρμόστηκε.

```python
# Save the document to the desired location
output_path = r"YOUR_DIRECTORY/output.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Όταν ανοίξετε το `output.docx`, θα δείτε ένα απλό ορθογώνιο με μια ήπια γκρι σκιά μετατοπισμένη προς τα κάτω‑δεξιά. Η διαφάνεια 30 % της σκιάς κάνει το σχήμα να φαίνεται ανυψωμένο από τη σελίδα.

![Add shadow to shape example](placeholder-image.png){: .align-center alt="Παράδειγμα προσθήκης σκιάς σε σχήμα σε έγγραφο Word που δημιουργήθηκε με Python"}

## Πλήρες, εκτελέσιμο σενάριο

Συνδυάζοντας όλα τα κομμάτια παίρνετε ένα αυτόνομο σενάριο που μπορείτε να αντιγράψετε, επικολλήσετε και τρέξετε αμέσως.

```python
import aspose.words as aw

def create_word_with_shadow(output_path: str):
    """
    Creates a Word document that contains a rectangle shape
    with a 30 % transparent shadow.
    """
    # Step 1: Initialize document and builder
    doc = aw.Document()
    builder = aw.DocumentBuilder(doc)

    # Step 2: Insert rectangle shape
    shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 100, 50)

    # Step 3: Access shadow format
    shadow = shape.shadow_format

    # Step 4: Configure shadow properties
    shadow.visible = True
    shadow.transparency = 0.3
    shadow.distance = 4
    shadow.blur = 4
    shadow.color = aw.Color.black

    # Step 5: Save the document
    doc.save(output_path)
    print(f"Document saved to {output_path}")

if __name__ == "__main__":
    # Replace with a valid folder on your machine
    create_word_with_shadow(r"YOUR_DIRECTORY/output.docx")
```

**Αναμενόμενο αποτέλεσμα:** Το άνοιγμα του παραγόμενου `output.docx` εμφανίζει μία σελίδα με ένα ορθογώνιο που ρίχνει μια ελαφριά, ημιδιαφανή σκιά. Δεν απαιτείται πρόσθετη μορφοποίηση.

## Συνηθισμένες παραλλαγές και ειδικές περιπτώσεις

| Κατάσταση | Πώς να προσαρμόσετε τον κώδικα |
|-----------|-------------------------------|
| **Διαφορετικός τύπος σχήματος** (π.χ., έλλειψη) | Αλλάξτε `aw.drawing.ShapeType.RECTANGLE` σε `aw.drawing.ShapeType.ELLIPSE`. |
| **Προσαρμοσμένο χρώμα σκιάς** | Ορίστε `shadow.color = aw.Color.from_argb(255, 128, 0, 0)` για μια κοκκινωπή σκιά. |
| **Πολλαπλά σχήματα** | Καλέστε `builder.insert_shape` επανειλημμένα· κάθε κλήση επιστρέφει ένα ξεχωριστό αντικείμενο `Shape` που μπορείτε να μορφοποιήσετε ανεξάρτητα. |
| **Αποθήκευση ως PDF** | Αντικαταστήστε `doc.save(output_path)` με `doc.save(output_path.replace('.docx', '.pdf'))` και χρησιμοποιήστε την επέκταση `.pdf`. |
| **Εκτέλεση χωρίς άδεια** | Η δωρεάν δοκιμή προσθέτει υδατογράφημα στην πρώτη σελίδα. Αποκτήστε άδεια για να το αφαιρέσετε σε παραγωγική χρήση. |

Αυτές οι παραλλαγές δείχνουν ότι το ίδιο μοτίβο — δημιουργία εγγράφου, εισαγωγή σχήματος, ρύθμιση `shadow_format`, αποθήκευση — καλύπτει τις περισσότερες περιπτώσεις αυτοματοποίησης.

## Συμβουλές και βέλτιστες πρακτικές

* **Επαναχρησιμοποίηση του builder**: Διατηρήστε ένα μόνο αντικείμενο `DocumentBuilder` για ολόκληρο το έγγραφο ώστε να αποφύγετε περιττές δημιουργίες αντικειμένων.
* **Απελευθέρωση πόρων**: Σε υπηρεσίες μακράς διάρκειας, καλέστε `doc.dispose()` μετά την αποθήκευση για να ελευθερώσετε τη φυσική μνήμη.
* **Επαλήθευση εξόδου**: Χρησιμοποιήστε `doc.validate(aw.ValidationType.FULL_VALIDATION)` πριν την αποθήκευση εάν χρειάζεται να διασφαλίσετε τη συμμόρφωση με το πρότυπο Open XML.
* **Συμβατότητα εκδόσεων**: Ο κώδικας λειτουργεί με Aspose.Words for Python ≥ 22.9. Βεβαιωθείτε ότι το πακέτο σας είναι ενημερωμένο με `pip install --upgrade aspose-words`.

## Συμπέρασμα

Τώρα ξέρετε πώς να **προσθέσετε σκιά σε σχήμα** σε έγγραφο Word χρησιμοποιώντας Python. Ακολουθώντας τα πέντε βήματα — δημιουργία εγγράφου, **εισαγωγή σχήματος ορθογωνίου**, ρύθμιση της σκιάς και αποθήκευση — μπορείτε να αυτοματοποιήσετε την παραγωγή επαγγελματικών εγγράφων για αναφορές, τιμολόγια ή υλικά μάρκετινγκ.  

Από εδώ μπορείτε να εξερευνήσετε άλλες επιλογές μορφοποίησης όπως γεμίσματα διαβάθμισης, περιτύλιξη κειμένου ή μετατροπή του εγγράφου σε PDF. Κάθε ένα από αυτά τα θέματα βασίζεται στις ίδιες έννοιες `DocumentBuilder` και μορφοποίησης σχήματος που παρουσιάστηκαν σε αυτό το tutorial.

Καλή προγραμματιστική εργασία και απολαύστε το οπτικό βάθος που προσφέρει μια απλή σκιά στα αυτοματοποιημένα έγγραφα Word σας!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε πρόσθετες λειτουργίες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στην υλοποίηση των δικών σας έργων.

- [How to create rectangle shape in a Word document using Python](/words/english/python-net/images-shapes/how-to-create-rectangle-shape-in-a-word-document-using-pytho/)
- [Add Shadow to Shape in Python – Complete Aspose.Words Tutorial](/words/english/python-net/images-shapes/add-shadow-to-shape-in-python-complete-aspose-words-tutorial/)
- [Create Blank Word Document and Add Shadow to Shape – Full Python Guide](/words/english/python-net/images-shapes/create-blank-word-document-and-add-shadow-to-shape-full-pyth/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}