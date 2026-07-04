---
category: general
date: 2026-06-21
description: Δημιουργήστε σχήμα ορθογωνίου στην Python χρησιμοποιώντας το Aspose.Words.
  Μάθετε πώς να προσθέσετε σκιά στο σχήμα, να ορίσετε το χρώμα γεμίσματος του σχήματος
  και να αποθηκεύσετε το έγγραφο ως PDF σε λίγα λεπτά.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shadow
- set shape fill color
language: el
og_description: Δημιουργήστε σχήμα ορθογωνίου σε Python με το Aspose.Words. Αυτός
  ο οδηγός δείχνει πώς να προσθέσετε σκιά στο σχήμα, να ορίσετε το χρώμα γεμίσματος
  του σχήματος και να αποθηκεύσετε το έγγραφο ως PDF.
og_title: Δημιουργία σχήματος ορθογωνίου σε Python – Εγχειρίδιο Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-21'
  description: Create rectangle shape in Python using Aspose.Words. Learn how to add
    shadow to shape, set shape fill color, and save document as PDF in minutes.
  headline: Create rectangle shape in Python – Aspose.Words tutorial
  type: TechArticle
tags:
- Aspose.Words
- Python
- PDF generation
title: Δημιουργία σχήματος ορθογωνίου σε Python – Εκπαιδευτικό σεμινάριο Aspose.Words
url: /el/python/images-shapes/create-rectangle-shape-in-python-aspose-words-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία σχήματος ορθογωνίου σε Python – Εγχειρίδιο Aspose.Words

Έχετε αναρωτηθεί ποτέ **πώς να δημιουργήσετε σχήμα ορθογωνίου** σε ένα έγγραφο Word ενώ προγραμματίζετε σε Python; Δεν είστε οι μόνοι. Πολλοί προγραμματιστές συναντούν δυσκολία όταν χρειάζονται ένα γρήγορο οπτικό στοιχείο—όπως ένα χρωματιστό κουτί με ήπια σκιά—και στη συνέχεια εξάγουν το σύνολο ως PDF.  

Σε αυτόν τον οδηγό θα περάσουμε βήμα‑βήμα από ένα πλήρες, εκτελέσιμο παράδειγμα που **δημιουργεί σχήμα ορθογωνίου**, **ορίζει το χρώμα γεμίσματος του σχήματος**, **προσθέτει σκιά στο σχήμα**, και τελικά **αποθηκεύει το έγγραφο ως PDF**. Χωρίς ασαφείς αναφορές, μόνο συγκεκριμένος κώδικας που μπορείτε να αντιγράψετε‑επικολλήσετε και να τρέξετε σήμερα.

## Τι Θα Χρειαστείτε

- Python 3.8 ή νεότερη (η σύνταξη που χρησιμοποιούμε λειτουργεί σε οποιαδήποτε πρόσφατη έκδοση).
- Ένα ενεργό license του Aspose.Words for Python ή μια δωρεάν δοκιμή (η βιβλιοθήκη είναι καθαρά Python, χωρίς ανάγκη COM interop).
- Έναν επεξεργαστή κειμένου ή IDE με τον οποίο αισθάνεστε άνετα—το VS Code λειτουργεί εξαιρετικά, αλλά όποιον προτιμάτε είναι εντάξει.

Αυτό είναι όλο. Χωρίς βαριά frameworks, χωρίς επιπλέον εξαρτήσεις σε επίπεδο λειτουργικού συστήματος. Ας ξεκινήσουμε.

## Step 1: Install Aspose.Words for Python

Πρώτα απ’ όλα. Αν δεν το έχετε κάνει ήδη, κατεβάστε το πακέτο από το PyPI:

```bash
pip install aspose-words
```

Γιατί είναι σημαντικό αυτό το βήμα: το Aspose.Words παρέχει τις κλάσεις `Document` και `DocumentBuilder` στις οποίες θα βασιστούμε. Χωρίς τη βιβλιοθήκη, καμία από τις μετέπειτα κλήσεις—όπως `insert_shape`—δεν υπάρχει, οπότε το script θα καταρρεύσει πριν καν σχεδιάσει κάτι.

