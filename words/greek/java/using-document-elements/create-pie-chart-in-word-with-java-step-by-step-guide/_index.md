---
category: general
date: 2026-08-14
description: Δημιουργήστε διάγραμμα πίτας στο Word με Java χρησιμοποιώντας το Aspose.Words.
  Μάθετε πώς να προσθέσετε δεδομένα σειράς στο διάγραμμα και να περιστρέψετε το τμήμα
  του διαγράμματος πίτας με λίγες μόνο γραμμές.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart in word
- how to add series data to chart
- rotate pie chart slice
- Aspose.Words chart API
- Java document automation
language: el
lastmod: 2026-08-14
og_description: Δημιουργήστε διάγραμμα πίτας στο Word με Java χρησιμοποιώντας το Aspose.Words.
  Αυτό το σεμινάριο δείχνει πώς να προσθέσετε δεδομένα σειράς στο διάγραμμα και να
  περιστρέψετε γρήγορα ένα τμήμα του διαγράμματος πίτας.
og_image_alt: Screenshot of a Word document containing a colorful pie chart generated
  by Java code
og_title: Δημιουργία διαγράμματος πίτας στο Word με Java – πλήρης οδηγός κωδικοποίησης
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Create pie chart in Word with Java using Aspose.Words. Learn how to
    add series data to chart and rotate pie chart slice in just a few lines.
  headline: Create pie chart in Word with Java – step-by-step guide
  type: TechArticle
- description: Create pie chart in Word with Java using Aspose.Words. Learn how to
    add series data to chart and rotate pie chart slice in just a few lines.
  name: Create pie chart in Word with Java – step-by-step guide
  steps:
  - name: Why use Aspose.Words?
    text: '* **No Microsoft Office required** – the library works on any server or
      CI environment. * **Full .docx fidelity** – the generated chart looks identical
      to one created manually in Word. * **Single‑file dependency** – just add the
      JAR and you’re ready to go.'
  - name: Expected output
    text: '* A file named **PieChart.docx** appears in the `output` folder. * Opening
      the file in Microsoft Word shows a colorful pie chart with three slices (40
      %, 30 %, 30 %). * The chart is rotated 45° clockwise, so the first slice starts
      slightly to the right of the vertical axis.'
  - name: Tips for production use
    text: '* **Reuse the `DocumentBuilder`** – you can insert multiple charts in the
      same document by calling `insertChart` repeatedly. * **Styling** – use `chart.getSeries().get(0).getDataLabels().setShowPercentage(true);`
      to display percentages directly on the chart. * **Performance** – generate the
      chart on'
  - name: What’s next?
    text: '* Explore other chart types (`ChartType.BAR`, `ChartType.LINE`) to broaden
      your automation toolkit. * Combine chart generation with **mail merge** to produce
      personalized reports for each recipient. * Dive into the **Styling API** (`ChartFormat`,
      `DataLabel`, `ChartTitle`) to match your corporate br'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Δημιουργία διαγράμματος πίτας στο Word με Java – οδηγός βήμα‑βήμα
url: /el/java/using-document-elements/create-pie-chart-in-word-with-java-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία διαγράμματος πίτας στο Word με Java – οδηγός βήμα‑βήμα

Αν χρειάζεστε να **δημιουργήσετε διάγραμμα πίτας στο Word** προγραμματιστικά, αυτός ο οδηγός σας δείχνει ακριβώς πώς να το κάνετε με Java και Aspose.Words. Θα μάθετε τη πλήρη ροή εργασίας, από την εισαγωγή του διαγράμματος μέχρι την προσθήκη σημείων δεδομένων και την περιστροφή του πρώτου τμήματος.

Η δημιουργία ενός διαγράμματος απευθείας σε αρχείο `.docx` αφαιρεί το χειροκίνητο βήμα αντιγραφής‑επικόλλησης και σας επιτρέπει να αυτοματοποιήσετε αναφορές, τιμολόγια ή πίνακες ελέγχου. Καθ' όλη τη διάρκεια θα καλύψουμε επίσης **πώς να προσθέσετε δεδομένα σειράς σε διάγραμμα** και πώς να **περιστρέψετε τμήμα διαγράμματος πίτας** για καλύτερη οπτική έμφαση.

## Δημιουργία διαγράμματος πίτας στο Word – επισκόπηση

Aspose.Words for Java παρέχει ένα ευέλικτο API `DocumentBuilder` που μπορεί να εισάγει ένα αντικείμενο διαγράμματος σε ένα έγγραφο Word. Ο τύπος διαγράμματος που επιλέγετε καθορίζει την προεπιλεγμένη διάταξη, και μπορείτε να προσαρμόσετε τις σειρές, τα χρώματα, τις γωνίες και ακόμη και να μεταβείτε σε σχήμα δακτυλίου με μία κλήση μεθόδου.

### Γιατί να χρησιμοποιήσετε το Aspose.Words;

