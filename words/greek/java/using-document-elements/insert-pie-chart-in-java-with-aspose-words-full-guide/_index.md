---
category: general
date: 2026-07-29
description: Εισαγωγή διαγράμματος πίτας χρησιμοποιώντας το Aspose.Words για Java
  και μάθετε πώς να δημιουργήσετε διάγραμμα δακτυλίου, να μορφοποιήσετε διάγραμμα
  πίτας, να μορφοποιήσετε διάγραμμα στο Word και να προσαρμόσετε το μέγεθος του διαγράμματος.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- generate doughnut chart
- format pie chart
- format chart word
- customize chart size
language: el
lastmod: 2026-07-29
og_description: Εισάγετε διάγραμμα πίτας με το Aspose.Words for Java και μάθετε γρήγορα
  να δημιουργείτε διάγραμμα δακτυλίου, να μορφοποιείτε διάγραμμα πίτας, να μορφοποιείτε
  διάγραμμα στο Word και να προσαρμόζετε το μέγεθος του διαγράμματος για επαγγελματικά
  έγγραφα.
og_image_alt: Screenshot showing a Word document with an inserted pie chart created
  by Aspose.Words Java API
og_title: Εισαγωγή διαγράμματος πίτας σε Java – Πλήρης οδηγός Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Insert pie chart using Aspose.Words for Java and learn how to generate
    doughnut chart, format pie chart, format chart Word, and customize chart size.
  headline: Insert pie chart in Java with Aspose.Words – Full Guide
  type: TechArticle
- questions:
  - answer: The evaluation version works fine for testing, but it adds a watermark.
      Drop your `aspose.words.lic` file in the classpath for a clean output.
    question: Do I need a license?
  - answer: 'Absolutely. Add the following dependency to your `pom.xml`:'
    question: Can I use this with Maven?
  - answer: Loop over `pieChart.getSeries()` and apply `setExplosion`, `setFillColor`,
      or other formatting per series. That’s the way to **format pie chart** for multi‑dimensional
      data.
    question: What if I have more than one series?
  - answer: Yes—once saved, you can open the document and manually adjust colors,
      fonts, or even convert the pie to a bar chart if you need to.
    question: Is the chart editable in Word after generation?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Chart
- Document Generation
- Word Automation
title: Εισαγωγή διαγράμματος πίτας σε Java με το Aspose.Words – Πλήρης Οδηγός
url: /el/java/using-document-elements/insert-pie-chart-in-java-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Εισαγωγή διαγράμματος πίτας σε Java με Aspose.Words – Πλήρης Οδηγός

Έχετε αναρωτηθεί ποτέ πώς να **εισάγετε διάγραμμα πίτας** σε ένα έγγραφο Word από κώδικα Java; Δεν είστε οι μόνοι—πολλοί προγραμματιστές αντιμετωπίζουν αυτό το εμπόδιο όταν χρειάζονται έναν γρήγορο, προγραμματιστικό τρόπο οπτικοποίησης δεδομένων. Τα καλά νέα; Με το Aspose.Words for Java μπορείτε να το κάνετε σε λίγες γραμμές κώδικα, και ενώ το κάνετε, μπορείτε επίσης να **δημιουργήσετε διάγραμμα δαχτυλιδιού**, **μορφοποιήσετε διάγραμμα πίτας**, **μορφοποιήσετε διάγραμμα Word**, και **προσαρμόσετε το μέγεθος του διαγράμματος** ώστε να ταιριάζει με το branding σας.

Σε αυτό το tutorial θα περάσουμε από ένα πραγματικό παράδειγμα που ξεκινά με τη δημιουργία ενός κεντρικού εγγράφου, προσθέτει ένα διάγραμμα πίτας, ρυθμίζει μερικές οπτικές ιδιότητες και τέλος αποθηκεύει το αρχείο. Στο τέλος θα έχετε ένα επαναχρησιμοποιήσιμο snippet που μπορείτε να επικολλήσετε σε οποιοδήποτε έργο Java χρειάζεται αυτοματοποίηση διαγραμμάτων. Χωρίς επιπλέον βιβλιοθήκες, χωρίς χειροκίνητη παρέμβαση με Office interop—απλώς καθαρή, μεταγλωττισμένη Java.