> **Pro tip:** Κρατήστε το εικονικό σας περιβάλλον καθαρό. Εκτελέστε `python -m venv .venv && source .venv/bin/activate` πριν την εγκατάσταση, ώστε η βιβλιοθήκη να παραμείνει απομονωμένη από τα συστημικά πακέτα.

## Step 2: Create a New Document and a DocumentBuilder

Τώρα δημιουργούμε πραγματικά **σχήμα ορθογωνίου** – αλλά πρώτα χρειαζόμαστε έναν κενό καμβά.

```python
import aspose.words as aw

# Initialize a new, empty Word document
doc = aw.Document()
# DocumentBuilder lets us add content programmatically
builder = aw.DocumentBuilder(doc)
```

Το αντικείμενο `Document` αντιπροσωπεύει ολόκληρο το αρχείο, ενώ το `DocumentBuilder` είναι ένας χρήσιμος βοηθός που ξέρει πού βρίσκεται ο κέρσορας και μπορεί να εισάγει στοιχεία σε εκείνο το σημείο. Σκεφτείτε το builder ως ένα στυλό που γράφει στη σελίδα.

## Step 3: Insert the Rectangle Shape

Εδώ συμβαίνει η κύρια ενέργεια. Θα **δημιουργήσουμε σχήμα ορθογωνίου** με σταθερό πλάτος και ύψος, και στη συνέχεια θα το τοποθετήσουμε στη σελίδα.

```python
# Insert a rectangle 200 points wide and 100 points tall
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

Γιατί ορθογώνιο; Είναι το πιο απλό σχήμα που μας επιτρέπει να παρουσιάσουμε χρώματα γεμίσματος και σκιές. Αν αργότερα χρειαστείτε κύκλο ή αστέρι, απλώς αντικαταστήστε το `ShapeType.RECTANGLE` με άλλη τιμή του enum.

## Step 4: Set Shape Fill Color

Ένα απλό λευκό κουτί δεν είναι πολύ εντυπωσιακό, οπότε ας **ορίσουμε το χρώμα γεμίσματος του σχήματος** σε κάτι ήπιο—το ανοιχτό μπλε λειτουργεί καλά για αναφορές.

```python
# Apply a light‑blue background to the rectangle
rectangle.fill_color = aw.Color.light_blue
```

Μπορείτε να χρησιμοποιήσετε οποιοδήποτε από τα προ‑καθορισμένα μέλη του `aw.Color` (`red`, `green`, `dark_gray`, κ.λπ.) ή να περάσετε ένα RGB tuple (`aw.Color.from_argb(255, 30, 144, 255)`). Το χρώμα γεμίσματος είναι αυτό που βλέπει ο χρήστης πριν εφαρμοστεί οποιαδήποτε σκιά ή περίγραμμα.

## Step 5: Add Shadow to Shape

Τώρα για το οπτικό φινίρισμα: **προσθήκη σκιάς στο σχήμα**. Οι σκιές δίνουν βάθος και κάνουν το ορθογώνιο να ξεχωρίζει στη σελίδα.

```python
# Grab the shadow format object
shadow = rectangle.shadow_format

