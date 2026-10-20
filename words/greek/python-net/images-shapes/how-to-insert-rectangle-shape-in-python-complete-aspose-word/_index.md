---
category: general
date: 2026-06-27
description: Μάθετε πώς να εισάγετε σχήμα ορθογωνίου στην Python χρησιμοποιώντας το
  Aspose.Words, να αλλάξετε το χρώμα της σκιάς, να προσθέσετε εξωτερική σκιά και να
  εφαρμόσετε εφέ σκιάς στο σχήμα—όλα σε ένα μόνο σεμινάριο.
draft: false
keywords:
- how to insert rectangle shape
- how to change shadow color
- how to add outer shadow
- apply shadow effect to shape
language: el
og_description: Μάθετε πώς να εισάγετε σχήμα ορθογωνίου στην Python, να αλλάξετε το
  χρώμα της σκιάς του, να προσθέσετε εξωτερική σκιά και να εφαρμόσετε εφέ σκιάς στο
  σχήμα με το Aspose.Words.
og_title: Πώς να εισάγετε σχήμα ορθογωνίου στην Python – Οδηγός Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Learn how to insert rectangle shape in Python using Aspose.Words, change
    shadow color, add outer shadow, and apply shadow effect to shape—all in one tutorial.
  headline: How to Insert Rectangle Shape in Python – Complete Aspose.Words Guide
  type: TechArticle
- description: Learn how to insert rectangle shape in Python using Aspose.Words, change
    shadow color, add outer shadow, and apply shadow effect to shape—all in one tutorial.
  name: How to Insert Rectangle Shape in Python – Complete Aspose.Words Guide
  steps:
  - name: Pro tip
    text: If you need the rectangle positioned at a specific location, use `builder.move_to`
      before inserting, or adjust `rectangle.left` and `rectangle.top` after creation.
  - name: Edge case
    text: If you forget to set `shadow.opacity`, the default is fully opaque, which
      can make the shadow look like a solid shape. Always pair a color change with
      an appropriate opacity level.
  - name: Common pitfalls
    text: '- **Missing directory:** `doc.save` will raise an error if the folder doesn’t
      exist. Create it first or use `os.makedirs`. - **Version mismatch:** The shadow
      API requires Aspose.Words 22.9+; older versions silently ignore shadow settings.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Document Automation
title: Πώς να εισάγετε σχήμα ορθογωνίου στην Python – Ο πλήρης οδηγός Aspose.Words
url: /el/python/images-shapes/how-to-insert-rectangle-shape-in-python-complete-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να Εισάγετε Σχήμα Ορθογωνίου σε Python – Πλήρης Οδηγός Aspose.Words

Έχετε αναρωτηθεί ποτέ **πώς να εισάγετε σχήμα ορθογωνίου** σε ένα έγγραφο Word χρησιμοποιώντας Python; Δεν είστε οι μόνοι—πολλοί προγραμματιστές αντιμετωπίζουν αυτό το πρόβλημα όταν αυτοματοποιούν αναφορές ή δημιουργούν πρότυπα. Τα καλά νέα είναι ότι το Aspose.Words το κάνει παιχνιδάκι, και σε αυτό το tutorial θα περάσουμε από όλη τη διαδικασία, από το σχεδιασμό του ορθογωνίου μέχρι την προσθήκη μιας κομψής εξωτερικής σκιάς.

Θα καλύψουμε επίσης **πώς να αλλάξετε το χρώμα της σκιάς**, **πώς να προσθέσετε εξωτερική σκιά**, και το τελικό βήμα **εφαρμογής εφέ σκιάς στο σχήμα**. Στο τέλος, θα έχετε ένα πλήρως μορφοποιημένο ορθογώνιο που μπορείτε να ενσωματώσετε σε οποιοδήποτε αρχείο .docx προγραμματιστικά.

## Προαπαιτούμενα

- Python 3.8+ εγκατεστημένο στο σύστημά σας  
- Aspose.Words for Python μέσω `pip install aspose-words`  
- Βασική εξοικείωση με scripting σε Python (δεν απαιτείται βαθιά γνώση του Word‑API)  

Αν έχετε ήδη όλα αυτά, τέλεια—ας ξεκινήσουμε. Αν όχι, κατεβάστε τη βιβλιοθήκη πρώτα· ο υπόλοιπος οδηγός υποθέτει ότι η εισαγωγή λειτουργεί χωρίς προβλήματα.

## Πώς να Εισάγετε Σχήμα Ορθογωνίου με Aspose.Words for Python

