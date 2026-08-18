---
category: general
date: 2026-07-03
description: Δημιουργήστε σχήμα ορθογωνίου στην Java και μάθετε πώς να προσθέσετε
  σκιά στο σχήμα, να εφαρμόσετε το εφέ σκιάς, να ορίσετε τη διαφάνεια του σχήματος
  και να δημιουργήσετε γρήγορα ένα κενό έγγραφο.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- apply shadow effect
- set shape transparency
- create blank document
language: el
og_description: Δημιουργήστε σχήμα ορθογωνίου στη Java με σκιά, διαφάνεια και ένα
  κενό έγγραφο. Ακολουθήστε αυτόν τον οδηγό για να κατακτήσετε τη διαχείριση σχημάτων.
og_title: Δημιουργία σχήματος ορθογωνίου στη Java – Πλήρες μάθημα προγραμματισμού
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Create rectangle shape in Java and learn how to add shadow to shape,
    apply shadow effect, set shape transparency, and create blank document quickly.
  headline: Create rectangle shape in Java – Complete Step‑by‑Step Guide
  type: TechArticle
- description: Create rectangle shape in Java and learn how to add shadow to shape,
    apply shadow effect, set shape transparency, and create blank document quickly.
  name: Create rectangle shape in Java – Complete Step‑by‑Step Guide
  steps:
  - name: What if I want a different shadow color?
    text: 'Simply change the `setColor` call:'
  - name: Can I apply the same shadow to multiple shapes?
    text: 'Yes. Create one `ShadowEffect` instance, configure it, then reuse it:'
  - name: How do I change the shadow blur dynamically?
    text: Expose a UI slider that maps to `setBlurRadius`. Values between `2` and
      `12` are typical; larger numbers produce a “glow” rather than a crisp shadow.
  - name: What if I need the shape to float rather than be inline?
    text: 'Swap the wrap type:'
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Automation
title: Δημιουργία σχήματος ορθογωνίου σε Java – Πλήρης Οδηγός Βήμα‑βήμα
url: /el/java/images-shapes/create-rectangle-shape-in-java-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία σχήματος ορθογωνίου σε Java – Πλήρης Οδηγός Βήμα‑βήμα

Έχετε αναρωτηθεί ποτέ πώς να **δημιουργήσετε σχήμα ορθογωνίου** σε ένα έγγραφο Word χρησιμοποιώντας Java; Δεν είστε οι μόνοι—οι προγραμματιστές συχνά χρειάζονται έναν γρήγορο τρόπο να προσθέσουν γεωμετρικά γραφικά, και στη συνέχεια να τους δώσουν μια διακριτική σκιά ώστε η διάταξη να φαίνεται πιο επαγγελματική. Σε αυτό το tutorial θα περάσουμε από όλη τη διαδικασία: από τη δημιουργία ενός **create blank document** μέχρι το **add shadow to shape**, **apply shadow effect**, και ακόμη το **set shape transparency** για το τελικό επαγγελματικό αποτέλεσμα.

Το παρακάτω απόσπασμα κώδικα είναι ένα πλήρως λειτουργικό παράδειγμα που μπορείτε να αντιγράψετε‑και‑επικολλήσετε στο πρότζεκτ σας. Δεν απαιτείται εξωτερική τεκμηρίωση—απλώς ακολουθήστε τα βήματα, κατανοήστε το “γιατί”, και θα δημιουργείτε σκιώδεις ορθογώνιους σε δευτερόλεπτα.

## Τι Θα Μάθετε

- Πώς να **create rectangle shape** προγραμματιστικά με Aspose.Words for Java.
- Τα ακριβή κλήσεις που χρειάζονται για **add shadow to shape** και τη διαμόρφωση των οπτικών του ιδιοτήτων.
- Τρόπους για **apply shadow effect** και ρύθμιση παραμέτρων όπως offset, blur radius και χρώμα.
- Τεχνικές για **set shape transparency** ώστε να επιτυγχάνεται πιο διακριτική εμφάνιση.
- Πώς να **create blank document**, να εισάγετε το σχήμα και να αποθηκεύσετε το αποτέλεσμα.

> **Pro tip:** Όλες αυτές οι ενέργειες εκτελούνται σε ένα μόνο αντικείμενο `Document`, πράγμα που σημαίνει ότι μπορείτε να τις αλυσίδετε χωρίς να ανησυχείτε για ενδιάμεσες εγγραφές αρχείων.

