---
category: general
date: 2026-09-11
description: Πώς να επεξεργαστείτε ένα γράφημα σε έγγραφο Word με Java – μάθετε πώς
  να ενημερώνετε τις ρυθμίσεις του γραφήματος, να ενεργοποιείτε τις γραμμές πλέγματος,
  να αλλάζετε τις επιλογές του γραφήματος και να αποθηκεύετε το ενημερωμένο έγγραφο.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit chart
- update chart settings
- save updated document
- change chart options
- enable chart gridlines
language: el
lastmod: 2026-09-11
og_description: Πώς να επεξεργαστείτε ένα γράφημα σε ένα έγγραφο Word με τη Java.
  Ακολουθήστε αυτόν τον οδηγό για να ενημερώσετε τις ρυθμίσεις του γραφήματος, να
  ενεργοποιήσετε τις γραμμές πλέγματος, να αλλάξετε τις επιλογές του γραφήματος και
  να αποθηκεύσετε το ενημερωμένο έγγραφο.
og_image_alt: Screenshot of a Word document showing a chart with gridlines enabled
og_title: Πώς να επεξεργαστείτε το γράφημα σε ένα έγγραφο Word χρησιμοποιώντας Java
  – πλήρης οδηγός
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: How to edit chart in a Word document with Java – learn to update chart
    settings, enable chart gridlines, change chart options, and save the updated document.
  headline: How to edit chart in a Word document using Java
  type: TechArticle
- description: How to edit chart in a Word document with Java – learn to update chart
    settings, enable chart gridlines, change chart options, and save the updated document.
  name: How to edit chart in a Word document using Java
  steps:
  - name: Expected result
    text: 'When you open `output.docx`:'
  - name: What if the document has no chart?
    text: 'Attempting to cast a non‑chart shape will throw a `ClassCastException`.
      Guard against this by checking the shape type:'
  - name: How to edit a specific chart instead of the first one?
    text: 'Iterate through `shapes` and match a known title or an alternative identifier:'
  - name: Can I disable gridlines again later?
    text: 'Yes, simply set the property to `false`:'
  - name: Does this work with `.doc` (binary) files?
    text: Aspose.Words abstracts the file format, so the same code works for `.doc`
      and `.docx`. However, some newer chart features (like graduations) are only
      stored in the OOXML format, so you’ll see the effect only when saving as `.docx`.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart manipulation
title: Πώς να επεξεργαστείτε ένα γράφημα σε έγγραφο Word χρησιμοποιώντας τη Java
url: /el/java/using-document-elements/how-to-edit-chart-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να επεξεργαστείτε ένα γράφημα σε έγγραφο Word χρησιμοποιώντας Java

Αν χρειάζεστε **how to edit chart** σε αρχείο Word, αυτός ο οδηγός σας δείχνει τα ακριβή βήματα. Θα μάθετε πώς να ενημερώνετε τις ρυθμίσεις του γραφήματος, να ενεργοποιείτε τις γραμμές πλέγματος του γραφήματος, να αλλάζετε τις επιλογές του γραφήματος και τελικά **να αποθηκεύσετε το ενημερωμένο έγγραφο** χωρίς να χάσετε καμία μορφοποίηση.

Η εργασία με γραφήματα προγραμματιστικά συχνά φαίνεται σαν λειτουργία μαύρου κουτιού, ειδικά όταν θέλετε να ρυθμίσετε οπτικές λεπτομέρειες όπως οι διαβάσεις ή οι γραμμές πλέγματος. Αυτό το tutorial καλύπτει όλα όσα χρειάζεστε, από τη φόρτωση του εγγράφου μέχρι την αποθήκευση των αλλαγών. Δεν απαιτούνται εξωτερικά εργαλεία—μόνο η βιβλιοθήκη Aspose.Words for Java (έκδοση 24.9 ή νεότερη).

Με το τέλος αυτού του άρθρου θα μπορείτε να:

* Φορτώσετε ένα αρχείο `.docx` που περιέχει ένα γράφημα.
* Εντοπίσετε το σχήμα του γραφήματος και τροποποιήσετε τις ιδιότητές του.
* Ενεργοποιήσετε τις γραμμές πλέγματος του γραφήματος (graduations) και προσαρμόσετε άλλες επιλογές.
* **Αποθηκεύσετε το ενημερωμένο έγγραφο** σε νέο αρχείο.

