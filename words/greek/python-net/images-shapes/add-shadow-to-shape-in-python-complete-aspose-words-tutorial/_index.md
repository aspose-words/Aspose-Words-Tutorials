---
category: general
date: 2026-06-08
description: Προσθέστε σκιά σε σχήμα χρησιμοποιώντας το Aspose.Words για Python και
  ορίστε το χρώμα γεμίσματος του σχήματος σε λίγα μόνο βήματα. Μάθετε τη πλήρη διαδικασία
  με εκτελέσιμο κώδικα.
draft: false
keywords:
- add shadow to shape
- set shape fill color
- Aspose.Words Python shadow
- shape formatting Python
- PDF generation Aspose
language: el
og_description: Προσθέστε σκιά σε σχήμα με το Aspose.Words για Python και ορίστε άμεσα
  το χρώμα γεμίσματος του σχήματος. Ακολουθήστε αυτό το βήμα‑βήμα οδηγό για να δημιουργήσετε
  έξοδο PDF.
og_title: Προσθήκη σκιάς σε σχήμα σε Python – Πλήρης οδηγός Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-08'
  description: Add shadow to shape using Aspose.Words for Python and set shape fill
    color in just a few steps. Learn the full workflow with runnable code.
  headline: Add Shadow to Shape in Python – Complete Aspose.Words Tutorial
  type: TechArticle
- description: Add shadow to shape using Aspose.Words for Python and set shape fill
    color in just a few steps. Learn the full workflow with runnable code.
  name: Add Shadow to Shape in Python – Complete Aspose.Words Tutorial
  steps:
  - name: Create the Document and Builder
    text: '```python import aspose.words as aw from aspose.words.drawing import ShadowEffect,
      ShadowType, Color'
  - name: Insert a Rectangle Shape and Set Its Fill Color
    text: '```python # Insert a rectangle shape of width 200 points and height 100
      points. rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE,
      200, 100)'
  - name: Define the Shadow Effect
    text: '```python # Create a new shadow effect object. shape_shadow = ShadowEffect()
      shape_shadow.type = ShadowType.OUTER # outer shadow around the shape shape_shadow.blur_radius
      = 10.0 # softer edges shape_shadow.distance = 5.0 # how far the shadow sits
      from the shape shape_shadow.direction = 45 # angle in'
  - name: Apply the Shadow to the Shape
    text: '```python # Attach the shadow effect to the rectangle. rectangle_shape.shadow_effect
      = shape_shadow ```'
  - name: Save the Document as PDF
    text: '```python # Choose a folder you have write access to. output_path = "YOUR_DIRECTORY/ShadowShape.pdf"
      doc.save(output_path) print(f"Document saved to {output_path}") ```'
  type: HowTo
tags:
- Aspose.Words
- Python
- Document Automation
title: Προσθήκη σκιάς σε σχήμα με Python – Πλήρης οδηγός Aspose.Words
url: /el/python/images-shapes/add-shadow-to-shape-in-python-complete-aspose-words-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Προσθήκη Σκιάς σε Σχήμα σε Python – Πλήρης Οδηγός Aspose.Words

Έχετε αναρωτηθεί ποτέ πώς να **προσθέσετε σκιά σε σχήμα** όταν δημιουργείτε ένα έγγραφο με το Aspose.Words for Python; Δεν είστε μόνοι. Είτε δημιουργείτε ένα πρότυπο αναφοράς, ένα διαφημιστικό φυλλάδιο, είτε ένα τεχνικό διάγραμμα, μια διακριτική σκιά μπορεί να κάνει ένα ορθογώνιο να ξεχωρίζει και να φαίνεται πιο επαγγελματικό.  

Σε αυτόν τον οδηγό θα σας δείξουμε επίσης **πώς να ορίσετε το χρώμα γεμίσματος του σχήματος**, ώστε να έχετε ένα πλήρως μορφοποιημένο ορθογώνιο έτοιμο για εξαγωγή σε PDF. Η λύση είναι απλή, ο κώδικας είναι έτοιμος‑για‑εκτέλεση, και η λογική πίσω από κάθε γραμμή εξηγείται με απλά αγγλικά.

## Τι Καλύπτει Αυτός ο Οδηγός

- Αρχικοποίηση ενός εγγράφου Aspose.Words και του builder.  
- Εισαγωγή ενός ορθογωνίου σχήματος και **ορισμός του χρώματος γεμίσματος**.  
- Ορισμός και εφαρμογή ενός **εφέ σκιάς** σε αυτό το σχήμα.  
- Αποθήκευση του αποτελέσματος ως PDF.  
- Πλήρες, εκτελέσιμο παράδειγμα μαζί με συμβουλές για κοινά προβλήματα.

Στο τέλος του άρθρου θα μπορείτε να ενσωματώσετε ένα μορφοποιημένο ορθογώνιο σε οποιοδήποτε αρχείο Word ή PDF με μόνο μερικές γραμμές Python. Χωρίς εξωτερικά εργαλεία, χωρίς εικασίες.

> **Προαπαιτούμενα** – Χρειάζεστε Python 3.7+ και το πακέτο `aspose-words` (`pip install aspose-words`). Ένα IDE ή κειμενογράφο της επιλογής σας αρκεί· το Visual Studio Code λειτουργεί άψογα.

---

## Προσθήκη Σκιάς σε Σχήμα – Βήμα‑βήμα

Παρακάτω χωρίζουμε τη διαδικασία σε λογικά τμήματα. Κάθε βήμα περιλαμβάνει τον ακριβή κώδικα που χρειάζεστε, μια σύντομη εξήγηση του *γιατί* είναι σημαντικό, και μια γρήγορη συμβουλή για να μην αντιμετωπίσετε προβλήματα αργότερα.

### Βήμα 1: Δημιουργία του Εγγράφου και του Builder

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowType, Color

# Create a new, empty document.
doc = aw.Document()

# DocumentBuilder gives us a convenient way to add content.
builder = aw.DocumentBuilder(doc)
```

