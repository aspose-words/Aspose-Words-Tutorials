---
category: general
date: 2026-07-20
description: πώς να εισάγετε διάγραμμα πίτας στο Word με το Aspose.Words. Μάθετε πώς
  να προσθέσετε το ποσοστό ετικέτας δεδομένων και να εμφανίσετε τα ποσοστά στο διάγραμμα
  για επαγγελματικά έγγραφα.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert pie chart
- add data label percent
- display percentages on chart
- add pie chart to word
- show percent on pie chart
language: el
lastmod: 2026-07-20
og_description: πώς να εισαγάγετε διάγραμμα πίτας στο Word χρησιμοποιώντας το Aspose.Words.
  Αυτός ο οδηγός δείχνει πώς να προσθέσετε το ποσοστό ετικέτας δεδομένων και να εμφανίσετε
  τα ποσοστά στο διάγραμμα με λίγες μόνο γραμμές.
og_image_alt: Screenshot showing how to insert pie chart in Word with percentage labels
og_title: πώς να εισαγάγετε διάγραμμα πίτας στο Word – γρήγορος οδηγός
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: how to insert pie chart in Word with Aspose.Words. Learn to add data
    label percent and display percentages on chart for professional documents.
  headline: how to insert pie chart in Word – add data label percent
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart
- Word Automation
title: πώς να εισάγετε διάγραμμα πίτας στο Word – προσθήκη ποσοστού ετικέτας δεδομένων
url: /el/java/using-document-elements/how-to-insert-pie-chart-in-word-add-data-label-percent/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# πώς να εισάγετε διάγραμμα πίτας στο Word – προσθήκη ποσοστού ετικέτας δεδομένων

Έχετε αναρωτηθεί ποτέ **πώς να εισάγετε διάγραμμα πίτας** σε ένα έγγραφο Word χωρίς να παλεύετε με το UI; Δεν είστε μόνοι. Σε πολλές περιπτώσεις αναφοράς χρειάζεται να *προσθέσετε διάγραμμα πίτας στο Word* και, πιο σημαντικό, **να εμφανίσετε το ποσοστό στο διάγραμμα πίτας** ώστε οι αναγνώστες να κατανοήσουν άμεσα την κατανομή των δεδομένων.

Σε αυτό το tutorial θα περάσουμε βήμα‑βήμα τη διαδικασία χρησιμοποιώντας το Aspose.Words for Java. Στο τέλος θα ξέρετε ακριβώς πώς να **προσθέσετε ποσοστό ετικέτας δεδομένων**, **να εμφανίσετε τα ποσοστά στο διάγραμμα**, και να αποκτήσετε ένα επαγγελματικό διάγραμμα πίτας που φαίνεται σωστό από την πρώτη στιγμή. Χωρίς πρόσθετα plugins, χωρίς χειροκίνητες προσαρμογές — μόνο καθαρός κώδικας που μπορείτε να ενσωματώσετε σε οποιοδήποτε project.

---

## Προαπαιτούμενα

- Java 17 (ή νεότερη) – η τρέχουσα έκδοση LTS που υποστηρίζει το Aspose.Words.
- Aspose.Words for Java 24.x (η πιο πρόσφατη τη στιγμή της συγγραφής, Ιούλιος 2026).
- Μια βασική ρύθμιση Maven ή Gradle για να κατεβάσετε τη βιβλιοθήκη.
- Ένα IDE που προτιμάτε (IntelliJ IDEA, Eclipse, VS Code… όποιο σας βολεύει).

Αν έχετε ήδη όλα αυτά, τέλεια — ας ξεκινήσουμε.

---

## Βήμα 1: Ρύθμιση του project και εισαγωγή της βιβλιοθήκης

Πρώτα, προσθέστε την εξάρτηση Aspose.Words στο `pom.xml` (Maven) ή στο `build.gradle` (Gradle). Αυτό σας δίνει πρόσβαση στις κλάσεις `Document`, `DocumentBuilder` και στα charts.

