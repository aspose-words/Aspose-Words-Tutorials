---
category: general
date: 2026-05-04
description: Δημιουργήστε ένα κενό έγγραφο Word σε Java και μάθετε πώς να ορίζετε
  το χρώμα σκιάς, το θόλωμα και την απόσταση για σχήματα – γρήγορος οδηγός.
draft: false
keywords:
- create blank word
- set shadow color
- how to add shadow
- how to set blur
- how to set offset
language: el
og_description: Δημιουργήστε ένα κενό έγγραφο Word σε Java και μάθετε πώς να ορίζετε
  το χρώμα σκιάς, το θόλωμα και την απόσταση για σχήματα. Ακολουθήστε αυτό το βήμα‑βήμα
  οδηγό.
og_title: Δημιουργία κενής λέξης με σκιά σε Java – Πλήρης οδηγός
tags:
- Aspose.Words
- Java
- Document Automation
title: Δημιουργήστε κενή λέξη με σκιά σε Java – Πλήρης οδηγός
url: /el/java/images-shapes/create-blank-word-with-shadow-in-java-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία κενής Word με σκιά σε Java – Πλήρης οδηγός

Ποτέ χρειάστηκε να **δημιουργήσετε κενά αρχεία Word** από κώδικα και να τα κάνετε λίγο πιο εντυπωσιακά; Δεν είστε οι μόνοι. Σε πολλά έργα αναφορών ή δημιουργίας προτύπων, το πρώτο βήμα είναι να δημιουργήσετε ένα κενό έγγραφο Word, έπειτα να προσθέσετε ένα σχήμα με σκιά για να του δώσετε ένα πιο επαγγελματικό αίσθημα.  

Σε αυτό το tutorial θα περάσουμε βήμα‑βήμα από το πώς να δημιουργήσετε ένα κενό έγγραφο Word χρησιμοποιώντας το Aspose.Words for Java, **πώς να προσθέσετε σκιά** σε ένα σχήμα, και τις λεπτομέρειες του **set shadow color**, **πώς να ορίσετε blur**, και **πώς να ορίσετε offset**. Στο τέλος θα έχετε ένα έτοιμο αρχείο `.docx` που εμφανίζει ένα ορθογώνιο με μια ωραία θολή, ημιδιαφανή κόκκινη σκιά.

## Τι θα χρειαστείτε

- **Aspose.Words for Java** (οποιαδήποτε πρόσφατη έκδοση· ο κώδικας λειτουργεί με 23.9+)
- JDK 8 ή νεότερο
- Ένα IDE ή απλός επεξεργαστής κειμένου μαζί με τερματικό
- Βασικές γνώσεις Java—τίποτα περίπλοκο, μόνο η δυνατότητα εκτέλεσης μιας μεθόδου `main`

Δεν απαιτείται επιπλέον ρύθμιση Maven ή Gradle για τη demo· απλώς προσθέστε το JAR του Aspose στο classpath και είστε έτοιμοι.

---

![δημιουργία κενής word με σκιά παράδειγμα](image-placeholder.png){: .center alt="δημιουργία κενής word με σκιά παράδειγμα"}

## Δημιουργία κενής word – Αρχικοποίηση του Document

Το πρώτο βήμα είναι να δημιουργήσετε ένα ολοκαίνουργιο, κενό αρχείο Word. Σκεφτείτε το ως έναν φρέσκο καμβά όπου μπορείτε αργότερα να σχεδιάσετε σχήματα, πίνακες ή κείμενο.

```java
import com.aspose.words.*;

public class ShadowDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank Word document
        Document document = new Document();

        // Step 2: Initialise a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(document);
```

> **Γιατί είναι σημαντικό:** Το `Document` αντιπροσωπεύει ολόκληρο το πακέτο `.docx`. Δημιουργώντας το με τον προεπιλεγμένο κατασκευαστή, ουσιαστικά **δημιουργείτε κενή word** – δεν υπάρχει περιεχόμενο, δεν υπάρχουν ενότητες, μόνο η δομή του αρχείου έτοιμη να γεμίσει.

## Πώς να προσθέσετε σκιά σε ένα σχήμα

