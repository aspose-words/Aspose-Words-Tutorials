---
category: general
date: 2026-09-24
description: Εισαγωγή διαγράμματος πίτας σε αρχείο DOCX χρησιμοποιώντας το Aspose.Words
  for Java. Μάθετε πώς να ορίζετε το μέγεθος της τρύπας, να εκτοξεύετε το κομμάτι
  της πίτας, να επισημαίνετε το κομμάτι του διαγράμματος πίτας και να δημιουργείτε
  διαγράμματα DOCX με ευκολία.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart word
- set hole size
- explode pie slice
- highlight pie chart slice
- create docx chart
language: el
lastmod: 2026-09-24
og_description: Εισαγωγή διαγράμματος πίτας σε DOCX με το Aspose.Words for Java. Μάθετε
  να ορίζετε το μέγεθος της τρύπας, να εκτοξεύετε το κομμάτι της πίτας, να επισημαίνετε
  τμήμα διαγράμματος πίτας και να δημιουργείτε διάγραμμα DOCX σε λίγα λεπτά.
og_image_alt: Screenshot of a Word document displaying a formatted pie chart created
  with Java
og_title: Εισαγωγή λέξης διαγράμματος πίτας σε Java – βήμα‑βήμα οδηγός
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Insert pie chart word in a DOCX using Aspose.Words for Java. Learn
    to set hole size, explode pie slice, highlight pie chart slice, and create docx
    chart effortlessly.
  headline: Insert pie chart word in Java – complete guide
  type: TechArticle
- description: Insert pie chart word in a DOCX using Aspose.Words for Java. Learn
    to set hole size, explode pie slice, highlight pie chart slice, and create docx
    chart effortlessly.
  name: Insert pie chart word in Java – complete guide
  steps:
  - name: Prerequisites
    text: '* Java 17 or later (the code compiles with Java 8 as well) * Aspose.Words
      for Java library (version 23.9 or newer) * An IDE or build tool (Maven/Gradle)
      that can resolve the Aspose.Words dependency'
  - name: Why this matters
    text: '`Document` represents the whole Word file, while `DocumentBuilder` is the
      high‑level API that lets you insert paragraphs, tables, and charts without dealing
      with low‑level XML. Starting with a clean document ensures that the chart you
      add is the only content, which is perfect for learning or for gen'
  - name: Practical tip
    text: If you later decide to switch to a doughnut chart, simply change the `holeSize`
      value to a percentage (e.g., `30`). The same API works for both chart types.
  - name: Why explode?
    text: An exploded slice draws the reader’s eye to the most important data point—perfect
      for dashboards or executive summaries. The value `20` means 20 % of the radius;
      you can adjust it between `0` (no explosion) and `100` (fully detached).
  - name: Expert note
    text: Changing the fill color of a specific slice requires accessing the `DataPoint`
      object. If you have multiple series, iterate through `series.getDataPoints()`
      and apply styles conditionally.
  - name: Pro tip
    text: Always call `setHoleSize(0)` **after** `insertChart`. If you set it before
      insertion, Aspose.Words will revert to the default doughnut size once the chart
      is created.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart formatting
title: Εισαγωγή λέξης διαγράμματος πίτας σε Java – πλήρης οδηγός
url: /el/java/using-document-elements/insert-pie-chart-word-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Εισαγωγή pie chart word σε Java – πλήρης οδηγός

Αν χρειάζεστε να **insert pie chart word** σε αρχείο DOCX, αυτό το tutorial σας δείχνει ακριβώς πώς να το κάνετε με το Aspose.Words for Java. Θα δείτε τη πλήρη ροή εργασίας από τη δημιουργία του εγγράφου μέχρι την προσαρμογή του διαγράμματος ώστε το τμήμα να εκτοξευθεί, το μέγεθος της τρύπας να οριστεί σε μηδέν και το τμήμα να επισημανθεί.

Η εργασία με διαγράμματα σε έγγραφα Word συχνά φαίνεται ως ξεχωριστό ζήτημα από την κανονική επεξεργασία κειμένου, αλλά το Aspose.Words ενοποιεί και τα δύο. Σ τα παρακάτω βήματα θα μάθετε επίσης πώς να **create docx chart** αρχεία που είναι έτοιμα να ανοιχτούν στο Microsoft Word, Google Docs ή σε οποιονδήποτε άλλο προβολέα συμβατό με DOCX.

## Τι θα πετύχετε

