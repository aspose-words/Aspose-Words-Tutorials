---
category: general
date: 2026-05-23
description: Προσθέστε σκιά σε σχήμα σε Java χρησιμοποιώντας το Aspose.Words. Μάθετε
  πώς να φορτώνετε ένα έγγραφο Word, να ορίζετε την θόλωση της σκιάς, τη γωνία και
  να αλλάζετε το χρώμα της σκιάς αποδοτικά.
draft: false
keywords:
- add shadow to shape
- change shadow color
- load word document
- set shadow blur
- set shadow angle
language: el
og_description: Προσθέστε σκιά σε σχήμα στην Java με το Aspose.Words. Αυτό το σεμινάριο
  δείχνει πώς να φορτώσετε ένα έγγραφο Word, να ορίσετε τη θολότητα της σκιάς, τη
  γωνία και να αλλάξετε το χρώμα της σκιάς.
og_title: Προσθήκη σκιάς σε σχήμα στη Java – Πλήρης οδηγός
schemas:
- author: Aspose
  dateModified: '2026-05-23'
  description: Add shadow to shape in Java using Aspose.Words. Learn how to load a
    Word document, set shadow blur, angle, and change shadow color efficiently.
  headline: Add shadow to shape in Java – Complete Programming Guide
  type: TechArticle
- description: Add shadow to shape in Java using Aspose.Words. Learn how to load a
    Word document, set shadow blur, angle, and change shadow color efficiently.
  name: Add shadow to shape in Java – Complete Programming Guide
  steps:
  - name: 1. Load Word document
    text: First, we need to bring the `.docx` file into memory. This is the foundation
      for every subsequent operation.
  - name: 2. Retrieve the first shape in the document
    text: Most tutorials skim over node traversal, but grabbing the right shape is
      essential when you want to **add shadow to shape**.
  - name: 3. Configure the shape’s shadow effect
    text: Now the fun part—tweaking the shadow. We’ll touch on **set shadow blur**,
      **set shadow angle**, and **change shadow color** all in one tidy block.
  - name: 4. Save the modified document
    text: Once the shadow is set, persist the changes.
  - name: Expected Output
    text: '- The `output.docx` file will look identical to `input.docx` except the
      first shape now sports a soft blue shadow cast at a 45° angle. - Open the file
      in Microsoft Word or LibreOffice to verify the visual effect.'
  type: HowTo
- questions:
  - answer: Yes—Aspose.Words handles `.doc` transparently. Just change the file extension
      in the `Document` constructor.
    question: Does this work with older `.doc` files?
  - answer: The Word format doesn’t support animated shadows; you’d need to export
      to a format like PowerPoint or HTML + CSS for that.
    question: Can I animate the shadow?
  - answer: 'Pass `true` for the `deep` flag (as we did) and the API will locate shapes
      anywhere in the document tree, including headers/footers. --- ## Conclusion
      We’ve just **added shadow to shape** objects in a Word document using Java,
      covering everything from **load word document** to **set shadow blur**, *'
    question: What if the shape is inside a header or footer?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Word Automation
title: Προσθήκη σκιάς σε σχήμα στη Java – Πλήρης Οδηγός Προγραμματισμού
url: /el/java/images-shapes/add-shadow-to-shape-in-java-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Προσθήκη σκιάς σε σχήμα σε Java – Πλήρης Οδηγός Προγραμματισμού

Έχετε ποτέ χρειαστεί να **προσθέσετε σκιά σε σχήμα** σε ένα έγγραφο Word αλλά δεν ήξερτε από πού να ξεκινήσετε; Σε αυτόν τον οδηγό θα περάσουμε από τη φόρτωση ενός εγγράφου Word, τη ρύθμιση της θολότητας, της γωνίας της σκιάς και ακόμη και την αλλαγή του χρώματος της σκιάς — όλα με καθαρό κώδικα Java.