Το πρώτο βήμα είναι ακριβώς αυτό που υποσχέθηκε η κύρια λέξη‑κλειδί: **πώς να εισάγετε σχήμα ορθογωνίου**. Θα δημιουργήσουμε ένα νέο έγγραφο, θα δημιουργήσουμε ένα `DocumentBuilder`, και θα τοποθετήσουμε ένα ορθογώνιο στη σελίδα.

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Create a fresh document and a builder to add content
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# Insert a rectangle shape of 200x100 points
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# Optional: give the rectangle a light fill so the shadow is visible
rectangle.fill_color = aw.drawing.Color.light_blue
```

> **Γιατί είναι σημαντικό:** Η κλήση `insert_shape` είναι ο πυρήνας του *πώς να εισάγετε σχήμα ορθογωνίου*. Επιστρέφει ένα αντικείμενο `Shape` που μπορείτε αργότερα να επεξεργαστείτε—μέγεθος, θέση, γέμισμα, περιγράμματα, ό,τι θέλετε. Παρατηρήστε ότι ορίζουμε επίσης ένα `fill_color`; χωρίς αυτό η σκιά μπορεί να ενσωματωθεί σε λευκή σελίδα, καθιστώντας τη δύσκολη στην παρατήρηση.

### Συμβουλή επαγγελματία
Αν χρειάζεστε το ορθογώνιο σε συγκεκριμένη θέση, χρησιμοποιήστε `builder.move_to` πριν από την εισαγωγή, ή προσαρμόστε τα `rectangle.left` και `rectangle.top` μετά τη δημιουργία.

## Αλλαγή του Χρώματος της Σκιάς ενός Σχήματος

Τώρα που το ορθογώνιο βρίσκεται στο έγγραφο, ας απαντήσουμε στο **πώς να αλλάξετε το χρώμα της σκιάς**. Το Aspose.Words εκθέτει ένα αντικείμενο `ShadowEffect` όπου μπορείτε να ορίσετε την ιδιότητα `color` σε οποιαδήποτε τιμή RGB.

```python
# Create a shadow effect instance
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # we’ll also cover outer shadow later
shadow.blur_radius = 8.0                  # smooth edges
shadow.distance = 6.0                     # how far the shadow sits from the shape
shadow.direction = 45                     # angle in degrees
shadow.opacity = 0.6                      # semi‑transparent

# Change the shadow color to a deep gray instead of black
shadow.color = aw.drawing.Color.from_argb(255, 80, 80, 80)

# Apply the shadow to our rectangle
rectangle.shadow = shadow
```

> **Γιατί μπορεί να το θέλετε:** Μια σκοτεινή μαύρη σκιά μπορεί να είναι πολύ έντονη, ειδικά σε έγγραφα ανοιχτού χρώματος. Η ρύθμιση του χρώματος σας επιτρέπει να ταιριάξετε το εταιρικό branding ή απλώς να πετύχετε ένα πιο ήπιο οπτικό αποτέλεσμα.

### Ακραία περίπτωση
Αν ξεχάσετε να ορίσετε `shadow.opacity`, η προεπιλογή είναι πλήρως αδιαφανής, κάτι που μπορεί να κάνει τη σκιά να φαίνεται σαν στερεό σχήμα. Συνδυάστε πάντα την αλλαγή χρώματος με ένα κατάλληλο επίπεδο αδιαφάνειας.

## Προσθήκη Εξωτερικής Σκιάς

Η επόμενη ερώτηση που κάνουν πολλοί είναι **πώς να προσθέσετε εξωτερική σκιά**. Η σημαία `ShadowStyle.OUTER` λέει στο Aspose.Words να αποδώσει τη σκιά έξω από το περίγραμμα του σχήματος αντί για μέσα.

Το παραπάνω απόσπασμα κώδικα χρησιμοποιεί ήδη `ShadowStyle.OUTER`, αλλά ας το απομονώσουμε για σαφήνεια:

```python
# Ensure the shadow style is outer
shadow.style = ShadowStyle.OUTER
```

Αν αλλάξετε σε `ShadowStyle.INNER`, η σκιά θα εμφανιστεί *μέσα* στο ορθογώνιο, κάτι χρήσιμο για εφέ ανάγλυφου. Για τις περισσότερες περιπτώσεις σχεδιασμού εγγράφων, το εξωτερικό στυλ δίνει μια φυσική εμφάνιση «πτώσης» σκιάς.

## Εφαρμογή του Εφέ Σκιάς στο Σχήμα Σας

Έχουμε ήδη **εφαρμόσει εφέ σκιάς στο σχήμα** με την ανάθεση `rectangle.shadow = shadow`. Ας συνδυάσουμε όλα τα βήματα και να αποθηκεύσουμε το έγγραφο, επιβεβαιώνοντας ότι το εφέ παραμένει.

```python
# Save the document – choose a folder you have write access to
output_path = "output/RectangleWithShadow.docx"
doc.save(output_path)

