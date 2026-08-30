---
category: general
date: 2026-07-06
description: Δημιουργήστε σχήμα ορθογωνίου σε Java χρησιμοποιώντας το Aspose.Words
  – μάθετε πώς να προσθέσετε σκιά στο σχήμα, να ορίσετε τη διαφάνεια του σχήματος
  και να αποθηκεύσετε το έγγραφο ως PDF.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- set shape transparency
- save document as pdf
- how to add shadow
language: el
og_description: Δημιουργήστε σχήμα ορθογωνίου σε Java με το Aspose.Words. Αυτός ο
  οδηγός δείχνει πώς να προσθέσετε σκιά στο σχήμα, να ορίσετε τη διαφάνεια του σχήματος
  και να αποθηκεύσετε το έγγραφο ως PDF.
og_title: Δημιουργία σχήματος ορθογωνίου σε Java – Εκπαιδευτικό σεμινάριο Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-06'
  description: Create rectangle shape in Java using Aspose.Words – learn how to add
    shadow to shape, set shape transparency, and save document as PDF.
  headline: Create rectangle shape in Java with Aspose.Words – Full Guide
  type: TechArticle
- description: Create rectangle shape in Java using Aspose.Words – learn how to add
    shadow to shape, set shape transparency, and save document as PDF.
  name: Create rectangle shape in Java with Aspose.Words – Full Guide
  steps:
  - name: 1️⃣ What if I need a larger rectangle?
    text: Just change the width and height parameters in `insertShape`. Remember that
      72 pt = 1 in, so `400.0, 200.0` would give you a 5.5 × 2.8 inch rectangle.
  - name: 2️⃣ Can I use a different color for the shadow?
    text: Absolutely. The `ShadowFormat` class also exposes `setColor(java.awt.Color)`.
      For a subtle gray shadow, try `shadow.setColor(java.awt.Color.DARK_GRAY);`.
  - name: 3️⃣ Does `save document as pdf` work on all platforms?
    text: Yes. Aspose.Words for Java is platform‑agnostic; the same code runs on Windows,
      macOS, and Linux as long as you have a compatible JRE.
  - name: 4️⃣ How do I remove the shadow later?
    text: Call `rect.getShadowFormat().clear();` or set the `Visible` property to
      `false` (`shadow.setVisible(false);`).
  - name: 5️⃣ What about DPI and image quality?
    text: When saving to PDF, Aspose automatically uses 300 DPI for vector graphics
      like shapes, so you get crisp results regardless of zoom level.
  type: HowTo
tags:
- Aspose.Words
- Java
- PDF
- Shape
- Shadow
title: Δημιουργία σχήματος ορθογωνίου σε Java με το Aspose.Words – Πλήρης Οδηγός
url: /el/java/images-shapes/create-rectangle-shape-in-java-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία σχήματος ορθογωνίου σε Java με Aspose.Words – Πλήρης Οδηγός

Έχετε αναρωτηθεί ποτέ πώς να **create rectangle shape** σε Java χωρίς να παλεύετε με χαμηλού επιπέδου APIs σχεδίασης; Δεν είστε μόνοι. Πολλοί προγραμματιστές χρειάζονται έναν γρήγορο, αξιόπιστο τρόπο να προσθέσουν ένα ορθογώνιο σε ένα έγγραφο Word, να του δώσουν μια διακριτική σκιά, να ρυθμίσουν τη διαφάνειά του και στη συνέχεια να παραδώσουν το αποτέλεσμα ως PDF.  

Σε αυτό το tutorial θα περάσουμε ακριβώς από αυτό—βήμα προς βήμα, με πλήρη, εκτελέσιμο κώδικα. Στο τέλος θα ξέρετε **how to add shadow** σε ένα σχήμα, πώς να **set shape transparency**, και πώς να **save document as PDF** χρησιμοποιώντας το Aspose.Words for Java. Χωρίς περιττές πληροφορίες, μόνο πρακτικές οδηγίες που μπορείτε να αντιγράψετε‑επικολλήσετε στο πρότζεκτ σας σήμερα.

