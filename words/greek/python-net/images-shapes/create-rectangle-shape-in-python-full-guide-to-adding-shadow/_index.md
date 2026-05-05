---
category: general
date: 2026-05-04
description: Μάθετε πώς να δημιουργήσετε σχήμα ορθογώνιου, πώς να προσθέσετε σχήμα
  με σκιές, να αλλάξετε το χρώμα της σκιάς, να ορίσετε την απόσταση της σκιάς και
  να αποθηκεύσετε το έγγραφο ως PDF χρησιμοποιώντας το Aspose.Words για Python.
draft: false
keywords:
- create rectangle shape
- how to add shape
- change shadow color
- save document as pdf
- set shadow distance
language: el
og_description: Δημιουργήστε σχήμα ορθογωνίου με το Aspose.Words για Python, μάθετε
  πώς να προσθέτετε σχήμα, να αλλάζετε το χρώμα της σκιάς, να ορίζετε την απόσταση
  της σκιάς και να αποθηκεύετε το έγγραφο ως PDF.
og_title: Δημιουργήστε σχήμα ορθογωνίου – Προσθέστε σκιά, Αλλάξτε το χρώμα & Αποθηκεύστε
  ως PDF
tags:
- Aspose.Words
- Python
- PDF generation
title: Δημιουργία σχήματος ορθογωνίου σε Python – Πλήρης οδηγός για την προσθήκη σκιών
  & αποθήκευση ως PDF
url: /el/python/images-shapes/create-rectangle-shape-in-python-full-guide-to-adding-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία σχήματος ορθογωνίου – Πλήρης Εκπαιδευτικό Υλικό για Προγραμματιστές Python

Έχετε ποτέ χρειαστεί να **create rectangle shape** σε ένα έγγραφο Word και να αναρωτηθείτε πώς να του προσθέσετε μια επαγγελματική σκιά; Ίσως δημιουργείτε έναν γεννήτορα αναφορών και η οπτική ποιότητα έχει σημασία—ιδιαίτερα όταν το τελικό αποτέλεσμα είναι PDF. Τα καλά νέα; Με το Aspose.Words for Python μπορείτε όχι μόνο να **how to add shape**, αλλά και να ρυθμίσετε κάθε ιδιότητα της σκιάς, από το χρώμα μέχρι την απόσταση, και στη συνέχεια να **save document as pdf** σε μια ομαλή ροή.

Σε αυτόν τον οδηγό θα περάσουμε από όλη τη διαδικασία βήμα‑βήμα. Θα δείτε τον ακριβή κώδικα που μπορείτε να αντιγράψετε‑και‑επικολλήσετε, θα καταλάβετε *γιατί* κάθε γραμμή είναι σημαντική, και θα αποκτήσετε μερικές συμβουλές για τη διαχείριση ειδικών περιπτώσεων (όπως διαφανείς σκιές ή μη‑τυπικό DPI). Στο τέλος θα μπορείτε να **create rectangle shape**, να προσαρμόσετε τη σκιά της και να εξάγετε ένα καθαρό PDF χωρίς κόπο.

## Προαπαιτούμενα

- Python 3.8+ εγκατεστημένο στον υπολογιστή σας.  
- Aspose.Words for Python μέσω `pip install aspose-words`.  
- Βασική εξοικείωση με αντικειμενοστραφή Python (τίποτα περίπλοκο).  

Αν έχετε ήδη ρυθμίσει ένα εικονικό περιβάλλον, απλώς εκτελέστε την εντολή εγκατάστασης και είστε έτοιμοι.

## Βήμα 1: Αρχικοποίηση του Εγγράφου και του Builder

Πριν μπορέσετε να **how to add shape**, χρειάζεστε ένα κενό έγγραφο για εργασία. Η κλάση `Document` αντιπροσωπεύει ολόκληρο το αρχείο, και το `DocumentBuilder` είναι το πινέλο σας.

```python
import aspose.words as aw

# Step 1: Create a new document and a DocumentBuilder to edit it
document = aw.Document()
builder = aw.DocumentBuilder(document)
```

*Γιατί είναι σημαντικό:* `Document` περιέχει όλα τα τμήματα, τις σελίδες και τους πόρους. `DocumentBuilder` σας παρέχει ένα ευέλικτο API για την εισαγωγή περιεχομένου ακριβώς εκεί που το χρειάζεστε—σκεφτείτε το ως κέρσορα σε έναν επεξεργαστή κειμένου.

## Βήμα 2: Εισαγωγή του Σχήματος Ορθογωνίου