**Γιατί είναι σημαντικό:** `Document` είναι το δοχείο για τα πάντα—σελίδες, στυλ, εικόνες και σχήματα. Το `DocumentBuilder` είναι το υψηλού επιπέδου API που μας επιτρέπει να τοποθετούμε αντικείμενα χωρίς να ανησυχούμε για τα χαμηλού επιπέδου δέντρα κόμβων.

### Βήμα 2: Εισαγωγή Ορθογώνιου Σχήματος και Ορισμός του Χρώματος Γεμίσματος

```python
# Insert a rectangle shape of width 200 points and height 100 points.
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# Set the interior color of the shape.
rectangle_shape.fill_color = Color.BLUE   # <-- set shape fill color
```

**Γιατί είναι σημαντικό:** Το σχήμα λειτουργεί ως καμβάς για τη σκιά μας. Με το **ορισμό του χρώματος γεμίσματος του σχήματος** διασφαλίζουμε ότι το ορθογώνιο δεν είναι απλώς ένα διαφανές κουτί· γίνεται ένα ορατό στοιχείο που η σκιά μπορεί να τονίσει. Μπορείτε να αντικαταστήσετε το `Color.BLUE` με οποιαδήποτε τιμή RGB ή ακόμη και με ένα gradient αν χρειάζεστε περισσότερη έμφαση.

> **Συμβουλή:** Αν σκοπεύετε να χρησιμοποιήσετε το ίδιο χρώμα σε πολλά σχήματα, αποθηκεύστε το σε μια μεταβλητή (`my_fill = Color.from_argb(0, 120, 200, 255)`) και επαναχρησιμοποιήστε αυτήν την αναφορά.

### Βήμα 3: Ορισμός του Εφέ Σκιάς

```python
# Create a new shadow effect object.
shape_shadow = ShadowEffect()
shape_shadow.type = ShadowType.OUTER          # outer shadow around the shape
shape_shadow.blur_radius = 10.0               # softer edges
shape_shadow.distance = 5.0                   # how far the shadow sits from the shape
shape_shadow.direction = 45                   # angle in degrees (45° = diagonal)
shape_shadow.color = Color.from_argb(128, 0, 0, 0)  # semi‑transparent black
```