## Προαπαιτούμενα

* Java 17 ή νεότερη εγκατεστημένη στο μηχάνημά σας.  
* Maven ή Gradle για διαχείριση εξαρτήσεων.  
* Aspose.Words for Java 24.9+ (η έκδοση που εισήγαγε τη μέθοδο `setShowGraduations`).  
* Ένα έγγραφο Word (`input.docx`) που ήδη περιέχει τουλάχιστον ένα γράφημα.

Αν δεν είστε εξοικειωμένοι με το Aspose.Words, σκεφτείτε το ως ένα πλήρες API που σας επιτρέπει να διαβάζετε, να τροποποιείτε και να γράφετε έγγραφα Word προγραμματιστικά—παρόμοιο με το πώς θα χειριζόσασταν ένα DOM σε έναν web browser.

## Βήμα 1: Ρυθμίστε το έργο και εισάγετε τη βιβλιοθήκη

Δημιουργήστε ένα νέο Maven project ή προσθέστε την εξάρτηση σε ένα υπάρχον:

```xml
<!-- pom.xml -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

> **Pro tip:** Χρησιμοποιήστε την πιο πρόσφατη σταθερή έκδοση για να διασφαλίσετε ότι έχετε τη μέθοδο `setShowGraduations`. Οι παλαιότερες εκδόσεις δεν θα μεταγλωττιστούν.

## Βήμα 2: Φορτώστε το έγγραφο Word που περιέχει ένα γράφημα

Η πρώτη ενέργεια σε οποιαδήποτε ροή εργασίας **how to edit chart** είναι η φόρτωση του αρχείου προέλευσης. Το Aspose.Words αντιπροσωπεύει ολόκληρο το έγγραφο με την κλάση `Document`.

```java
import com.aspose.words.*;

public class ChartEditor {
    public static void main(String[] args) throws Exception {
        // Replace with the actual path to your input file
        String inputPath = "YOUR_DIRECTORY/input.docx";

        // Load the document into memory
        Document doc = new Document(inputPath);
```

Το αντικείμενο `Document` σας δίνει πρόσβαση σε κάθε κόμβο μέσα στο αρχείο, συμπεριλαμβανομένων σχημάτων, πινάκων και παραγράφων.  

## Βήμα 3: Εντοπίστε το πρώτο σχήμα γραφήματος στο έγγραφο

Τα γραφήματα αποθηκεύονται ως κόμβοι `Shape` των οποίων ο renderer είναι ένα `Chart`. Για να επεξεργαστείτε ένα γράφημα πρέπει πρώτα να ανακτήσετε αυτόν τον κόμβο.

```java
        // Find all shape nodes (including charts)
        NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);

        // Assume the first shape is a chart; adjust the index if needed
        Shape chartShape = (Shape) shapes.get(0);

        // Cast the shape renderer to Chart
        Chart chart = (Chart) chartShape.getChart();
```

Αν το έγγραφο περιέχει πολλαπλά γραφήματα, επαναλάβετε πάνω από τα `shapes` και ελέγξτε `chartShape.getChart() != null` πριν κάνετε cast. Αυτό αποτρέπει το `ClassCastException` και διασφαλίζει ότι **αλλάζετε τις επιλογές του γραφήματος** μόνο σε έγκυρα αντικείμενα γραφήματος.

## Βήμα 4: Ενεργοποίηση των γραμμών πλέγματος του γραφήματος (graduations) – μια νέα ιδιότητα στην έκδοση 24.9

Η ιδιότητα `setShowGraduations` εναλλάσσει την ορατότητα των μικρών γραμμών πλέγματος στον άξονα τιμών. Η ενεργοποίησή τους συχνά βελτιώνει την αναγνωσιμότητα για πυκνά σύνολα δεδομένων.

```java
        // Turn on gridlines (graduations) for the value axis
        chart.setShowGraduations(true);
```

> **Why this matters:** Οι γραμμές πλέγματος παρέχουν στους θεατές μια οπτική αναφορά για κάθε δεδομένο, καθιστώντας τις τάσεις πιο εύκολες στην ανίχνευση. Η προεπιλογή είναι `false`, επομένως πρέπει να τις ενεργοποιήσετε ρητά όταν απαιτείται.

Μπορείτε επίσης να προσαρμόσετε άλλες πτυχές, όπως τις κύριες γραμμές πλέγματος, τους τίτλους των αξόνων ή τη θέση του υπομνήματος. Παρακάτω υπάρχει ένα παράδειγμα αλλαγής του τίτλου του γραφήματος και της θέσης του υπομνήματος—και τα δύο μέρος του **change chart options**.

```java
        // Change the chart title
        chart.getTitle().setText("Sales Overview 2026");
        chart.getTitle().setOverlay(false);

