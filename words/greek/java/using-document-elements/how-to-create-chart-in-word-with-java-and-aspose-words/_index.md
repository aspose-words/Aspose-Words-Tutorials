---
category: general
date: 2026-09-24
description: Μάθετε πώς να δημιουργείτε γράφημα στο Word χρησιμοποιώντας Java, να
  εισάγετε ένα ακτινικό γράφημα και να αποθηκεύσετε το έγγραφο ως docx με το Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create chart in word
- save document as docx
- add chart to word
- create word document java
- insert radial chart
language: el
lastmod: 2026-09-24
og_description: Δημιουργήστε γράφημα στο Word με Java και Aspose.Words. Αυτό το σεμινάριο
  σας δείχνει πώς να προσθέσετε ένα ακτινικό γράφημα, να προσαρμόσετε τα δεδομένα
  και να αποθηκεύσετε το έγγραφο ως docx.
og_image_alt: Radial chart inserted in a Word document using Java code
og_title: Δημιουργία γραφήματος στο Word με Java – οδηγός βήμα‑προς‑βήμα
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Learn how to create chart in Word using Java, insert a radial chart,
    and save document as docx with Aspose.Words.
  headline: How to create chart in Word with Java and Aspose.Words
  type: TechArticle
- description: Learn how to create chart in Word using Java, insert a radial chart,
    and save document as docx with Aspose.Words.
  name: How to create chart in Word with Java and Aspose.Words
  steps:
  - name: You should see a single page with a centered radial chart.
    text: You should see a single page with a centered radial chart.
  - name: If you added series data, the chart displays four slices labeled Q1‑Q4.
    text: If you added series data, the chart displays four slices labeled Q1‑Q4.
  - name: Right‑click the chart → **Edit Data** to confirm the underlying data table.
    text: Right‑click the chart → **Edit Data** to confirm the underlying data table.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- Chart
- DOCX
title: Πώς να δημιουργήσετε γράφημα στο Word με Java και Aspose.Words
url: /el/java/using-document-elements/how-to-create-chart-in-word-with-java-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να δημιουργήσετε γράφημα στο Word με Java και Aspose.Words

Αν χρειάζεστε **create chart in Word** από μια εφαρμογή Java, αυτός ο οδηγός σας καθοδηγεί μέσα από τη διαδικασία. Θα δείτε πώς να προσθέσετε ένα radial chart, προαιρετικά να γεμίσετε τις σειρές του, και τελικά **save document as docx** χρησιμοποιώντας τη βιβλιοθήκη Aspose.Words for Java.

Η δημιουργία οπτικών δεδομένων μέσα σε ένα αρχείο Word είναι συχνή απαίτηση για αναφορές, τιμολόγηση ή αυτόματη δημιουργία εγγράφων. Στο τέλος αυτού του tutorial θα μπορείτε να δημιουργήσετε **create word document java** έργα που **add chart to Word** αρχεία χωρίς καμία χειροκίνητη επεξεργασία.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε:

* Java Development Kit (JDK) 8 ή νεότερο.
* Maven ή Gradle για διαχείριση εξαρτήσεων.
* IDE όπως IntelliJ IDEA, Eclipse ή VS Code.
* Έγκυρη άδεια Aspose.Words for Java (η δωρεάν δοκιμή λειτουργεί για ανάπτυξη).

Αυτά τα εργαλεία παρέχουν τη βάση για τα παραδείγματα κώδικα που ακολουθούν.

## Βήμα 1: Ρύθμιση του έργου Maven

Δημιουργήστε ένα νέο έργο Maven (ή ενημερώστε ένα υπάρχον) και προσθέστε την εξάρτηση Aspose.Words στο `pom.xml`:

```xml
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word‑chart‑demo</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

Η εκτέλεση του `mvn clean install` κατεβάζει τη βιβλιοθήκη και κάνει τις κλάσεις όπως `Document`, `DocumentBuilder` και `ChartType` διαθέσιμες στο classpath.

> **Pro tip:** Κρατήστε την έκδοση της βιβλιοθήκης ενημερωμένη. Οι νέες εκδόσεις προσθέτουν τύπους γραφημάτων και βελτιώνουν την απόδοση απόδοσης.

## Βήμα 2: Δημιουργία νέου εγγράφου Word

Το πρώτο προγραμματιστικό βήμα για **create chart in Word** είναι η δημιουργία ενός κενό `Document`. Αυτό το αντικείμενο αντιπροσωπεύει ολόκληρο το πακέτο `.docx`.

```java
import com.aspose.words.*;