**Γιατί είναι σημαντικό:** Η σκιά δεν είναι μόνο ένα οπτικό κόλπο· μεταδίδει βάθος και ιεραρχία. Το `blur_radius` ελέγχει τη μαλακότητα, το `distance` καθορίζει την απόσταση, και το `direction` σας επιτρέπει να προσομοιώσετε μια πηγή φωτός. Ρυθμίστε αυτές τις τιμές ώστε να ταιριάζουν με τη γλώσσα σχεδίασής σας.

### Βήμα 4: Εφαρμογή της Σκιάς στο Σχήμα

```python
# Attach the shadow effect to the rectangle.
rectangle_shape.shadow_effect = shape_shadow
```

**Γιατί είναι σημαντικό:** Μέχρι να εκτελεστεί αυτή η γραμμή, το σχήμα παραμένει επίπεδο. Η ανάθεση του `shadow_effect` λέει στο Aspose.Words να αποδώσει το ορθογώνιο με τη καθορισμένη σκιά όταν αποθηκευτεί το έγγραφο.

### Βήμα 5: Αποθήκευση του Εγγράφου ως PDF

```python
# Choose a folder you have write access to.
output_path = "YOUR_DIRECTORY/ShadowShape.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

**Γιατί είναι σημαντικό:** Η αποθήκευση ως PDF κλειδώνει το οπτικό στυλ, κάνοντας τη σκιά να εμφανίζεται ακριβώς όπως τη σχεδιάσατε. Μπορείτε επίσης να αποθηκεύσετε ως `.docx` αν χρειάζεστε περαιτέρω επεξεργασία αργότερα—το Aspose.Words διαχειρίζεται και τις δύο μορφές άψογα.

---

## Ορισμός Χρώματος Γεμίσματος Σχήματος – Προσαρμογή Εμφάνισης

Αν χρειάζεστε διαφορετική απόχρωση, αντικαταστήστε την ανάθεση `Color.BLUE` με οποιοδήποτε από τα παρακάτω παραδείγματα:

```python
# Solid RGB color
rectangle_shape.fill_color = Color.from_argb(255, 255, 165, 0)   # orange

# Semi‑transparent fill
rectangle_shape.fill_color = Color.from_argb(128, 0, 128, 0)    # 50% transparent green
```

> **Γιατί μπορεί να το θέλετε:** Ένα ημιδιαφανές γέμισμα σε συνδυασμό με σκιά μπορεί να δημιουργήσει ένα εφέ “γυαλιού” που είναι δημοφιλές σε σύγχρονα mock‑ups UI.

---

## Πλήρες Παράδειγμα Λειτουργίας

Ακολουθεί ολόκληρο το script σε ένα μπλοκ. Αντιγράψτε‑και‑επικολλήστε το σε ένα αρχείο με όνομα `shadow_shape.py` και εκτελέστε το—υποθέτοντας ότι έχετε εγκαταστήσει το `aspose-words`.

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowType, Color

# 1️⃣ Create document and builder
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# 2️⃣ Insert rectangle and set fill color
rect = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
rect.fill_color = Color.BLUE          # set shape fill color

# 3️⃣ Configure shadow
shadow = ShadowEffect()
shadow.type = ShadowType.OUTER
shadow.blur_radius = 10.0
shadow.distance = 5.0
shadow.direction = 45
shadow.color = Color.from_argb(128, 0, 0, 0)

# 4️⃣ Apply shadow
rect.shadow_effect = shadow

# 5️⃣ Save as PDF
output = "ShadowShape.pdf"
doc.save(output)
print(f"✅ PDF generated: {output}")
```

**Αναμενόμενο αποτέλεσμα:** Ανοίξτε το `ShadowShape.pdf` και θα δείτε ένα μπλε ορθογώνιο με μια ήπια, διαγώνια μαύρη σκιά μετατοπισμένη προς το κάτω‑δεξιά. Η σκιά θα πρέπει να φαίνεται ελαφρώς θολή, δίνοντας στο σχήμα μια ανυψωμένη εμφάνιση.

