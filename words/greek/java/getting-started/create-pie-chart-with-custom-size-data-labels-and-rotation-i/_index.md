---
category: general
date: 2026-11-22
description: Δημιουργήστε διάγραμμα πίτας σε Java και μάθετε πώς να ορίσετε το μέγεθος
  του διαγράμματος, να προσθέσετε ετικέτες δεδομένων, να εμφανίσετε ποσοστά και να
  περιστρέψετε το πρώτο τμήμα για σαφή οπτική επίδραση.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- set chart size
- show percentages pie chart
- add data labels pie chart
- rotate pie chart slice
language: el
lastmod: 2026-11-22
og_description: Δημιουργήστε διάγραμμα πίτας σε Java, ορίστε το μέγεθος του διαγράμματος,
  εμφανίστε τα ποσοστά στις ετικέτες δεδομένων και περιστρέψτε το πρώτο τμήμα—όλα
  σε ένα ενιαίο, εκτελέσιμο παράδειγμα.
og_image_alt: Screenshot of a created pie chart showing custom size, percentage labels,
  and a rotated first slice
og_title: Δημιουργήστε διάγραμμα πίτας με προσαρμοσμένο μέγεθος, ετικέτες και περιστροφή
  σε Java
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Create pie chart in Java and learn how to set chart size, add data
    labels, show percentages, and rotate the first slice for clear visual impact.
  headline: Create pie chart with custom size, data labels, and rotation in Java
  type: TechArticle
- description: Create pie chart in Java and learn how to set chart size, add data
    labels, show percentages, and rotate the first slice for clear visual impact.
  name: Create pie chart with custom size, data labels, and rotation in Java
  steps:
  - name: Why each step matters
    text: '| Step | Purpose | How it relates to the keywords | |------|---------|--------------------------------|
      | **Insert chart** | **Create pie chart** – the core object that will render
      the visual. | Directly satisfies the *create pie chart* requirement. | | **Set
      dimensions** | The `addChart(..., 400, 3'
  - name: 1. Insert a pie chart and set chart size
    text: '```java IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50,
      400, 300); ```'
  - name: 2. Populate the chart with data
    text: The demo adds three categories and a single series. Replace the hard‑coded
      numbers with data from a database, CSV, or user input as needed.
  - name: 3. Show percentages on each slice
    text: '```java series.getDataLabelFormat().setShowPercentage(true); ```'
  - name: 4. Add detailed data labels
    text: '```java series.getDataLabelFormat().setShowCategoryName(false); series.getDataLabelFormat().setShowLeaderLines(false);
      ```'
  - name: 5. Rotate the first slice
    text: '```java chart.setFirstSliceAngle(45); ```'
  - name: 6. Save and view the result
    text: 'Running the program produces `output/PieChartDemo.pptx`. Open it in PowerPoint
      or any compatible viewer to see the final pie chart:'
  - name: What’s next?
    text: '* Explore other chart types (Bar, Line, Area) using the same `ChartType`
      enum. * Combine multiple charts on a single slide for dashboards. * Export charts
      to PNG or SVG for use in web applications.'
  type: HowTo
tags:
- Java
- charts
- Aspose.Slides
- data‑visualization
title: Δημιουργία διαγράμματος πίτας με προσαρμοσμένο μέγεθος, ετικέτες δεδομένων
  και περιστροφή σε Java
url: /el/java/getting-started/create-pie-chart-with-custom-size-data-labels-and-rotation-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία διαγράμματος πίτας με προσαρμοσμένο μέγεθος, ετικέτες δεδομένων και περιστροφή σε Java

Αν χρειάζεστε **create pie chart** σε Java, αυτός ο οδηγός σας καθοδηγεί σε όλη τη διαδικασία. Θα μάθετε πώς να **set chart size**, να ενεργοποιήσετε **show percentages pie chart**, να προσθέσετε **data labels pie chart**, και να **rotate pie chart slice** ώστε το πρώτο τμήμα να ξεκινάει σε γωνία 45 μοιρών.

Το παράδειγμα χρησιμοποιεί το **Aspose.Slides for Java**, μια ευρέως χρησιμοποιούμενη βιβλιοθήκη για τη διαχείριση αρχείων PowerPoint. Οι ίδιες έννοιες ισχύουν και για άλλες βιβλιοθήκες δημιουργίας διαγραμμάτων· απλώς αντικαταστήστε τις κλήσεις API με τα ισοδύναμα στη δική σας εργαλειοθήκη.

## Προαπαιτούμενα

* Εγκατεστημένο Java 17 ή νεότερο  
* Maven 3.8+ (ή Gradle) για διαχείριση εξαρτήσεων  
* Βασική κατανόηση της σύνταξης της Java  
* Πρόσβαση στο δυαδικό αρχείο Aspose.Slides for Java (μπορείτε να αποκτήσετε δωρεάν δοκιμαστική έκδοση από την επίσημη ιστοσελίδα)

Προσθέστε την εξάρτηση στο `pom.xml` σας:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-slides</artifactId>
    <version>24.9</version> <!-- latest version as of November 2026 -->
</dependency>
```

