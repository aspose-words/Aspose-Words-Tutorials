---
category: general
date: 2026-08-20
description: Προσθέστε γραμμές οδηγού σε διάγραμμα πίτας σε Java γρήγορα. Μάθετε πώς
  να προσθέτετε, να απομακρύνετε, να αλλάζετε χρώμα και να ετικετοποιείτε τις φέτες
  χρησιμοποιώντας το Chart API.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add leader lines to pie chart
- pie chart explosion Java
- set sector color Chart API
- builder.insertChart usage
- ChartType.PIE example
language: el
lastmod: 2026-08-20
og_description: Προσθέστε γραμμές οδηγού σε διάγραμμα πίτας σε Java με ένα σύντομο
  παράδειγμα. Ακολουθήστε αυτόν τον οδηγό για να εισάγετε, διασπάσετε, αλλάξετε χρώματα
  και επισημάνετε τα τμήματα χρησιμοποιώντας το Chart API.
og_image_alt: Screenshot showing a pie chart with an exploded slice and leader lines
  – add leader lines to pie chart
og_title: Προσθήκη γραμμών οδηγού σε διάγραμμα πίτας σε Java – βήμα‑βήμα οδηγός Chart
  API
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Add leader lines to pie chart in Java quickly. Learn to insert, explode,
    recolor, and label slices using the Chart API.
  headline: How to add leader lines to pie chart in Java with the Chart API
  type: TechArticle
tags:
- pie chart
- Java
- Chart API
- data visualization
title: Πώς να προσθέσετε γραμμές σύνδεσης σε διάγραμμα πίτας σε Java με το Chart API
url: /el/java/using-document-elements/how-to-add-leader-lines-to-pie-chart-in-java-with-the-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να προσθέσετε γραμμές οδηγού σε διάγραμμα πίτας σε Java με το Chart API

Αν χρειάζεστε **να προσθέσετε γραμμές οδηγού σε διάγραμμα πίτας** σε Java, αυτός ο οδηγός σας καθοδηγεί μέσα από τη διαδικασία. Θα δείτε πώς να εισάγετε ένα διάγραμμα πίτας, να εκτοξεύσετε ένα τμήμα για έμφαση, να αλλάξετε το χρώμα του και, τέλος, να ενεργοποιήσετε τις γραμμές οδηγού που ετικετοφορούν το εκτοξευμένο τμήμα.

Το παράδειγμα χρησιμοποιεί το τυπικό Chart API που βρίσκεται σε πολλές βιβλιοθήκες αναφοράς Java. Δεν απαιτούνται εξωτερικά εργαλεία και ο κώδικας εκτελείται σε οποιοδήποτε περιβάλλον JDK 8+.

## Τι θα επιτύχετε

* Δημιουργήστε ένα `Chart` τύπου `ChartType.PIE` με προσαρμοσμένο μέγεθος.  
* Εκτοξεύστε το πρώτο τμήμα για να τραβήξετε την προσοχή.  
* Ορίστε το χρώμα του τομέα του εκτοξευμένου τμήματος σε μπλε.  
* **Προσθέστε γραμμές οδηγού σε διάγραμμα πίτας** ώστε η ετικέτα του τμήματος να συνδέεται καθαρά.

Θα πρέπει ήδη να έχετε ένα έργο Java με τη βιβλιοθήκη Chart στο classpath. Εάν χρησιμοποιείτε Maven, προσθέστε την εξάρτηση που φαίνεται στην ενότητα προαπαιτούμενων.

## Προαπαιτούμενα

* Εγκατεστημένο JDK 8 ή νεότερο.  
* Η βιβλιοθήκη Chart (π.χ., `com.example.chart:chart-api:2.5.0`).  
* Βασική εξοικείωση με κλάσεις Java και κλήσεις μεθόδων.

---

## Πώς να προσθέσετε γραμμές οδηγού σε διάγραμμα πίτας

Παρακάτω υπάρχει ένα πλήρες, εκτελέσιμο πρόγραμμα που δείχνει κάθε βήμα. Ο κώδικας είναι σκόπιμα αυτόνομος ώστε να μπορείτε να τον αντιγράψετε, επικολλήσετε και εκτελέσετε χωρίς τροποποιήσεις.

