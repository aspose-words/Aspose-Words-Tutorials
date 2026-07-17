---
category: general
date: 2026-07-16
description: Δημιουργήστε διάγραμμα πίτας σε Java χρησιμοποιώντας το Aspose.Words.
  Μάθετε πώς να προσθέσετε γραμμές οδηγίας, να εμφανίσετε το υπόμνημα του διαγράμματος
  και να αποσπάσετε ένα τμήμα σε ένα ενιαίο σεμινάριο.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- add leader lines
- show chart legend
- how to explode slice
- how to add legend
language: el
lastmod: 2026-07-16
og_description: Δημιουργήστε διάγραμμα πίτας σε Java χρησιμοποιώντας το Aspose.Words.
  Αυτός ο οδηγός δείχνει πώς να προσθέσετε γραμμές οδηγού, να εμφανίσετε το υπόμνημα
  του διαγράμματος και να «σπάσετε» ένα τμήμα, παρέχοντάς σας ένα επαγγελματικό οπτικό
  αποτέλεσμα σε λίγα λεπτά.
og_image_alt: Screenshot of a Java‑generated pie chart with an exploded slice and
  visible legend
og_title: Δημιουργία διαγράμματος πίτας με Aspose.Words Java – Πλήρης οδηγός μορφοποίησης
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: Create pie chart in Java using Aspose.Words. Learn how to add leader
    lines, show chart legend, and explode a slice in a single tutorial.
  headline: Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide
  type: TechArticle
- description: Create pie chart in Java using Aspose.Words. Learn how to add leader
    lines, show chart legend, and explode a slice in a single tutorial.
  name: Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide
  steps:
  - name: Java 17 (or later) installed.
    text: Java 17 (or later) installed.
  - name: Aspose.Words for Java JAR on your classpath.
    text: Aspose.Words for Java JAR on your classpath.
  - name: A basic IDE or text editor—IntelliJ IDEA, Eclipse, VS Code, whatever you
      prefer.
    text: A basic IDE or text editor—IntelliJ IDEA, Eclipse, VS Code, whatever you
      prefer.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart Formatting
- Data Visualization
title: Δημιουργία διαγράμματος πίτας με το Aspose.Words Java – Πλήρης οδηγός βήμα‑βήμα
url: /el/java/using-document-elements/create-pie-chart-with-aspose-words-java-full-step-by-step-gu/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία Πίτας Γραφήματος με Aspose.Words Java – Πλήρης Οδηγός Βήμα‑Βήμα

Έχετε αναρωτηθεί ποτέ πώς να **δημιουργήσετε γράφημα πίτας** προγραμματιστικά σε Java χωρίς να παλεύετε με API χαμηλού επιπέδου; Δεν είστε οι μόνοι. Πολλοί προγραμματιστές χρειάζονται ένα γρήγορο οπτικό στοιχείο για αναφορές, πίνακες ελέγχου ή αυτοματοποιημένα έγγραφα, και στρέφονται στο Aspose.Words επειδή αναλαμβάνει το δύσκολο κομμάτι.  

Σε αυτό το tutorial θα περάσουμε από ένα πλήρες, έτοιμο‑για‑εκτέλεση παράδειγμα που όχι μόνο **δημιουργεί ένα γράφημα πίτας** αλλά και σας δείχνει πώς να **προσθέσετε γραμμές οδηγού**, **εμφανίσετε το υπόμνημα του γραφήματος**, και ακόμη **εξαπολύσετε ένα τμήμα** για έμφαση. Στο τέλος θα έχετε ένα αρχείο `.docx` που φαίνεται τόσο επαγγελματικό ώστε να εντυπωσιάσει έναν πελάτη.

> **Γρήγορο κέρδος:** Το παρακάτω απόσπασμα κώδικα λειτουργεί αμέσως με το Aspose.Words for Java 23.9 (ή οποιαδήποτε νεότερη έκδοση). Δεν απαιτούνται επιπλέον εξαρτήσεις, μόνο το JAR.