## Τι Θα Χρειαστείτε

- **Java 17** (ή οποιοδήποτε πρόσφατο JDK· το API είναι συμβατό με παλαιότερες εκδόσεις)
- **Aspose.Words for Java** 22.12 ή νεότερο – μπορείτε να κατεβάσετε το Maven artifact ή το .jar από τον ιστότοπο της Aspose.
- Ένα βασικό IDE (IntelliJ IDEA, Eclipse, VS Code…) – οτιδήποτε που σας επιτρέπει να εκτελέσετε μια μέθοδο `main`.
- Προαιρετικά: αρχείο άδειας εάν δεν θέλετε το υδατογράφημα αξιολόγησης.

Αν έχετε όλα αυτά, μπορούμε να περάσουμε κατευθείαν στον κώδικα.

## Βήμα 1: Εισαγωγή διαγράμματος πίτας με Aspose.Words

Το πρώτο που κάνουμε είναι **εισαγωγή διαγράμματος πίτας** σε ένα νέο έγγραφο. Αυτό το βήμα θέτει τη βάση για όλα τα υπόλοιπα, επειδή το αντικείμενο διαγράμματος μας δίνει πρόσβαση σε σειρές, σημεία δεδομένων και οπτικές ρυθμίσεις.

```java
import com.aspose.words.*;

public class PieChartFormatting {
    public static void main(String[] args) throws Exception {
        // Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a pie chart with a specific size (500x400 points)
        Chart pieChart = builder.insertChart(ChartType.PIE, 500, 400);
```

> **Γιατί είναι σημαντικό:** `DocumentBuilder.insertChart` όχι μόνο δημιουργεί το διάγραμμα αλλά επιστρέφει και ένα αντικείμενο `Chart` που μπορούμε να χειριστούμε. Τα επιχειρήματα πλάτους και ύψους σας επιτρέπουν να **προσαρμόσετε το μέγεθος του διαγράμματος** ακριβώς κατά τη δημιουργία, ώστε να μην χρειάζεται να το ξαναμεγέθυντε αργότερα.

## Βήμα 2: Δημιουργία διαγράμματος δαχτυλιδιού (προαιρετικό)

Αν το σχέδιό σας απαιτεί μια τρύπα στο κέντρο—σκεφτείτε ένα κλασικό διάγραμμα δαχτυλιδιού—το Aspose το κάνει με μία γραμμή κώδικα. Η ίδια παρουσία `Chart` μπορεί να μετατραπεί από κανονική πίτα σε δαχτυλίδι ρυθμίζοντας το μέγεθος της τρύπας.

```java
        // Optional: Turn the pie into a doughnut by setting the hole size (0‑100%)
        pieChart.getChartData().setHoleSize(30); // 30% hole makes it a doughnut chart
```

> **Συμβουλή:** Το μέγεθος της τρύπας έχει αποτέλεσμα μόνο για `ChartType.DONUT`. Αν διατηρήσετε τον τύπο ως `PIE`, η κλήση αγνοείται, οπότε πειραματιστείτε ελεύθερα.

## Βήμα 3: Μορφοποίηση φέτων διαγράμματος πίτας

Ένα καλό οπτικό στοιχείο συχνά τονίζει μια συγκεκριμένη φέτα. Εδώ **μορφοποιούμε το διάγραμμα πίτας** εξωθώντας την πρώτη φέτα κατά 20 σημεία. Αυτό τραβάει το βλέμμα του αναγνώστη στο πιο σημαντικό σημείο δεδομένων.

```java
        // Explode the first slice to emphasize it
        pieChart.getSeries().get(0).setExplosion(20);
```