print(f"Document saved to {output_path}. Open it to see the rectangle with its outer shadow.")
```

Όταν ανοίξετε το `RectangleWithShadow.docx` στο Microsoft Word, θα δείτε ένα ανοιχτό-μπλε ορθογώνιο με μια διακριτική γκρι εξωτερική σκιά που πέφτει υπό γωνία 45°. Η σκιά θα είναι ελαφρώς θολή και μετατοπισμένη, ακριβώς όπως τη ρυθμίσαμε.

### Συνηθισμένα λάθη
- **Λείπει ο φάκελος:** Το `doc.save` θα προκαλέσει σφάλμα αν ο φάκελος δεν υπάρχει. Δημιουργήστε τον πρώτα ή χρησιμοποιήστε `os.makedirs`.
- **Ασυμφωνία εκδόσεων:** Το API σκιάς απαιτεί Aspose.Words 22.9+· παλαιότερες εκδόσεις αγνοούν σιωπηλά τις ρυθμίσεις σκιάς.

## Πλήρες Παράδειγμα Λειτουργίας

Παρακάτω βρίσκεται το ολοκληρωμένο, έτοιμο‑για‑εκτέλεση script που συνδυάζει όλα τα βήματα. Αντιγράψτε‑και‑επικολλήστε το σε ένα αρχείο με όνομα `rectangle_shadow.py` και εκτελέστε το με `python rectangle_shadow.py`.

```python
import os
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Ensure output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1️⃣ Create a new document and builder
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# 2️⃣ Insert the rectangle shape (how to insert rectangle shape)
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
rectangle.fill_color = aw.drawing.Color.light_blue   # make the shape visible

# 3️⃣ Define the shadow (how to change shadow color, how to add outer shadow)
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # outer shadow
shadow.blur_radius = 8.0
shadow.distance = 6.0
shadow.direction = 45
shadow.opacity = 0.6
shadow.color = aw.drawing.Color.from_argb(255, 80, 80, 80)  # custom gray

# 4️⃣ Apply the shadow (apply shadow effect to shape)
rectangle.shadow = shadow

# 5️⃣ Save the file
output_path = os.path.join(output_dir, "RectangleWithShadow.docx")
doc.save(output_path)

print(f"✅ Document generated: {output_path}")
```

**Αναμενόμενο αποτέλεσμα:** Ένα έγγραφο Word (`RectangleWithShadow.docx`) που περιέχει ένα μόνο ορθογώνιο με γκρι εξωτερική σκιά. Ανοίξτε το στο Word για να επαληθεύσετε το οπτικό εφέ.

## Συχνές Ερωτήσεις

| Ερώτηση | Απάντηση |
|----------|--------|
| *Μπορώ να χρησιμοποιήσω διαφορετικό τύπο σχήματος;* | Φυσικά—αντικαταστήστε το `ShapeType.RECTANGLE` με `ShapeType.OVAL`, `ShapeType.TRIANGLE` κ.λπ., και η ίδια λογική σκιάς ισχύει. |
| *Τι γίνεται αν χρειάζομαι πιο παχύ περίγραμμα;* | Ορίστε `rectangle.line_width = 2.0` (points) πριν εφαρμόσετε τη σκιά. |
| *Μπορεί να γίνει animation της σκιάς;* | Δεν είναι δυνατόν άμεσα με το Aspose.Words· θα πρέπει να εξάγετε σε HTML/CSS για animation. |
| *Λειτουργεί αυτό σε macOS;* | Ναι—το Aspose.Words είναι ανεξάρτητο πλατφόρμας εφόσον τρέχει η Python. |

## Συμπέρασμα

Διασχίσαμε **πώς να εισάγετε σχήμα ορθογωνίου**, δείξαμε **πώς να αλλάξετε το χρώμα της σκιάς**, εξηγήσαμε **πώς να προσθέσετε εξωτερική σκιά**, και τελικά σας δείξαμε **πώς να εφαρμόσετε εφέ σκιάς στο σχήμα** χρησιμοποιώντας Aspose.Words for Python. Το πλήρες script είναι έτοιμο να ενσωματωθεί σε οποιοδήποτε pipeline αυτοματοποίησης, παρέχοντάς σας ένα επαγγελματικό ορθογώνιο με πολυτελή σκιά σε δευτερόλεπτα.

Έτοιμοι για το επόμενο βήμα; Δοκιμάστε να αλλάξετε το χρώμα γεμίσματος, πειραματιστείτε με διαφορετικές γωνίες `direction`, ή προσθέστε πολλαπλά σχήματα στην ίδια σελίδα. Μπορείτε επίσης να εξερευνήσετε το πλούσιο API μορφοποίησης κειμένου του Aspose.Words για να συνδυάσετε σκιές με στυλιζαρισμένο κείμενο—τέλειο για εντυπωσιακές αναφορές.

Αν βρήκατε αυτό το tutorial χρήσιμο, δώστε του ένα thumbs‑up, μοιραστείτε το με συναδέλφους, ή αφήστε ένα σχόλιο με τις δικές σας παραλλαγές. Καλή προγραμματιστική!

![Diagram showing how to insert rectangle shape with an outer shadow applied in a Word document](/images/rectangle-shadow.png)


## Τι Πρέπει να Μάθετε Στη Σύντομη Μελλοντική

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στην υλοποίηση των δικών σας έργων.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}