```xml
<!-- Maven -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

```gradle
// Gradle
implementation 'com.aspose:aspose-words:24.9'
```

> **Pro tip:** Κρατήστε τον αριθμό έκδοσης ενημερωμένο· οι νεότερες κυκλοφορίες συχνά προσθέτουν διορθώσεις σχετικές με τα charts που κάνουν το **display percentages on chart** πιο αξιόπιστο.

---

## Βήμα 2: Δημιουργία νέου εγγράφου Word και builder

Ο builder είναι το πολυεργαλείο σας για την εισαγωγή περιεχομένου. Εδώ δημιουργούμε ένα νέο έγγραφο και συνδέουμε έναν `DocumentBuilder` σε αυτό.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank document and a builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Γιατί χρειαζόμαστε έναν builder; Απομονώνει τις χαμηλού επιπέδου δομές OpenXML, επιτρέποντάς μας να εστιάσουμε στο *τι* θέλουμε — όπως **add pie chart to word** — αντί για το *πώς* φαίνεται το XML.

---

## Βήμα 3: Εισαγωγή του διαγράμματος πίτας

Τώρα έρχεται ο πυρήνας του **how to insert pie chart**. Ζητάμε από τον builder να τοποθετήσει ένα διάγραμμα πίτας συγκεκριμένου μεγέθους. Οι διαστάσεις είναι σε points (1 pt ≈ 1/72 in).

```java
        // Step 3: Insert a pie chart – width 400pt, height 300pt
        Chart pieChart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);
```

Σε αυτό το σημείο το διάγραμμα είναι κενό, αλλά το placeholder βρίσκεται ήδη στο έγγραφο. Μόλις **add pie chart to word** προγραμματιστικά.

---

## Βήμα 4: Συμπλήρωση του διαγράμματος με δεδομένα

Ένα διάγραμμα πίτας χρειάζεται τουλάχιστον μία σειρά τιμών. Ας του δώσουμε δείγμα δεδομένων που αντιπροσωπεύει το μερίδιο αγοράς.

```java
        // Step 4: Add a data series with sample values
        ChartSeries series = pieChart.getSeries().get(0);
        series.getDataPoints().add(30); // Product A
        series.getDataPoints().add(45); // Product B
        series.getDataPoints().add(25); // Product C
```

Αν χρειαστείτε πολλαπλές σειρές (στοιβαγμένες πίτες, donuts κ.λπ.) μπορείτε να καλέσετε `pieChart.getSeries().add()` και να επαναλάβετε τα βήματα. Η ίδια λογική ισχύει όταν θέλετε **display percentages on chart** για κάθε φέτα.

---

## Βήμα 5: **add data label percent** – εμφάνιση των ποσοστών στις φέτες

Αυτό είναι το κομμάτι που ξεχνάει η πλειονότητα των προγραμματιστών: η διαμόρφωση των ετικετών δεδομένων ώστε να εμφανίζουν ποσοστά. Χωρίς αυτό, το διάγραμμα δείχνει μόνο ακατέργαστους αριθμούς, που μπορεί να είναι ασαφείς.

```java
        // Step 5: Enable percentage labels on the first series
        series.getDataLabel().setShowPercent(true);