* **Δεν απαιτείται Microsoft Office** – η βιβλιοθήκη λειτουργεί σε οποιονδήποτε διακομιστή ή περιβάλλον CI.  
* **Πλήρης πιστότητα .docx** – το παραγόμενο διάγραμμα φαίνεται ταυτόσημο με αυτό που δημιουργείται χειροκίνητα στο Word.  
* **Εξάρτηση ενός μόνο αρχείου** – απλώς προσθέστε το JAR και είστε έτοιμοι.

## Πώς να προσθέσετε δεδομένα σειράς σε διάγραμμα

Ένα διάγραμμα χωρίς δεδομένα είναι μόνο ένας κράτημα θέσης. Το αντικείμενο `Chart` εκθέτει μια συλλογή `Series`; κάθε σειρά περιέχει μια λίστα αριθμητικών τιμών που αντιστοιχούν σε τμήματα (για πίτα) ή σημεία (για γραμμή). Η προσθήκη δεδομένων είναι απλή:

```java
// Add three values to the first (and only) series of the pie chart
chart.getSeries().get(0).add(40); // 40 % of the whole
chart.getSeries().get(0).add(30); // 30 %
chart.getSeries().get(0).add(30); // remaining 30 %
```

**Τι κάνει ο κώδικας:**  
* `chart.getSeries()` επιστρέφει μια `List<ChartSeries>`.  
* `get(0)` επιλέγει την πρώτη σειρά επειδή ένα διάγραμμα πίτας περιέχει μόνο μία σειρά κατά ορισμό.  
* `add(double)` προσθέτει ένα σημείο δεδομένων. Οι τιμές μετατρέπονται αυτόματα σε ποσοστά που αθροίζουν στο 100 % όταν το διάγραμμα αποδίδεται.

> **Συμβουλή:** Εάν η πηγή δεδομένων σας περιέχει περισσότερες από τρεις κατηγορίες, συνεχίστε να προσθέτετε τιμές με τον ίδιο τρόπο. Το Aspose.Words θα δημιουργήσει αυτόματα επιπλέον τμήματα.

## Περιστροφή τμήματος διαγράμματος πίτας

Μερικές φορές θέλετε ένα συγκεκριμένο τμήμα να ξεκινάει σε συγκεκριμένη γωνία ώστε το πιο σημαντικό τμήμα να κατευθύνεται προς τον θεατή. Η μέθοδος `setFirstSliceAngle(double)` περιστρέφει ολόκληρο το διάγραμμα, μετακινώντας ουσιαστικά την αρχή του πρώτου τμήματος:

```java
// Rotate the chart so that the first slice starts at 45 degrees
chart.setFirstSliceAngle(45);
```

Η γωνία μετριέται σε μοίρες δεξιόστροφα από τον κατακόρυφο άξονα. Ορίζοντάς την σε `0` (η προεπιλογή) τοποθετεί το πρώτο τμήμα στην κορυφή. Ρυθμίστε την τιμή για να τονίσετε ένα τμήμα ή να ταιριάξετε με μια οδηγία σχεδίασης.

> **Συχνή ερώτηση:** *Επηρεάζει η περιστροφή τη σειρά των δεδομένων;*  
> Όχι. Η σειρά των δεδομένων παραμένει η ίδια· μόνο η οπτική θέση εκκίνησης αλλάζει.

## Πλήρες παράδειγμα Java

