---
category: general
date: 2026-07-20
description: Δημιουργήστε ένα κενό έγγραφο Word σε Java χρησιμοποιώντας το Aspose.Words.
  Μάθετε πώς να δημιουργήσετε ομάδα, να εισάγετε σχήμα ορθογωνίου και να ενσωματώσετε
  εικόνα στο σχήμα.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to create group
- add image word document
- insert rectangle shape
- embed image in shape
language: el
lastmod: 2026-07-20
og_description: Δημιουργήστε κενό έγγραφο Word σε Java με το Aspose.Words. Αυτός ο
  οδηγός δείχνει πώς να δημιουργήσετε ομάδα, να εισάγετε σχήμα ορθογωνίου και να ενσωματώσετε
  εικόνα στο σχήμα για δυναμικά αρχεία Word.
og_image_alt: Screenshot of a blank Word document containing a grouped shape with
  a rectangle and an embedded image
og_title: Δημιουργήστε κενό έγγραφο Word με ομαδοποιημένο σχήμα – Οδηγός Java
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Create blank word document in Java using Aspose.Words. Learn how to
    create group, insert rectangle shape, and embed image in shape.
  headline: Create blank word document with grouped shape – Java guide
  type: TechArticle
- description: Create blank word document in Java using Aspose.Words. Learn how to
    create group, insert rectangle shape, and embed image in shape.
  name: Create blank word document with grouped shape – Java guide
  steps:
  - name: '`output.docx` appears in the project folder.'
    text: '`output.docx` appears in the project folder.'
  - name: Opening the file shows a single page with a grouped shape.
    text: Opening the file shows a single page with a grouped shape.
  - name: Inside the group, the rectangle is positioned at the top‑left, and the image
      sits directly below it.
    text: Inside the group, the rectangle is positioned at the top‑left, and the image
      sits directly below it.
  - name: Selecting the group in Word highlights both child objects, confirming they
      are truly grouped.
    text: Selecting the group in Word highlights both child objects, confirming they
      are truly grouped.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word Automation
title: Δημιουργία κενού εγγράφου Word με ομαδοποιημένο σχήμα – Οδηγός Java
url: /el/java/images-shapes/create-blank-word-document-with-grouped-shape-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία κενής εγγράφου Word με ομαδοποιημένο σχήμα – Οδηγός Java

Έχετε αναρωτηθεί ποτέ πώς να **δημιουργήσετε κενό έγγραφο Word** που περιέχει ήδη ένα ωραία ομαδοποιημένο σχήμα; Ίσως δημιουργείτε ένα πρότυπο αναφοράς ή χρειάζεστε ένα placeholder για λογότυπο και λεζάντα. Σε κάθε περίπτωση, το πρόβλημα είναι κοινό: ξεκινάτε με ένα κενό αρχείο, προσθέτετε μια ομάδα, τοποθετείτε ένα ορθογώνιο μέσα και, τέλος, ενσωματώνετε μια εικόνα—όλα προγραμματιστικά.

Σε αυτόν τον οδηγό θα περάσουμε βήμα‑βήμα από ένα πλήρες, έτοιμο‑για‑εκτέλεση παράδειγμα Java που κάνει ακριβώς αυτό. Θα μάθετε **πώς να δημιουργήσετε ομάδα**, **πώς να εισάγετε σχήμα ορθογωνίου** και **πώς να προσθέσετε εικόνα σε έγγραφο Word** μέσα στην ίδια ομάδα. Στο τέλος θα έχετε ένα αρχείο Word που μοιάζει με ένα επαγγελματικό πρότυπο, έτοιμο για περαιτέρω προσαρμογές.

> **Τι θα πάρετε:** μια πλήρως λειτουργική κλάση Java, εξηγήσεις βήμα‑βήμα, συμβουλές για τη διαχείριση διαδρομών αρχείων και μια προεπισκόπηση του αναμενόμενου αποτελέσματος. Δεν απαιτείται εξωτερική τεκμηρίωση—όλα όσα χρειάζεστε είναι εδώ.

---

## Δημιουργία κενής εγγράφου Word – Επισκόπηση βήμα‑βήμα

Το πρώτο που χρειαζόμαστε είναι ένα πραγματικά κενό αρχείο Word. Το Aspose.Words το κάνει εύκολο: απλώς δημιουργήστε ένα αντικείμενο της κλάσης `Document` με τον προεπιλεγμένο κατασκευαστή. Αυτό σας δίνει έναν καθαρό καμβά, ισοδύναμο με το άνοιγμα του Word και την επιλογή **New → Blank document**.