```

Η κλήση `setShowPercent(true)` λέει στο Aspose.Words να αποδώσει την ετικέτα ως “30 %”, “45 %”, κ.λπ. Αυτό είναι ακριβώς το **show percent on pie chart** χωρίς επιπλέον δουλειά μορφοποίησης.

---

## Βήμα 6: Αποθήκευση του εγγράφου

Τέλος, γράψτε το έγγραφο στο δίσκο. Μπορείτε να επιλέξετε `.docx`, `.pdf` ή ακόμη και `.html`. Για αυτόν τον οδηγό θα μείνουμε στο σύγχρονο φορμάτ `.docx`.

```java
        // Step 6: Save the result
        doc.save("PieChartDemo.docx");
    }
}
```

Τρέξτε το πρόγραμμα, ανοίξτε το `PieChartDemo.docx` και θα δείτε ένα καλοσχεδιασμένο διάγραμμα πίτας με ετικέτες ποσοστών σε κάθε φέτα.

---

## Αναμενόμενο αποτέλεσμα

Παρακάτω υπάρχει ένα στιγμιότυπο του παραγόμενου αρχείου Word. Παρατηρήστε πώς κάθε φέτα εμφανίζει το μερίδιό της ως ποσοστό — ακριβώς αυτό που θέλαμε όταν ορίσαμε **add data label percent**.

![Screenshot of a Word document containing a pie chart with percentage labels](/images/pie-chart-percent.png){.center width=600px alt="Στιγμιότυπο ενός εγγράφου Word που περιέχει διάγραμμα πίτας με ετικέτες ποσοστών"}

*Το κείμενο alt περιλαμβάνει τη βασική λέξη‑κλειδί, ικανοποιώντας τόσο το SEO όσο και την προσβασιμότητα.*

---

## Συχνές ερωτήσεις & αντιμετώπιση ειδικών περιπτώσεων

| Ερώτηση | Απάντηση |
|----------|--------|
| **Μπορώ να αλλάξω τη γραμματοσειρά των ετικετών ποσοστών;** | Ναι. Αφού ενεργοποιήσετε `setShowPercent(true)`, ανακτήστε το αντικείμενο `DataLabel` και προσαρμόστε την ιδιότητα `Font` (`dataLabel.getFont().setSize(10);`). |
| **Τι γίνεται αν χρειαστώ διάγραμμα donut αντί για πίτα;** | Αντικαταστήστε το `ChartType.PIE` με `ChartType.DOUGHNUT` στην κλήση `insertChart`. Η ίδια λογική **add data label percent** λειτουργεί. |
| **Εμφανίζονται σωστά τα ποσοστά σε παλαιότερες εκδόσεις Word (2007‑2010);** | Το Aspose.Words γράφει το υποκείμενο XML με τρόπο ανεξάρτητο από την έκδοση, έτσι τα ποσοστά εμφανίζονται σε οποιοδήποτε Word που υποστηρίζει charts (2007+). |
| **Πώς προσθέτω τίτλο στο διάγραμμα;** | Χρησιμοποιήστε `pieChart.getTitle().setText("Market Share");` πριν αποθηκεύσετε. |
| **Μπορώ να εισάγω το διάγραμμα σε συγκεκριμένη παράγραφο ή κελί πίνακα;** | Απόλυτα. Μετακινήστε τον `DocumentBuilder` στην επιθυμητή θέση (`builder.moveToParagraph(index, true);` ή `builder.moveToCell(table, row, column, true);`) πριν καλέσετε `insertChart`. |

---

## Συμβουλές και κόλπα από την πράξη

- **Pro tip:** Αν σκοπεύετε να δημιουργήσετε πολλά διαγράμματα σε βρόχο, επαναχρησιμοποιήστε ένα μόνο αντικείμενο `DocumentBuilder`; μειώνει την κατανάλωση μνήμης.
- **Προσοχή σε:** Πολύ μικρές φέτες (< 2 %). Το Aspose.Words μπορεί να παραλείψει την ετικέτα για να αποφύγει την ακαταστασία· μπορείτε να την εξαναγκάσετε με `dataLabel.setShowLabel(true);`.
- **Σημείωση απόδοσης:** Η απόδοση των charts είναι απαιτητική σε CPU. Για μαζική δημιουργία αναφορών, σκεφτείτε πολυνηματικότητα, αλλά βεβαιωθείτε ότι κάθε νήμα εργάζεται σε δικό του αντικείμενο `Document`.
- **Έλεγχος έκδοσης:** Η μέθοδος `setShowPercent` εισήχθη στο Aspose.Words 22.8. Αν χρησιμοποιείτε παλαιότερη έκδοση, αναβαθμίστε ή υπολογίστε τα ποσοστά χειροκίνητα και ορίστε τα ως προσαρμοσμένες ετικέτες.

---

## Ανακεφαλαίωση

Καλύψαμε **πώς να εισάγετε διάγραμμα πίτας** σε έγγραφο Word χρησιμοποιώντας το Aspose.Words, σας δείξαμε πώς να **προσθέσετε ποσοστό ετικέτας δεδομένων**, και παρουσιάσαμε τον πιο εύκολο τρόπο για **να εμφανίσετε τα ποσοστά στο διάγραμμα**. Με λίγες γραμμές Java μπορείτε να **add pie chart to word** και **show percent on pie chart**, μετατρέποντας ακατέργαστους αριθμούς σε άμεσα κατανοητές οπτικές παραστάσεις.

---

## Τι ακολουθεί;

- Πειραματιστείτε με άλλους τύπους διαγραμμάτων (`BAR`, `LINE`, `AREA`) και δείτε πώς η ίδια λογική **add data label percent** εφαρμόζεται.
- Συνδυάστε charts με πίνακες για πιο πλούσιες αναφορές — το Aspose.Words το κάνει εύκολο τοποθετώντας ένα chart δίπλα σε έναν πίνακα δεδομένων.
- Εξερευνήστε την εξαγωγή του ίδιου εγγράφου σε PDF ή HTML για να δείτε πώς τα ποσοστά αποδίδονται σε διαφορετικές μορφές.

Αλλάξτε τις διαστάσεις, τα χρώματα ή την πηγή δεδομένων (π.χ. ερώτημα βάσης) και δείτε τις αναφορές Word σας να ζωντανεύουν. Αν αντιμετωπίσετε πρόβλημα, αφήστε ένα σχόλιο παρακάτω — καλή δημιουργία charts!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να κατακτήσετε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στα δικά σας projects.

- [Εισαγωγή Διάγραμμα Στήλης στο Word χρησιμοποιώντας Aspose.Words για .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Εισαγωγή Διάγραμμα Περιοχής σε Έγγραφο Word | Aspose.Words για .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Εισαγωγή Διάγραμμα Φούσκας σε Word χρησιμοποιώντας Aspose.Words για .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}