## Προαπαιτούμενα

Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε:

- Java 17 (ή οποιοδήποτε πρόσφατο JDK) εγκατεστημένο.
- Βιβλιοθήκη Aspose.Words for Java προστιθέμενη στο πρότζεκτ σας (συντεταγμένες Maven: `com.aspose:aspose-words:23.12`).
- Ένα IDE Java ή απλό κειμενογράφο—τίποτα περίπλοκο, μόνο ένα μέρος για να μεταγλωττίσετε και να τρέξετε.

Αν λείπει κάτι από αυτά, κατεβάστε το JDK από την Oracle και προσθέστε την εξάρτηση Aspose μέσω Maven ή Gradle. Μόλις το κάνετε, είστε έτοιμοι να ξεκινήσετε.

## Βήμα 1: **Create blank document** – ο καμβάς για όλα

Το πρώτο πράγμα που χρειάζεστε είναι ένα κενό αντικείμενο `Document`. Σκεφτείτε το ως ένα φρέσκο φύλλο χαρτί· χωρίς αυτό, δεν υπάρχει που να τοποθετήσετε το ορθογώνιο σας.

```java
// Step 1: Create a new blank document
Document document = new Document();
```

Γιατί ξεκινάμε με ένα κενό έγγραφο; Επειδή κάθε σχήμα ζει μέσα σε ένα `Section`, και ένα νεοδημιουργημένο `Document` περιέχει ήδη μια προεπιλεγμένη ενότητα με σώμα έτοιμο να δεχτεί κόμβους. Παραλείποντας αυτό το βήμα θα σας ανάγκαζε να δημιουργήσετε ενότητες χειροκίνητα αργότερα, προσθέτοντας περιττή πολυπλοκότητα.

## Βήμα 2: **Create rectangle shape** και ορισμός διαστάσεων

Τώρα που έχουμε καμβά, ας **create rectangle shape**. Η κλάση `Shape` δέχεται την αναφορά του εγγράφου και έναν `ShapeType`. Εδώ επιλέγουμε `RECTANGLE` και ορίζουμε πλάτος/ύψος σε points (1 pt ≈ 1/72 inch).

```java
// Step 2: Insert a rectangle shape and define its size and layout
Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
rectangleShape.setWidth(200);   // 200 pt ≈ 2.78 inches
rectangleShape.setHeight(100);  // 100 pt ≈ 1.39 inches
rectangleShape.setWrapType(WrapType.INLINE);
```

Γιατί ορίζουμε `WrapType.INLINE`; Η ενσωματωμένη αναδίπλωση κάνει το σχήμα να συμπεριφέρεται όπως ένας χαρακτήρας στην παράγραφο, εξασφαλίζοντας ότι κινείται μαζί με το περιβάλλον κείμενο. Αν χρειάζεστε αιωρούμενη συμπεριφορά, αλλάξτε σε `WrapType.SQUARE` ή `WrapType.TOP_BOTTOM`.

## Βήμα 3: **Apply shadow effect** – δώστε βάθος στο ορθογώνιο

Ένα επίπεδο ορθογώνιο φαίνεται… απλό. Η προσθήκη σκιάς το κάνει να «αναδύεται». Θα **apply shadow effect** δημιουργώντας μια παρουσία `ShadowEffect`, έπειτα ρυθμίζοντας τις οπτικές του ιδιότητες.

```java
// Step 3: Create a shadow effect and configure its visual properties
ShadowEffect shadowEffect = new ShadowEffect();
shadowEffect.setColor(Color.getGray(0.5));   // medium gray
shadowEffect.setOffsetX(5);                  // horizontal offset (points)
shadowEffect.setOffsetY(5);                  // vertical offset (points)
shadowEffect.setBlurRadius(8);               // softness of the shadow
shadowEffect.setTransparency(0.3);           // 30 % transparent
```

Ας το εξηγήσουμε λίγο:

- **Color** – `Color.getGray(0.5)` δίνει γκρι 50 %, ουδέτερο και λειτουργεί σε περισσότερα υπόβαθρα.
- **OffsetX/Y** – Θετικές τιμές σπρώχνουν τη σκιά προς τα δεξιά και κάτω· αρνητικές τιμές θα την μετακινούσαν αριστερά/πάνω.
- **BlurRadius** – Μεγαλύτερες τιμές δημιουργούν πιο μαλακή, πιο διαχυμένη σκιά.
- **Transparency** – Κυμαίνεται από `0` (αδιαφανής) έως `1` (πλήρως διαφανής). Εδώ επιλέξαμε `0.3` για διακριτικό αποτέλεσμα.

