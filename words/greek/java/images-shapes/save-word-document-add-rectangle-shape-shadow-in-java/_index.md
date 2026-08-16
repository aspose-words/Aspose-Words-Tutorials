---
category: general
date: 2026-06-20
description: Αποθηκεύστε έγγραφο Word χρησιμοποιώντας το Aspose.Words σε Java ενώ
  προσθέτετε ένα σχήμα ορθογωνίου και εφαρμόζετε σκιά. Μάθετε πώς να εισάγετε σχήμα
  βήμα‑βήμα.
draft: false
keywords:
- save word document
- add rectangle shape
- apply shadow to shape
- how to add shadow
- how to insert shape
language: el
og_description: Αποθηκεύστε έγγραφο Word με το Aspose.Words Java. Αυτός ο οδηγός δείχνει
  πώς να προσθέσετε ένα σχήμα ορθογωνίου, να εφαρμόσετε σκιά και να το εισάγετε σε
  μια παράγραφο.
og_title: Αποθήκευση εγγράφου Word – Προσθήκη σχήματος ορθογωνίου & σκιάς σε Java
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: Save Word document using Aspose.Words in Java while adding a rectangle
    shape and applying a shadow. Learn how to insert shape step‑by‑step.
  headline: Save Word Document – Add Rectangle Shape & Shadow in Java
  type: TechArticle
- description: Save Word document using Aspose.Words in Java while adding a rectangle
    shape and applying a shadow. Learn how to insert shape step‑by‑step.
  name: Save Word Document – Add Rectangle Shape & Shadow in Java
  steps:
  - name: '**Compile** – `javac -cp "aspose-words-xx.jar" ShadowShapeDemo.java`'
    text: '**Compile** – `javac -cp "aspose-words-xx.jar" ShadowShapeDemo.java`'
  - name: '**Execute** – `java -cp ".;aspose-words-xx.jar" ShadowShapeDemo`'
    text: '**Execute** – `java -cp ".;aspose-words-xx.jar" ShadowShapeDemo`'
  - name: '**Open** `shadow.docx` in Microsoft Word or LibreOffice. You should see
      the rectangle with a soft black shadow anchored at the start of the first paragraph.'
    text: '**Open** `shadow.docx` in Microsoft Word or LibreOffice. You should see
      the rectangle with a soft black shadow anchored at the start of the first paragraph.'
  type: HowTo
- questions:
  - answer: Yes. Retrieve the target `Section` or `PageSetup` and insert the shape
      into a paragraph located on that page.
    question: Can I add the shape to a specific page?
  - answer: Absolutely. Aspose.Words abstracts the format, so the same code **saves
      a Word document** whether it’s `.doc` or `.docx`.
    question: Does this work with .doc files?
  - answer: 'Replace `ShapeType.RECTANGLE` with `ShapeType.ELLIPSE`. All shadow properties
      remain the same. --- ## Conclusion You now know how to **save a Word document**
      while **adding a rectangle shape**, **applying a shadow**, and **inserting the
      shape** into the first paragraph—all with a handful of clean Ja'
    question: What if I need a different shape, like an ellipse?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Word Automation
title: Αποθήκευση εγγράφου Word – Προσθήκη σχήματος ορθογωνίου & σκιάς σε Java
url: /el/java/images-shapes/save-word-document-add-rectangle-shape-shadow-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Αποθήκευση Εγγράφου Word – Προσθήκη Σχήματος Ορθογωνίου & Σκιά σε Java

Έχετε αναρωτηθεί ποτέ πώς να **αποθηκεύσετε ένα έγγραφο Word** μετά την προσαρμογή της διάταξής του; Δεν είστε μόνοι—οι περισσότεροι προγραμματιστές αντιμετωπίζουν αυτό το πρόβλημα όταν χρειάζεται να εμπλουτίσουν προγραμματιστικά ένα αρχείο DOCX. Τα καλά νέα είναι ότι με το Aspose.Words for Java μπορείτε να **αποθηκεύσετε ένα έγγραφο Word**, να προσθέσετε ένα σχήμα ορθογωνίου ακριβώς όπου το θέλετε, και ακόμη να δώσετε σε αυτό το σχήμα μια διακριτική σκιά.

Σε αυτό το tutorial θα περάσουμε από όλη τη διαδικασία: φόρτωση υπάρχοντος αρχείου, **προσθήκη σχήματος ορθογωνίου**, ρύθμιση της **σκιάς** του, εισαγωγή του σχήματος στην πρώτη παράγραφο, και τέλος **αποθήκευση του εγγράφου Word**. Στο τέλος θα έχετε ένα εκτελέσιμο πρόγραμμα Java που παράγει ένα τελειοποιημένο αρχείο `shadow.docx`—χωρίς καμία χειροκίνητη παρέμβαση.