Τώρα που έχουμε ένα καθαρό έγγραφο, ας εισάγουμε ένα ορθογώνιο που θα φιλοξενήσει τη σκιά μας. Εδώ αρχίζει η οπτική μαγεία.

```java
        // Step 3: Insert a rectangle shape that will receive a custom shadow
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 150, 80);
```

> **Pro tip:** Η κλήση `insertShape` προσθέτει αυτόματα το σχήμα στην τρέχουσα παράγραφο, οπότε δεν χρειάζεται να διαχειριστείτε τη θέση χειροκίνητα εκτός αν θέλετε απόλυτη τοποθέτηση.

## Ορισμός χρώματος σκιάς – κάντε τη σκιά να ξεχωρίζει

Μια σκιά χωρίς χρώμα είναι απλώς γκρι θόλωση, που μπορεί να φαίνεται επίπεδη. Ορίζοντας το χρώμα της σκιάς μπορείτε να ταιριάξετε το branding ή απλώς να την κάνετε πιο εντυπωσιακή.

```java
        // Step 4a: Make the shadow visible and set its color
        rectangleShape.getShadowFormat().setVisible(true);
        rectangleShape.getShadowFormat().setColor(java.awt.Color.RED); // set shadow color
```

> **Τι συμβαίνει:** Το `ShadowFormat` ελέγχει κάθε οπτικό στοιχείο της σκιάς. Η ενεργοποίηση του `setVisible(true)` ενεργοποιεί το εφέ, και το `setColor` σας επιτρέπει να επιλέξετε οποιοδήποτε `java.awt.Color`. Στο παράδειγμά μας επιλέξαμε κόκκινο για να δείξουμε καθαρά το **set shadow color**.

## Πώς να ορίσετε blur για ήπιο αποτέλεσμα

Μια καθαρή, σκληρά ορισμένη σκιά μπορεί να φαίνεται σκληρή. Η προσθήκη blur μαλακώνει τις άκρες, δίνοντας πιο φυσική εμφάνιση.

```java
        // Step 4b: Define how fuzzy the shadow should be
        rectangleShape.getShadowFormat().setBlur(5.0); // how to set blur
```

> **Γιατί το blur είναι σημαντικό:** Η τιμή του `setBlur` μετράται σε points. Μια τιμή `5.0` δημιουργεί ήπια διάχυση· αυξήστε την για πιο «συνεφιασμένη» σκιά, μειώστε την για πιο έντονη άκρη.

## Πώς να ορίσετε offset – τοποθέτηση της σκιάς

Τα offsets καθορίζουν πού «κάθεται» η σκιά σε σχέση με το σχήμα. Σκεφτείτε τα ως μετατοπίσεις X και Y.

```java
        // Step 4c: Position the shadow horizontally and vertically
        rectangleShape.getShadowFormat().setOffsetX(8.0); // how to set offset (horizontal)
        rectangleShape.getShadowFormat().setOffsetY(8.0); // how to set offset (vertical)
```

> **Εξήγηση offset:** Θετικό X μετακινεί τη σκιά δεξιά, θετικό Y τη μετακινεί κάτω. Παίξτε με αρνητικούς αριθμούς αν θέλετε η σκιά να εμφανίζεται στην αντίθετη πλευρά.

## Λεπτομερής ρύθμιση διαφάνειας

Αν θέλετε η σκιά να είναι λιγότερο κυρίαρχη, προσαρμόστε τη διαφάνειά της. Αυτό το βήμα δεν είναι υποχρεωτικό, αλλά ολοκληρώνει τον έλεγχο της εμφάνισης.

```java
        // Optional: Make the shadow semi‑transparent (30 % transparent)
        rectangleShape.getShadowFormat().setTransparency(0.3);
```

## Αποθήκευση του εγγράφου – δείτε το αποτέλεσμα

Τέλος, γράψτε το έγγραφο στο δίσκο. Θα έχετε ένα `.docx` που μπορείτε να ανοίξετε στο Word, LibreOffice ή οποιονδήποτε προβολέα που υποστηρίζει τη μορφή.

