---
date: 2026-02-16
description: Μάθετε πώς να προσθέτετε πολλαπλές σειρές σε διαγράμματα στο Aspose.Words
  for Java, να αλλάζετε τις σημάνσεις των αξόνων, να εφαρμόζετε προσαρμοσμένη μορφή
  αριθμού και να δημιουργείτε έγγραφα Word με διαγράμματα γραμμής και στήλης.
linktitle: Using Charts
second_title: Aspose.Words Java Document Processing API
title: Προσθήκη πολλαπλών σειρών σε γραφήματα στο Aspose.Words για Java
url: /el/java/document-conversion-and-export/using-charts/
weight: 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Προσθήκη Πολλαπλών Σειρών σε Διαγράμματα στο Aspose.Words για Java

## Εισαγωγή στη Χρήση Διαγραμμάτων στο Aspose.Words για Java

Σε αυτό το tutorial θα μάθετε **πώς να προσθέσετε πολλαπλές σειρές** σε ένα διάγραμμα χρησιμοποιώντας το Aspose.Words για Java, γιατί η προσαρμογή των σημείων σήμανσης του άξονα και η εφαρμογή προσαρμοσμένης μορφής αριθμού είναι σημαντική, και πώς να δημιουργήσετε ένα έγγραφο Word γεμάτο διαγράμματα. Είτε χρειάζεστε ένα γραμμικό διάγραμμα για οικονομικά δεδομένα είτε ένα στήλης διάγραμμα για πωλήσεις, τα παρακάτω βήματα θα σας καθοδηγήσουν στη δημιουργία, το στυλ και τη λεπτομερή ρύθμιση των διαγραμμάτων προγραμματιστικά.

## Quick Answers
- **Πώς προσθέτω πολλαπλές σειρές;** Χρησιμοποιήστε `chart.getSeries().add(...)` για κάθε σειρά που θέλετε να εμφανίσετε.  
- **Μπορώ να αλλάξω τα σημεία σήμανσης του άξονα;** Ναι – χρησιμοποιήστε `setMajorTickMark()` και `setMinorTickMark()` στα αντικείμενα του άξονα.  
- **Τι μορφή μπορώ να εφαρμόσω στις ετικέτες δεδομένων;** Οποιαδήποτε μορφή αριθμού συμβατή με το Excel, π.χ., `"$"#,##0.00` ή `0.00%`.  
- **Ποιοι τύποι διαγραμμάτων υποστηρίζονται;** Γραμμικά, στήλης, περιοχής, φυσαλίδων, διασποράς και πολλοί άλλοι μέσω του `ChartType`.  
- **Απαιτείται άδεια για παραγωγή;** Απαιτείται έγκυρη άδεια Aspose.Words για Java για πλήρη λειτουργικότητα.

## Τι σημαίνει «προσθήκη πολλαπλών σειρών» σε ένα διάγραμμα;

Η προσθήκη πολλαπλών σειρών σημαίνει την εισαγωγή περισσότερων από ένα συνόλων δεδομένων στην ίδια περιοχή διαγράμματος, επιτρέποντας τη σύγκριση διαφορετικών κατηγοριών ή χρονικών περιόδων πλάι‑πλάι. Κάθε σειρά εμφανίζεται ως δική της γραμμή, στήλη ή σύνολο σημείων, προσφέροντας στους αναγνώστες μια πιο πλούσια οπτική ιστορία.

## Γιατί να χρησιμοποιήσετε το Aspose.Words για Java για τη δημιουργία εγγράφων Word με διαγράμματα;

- **Πλήρης έλεγχος** πάνω στον τύπο, τη διάταξη και το στυλ του διαγράμματος χωρίς να ανοίξετε το Word χειροκίνητα.  
- **Προγραμματισμένη δημιουργία** που εντάσσεται σε αυτοματοποιημένες αλυσίδες αναφορών.  
- **Διαπλατφόρμα** – λειτουργεί σε οποιοδήποτε περιβάλλον συμβατό με Java.  
- **Πλούσιο API** για προσαρμογή άξονα, ετικετών δεδομένων και μορφών αριθμών.

## Προαπαιτούμενα
- Java Development Kit (JDK) 8 ή νεότερο.  
- Βιβλιοθήκη Aspose.Words για Java προστιθέμενη στο έργο σας (Maven/Gradle ή JAR).  
- Έγκυρη άδεια Aspose για παραγωγή (προαιρετική για αξιολόγηση).

## Οδηγός Βήμα‑βήμα

### Βήμα 1: Δημιουργία γραμμικού διαγράμματος και **προσθήκη πολλαπλών σειρών**
Παρακάτω βρίσκεται ο βασικός κώδικας που δημιουργεί ένα γραμμικό διάγραμμα, καθαρίζει τις προεπιλεγμένες σειρές και προσθέτει τρεις διαφορετικές σειρές με προσαρμοσμένες ετικέτες δεδομένων.

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

> **Συμβουλή:** Καλέστε `chart.getSeries().add(...)` όσες φορές χρειάζεται για **να προσθέσετε πολλαπλές σειρές** – κάθε κλήση δημιουργεί μια νέα γραμμή (ή στήλη κ.λπ.) στο ίδιο διάγραμμα.

### Βήμα 2: **Δημιουργία διαγράμματος στήλης** (create column chart java)
Το επόμενο απόσπασμα δείχνει πώς να εισάγετε ένα απλό διάγραμμα στήλης, χρήσιμο για σύγκριση κατηγοριών πλάι‑πλάι.

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