## Τι Θα Μάθετε

- Δημιουργία ενός κεντρικού εγγράφου Word με `DocumentBuilder`.
- Εισαγωγή **γράφηματος πίτας** προσαρμοσμένου μεγέθους.
- Χρήση της λειτουργίας **explode slice** για να τονίσετε ένα σημείο δεδομένων.
- Ενεργοποίηση **γραμμών οδηγού** ώστε το εξαρθέντο τμήμα να παραμένει συνδεδεμένο με την ετικέτα.
- Ενεργοποίηση **legend** του γραφήματος ώστε οι αναγνώστες να αναγνωρίζουν αμέσως κάθε τμήμα.
- Αποθήκευση του αποτελέσματος σε αρχείο `.docx` που μπορείτε να ανοίξετε με Microsoft Word ή LibreOffice.

**Προαπαιτούμενα** – Θα χρειαστείτε:

1. Java 17 (ή νεότερη) εγκατεστημένη.
2. Aspose.Words for Java JAR στο classpath σας.
3. Ένα βασικό IDE ή κειμενογράφο — IntelliJ IDEA, Eclipse, VS Code, ό,τι προτιμάτε.

Τώρα, ας βουτήξουμε.

## Βήμα 1: Αρχικοποίηση του Εγγράφου και του Builder – Προετοιμασία για **δημιουργία πίτας γραφήματος**

Πρώτα, χρειαζόμαστε έναν καθαρό καμβά εγγράφου. Το `Document` αντιπροσωπεύει ολόκληρο το αρχείο Word, ενώ το `DocumentBuilder` είναι ο βοηθός που μας επιτρέπει να προσθέτουμε περιεχόμενο.

```java
import com.aspose.words.*;

public class PieChartFormattingDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();               // the container for our Word file
        DocumentBuilder builder = new DocumentBuilder(doc); // convenient API for adding elements
```

> **Γιατί είναι σημαντικό:** Ξεκινώντας με ένα φρέσκο `Document` εξασφαλίζετε ότι δεν υπάρχουν κρυφά στυλ ή αντικείμενα που θα μπορούσαν να επηρεάσουν την απόδοση του γραφήματος.

## Βήμα 2: Εισαγωγή του **γράφηματος πίτας** – Το μέγεθος μετρά

Το Aspose.Words κάνει την εισαγωγή γραφήματος με μία γραμμή κώδικα. Εδώ ζητάμε ένα γράφημα πίτας 400 × 300 points — περίπου 5,5 × 4,2 ίντσες σε τυπική οθόνη.

```java
        // Step 2: Insert a pie chart of size 400x300 points
        Shape chartShape = builder.insertChart(ChartType.PIE, 400, 300);
        Chart chart = chartShape.getChart(); // the underlying chart object we will format
```

> **Pro tip:** Αν χρειάζεστε διαφορετικό μέγεθος, απλώς αλλάξτε τα δύο αριθμητικά ορίσματα. Το API λειτουργεί σε points, όπου 72 points = 1 ίντσα.

## Βήμα 3: **Πώς να εξαπολύσετε τμήμα** – Τονίζοντας ένα βασικό σημείο δεδομένων

Η εξαπόλυση ενός τμήματος το απομακρύνει από το υπόλοιπο της πίτας, τραβώντας το βλέμμα του αναγνώστη. Η μέθοδος `setExplosion` δέχεται έναν ακέραιο που αντιπροσωπεύει την απόσταση σε points.

```java
        // Step 3: Explode the first slice to emphasize it
        chart.getSeries().get(0).setExplosion(10); // 10 points outward
```

> **Τι γίνεται αν έχετε πολλαπλές σειρές;** Μπορείτε να καλέσετε `setExplosion` σε οποιονδήποτε δείκτη σειράς (`get(1)`, `get(2)`, …) για να εξαπολύσετε διαφορετικά τμήματα.