## Δημιουργία διαγράμματος πίτας – πλήρες παράδειγμα

Το παρακάτω πρόγραμμα δημιουργεί μια διαφάνεια PowerPoint που περιέχει ένα διάγραμμα πίτας με προσαρμοσμένο μέγεθος, ετικέτες δεδομένων σε ποσοστό και το πρώτο τμήμα περιστραμμένο.

```java
package com.example.piechart;

import com.aspose.slides.*;
import com.aspose.slides.charts.*;

public class PieChartDemo {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a presentation
        Presentation pres = new Presentation();

        // 2️⃣ Add a blank slide
        ISlide slide = pres.getSlides().addEmptySlide(pres.getLayoutSlides().get_Item(0));

        // 3️⃣ Insert a pie chart (create pie chart)
        IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50, 400, 300);
        // The dimensions above also demonstrate set chart size

        // 4️⃣ Populate the chart with sample data
        IChartDataWorkbook workbook = chart.getChartData().getChartDataWorkbook();

        // Clear the default series & categories
        chart.getChartData().getSeries().clear();
        chart.getChartData().getCategories().clear();

        // Add categories (slices)
        chart.getChartData().getCategories().add(workbook.getCell(0, "A1", "Category A"));
        chart.getChartData().getCategories().add(workbook.getCell(0, "A2", "Category B"));
        chart.getChartData().getCategories().add(workbook.getCell(0, "A3", "Category C"));

        // Add a series and assign values
        IChartSeries series = chart.getChartData().getSeries().add(
                workbook.getCell(0, "B1", "Series 1"),
                chart.getType());

        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B1", 30));
        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B2", 45));
        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B3", 25));

        // 5️⃣ Enable percentage display on data labels (show percentages pie chart)
        series.getDataLabelFormat().setShowPercentage(true);
        series.getDataLabelFormat().setShowCategoryName(false);
        series.getDataLabelFormat().setShowLegendKey(false);
        series.getDataLabelFormat().setShowSeriesName(false);
        series.getDataLabelFormat().setShowValue(false);
        series.getDataLabelFormat().setShowLeaderLines(false);

        // 6️⃣ Rotate the chart so the first slice starts at 45 degrees (rotate pie chart slice)
        chart.setFirstSliceAngle(45);

        // 7️⃣ Save the presentation
        String outPath = "output/PieChartDemo.pptx";
        pres.save(outPath, SaveFormat.Pptx);
        System.out.println("Presentation saved to " + outPath);
    }
}
```

### Γιατί κάθε βήμα είναι σημαντικό

| Βήμα | Σκοπός | Πώς σχετίζεται με τις λέξεις-κλειδιά |
|------|--------|--------------------------------------|
| **Insert chart** | **Create pie chart** – το κύριο αντικείμενο που θα αποδώσει το οπτικό. | ικανοποιεί άμεσα την απαίτηση *create pie chart*. |
| **Set dimensions** | Η κλήση `addChart(..., 400, 300)` δείχνει το **set chart size**. | Ελέγχει το πλάτος (400 px) και το ύψος (300 px). |
| **Show percentages** | Η `setShowPercentage(true)` κάνει το διάγραμμα **show percentages pie chart** σε κάθε τμήμα. | Οι χρήστες συχνά χρειάζονται ποσοστά αντί για ακατέργαστες τιμές. |
| **Add data labels** | Η διαμόρφωση `DataLabelFormat` προσθέτει **data labels pie chart** με την επιθυμητή ορατότητα. | Οι ετικέτες βελτιώνουν την αναγνωσιμότητα και είναι προσαρμόσιμες. |
| **Rotate slice** | Η `setFirstSliceAngle(45)` περιστρέφει το διάγραμμα ώστε το πρώτο τμήμα να ξεκινάει σε γωνία 45 μοιρών, ικανοποιώντας το **rotate pie chart slice**. | Βελτιώνει την οπτική έμφαση σε συγκεκριμένο τμήμα. |

## Αναλυτική ανάλυση βήμα προς βήμα

### 1. Εισαγωγή διαγράμματος πίτας και ορισμός μεγέθους διαγράμματος

```java
IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50, 400, 300);
```

*Η μέθοδος `addChart` δημιουργεί το διάγραμμα και ταυτόχρονα **set chart size** σε 400 × 300 σημεία.*  
Αν χρειάζεστε διαφορετικό μέγεθος, προσαρμόστε τα δύο τελευταία ορίσματα.

### 2. Συμπλήρωση του διαγράμματος με δεδομένα

Η επίδειξη προσθέτει τρεις κατηγορίες και μία σειρά. Αντικαταστήστε τους σκληρά κωδικοποιημένους αριθμούς με δεδομένα από βάση, CSV ή είσοδο χρήστη, όπως απαιτείται.

### 3. Εμφάνιση ποσοστών σε κάθε τμήμα

```java
series.getDataLabelFormat().setShowPercentage(true);
```