---

## Συνηθισμένα Προβλήματα & Συμβουλές

| Πρόβλημα | Γιατί συμβαίνει | Διόρθωση |
|------|----------------|-----|
| **Σκιά δεν εμφανίζεται** | Το γέμισμα του σχήματος είναι πλήρως διαφανές ή ο προβολέας PDF απενεργοποιεί τις σκιές. | Βεβαιωθείτε ότι το `fill_color` είναι αδιαφανές (`alpha = 255`) ή προσαρμόστε τη διαφάνεια του `color` της σκιάς. |
| **Σφάλμα διαδρομής αρχείου** | `YOUR_DIRECTORY` δεν υπάρχει ή δεν έχετε δικαίωμα εγγραφής. | Χρησιμοποιήστε `os.makedirs("YOUR_DIRECTORY", exist_ok=True)` πριν από το `doc.save`. |
| **Λανθασμένη εισαγωγή** | Προσπάθεια εισαγωγής του `ShadowEffect` από το λάθος υπο‑module. | Εισάγετε ακριβώς όπως φαίνεται: `from aspose.words.drawing import ShadowEffect, ShadowType, Color`. |
| **Απρόσμενο χρώμα** | Χρήση του `Color.from_argb` με λανθασμένη σειρά (alpha, red, green, blue). | Θυμηθείτε τη σειρά: **alpha**, **red**, **green**, **blue**. |

---

## Επόμενα Βήματα – Επέκταση του Εργαλειοθήκης Σχημάτων

Τώρα που ξέρετε πώς να **προσθέσετε σκιά σε σχήμα** και **ορίσετε το χρώμα γεμίσματος του σχήματος**, μπορείτε να εξερευνήσετε:

- **Γεμίσματα gradient** (`LinearGradientBrush`) για πιο πλούσια φόντα.  
- **Πολλαπλές σκιές** (εσωτερική + εξωτερική) συνδέοντας αντικείμενα `ShadowEffect`.  
- **Άλλοι τύποι σχημάτων** (`Ellipse`, `Polygon`) για δημιουργία εικονιδίων ή στοιχείων διαγράμματος ροής.  
- **Ενσωμάτωση του PDF** σε απάντηση web ή συνημμένο email χρησιμοποιώντας Flask ή Django.

Κάθε ένα από αυτά τα θέματα βασίζεται στις ίδιες βασικές έννοιες που καλύφθηκαν εδώ, οπότε θα νιώσετε άνετα.

---

## Συμπέρασμα

Διασχίσαμε τη πλήρη διαδικασία **προσθήκης σκιάς σε σχήμα** στο Aspose.Words for Python ενώ επίσης **ορίσαμε το χρώμα γεμίσματος του σχήματος**. Από τη δημιουργία του εγγράφου μέχρι την εξαγωγή σε PDF, ο κώδικας είναι αυτόνομος και έτοιμος για παραγωγική χρήση.  

Μη διστάσετε να προσαρμόσετε το `blur_radius`, την απόσταση ή το χρώμα ώστε να ταιριάζει με τις οδηγίες της μάρκας σας. Αν αντιμετωπίσετε μια σπάνια περίπτωση ή έχετε αίτημα για νέα λειτουργία, αφήστε ένα σχόλιο παρακάτω—καλή προγραμματιστική!

## Τι Θα Πρέπει Να Μάθετε Στη Σειρά;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που βασίζονται στις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε σε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Ρύθμιση Άδειας Aspose.Words σε Python](/words/english/python-net/getting-started/aspose-words-license-python-setup/)
- [Δημιουργία ορθογώνιου σχήματος σε Word με Aspose.Words – Οδηγός βήμα‑βήμα](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Οδηγός Σκιάς Σχήματος Aspose.Words – Προσθήκη Σκιάς σε Σχήμα Word σε C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}