## Τι Θα Μάθετε

- Η ελάχιστη ρύθμιση που απαιτείται για να δουλέψετε με το Aspose.Words σε ένα έργο Java.  
- Πώς να **create rectangle shape** προγραμματιστικά.  
- Οι ακριβείς κλήσεις που χρειάζονται για **add shadow to shape** και προσαρμογή του θολώματος, της μετατόπισης και της αδιαφάνειας.  
- Τρόποι για **set shape transparency** ώστε το ορθογώνιο να ενσωματώνεται ομαλά με το περιεχόμενο γύρω του.  
- Η πιο απλή μέθοδος για **save document as PDF** χωρίς επιπλέον βήματα μετατροπής.  

Αν είστε άνετοι με τη βασική Java και έχετε μια κατασκευή Maven ή Gradle, είστε έτοιμοι να ξεκινήσετε.

## Προαπαιτούμενα

- Java 8 ή νεότερη.  
- Aspose.Words for Java 23.x (ή η πιο πρόσφατη έκδοση τη στιγμή της ανάγνωσης).  
- Ένα IDE ή εργαλείο κατασκευής γραμμής εντολών (IntelliJ, Eclipse, Maven, Gradle—επιλέξτε ό,τι προτιμάτε).  

> **Pro tip:** Η Aspose προσφέρει δωρεάν προσωρινή άδεια για αξιολόγηση. Πάρτε την από το portal του λογαριασμού σας και τοποθετήστε το αρχείο `license.xml` στο classpath· διαφορετικά θα δείτε ένα υδατογράφημα στο PDF.

---

## Βήμα 1: **Create rectangle shape** με Aspose.Words

Το πρώτο που χρειαζόμαστε είναι ένα κενό `Document` και ένα `DocumentBuilder`. Ο builder είναι ο κύριος μηχανισμός που μας επιτρέπει να εισάγουμε σχήματα απευθείας στη ροή του εγγράφου.

```java
import com.aspose.words.*;

public class RectangleShadowDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new empty Word document
        Document doc = new Document();

        // 2️⃣ Create a builder attached to the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3️⃣ Insert a rectangle shape – 200 points wide, 100 points tall
        Shape rect = builder.insertShape(ShapeType.RECTANGLE, 200.0, 100.0);
        // Optional: give the rectangle a light gray fill so the shadow is visible
        rect.getFillColor().setColor(java.awt.Color.LIGHT_GRAY);
```

**Why this matters:** Το `ShapeType.RECTANGLE` λέει στην Aspose ότι θέλουμε ένα τέλειο ορθογώνιο. Το πλάτος και το ύψος εκφράζονται σε points (1 pt ≈ 1/72 in), κάτι που σας δίνει ακριβή έλεγχο του τελικού μεγέθους.

---

## Βήμα 2: **Add shadow to shape**

Τώρα που έχουμε ένα ορθογώνιο, ας του δώσουμε μια διακριτική σκιά. Το αντικείμενο `ShadowFormat` εκθέτει όλα όσα χρειαζόμαστε—ακτίνα θολώματος, μετατόπιση X/Y, και ακόμη και διαφάνεια.

```java
        // 4️⃣ Configure the shadow effect
        ShadowFormat shadow = rect.getShadowFormat();
        shadow.setBlur(5.0);          // Softness of the shadow edge
        shadow.setOffsetX(3.0);       // Horizontal shift (points)
        shadow.setOffsetY(3.0);       // Vertical shift (points)
        shadow.setTransparency(0.3); // 30 % transparent – makes it look natural
```

**Why this matters:** Μια σκιά χωρίς θόλωση φαίνεται σαν σκληρή γραμμή, κάτι που σπάνια θέλουν οι σχεδιαστές. Η κλήση `setBlur` λειαίνει τις άκρες, ενώ το `setTransparency` επιτρέπει στη σκιά να εξασθενεί στο φόντο. Ρυθμίστε αυτές τις τιμές ώστε να ταιριάζουν με τις οδηγίες UI σας.

---

## Βήμα 3: **Set shape transparency**

