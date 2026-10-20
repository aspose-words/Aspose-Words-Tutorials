---
category: general
date: 2026-05-30
description: Δημιουργήστε σχήμα πλαισίου κειμένου στη Java και μάθετε πώς να προσθέσετε
  σκιά, να ορίσετε το χρώμα της σκιάς και την απόσταση της σκιάς. Ακολουθήστε αυτό
  το βήμα‑βήμα οδηγό για ένα επαγγελματικό έγγραφο.
draft: false
keywords:
- create text box shape
- set shadow color
- how to add shadow
- set shadow distance
- add shadow textbox
language: el
og_description: Δημιουργήστε σχήμα πλαισίου κειμένου σε Java και δείτε αμέσως πώς
  να προσθέσετε σκιά, να ορίσετε το χρώμα και την απόσταση της σκιάς. Ένας πρακτικός
  οδηγός για το Aspose.Words.
og_title: Δημιουργία σχήματος πλαισίου κειμένου σε Java – Οδηγός πλήρους σκιάς
schemas:
- author: Aspose
  dateModified: '2026-05-30'
  description: Create text box shape in Java and learn how to add shadow, set shadow
    color, and set shadow distance. Follow this step‑by‑step tutorial for a polished
    document.
  headline: Create Text Box Shape in Java – Complete Guide to Adding Shadows
  type: TechArticle
- description: Create text box shape in Java and learn how to add shadow, set shadow
    color, and set shadow distance. Follow this step‑by‑step tutorial for a polished
    document.
  name: Create Text Box Shape in Java – Complete Guide to Adding Shadows
  steps:
  - name: Why These Values?
    text: '- **BlurRadius** of `4.0` gives a gentle feathered edge without looking
      fuzzy. - **Distance** of `5.0` offsets the shadow enough to be noticeable but
      not detached. - **Transparency** of `0.35` keeps the shadow from overwhelming
      the text. - **Color** `GRAY` works well on both light and dark backgroun'
  - name: 1️⃣ Can I apply a shadow to a shape that already contains images?
    text: Absolutely. The `ShadowFormat` works on any `Shape`, whether it’s a text
      box, picture, or auto‑shape. Just retrieve the shape’s `ShadowFormat` and set
      the desired properties.
  - name: 2️⃣ What if I need multiple shadows (e.g., inner and outer)?
    text: Aspose.Words currently supports a single drop shadow per shape. For more
      complex effects you might need to duplicate the shape, offset it, and adjust
      opacity manually.
  - name: 3️⃣ Does the shadow respect the document’s theme colors?
    text: When you use `Color.getThemeColor(ThemeColor.ACCENT_1)`, the shadow will
      follow the active theme. This is handy for corporate branding where you don’t
      want hard‑coded RGB values.
  - name: 4️⃣ How does **add shadow textbox** differ from adding a picture shadow?
    text: The API is identical; the only distinction is the shape type. A textbox
      is a `ShapeType.TEXT_BOX`, while a picture is `ShapeType.IMAGE`. Both expose
      `ShadowFormat`.
  - name: 5️⃣ I’m targeting PDF output—will the shadow survive the conversion?
    text: Yes. Aspose.Words renders shadows when saving to PDF, provided you’re using
      a recent version (23.12+). Just call `doc.save("output.pdf")` instead of DOCX.
  - name: Wrap‑Up
    text: We’ve just walked through a complete, end‑to‑end example that shows you
      how
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Generation
title: Δημιουργία σχήματος πλαισίου κειμένου στη Java – Πλήρης οδηγός προσθήκης σκιών
url: /el/java/images-shapes/create-text-box-shape-in-java-complete-guide-to-adding-shado/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία Σχήματος Πλαισίου Κειμένου σε Java – Πλήρης Οδηγός για Προσθήκη Σκιών

Έχετε αναρωτηθεί ποτέ πώς να **create text box shape** σε Java και να του δώσετε μια κομψή σκιά πτώσης; Δεν είστε μόνοι. Είτε δημιουργείτε αναφορές, είτε ετοιμάζετε διαφημιστικά φυλλάδια, είτε απλώς πειραματίζεστε με το στυλ εγγράφων, ένα πλαίσιο κειμένου με σκιά μπορεί να κάνει το αποτέλεσμα σας να φαίνεται πολύ πιο επαγγελματικό.