## Βήμα 4: **Προσθήκη γραμμών οδηγού** και **εμφάνιση legend** – Σύνδεση των σημείων

Όταν ένα τμήμα εξαπολύεται, η ετικέτα μπορεί να απομακρυνθεί. Οι γραμμές οδηγού κρατούν την ετικέτα δεμένη, διατηρώντας την αναγνωσιμότητα. Ταυτόχρονα, ένα legend προσφέρει ένα γρήγορο κλειδί για όλα τα τμήματα.

```java
        // Step 4: Enable leader lines for the exploded slice and show the legend
        chart.getSeries().get(0).setLeaderLines(true); // draws a line from slice to its label
        chart.setShowLegend(true);                     // makes the legend visible below the chart
```

> **Γιατί να ενεργοποιήσετε τις γραμμές οδηγού;** Χωρίς αυτές, η ετικέτα μπορεί να φαίνεται «αιωρούμενη», προκαλώντας σύγχυση για το σε ποιο τμήμα ανήκει.  
> **Χρειάζεστε προσαρμοσμένη θέση legend;** Χρησιμοποιήστε `chart.getLegend().setPosition(LegendPosition.TOP)` ή οποιαδήποτε άλλη τιμή του enum.

## Βήμα 5: Αποθήκευση του Εγγράφου – Το τελικό βήμα **δημιουργίας πίτας γραφήματος**

Τέλος, αποθηκεύουμε το έγγραφο στο δίσκο. Προσαρμόστε τη διαδρομή σε έναν φάκελο όπου έχετε δικαιώματα εγγραφής.

```java
        // Step 5: Save the document with the formatted pie chart
        doc.save("YOUR_DIRECTORY/PieChartDemo.docx");
    }
}
```

Εκτελέστε το πρόγραμμα, ανοίξτε το παραγόμενο `PieChartDemo.docx`, και θα δείτε ένα ωραία μορφοποιημένο γράφημα πίτας με το πρώτο τμήμα εξαπολυμένο, γραμμές οδηγού και ορατό legend.

![Pie chart example showing exploded slice and legend](pie-chart-example.png){: .center-image alt="Παράδειγμα δημιουργίας γραφήματος πίτας με εξαπολυμένο τμήμα, γραμμές οδηγού και legend"}

### Αναμενόμενο Αποτέλεσμα

Όταν ανοίξετε το αρχείο Word, το γράφημα θα μοιάζει περίπου έτσι:

- Γράφημα πίτας 400 × 300 pt.
- Το πρώτο τμήμα είναι μετατοπισμένο κατά 10 pt.
- Μία λεπτή γραμμή οδηγού συνδέει το εξαπολυμένο τμήμα με την ετικέτα του.
- Ένα legend κάτω από το γράφημα καταγράφει το όνομα κάθε σειράς.

Αν δεν δείτε τη γραμμή οδηγού, ελέγξτε ξανά ότι το `setLeaderLines(true)` καλείται *μετά* την ρύθμιση της εξαπόλυσης — η σειρά είναι σημαντική.

## Συνηθισμένα Προβλήματα και Πώς να τα Αποφύγετε

| Πρόβλημα | Γιατί συμβαίνει | Διόρθωση |
|----------|----------------|----------|
| **Δεν εμφανίζεται legend** | Η κλήση `setShowLegend(true)` λείπει ή έγινε σε λάθος αντικείμενο γραφήματος. | Βεβαιωθείτε ότι καλείτε `chart.setShowLegend(true)` **μετά** την ανάκτηση του `Chart` από το shape. |
| **Λείπει η γραμμή οδηγού** | Το τμήμα δεν εξαπολύθηκε, ή ο τύπος γραφήματος δεν υποστηρίζει γραμμές οδηγού. | Μόνο `ChartType.PIE` (ή `PIE_3D`) υποστηρίζει γραμμές οδηγού. Καλέστε πρώτα `setExplosion`, μετά `setLeaderLines(true)`. |
| **Το τμήμα δεν κινείται** | Η τιμή εξαπόλυσης είναι πολύ μικρή (0‑2 pt). | Αυξήστε τον ακέραιο, π.χ. `setExplosion(10)` ή μεγαλύτερο για πιο έντονη επίδραση. |
| **Το γράφημα φαίνεται παραμορφωμένο** | Η χρήση μη τετράγωνου μεγέθους (πλάτος ≠ ύψος) μπορεί να «σπρώξει» την πίτα. | Κρατήστε το πλάτος και το ύψος ίσα ή κοντά· 400 × 300 λειτουργεί, αλλά 400 × 400 δίνει τέλειο κύκλο. |

