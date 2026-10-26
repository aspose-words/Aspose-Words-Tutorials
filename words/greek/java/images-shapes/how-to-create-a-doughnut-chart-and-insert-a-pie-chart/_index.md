---
category: general
date: 2026-10-26
description: Δημιουργήστε διάγραμμα δακτυλίου και ενσωματώστε διάγραμμα πίτας σε Java
  με κώδικα βήμα‑βήμα. Μάθετε τη πλήρη ροή εργασίας για ευέλικτες απεικονίσεις διαγραμμάτων.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create doughnut chart
- insert pie chart
- Java chart library
- chart customization Java
- data visualization Java
language: el
lastmod: 2026-10-26
og_description: Δημιουργήστε διάγραμμα ντόνατ σε Java με αυτόν τον οδηγό, ο οποίος
  δείχνει επίσης πώς να εισάγετε διάγραμμα πίτας για ευέλικτες απεικονίσεις.
og_image_alt: Java code snippet creating a doughnut chart and inserting a pie chart
og_title: Δημιουργία διαγράμματος δακτυλίου και εισαγωγή διαγράμματος πίτας – Οδηγός
  Java
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Create doughnut chart and insert pie chart in Java with step‑by‑step
    code. Learn the full workflow for flexible chart visualizations.
  headline: How to create a doughnut chart and insert a pie chart
  type: TechArticle
tags:
- chart
- Java
- data‑visualization
title: Πώς να δημιουργήσετε ένα διάγραμμα δακτυλίου και να εισάγετε ένα διάγραμμα
  πίτας
url: /el/java/images-shapes/how-to-create-a-doughnut-chart-and-insert-a-pie-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να δημιουργήσετε doughnut chart και να εισάγετε pie chart

Αν χρειάζεστε **create doughnut chart** σε Java, αυτό το tutorial σας καθοδηγεί βήμα‑βήμα. Θα δείξουμε επίσης πώς να **insert pie chart** χρησιμοποιώντας το ίδιο builder API, ώστε να μπορείτε να εναλλάσσετε εύκολα μεταξύ των δύο στυλ. Στο τέλος του οδηγού θα έχετε ένα πλήρες, εκτελέσιμο πρόγραμμα που παράγει και τους δύο τύπους διαγραμμάτων και παρουσιάζει κοινές προσαρμογές.

Το tutorial καλύπτει:

* Αρχικοποίηση του chart builder που παρέχεται από τη βιβλιοθήκη.  
* Δημιουργία doughnut chart και ρύθμιση του μεγέθους της τρύπας.  
* Εισαγωγή pie chart και «exploding» ενός τμήματος για έμφαση.  
* Συμβουλές για αντιμετώπιση ειδικών περιπτώσεων όπως ελλιπείς σειρές ή μη υποστηριζόμενοι τύποι διαγράμματος.

Απαιτείται μόνο ένα πρόσφατο JDK (8 ή νεότερο) και το JAR της βιβλιοθήκης διαγραμμάτων στο classpath. Δεν χρειάζονται εξωτερικές υπηρεσίες.

---

## Προαπαιτούμενα

| Item | Reason |
|------|--------|
| Java Development Kit (JDK) 8+ | Απαιτείται για τη μεταγλώττιση και εκτέλεση του παραδείγματος. |
| Chart library (π.χ., **Aspose.Cells for Java** ή **JFreeChart**) | Παρέχει `ChartBuilder`, `ChartType` και μεθόδους διαχείρισης σειρών που χρησιμοποιούνται στον κώδικα. |
| Ένα IDE ή ένας επεξεργαστής κειμένου | Για τη δημιουργία και εκτέλεση του αρχείου πηγαίου κώδικα Java. |

Βεβαιωθείτε ότι το JAR της βιβλιοθήκης έχει προστεθεί στο build path του έργου σας. Αν χρησιμοποιείτε Maven, προσθέστε την κατάλληλη εξάρτηση· διαφορετικά, τοποθετήστε το JAR στο φάκελο `libs` και αναφερθείτε σε αυτό κατά τη μεταγλώττιση.

---

## Step 1: Set up the chart builder