## Βήμα 4: **Add shadow to shape** – σύνδεση του εφέ

Η δημιουργία του εφέ δεν αρκεί· πρέπει να **add shadow to shape** αναθέτοντας το αντικείμενο `ShadowEffect` στο ορθογώνιο.

```java
// Step 4: Apply the shadow effect to the rectangle shape
rectangleShape.setShadowEffect(shadowEffect);
```

Πίσω από τις κουρτίνες, αυτή η κλήση ενημερώνει το υποκείμενο markup OpenXML (`<w:shdw>`) που χρησιμοποιεί το Word για την απόδοση σκιών. Αν εξετάσετε το αποθηκευμένο `.docx`, θα δείτε ένα στοιχείο `<w:effect>` γεμάτο με τις παραμέτρους που ορίσαμε.

## Βήμα 5: **Set shape transparency** – προαιρετικό αλλά συχνά χρήσιμο

Μερικές φορές θέλετε το ίδιο το ορθογώνιο να είναι ημιδιαφανές, ώστε το κείμενο του υποβάθρου να φαίνεται. Η κλάση `Shape` εκθέτει `setFillColor` και `setFillTransparency`. Ακολουθεί ένα γρήγορο παράδειγμα που κάνει το ορθογώνιο 40 % διαφανές:

```java
// Optional: make the rectangle partially transparent
rectangleShape.setFillColor(Color.getWhite());
rectangleShape.setFillTransparency(0.4); // 40 % transparent
```

Γιατί μπορεί να το θέλετε αυτό; Σκεφτείτε ένα υδατογράφημα ή μια επισημάνση όπου το υποκείμενο περιεχόμενο πρέπει να παραμένει αναγνώσιμο. Ρυθμίστε την τιμή διαφάνειας ώστε να ταιριάζει με το στυλ σχεδίασής σας.

## Βήμα 6: Εισαγωγή του σχήματος στο έγγραφο

Έχουμε χτίσει το ορθογώνιο, προσθέσαμε σκιά και (προαιρετικά) ορίσαμε τη διαφάνειά του. Το τελευταίο βήμα είναι να **add the shape to the first section of the document**.

```java
// Step 5: Add the shape to the first section of the document
document.getFirstSection().getBody().appendChild(rectangleShape);
```

Η προσθήκη του σχήματος στο σώμα τοποθετεί το αντικείμενο στο τέλος της πρώτης παραγράφου. Αν χρειάζεστε συγκεκριμένο σημείο εισαγωγής, ανακτήστε το στόχο `Paragraph` και χρησιμοποιήστε `insertBefore` ή `insertAfter`.

## Βήμα 7: Αποθήκευση του εγγράφου – δείτε το αποτέλεσμα

Όλη αυτή η δουλειά καταλήγει σε μία κλήση `save`. Επιλέξτε μια διαδρομή που έχει νόημα για το περιβάλλον σας.

```java
// Step 6: Save the document with the shadowed shape
document.save("YOUR_DIRECTORY/ShadowShape.docx");
```

Ανοίξτε το παραγόμενο `ShadowShape.docx` στο Microsoft Word ή στο LibreOffice, και θα δείτε ένα καθαρό ορθογώνιο με ήπια γκρι σκιά, ελαφρώς διαφανές αν διατηρήσατε το προαιρετικό βήμα. Η οπτική αντιστοιχεί στις παραμέτρους που ορίσαμε προγραμματιστικά.

---