> **Pro tip:** Μπορείτε να κάνετε βρόχο μέσω `pieChart.getSeries()` αν έχετε πολλαπλές σειρές και να ορίσετε ατομικά χρώματα, περιθώρια ή ετικέτες δεδομένων. Αυτός είναι ο τρόπος να **μορφοποιήσετε το διάγραμμα Word** με πλούσιο στυλ.

## Βήμα 4: Προσθήκη δεδομένων στο διάγραμμα

Ένα διάγραμμα χωρίς δεδομένα είναι απλώς ένα διακοσμητικό σχήμα. Ας του δώσουμε ένα απλό σύνολο δεδομένων—π.χ. αριθμούς πωλήσεων ανά τρίμηνο.

```java
        // Populate the chart with sample data
        ChartSeries series = pieChart.getSeries().get(0);
        series.getDataLabels().setShowCategoryName(true);
        series.getDataLabels().setShowValue(true);

        // Clear any default points and add our own
        series.getPoints().clear();
        series.getPoints().add(new ChartPoint(30)); // Q1
        series.getPoints().add(new ChartPoint(45)); // Q2
        series.getPoints().add(new ChartPoint(15)); // Q3
        series.getPoints().add(new ChartPoint(10)); // Q4
```

> **Γιατί το κάνουμε:** Προσθέτοντας ρητά αντικείμενα `ChartPoint` εξασφαλίζουμε ότι το διάγραμμα αντικατοπτρίζει τη λογική της επιχείρησής μας. Οι κλήσεις `setShowCategoryName` και `setShowValue` είναι μέρος της **μορφοποίησης του διαγράμματος πίτας** ώστε να εμφανίζονται τόσο οι ετικέτες όσο και οι αριθμοί.

## Βήμα 5: Λεπτομερής ρύθμιση εμφάνισης (προσαρμογή μεγέθους & στυλ διαγράμματος)

Πέρα από τις αρχικές διαστάσεις, ίσως θέλετε να ρυθμίσετε τη λεζάντα, τον τίτλο ή ακόμη και τη γραμματοσειρά των ετικετών δεδομένων. Όλα αυτά εμπίπτουν στην **προσαρμογή μεγέθους διαγράμματος** και στη γενική μορφοποίηση.

```java
        // Set a title for the chart
        ChartTitle title = pieChart.getTitle();
        title.setText("Quarterly Sales Distribution");
        title.getFont().setSize(14);
        title.getFont().setBold(true);

        // Move the legend to the right side
        ChartLegend legend = pieChart.getLegend();
        legend.setPosition(LegendPosition.RIGHT);
        legend.getFont().setSize(10);

        // Adjust the overall chart size again if needed
        pieChart.setWidth(600);   // width in points
        pieChart.setHeight(450);  // height in points
```

> **Edge case:** Αν αργότερα αποφασίσετε να εξάγετε το έγγραφο σε PDF, τα διανυσματικά δεδομένα του διαγράμματος παραμένουν καθαρά επειδή το μέγεθος ορίζεται σε points, όχι σε pixels. Αυτό είναι πλεονέκτημα για τη **μορφοποίηση διαγράμματος Word** και τις επόμενες μορφές.

## Βήμα 6: Αποθήκευση και προβολή του εγγράφου

Το τελευταίο βήμα είναι τόσο απλό όσο η κλήση `doc.save`. Αυτό γράφει ένα αρχείο `.docx` που μπορείτε να ανοίξετε στο Microsoft Word, LibreOffice ή οποιονδήποτε προβολέα που υποστηρίζει τη μορφή OpenXML.

```java
        // Save the document containing the formatted chart
        doc.save("YOUR_DIRECTORY/PieChart.docx");
    }
}
```

> **Αποτέλεσμα:** Ανοίξτε το `PieChart.docx` και θα δείτε ένα καλοσχεδιασμένο διάγραμμα πίτας (ή δαχτυλιδιού) με εξωθούμενη φέτα, τίτλο και λεζάντα—όλα δημιουργημένα χωρίς να αγγίξετε ποτέ το UI.

### Αναμενόμενο Αποτέλεσμα

