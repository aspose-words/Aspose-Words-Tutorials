---
date: 2025-12-13
description: Μάθετε πώς να δημιουργήσετε ένα ραβδόγραμμα και να μορφοποιήσετε τις
  ετικέτες δεδομένων του διαγράμματος με το Aspose.Words for Java. Εξερευνήστε την
  προσθήκη πολλαπλών σειρών, την αλλαγή τύπου άξονα και την απόκρυψη του άξονα του
  διαγράμματος.
linktitle: Using Charts
second_title: Aspose.Words Java Document Processing API
title: Πώς να δημιουργήσετε γράφημα στήλης χρησιμοποιώντας το Aspose.Words για Java
url: /el/java/document-conversion-and-export/using-charts/
weight: 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να δημιουργήσετε γράφημα στήλης χρησιμοποιώντας το Aspose.Words για Java

Σε αυτό το tutorial θα **create column chart** απευθείας μέσα σε έγγραφα Word χρησιμοποιώντας το Aspose.Words για Java. Θα περάσουμε από τη δημιουργία διαφορετικών τύπων γραφημάτων, την προσθήκη πολλαπλών σειρών, τη μορφοποίηση ετικετών δεδομένων γραφήματος, την αλλαγή τύπου άξονα και ακόμη την απόκρυψη άξονα γραφήματος όταν χρειάζεστε πιο καθαρή εμφάνιση. Στο τέλος θα έχετε μια σταθερή, έτοιμη για παραγωγή προσέγγιση για την ενσωμάτωση πλούσιων γραφημάτων στα έγγραφά σας.

## Γρήγορες Απαντήσεις
- **Ποια είναι κύρια κλάση για τη δημιουργία γραφήματος;** `DocumentBuilder` with `insertChart`.
- **Ποια μέθοδος προσθέτει μια νέα σειρά;** `chart.getSeries().add(...)`.
- **Πώς μορφοποιώ τις ετικέτες δεδομένων του γραφήματος;** Use `getDataLabels().get(...).getNumberFormat().setFormatCode(...)`.
- **Μπορώ να κρύψω έναν άξονα;** Yes, call `setHidden(true)` on the axis object.
- **Χρειάζομαι άδεια για το Aspose.Words;** A license is required for production use; a free trial is available.

## Τι είναι ένα γράφημα στήλης και γιατί να το χρησιμοποιήσετε;

Ένα γράφημα στήλης εμφανίζει κατηγοριοποιημένα δεδομένα ως κάθετες μπάρες, καθιστώντας το ιδανικό για τη σύγκριση τιμών μεταξύ ομάδων (πωλήσεις ανά περιοχή, μηνιαία έξοδα κ.λπ.). Σε εφαρμογές Java, η δημιουργία ενός γραφήματος στήλης με το Aspose.Words σας επιτρέπει να ενσωματώσετε αυτές τις απεικονίσεις απευθείας σε αρχεία Word / DOCX χωρίς την ανάγκη Excel ή εξωτερικών εργαλείων.

## Πώς να δημιουργήσετε ένα γράφημα στήλης

Παρακάτω υπάρχει ένα απλό παράδειγμα που δημιουργεί ένα απλό γράφημα στήλης. Ο κώδικας είναι πανομοιότυπος με το αρχικό απόσπασμα – προσθέσαμε μόνο επεξηγηματικά σχόλια για να είναι πιο εύκολο στην κατανόηση.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Delete default generated series.
chart.getSeries().clear();

// Creating categories and adding data.
String[] categories = new String[] { "Category 1", "Category 2" };
chart.getSeries().add("Aspose Series 1", categories, new double[] { 1.0, 2.0 });
chart.getSeries().add("Aspose Series 2", categories, new double[] { 3.0, 4.0 });