Σε αυτό το tutorial θα περάσουμε από όλη τη διαδικασία — από τη δημιουργία του σχήματος μέχρι τη ρύθμιση της σκιάς — ώστε να μπορείτε να **add shadow textbox** στοιχεία με σιγουριά. Στο τέλος θα γνωρίζετε ακριβώς **how to add shadow**, πώς να **set shadow color**, και πώς να **set shadow distance** χρησιμοποιώντας το Aspose.Words for Java.

## Τι Θα Μάθετε

- Τα προαπαιτούμενα εργαλεία (Java 17+, Aspose.Words for Java, ένα IDE)
- Πώς να **create text box shape** με `DocumentBuilder`
- Πώς να **set shadow color**, **set shadow distance**, και να ρυθμίσετε το blur ή τη διαφάνεια
- Ένα πλήρες, εκτελέσιμο παράδειγμα που μπορείτε να αντιγράψετε‑και‑επικολλήσετε
- Συμβουλές για αντιμετώπιση κοινών προβλημάτων και επέκταση του εφέ

> **Pro tip:** Αν δεν έχετε εγκαταστήσει ακόμη το Aspose.Words, πάρτε το τελευταίο JAR από το επίσημο αποθετήριο Maven — αυτό το tutorial στοχεύει στην έκδοση 23.12, η οποία υποστηρίζει όλα τα shadow‑related APIs που θα χρησιμοποιήσουμε.

