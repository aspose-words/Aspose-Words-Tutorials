---
category: general
date: 2026-06-27
description: Μάθετε πώς να ρυθμίζετε την ακτίνα θολώματος σχήματος χρησιμοποιώντας
  το Aspose.Words for Java. Αυτός ο βήμα‑βήμα οδηγός καλύπτει επίσης τις ρυθμίσεις
  σκιάς, τη διαφάνεια και την αποθήκευση του εγγράφου.
draft: false
keywords:
- configure shape blur radius
- Aspose.Words shape shadow
- Java shadow format
- Word document shape manipulation
- set blur radius
language: el
og_description: Διαμορφώστε την ακτίνα θολώματος του σχήματος σε ένα έγγραφο Word
  χρησιμοποιώντας Java. Ακολουθήστε αυτόν τον λεπτομερή οδηγό για να κατακτήσετε τις
  ρυθμίσεις σκιάς σχήματος του Aspose.Words.
og_title: Διαμόρφωση Ακτίνας Θολώματος Σχήματος σε Java – Πλήρης Οδηγός
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Learn how to configure shape blur radius using Aspose.Words for Java.
    This step‑by‑step tutorial also covers shadow settings, transparency, and saving
    the document.
  headline: Configure Shape Blur Radius in Java – Complete Guide
  type: TechArticle
- description: Learn how to configure shape blur radius using Aspose.Words for Java.
    This step‑by‑step tutorial also covers shadow settings, transparency, and saving
    the document.
  name: Configure Shape Blur Radius in Java – Complete Guide
  steps:
  - name: Understanding the Numbers
    text: '- **Blur radius** (`setBlurRadius`) controls how fuzzy the shadow looks.
      A value of `0` gives a crisp edge, while `10` or higher yields a dreamy glow.
      - **DistanceX / DistanceY** shift the shadow relative to the shape. Positive
      X moves it right; positive Y moves it down. - **Transparency** makes the'
  - name: Targeting a Specific Shape by Name
    text: 'If your document contains many shapes, rely on the shape’s **name** (set
      in Word’s layout options) instead of index:'
  - name: Applying Different Blur Radii
    text: 'You might want a stronger blur for background graphics and a subtle one
      for icons. Loop through all shapes:'
  - name: Compatibility Notes
    text: '- **Units:** Aspose.Words uses points (1 pt = 1/72 inch). If you work with
      millimeters, convert accordingly. - **Version:** The API shown works with Aspose.Words
      for Java 24.9 and later. Older versions may use `setBlurRadius(double)` but
      lack some newer shadow properties.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Document Automation
title: Διαμόρφωση της ακτίνας θολώματος σχήματος σε Java – Πλήρης οδηγός
url: /el/java/images-shapes/configure-shape-blur-radius-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Διαμόρφωση Ακτίνας Θολώματος Σχήματος σε Java – Πλήρης Οδηγός

Έχετε ποτέ χρειαστεί να **configure shape blur radius** σε ένα έγγραφο Word ενώ εργάζεστε με Java; Δεν είστε ο μόνος που σκεπάζει το κεφάλι του για αυτό. Είτε βελτιώνετε μια εταιρική αναφορά είτε προσθέτετε μια διακριτική οπτική πινελιά σε ένα φυλλάδιο, η εξοικείωση με αυτή τη ρύθμιση μπορεί να κάνει τα έγγραφά σας να φαίνονται πολύ πιο επαγγελματικά.

Σε αυτό το tutorial θα περάσουμε από όλη τη διαδικασία — από τη φόρτωση του αρχείου `.docx` μέχρι τη ρύθμιση του θολώματος της σκιάς και, τέλος, την αποθήκευση του αποτελέσματος. Καθ' οδόν θα αγγίξουμε επίσης συναφή θέματα όπως **Aspose.Words shape shadow**, **Java shadow format**, και γενική **Word document shape manipulation**. Στο τέλος, θα έχετε ένα έτοιμο‑για‑εκτέλεση απόσπασμα κώδικα και μια σαφή κατανόηση του γιατί κάθε γραμμή είναι σημαντική.

## Τι Θα Μάθετε

- Πώς να φορτώσετε ένα έγγραφο Word με Aspose.Words for Java.  
- Πώς να εντοπίσετε το πρώτο αντικείμενο `Shape` μέσα στο σώμα του εγγράφου.  
- Τα ακριβή βήματα για **configure shape blur radius** και άλλες ιδιότητες σκιάς όπως η απόσταση και η διαφάνεια.  
- Πώς να αποθηκεύσετε τις αλλαγές σε ένα νέο αρχείο `.docx`.  

