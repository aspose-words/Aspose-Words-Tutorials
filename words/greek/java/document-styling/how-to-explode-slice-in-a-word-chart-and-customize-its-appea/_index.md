---
category: general
date: 2026-10-04
description: Μάθετε πώς να αποσπάτε ένα τμήμα σε γράφημα του Word, να αποσπάτε τμήμα
  πίτας και να αλλάζετε το μέγεθος του δακτυλιοειδούς γραφήματος με ένα βήμα‑βήμα
  παράδειγμα Java.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to explode slice
- modify chart in word
- explode pie chart slice
- change doughnut chart size
- customize pie chart word
language: el
lastmod: 2026-10-04
og_description: Πώς να «εξαπολύσετε» ένα τμήμα σε γράφημα του Word και να προσαρμόσετε
  γραφήματα τύπου πίτας ή δακτυλίου με Java. Ακολουθήστε το πλήρες παράδειγμα για
  να τροποποιήσετε το γράφημα στο Word.
og_image_alt: Screenshot showing an exploded pie chart slice inside a Word document
og_title: Πώς να αποσπάσετε το τμήμα σε διάγραμμα Word – πλήρης οδηγός Java
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to explode slice in a Word chart, explode pie chart slice
    and change doughnut chart size with a step‑by‑step Java example.
  headline: How to explode slice in a Word chart and customize its appearance
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart manipulation
title: Πώς να αποσπάσετε ένα τμήμα σε γράφημα του Word και να προσαρμόσετε την εμφάνισή
  του
url: /el/java/document-styling/how-to-explode-slice-in-a-word-chart-and-customize-its-appea/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να εκτοξεύσετε τμήμα σε γράφημα Word και να προσαρμόσετε την εμφάνισή του

Αν χρειάζεστε **how to explode slice** σε ένα γράφημα Word, αυτός ο οδηγός σας δείχνει ακριβώς πώς. Είτε ετοιμάζετε μια παρουσίαση πωλήσεων είτε μια οικονομική αναφορά, η εκτόξευση ενός τμήματος πίτας ή η προσαρμογή της τρύπας του doughnut μπορεί να κάνει τα πιο σημαντικά δεδομένα να ξεχωρίζουν. Στις επόμενες ενότητες θα μάθετε επίσης πώς να **modify chart in Word**, **explode pie chart slice**, **change doughnut chart size**, και **customize pie chart word** έγγραφα χρησιμοποιώντας το Aspose.Words for Java.

Θα ολοκληρώσετε αυτό το tutorial με ένα πλήρες, έτοιμο‑για‑εκτέλεση πρόγραμμα Java που φορτώνει ένα αρχείο `.docx`, εκτοξεύει το πρώτο τμήμα ενός γραφήματος πίτας, αλλάζει το μέγεθος της τρύπας του doughnut και αποθηκεύει το αποτέλεσμα. Δεν απαιτούνται εξωτερικά scripts ή χειροκίνητη επεξεργασία.

## Prerequisites

- Java 17 ή νεότερη έκδοση εγκατεστημένη στο μηχάνημα ανάπτυξής σας.  
- Maven 3.6+ (ή Gradle) για διαχείριση εξαρτήσεων.  
- Βιβλιοθήκη Aspose.Words for Java (η δωρεάν δοκιμαστική έκδοση λειτουργεί για ανάπτυξη).  
- Ένα έγγραφο Word (`input.docx`) που περιέχει τουλάχιστον ένα γράφημα (πίτα ή doughnut).

## Step 1: Add Aspose.Words to your project

Αν χρησιμοποιείτε Maven, προσθέστε την ακόλουθη εξάρτηση στο `pom.xml` σας:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Replace with the latest version -->
</dependency>
```

Για Gradle, τοποθετήστε αυτό στο `build.gradle`:

```groovy
implementation 'com.aspose:aspose-words:24.9'
```

> **Pro tip:** Διατηρήστε την έκδοση της βιβλιοθήκης σας ενημερωμένη· οι νεότερες εκδόσεις προσθέτουν υποστήριξη για επιπλέον τύπους γραφημάτων και βελτιώνουν την απόδοση.

## Step 2: Load the Word document that contains a chart

```java
import com.aspose.words.*;