> **Τι θα χρειαστείτε**  
> * Java 17 (ή οποιοδήποτε πρόσφατο JDK)  
> * Βιβλιοθήκη Aspose.Words for Java (Maven/Gradle ή το JAR)  
> * Ένα αρχείο εισόδου DOCX (`input.docx`) σε γνωστό φάκελο  

Αν έχετε καλύψει αυτά τα βασικά, ας βουτήξουμε.

---

## Αποθήκευση Εγγράφου Word – Πλήρες Παράδειγμα Java

Παρακάτω βρίσκεται ο πλήρης, έτοιμος‑για‑εκτέλεση κώδικας. Αντιγράψτε τον στο IDE σας, προσαρμόστε τις διαδρομές και πατήστε **Run**.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class ShadowShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the existing document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Create a rectangle shape (the core of add rectangle shape step)
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);
        rectangle.setHeight(50.0);

        // 3️⃣ Apply shadow to shape – how to add shadow in Aspose.Words
        rectangle.getShadow().setVisible(true);
        rectangle.getShadow().setColor(java.awt.Color.BLACK);
        rectangle.getShadow().setBlurRadius(5.0);
        rectangle.getShadow().setOffsetX(4.0);
        rectangle.getShadow().setOffsetY(4.0);
        rectangle.getShadow().setTransparency(0.3);

        // 4️⃣ Insert shape into the first paragraph – how to insert shape
        Paragraph firstPara = doc.getFirstSection().getBody().getParagraphs().get(0);
        firstPara.appendChild(rectangle);

        // 5️⃣ Save the modified document – the final save word document step
        doc.save("YOUR_DIRECTORY/shadow.docx");
        System.out.println("Document saved successfully as shadow.docx");
    }
}
```

**Αναμενόμενο αποτέλεσμα:** Μετά την εκτέλεση του προγράμματος, ανοίξτε το `shadow.docx`. Θα δείτε το αρχικό περιεχόμενο συν ένα μαύρο ορθογώνιο 100 × 50 pt με ήπια σκιά ακριβώς στην αρχή της πρώτης παραγράφου.

---

## Προσθήκη Σχήματος Ορθογωνίου σε Έγγραφο Word

Γιατί να χρησιμοποιήσετε καθόλου σχήμα ορθογωνίου; Σκεφτείτε το ως οπτικό άγκυρο—τέλειο για call‑outs, placeholders ή απλά γραφικά. Στο Aspose.Words η κλάση `Shape` αφαιρεί την πολυπλοκότητα όλων των αντικειμένων σχεδίασης, και το `ShapeType.RECTANGLE` σας δίνει ένα καθαρό κουτί χωρίς περιττές δυσκολίες.

**Βασικά σημεία κατά την προσθήκη σχήματος ορθογωνίου**

- **Οι μονάδες είναι points** (1 pt = 1/72 in). Ρυθμίστε `setWidth`/`setHeight` ώστε να ταιριάζει στη διάταξή σας.  
- Το σχήμα ζει μέσα στο δέντρο κόμβων του εγγράφου, οπότε μπορείτε να το εισάγετε οπουδήποτε επιτρέπεται ένα `Paragraph` ή `Run`.  
- Μπορείτε να μορφοποιήσετε το ορθογώνιο (γέμισμα, χρώμα γραμμής κ.λπ.) πριν εφαρμόσετε τη σκιά.

> **Pro tip:** Αν χρειάζεστε διαφανές γέμισμα, καλέστε `rectangle.getFill().setTransparent(true);`.

---

## Εφαρμογή Σκιάς στο Σχήμα

Οι σκιές προσδίδουν βάθος. Το αντικείμενο `Shadow` που συνδέεται με ένα `Shape` εκθέτει ιδιότητες που αντιστοιχούν άμεσα στις επιλογές του UI του Word.

| Ιδιότητα | Τι κάνει | Τυπική τιμή |
|----------|----------|-------------|
| `setVisible(true)` | Ενεργοποιεί τη σκιά | `true` |
| `setColor(Color.BLACK)` | Χρώμα σκιάς | `Color.BLACK` |
| `setBlurRadius(5.0)` | Απαλότητα άκρων | `5.0` |
| `setOffsetX(4.0)` / `setOffsetY(4.0)` | Οριζόντια/κάθετη μετατόπιση | `4.0` each |
| `setTransparency(0.3)` | Διαφάνεια (0 = αδιαφανές, 1 = αόρατο) | `0.3` |

Όταν ρωτάτε **πώς να εφαρμόσετε σκιά σε σχήμα**, η απάντηση είναι απλώς να ρυθμίσετε αυτές τις έξι ιδιότητες. Μπορείτε να πειραματιστείτε—μεγαλύτερες μετατοπίσεις δημιουργούν αίσθηση «υψωμένης» σκιάς, ενώ μεγαλύτερη ακτίνα θολώματος δίνει πιο απαλό αποτέλεσμα.

> **Κοινό λάθος:** Η παράλειψη του `setVisible(true)` αφήνει το σχήμα χωρίς σκιά, ακόμη και αν έχετε ρυθμίσει άλλες ιδιότητες.

---

## Πώς να Εισάγετε Σχήμα σε Παράγραφο

Η εισαγωγή σχήματος δεν είναι μαγεία· είναι απλώς διαχείριση κόμβων. Η μέθοδος `appendChild` τοποθετεί το σχήμα στο τέλος των παιδικών κόμβων της παραγράφου. Αν χρειάζεστε το σχήμα πριν από το κείμενο, χρησιμοποιήστε `insertBefore` αντί αυτού.

```java
Paragraph para = doc.getFirstSection().getBody().getParagraphs().get(0);
para.insertBefore(rectangle, para.getFirstChild());
```

Αυτή η μικρή αλλαγή απαντά στο **πώς να εισάγετε σχήμα** ακριβώς εκεί που το χρειάζεστε—πριν από τυχόν υπάρχουσες runs, μετά από μια επικεφαλίδα, ή ακόμη και μέσα σε κελί πίνακα (απλώς ανακτήστε πρώτα τον κατάλληλο κόμβο `Cell`).

---

## Εκτέλεση του Κώδικα και Επαλήθευση Αποτελέσματος

1. **Μεταγλώττιση** – `javac -cp "aspose-words-xx.jar" ShadowShapeDemo.java`  
2. **Εκτέλεση** – `java -cp ".;aspose-words-xx.jar" ShadowShapeDemo`  
3. **Άνοιγμα** `shadow.docx` σε Microsoft Word ή LibreOffice. Θα πρέπει να δείτε το ορθογώνιο με ήπια μαύρη σκιά αγκυροβολημένο στην αρχή της πρώτης παραγράφου.

Αν το σχήμα δεν εμφανίζεται, ελέγξτε ξανά:

- Η διαδρομή του αρχείου εισόδου είναι σωστή.  
- Χρησιμοποιείτε πρόσφατη έκδοση του Aspose.Words (το API άλλαξε ελαφρώς πριν από το 20.12).  
- Το έγγραφο έχει τουλάχιστον μία παράγραφο (διαφορετικά το `getParagraphs().get(0)` πετάει IndexOutOfBoundsException).

---

## Συχνές Ερωτήσεις (FAQ)

**Ε: Μπορώ να προσθέσω το σχήμα σε συγκεκριμένη σελίδα;**  
Α: Ναι. Ανακτήστε το επιθυμητό `Section` ή `PageSetup` και εισάγετε το σχήμα σε μια παράγραφο που βρίσκεται σε εκείνη τη σελίδα.

**Ε: Λειτουργεί αυτό με αρχεία .doc;**  
Α: Απόλυτα. Το Aspose.Words αφαιρεί τη μορφή, οπότε ο ίδιος κώδικας **αποθηκεύει ένα έγγραφο Word** είτε είναι `.doc` είτε `.docx`.

**Ε: Τι γίνεται αν χρειαστώ διαφορετικό σχήμα, όπως έλλειψη;**  
Α: Αντικαταστήστε το `ShapeType.RECTANGLE` με `ShapeType.ELLIPSE`. Όλες οι ιδιότητες σκιάς παραμένουν ίδιες.

---

## Συμπέρασμα

Τώρα ξέρετε πώς να **αποθηκεύσετε ένα έγγραφο Word** ενώ **προσθέτετε ένα σχήμα ορθογωνίου**, **εφαρμόζετε σκιά**, και **εισάγετε το σχήμα** στην πρώτη παράγραφο—όλα με λίγες καθαρές γραμμές Java. Αυτό το μοτίβο κλιμακώνεται: αλλάξτε τον τύπο του σχήματος, ρυθμίστε τις παραμέτρους σκιάς, ή τοποθετήστε το σχήμα σε πίνακες και κεφαλίδες. Οι δυνατότητες είναι τόσο ευρείες όσο οι ανάγκες αυτοματοποίησης εγγράφων σας.

Έτοιμοι για την επόμενη πρόκληση; Δοκιμάστε να στρώσετε πολλαπλά σχήματα, να προσθέσετε κείμενο μέσα στο ορθογώνιο, ή να δημιουργήσετε μια πλήρη αναφορά με γραφήματα και υδατογραφήματα. Κάθε μία από αυτές τις εργασίες βασίζεται στα ίδια θεμέλια που καλύφθηκαν εδώ—οπότε είστε ήδη ένα βήμα μπροστά.

Καλή κωδικοποίηση, και εύχομαι η αυτοματοποίηση Word σας να είναι χωρίς σκιές σφαλμάτων!

## Τι Θα Μάθετε Στη Συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετικές θεματικές που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικά παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε επιπλέον δυνατότητες API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Δημιουργία Εγγράφου Word Java – Προσθήκη Σχήματος Ορθογωνίου με Εφέ Σκιάς](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Πώς να αποθηκεύσετε το έγγραφο ως pdf με Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Πώς να αποθηκεύσετε το word ως pcl με Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pcl-format/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}