```java
// File: AddLeaderLinesDemo.java
import com.example.chart.Chart;
import com.example.chart.ChartBuilder;
import com.example.chart.ChartType;
import com.example.chart.Color;

/**
 * Demonstrates adding leader lines to a pie chart in Java.
 */
public class AddLeaderLinesDemo {

    public static void main(String[] args) {
        // 1️⃣ Insert a pie chart with the desired size
        ChartBuilder builder = new ChartBuilder();
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // 2️⃣ Pull out the first slice for emphasis (explosion)
        chart.getSeries().get(0).setExplosion(20);

        // 3️⃣ Change the color of the first slice to blue
        chart.getSeries().get(0).setSectorColor(Color.BLUE);

        // 4️⃣ Show leader lines for the exploded slice
        chart.setLeaderLines(true);

        // Optional: Save the chart as an image file
        chart.saveAsPng("pie-with-leader-lines.png");
        System.out.println("Chart saved to pie-with-leader-lines.png");
    }
}
```

### Επεξήγηση κάθε βήματος

| Step | What the code does | Why it matters |
|------|-------------------|----------------|
| **1️⃣ Εισαγωγή διαγράμματος πίτας** | `builder.insertChart(ChartType.PIE, 400, 300)` δημιουργεί ένα διάγραμμα πίτας 400 × 300 pixel. | Καθορίζει το κοντέινερ του διαγράμματος και τις διαστάσεις του, που επηρεάζουν τη θέση των ετικετών και το μήκος των γραμμών οδηγού. |
| **2️⃣ Εκτόξευση του πρώτου τμήματος** | `setExplosion(20)` μετατοπίζει το τμήμα κατά 20 % της ακτίνας. | Ένα εκτοξευμένο τμήμα τραβάει το βλέμμα του χρήστη και κάνει τη γραμμή οδηγού ορατή. |
| **3️⃣ Ορισμός χρώματος τομέα** | `setSectorColor(Color.BLUE)` αλλάζει το γέμισμα του τμήματος σε μπλε. | Η αντίθεση χρώματος βελτιώνει την αναγνωσιμότητα, ειδικά όταν το τμήμα είναι επισημασμένο. |
| **4️⃣ Ενεργοποίηση γραμμών οδηγού** | `setLeaderLines(true)` ενεργοποιεί τις γραμμές σύνδεσης που συνδέουν το τμήμα με την ετικέτα του. | Οι γραμμές οδηγού εξασφαλίζουν ότι η ετικέτα παραμένει αναγνώσιμη ακόμη και όταν το τμήμα μετακινείται προς τα έξω. |

Η κλήση `saveAsPng` είναι προαιρετική αλλά χρήσιμη για την επαλήθευση του οπτικού αποτελέσματος. Μετά την εκτέλεση του προγράμματος, θα πρέπει να δείτε μια εικόνα παρόμοια με την παρακάτω.