Το πρώτο βήμα είναι η δημιουργία μιας παρουσίας `ChartBuilder` (ή ισοδύναμης) που θα παράγει τα αντικείμενα διαγράμματος. Αυτό το αντικείμενο λειτουργεί ως εργοστάσιο και κρατά το worksheet ή το canvas όπου θα τοποθετηθεί το διάγραμμα.

```java
import com.aspose.cells.*;

public class DoughnutAndPieDemo {
    public static void main(String[] args) throws Exception {
        // Create a new workbook to host the charts
        Workbook workbook = new Workbook();
        Worksheet sheet = workbook.getWorksheets().get(0);

        // Initialize the chart builder with the worksheet
        ChartBuilder builder = new ChartBuilder(sheet);
```

**Why this matters:**  
Ο builder συνδέει το διάγραμμα με ένα συγκεκριμένο worksheet, εξασφαλίζοντας ότι όλα τα επόμενα αντικείμενα διαγράμματος μοιράζονται την ίδια επιφάνεια σχεδίασης. Η παράλειψη αυτού του βήματος θα σας άφηνε χωρίς προορισμό για τα οπτικά στοιχεία.

---

## Step 2: **Create doughnut chart**

Τώρα δημιουργούμε ένα doughnut chart με καθορισμένο μέγεθος. Το μέγεθος της τρύπας καθορίζει πόσο κενό θα είναι το κέντρο του διαγράμματος, μετατρέποντας μια κανονική πίτα σε doughnut.

```java
        // Insert a doughnut chart with a width of 500 and height of 350
        Chart doughnutChart = builder.insertChart(ChartType.DOUGHNUT, 500, 350);

        // Set the hole size to 30% of the chart radius
        doughnutChart.getDoughnutChart().setHoleSize(30);

        // Add sample data series
        doughnutChart.getNSeries().add("{10, 20, 30, 40}", true);
```

**Explanation:**  

* `insertChart(ChartType.DOUGHNUT, 500, 350)` δημιουργεί το αντικείμενο διαγράμματος και κρατά χώρο στο worksheet.  
* `setHoleSize(30)` μετατρέπει την πίτα σε doughnut με κενό 30 % στο κέντρο.  
* `add("{10, 20, 30, 40}", true)` παρέχει τέσσερα σημεία δεδομένων· η σημαία `true` λέει στη βιβλιοθήκη να θεωρήσει τις τιμές ως μία σειρά.

**Edge case:** Αν ο επιλεγμένος τύπος διαγράμματος δεν υποστηρίζει τρύπα (π.χ., ένα bar chart), η κλήση `getDoughnutChart()` ρίχνει εξαίρεση. Πάντα ελέγχετε τον τύπο διαγράμματος πριν ρυθμίσετε το μέγεθος της τρύπας.

---

## Step 3: **Insert pie chart**

Αφού το doughnut είναι έτοιμο, δείχνουμε πώς να **insert pie chart** χρησιμοποιώντας τον ίδιο builder. Αυτό το βήμα υπογραμμίζει την ομοιότητα μεταξύ των δύο τύπων διαγράμματος και δείχνει πώς να τονίσετε ένα τμήμα.

```java
        // Insert a pie chart next to the doughnut
        Chart pieChart = builder.insertChart(ChartType.PIE, 400, 300);

        // Add the same data series for consistency
        pieChart.getNSeries().add("{10, 20, 30, 40}", true);

        // Explode the first slice by 10% to draw attention
        pieChart.getSeries().get(0).setExplode(10);
```

**Explanation:**  

* `ChartType.PIE` λέει στον builder να δημιουργήσει ένα κλασικό pie chart.  
* `setExplode(10)` μετατοπίζει το πρώτο τμήμα κατά 10 % της ακτίνας, μια κοινή τεχνική για την επισήμανση ενός σημαντικού σημείου δεδομένων.  

**Tip:** Η μέθοδος `setExplode` λειτουργεί μόνο στην πρώτη σειρά ενός pie chart. Αν έχετε πολλαπλές σειρές, πρέπει να στοχεύσετε το σωστό δείκτη.

---

## Step 4: Save the workbook

Τέλος, γράψτε το workbook σε αρχείο ώστε να μπορείτε να δείτε τα διαγράμματα στο Excel ή σε οποιονδήποτε συμβατό προβολέα.