Αν έχετε αναρωτηθεί ποτέ πώς να **φορτώσετε έγγραφο Word** προγραμματιστικά ή πώς να **ορίσετε τη θολότητα της σκιάς** για πιο επαγγελματική εμφάνιση, βρίσκεστε στο σωστό μέρος. Στο τέλος θα έχετε ένα έτοιμο‑για‑εκτέλεση απόσπασμα κώδικα που μπορείτε να ενσωματώσετε σε οποιοδήποτε έργο Java χρησιμοποιώντας το Aspose.Words.

---

## Τι Θα Μάθετε

- Πώς να **φορτώσετε ένα έγγραφο Word** με το Aspose.Words for Java  
- Τα ακριβή βήματα για να **προσθέσετε σκιά σε σχήμα** αντικείμενα  
- Τρόποι για **αλλαγή χρώματος σκιάς**, ρύθμιση **θολότητας σκιάς**, και ορισμό **γωνίας σκιάς**  
- Συμβουλές για τη διαχείριση πολλαπλών σχημάτων και κοινών παγίδων  

Δεν απαιτείται προηγούμενη εμπειρία με το Aspose· αρκεί μια βασική ρύθμιση Java και περιέργεια για αυτοματοποίηση εγγράφων.

---

## Προαπαιτούμενα

- Java 8 ή νεότερη (ο κώδικας συντάσσεται και σε JDK 11)  
- Βιβλιοθήκη Aspose.Words for Java – μπορείτε να την αποκτήσετε από το Maven Central (`com.aspose:aspose-words:23.11`)  
- Ένα απλό αρχείο `.docx` που περιέχει τουλάχιστον ένα σχήμα (ορθογώνιο, κύκλο κ.λπ.)  
- Ένα IDE ή εργαλείο κατασκευής της επιλογής σας (IntelliJ, Eclipse, Maven, Gradle…)  

Αυτό είναι όλο—τίποτα περίπλοκο, μόνο τα απαραίτητα για να τρέξει η επίδειξη.

---

## Προσθήκη σκιάς σε σχήμα – Υλοποίηση Βήμα‑Βήμα

Παρακάτω χωρίζουμε τη διαδικασία σε μικρά βήματα. Μπορείτε να το διαβάσετε γρήγορα, αλλά συνιστώ να ακολουθήσετε τη σειρά ώστε να μην χάσετε καμία κρίσιμη κλήση.

### 1. Φόρτωση εγγράφου Word

Πρώτα, πρέπει να φορτώσουμε το αρχείο `.docx` στη μνήμη. Αυτό αποτελεί τη βάση για κάθε επόμενη λειτουργία.

```java
import com.aspose.words.*;

public class ShadowDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        // Continue with shape handling...
    }
}
```

> **Γιατί είναι σημαντικό:** Η φόρτωση του εγγράφου σας δίνει ένα αντικείμενο `Document` που λειτουργεί ως πύλη σε κάθε κόμβο — παραγράφους, πίνακες, **σχήματα**, κ.ά. Αν η διαδρομή του αρχείου είναι λανθασμένη, το Aspose θα ρίξει ένα σαφές `FileNotFoundException`, οπότε ελέγξτε ξανά τη θέση.

### 2. Ανάκτηση του πρώτου σχήματος στο έγγραφο

Οι περισσότεροι οδηγοί παραλείπουν τη διάσχιση των κόμβων, αλλά η λήψη του σωστού σχήματος είναι ουσιώδης όταν θέλετε να **προσθέσετε σκιά σε σχήμα**.

```java
        // Step 2: Retrieve the first shape (index 0) in the document
        Shape firstShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        if (firstShape == null) {
            System.out.println("No shapes found in the document.");
            return;
        }
```

> **Συμβουλή:** Χρησιμοποιήστε `true` για την παράμετρο `deep` ώστε η αναζήτηση να διασχίσει ολόκληρο το δέντρο κόμβων. Εάν έχετε πολλαπλά σχήματα, απλώς αλλάξτε το δείκτη (`1`, `2`, …) ή κάντε βρόχο μέσω `doc.getChildNodes(NodeType.SHAPE, true)`.

### 3. Διαμόρφωση του εφέ σκιάς του σχήματος