# Turn the shadow on
shadow.visible = True
# Choose a dark gray tone for realism
shadow.color = aw.Color.dark_gray
# Blur radius controls softness (5 points is a nice middle ground)
shadow.blur = 5
# Horizontal and vertical offsets shift the shadow relative to the shape
shadow.offset_x = 3
shadow.offset_y = 3
# Slight transparency makes the shadow feel natural
shadow.transparency = 0.2
# Use an outer shadow – you could also try INSET for a different effect
shadow.type = aw.drawing.ShadowType.OUTER
```

**Πώς προστίθεται η σκιά**; Ο παραπάνω κώδικας το κάνει ακριβώς, αλλά ας εξηγήσουμε γιατί κάθε ιδιότητα είναι σημαντική:

- `visible` – ενεργοποιεί/απενεργοποιεί το εφέ.
- `color` – καθορίζει την απόχρωση· ένα σκούρο γκρι μιμείται το φυσικό φωτισμό.
- `blur` – υψηλότερες τιμές παράγουν πιο απαλό άκρο.
- `offset_x` / `offset_y` – μετακινούν τη σκιά μακριά από το σχήμα· ρυθμίστε τα για να προσομοιώσετε διαφορετικές γωνίες φωτός.
- `transparency` – 0 είναι αδιαφανές, 1 είναι αόρατο· 0.2 δίνει ήπια εντύπωση.
- `type` – `OUTER` ρίχνει τη σκιά έξω από το σχήμα, ενώ `INNER` θα την ενσωματώνει μέσα.

Αν χρειάζεστε δραματική «πτώση» σκιάς, αυξήστε το `blur` σε 10‑15 και αυξήστε τα `offset_x`/`offset_y` σε 6‑8.

## Step 6: Save the Document as PDF

Όλη αυτή η δουλειά είναι μάταιη αν δεν μπορούμε να **αποθηκεύσουμε το έγγραφο ως PDF** και να το μοιραστούμε. Το Aspose.Words το κάνει με μία γραμμή:

```python
output_path = r"YOUR_DIRECTORY/ShapeWithShadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Γιατί PDF; Τα PDF διατηρούν τη διάταξη σε όλες τις πλατφόρμες, καθιστώντας τα ιδανικά για αναφορές, τιμολόγια ή οποιοδήποτε εκτυπώσιμο υλικό. Η μέθοδος `save` ανιχνεύει αυτόματα την επέκταση του αρχείου και επιλέγει τη σωστή μορφή—απλώς βεβαιωθείτε ότι η διαδρομή τελειώνει σε `.pdf`.

### Expected Result

Ανοίξτε το παραγόμενο `ShapeWithShadow.pdf` και θα δείτε ένα ανοιχτό‑μπλε ορθογώνιο κεντραρισμένο κοντά στην κορυφή της πρώτης σελίδας, με μια ήπια σκούρα γκρι σκιά ελαφρώς μετατοπισμένη δεξιά και κάτω. Οι άκρες του σχήματος είναι καθαρές, η σκιά ήπια, και το μέγεθος του αρχείου είναι συνήθως κάτω από 100 KB.

## Bonus: Tweaking Shadows – Answers to “how to add shadow”

Μπορεί να αναρωτιέστε, *«Μπορώ να αλλάξω την κατεύθυνση της σκιάς χωρίς να μετακινήσω το σχήμα;»* Απολύτως. Η θέση της σκιάς είναι ανεξάρτητη από τις συντεταγμένες του σχήματος· απλώς ρυθμίστε τα `offset_x` και `offset_y`. Θετικές τιμές μετακινούν τη σκιά δεξιά/κάτω, αρνητικές αριστερά/πάνω. Για πηγή φωτός πάνω‑αριστερά, χρησιμοποιήστε `offset_x = -3` και `offset_y = -3`.

Μια άλλη συχνή ερώτηση: *«Τι γίνεται αν χρειαστώ πολλαπλές σκιές στο ίδιο σχήμα;»* Το Aspose.Words υποστηρίζει μόνο μία σκιά ανά σχήμα. Αν χρειάζεστε στρωματοποιημένα εφέ, δημιουργήστε ένα αντίγραφο του σχήματος, μετατοπίστε το ελαφρώς και εφαρμόστε διαφορετική σκιά σε καθένα. Είναι λίγο «hack», αλλά λειτουργεί.

## Full Script – Ready to Run

Παρακάτω είναι το πλήρες, αυτόνομο script. Αντιγράψτε το σε ένα αρχείο με όνομα `create_rectangle_with_shadow.py` και τρέξτε το με `python create_rectangle_with_shadow.py`.