Δεν απαιτούνται εξωτερικές βιβλιοθήκες εκτός από το Aspose.Words, και ο κώδικας λειτουργεί με Java 8‑plus και οποιαδήποτε πρόσφατη έκδοση του Aspose.Words for Java (π.χ., 24.9). Εάν είστε άνετοι με τη βασική σύνταξη της Java, θα είστε εντάξει.

---

## Βήμα 1: Φόρτωση του Εγγράφου Word

Πριν μπορέσετε να επεξεργαστείτε οποιοδήποτε σχήμα, χρειάζεστε το έγγραφο στη μνήμη. Το Aspose.Words το κάνει αυτό με μία μόνο γραμμή κώδικα.

```java
// Load the source .docx file
com.aspose.words.Document document = new com.aspose.words.Document("YOUR_DIRECTORY/input.docx");
```

**Γιατί είναι σημαντικό:**  
Η δημιουργία ενός αντικειμένου `Document` αναλύει ολόκληρο το αρχείο, παρέχοντάς σας πρόσβαση σε ενότητες, παραγράφους, πίνακες, **και σχήματα**. Η παράλειψη αυτού του βήματος θα σας αφήσει χωρίς το πλαίσιο για την εφαρμογή της ακτίνας θολώματος.

> **Pro tip:** Εάν εργάζεστε με μεγάλα αρχεία, σκεφτείτε τη χρήση του `LoadOptions` για να μεταφέρετε μόνο τα τμήματα που χρειάζεστε. Μπορεί να μειώσει δραματικά τη χρήση μνήμης.

---

## Βήμα 2: Ανάκτηση του Στόχου Σχήματος

Τα σχήματα μπορούν να βρίσκονται οπουδήποτε — κεφαλίδες, υποσέλιδα, πίνακες, ό,τι θέλετε. Για απλότητα, θα πάρουμε το πρώτο σχήμα που βρίσκεται στο κύριο σώμα της πρώτης ενότητας.

```java
// Navigate to the first shape in the document body
com.aspose.words.Shape shape = (com.aspose.words.Shape) document
        .getFirstSection()
        .getBody()
        .getChild(com.aspose.words.NodeType.SHAPE, 0, true);
```

**Γιατί είναι σημαντικό:**  
Η κλήση `getChild` διασχίζει το δέντρο κόμβων βάθος‑πρώτα, επιστρέφοντας το *πρώτο* σχήμα που ταιριάζει με το `NodeType.SHAPE`. Εάν το έγγραφό σας περιέχει πολλαπλά σχήματα, μπορείτε να προσαρμόσετε το δείκτη (`0`) ή να επαναλάβετε μέσω `document.getChildNodes(NodeType.SHAPE, true)`.

> **Edge case:** Εάν το έγγραφο δεν έχει σχήματα, το `shape` θα είναι `null` και η επόμενη γραμμή θα προκαλέσει `NullPointerException`. Πάντα να το ελέγχετε σε κώδικα παραγωγής.

---

## Βήμα 3: Διαμόρφωση της Σκιάς του Σχήματος – Ορισμός Ακτίνας Θολώματος

Τώρα έρχεται το αστέρι της παράστασης: η ρύθμιση της ακτίνας θολώματος. Αυτό βρίσκεται μέσα στο αντικείμενο `ShadowFormat` που είναι συνδεδεμένο με το σχήμα.

```java
// Access the shadow format of the shape
com.aspose.words.ShadowFormat shadow = shape.getShadowFormat();

// Set the blur radius (in points). Larger values produce a softer edge.
shadow.setBlurRadius(5.0);

// Optional: fine‑tune other shadow attributes
shadow.setDistanceX(3.0);          // Horizontal offset
shadow.setDistanceY(3.0);          // Vertical offset
shadow.setTransparency(0.3);      // 0 = fully opaque, 1 = fully transparent
```

### Κατανόηση των Αριθμών