        // Move the legend to the bottom
        chart.getLegend().setPosition(LegendPosition.BOTTOM);
```

## Βήμα 5: Αποθηκεύστε το έγγραφο με τις ενημερωμένες ρυθμίσεις του γραφήματος

Αφού τροποποιήσετε το γράφημα, διατηρήστε τις αλλαγές. Αυτό το βήμα ολοκληρώνει τη φάση **save updated document**.

```java
        // Replace with the desired output path
        String outputPath = "YOUR_DIRECTORY/output.docx";

        // Save the modified document
        doc.save(outputPath);
        System.out.println("Chart edited and document saved to: " + outputPath);
    }
}
```

Η εκτέλεση του προγράμματος θα δημιουργήσει το `output.docx` όπου το γράφημα εμφανίζει τώρα γραμμές πλέγματος, έναν νέο τίτλο και ένα μετακινημένο υπόμνημα. Ανοίξτε το αρχείο στο Microsoft Word για να επαληθεύσετε τις οπτικές αλλαγές.

## Πλήρης κώδικας πηγής (εκτελέσιμος)

```java
import com.aspose.words.*;

public class ChartEditor {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the Word document that contains a chart
        String inputPath = "YOUR_DIRECTORY/input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Locate the first chart shape in the document
        NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);
        Shape chartShape = (Shape) shapes.get(0);
        Chart chart = (Chart) chartShape.getChart();

        // 3️⃣ Enable chart gridlines (graduations)
        chart.setShowGraduations(true);

        // 4️⃣ Change chart options (title and legend)
        chart.getTitle().setText("Sales Overview 2026");
        chart.getTitle().setOverlay(false);
        chart.getLegend().setPosition(LegendPosition.BOTTOM);

        // 5️⃣ Save the document with the updated chart settings
        String outputPath = "YOUR_DIRECTORY/output.docx";
        doc.save(outputPath);

        System.out.println("Chart edited and document saved to: " + outputPath);
    }
}
```

### Αναμενόμενο αποτέλεσμα

Όταν ανοίξετε το `output.docx`:

* Το γράφημα εμφανίζει μικρές γραμμές πλέγματος στον άξονα τιμών.  
* Ο τίτλος γράφει **“Sales Overview 2026”**.  
* Το υπόμνημα εμφανίζεται στο κάτω μέρος του γραφήματος.

Αν το αρχικό γράφημα είχε ήδη γραμμές πλέγματος, η οπτική εμφάνιση παραμένει αμετάβλητη, επιβεβαιώνοντας ότι ο κώδικας είναι **idempotent**.

## Συχνές ερωτήσεις και διαχείριση ειδικών περιπτώσεων

### Τι γίνεται αν το έγγραφο δεν έχει γράφημα;

Η προσπάθεια cast ενός σχήματος που δεν είναι γράφημα θα προκαλέσει `ClassCastException`. Προστατέψτε εναντίον αυτού ελέγχοντας τον τύπο του σχήματος:

```java
if (chartShape.getShapeType() == ShapeType.CHART) {
    Chart chart = (Chart) chartShape.getChart();
    // proceed with modifications
}
```

### Πώς να επεξεργαστείτε ένα συγκεκριμένο γράφημα αντί για το πρώτο;

Επαναλάβετε μέσα από τα `shapes` και ταιριάξτε έναν γνωστό τίτλο ή έναν εναλλακτικό αναγνωριστικό:

```java
for (Node node : shapes) {
    Shape shape = (Shape) node;
    if (shape.getShapeType() == ShapeType.CHART) {
        Chart c = (Chart) shape.getChart();
        if ("Revenue Q1".equals(c.getTitle().getText())) {
            // modify this chart
        }
    }
}
```

### Μπορώ να απενεργοποιήσω ξανά τις γραμμές πλέγματος αργότερα;

Ναι, απλώς ορίστε την ιδιότητα σε `false`:

```java
chart.setShowGraduations(false);
```

### Λειτουργεί αυτό με αρχεία `.doc` (δυαδικά);

Το Aspose.Words αφαιρεί την εξάρτηση από τη μορφή αρχείου, έτσι ο ίδιος κώδικας λειτουργεί για `.doc` και `.docx`. Ωστόσο, ορισμένα νεότερα χαρακτηριστικά γραφήματος (όπως τα graduations) αποθηκεύονται μόνο στη μορφή OOXML, οπότε θα δείτε το αποτέλεσμα μόνο όταν αποθηκεύετε ως `.docx`.

## Συμβουλές για κώδικα έτοιμο για παραγωγή

* **Επικυρώστε τις διαδρομές εισόδου** – χρησιμοποιήστε `Files.exists(Paths.get(inputPath))` πριν τη φόρτωση.  
* **Τυλίξτε τις κλήσεις API** σε μπλοκ try‑catch για να εμφανίσετε τις λεπτομέρειες του `Exception`, ειδικά όταν εργάζεστε με κατεστραμμένα έγγραφα.  
* **Αποδεσμεύστε πόρους** – παρόλο που το Aspose.Words διαχειρίζεται τη μνήμη, η κλήση `doc.close()` (ή η χρήση try‑with‑resources αν είναι διαθέσιμη) μπορεί να ελευθερώσει τους εγγενείς χειριστές νωρίτερα.  
* **Έλεγχος έκδοσης** – βεβαιωθείτε ότι η έκδοση της βιβλιοθήκης χρόνου εκτέλεσης είναι ≥ 24.9 πριν καλέσετε τη `setShowGraduations`. Μπορείτε να ερωτήσετε το `License.getVersion()` αν χρειάζεστε προγραμματικό έλεγχο.

## Συμπέρασμα

Τώρα γνωρίζετε **how to edit chart** αντικείμενα σε έγγραφο Word χρησιμοποιώντας Java. Η διαδικασία—φόρτωση του εγγράφου, εντοπισμός του γραφήματος, ενεργοποίηση των γραμμών πλέγματος του γραφήματος, αλλαγή των επιλογών του γραφήματος, και **αποθήκευση του ενημερωμένου εγγράφου**—καλύπτει τα πιο κοινά σενάρια για προγραμματιστική διαχείριση γραφημάτων.  

Από εδώ μπορείτε να εξερευνήσετε πρόσθετες προσαρμογές όπως η αλλαγή χρωμάτων σειρών δεδομένων, η εφαρμογή στυλ γραφήματος ή η εξαγωγή του γραφήματος ως εικόνα. Κάθε μία από αυτές τις εργασίες ακολουθεί το ίδιο μοτίβο: ανακτήστε το στιγμιότυπο `Chart`, προσαρμόστε τις ιδιότητές του, και **αποθηκεύστε το ενημερωμένο έγγραφο**.

Καλή προγραμματιστική, και μη διστάσετε να πειραματιστείτε με άλλες ρυθμίσεις γραφήματος για να ταιριάζουν στις ανάγκες αναφοράς σας!

## Τι Θα Πρέπει Να Μάθετε Στη Σύντομη Μελλοντική;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που βασίζονται στις τεχνικές που επιδείχθηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετα χαρακτηριστικά του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Πώς να δημιουργήσετε γράφημα στήλης χρησιμοποιώντας Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Πώς να αποθηκεύσετε έγγραφο ως pdf με Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Ορισμός προεπιλεγμένων επιλογών για ετικέτες δεδομένων σε γράφημα](/words/english/net/programming-with-charts/default-options-for-data-labels/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}