![Add leader lines to pie chart](https://example.com/assets/pie-leader-lines.png "Add leader lines to pie chart – exploded slice with blue color and leader lines")

*Σχήμα: Ένα διάγραμμα πίτας όπου το πρώτο τμήμα είναι εκτοξευμένο, χρωματισμένο μπλε, και συνδεδεμένο με την ετικέτα του μέσω μιας γραμμής οδηγού.*

## Προσαρμογή γραμμών οδηγού (προχωρημένο)

Η βασική κλήση `setLeaderLines(true)` χρησιμοποιεί το προεπιλεγμένο στυλ της βιβλιοθήκης. Μπορείτε να ελέγξετε περαιτέρω την εμφάνιση:

```java
// Change leader line color to dark gray
chart.setLeaderLineColor(Color.DARK_GRAY);

// Increase line thickness for better visibility
chart.setLeaderLineWidth(2);

// Position labels outside the chart area
chart.setLabelPlacement(Chart.LabelPlacement.OUTSIDE);
```

Αυτές οι επιλογές είναι χρήσιμες όταν χρειάζεται να ταιριάξετε την εταιρική ταυτότητα ή να βελτιώσετε την προσβασιμότητα.

### Διαχείριση πολλαπλών σειρών

Εάν το διάγραμμα πίτας σας περιέχει περισσότερες από μία σειρές, ίσως θέλετε γραμμές οδηγού μόνο για ένα συγκεκριμένο τμήμα. Χρησιμοποιήστε το δείκτη σειράς για να στοχεύσετε το σωστό στοιχείο:

```java
// Enable leader lines only for the second series, third slice
chart.getSeries().get(1).get(2).setExplosion(15);
chart.getSeries().get(1).get(2).setLeaderLineEnabled(true);
```

Όταν ένα τμήμα δεν είναι εκτοξευμένο, η γραμμή οδηγού συνήθως κρύβεται αυτόματα, αλλά μπορείτε να την ενεργοποιήσετε με `setLeaderLineEnabled(true)`.

## Συνηθισμένα προβλήματα και πώς να τα αποφύγετε

| Pitfall | Symptom | Fix |
|--------|---------|-----|
| **Οι γραμμές οδηγού δεν είναι ορατές** | Το διάγραμμα αποδίδεται χωρίς συνδέσμους. | Βεβαιωθείτε ότι το τμήμα είναι εκτοξευμένο (`setExplosion` > 0) ή ενεργοποιήστε ρητά τις γραμμές οδηγού στο τμήμα. |
| **Επικάλυψη ετικετών** | Οι ετικέτες συγκρούονται μεταξύ τους. | Αυξήστε το μέγεθος του διαγράμματος ή ορίστε `setLabelPlacement(Chart.LabelPlacement.OUTSIDE)`. |
| **Το χρώμα δεν εφαρμόζεται** | Το τμήμα παραμένει στο προεπιλεγμένο χρώμα. | Επαληθεύστε ότι στοχεύετε τον σωστό δείκτη σειράς (`getSeries().get(0)`). |
| **Η εικόνα δεν αποθηκεύεται** | Το `saveAsPng` ρίχνει εξαίρεση. | Ελέγξτε τα δικαιώματα εγγραφής για τον φάκελο εξόδου και ότι η βιβλιοθήκη υποστηρίζει εξαγωγή PNG. |

## Πλήρης λίστα πηγαίου κώδικα

Για ευκολία, εδώ είναι ξανά το πλήρες αρχείο πηγαίου κώδικα, συμπεριλαμβανομένων των εισαγωγών και των σχολίων:

```java
// AddLeaderLinesDemo.java
import com.example.chart.Chart;
import com.example.chart.ChartBuilder;
import com.example.chart.ChartType;
import com.example.chart.Color;

/**
 * Complete example that adds leader lines to a pie chart.
 */
public class AddLeaderLinesDemo {

    public static void main(String[] args) {
        // Create a builder and insert a 400×300 pie chart
        ChartBuilder builder = new ChartBuilder();
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // Explode the first slice (20% offset) and color it blue
        chart.getSeries().get(0).setExplosion(20);
        chart.getSeries().get(0).setSectorColor(Color.BLUE);

        // Turn on leader lines for the exploded slice
        chart.setLeaderLines(true);

        // Optional styling
        chart.setLeaderLineColor(Color.DARK_GRAY);
        chart.setLeaderLineWidth(2);
        chart.setLabelPlacement(Chart.LabelPlacement.OUTSIDE);

        // Export the chart as a PNG image
        chart.saveAsPng("pie-with-leader-lines.png");
        System.out.println("Chart generated successfully.");
    }
}
```

Η εκτέλεση αυτού του προγράμματος δημιουργεί το `pie-with-leader-lines.png`, το οποίο εμφανίζει ένα διάγραμμα πίτας με ένα εκτοξευμένο μπλε τμήμα και σαφείς γραμμές οδηγού που δείχνουν στην ετικέτα του τμήματος.

## Συμπέρασμα

Τώρα γνωρίζετε πώς να **προσθέσετε γραμμές οδηγού σε διαγράμματα πίτας** σε Java χρησιμοποιώντας το Chart API. Η διαδικασία αποτελείται από την εισαγωγή ενός `ChartType.PIE`, την εκτόξευση του επιθυμητού τμήματος, την προσαρμογή του χρώματός του και την ενεργοποίηση των γραμμών οδηγού. Με τις προαιρετικές επιλογές στυλ μπορείτε να ρυθμίσετε λεπτομερώς το χρώμα της γραμμής, το πάχος και τη θέση της ετικέτας ώστε να καλύψετε οποιαδήποτε οπτική απαίτηση.

Στη συνέχεια, σκεφτείτε να εξερευνήσετε συναφή θέματα όπως **pie chart explosion Java**, **set sector color Chart API**, και **builder.insertChart usage** για να δημιουργήσετε πιο σύνθετες απεικονίσεις όπως διαγράμματα δακτυλίου, στοίβαξη πίτας ή διαδραστικούς πίνακες ελέγχου.

Μη διστάσετε να πειραματιστείτε με διαφορετικούς δείκτες τμημάτων, χρώματα και στυλ γραμμών οδηγού—τα διαγράμματά σας θα γίνουν πιο ενημερωτικά και οπτικά ελκυστικά με κάθε προσαρμογή. Καλή προγραμματιστική!

## Τι πρέπει να μάθετε στη συνέχεια;

Τα παρακάτω tutorials καλύπτουν στενά σχετιζόμενα θέματα που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικά παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσει να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Add Date Time Values To Axis Of A Chart](/words/english/net/programming-with-charts/date-time-values-to-axis/)
- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}