```java
import com.aspose.words.*;

public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a blank Word document
        Document doc = new Document();               // <-- blank document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Γιατί να ξεκινήσετε με κενό έγγραφο;**  
> Ένα κενό έγγραφο εγγυάται ότι δεν υπάρχουν κρυφά στυλ ή ενότητες που να παρεμβαίνουν στα σχήματα που θα προσθέσετε αργότερα. Επίσης διατηρεί το μέγεθος του αρχείου στο ελάχιστο, κάτι χρήσιμο όταν δημιουργείτε δεκάδες αρχεία σε μια παρτίδα.

---

## Πώς να δημιουργήσετε ομάδα και να προσθέσετε σχήματα

Μια **ομαδοποιημένη μορφή** (group shape) είναι ουσιαστικά ένας container που μπορεί να κρατήσει πολλαπλά παιδικά σχήματα—σκεφτείτε το ως φάκελο για αντικείμενα σχεδίασης. Με την ομαδοποίηση, μπορείτε να μετακινήσετε, να αλλάξετε μέγεθος ή να περιστρέψετε ολόκληρο το σύνολο με μία εντολή.

```java
        // 2️⃣ Insert a group shape 200x200 points
        GroupShape group = builder.insertGroupShape(200.0, 200.0);
```

Η μέθοδος `insertGroupShape` επιστρέφει ένα αντικείμενο `GroupShape` που θα χρησιμοποιήσουμε ως γονέα για το ορθογώνιο και την εικόνα. Το μέγεθος εκφράζεται σε points (1 point = 1/72 ίντσα), έτσι 200 points δίνουν περίπου ένα κουτί 2,78 × 2,78 ίντσες.

> **Pro tip:** Αν θέλετε η ομάδα να είναι διαφανής, ορίστε `group.setFillColor(Color.getWhite());` μετά τη δημιουργία.

Τώρα που υπάρχει η ομάδα, πρέπει να πούμε στον builder πού να τοποθετήσει τα επόμενα σχήματα. Ο κέρσορας του builder πρέπει να βρίσκεται μέσα στην πρώτη παράγραφο της ομάδας.

```java
        // Move the cursor to the first paragraph of the group
        builder.moveTo(group.getFirstParagraph());
```

---

## Εισαγωγή σχήματος ορθογωνίου μέσα στην ομάδα

Ένα ορθογώνιο χρησιμοποιείται συχνά ως placeholder για κείμενο ή ως οπτική ένδειξη. Η προσθήκη του ως **πρώτο παιδί** της ομάδας εξασφαλίζει ότι βρίσκεται πίσω από τυχόν επόμενες εικόνες.

```java
        // 3️⃣ Insert a rectangle (100x50 points) as the first child
        builder.insertShape(ShapeType.RECTANGLE, 100.0, 50.0);
```

Το ορθογώνιο κληρονομεί το σύστημα συντεταγμένων της ομάδας, έτσι το μέγεθός του 100 × 50 points θα κεντραριστεί εξ ορισμού. Μπορείτε να το μορφοποιήσετε περαιτέρω—να προσθέσετε περίγραμμα, να αλλάξετε το χρώμα γεμίσματος ή να εφαρμόσετε σκιά—πρόσβαση στο επιστρεφόμενο αντικείμενο `Shape`.

```java
        // Optional styling (commented out for brevity)
        // Shape rect = builder.getCurrentShape();
        // rect.setFillColor(Color.getLightGray());
        // rect.setStrokeColor(Color.getBlack());
```

---

## Προσθήκη εικόνας σε έγγραφο Word – ενσωμάτωση εικόνας σε σχήμα

Τώρα το διασκεδαστικό κομμάτι: **ενσωμάτωση εικόνας σε σχήμα**. Θα εισάγουμε μια εικόνα JPEG ως δεύτερο παιδί της ίδιας ομάδας. Επειδή ο κέρσορας παραμένει μέσα στην ομάδα, η εικόνα θα γίνει αυτόματα παιδί του κόμβου.

```java
        // 4️⃣ Insert an image (make sure the path is correct)
        builder.insertImage("sample.jpg");   // <-- replace with your image path