public class RadialChartDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a blank Word document
        Document doc = new Document();

        // Step 2.2: Obtain a DocumentBuilder to insert content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Το `DocumentBuilder` λειτουργεί σαν κέρσορας· γνωρίζει το τρέχον σημείο εισαγωγής και παρέχει μεθόδους για κείμενο, πίνακες και γραφήματα. Σε αυτό το σημείο έχετε **created word document java** στυλ – έναν καθαρό καμβά έτοιμο για περιεχόμενο.

## Βήμα 3: Εισαγωγή radial chart

Το Aspose.Words υποστηρίζει πολλούς τύπους γραφημάτων. Για **insert radial chart**, καλέστε `insertChart` με `ChartType.RADIAL`. Η μέθοδος απαιτεί επίσης το πλάτος και το ύψος σε points (1 point ≈ 1/72 inch).

```java
        // Step 3: Insert a radial chart (400 × 300 points)
        Shape chart = builder.insertChart(ChartType.RADIAL, 400, 300);
```

Το επιστρεφόμενο αντικείμενο `Shape` περιέχει το υποκείμενο αντικείμενο γραφήματος. Το γράφημα αυτόματα αποδίδει τις κλίμακες για διάταξη 24.9°, η οποία είναι η προεπιλογή για radial charts στο Word.

### Γιατί να χρησιμοποιήσετε radial chart;

Ένα radial chart οπτικοποιεί δεδομένα που τυλίγονται γύρω από έναν κύκλο, καθιστώντας το ιδανικό για την εμφάνιση κυκλικών προτύπων (π.χ. μηνιαίες πωλήσεις, μετρικές ρολογιού). Το ίδιο API μπορεί να εισάγει bar, pie ή line charts, αλλά ο radial τύπος προσθέτει μια χαρακτηριστική εμφάνιση χωρίς επιπλέον κώδικα μορφοποίησης.

## Βήμα 4: (Προαιρετικό) Συμπλήρωση των δεδομένων σειράς του γραφήματος

Αν θέλετε το γράφημα να εμφανίζει πραγματικές τιμές, πρέπει να προσθέσετε σειρές και σημεία. Το παρακάτω απόσπασμα προσθέτει μια μοναδική σειρά με τρία σημεία δεδομένων:

```java
        // Optional: add data to the chart
        Chart chartObj = chart.getChart();
        chartObj.getSeries().clear(); // remove any default series

        // Create a new series
        ChartSeries series = chartObj.getSeries().add("Quarterly Revenue");

        // Add data points (value, category)
        series.getDataPoints().add(15000, "Q1");
        series.getDataPoints().add(21000, "Q2");
        series.getDataPoints().add(18000, "Q3");
        series.getDataPoints().add(24000, "Q4");
```

Μπορείτε να επαναλάβετε τις κλήσεις `add` για όσες τιμές χρειάζεστε. Το Aspose.Words ενημερώνει αυτόματα την οπτική αναπαράσταση, ώστε να βλέπετε τις radial φέτες να προσαρμόζονται στις νέες τιμές.

> **Common question:** *What if I need to bind data from a database?*  
> Ανακτήστε τις γραμμές, κάντε βρόχο πάνω τους και καλέστε `series.getDataPoints().add(value, label)` μέσα στον βρόχο. Το API είναι thread‑safe και λειτουργεί με οποιοδήποτε `ResultSet` παρέχετε.

## Βήμα 5: Αποθήκευση του εγγράφου ως DOCX

Όταν το γράφημα είναι έτοιμο, το τελικό βήμα είναι να **save document as docx**. Η μέθοδος `save` καθορίζει τη μορφή εξόδου από την επέκταση του αρχείου.