*Η ενεργοποίηση της `setShowPercentage(true)` εξασφαλίζει ότι το διάγραμμα **show percentages pie chart** υπολογίζει αυτόματα το μερίδιο κάθε τμήματος από το σύνολο.*

### 4. Προσθήκη λεπτομερών ετικετών δεδομένων

```java
series.getDataLabelFormat().setShowCategoryName(false);
series.getDataLabelFormat().setShowLeaderLines(false);
```

Μπορείτε να ενεργοποιήσετε/απενεργοποιήσετε άλλες επιλογές ετικετών (`setShowValue`, `setShowSeriesName`, κ.λπ.) για να προσαρμόσετε την εμπειρία **add data labels pie chart**.

### 5. Περιστροφή του πρώτου τμήματος

```java
chart.setFirstSliceAngle(45);
```

*Η κλήση `setFirstSliceAngle(45)` **rotate pie chart slice** έτσι ώστε το πρώτο τμήμα να αρχίζει σε γωνία 45 μοιρών, καθιστώντας το πιο εμφανές.*

### 6. Αποθήκευση και προβολή του αποτελέσματος

Η εκτέλεση του προγράμματος παράγει το `output/PieChartDemo.pptx`. Ανοίξτε το στο PowerPoint ή σε οποιονδήποτε συμβατό προβολέα για να δείτε το τελικό διάγραμμα πίτας:

![Create pie chart example](images/pie_chart_example.png){.align-center alt="Στιγμιότυπο οθόνης ενός δημιουργημένου διαγράμματος πίτας με προσαρμοσμένο μέγεθος, ετικέτες ποσοστών και το πρώτο τμήμα περιστραμμένο"}

Η παραπάνω εικόνα δείχνει το αποτέλεσμα του **create pie chart**, επιβεβαιώνοντας ότι το μέγεθος, οι ετικέτες, τα ποσοστά και η περιστροφή έχουν εφαρμοστεί σωστά.

## Συνηθισμένες παραλλαγές και ειδικές περιπτώσεις

| Κατάσταση | Προσαρμογή |
|-----------|------------|
| **Different chart dimensions** | Αλλάξτε τις παραμέτρους πλάτους/ύψους στη `addChart`. |
| **Multiple series** | Προσθέστε επιπλέον αντικείμενα `IChartSeries`; κάθε σειρά μπορεί να έχει τις δικές της ρυθμίσεις ετικετών. |
| **Custom label format** | Χρησιμοποιήστε `series.getDataLabelFormat().setNumberFormat("0.0%")` για να ελέγξετε τα δεκαδικά ψηφία. |
| **Rotating to another angle** | Περνάτε οποιονδήποτε ακέραιο (0‑360) στη `setFirstSliceAngle`. |
| **Export as image** | Μετά την αποθήκευση, καλέστε `chart.writeAsSvg(outPath)` ή `chart.writeAsPng(outPath)` για μια raster έκδοση. |

> **Pro tip:** Αν σκοπεύετε να δημιουργήσετε πολλά διαγράμματα σε βρόχο, επαναχρησιμοποιήστε το ίδιο αντικείμενο `Presentation` και αντικαταστήστε μόνο τα δεδομένα του διαγράμματος. Αυτό μειώνει το φορτίο μνήμης και επιταχύνει την επεξεργασία.

## Συμπέρασμα

Τώρα ξέρετε πώς να **create pie chart** σε Java, **set chart size**, να ενεργοποιήσετε **show percentages pie chart**, **add data labels pie chart**, και **rotate pie chart slice** για καλύτερη οπτική έμφαση. Το πλήρες, εκτελέσιμο παράδειγμα δείχνει κάθε βήμα από την αρχικοποίηση μέχρι την αποθήκευση του τελικού αρχείου PowerPoint.

### Τι ακολουθεί;

* Εξερευνήστε άλλους τύπους διαγραμμάτων (Bar, Line, Area) χρησιμοποιώντας το ίδιο enum `ChartType`.  
* Συνδυάστε πολλαπλά διαγράμματα σε μία διαφάνεια για πίνακες ελέγχου.  
* Εξάγετε διαγράμματα σε PNG ή SVG για χρήση σε web εφαρμογές.  

Μη διστάσετε να πειραματιστείτε με χρώματα, υπομνήματα και εφέ κίνησης—οι οπτικοποιήσεις δεδομένων σας περιορίζονται μόνο από τη φαντασία. Καλή δημιουργία διαγραμμάτων!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετικές θεματικές που επεκτείνουν τις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [πώς να εισάγετε διάγραμμα πίτας σε Word – προσθήκη ποσοστού ετικέτας δεδομένων](/words/english/java/using-document-elements/how-to-insert-pie-chart-in-word-add-data-label-percent/)
- [Πώς να εκτοξεύσετε τμήμα πίτας σε Java – tutorial διαγράμματος Aspose.Words](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)
- [Εισαγωγή διαγράμματος πίτας σε Java – Εκτόξευση, Περιστροφή & Επισήμανση Τμημάτων](/words/english/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}