```java
        // Step 5: Save the document with the shaped shadow
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

> **Τι θα δείτε:** Ανοίξτε το `ShadowShape.docx`. Μία σελίδα θα εμφανίσει ένα ορθογώνιο 150 × 80 pt με κόκκινη, ελαφρώς θολή σκιά μετατοπισμένη 8 pt κάτω και δεξιά. Η σκιά είναι 30 % διαφανής, ώστε το ορθογώνιο να παραμένει καθαρά ορατό.

---

## Συχνές ερωτήσεις και ειδικές περιπτώσεις

### Τι γίνεται αν χρειαστώ διαφορετικό σχήμα;

Αντικαταστήστε το `ShapeType.RECTANGLE` με οποιαδήποτε άλλη τιμή enum (`ELLIPSE`, `CLOUD`, `CALLOUT`, κλπ.). Οι ρυθμίσεις σκιάς λειτουργούν ταυτόσημα για όλα τα σχήματα.

### Μπορώ να εφαρμόσω την ίδια σκιά σε πολλά σχήματα χωρίς επανάληψη κώδικα;

Απόλυτα. Δημιουργήστε μια βοηθητική μέθοδο:

```java
private static void applyShadow(Shape shape, java.awt.Color color,
                                double blur, double offsetX, double offsetY,
                                double transparency) {
    shape.getShadowFormat().setVisible(true);
    shape.getShadowFormat().setColor(color);
    shape.getShadowFormat().setBlur(blur);
    shape.getShadowFormat().setOffsetX(offsetX);
    shape.getShadowFormat().setOffsetY(offsetY);
    shape.getShadowFormat().setTransparency(transparency);
}
```

Στη συνέχεια καλέστε `applyShadow(rectangleShape, Color.RED, 5.0, 8.0, 8.0, 0.3);` για οποιοδήποτε σχήμα.

### Λειτουργεί αυτό με παλαιότερες εκδόσεις του Aspose;

Το API `ShadowFormat` είναι σταθερό από την έκδοση 19.8, οπότε θα πρέπει να λειτουργεί με τις περισσότερες πρόσφατες εκδόσεις. Αν χρησιμοποιείτε πολύ παλιά έκδοση, ελέγξτε το Javadoc του `ShadowFormat` για να βεβαιωθείτε για τα ονόματα μεθόδων.

### Πώς να εξάγω σε PDF διατηρώντας τη σκιά;

Απλώς καλέστε `document.save("output.pdf");` μετά τη δημιουργία του σχήματος. Το Aspose.Words αποδίδει σωστά τις σκιές σε PDF, διατηρώντας το blur και τη διαφάνεια.

---

## Ανακεφαλαίωση – δημιουργία κενής word με προσαρμοσμένη σκιά

Ξεκινήσαμε με **create blank word** χρησιμοποιώντας `new Document()`, στη συνέχεια εισάγαμε ένα ορθογώνιο, **set shadow color**, μάθαμε **how to add shadow**, ρυθμίσαμε **how to set blur**, και τέλος προσαρμόσαμε **how to set offset** για την ιδανική θέση. Ο πλήρης, εκτελέσιμος κώδικας βρίσκεται στο παραπάνω απόσπασμα, και το παραγόμενο αρχείο δείχνει το αποτέλεσμα καθαρά.

---

## Τι έπεται;

- **Δοκιμάστε άλλες ιδιότητες σκιάς** όπως `ShadowFormat.setStyle(ShadowStyle.OUTER)` για διαφορετικά οπτικά στυλ.
- **Συνδυάστε πολλαπλά σχήματα** το καθένα με τη δική του σκιά για να δημιουργήσετε σύνθετα διαγράμματα.
- **Προσθέστε κείμενο μέσα στο σχήμα** χρησιμοποιώντας `builder.insertHtml("<b>Hello</b>")` πριν εισάγετε το σχήμα, έπειτα εφαρμόστε την ίδια λογική σκιάς.
- **Εξερευνήστε άλλες επιλογές μορφοποίησης** όπως στυλ γραμμής, χρώμα γεμίσματος ή διαβαθμίσεις—το Aspose.Words προσφέρει πλούσιο API για όλα αυτά.

Πειραματιστείτε με την ακτίνα blur, τα offsets ή τα χρώματα μέχρι η σκιά να ταιριάζει ακριβώς με το σχεδιαστικό σας ύφος. Καλό προγραμματισμό, και ας είναι τα παραγόμενα Word αρχεία σας πάντα λίγο πιο επαγγελματικά!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}