Τώρα πραγματικά **how to add shape**. Η μέθοδος `insert_shape` χρειάζεται τον τύπο του σχήματος και τις διαστάσεις του (σε points). Εδώ επιλέγουμε ένα ορθογώνιο 200 × 100 pt και του δίνουμε γέμισμα ανοιχτό‑μπλε.

```python
# Step 2: Insert a rectangle shape and give it a light‑blue fill
rectangle_shape = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,  # shape type
    200,                            # width in points
    100)                            # height in points
rectangle_shape.fill_color = aw.Color.light_blue
```

*Συμβουλή:* Αν χρειάζεται το σχήμα να ευθυγραμμιστεί με υπάρχον κείμενο, χρησιμοποιήστε `builder.move_to` πριν την εισαγωγή, ή προσαρμόστε τις ιδιότητες `left`/`top` μετά τη δημιουργία.

## Βήμα 3: Ενεργοποίηση της Σκιάς

Ένα σχήμα χωρίς σκιά φαίνεται επίπεδο. Για να **set shadow distance** και να κάνετε το εφέ ορατό, αποκτήστε το shadow format και ενεργοποιήστε το.

```python
# Step 3: Access the shape's shadow format and make the shadow visible
rectangle_shadow = rectangle_shape.shadow_format
rectangle_shadow.visible = True
```

*Γιατί αυτό το βήμα:* Το shadow format είναι ξεχωριστό αντικείμενο· η εναλλαγή του `visible` είναι το πρώτο που πρέπει να κάνετε, διαφορετικά όλες οι άλλες ιδιότητες της σκιάς αγνοούνται.

## Βήμα 4: Στυλ της Σκιάς – Χρώμα, Θολό, Απόσταση, Κατεύθυνση

Εδώ συμβαίνει η μαγεία. Θα **change shadow color**, προσαρμόσουμε την ακτίνα θολώματος, ορίσουμε πόσο μακριά βρίσκεται η σκιά από το ορθογώνιο, και την περιστρέψουμε 45°.

```python
# Step 4: Configure the appearance of the shadow
rectangle_shadow.style = aw.drawing.ShadowStyle.OUTER   # outer shadow
rectangle_shadow.blur_radius = 10.0                    # blur amount (pixels)
rectangle_shadow.distance = 5.0                        # distance from the shape
rectangle_shadow.direction = 45.0                     # angle in degrees
rectangle_shadow.color = aw.Color.gray                 # shadow colour
```

*Επεξήγηση κάθε ιδιότητας:*

| Ιδιότητα | Τι κάνει | Τυπικές τιμές |
|----------|----------|----------------|
| `style` | Καθορίζει αν η σκιά είναι *inner* ή *outer*. | `OUTER` (most common) |
| `blur_radius` | Ελέγχει τη μαλακότητα· υψηλότερη τιμή = πιο θολές άκρες. | 0–20 px is usual |
| `distance` | Πόσο μακριά είναι η σκιά από το σχήμα. | 0–10 pt for subtle, >10 for dramatic |
| `direction` | Γωνία της πηγής φωτός, μετρημένη δεξιόστροφα από τον άξονα x. | 0‑360° |
| `color` | Τόνος της σκιάς. | Any `aw.Color` (e.g., `gray`, `dark_red`) |

*Περίπτωση άκρης:* Αν ορίσετε `distance` σε `0` η σκιά θα βρίσκεται ακριβώς κάτω από το σχήμα, κρύβοντας ουσιαστικά το γέμισμα του σχήματος. Κρατήστε το πάνω από `0` για ορατό offset.

## Βήμα 5: Αποθήκευση του Εγγράφου ως PDF

Τέλος, κάνουμε **save document as pdf**. Το Aspose.Words ραστεροποιεί αυτόματα τη σκιά, έτσι το PDF φαίνεται ακριβώς όπως η προβολή Word.