Τώρα το διασκεδαστικό μέρος — η ρύθμιση της σκιάς. Θα ασχοληθούμε με **ορισμό θολότητας σκιάς**, **ορισμό γωνίας σκιάς**, και **αλλαγή χρώματος σκιάς** όλα σε ένα κομψό μπλοκ.

```java
        // Step 3: Configure the shadow effect
        ShadowEffect shadow = firstShape.getShadowEffect();

        // Set shadow blur (softness) – this is the "set shadow blur" part
        shadow.setBlurRadius(5.0);          // 5 points of blur gives a gentle feather

        // Set distance from the shape – not a keyword but influences perception
        shadow.setDistance(3.0);            // 3 points away from the shape

        // Set angle (direction) – fulfills the "set shadow angle" requirement
        shadow.setDirection(45.0);          // 45° points to the bottom‑right

        // Change shadow color – here we pick a subtle blue
        shadow.setColor(Color.getBlue());   // This is the "change shadow color" step
```

> **Γιατί κάθε ιδιότητα;**  
> - **BlurRadius** ελέγχει πόσο θολές φαίνονται οι άκρες· μια υψηλότερη τιμή δίνει πιο απαλό αποτέλεσμα.  
> - **Distance** καθορίζει πόσο μακριά είναι η σκιά· συνδυάστε το με **Direction** για ρεαλιστικό φωτισμό.  
> - **Direction** μετράται σε μοίρες δεξιόστροφα από τον οριζόντιο άξονα — 45° είναι μια κοινή γωνία «ήλιος‑από‑το‑αριστερό‑επάνω».  
> - **Color** σας επιτρέπει να ταιριάξετε το χρώμα με το branding ή τις οδηγίες σχεδίασης· οποιοδήποτε `java.awt.Color` λειτουργεί.

### 4. Αποθήκευση του τροποποιημένου εγγράφου

Μόλις οριστεί η σκιά, αποθηκεύστε τις αλλαγές.

```java
        // Step 4: Save the modified document
        doc.save("YOUR_DIRECTORY/output.docx");
        System.out.println("Shadow applied and document saved successfully.");
    }
}
```

> **Συμβουλή:** Το Aspose επιλέγει αυτόματα τη μορφή εξόδου βάσει της επέκτασης του αρχείου. Αποθηκεύστε ως `.pdf` αν χρειάζεστε μια φορητή έκδοση.

---

## Πλήρες Παράδειγμα Εργασίας

Συνδυάζοντας όλα, εδώ είναι ο πλήρης κώδικας που μπορείτε να αντιγράψετε‑και‑επικολλήσετε σε μια νέα κλάση Java.

```java
import com.aspose.words.*;

public class ShadowDemo {
    public static void main(String[] args) throws Exception {
        // Load the source .docx file
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Grab the first shape in the document
        Shape firstShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        if (firstShape == null) {
            System.out.println("No shapes found in the document.");
            return;
        }

        // Apply shadow settings
        ShadowEffect shadow = firstShape.getShadowEffect();
        shadow.setBlurRadius(5.0);          // set shadow blur
        shadow.setDistance(3.0);
        shadow.setDirection(45.0);          // set shadow angle
        shadow.setColor(Color.getBlue());   // change shadow color

        // Save the result
        doc.save("YOUR_DIRECTORY/output.docx");
        System.out.println("Shadow applied and document saved successfully.");
    }
}
```

### Αναμενόμενο Αποτέλεσμα

- Το αρχείο `output.docx` θα φαίνεται ταυτόσημο με το `input.docx` εκτός από το ότι το πρώτο σχήμα θα έχει τώρα μια ήπια μπλε σκιά που ρίχνεται σε γωνία 45°.  
- Ανοίξτε το αρχείο στο Microsoft Word ή στο LibreOffice για να επαληθεύσετε το οπτικό αποτέλεσμα.

---

## Περιπτώσεις Ορίων & Πρακτικές Συμβουλές