* **Insert pie chart word** σε ένα κενό έγγραφο  
* **Set hole size** για να μετατρέψετε το διάγραμμα σε πλήρη πίτα (χωρίς doughnut)  
* **Explode pie slice** για να τραβήξετε την προσοχή σε ένα συγκεκριμένο τμήμα  
* **Highlight pie chart slice** με προσαρμοσμένη μορφοποίηση  
* **Create docx chart** που μπορεί να μοιραστεί ή να επεξεργαστεί περαιτέρω  

### Προαπαιτούμενα

* Java 17 ή νεότερη (ο κώδικας συντάσσεται επίσης με Java 8)  
* Βιβλιοθήκη Aspose.Words for Java (έκδοση 23.9 ή νεότερη)  
* Ένα IDE ή εργαλείο κατασκευής (Maven/Gradle) που μπορεί να επιλύσει την εξάρτηση Aspose.Words  

```xml
<!-- Example Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

---

## Πώς να insert pie chart word σε DOCX χρησιμοποιώντας Aspose.Words

Το πρώτο βήμα είναι να δημιουργήσετε ένα νέο κενό έγγραφο και να αποκτήσετε ένα `DocumentBuilder`. Ο builder σας δίνει άμεση πρόσβαση στο ρεύμα περιεχομένου του εγγράφου, καθιστώντας εύκολο το **insert pie chart word**.

```java
import com.aspose.words.*;

public class PieChartFormattingDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

### Γιατί είναι σημαντικό
`Document` αντιπροσωπεύει ολόκληρο το αρχείο Word, ενώ `DocumentBuilder` είναι το υψηλού επιπέδου API που σας επιτρέπει να εισάγετε παραγράφους, πίνακες και διαγράμματα χωρίς να ασχοληθείτε με XML χαμηλού επιπέδου. Ξεκινώντας με ένα καθαρό έγγραφο εξασφαλίζει ότι το διάγραμμα που προσθέτετε είναι το μοναδικό περιεχόμενο, κάτι ιδανικό για εκμάθηση ή για δημιουργία αναφορών βασισμένων σε πρότυπα.

## Ορίστε το μέγεθος τρύπας για να δημιουργήσετε πλήρη πίτα

Από προεπιλογή, το Aspose.Words δημιουργεί ένα διάγραμμα doughnut όταν ζητάτε ένα διάγραμμα πίτας. Για να κάνετε το διάγραμμα πραγματικό κύκλο, πρέπει να **set hole size** στο `0`. Αυτό αφαιρεί την εσωτερική τρύπα και δίνει μια κλασική εμφάνιση πίτας.

```java
        // Step 2: Insert a pie chart with a specific size
        Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);

        // Step 4: Ensure the chart is a full pie (no doughnut hole)
        pieChart.getChart().setHoleSize(0);   // set hole size to zero
```

### Πρακτική συμβουλή
Αν αργότερα αποφασίσετε να μεταβείτε σε διάγραμμα doughnut, απλώς αλλάξτε την τιμή `holeSize` σε ποσοστό (π.χ., `30`). Το ίδιο API λειτουργεί και για τους δύο τύπους διαγράμματος.

## Εκτοξευστε τμήμα πίτας για να επισημάνετε ένα τμήμα

Η εκτόξευση ενός τμήματος το κάνει να ξεχωρίζει οπτικά. Η λειτουργία **explode pie slice** μετακινεί το επιλεγμένο τμήμα προς τα έξω κατά ένα ποσοστό της ακτίνας του διαγράμματος.

```java
        // Step 3: Explode the first slice to highlight it
        pieChart.getChart().getSeries().get(0).setExplosion(20); // explode pie slice
```

### Γιατί να εκτοξευτεί;
Ένα εκτοξευμένο τμήμα τραβά το βλέμμα του αναγνώστη στο πιο σημαντικό σημείο δεδομένων—ιδανικό για πίνακες ελέγχου ή εκτελεστικές περιλήψεις. Η τιμή `20` σημαίνει 20 % της ακτίνας· μπορείτε να την προσαρμόσετε μεταξύ `0` (χωρίς εκτόξευση) και `100` (πλήρως αποσπασμένο).

## Επισημάνετε τμήμα διαγράμματος πίτας με προσαρμοσμένη μορφοποίηση

Πέρα από την εκτόξευση, ίσως θέλετε να **highlight pie chart slice** αλλάζοντας το χρώμα γεμίσματος ή το περίγραμμα του. Ενώ ο κώδικας επίδειξης εστιάζει στην εκτόξευση, μπορείτε να τον επεκτείνετε ως εξής:

```java
        // Optional: Change fill color of the exploded slice
        ChartSeries series = pieChart.getChart().getSeries().get(0);
        series.getDataPoints().get(0).getFormat().setFillColor(java.awt.Color.RED);
```

