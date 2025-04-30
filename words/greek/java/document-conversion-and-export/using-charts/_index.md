---
"description": "Μάθετε πώς να δημιουργείτε και να προσαρμόζετε γραφήματα στο Aspose.Words για Java. Εξερευνήστε τύπους γραφημάτων, μορφοποίηση και ιδιότητες αξόνων για οπτικοποίηση δεδομένων."
"linktitle": "Χρήση γραφημάτων"
"second_title": "API επεξεργασίας εγγράφων Java Aspose.Words"
"title": "Χρήση γραφημάτων στο Aspose.Words για Java"
"url": "/el/java/document-conversion-and-export/using-charts/"
"weight": 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Χρήση γραφημάτων στο Aspose.Words για Java


## Εισαγωγή στη χρήση γραφημάτων στο Aspose.Words για Java

Σε αυτό το σεμινάριο, θα εξερευνήσουμε πώς να εργαζόμαστε με γραφήματα χρησιμοποιώντας το Aspose.Words για Java. Θα μάθετε πώς να δημιουργείτε διάφορους τύπους γραφημάτων, να προσαρμόζετε τις ιδιότητες των αξόνων, να μορφοποιείτε ετικέτες δεδομένων και πολλά άλλα. Ας ξεκινήσουμε!

## Δημιουργία γραφήματος γραμμών

Για να δημιουργήσετε ένα γράφημα γραμμών, χρησιμοποιήστε τον ακόλουθο κώδικα:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.LINE, 432.0, 252.0);
Chart chart = shape.getChart();
chart.getTitle().setText("Data Labels With Different Number Format");

// Διαγραφή προεπιλεγμένων σειρών.
chart.getSeries().clear();

// Προσθήκη σειράς με δεδομένα και ετικέτες δεδομένων.
ChartSeries series1 = chart.getSeries().add("Aspose Series 1", 
    new String[] { "Category 1", "Category 2", "Category 3" }, 
    new double[] { 2.5, 1.5, 3.5 });

series1.hasDataLabels(true);
series1.getDataLabels().setShowValue(true);
series1.getDataLabels().get(0).getNumberFormat().setFormatCode("\"$\"#,##0.00");
series1.getDataLabels().get(1).getNumberFormat().setFormatCode("dd/mm/yyyy");
series1.getDataLabels().get(2).getNumberFormat().setFormatCode("0.00%");

// Ή συνδέστε τον κώδικα μορφοποίησης με ένα κελί πηγής.
series1.getDataLabels().get(2).getNumberFormat().isLinkedToSource(true);