public class ChartExploder {
    public static void main(String[] args) throws Exception {
        // Path to the source .docx file
        String inputPath = "YOUR_DIRECTORY/input.docx";

        // Load the document – this step is required before any chart manipulation.
        Document doc = new Document(inputPath);
```

**Why this matters:** Η φόρτωση του εγγράφου δημιουργεί μια αναπαράσταση στη μνήμη που μπορεί να διασχίσει το Aspose.Words. Χωρίς αυτό το αντικείμενο δεν μπορείτε να έχετε πρόσβαση στους κόμβους του γραφήματος.

## Step 3: Retrieve the first chart in the document

```java
        // Locate the first Shape node that contains a chart.
        Shape chartShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);

        // Cast the Shape to a Chart object.
        Chart chart = chartShape.getChart();
```

> **Explanation:** Το `NodeType.SHAPE` καλύπτει όλα τα αντικείμενα σχεδίασης, συμπεριλαμβανομένων των γραφημάτων. Το όρισμα `true` λέει στο Aspose να ψάξει αναδρομικά, εξασφαλίζοντας ότι το πρώτο γράφημα θα βρεθεί ακόμη και αν είναι ενσωματωμένο σε πίνακα.

## Step 4: Explode the first slice of a pie chart

```java
        // Verify the chart type before exploding.
        if (chart.getChartType() == ChartType.PIE) {
            // Explode the first series (slice) by 20 points.
            chart.getSeries().get(0).setExplosion(20);
        } else {
            System.out.println("The first chart is not a pie chart; explosion skipped.");
        }
```

**How it works:** Η μέθοδος `setExplosion` δέχεται μια αριθμητική τιμή που καθορίζει πόσο μακριά θα μετακινηθεί το τμήμα από το κέντρο. Μια τιμή `20` είναι οπτικά εμφανής χωρίς να διασπά τη διάταξη του γραφήματος.

## Step 5: Adjust the doughnut hole size for a doughnut chart

```java
        // If the chart is a doughnut, change the hole size.
        if (chart.getChartType() == ChartType.DOUGHNUT) {
            // Set the doughnut hole size to 40% of the chart radius.
            chart.setDoughnutHoleSize(40);
        } else {
            System.out.println("The first chart is not a doughnut chart; hole size unchanged.");
        }
```

**Why this helps:** Μια μεγαλύτερη τρύπα doughnut μπορεί να βελτιώσει την αναγνωσιμότητα όταν έχετε πολλά σημεία δεδομένων. Η μέθοδος `setDoughnutHoleSize` αναμένει ένα ποσοστό (0‑100).

## Step 6: Save the modified document

```java
        // Path for the output document
        String outputPath = "YOUR_DIRECTORY/PieChart.docx";