### Σημείωση ειδικού
Η αλλαγή του χρώματος γεμίσματος ενός συγκεκριμένου τμήματος απαιτεί πρόσβαση στο αντικείμενο `DataPoint`. Εάν έχετε πολλαπλές σειρές, επαναλάβετε μέσω `series.getDataPoints()` και εφαρμόστε στυλ υπό όρους.

## Αποθήκευση και επαλήθευση του δημιουργημένου docx chart

Τέλος, **create docx chart** αποθηκεύοντας το `Document`. Το προκύπτον αρχείο μπορεί να ανοιχθεί στο Microsoft Word για να δείτε το μορφοποιημένο διάγραμμα πίτας.

```java
        // Step 5: Save the document with the formatted pie chart
        doc.save("YOUR_DIRECTORY/PieChartFormatted.docx");
    }
}
```

#### Αναμενόμενο αποτέλεσμα
Το άνοιγμα του `PieChartFormatted.docx` εμφανίζει ένα μόνο διάγραμμα πίτας:

* Το διάγραμμα καταλαμβάνει περιοχή 400 × 300 pt.  
* Το μέγεθος τρύπας είναι `0`, έτσι το διάγραμμα είναι πλήρης πίτα.  
* Το πρώτο τμήμα εκτοξεύεται κατά 20 % και χρωματίζεται κόκκινο (αν προσθέσατε την προαιρετική μορφοποίηση).  

Τώρα έχετε ένα **create docx chart** που μπορεί να διανεμηθεί, να ενσωματωθεί σε email ή να επεξεργαστεί περαιτέρω προγραμματιστικά.

---

## Συνηθισμένες παραλλαγές και ειδικές περιπτώσεις

| Σενάριο | Πώς να προσαρμόσετε τον κώδικα |
|----------|----------------------|
| **Multiple series** | Επανάληψη πάνω από `pieChart.getChart().getSeries()` και ορισμός `Explosion` ή `FillColor` ανά σειρά. |
| **Dynamic data** | Συμπληρώστε τις σειρές με τιμές από βάση δεδομένων ή CSV πριν καλέσετε `setExplosion`. |
| **Different chart size** | Αλλάξτε τα επιχειρήματα πλάτους/ύψους στο `insertChart(ChartType.PIE, width, height)`. |
| **Export to PDF** | Μετά την αποθήκευση του DOCX, καλέστε `doc.save("output.pdf")` για να δημιουργήσετε μια έκδοση PDF του ίδιου διαγράμματος. |
| **Localization** | Χρησιμοποιήστε `DocumentBuilder.insertChart` με μορφοποίηση αριθμών ειδική για την τοπική ρύθμιση για τις ετικέτες. |

### Συμβουλή επαγγελματία
Πάντα καλέστε `setHoleSize(0)` **μετά** το `insertChart`. Αν το ορίσετε πριν από την εισαγωγή, το Aspose.Words θα επανέλθει στο προεπιλεγμένο μέγεθος doughnut μόλις δημιουργηθεί το διάγραμμα.

---

## Ανακεφαλαίωση

Τώρα ξέρετε πώς να **insert pie chart word** σε έγγραφο Word χρησιμοποιώντας Java, πώς να **set hole size** για εμφάνιση πλήρους πίτας, πώς να **explode pie slice** για να τραβήξετε την προσοχή, και πώς να **highlight pie chart slice** με προσαρμοσμένα χρώματα. Το πλήρες παράδειγμα δείχνει επίσης πώς να **create docx chart** αρχεία που είναι έτοιμα για διανομή.

---

## Επόμενα βήματα

* Εξερευνήστε άλλους τύπους διαγραμμάτων (`BAR`, `LINE`, `SCATTER`) με `ChartType`.  
* Συνδυάστε τη δημιουργία διαγράμματος με mail merge για να παράγετε εξατομικευμένες αναφορές.  
* Ενσωματώστε το παραγόμενο DOCX σε μια υπηρεσία web που επιστρέφει το αρχείο κατόπιν ζήτησης.  

Αν αντιμετωπίσετε προβλήματα, θυμηθείτε να ελέγξετε ότι χρησιμοποιείτε μια συμβατή έκδοση του Aspose.Words και ότι ο φάκελος εξόδου υπάρχει και είναι εγγράψιμος.

Καλή προγραμματιστική!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κυριαρχήσετε σε πρόσθετες δυνατότητες API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Πώς να δημιουργήσετε διάγραμμα στήλης χρησιμοποιώντας Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Χρήση Word Chart API](/words/english/net/programming-with-charts/)
- [Εισαγωγή Bubble Chart σε Word χρησιμοποιώντας Aspose.Words for .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}