```

Αν το αρχείο εικόνας δεν βρεθεί, το Aspose.Words ρίχνει `FileNotFoundException`. Για να το αποφύγετε, τοποθετήστε το `sample.jpg` στον φάκελο εργασίας του έργου ή χρησιμοποιήστε απόλυτη διαδρομή.

> **Τι αν χρειάζεστε διαφορετική μορφή εικόνας;**  
> Το Aspose.Words υποστηρίζει PNG, BMP, GIF, TIFF και ακόμη SVG. Απλώς αλλάξτε την επέκταση του αρχείου και η βιβλιοθήκη θα διαχειριστεί τη μετατροπή.

---

## Αποθήκευση του εγγράφου και προβολή του αποτελέσματος

Τέλος, αποθηκεύουμε το έγγραφο που βρίσκεται στη μνήμη στο δίσκο. Το παραγόμενο `.docx` θα περιέχει μία σελίδα με μια ομαδοποιημένη μορφή που κρατά τόσο το ορθογώνιο όσο και την εικόνα.

```java
        // 5️⃣ Save the document to verify the output
        doc.save("output.docx");
    }
}
```

Όταν ανοίξετε το `output.docx` στο Microsoft Word, θα δείτε μια ομάδα 200 × 200 points στην επάνω‑αριστερή γωνία. Μέσα στην ομάδα, ένα ανοιχτό γκρι ορθογώνιο βρίσκεται στην κορυφή, και ακριβώς κάτω από αυτό εμφανίζεται η εικόνα που καθορίσατε, τέλεια ευθυγραμμισμένη.

![Grouped shape example](grouped-shape.png){:alt="Στιγμιότυπο οθόνης ενός κενό εγγράφου Word με ομαδοποιημένο σχήμα που περιέχει ένα ορθογώνιο και μια ενσωματωμένη εικόνα"}

---

## Συνηθισμένες παραλλαγές και διαχείριση edge‑case

| Σενάριο | Τι να αλλάξετε | Γιατί είναι σημαντικό |
|----------|----------------|------------------------|
| **Διαφορετικό μέγεθος ομάδας** | Προσαρμόστε τις παραμέτρους του `insertGroupShape(width, height)` | Μεγαλύτερες ομάδες μπορούν να φιλοξενήσουν πιο σύνθετες διατάξεις. |
| **Πολλές εικόνες** | Καλέστε `builder.insertImage()` επανειλημμένα μετά από μετακίνηση στην παράγραφο της ομάδας κάθε φορά | Κάθε κλήση προσθέτει νέο παιδί· μπορείτε επίσης να τα τοποθετήσετε με `Shape.setLeft()` / `setTop()`. |
| **Δυναμικές διαδρομές εικόνων** | Χρησιμοποιήστε `String.format("images/%s.jpg", imageName)` | Κάνει τον κώδικα επαναχρησιμοποιήσιμο για επεξεργασία παρτίδας. |
| **Αποθήκευση ως PDF** | Αντικαταστήστε `doc.save("output.pdf")` | Το Aspose.Words μπορεί να μετατρέπει άμεσα, επιτρέποντάς σας να δημιουργήσετε PDF απευθείας. |
| **Περιστροφή της ομάδας** | `group.setRotation(45);` | Χρήσιμο για διακοσμητικά υδατογραφήματα ή στυλιζαρισμένα κεφαλίδες. |

---

## Αναμενόμενο αποτέλεσμα και επαλήθευση

Μετά την εκτέλεση της κλάσης:

1. Το `output.docx` εμφανίζεται στον φάκελο του έργου.  
2. Το άνοιγμα του αρχείου δείχνει μία σελίδα με ομαδοποιημένο σχήμα.  
3. Μέσα στην ομάδα, το ορθογώνιο είναι τοποθετημένο στην επάνω‑αριστερή γωνία, και η εικόνα βρίσκεται ακριβώς κάτω από αυτό.  
4. Η επιλογή της ομάδας στο Word επισημαίνει και τα δύο παιδικά αντικείμενα, επιβεβαιώνοντας ότι είναι πραγματικά ομαδοποιημένα.

Αν κάποιο από αυτά τα βήματα αποτύχει, ελέγξτε ξανά τη διαδρομή της εικόνας και βεβαιωθείτε ότι το JAR του Aspose.Words βρίσκεται στο classpath.

---

## Συμπέρασμα

Τώρα γνωρίζετε **πώς να δημιουργήσετε κενό έγγραφο Word** και να το εμπλουτίσετε με μια ομαδοποιημένη μορφή που περιέχει ένα ορθογώνιο και μια ενσωματωμένη εικόνα. Με την εξοικείωση σας με **πώς να δημιουργήσετε ομάδα**, **πώς να εισάγετε σχήμα ορθογωνίου** και **πώς να προσθέσετε εικόνα σε έγγραφο Word**, μπορείτε να χτίσετε πολύπλοκα πρότυπα Word εξ ολοκλήρου με κώδικα—χωρίς χειροκίνητη παρέμβαση.

Έτοιμοι για την επόμενη πρόκληση; Δοκιμάστε να προσθέσετε πλαίσια κειμένου μέσα στην ίδια ομάδα ή πειραματιστείτε με διαφορετικά στυλ σχημάτων για να ταιριάζουν με την εταιρική σας ταυτότητα. Μπορείτε ακόμη να δημιουργήσετε μια ολόκληρη βιβλιοθήκη αναφορών όπου κάθε έγγραφο ξεκινά με αυτή τη διάταξη.

Καλή προγραμματιστική δουλειά, και μη διστάσετε να μοιραστείτε τις δικές σας παραλλαγές στα σχόλια παρακάτω!

## Τι πρέπει να μάθετε στη συνέχεια;

Οι παρακάτω οδηγοί καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Create PDF Documents with Aspose.Words for Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}