- **Blur radius** (`setBlurRadius`) ελέγχει πόσο θολή φαίνεται η σκιά. Μια τιμή `0` δίνει καθαρή άκρη, ενώ `10` ή μεγαλύτερη δημιουργεί ένα ονειρικό φωτισμό.
- **DistanceX / DistanceY** μετατοπίζουν τη σκιά σε σχέση με το σχήμα. Θετικό X τη μετακινεί δεξιά· θετικό Y τη μετακινεί κάτω.
- **Transparency** κάνει τη σκιά διαυγή. Χρήσιμο όταν θέλετε ένα διακριτικό εφέ αντί για ένα στερεό μαύρο μπλοκ.

> **Why configure blur radius?**  
> Σε πολλά εταιρικά πρότυπα, μια ήπια θόλωση προσθέτει βάθος χωρίς να αποσπά την προσοχή του αναγνώστη. Είναι μια μικρή οπτική ρύθμιση που μπορεί να βελτιώσει δραματικά την αντιληπτή ποιότητα.

---

## Βήμα 4: Αποθήκευση του Τροποποιημένου Εγγράφου

Όλη η βαριά δουλειά έχει ολοκληρωθεί· τώρα γράψτε τις αλλαγές πίσω στο δίσκο.

```java
// Persist the modified document
document.save("YOUR_DIRECTORY/output.docx");
```

**Γιατί είναι σημαντικό:**  
Η κλήση `save` γράφει ολόκληρο το έγγραφο, συμπεριλαμβανομένου του ενημερωμένου `ShadowFormat`. Εάν χρειάζεστε μόνο το σχήμα ως εικόνα, μπορείτε να το εξάγετε μέσω `shape.getImageData().save(...)`.

---

## Πλήρης Παράδειγμα Λειτουργίας

Παρακάτω βρίσκεται το πλήρες, αυτόνομο πρόγραμμα που μπορείτε να αντιγράψετε‑και‑επικολλήσετε σε οποιοδήποτε IDE της Java. Βεβαιωθείτε ότι έχετε το JAR του Aspose.Words for Java στο classpath σας.

```java
import com.aspose.words.*;

public class ConfigureShapeBlurRadius {
    public static void main(String[] args) throws Exception {
        // 1. Load the document
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Get the first shape (add null‑check for safety)
        Shape shape = (Shape) document.getFirstSection()
                .getBody()
                .getChild(NodeType.SHAPE, 0, true);
        if (shape == null) {
            System.out.println("No shape found in the document.");
            return;
        }

        // 3. Configure shadow – focus on blur radius
        ShadowFormat shadow = shape.getShadowFormat();
        shadow.setBlurRadius(5.0);          // Soft blur
        shadow.setDistanceX(3.0);           // Horizontal offset
        shadow.setDistanceY(3.0);           // Vertical offset
        shadow.setTransparency(0.3);        // Slightly transparent

        // 4. Save the result
        document.save("YOUR_DIRECTORY/output.docx");
        System.out.println("Document saved with configured shape blur radius.");
    }
}
```

**Αναμενόμενο αποτέλεσμα:**  
Η εκτέλεση του προγράμματος δημιουργεί ένα νέο `output.docx` όπου το πρώτο σχήμα έχει τώρα μια ήπια, ημιδιαφανή σκιά με ακτίνα θολώματος `5` σημεία. Ανοίξτε το αρχείο στο Word, επιλέξτε το σχήμα και, κάτω από **Shape Format → Shadow Effects → Shadow Options**, θα δείτε τις τιμές που ορίσατε να εμφανίζονται στη διεπαφή.

---

## Διαχείριση Πολλαπλών Σχημάτων & Προχωρημένα Σενάρια

### Στόχευση Συγκεκριμένου Σχήματος με Όνομα

Εάν το έγγραφό σας περιέχει πολλά σχήματα, βασιστείτε στο **όνομα** του σχήματος (ορίζεται στις επιλογές διάταξης του Word) αντί για το δείκτη:

```java
Shape target = (Shape) document.getChildNodes(NodeType.SHAPE, true)
        .stream()
        .filter(node -> ((Shape) node).getName().equals("MyLogo"))
        .findFirst()
        .orElse(null);
```

### Εφαρμογή Διαφορετικών Ακτίνων Θολώματος

Μπορεί να θέλετε μια πιο έντονη θόλωση για γραφικά φόντου και μια διακριτική για εικονίδια. Επανάληψη σε όλα τα σχήματα:

```java
for (Node node : document.getChildNodes(NodeType.SHAPE, true)) {
    Shape s = (Shape) node;
    ShadowFormat sf = s.getShadowFormat();
    sf.setBlurRadius(s.getName().contains("Background") ? 10.0 : 3.0);
}
```