```java
        // Save the workbook to a file
        workbook.save("DoughnutAndPieChart.xlsx");
        System.out.println("Workbook created with doughnut and pie charts.");
    }
}
```

**Why save now:** Η αποθήκευση του workbook ολοκληρώνει όλες τις λειτουργίες σχεδίασης. Η προσπάθεια προβολής του αρχείου πριν την αποθήκευση οδηγεί σε κενό ή ελλιπές έγγραφο.

**Result:** Το άνοιγμα του *DoughnutAndPieChart.xlsx* εμφανίζει ένα doughnut chart με τρύπα 30 % στα αριστερά και ένα pie chart με εκτοξευμένο πρώτο τμήμα στα δεξιά.

---

## Step 5: Common variations and troubleshooting

| Situation | Adjustment |
|-----------|------------|
| **Different chart dimensions** | Αλλάξτε τα ορίσματα πλάτους και ύψους στη `insertChart`. |
| **Multiple data series** | Καλέστε `add` πολλές φορές ή περάστε μια συμβολοσειρά 2‑Δ πίνακα. |
| **Dynamic hole size** | Υπολογίστε το μέγεθος της τρύπας βάσει του εύρους δεδομένων, έπειτα καλέστε `setHoleSize`. |
| **Explode multiple slices** | Επαναλάβετε `chart.getSeries().get(i).setExplode(percent)` για κάθε τμήμα που θέλετε να μετατοπίσετε. |
| **Library not supporting doughnut** | Χρησιμοποιήστε ένα pie chart και σχεδιάστε χειροκίνητα ένα λευκό κύκλο επικάλυψης, αν και αυτό είναι λιγότερο ακριβές. |

**Pro tip:** Πάντα καλέστε `builder.flush()` (αν υπάρχει) μετά την εισαγωγή διαγραμμάτων όταν εργάζεστε με μεγάλα workbooks. Αυτό απελευθερώνει εσωτερικές μνήμες και αποτρέπει διαρροές μνήμης.

---

![Java code creating a doughnut chart and inserting a pie chart](https://example.com/images/doughnut-pie-java.png "παράδειγμα δημιουργίας doughnut chart σε Java")

*Η εικόνα απεικονίζει τη διαρρύθμιση του τελικού workbook με και τα δύο διαγράμματα δίπλα‑δίπλα.*

---

## Conclusion

Τώρα ξέρετε πώς να **create doughnut chart** και **insert pie chart** σε Java χρησιμοποιώντας ένα fluent builder API. Το πλήρες παράδειγμα καλύπτει την αρχικοποίηση, τη ρύθμιση μεγέθους, το μέγεθος τρύπας, το «exploding» τμημάτων και την έξοδο σε αρχείο. Από εδώ μπορείτε να εξερευνήσετε πρόσθετες προσαρμογές όπως χρώματα, υπομνήματα και ετικέτες δεδομένων για να ταιριάζουν στις απαιτήσεις αναφοράς σας.

**Next steps**

* Πειραματιστείτε με τις δυνατότητες **chart customization Java** όπως gradient fills και data labels.  
* Ενσωματώστε τη δημιουργία διαγράμματος σε μια web service που επιστρέφει το workbook κατ' απαίτηση.  
* Συγκρίνετε την προσέγγιση builder με άλλες βιβλιοθήκες (π.χ., JFreeChart) για να επιλέξετε την καλύτερη λύση για το έργο σας.

Happy charting!

## What Should You Learn Next?

Τα παρακάτω tutorials καλύπτουν στενά συναφή θέματα που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη, λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κυριαρχήσετε επιπλέον δυνατότητες API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στα δικά σας έργα.

- [Πώς να δημιουργήσετε doughnut chart σε έγγραφο Word με Java](/words/english/java/images-shapes/how-to-create-doughnut-chart-in-a-word-document-with-java/)
- [Αποθήκευση εγγράφου Word μετά την επεξεργασία doughnut chart σε Java](/words/english/java/using-document-elements/save-word-document-after-editing-doughnut-chart-in-java/)
- [Insert Pie Chart in Java – Explode, Rotate & Highlight Slices](/words/english/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}