doc.save("Your Directory Path" + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

## Δημιουργία άλλων τύπων γραφημάτων

Μπορείτε να δημιουργήσετε διαφορετικούς τύπους γραφημάτων, όπως γραφήματα στηλών, περιοχών, φυσαλίδων, διασποράς και άλλα, χρησιμοποιώντας παρόμοιες τεχνικές. Ακολουθεί ένα παράδειγμα εισαγωγής ενός απλού γραφήματος στηλών:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Διαγραφή προεπιλεγμένων σειρών.
chart.getSeries().clear();

// Δημιουργία κατηγοριών και προσθήκη δεδομένων.
String[] categories = new String[] { "Category 1", "Category 2" };
chart.getSeries().add("Aspose Series 1", categories, new double[] { 1.0, 2.0 });
chart.getSeries().add("Aspose Series 2", categories, new double[] { 3.0, 4.0 });

doc.save("Your Directory Path" + "WorkingWithCharts.InsertSimpleColumnChart.docx");
```

## Προσαρμογή ιδιοτήτων άξονα

Μπορείτε να προσαρμόσετε τις ιδιότητες του άξονα, όπως αλλαγή του τύπου άξονα, ορισμό σημαδιών υποδιαίρεσης, μορφοποίηση ετικετών και άλλα. Ακολουθεί ένα παράδειγμα ορισμού ιδιοτήτων άξονα XY:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.AREA, 432.0, 252.0);
Chart chart = shape.getChart();

// Διαγράψτε την προεπιλεγμένη σειρά και προσθέστε τα δεδομένα σας.

ChartAxis xAxis = chart.getAxisX();
ChartAxis yAxis = chart.getAxisY();

// Αλλάξτε τον άξονα X ώστε να είναι κατηγορία αντί για ημερομηνία.
xAxis.setCategoryType(AxisCategoryType.CATEGORY);
xAxis.setCrosses(AxisCrosses.CUSTOM);
xAxis.setCrossesAt(3.0); // Μετρημένο σε μονάδες απεικόνισης του άξονα Y (εκατοντάδες).
xAxis.setReverseOrder(true);
xAxis.setMajorTickMark(AxisTickMark.CROSS);
xAxis.setMinorTickMark(AxisTickMark.OUTSIDE);
xAxis.setTickLabelOffset(200);

yAxis.setTickLabelPosition(AxisTickLabelPosition.HIGH);
yAxis.setMajorUnit(100.0);
yAxis.setMinorUnit(50.0);
yAxis.getDisplayUnit().setUnit(AxisBuiltInUnit.HUNDREDS);
yAxis.getScaling().setMinimum(new AxisBound(100.0));
yAxis.getScaling().setMaximum(new AxisBound(700.0));

doc.save("Your Directory Path" + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

## Μορφοποίηση ετικετών δεδομένων

Μπορείτε να μορφοποιήσετε ετικέτες δεδομένων με διαφορετικές μορφές αριθμών. Ακολουθεί ένα παράδειγμα:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Διαγράψτε την προεπιλεγμένη σειρά και προσθέστε τα δεδομένα σας.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

## Πρόσθετες προσαρμογές γραφημάτων

Μπορείτε να προσαρμόσετε περαιτέρω τα γραφήματά σας προσαρμόζοντας τα όρια, τις μονάδες διαστήματος μεταξύ ετικετών, αποκρύπτοντας τους άξονες του γραφήματος και πολλά άλλα. Εξερευνήστε τα παρεχόμενα αποσπάσματα κώδικα για να μάθετε περισσότερα σχετικά με αυτές τις επιλογές.

## Σύναψη

Σε αυτό το σεμινάριο, εξερευνήσαμε τον τρόπο εργασίας με γραφήματα χρησιμοποιώντας το Aspose.Words για Java. Μάθατε πώς να δημιουργείτε διάφορους τύπους γραφημάτων, να προσαρμόζετε τις ιδιότητες των αξόνων, να μορφοποιείτε ετικέτες δεδομένων και πολλά άλλα. Το Aspose.Words για Java παρέχει ισχυρά εργαλεία για την προσθήκη οπτικών αναπαραστάσεων δεδομένων στα έγγραφά σας, βελτιώνοντας τον τρόπο με τον οποίο παρουσιάζετε πληροφορίες.

## Συχνές ερωτήσεις

### Πώς μπορώ να προσθέσω πολλές σειρές σε ένα γράφημα;

Μπορείτε να προσθέσετε πολλές σειρές σε ένα γράφημα χρησιμοποιώντας το `chart.getSeries().add()` μέθοδος. Βεβαιωθείτε ότι έχετε καθορίσει το όνομα της σειράς, τις κατηγορίες και τις τιμές δεδομένων.

### Πώς μπορώ να μορφοποιήσω ετικέτες δεδομένων με προσαρμοσμένες μορφές αριθμών;

Μπορείτε να μορφοποιήσετε ετικέτες δεδομένων αποκτώντας πρόσβαση στο `DataLabels` ιδιότητες μιας σειράς και ορισμός του επιθυμητού κώδικα μορφοποίησης χρησιμοποιώντας `getNumberFormat().setFormatCode()`.

### Πώς μπορώ να προσαρμόσω τις ιδιότητες του άξονα σε ένα γράφημα;

Μπορείτε να προσαρμόσετε τις ιδιότητες του άξονα, όπως τον τύπο, τα σημάδια υποδιαίρεσης, τις ετικέτες και άλλα, αποκτώντας πρόσβαση στο `ChartAxis` ιδιότητες όπως `setCategoryType()`, `setCrosses()`, και `setMajorTickMark()`.

### Πώς μπορώ να δημιουργήσω άλλους τύπους γραφημάτων, όπως γραφήματα διασποράς ή περιοχής;

Μπορείτε να δημιουργήσετε διάφορους τύπους γραφημάτων καθορίζοντας τα κατάλληλα `ChartType` κατά την εισαγωγή του γραφήματος χρησιμοποιώντας `builder.insertChart(ChartType.TYPE, width, height)`.

### Πώς μπορώ να αποκρύψω έναν άξονα γραφήματος;

Μπορείτε να αποκρύψετε έναν άξονα γραφήματος ορίζοντας το `setHidden(true)` ιδιότητα του άξονα.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}