```python
# Step 5: Save the document as a PDF with the shadowed shape
output_path = "YOUR_DIRECTORY/ShadowedShape.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

*Γιατί PDF;* Τα PDF διατηρούν τη διάταξη σε όλες τις πλατφόρμες, καθιστώντας τα ιδανικά για αναφορές, τιμολόγια ή οποιοδήποτε εκτυπώσιμο αντικείμενο.

---

![Create rectangle shape with shadow](https://example.com/images/rectangle-shadow.png){: .align-center alt="παράδειγμα δημιουργίας σχήματος ορθογωνίου με σκιά"}

*Η παραπάνω εικόνα δείχνει το τελικό αποτέλεσμα PDF – ένα ανοιχτό‑μπλε ορθογώνιο με μια ήπια γκρι εξωτερική σκιά, ακριβώς όπως το ρυθμίσαμε.*

## Συχνές Ερωτήσεις & Παραλλαγές

### Τι γίνεται αν χρειάζομαι **transparent** σκιά;

Ορίστε το κανάλι άλφα στο χρώμα της σκιάς:

```python
transparent_gray = aw.Color.from_argb(128, 0, 0, 0)  # 50% opacity black
rectangle_shadow.color = transparent_gray
```

### Μπορώ να εφαρμόσω την ίδια σκιά σε πολλαπλά σχήματα;

Ναι. Εξάγετε το `ShadowFormat` από ένα σχήμα και αντιστοιχίστε το σε ένα άλλο:

```python
another_shape = builder.insert_shape(aw.drawing.ShapeType.ELLIPSE, 150, 150)
another_shape.shadow_format = rectangle_shadow.clone()
```

### Πώς αλλάζω τη σκιά για έναν **different shape type**;

Όλοι οι τύποι σχημάτων μοιράζονται τις ίδιες ιδιότητες `ShadowFormat`, έτσι μπορείτε να επαναχρησιμοποιήσετε το ίδιο μπλοκ ρυθμίσεων—απλώς αντικαταστήστε το `ShapeType.RECTANGLE` με `ShapeType.OVAL`, `ShapeType.TRIANGLE`, κ.λπ.

### Τι γίνεται με **high‑resolution PDFs** για εκτύπωση;

Ορίστε το `PdfSaveOptions` με υψηλότερο DPI:

```python
options = aw.saving.PdfSaveOptions()
options.image_resolution = 300  # 300 DPI for print quality
document.save(output_path, options)
```

## Περίληψη

Συζητήσαμε όλα όσα χρειάζεστε για να **create rectangle shape**, **how to add shape**, να προσαρμόσετε το **shadow colour**, **set shadow distance**, και τέλος **save document as pdf**. Το πλήρες, εκτελέσιμο σενάριο είναι το εξής:

```python
import aspose.words as aw

# Initialise document
document = aw.Document()
builder = aw.DocumentBuilder(document)

# Insert rectangle shape
rectangle_shape = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE, 200, 100)
rectangle_shape.fill_color = aw.Color.light_blue

# Enable and style shadow
rectangle_shadow = rectangle_shape.shadow_format
rectangle_shadow.visible = True
rectangle_shadow.style = aw.drawing.ShadowStyle.OUTER
rectangle_shadow.blur_radius = 10.0
rectangle_shadow.distance = 5.0
rectangle_shadow.direction = 45.0
rectangle_shadow.color = aw.Color.gray

# Save as PDF
output_path = "YOUR_DIRECTORY/ShadowedShape.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

## Τι Επόμενο;

- **Εξερευνήστε άλλους τύπους σχημάτων** (`ShapeType.OVAL`, `ShapeType.LINE`) για να εμπλουτίσετε τα έγγραφά σας.  
- **Συνδυάστε πολλαπλές σκιές** στρώνοντας σχήματα· μπορείτε ακόμη να δημιουργήσετε εφέ “glow” χρησιμοποιώντας εσωτερική σκιά με φωτεινό χρώμα.  
- **Αυτοματοποιήστε την επεξεργασία παρτίδας**: κάντε βρόχο σε μια συλλογή γραμμών δεδομένων, δημιουργήστε ένα σχήμα ανά γραμμή, και συγχωνεύστε όλα σε ένα ενιαίο PDF.  
- **Ενσωματώστε με άλλες βιβλιοθήκες Aspose** (π.χ., Aspose.Slides) αν χρειάζεται να εξάγετε το ίδιο οπτικό στοιχείο σε PowerPoint.

Μη διστάσετε να πειραματιστείτε—αλλάξτε το `blur_radius`, παίξτε με το `direction`, ή αντικαταστήστε το `gray` με ένα χρώμα ειδικό για το brand σας. Το API είναι αρκετά ευέλικτο ώστε με λίγες προσαρμογές να αλλάξει δραστικά η οπτική εντύπωση.

Έχετε ερωτήσεις ή μια δύσκολη περίπτωση; Αφήστε ένα σχόλιο παρακάτω ή στείλτε μήνυμα στα φόρουμ της κοινότητας Aspose. Καλή προγραμματιστική δουλειά, και απολαύστε αυτά τα όμορφα σκιώδη ορθογώνια!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}