Παρακάτω υπάρχει ένα πλήρες, έτοιμο‑για‑εκτέλεση πρόγραμμα που δημιουργεί ένα έγγραφο Word με διάγραμμα πίτας, προσθέτει δεδομένα σειράς, περιστρέφει το τμήμα και αποθηκεύει το αρχείο. Όλες οι απαιτούμενες εισαγωγές παρατίθενται, ώστε να μπορείτε να αντιγράψετε τον κώδικα σε οποιοδήποτε IDE.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartInWord {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a PIE chart with a width of 400 points and a height of 300 points
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // 3️⃣ Add data points to the first (and only) series
        chart.getSeries().get(0).add(40); // Slice 1
        chart.getSeries().get(0).add(30); // Slice 2
        chart.getSeries().get(0).add(30); // Slice 3

        // 4️⃣ Rotate the start angle so the first slice begins at 45°
        chart.setFirstSliceAngle(45);

        // 5️⃣ (Optional) If you prefer a doughnut chart, uncomment the next line
        // chart.setHoleSize(0.5); // hole size between 0.0 (pie) and 1.0 (empty)

        // 6️⃣ Save the document – adjust the path as needed
        String outPath = "output/PieChart.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### Αναμενόμενο αποτέλεσμα

* Ένα αρχείο με όνομα **PieChart.docx** εμφανίζεται στο φάκελο `output`.  
* Ανοίγοντας το αρχείο στο Microsoft Word εμφανίζεται ένα πολύχρωμο διάγραμμα πίτας με τρία τμήματα (40 %, 30 %, 30 %).  
* Το διάγραμμα είναι περιστραμμένο 45° δεξιόστροφα, έτσι ώστε το πρώτο τμήμα να ξεκινά ελαφρώς δεξιά από τον κατακόρυφο άξονα.

## Συνηθισμένα προβλήματα και βέλτιστες πρακτικές

| Πρόβλημα | Γιατί συμβαίνει | Διόρθωση |
|----------|----------------|----------|
| **Το διάγραμμα εμφανίζεται κενό** | Το έγγραφο αποθηκεύτηκε πριν το διάγραμμα αποδοθεί πλήρως. | Κλήση `doc.save()` **μετά** από όλες τις τροποποιήσεις του διαγράμματος. |
| **Οι τιμές των τμημάτων δεν αθροίζουν στο 100 %** | Η προσθήκη ακατέργαστων αριθμών που δεν αντιπροσωπεύουν ποσοστά μπορεί να οδηγήσει σε απροσδόκητη κλιμάκωση. | Παρέχετε τιμές που αντιπροσωπεύουν λογικά τμήματα ενός συνόλου, ή αφήστε το Aspose.Words να υπολογίσει αυτόματα τα ποσοστά. |
| **Η περιστροφή δεν έχει αποτέλεσμα** | Η χρήση `ChartType.DOUGHNUT` χωρίς ορισμό `holeSize` μπορεί να κρύβει το αποτέλεσμα της περιστροφής. | Διατηρήστε το διάγραμμα ως `PIE` ή προσαρμόστε το `holeSize` μετά τον ορισμό της γωνίας. |
| **Σφάλματα διαδρομής αρχείου** | Οι σχετικές διαδρομές μπορεί να επιλύονται διαφορετικά σε Windows vs. Linux. | Χρησιμοποιήστε `Paths.get("output", "PieChart.docx").toString()` ή μια απόλυτη διαδρομή για κώδικα παραγωγής. |

### Συμβουλές για χρήση σε παραγωγή

* **Επαναχρησιμοποίηση του `DocumentBuilder`** – μπορείτε να εισάγετε πολλαπλά διαγράμματα στο ίδιο έγγραφο καλώντας επανειλημμένα το `insertChart`.  
* **Στυλ** – χρησιμοποιήστε `chart.getSeries().get(0).getDataLabels().setShowPercentage(true);` για να εμφανίσετε τα ποσοστά απευθείας στο διάγραμμα.  
* **Απόδοση** – δημιουργήστε το διάγραμμα μία φορά και κλωνοποιήστε το (`chart.deepClone()`) εάν χρειάζεστε ίδια διαγράμματα σε πολλαπλές θέσεις.

## Περιστροφή τμήματος διαγράμματος πίτας – προχωρημένα σενάρια

* **Δυναμική γωνία** – υπολογίστε τη γωνία βάσει των δεδομένων (π.χ., κάντε το μεγαλύτερο τμήμα να ξεκινάει στην κορυφή).  
  ```java
  double maxValue = Collections.max(chart.getSeries().get(0).getDataPoints());
  double total = chart.getSeries().get(0).getDataPoints().stream().mapToDouble(Double::doubleValue).sum();
  double startAngle = 360 * (maxValue / total) / 2; // Center the largest slice
  chart.setFirstSliceAngle(startAngle);
  ```
* **Πολλαπλές σειρές** – ενώ ένα διάγραμμα πίτας συνήθως έχει μία σειρά, το Aspose.Words σας επιτρέπει να προσθέσετε περισσότερες για στοίβαξη πινών. Η περιστροφή εξακολουθεί να ισχύει μόνο για την πρώτη σειρά.

## Συμπέρασμα

Τώρα γνωρίζετε πώς να **δημιουργήσετε διάγραμμα πίτας στο Word** χρησιμοποιώντας Java, πώς να **προσθέσετε δεδομένα σειράς σε διάγραμμα**, και πώς να **περιστρέψετε τμήμα διαγράμματος πίτας** για οπτική έμφαση. Το πλήρες παράδειγμα παρουσιάζει ολόκληρη τη ροή εργασίας—από την αρχικοποίηση του εγγράφου μέχρι την αποθήκευση του τελικού αρχείου `.docx`—ώστε να ενσωματώσετε τη δημιουργία διαγράμματος σε οποιοδήποτε αυτοματοποιημένο σύστημα αναφορών.

### Τι θα ακολουθήσει;

* Εξερευνήστε άλλους τύπους διαγραμμάτων (`ChartType.BAR`, `ChartType.LINE`) για να διευρύνετε το εργαλείο αυτοματοποίησής σας.  
* Συνδυάστε τη δημιουργία διαγράμματος με **mail merge** για να παράγετε εξατομικευμένες αναφορές για κάθε παραλήπτη.  
* Βυθιστείτε στο **Styling API** (`ChartFormat`, `DataLabel`, `ChartTitle`) για να ταιριάξετε με την εταιρική σας ταυτότητα.

Μη διστάσετε να πειραματιστείτε με διαφορετικά σύνολα δεδομένων, γωνίες και στυλ διαγράμματος. Καλή προγραμματιστική!

## Τι Θα Πρέπει Να Μάθετε Στη Σύντομη Επόμενη

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Πώς να δημιουργήσετε γράφημα στήλης χρησιμοποιώντας Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Πώς να δημιουργήσετε πεδία φόρμας και να προσθέσετε περιεχόμενο χρησιμοποιώντας DocumentBuilder στο Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Πώς να μετατρέψετε Word σε PDF χρησιμοποιώντας Aspose.Words for Java](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}