        // Save the changes – the file now contains the exploded slice and updated doughnut size.
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

### Expected output

- Το πρώτο τμήμα του πρώτου γραφήματος πίτας μετατοπίζεται προς τα έξω, κάνοντάς το να ξεχωρίζει.
- Αν το γράφημα είναι doughnut, η κεντρική τρύπα επεκτείνεται στο 40 % της ακτίνας του γραφήματος.
- Το προκύπτον αρχείο `PieChart.docx` μπορεί να ανοιχθεί στο Microsoft Word, LibreOffice ή σε οποιονδήποτε συμβατό προβολέα, εμφανίζοντας τις οπτικές αλλαγές που εφαρμόσατε προγραμματιστικά.

## Full, runnable example

Παρακάτω βρίσκεται ολόκληρο το πρόγραμμα σε ένα μπλοκ. Αντιγράψτε το στο `ChartExploder.java`, προσαρμόστε τις διαδρομές αρχείων και εκτελέστε το με `mvn compile exec:java` (ή τη ρύθμιση εκτέλεσης του IDE σας).

```java
import com.aspose.words.*;

public class ChartExploder {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the source document
        String inputPath = "YOUR_DIRECTORY/input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Find the first chart shape
        Shape chartShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        if (chartShape == null) {
            System.out.println("No chart found in the document.");
            return;
        }

        // 3️⃣ Cast to Chart
        Chart chart = chartShape.getChart();

        // 4️⃣ Explode the first slice if it is a pie chart
        if (chart.getChartType() == ChartType.PIE) {
            chart.getSeries().get(0).setExplosion(20);
            System.out.println("Exploded first slice of the pie chart.");
        }

        // 5️⃣ Change doughnut hole size if it is a doughnut chart
        if (chart.getChartType() == ChartType.DOUGHNUT) {
            chart.setDoughnutHoleSize(40);
            System.out.println("Set doughnut hole size to 40%.");
        }

        // 6️⃣ Save the modified document
        String outputPath = "YOUR_DIRECTORY/PieChart.docx";
        doc.save(outputPath);
        System.out.println("Modified document saved as " + outputPath);
    }
}
```

Η εκτέλεση αυτού του κώδικα θα **modify chart in Word**, **explode pie chart slice**, και **change doughnut chart size** αυτόματα.

## Common questions and edge cases

| Question | Answer |
|----------|--------|
| *Τι γίνεται αν το έγγραφο περιέχει πολλαπλά γραφήματα;* | Το παράδειγμα στοχεύει το **πρώτο** γράφημα (`NodeType.SHAPE, 0`). Για να εργαστείτε με άλλα γραφήματα, αλλάξτε το δείκτη ή επαναλάβετε μέσω `doc.getChildNodes(NodeType.SHAPE, true)` και φιλτράρετε με `shape.getChart() != null`. |
| *Μπορώ να εκτοξεύσω τμήμα διαφορετικό από το πρώτο;* | Ναι. Πρόσβαση στη ζητούμενη σειρά μέσω `chart.getSeries().get(seriesIndex)` και κλήση της `setExplosion(value)`. Οι δείκτες είναι μηδενικής βάσης. |
| *Λειτουργεί αυτό με αρχεία Word 2007‑2021;* | Το Aspose.Words υποστηρίζει `.doc`, `.docx`, `.dot` και `.dotx`. Ο ίδιος κώδικας λειτουργεί σε όλες τις εκδόσεις επειδή η βιβλιοθήκη αφαιρεί την εξάρτηση από τη μορφή αρχείου. |
| *Τι γίνεται αν το γράφημα είναι ραβδόγραμμα ή γραμμικό γράφημα;* | Οι μέθοδοι `setExplosion` και `setDoughnutHoleSize` ισχύουν μόνο για γραφήματα τύπου πίτας. Ο κώδικας παραλείπει με ασφάλεια αυτές τις λειτουργίες όταν ο τύπος του γραφήματος διαφέρει. |
| *Χρειάζομαι άδεια για το Aspose.Words;* | Μια δωρεάν άδεια αξιολόγησης αφαιρεί το όριο των 30 ημερών αλλά προσθέτει υδατογράφημα. Για παραγωγή, αγοράστε άδεια για να αφαιρέσετε το υδατογράφημα και να ξεκλειδώσετε πλήρη λειτουργικότητα. |

## Συμπέρασμα

Τώρα γνωρίζετε **how to explode slice** σε ένα γράφημα Word, πώς να **modify chart in Word**, και πώς να **change doughnut chart size** χρησιμοποιώντας το Aspose.Words for Java. Το πλήρες παράδειγμα δείχνει τη συνολική ροή εργασίας — από τη φόρτωση ενός εγγράφου, τον εντοπισμό του γραφήματος, την εφαρμογή οπτικών προσαρμογών, μέχρι την αποθήκευση του αποτελέσματος — ώστε να μπορείτε να ενσωματώσετε αυτά τα βήματα σε οποιοδήποτε pipeline αναφοράς ή δημιουργίας εγγράφων.

**Επόμενα βήματα**

- Εξερευνήστε άλλες προσαρμογές γραφημάτων όπως αλλαγή χρωμάτων, προσθήκη ετικετών δεδομένων ή αλλαγή τύπου γραφήματος (`chart.setChartType(ChartType.BAR_CLUSTERED)`).
- Συνδυάστε αυτή τη λογική με το Aspose.PDF για να δημιουργήσετε μια έκδοση PDF της ίδιας αναφοράς.
- Αυτοματοποιήστε τη διαδικασία για μια δέσμη εγγράφων επαναλαμβάνοντας τα αρχεία σε έναν φάκελο.

Μη διστάσετε να πειραματιστείτε με διαφορετικές τιμές εκτόξευσης ή ποσοστά τρύπας doughnut για να ταιριάζουν με τις οδηγίες σχεδίασής σας. Καλή προγραμματιστική!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικά παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Hide Chart Axis In A Word Document](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Insert Bubble Chart In Word Document](/words/english/net/programming-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}