![δημιουργία σχήματος ορθογωνίου με σκιά σε έγγραφο Word](https://example.com/images/rectangle-shadow.png "δημιουργία σχήματος ορθογωνίου με σκιά")

*Image alt text:* **δημιουργία σχήματος ορθογωνίου με σκιά** – οπτική αναπαράσταση του τελικού αποτελέσματος.

## Συχνές Ερωτήσεις & Ακραίες Περιπτώσεις

### Τι αν θέλω διαφορετικό χρώμα σκιάς;

Απλώς αλλάξτε την κλήση `setColor`:

```java
shadowEffect.setColor(Color.getRed()); // bright red shadow
```

Θυμηθείτε ότι υπερβολικά έντονες σκιές μπορεί να φαίνονται ακατάλληλες· οι διακριτοί τόνοι συνήθως λειτουργούν καλύτερα.

### Μπορώ να εφαρμόσω την ίδια σκιά σε πολλά σχήματα;

Ναι. Δημιουργήστε μία παρουσία `ShadowEffect`, διαμορφώστε την και επαναχρησιμοποιήστε την:

```java
Shape circle = new Shape(document, ShapeType.OVAL);
circle.setShadowEffect(shadowEffect); // same effect as rectangle
```

Απλώς αποφύγετε την τροποποίηση του `ShadowEffect` μετά την προσθήκη του σε άλλα σχήματα, εκτός αν θέλετε να τα ενημερώσετε όλα.

### Πώς μπορώ να αλλάξω δυναμικά το blur της σκιάς;

Εμφανίστε έναν διακόπτη UI που αντιστοιχεί στο `setBlurRadius`. Τιμές μεταξύ `2` και `12` είναι τυπικές· μεγαλύτεροι αριθμοί παράγουν «glow» αντί για καθαρή σκιά.

### Τι αν χρειάζομαι το σχήμα να αιωρείται αντί για inline;

Αλλάξτε τον τύπο αναδίπλωσης:

```java
rectangleShape.setWrapType(WrapType.SQUARE);
rectangleShape.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
rectangleShape.setHorizontalAlignment(HorizontalAlignment.CENTER);
```

Τα αιωρούμενα σχήματα προσφέρουν μεγαλύτερη ελευθερία διάταξης αλλά απαιτούν επιπλέον λογική τοποθέτησης.

## Πλήρες Παράδειγμα Εργασίας

Παρακάτω βρίσκεται το ολοκληρωμένο πρόγραμμα, έτοιμο για αντιγραφή‑και‑επικόλληση, που ενσωματώνει όλα τα βήματα που συζητήσαμε. Εκτελέστε το ως κανονική εφαρμογή Java.

```java
import com.aspose.words.*;

public class ShadowRectangleDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a blank document
        Document document = new Document();

        // 2. Build the rectangle shape
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(200);
        rectangleShape.setHeight(100);
        rectangleShape.setWrapType(WrapType.INLINE);

        // 3. Configure shadow effect
        ShadowEffect shadowEffect = new ShadowEffect();
        shadowEffect.setColor(Color.getGray(0.5));
        shadowEffect.setOffsetX(5);
        shadowEffect.setOffsetY(5);
        shadowEffect.setBlurRadius(8);
        shadowEffect.setTransparency(0.3);

        // 4. Apply shadow to the rectangle
        rectangleShape.setShadowEffect(shadowEffect);

        // 5. (Optional) Make rectangle semi‑transparent
        rectangleShape.setFillColor(Color.getWhite());
        rectangleShape.setFillTransparency(0.4);

        // 6. Insert shape into the document
        document.getFirstSection().getBody().appendChild(rectangleShape);

        // 7. Save the file
        document.save("ShadowShape.docx");
    }
}
```

**Αναμενόμενο αποτέλεσμα:** Όταν ανοίξετε το `ShadowShape.docx`, θα δείτε ένα λευκό ορθογώνιο, 200 × 100 pt, κεντραρισμένο στην πρώτη παράγραφο, με μέτρια γκρι σκιά μετατοπισμένη κατά 5 pt, θολή με ακτίνα 8, και 30 % διαφάνεια. Το ίδιο το ορθογώνιο είναι 40 % διαφανές, επιτρέποντας στο υποκείμενο κείμενο να φαίνεται.

## Συμπεράσματα

Μόλις **create rectangle shape** από το μηδέν, **add shadow to shape**, **apply shadow effect**, και ακόμη **set shape transparency**—όλα ενώ **create blank document** ως βάση. Η προσέγγιση είναι απλή, βασίζεται στο ευέλικτο API του Aspose.Words, και μπορεί να επεκταθεί σε κύκλους, αστέρια ή προσαρμοσμένα πολύγωνα.

Τι θα κάνετε στη συνέχεια; Δοκιμάστε να αντικαταστήσετε το `ShapeType.RECTANGLE` με `ShapeType.OVAL` για δημιουργία σκιωδών κύκλων, ή πειραματιστείτε με γεμίσματα gradient για

## Τι Θα Μάθετε Στη Σειρά;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη κώδικα με βήμα‑βήμα εξηγήσεις για να κυριαρχήσετε σε επιπλέον δυνατότητες API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στα δικά σας πρότζεκτ.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}