Μερικές φορές χρειάζεται το ίδιο το ορθογώνιο να είναι ημιδιαφανές—ίσως για να τοποθετήσετε ένα λογότυπο ή υδατογράφημα. Η Aspose το κάνει με μία μόνο γραμμή κώδικα.

```java
        // 5️⃣ Make the rectangle partially transparent (optional)
        rect.getFillFormat().setTransparency(0.2); // 20 % transparent fill
```

**Why this matters:** Η διαφάνεια μπορεί να σώσει τη ζωή σας όταν στρώετε σχήματα. Σημειώστε ότι η διαφάνεια της σκιάς είναι ανεξάρτητη, έτσι μπορείτε να έχετε ένα αχνό σχήμα με πιο σκοτεινή σκιά αν ταιριάζει στο σχέδιό σας.

---

## Βήμα 4: **Save document as PDF**

Όλη η οπτική δουλειά έχει ολοκληρωθεί· το τελευταίο βήμα είναι η αποθήκευση του εγγράφου. Το Aspose.Words μπορεί να γράψει απευθείας σε PDF, εξαλείφοντας την ανάγκη για ξεχωριστή βιβλιοθήκη μετατροπής.

```java
        // 6️⃣ Persist the document as a PDF file
        String outPath = "output/RectangleWithShadow.pdf";
        doc.save(outPath, SaveFormat.PDF);
        System.out.println("PDF saved to: " + outPath);
    }
}
```

**Why this matters:** Καθορίζοντας `SaveFormat.PDF`, η βιβλιοθήκη διαχειρίζεται την ενσωμάτωση γραμματοσειρών, τη συμπίεση εικόνων και τη συμμόρφωση PDF/A στο παρασκήνιο. Το παραγόμενο αρχείο είναι έτοιμο για διανομή, εκτύπωση ή αρχειοθέτηση.

---

## Πλήρες Παράδειγμα Εργασίας

Συνδυάζοντας όλα τα παραπάνω, εδώ είναι η πλήρης, έτοιμη‑για‑εκτέλεση κλάση. Αντιγράψτε‑επικολλήστε, προσαρμόστε το φάκελο εξόδου, και θα έχετε ένα PDF με ένα ορθογώνιο που ρίχνει μια ρεαλιστική σκιά.

```java
import com.aspose.words.*;

public class RectangleShadowDemo {
    public static void main(String[] args) throws Exception {
        // Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert rectangle shape (200×100 points)
        Shape rect = builder.insertShape(ShapeType.RECTANGLE, 200.0, 100.0);
        rect.getFillColor().setColor(java.awt.Color.LIGHT_GRAY);

        // Add shadow effect
        ShadowFormat shadow = rect.getShadowFormat();
        shadow.setBlur(5.0);
        shadow.setOffsetX(3.0);
        shadow.setOffsetY(3.0);
        shadow.setTransparency(0.3);

        // Optional: make the rectangle itself partially transparent
        rect.getFillFormat().setTransparency(0.2);

        // Save as PDF
        String outPath = "output/RectangleWithShadow.pdf";
        doc.save(outPath, SaveFormat.PDF);
        System.out.println("PDF saved to: " + outPath);
    }
}
```

**Expected output:** Όταν ανοίξετε το `RectangleWithShadow.pdf`, θα δείτε ένα ανοιχτό‑γκρι ορθογώνιο κεντραρισμένο στην πρώτη σελίδα, ελαφρώς ανυψωμένο από μια ήπια, ημιδιαφανή σκιά. Το ίδιο το σχήμα είναι 20 % διαφανές, επιτρέποντας σε οποιοδήποτε κείμενο στο παρασκήνιο (αν προσθέσατε κάποιο) να φαίνεται.

---

## Συχνές Ερωτήσεις & Ακραίες Περιπτώσεις

### 1️⃣ Τι γίνεται αν χρειάζομαι μεγαλύτερο ορθογώνιο;

Απλώς αλλάξτε τις παραμέτρους πλάτους και ύψους στην `insertShape`. Θυμηθείτε ότι 72 pt = 1 in, έτσι `400.0, 200.0` θα σας δώσει ένα ορθογώνιο 5.5 × 2.8 ίντσες.