```python
import aspose.words as aw

# ---------- Initialize document ----------
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# ---------- Insert rectangle ----------
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# ---------- Set fill color ----------
rectangle.fill_color = aw.Color.light_blue

# ---------- Configure shadow ----------
shadow = rectangle.shadow_format
shadow.visible = True
shadow.color = aw.Color.dark_gray
shadow.blur = 5
shadow.offset_x = 3
shadow.offset_y = 3
shadow.transparency = 0.2
shadow.type = aw.drawing.ShadowType.OUTER

# ---------- Save as PDF ----------
output_path = r"YOUR_DIRECTORY/ShapeWithShadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

> **Note:** Αντικαταστήστε το `YOUR_DIRECTORY` με μια απόλυτη ή σχετική διαδρομή που υπάρχει στον υπολογιστή σας. Αν ο φάκελος δεν υπάρχει, η Python θα πετάξει `FileNotFoundError`.

## Common Pitfalls & How to Avoid Them

| Issue | Why it Happens | Fix |
|-------|----------------|-----|
| Shadow not appearing | `shadow.visible` left at default `False` | Ensure `shadow.visible = True` |
| Shape is invisible | Fill color set to `aw.Color.transparent` or `None` | Use a solid color like `aw.Color.light_blue` |
| PDF is empty | Forgot to call `doc.save` or saved with wrong extension | Call `doc.save("output.pdf")` and verify the path |
| Runtime error `ImportError` | Aspose.Words not installed or wrong Python env | Run `pip install aspose-words` inside the active venv |

## Next Steps – Explore More Shapes and Formatting

Τώρα που έχετε κατακτήσει **create rectangle shape**, μπορείτε:

- Αντικαταστήστε το `ShapeType.RECTANGLE` με `ShapeType.ELLIPSE` ή `ShapeType.PENTAGON` για να πειραματιστείτε με άλλες γεωμετρίες.
- Προσθέστε κείμενο μέσα στο σχήμα χρησιμοποιώντας `builder.move_to(rectangle.absolute_position)` και μετά `builder.writeln("Hello World")`.
- Συνδυάστε πολλαπλά σχήματα σε μια ομάδα με `group = aw.drawing.GroupShape(doc)` για σύνθετα διαγράμματα.
- Εξάγετε σε άλλες μορφές όπως DOCX (`doc.save("output.docx")`) ή HTML (`doc.save("output.html")`) για να δείτε πώς μεταφράζεται η σκιά.

Κάθε μία από αυτές τις επεκτάσεις βασίζεται στις ίδιες βασικές έννοιες: **add shadow to shape**, **set shape fill color**, και **save document as PDF** (ή άλλη μορφή).

---

### Image Preview *(optional)*

![Δημιουργία σχήματος ορθογωνίου με σκιά σε Python](https://example.com/rectangle-shadow.png "Δημιουργία σχήματος ορθογωνίου με σκιά σε Python")

*Το στιγμιότυπο δείχνει το τελικό PDF με ένα ανοιχτό‑μπλε ορθογώνιο και μια ήπια εξωτερική σκιά.*

## Conclusion

Διασχίσαμε κάθε βήμα που απαιτείται για να **create rectangle shape** σε Python, να εφαρμόσουμε προσαρμοσμένο γέμισμα, **add shadow to shape**, και τελικά **save document as PDF**. Ο κώδικας είναι πλήρως εκτελέσιμος, οι εξηγήσεις καλύπτουν το *γιατί* πίσω από κάθε ιδιότητα, και αγγίξαμε κοινά edge cases και next‑

## What Should You Learn Next?

Οι παρακάτω οδηγοί καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Δημιουργία εγγράφου Word σε Java – Προσθήκη σχήματος ορθογωνίου με εφέ σκιάς](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Δημιουργία σχήματος ορθογωνίου σε Word χρησιμοποιώντας C# – Οδηγός βήμα‑βήμα](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Προσθήκη σκιάς σε σχήμα Word σε C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}