| Κατάσταση | Τι να κάνετε |
|-----------|------------|
| **Πολλαπλά σχήματα** | Κάντε βρόχο μέσω `doc.getChildNodes(NodeType.SHAPE, true)` και εφαρμόστε την ίδια λογική σκιάς σε κάθε ένα. |
| **Δεν υπάρχει υπάρχουσα σκιά** | Το Aspose δημιουργεί ένα προεπιλεγμένο αντικείμενο `ShadowEffect` στην πρώτη πρόσβαση, έτσι μπορείτε να ορίσετε ιδιότητες χωρίς επιπλέον αρχικοποίηση. |
| **Διαφορετικές ανάγκες χρώματος** | Χρησιμοποιήστε `new Color(r, g, b)` για προσαρμοσμένες αποχρώσεις, π.χ., `new Color(255, 128, 0)` για πορτοκαλί. |
| **Ανησυχίες απόδοσης** | Αν επεξεργάζεστε εκατοντάδες έγγραφα, επαναχρησιμοποιήστε ένα μόνο αντικείμενο `Document` όπου είναι δυνατόν και καλέστε `doc.clone()` για κάθε νέο αρχείο. |
| **Αποθήκευση ως PDF** | Αντικαταστήστε το `doc.save("output.pdf")` για να λάβετε ένα PDF με το ίδιο εφέ σκιάς ενσωματωμένο. |

---

## Συχνές Ερωτήσεις

**Ε: Λειτουργεί αυτό με παλαιότερα αρχεία `.doc`;**  
Α: Ναι — το Aspose.Words διαχειρίζεται τα `.doc` διαφανώς. Απλώς αλλάξτε την επέκταση του αρχείου στον κατασκευαστή `Document`.

**Ε: Μπορώ να κάνω την σκιά κινούμενη;**  
Α: Η μορφή Word δεν υποστηρίζει κινούμενες σκιές· θα χρειαστεί να εξάγετε σε μορφή όπως PowerPoint ή HTML + CSS για αυτό.

**Ε: Τι γίνεται αν το σχήμα βρίσκεται μέσα σε κεφαλίδα ή υποσέλιδο;**  
Α: Περάστε `true` για τη σημαία `deep` (όπως κάναμε) και το API θα εντοπίσει σχήματα οπουδήποτε στο δέντρο του εγγράφου, συμπεριλαμβανομένων κεφαλίδων/υποσέλιδων.

---

## Συμπέρασμα

Μόλις **προσθέσαμε σκιά σε σχήμα** σε αντικείμενα ενός εγγράφου Word χρησιμοποιώντας Java, καλύπτοντας τα πάντα από **φόρτωση εγγράφου Word** μέχρι **ορισμό θολότητας σκιάς**, **ορισμό γωνίας σκιάς**, και **αλλαγή χρώματος σκιάς**. Το απόσπασμα είναι αυτόνομο, εκτελείται αμέσως με το Aspose.Words, και σας παρέχει ένα επαγγελματικό αποτέλεσμα σε δευτερόλεπτα.

Έτοιμοι για την επόμενη πρόκληση; Δοκιμάστε να εφαρμόσετε διαβαθμίσεις, εφέ ανάγλυφου, ή ακόμη και να συνδυάσετε πολλαπλές σκιές στο ίδιο σχήμα. Και αν σας ενδιαφέρει η εξαγωγή σε PDF ή η αυτοματοποίηση μαζικών ενημερώσεων, αυτά τα θέματα είναι φυσικές επεκτάσεις του τι καλύψαμε σήμερα.

Καλό προγραμματισμό, και μη διστάσετε να αφήσετε ένα σχόλιο αν αντιμετωπίσετε προβλήματα! 

![Add shadow to shape example in Java](add-shadow-to-shape-java.png)


## Σχετικά Μαθήματα

- [Δημιουργία Εγγράφου Word Java – Προσθήκη Ορθογώνιου Σχήματος με Εφέ Σκιάς](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Πώς να δημιουργήσετε πεδία φόρμας και να προσθέσετε περιεχόμενο χρησιμοποιώντας DocumentBuilder στο Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Πώς να Προσθέσετε Υδατογράφημα σε Έγγραφα Χρησιμοποιώντας Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}