### Σημειώσεις Συμβατότητας

- **Units:** Το Aspose.Words χρησιμοποιεί μονάδες points (1 pt = 1/72 ίντσα). Εάν εργάζεστε με χιλιοστά, μετατρέψτε ανάλογα.
- **Version:** Το παραδειγματικό API λειτουργεί με Aspose.Words for Java 24.9 και μεταγενέστερες εκδόσεις. Παλαιότερες εκδόσεις μπορεί να χρησιμοποιούν `setBlurRadius(double)` αλλά λείπουν ορισμένες νεότερες ιδιότητες σκιάς.

---

## Συνηθισμένα Πιθανά Σφάλματα & Πώς να τα Αποφύγετε

| Πρόβλημα | Γιατί Συμβαίνει | Διόρθωση |
|----------|----------------|----------|
| `NullPointerException` στο `shape` | Το έγγραφο δεν έχει σχήματα ή ο δείκτης ερωτήματος είναι εκτός εύρους | Προσθέστε έλεγχο null πριν την πρόσβαση στο `ShadowFormat`. |
| Η σκιά δεν είναι ορατή στο Word | Το χρώμα της σκιάς είναι προεπιλεγμένα διαφανές ή οι τιμές απόστασης την μετακινούν εκτός σελίδας | Ορίστε ένα ορατό `ShadowColor` (`shadow.setColor(Color.BLACK)`) και κρατήστε τις τιμές `DistanceX/Y` μέτριες. |
| Η ακτίνα θολώματος δεν αλλάζει | Χρήση παλιάς έκδοσης του Aspose.Words που αγνοεί την ιδιότητα | Αναβαθμίστε στη νεότερη βιβλιοθήκη· η ιδιότητα εισήχθη στην έκδοση 20.5. |
| Μείωση απόδοσης σε μεγάλα έγγραφα | Επαναποθήκευση ολόκληρου του εγγράφου μετά από κάθε τροποποίηση σχήματος | Ομαδοποιήστε όλες τις αλλαγές και καλέστε `save` μία φορά. |

---

## Συμπέρασμα

Τώρα γνωρίζετε **πώς να διαμορφώσετε την ακτίνα θολώματος σχήματος** σε ένα έγγραφο Word χρησιμοποιώντας Java και Aspose.Words. Από τη φόρτωση του αρχείου, την ανάκτηση του σωστού `Shape`, τη ρύθμιση του `ShadowFormat`, μέχρι την αποθήκευση των αλλαγών — κάθε βήμα καλύπτεται με εξηγήσεις και πρακτικές συμβουλές.

Η τεχνική δεν περιορίζεται σε ένα μόνο σχήμα· μπορείτε να την επεκτείνετε σε ολόκληρα έγγραφα, να εφαρμόσετε διαφορετικά επίπεδα θολώματος ή να τη συνδυάσετε με άλλες ιδιότητες σκιάς όπως **shadow transparency Java**. Τα επόμενα λογικά βήματα είναι να εξερευνήσετε το **set blur radius** για εικόνες, να πειραματιστείτε με το **Java shadow format** σε διαγράμματα, ή να εμβαθύνετε στην **Word document shape manipulation** για δυναμική δημιουργία αναφορών.

Έχετε κάποιο σενάριο που δεν καλύφθηκε εδώ; Αφήστε ένα σχόλιο ή ελέγξτε την τεκμηρίωση του Aspose.Words for Java για πιο προχωρημένα εφέ σκιάς. Καλή προγραμματιστική!

---

<img src="configure-shape-blur-radius.png" alt="Διαμόρφωση ακτίνας θολώματος σχήματος χρησιμοποιώντας παράδειγμα Aspose.Words Java" style="max-width:100%;">

---

## Τι Θα Πρέπει Να Μάθετε Στη Σειρά;

Τα παρακάτω tutorials καλύπτουν στενά σχετικά θέματα που βασίζονται στις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Δημιουργία Εγγράφου Word Java – Προσθήκη Ορθογωνίου Σχήματος με Εφέ Σκιάς](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Χρήση Επιλογών και Ρυθμίσεων Εγγράφου στο Aspose.Words for Java](/words/english/java/document-manipulation/using-document-options-and-settings/)
- [Πώς να Μετατρέψετε Word σε PDF Χρησιμοποιώντας Aspose.Words for Java](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}