### 2️⃣ Μπορώ να χρησιμοποιήσω διαφορετικό χρώμα για τη σκιά;

Απολύτως. Η κλάση `ShadowFormat` εκθέτει επίσης τη μέθοδο `setColor(java.awt.Color)`. Για μια διακριτική γκρι σκιά, δοκιμάστε `shadow.setColor(java.awt.Color.DARK_GRAY);`.

### 3️⃣ Λειτουργεί το `save document as pdf` σε όλες τις πλατφόρμες;

Ναι. Το Aspose.Words for Java είναι ανεξάρτητο από πλατφόρμα· ο ίδιος κώδικας εκτελείται σε Windows, macOS και Linux εφόσον έχετε μια συμβατή JRE.

### 4️⃣ Πώς αφαιρώ τη σκιά αργότερα;

Καλέστε `rect.getShadowFormat().clear();` ή ορίστε την ιδιότητα `Visible` σε `false` (`shadow.setVisible(false);`).

### 5️⃣ Τι γίνεται με το DPI και την ποιότητα εικόνας;

Κατά την αποθήκευση σε PDF, το Aspose χρησιμοποιεί αυτόματα 300 DPI για διανυσματικά γραφικά όπως τα σχήματα, έτσι λαμβάνετε καθαρά αποτελέσματα ανεξάρτητα από το επίπεδο ζουμ.

---

## Συμβουλές & Καλές Πρακτικές

- **Batch processing:** Αν χρειάζεται να δημιουργήσετε δεκάδες PDFs, επαναχρησιμοποιήστε ένα μόνο αντικείμενο `Document` και καθαρίστε μόνο τις ενότητες του μεταξύ των επαναλήψεων για να μειώσετε το φορτίο του GC.  
- **Licensing:** Τοποθετήστε `License license = new License(); license.setLicense("license.xml");` στην αρχή του `main` για να αποφύγετε το υδατογράφημα αξιολόγησης.  
- **Performance:** Η απόδοση σκιάς είναι φθηνή για απλά σχήματα, αλλά πολύπλοκες διαδρομές μπορούν να επιβραδύνουν τη δημιουργία PDF. Κάντε profiling αν επεξεργάζεστε μεγάλες παρτίδες.  
- **Testing:** Χρησιμοποιήστε πρώτα το `Document.save(..., SaveFormat.DOCX)` της Aspose για να επαληθεύσετε ότι το σχήμα εμφανίζεται σωστά στο Word πριν το μετατρέψετε σε PDF.

---

## Συμπέρασμα

Τώρα γνωρίζετε πώς να **create rectangle shape** σε Java με Aspose.Words, **add shadow to shape**, **set shape transparency**, και τέλος **save document as PDF**. Ο κώδικας είναι αυτόνομος, λειτουργεί με τη νεότερη βιβλιοθήκη Aspose, και δείχνει τις βασικές κλήσεις API που θα χρειαστείτε για τις περισσότερες περιπτώσεις αυτοματοποίησης εγγράφων.

Έτοιμοι για την επόμενη πρόκληση; Δοκιμάστε να αντικαταστήσετε το ορθογώνιο με μια έλλειψη, πειραματιστείτε με γεμίσματα gradient, ή εξερευνήστε πώς να **add shadow** σε πλαίσια κειμένου. Οι ίδιες αρχές ισχύουν, και το Aspose API το κάνει να φαίνεται παιχνιδάκι.

Καλό κώδικα, και μη διστάσετε να αφήσετε ένα σχόλιο αν αντιμετωπίσετε προβλήματα!

## Τι Θα Μάθετε Στη Σειρά;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε σε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Δημιουργία Εγγράφου Word Java – Προσθήκη Ορθογωνίου Σχήματος με Εφέ Σκιάς](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Πώς να αποθηκεύσετε έγγραφο ως pdf με Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Πώς να δημιουργήσετε πεδία φόρμας και να προσθέσετε περιεχόμενο χρησιμοποιώντας DocumentBuilder στο Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}