## Προχωρημένες Ρυθμίσεις (Προαιρετικά)

Αν θέλετε να πάτε πέρα από τα βασικά, σκεφτείτε:

- **Προσαρμοσμένα χρώματα**: `chart.getSeries().get(0).getDataPoints().get(i).getFormat().getFill().setForeColor(Color.RED);`
- **Ετικέτες δεδομένων**: `chart.getSeries().get(0).setDataLabelType(ChartDataLabelType.CATEGORY);`
- **Εφέ 3‑Δ**: Αντικαταστήστε `ChartType.PIE` με `ChartType.PIE_3D`.

Αυτές οι επιλογές σας επιτρέπουν να προσαρμόσετε το οπτικό στοιχείο ώστε να ταιριάζει με τις εταιρικές οδηγίες branding.

## Ανακεφαλαίωση – Τι Καταφέραμε

Ξεκινήσαμε με ένα κενό έγγραφο Word, **δημιουργήσαμε ένα γράφημα πίτας**, **εξαπολύσαμε το πρώτο τμήμα**, **προσθέσαμε γραμμές οδηγού**, και **εμφανίσαμε το legend**. Η ολόκληρη ροή χωράει σε μια σύντομη μέθοδο `main`, καθιστώντας την εύκολη ενσωμάτωση σε μεγαλύτερους αγωγούς αναφορών.

## Επόμενα Βήματα

- **Προσθήκη περισσότερων σειρών**: Συμπληρώστε το γράφημα με πραγματικά δεδομένα από βάση ή CSV.
- **Εξαγωγή σε PDF**: Χρησιμοποιήστε `doc.save("output.pdf", SaveFormat.PDF);` για να δημιουργήσετε έκδοση PDF.
- **Συνδυασμός με άλλα σχήματα**: Εισάγετε πίνακες, εικόνες ή επιπλέον γραφήματα για μια πλήρη αναφορά.

Αν σας ενδιαφέρουν άλλοι τύποι γραφημάτων — στήλη, μπάρα, γραμμή — απλώς αντικαταστήστε το `ChartType.PIE` με το αντίστοιχο enum και ακολουθήστε τα ίδια βήματα μορφοποίησης.

---

*Καλή δημιουργία γραφημάτων!* Μη διστάσετε να αφήσετε ένα σχόλιο αν κάτι δεν λειτούργησε όπως περιμένατε, ή να μοιραστείτε πώς προσαρμόσατε τη θέση του legend. Η ανατροφοδότησή σας βοηθά όλους μας να δημιουργούμε καλύτερα αυτοματοποιημένα έγγραφα.

## Τι Πρέπει να Μάθετε Στη Σύντομη Επόμενη

Τα παρακάτω tutorials καλύπτουν στενά συναφείς θεματικές που επεκτείνουν τις τεχνικές που παρουσιάστηκαν σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη λειτουργικό κώδικα με βήμα‑βήμα εξηγήσεις για να κυριαρχήσετε σε επιπλέον δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις στα δικά σας έργα.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [How to Create PDF Documents with Aspose.Words for Java | Document Processing API](/words/english/java/)
- [How to Add Watermark to Documents Using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}