| Στοιχείο | Τι θα δείτε |
|----------|-------------|
| Τύπος διαγράμματος | Διάγραμμα πίτας (ή δαχτυλιδιού αν `holeSize` > 0) |
| Εξώθηση φέτας | Πρώτη φέτα μετατοπισμένη κατά 20 pts |
| Λεζάντα | Τοποθετημένη στα δεξιά |
| Τίτλος | “Quarterly Sales Distribution” με έντονη γραμματοσειρά 14 pt |
| Ετικέτες δεδομένων | Όνομα κατηγορίας και τιμή εμφανίζονται σε κάθε φέτα |
| Έγγραφο | Ένα τυπικό αρχείο Word `.docx` έτοιμο για διαμοιρασμό |

## Συχνές Ερωτήσεις & Πιθανά Προβλήματα

- **Χρειάζομαι άδεια;**  
  Η έκδοση αξιολόγησης λειτουργεί για δοκιμές, αλλά προσθέτει υδατογράφημα. Τοποθετήστε το αρχείο `aspose.words.lic` στο classpath για καθαρό αποτέλεσμα.

- **Μπορώ να το χρησιμοποιήσω με Maven;**  
  Φυσικά. Προσθέστε την παρακάτω εξάρτηση στο `pom.xml` σας:

  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>22.12</version>
  </dependency>
  ```

- **Τι γίνεται αν έχω περισσότερες από μία σειρές;**  
  Κάντε βρόχο μέσω `pieChart.getSeries()` και εφαρμόστε `setExplosion`, `setFillColor` ή άλλες μορφοποιήσεις ανά σειρά. Αυτός είναι ο τρόπος να **μορφοποιήσετε το διάγραμμα πίτας** για πολυδιάστατα δεδομένα.

- **Είναι το διάγραμμα επεξεργάσιμο στο Word μετά τη δημιουργία;**  
  Ναι—αφού αποθηκευτεί, μπορείτε να ανοίξετε το έγγραφο και να προσαρμόσετε χρώματα, γραμματοσειρές ή ακόμη και να μετατρέψετε την πίτα σε ραβδόγραμμα αν χρειαστεί.

## Συμπέρασμα

Μόλις **εισαγάγαμε διάγραμμα πίτας** σε ένα έγγραφο Word χρησιμοποιώντας το Aspose.Words for Java, δείξαμε πώς να **δημιουργήσουμε διάγραμμα δαχτυλιδιού**, παρουσιάσαμε πολλαπλούς τρόπους **μορφοποίησης διαγράμματος πίτας**, καλύψαμε τις καλύτερες πρακτικές **μορφοποίησης διαγράμματος Word** και μάθαμε πώς να **προσαρμόσουμε το μέγεθος του διαγράμματος** για ένα επαγγελματικό αποτέλεσμα. Το πλήρες, εκτελέσιμο παράδειγμα παραπάνω μπορεί να ενσωματωθεί σε οποιοδήποτε έργο Java, προσφέροντας άμεση αυτοματοποίηση διαγραμμάτων χωρίς το βάρος του COM interop ή εγκαταστάσεων Office.

Τι ακολουθεί; Δοκιμάστε να αντικαταστήσετε την πηγή δεδομένων με μια ζωντανή βάση, προσθέστε χρωματισμούς βάσει ορίων, ή εξάγετε το ίδιο έγγραφο σε PDF για εκτύπωση. Κάθε ένα από αυτά τα βήματα βασίζεται στο θεμέλιο που θέσαμε, οπότε η μετάβαση θα είναι ομαλή.

Αν αντιμετωπίσετε δυσκολίες ή έχετε ιδέες για περαιτέρω βελτιώσεις—ίσως ένα στοίβαγμα ραβδών ή ένα διάγραμμα γραμμής—αφήστε ένα σχόλιο παρακάτω. Καλή δημιουργία διαγραμμάτων!

## Τι Θα Μάθετε Στη Σειρά;

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στα δικά σας έργα.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Format Number Of Data Label In A Chart](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Number Format For Axis In A Chart](/words/english/net/programming-with-charts/number-format-for-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}