```java
        // Step 5: Persist the document
        String outputPath = "output/RadialChartDemo.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

Το παραγόμενο αρχείο περιέχει ένα πλήρως λειτουργικό radial chart που μπορεί να ανοιχθεί σε Microsoft Word, LibreOffice ή οποιονδήποτε προβολέα που υποστηρίζει τη μορφή DOCX. Επειδή χρησιμοποιήσαμε την επέκταση `.docx`, το Word αποθηκεύει το αρχείο σε μορφή Open XML, η οποία είναι το σύγχρονο πρότυπο για έγγραφα Word.

### Επαλήθευση του αποτελέσματος

Ανοίξτε το `RadialChartDemo.docx` στο Word:

1. Θα πρέπει να δείτε μια μοναδική σελίδα με ένα κεντραρισμένο radial chart.
2. Αν προσθέσατε δεδομένα σειράς, το γράφημα εμφανίζει τέσσερις φέτες με ετικέτες Q1‑Q4.
3. Δεξί‑κλικ στο γράφημα → **Edit Data** για να επιβεβαιώσετε τον υποκείμενο πίνακα δεδομένων.

Αν το γράφημα εμφανίζεται κενό, ελέγξτε ξανά ότι κάλεσατε `chart.getChart()` πριν προσθέσετε τις σειρές και βεβαιωθείτε ότι ο κέρσορας του document builder είναι τοποθετημένος στο σημείο που θέλετε το γράφημα.

## Βήμα 6: Προχωρημένες συμβουλές για εργασία με γραφήματα

| Συμβουλή | Γιατί είναι σημαντική |
|-----|----------------|
| **Set chart style** – `chart.getChart().setStyle(ChartStyle.STYLE_PRESET_5);` | Βελτιώνει τη συνοχή της εμφάνισης χωρίς να χρειάζεται χειροκίνητη μορφοποίηση κάθε στοιχείου. |
| **Resize after insertion** – `chart.setWidth(500); chart.setHeight(350);` | Σας επιτρέπει να ρυθμίσετε ακριβώς το μέγεθος του γραφήματος βάσει της διάταξης της σελίδας. |
| **Add a title** – `chart.getChart().getTitle().setText("Revenue Overview");` | Δίνει πλαίσιο στους αναγνώστες που βλέπουν το έγγραφο χωρίς το περιβάλλον κείμενο. |
| **Export to PDF** – `doc.save("RadialChartDemo.pdf");` | Χρήσιμο όταν χρειάζεστε μια μη επεξεργάσιμη έκδοση για διανομή. |
| **License handling** – `License lic = new License(); lic.setLicense("Aspose.Words.lic");` | Αποτρέπει το υδατογράφημα αξιολόγησης σε παραγωγικές εκδόσεις. |

Αυτές οι βελτιώσεις είναι προαιρετικές αλλά δείχνουν πώς μπορείτε να προσαρμόσετε περαιτέρω το γράφημα αφού έχετε μάθει να **add chart to Word**.

## Συμπέρασμα

Τώρα έχετε ένα πλήρες, αυτόνομο παράδειγμα που δείχνει πώς να **create chart in Word** χρησιμοποιώντας Java, **insert radial chart**, προαιρετικά να το γεμίσετε με δεδομένα, και **save document as docx**. Το ίδιο μοτίβο λειτουργεί για άλλους τύπους γραφημάτων, ώστε να μπορείτε να επεκτείνετε αυτόν τον οδηγό σε bar, line ή pie charts όπως χρειάζεται.

Στη συνέχεια μπορείτε να εξερευνήσετε:

* **create word document java** έργα που συνδυάζουν πίνακες, εικόνες και πολλαπλά γραφήματα.
* Χρήση του **save document as docx** μαζί με το **save document as pdf** για αναφορές πολλαπλών μορφών.
* Προσθήκη δυναμικών δεδομένων από REST APIs ή βάσεις δεδομένων στα γραφήματά σας.

Νιώστε ελεύθεροι να πειραματιστείτε με τις επιλογές στυλ, τις διαστάσεις του γραφήματος και τις πηγές δεδομένων. Καλό κώδικα!

## Τι πρέπει να μάθετε στη συνέχεια;

Οι παρακάτω εκπαιδευτικές οδηγίες καλύπτουν στενά σχετιζόμενα θέματα που βασίζονται στις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικά παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Πώς να δημιουργήσετε column chart χρησιμοποιώντας Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Δημιουργία κενής Word εγγράφου με Aspose.Words – Οδηγός βήμα‑βήμα](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [Δημιουργία Word Document Java – Προσθήκη Rectangle Shape με Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}