![Κώδικας Java που δημιουργεί σχήμα πλαισίου κειμένου με σκιά](https://example.com/images/shadow-textbox-java.png "Κώδικας Java που δημιουργεί σχήμα πλαισίου κειμένου με σκιά")

*(Κείμενο alt εικόνας: “Κώδικας Java που δημιουργεί σχήμα πλαισίου κειμένου με σκιά” – περιλαμβάνει την κύρια λέξη‑κλειδί)*

## Βήμα 1: Ρύθμιση του Έργου σας και Εισαγωγή Εξαρτήσεων

Πριν μπορέσουμε να **create text box shape**, χρειαζόμαστε ένα έργο Java που να αναφέρει το Aspose.Words. Αν χρησιμοποιείτε Maven, προσθέστε τα παρακάτω στο `pom.xml` σας:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

Αν προτιμάτε Gradle, το ισοδύναμο είναι:

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

Μόλις η βιβλιοθήκη είναι στο classpath, εισάγετε τις κλάσεις που θα χρειαστούμε:

```java
import com.aspose.words.*;
import java.awt.Color;
```

Αυτό είναι—το περιβάλλον σας είναι έτοιμο να **create text box shape** και να αρχίσει να το στυλιζάτε.

## Βήμα 2: Δημιουργία Κενής Εγγράφου και Builder

Το πρώτο κομμάτι του παζλ είναι ένα νέο αντικείμενο `Document`. Σκεφτείτε το ως έναν καθαρό καμβά. Στη συνέχεια συνδέουμε ένα `DocumentBuilder` για να αρχίσουμε να εισάγουμε περιεχόμενο.

```java
// Step 2: Initialize a new document and builder
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Παρατηρήστε ότι το σχόλιο αναφέρει “initialize”. Σε καθημερινό κώδικα συχνά βλέπετε “create document”, αλλά εμείς θα **create text box shape** αργότερα, οπότε κρατήστε αυτή τη διάκριση σαφή.

## Βήμα 3: **Create Text Box Shape** και Εισαγωγή Κειμένου

Τώρα έρχεται η κύρια ενέργεια: στην πραγματικότητα **create text box shape**. Η μέθοδος `insertShape` παίρνει ένα `ShapeType`, πλάτος και ύψος. Αφού το σχήμα τοποθετηθεί, μπορούμε να γράψουμε κείμενο απευθείας μέσα του.

```java
// Step 3: Insert a text box shape where the shadow will be applied
Shape textBox = builder.insertShape(ShapeType.TEXT_BOX, 300.0, 80.0);

// Write some placeholder text inside the box
builder.moveTo(textBox.getFirstParagraph());
builder.writeln("Shadowed TextBox Example");
```

- `ShapeType.TEXT_BOX` λέει στο Aspose ότι θέλουμε ένα κοντέινερ που μπορεί να περιέχει παραγράφους.
- Οι διαστάσεις (`300 × 80`) είναι σε points· προσαρμόστε τις ώστε να ταιριάζουν στο layout σας.
- Με τη μετακίνηση του κέρσορα του builder στην πρώτη παράγραφο του σχήματος, εξασφαλίζουμε ότι το κείμενο εμφανίζεται *μέσα* στο κουτί.

## Βήμα 4: **How to Add Shadow** – Διαμόρφωση του ShadowFormat

Το Aspose.Words εκθέτει ένα αντικείμενο `ShadowFormat` σε κάθε σχήμα. Εδώ απαντάμε στην ερώτηση **how to add shadow**. Μπορείτε να ελέγξετε το blur, την απόσταση, τη διαφάνεια και, φυσικά, το χρώμα.

```java
// Step 4: Access the shadow format and configure it
ShadowFormat shadow = textBox.getShadowFormat();

// Set a subtle blur radius
shadow.setBlurRadius(4.0);

// Define how far the shadow is offset from the shape
shadow.setDistance(5.0);               // This is the "set shadow distance" part

// Make the shadow semi‑transparent
shadow.setTransparency(0.35);

// Choose a color – here's where we **set shadow color**
shadow.setColor(Color.GRAY);
```

### Γιατί Αυτές οι Τιμές;

- **BlurRadius** των `4.0` δίνει μια ήπια θολή άκρη χωρίς να φαίνεται ασαφής.
- **Distance** των `5.0` μετατοπίζει τη σκιά αρκετά ώστε να είναι εμφανής αλλά όχι αποσπασμένη.
- **Transparency** του `0.35` αποτρέπει τη σκιά να κυριαρχεί πάνω στο κείμενο.
- **Color** `GRAY` λειτουργεί καλά τόσο σε ανοιχτά όσο και σε σκούρα φόντα· μπορείτε να αντικαταστήσετε με `Color.RED` ή οποιαδήποτε προσαρμοσμένη τιμή RGB.

Νιώστε ελεύθεροι να πειραματιστείτε — η αλλαγή του `setShadowDistance` σε μεγαλύτερο αριθμό θα ωθήσει τη σκιά πιο μακριά, ενώ ένα μικρότερο blur την κάνει πιο οξυμένη.

## Βήμα 5: Αποθήκευση του Εγγράφου

Με το σχήμα μορφοποιημένο, το τελευταίο βήμα είναι να γράψετε το αρχείο στο δίσκο. Το Aspose.Words υποστηρίζει πολλές μορφές· εδώ θα χρησιμοποιήσουμε DOCX για μέγιστη συμβατότητα.

```java
// Step 5: Persist the document
String outputPath = "output/ShadowedTextboxDemo.docx";
doc.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

Η εκτέλεση του προγράμματος θα δημιουργήσει ένα αρχείο Word που περιέχει ένα πλαίσιο κειμένου με μια ωραία αποδομένη σκιά. Ανοίξτε το σε Microsoft Word, LibreOffice ή οποιονδήποτε προβολέα που καταλαβαίνει DOCX, και θα δείτε το εφέ αμέσως.

## Πλήρες Παράδειγμα Λειτουργίας

Συνδυάζοντας όλα, εδώ είναι μια αυτόνομη κλάση που μπορείτε να μεταγλωττίσετε και να εκτελέσετε:

```java
import com.aspose.words.*;
import java.awt.Color;

public class ShadowEffectDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a new blank document and a builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a text box shape (the core of our tutorial)
        Shape textBox = builder.insertShape(ShapeType.TEXT_BOX, 300.0, 80.0);
        builder.moveTo(textBox.getFirstParagraph());
        builder.writeln("Shadowed TextBox Example");

        // 3️⃣ Configure shadow – this answers "how to add shadow"
        ShadowFormat shadow = textBox.getShadowFormat();
        shadow.setBlurRadius(4.0);
        shadow.setDistance(5.0);               // set shadow distance
        shadow.setTransparency(0.35);
        shadow.setColor(Color.GRAY);           // set shadow color

        // 4️⃣ Save the result
        String out = "output/ShadowedTextboxDemo.docx";
        doc.save(out);
        System.out.println("Document saved to " + out);
    }
}
```

**Αναμενόμενο αποτέλεσμα:** Όταν ανοίξετε το `ShadowedTextboxDemo.docx`, θα δείτε ένα μόνο πλαίσιο κειμένου κεντραρισμένο στην πρώτη σελίδα, που περιέχει τη φράση “Shadowed TextBox Example”. Μια ήπια γκρι σκιά θα εμφανιστεί μετατοπισμένη προς τα κάτω‑δεξιά, δίνοντας την εντύπωση βάθους.

## Συχνές Ερωτήσεις & Ακραίες Περιπτώσεις

### 1️⃣ Μπορώ να εφαρμόσω σκιά σε σχήμα που ήδη περιέχει εικόνες;

Απολύτως. Το `ShadowFormat` λειτουργεί σε οποιοδήποτε `Shape`, είτε είναι πλαίσιο κειμένου, εικόνα ή αυτόματο σχήμα. Απλώς ανακτήστε το `ShadowFormat` του σχήματος και ορίστε τις επιθυμητές ιδιότητες.

### 2️⃣ Τι γίνεται αν χρειάζομαι πολλαπλές σκιές (π.χ., εσωτερική και εξωτερική);

Το Aspose.Words αυτή τη στιγμή υποστηρίζει μία μόνο σκιά πτώσης ανά σχήμα. Για πιο σύνθετα εφέ ίσως χρειαστεί να διπλασιάσετε το σχήμα, να το μετατοπίσετε και να ρυθμίσετε τη διαφάνεια χειροκίνητα.

### 3️⃣ Η σκιά σέβεται τα χρώματα θέματος του εγγράφου;

Όταν χρησιμοποιείτε `Color.getThemeColor(ThemeColor.ACCENT_1)`, η σκιά θα ακολουθεί το ενεργό θέμα. Αυτό είναι χρήσιμο για εταιρική επωνυμία όπου δεν θέλετε σκληρά κωδικοποιημένες τιμές RGB.

### 4️⃣ Πώς διαφέρει το **add shadow textbox** από την προσθήκη σκιάς σε εικόνα;

Το API είναι ταυτόσημο· η μόνη διαφορά είναι ο τύπος σχήματος. Ένα πλαίσιο κειμένου είναι `ShapeType.TEXT_BOX`, ενώ μια εικόνα είναι `ShapeType.IMAGE`. Και τα δύο εκθέτουν `ShadowFormat`.

### 5️⃣ Στοχεύω σε έξοδο PDF — θα διατηρηθεί η σκιά μετά τη μετατροπή;

Ναι. Το Aspose.Words αποδίδει σκιές όταν αποθηκεύει σε PDF, εφόσον χρησιμοποιείτε πρόσφατη έκδοση (23.12+). Απλώς καλέστε `doc.save("output.pdf")` αντί για DOCX.

## Συμβουλές & Τεχνάσματα από το Πεδίο Μάχης

- **Pro tip:** Ενεργοποιήστε `doc.getCompatibilityOptions().optimizeFor(CompatibilityOptions.OPTIMIZE_FOR_MS_WORD_2016);` αν παρατηρήσετε λεπτές διαφορές απόδοσης μεταξύ Word και PDF.
- **Watch out for:** Ορίζοντας `distance` σε `0` η σκιά θα κάτσει ακριβώς πίσω από το σχήμα, κάτι που συχνά φαίνεται επίπεδο. Μια μικρή μη μηδενική τιμή είναι συνήθως η καλύτερη.
- **Performance note:** Η απόδοση σκιάς προσθέτει μικρό φορτίο. Αν δημιουργείτε χιλιάδες έγγραφα, ομαδοποιήστε τη ρύθμιση σκιάς μόνο για τα λίγα σχήματα που τη χρειάζονται.

## Επόμενα Βήματα

Τώρα που ξέρετε πώς να **create text box shape**, **set shadow color**, **set shadow distance**, και **add shadow textbox**, σκεφτείτε να εξερευνήσετε τα ακόλουθα σχετικά θέματα:

- **Add gradient fills** στο πλαίσιο κειμένου σας για πιο πλούσιο εμφάνιση.
- **Insert tables** μέσα σε ένα πλαίσιο κειμένου με σκιά για δομημένα δεδομένα.
- **Apply text effects** (outline, glow) μαζί με σκιές για μέγιστο αντίκτυπο.
- **Automate batch processing** πολλαπλών εγγράφων με ένα ενιαίο στυλ σκιάς.

Κάθε ένα από αυτά βασίζεται στο θεμέλιο που θέσαμε, επιτρέποντάς σας να παράγετε πραγματικά επαγγελματικά, συνεπή με το brand έγγραφα προγραμματιστικά.

### Συμπέρασμα

Μόλις περάσαμε από ένα πλήρες, ολοκληρωμένο παράδειγμα που σας δείχνει πώς

## Τι Πρέπει Να Μάθετε Στη Σειρά;

- [Δημιουργία Εγγράφου Word Java – Προσθήκη Σχήματος Ορθογωνίου με Εφέ Σκιάς](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Tutorial Σκιάς Σχήματος Aspose.Words – Προσθήκη Σκιάς σε Σχήμα Word σε C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Δημιουργία Κενής Εγγράφου Word με Σχήμα Ορθογωνίου με Σκιά – Οδηγός Βήμα‑Βήμα](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}