doc.save("Your Directory Path" + "WorkingWithCharts.InsertSimpleColumnChart.docx");
```

### Προσθήκη πολλαπλών σειρών

Μπορείτε να **προσθέσετε πολλαπλές σειρές** σε ένα γράφημα στήλης καλώντας επανειλημμένα το `chart.getSeries().add(...)`, όπως φαίνεται παραπάνω. Κάθε σειρά μπορεί να έχει το δικό της σύνολο κατηγοριών και τιμών, επιτρέποντάς σας να συγκρίνετε πολλαπλά σύνολα δεδομένων πλάι‑πλάι.

## Πώς να δημιουργήσετε ένα γράφημα γραμμής με προσαρμοσμένες ετικέτες δεδομένων

Αν χρειάζεστε ένα γράφημα γραμμής αντί για γράφημα στήλης, ισχύει το ίδιο μοτίβο. Αυτό το παράδειγμα δείχνει επίσης **μορφοποίηση ετικετών δεδομένων γραφήματος** με διαφορετικές μορφές αριθμών.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.LINE, 432.0, 252.0);
Chart chart = shape.getChart();
chart.getTitle().setText("Data Labels With Different Number Format");

// Delete default generated series.
chart.getSeries().clear();

// Adding a series with data and data labels.
ChartSeries series1 = chart.getSeries().add("Aspose Series 1", 
    new String[] { "Category 1", "Category 2", "Category 3" }, 
    new double[] { 2.5, 1.5, 3.5 });

series1.hasDataLabels(true);
series1.getDataLabels().setShowValue(true);
series1.getDataLabels().get(0).getNumberFormat().setFormatCode("\"$\"#,##0.00");
series1.getDataLabels().get(1).getNumberFormat().setFormatCode("dd/mm/yyyy");
series1.getDataLabels().get(2).getNumberFormat().setFormatCode("0.00%");

// Or link format code to a source cell.
series1.getDataLabels().get(2).getNumberFormat().isLinkedToSource(true);

doc.save("Your Directory Path" + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

### Προσθήκη ετικετών δεδομένων

Η κλήση `series1.hasDataLabels(true)` **προσθέτει ετικέτες δεδομένων** στη σειρά, ενώ το `setShowValue(true)` κάνει τις πραγματικές τιμές ορατές στο γράφημα.

## Πώς να αλλάξετε τον τύπο άξονα και να προσαρμόσετε τις ιδιότητες του άξονα

Η αλλαγή του τύπου άξονα (π.χ., από ημερομηνία σε κατηγορία) σας επιτρέπει να ελέγξετε πώς τοποθετούνται τα σημεία δεδομένων. Αυτό το απόσπασμα δείχνει επίσης πώς να **κρύψετε άξονα γραφήματος** αν προτιμάτε ένα μινιμαλιστικό σχέδιο.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.AREA, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

ChartAxis xAxis = chart.getAxisX();
ChartAxis yAxis = chart.getAxisY();

// Change the X axis to be a category instead of date.
xAxis.setCategoryType(AxisCategoryType.CATEGORY);
xAxis.setCrosses(AxisCrosses.CUSTOM);
xAxis.setCrossesAt(3.0); // Measured in display units of the Y axis (hundreds).
xAxis.setReverseOrder(true);
xAxis.setMajorTickMark(AxisTickMark.CROSS);
xAxis.setMinorTickMark(AxisTickMark.OUTSIDE);
xAxis.setTickLabelOffset(200);

// Example of hiding the Y axis.
yAxis.setHidden(true);

yAxis.setTickLabelPosition(AxisTickLabelPosition.HIGH);
yAxis.setMajorUnit(100.0);
yAxis.setMinorUnit(50.0);
yAxis.getDisplayUnit().setUnit(AxisBuiltInUnit.HUNDREDS);
yAxis.getScaling().setMinimum(new AxisBound(100.0));
yAxis.getScaling().setMaximum(new AxisBound(700.0));

doc.save("Your Directory Path" + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

### Αλλαγή τύπου άξονα

`xAxis.setCategoryType(AxisCategoryType.CATEGORY)` **αλλάζει τον τύπο άξονα** από άξονα βασισμένο σε ημερομηνίες σε κατηγορικό, δίνοντάς σας πλήρη έλεγχο στην τοποθέτηση των ετικετών.

## Πώς να μορφοποιήσετε τις ετικέτες δεδομένων του γραφήματος (μορφές αριθμών)

Μπορείτε να εφαρμόσετε μορφοποίηση αριθμών απευθείας στον άξονα ή στις ετικέτες δεδομένων. Αυτό το παράδειγμα μορφοποιεί τους αριθμούς του άξονα Y με διαχωριστικό χιλιάδων.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

## Πρόσθετες προσαρμογές γραφήματος

Πέρα από τα βασικά, μπορείτε να ρυθμίσετε τα όρια, να ορίσετε μονάδες διαστήματος μεταξύ των ετικετών, να κρύψετε συγκεκριμένους άξονες και πολλά άλλα. Ανατρέξτε στην τεκμηρίωση του Aspose.Words for Java API για μια πλήρη λίστα ιδιοτήτων.

## Συχνές Ερωτήσεις

**Q: Πώς μπορώ να προσθέσω πολλαπλές σειρές σε ένα γράφημα;**  
A: Χρησιμοποιήστε `chart.getSeries().add()` για κάθε σειρά που θέλετε να εμφανίσετε. Κάθε κλήση μπορεί να παρέχει ένα μοναδικό όνομα, πίνακα κατηγοριών και πίνακα τιμών.

**Q: Πώς μορφοποιώ τις ετικέτες δεδομένων του γραφήματος με προσαρμοσμένες μορφές αριθμών;**  
A: Πρόσβαση στο αντικείμενο `DataLabels` μιας σειράς και κλήση του `getNumberFormat().setFormatCode("your format")`. Μπορείτε επίσης να συνδέσετε τη μορφή με ένα κελί προέλευσης χρησιμοποιώντας `isLinkedToSource(true)`.

**Q: Πώς μπορώ να κρύψω έναν άξονα γραφήματος;**  
A: Κλήστε `setHidden(true)` στον `ChartAxis` που θέλετε να κρύψετε (π.χ., `chart.getAxisY().setHidden(true)`).

**Q: Ποιος είναι ο καλύτερος τρόπος για να αλλάξετε τον τύπο άξονα;**  
A: Χρησιμοποιήστε `setCategoryType(AxisCategoryType.CATEGORY)` για κατηγορικούς άξονες ή `AxisCategoryType.DATE` για άξονες ημερομηνίας.

**Q: Πώς προσθέτω ετικέτες δεδομένων σε μια σειρά;**  
A: Ενεργοποιήστε τις με `series.hasDataLabels(true)` και στη συνέχεια ρυθμίστε την ορατότητα χρησιμοποιώντας `series.getDataLabels().setShowValue(true)`.

## Συμπέρασμα

Καλύψαμε όλα όσα χρειάζεστε για να **create column chart** απεικονίσεις με το Aspose.Words for Java—από την εισαγωγή βασικών γραφημάτων και την προσθήκη πολλαπλών σειρών, μέχρι τη μορφοποίηση ετικετών δεδομένων γραφήματος, την αλλαγή τύπου άξονα και την απόκρυψη άξονων γραφήματος για καθαρή εμφάνιση. Ενσωματώστε αυτές τις τεχνικές στις διαδικασίες αναφοράς ή δημιουργίας εγγράφων σας για να παραδίδετε επαγγελματικά, δεδομενο‑προσανατολισμένα έγγραφα Word.

---

**Τελευταία Ενημέρωση:** 2025-12-13  
**Δοκιμή Με:** Aspose.Words for Java 24.12 (latest)  
**Συγγραφέας:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}