### Βήμα 3: **Αλλαγή σημείων σήμανσης άξονα** (change axis tick marks)
Η προσαρμογή των αξόνων X και Y βελτιώνει την αναγνωσιμότητα. Ο παρακάτω κώδικας δείχνει πώς να αλλάξετε τα σημεία σήμανσης, να αντιστρέψετε τη σειρά και να ορίσετε προσαρμοσμένα σημεία διασταύρωσης.

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

yAxis.setTickLabelPosition(AxisTickLabelPosition.HIGH);
yAxis.setMajorUnit(100.0);
yAxis.setMinorUnit(50.0);
yAxis.getDisplayUnit().setUnit(AxisBuiltInUnit.HUNDREDS);
yAxis.getScaling().setMinimum(new AxisBound(100.0));
yAxis.getScaling().setMaximum(new AxisBound(700.0));

doc.save("Your Directory Path" + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

### Βήμα 4: **Εφαρμογή προσαρμοσμένης μορφής αριθμού** (apply custom number format)
Μπορείτε να μορφοποιήσετε τους αριθμούς του άξονα ή τις ετικέτες δεδομένων με οποιοδήποτε μοτίβο υποστηρίζεται από το Excel. Παρακάτω είναι ένα σύντομο παράδειγμα που μορφοποιεί τον άξονα Y με μοτίβο διαχωριστή χιλιάδων.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

### Βήμα 5: Δημιουργία του τελικού εγγράφου Word (generate chart word document)
Μετά τη ρύθμιση των σειρών, των αξόνων και των ετικετών, απλώς καλέστε `doc.save(...)` όπως φαίνεται στα παραπάνω αποσπάσματα. Το παραγόμενο αρχείο `.docx` περιέχει πλήρως λειτουργικά διαγράμματα που μπορούν να ανοιχτούν και να επεξεργαστούν στο Microsoft Word.

## Συχνές Περιπτώσεις Χρήσης
- **Οικονομικοί πίνακες ελέγχου** – γραμμικά διαγράμματα με πολλαπλές σειρές για έσοδα, έξοδα και κέρδος.  
- **Αναφορές πωλήσεων** – διαγράμματα στήλης που συγκρίνουν τις τριμηνιαίες πωλήσεις ανά περιοχή.  
- **Παρακολούθηση έργων** – διαγράμματα περιοχής ή διασποράς που οπτικοποιούν την πρόοδο με την πάροδο του χρόνου.  

## Πρόσθετες Προσαρμογές Διαγράμματος
Πέρα από τα βασικά, μπορείτε να ρυθμίσετε τα όρια, να κρύψετε άξονες (`axis.setHidden(true)`), να αλλάξετε χρώματα, να προσθέσετε υπομνήματα κ.ά. Ανατρέξτε στην τεκμηρίωση του Aspose.Words για Java API για την πλήρη λίστα επιλογών.

## Συμπέρασμα
Σε αυτόν τον οδηγό καλύψαμε πώς να **προσθέσετε πολλαπλές σειρές** σε διαγράμματα, να δημιουργήσετε τόσο γραμμικά όσο και στήλης διαγράμματα, **να αλλάξετε τα σημεία σήμανσης του άξονα**, **να εφαρμόσετε προσαρμοσμένες μορφές αριθμού**, και τελικά **να δημιουργήσετε ένα έγγραφο Word γεμάτο διαγράμματα**. Με το Aspose.Words για Java έχετε έναν ισχυρό, κώδικα‑πρώτο τρόπο να ενσωματώσετε επαγγελματικές οπτικοποιήσεις δεδομένων απευθείας στα έγγραφά σας.

## Συχνές Ερωτήσεις

**Ε: Πώς μπορώ να προσθέσω πολλαπλές σειρές σε ένα διάγραμμα;**  
Α: Καλέστε `chart.getSeries().add()` για κάθε σειρά που θέλετε να εμφανίσετε. Κάθε κλήση δημιουργεί ένα νέο σύνολο δεδομένων που εμφανίζεται ως δική του γραμμή, στήλη ή ομάδα σημείων.

**Ε: Πώς μορφοποιώ τις ετικέτες δεδομένων με προσαρμοσμένη μορφή αριθμού;**  
Α: Πρόσβαση στο αντικείμενο `DataLabels` της σειράς και χρήση του `getNumberFormat().setFormatCode("your pattern")`. Μπορείτε επίσης να συνδέσετε τη μορφή με ένα κελί προέλευσης χρησιμοποιώντας `isLinkedToSource(true)`.

**Ε: Πώς μπορώ να αλλάξω τα σημεία σήμανσης του άξονα;**  
Α: Χρησιμοποιήστε `setMajorTickMark()` και `setMinorTickMark()` στο `ChartAxis`. Οι επιλογές περιλαμβάνουν `CROSS`, `INSIDE`, `OUTSIDE`, και `NONE`.

**Ε: Μπορώ να δημιουργήσω άλλους τύπους διαγραμμάτων όπως διασπορά ή περιοχή;**  
Α: Ναι – καθορίστε το επιθυμητό `ChartType` (π.χ., `ChartType.SCATTER`, `ChartType.AREA`) όταν καλείτε `builder.insertChart(...)`.

**Ε: Πώς κρύβω έναν άξονα που δεν χρειάζομαι;**  
Α: Καλέστε `axis.setHidden(true)` στο `ChartAxis` που θέλετε να κρύψετε.

---

**Τελευταία Ενημέρωση:** 2026-02-16  
**Δοκιμή Με:** Aspose.Words για Java 24.11  
**Συγγραφέας:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}