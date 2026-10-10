---
category: general
date: 2026-10-10
description: Μάθετε πώς να περιστρέφετε ένα γράφημα σε αρχείο Word και να τροποποιείτε
  το γράφημα στο Word για να αλλάξετε το μέγεθος του γραφήματος τύπου δακτυλίου με
  ένα πλήρες παράδειγμα Java.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to rotate chart
- modify chart in word
- change doughnut chart size
- Aspose.Words chart manipulation
- Java chart API
language: el
lastmod: 2026-10-10
og_description: Πώς να περιστρέψετε ένα γράφημα σε αρχείο Word και να τροποποιήσετε
  το γράφημα στο Word για να αλλάξετε το μέγεθος του διαγράμματος δακτυλίου χρησιμοποιώντας
  το Aspose.Words για Java.
og_image_alt: Screenshot showing a rotated doughnut chart after applying how to rotate
  chart steps
og_title: Πώς να περιστρέψετε το διάγραμμα σε ένα έγγραφο Word – βήμα‑βήμα οδηγός
  Java
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Learn how to rotate chart in a Word file and modify chart in Word to
    change doughnut chart size with a complete Java example.
  headline: How to rotate chart in a Word document using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Πώς να περιστρέψετε το διάγραμμα σε ένα έγγραφο Word χρησιμοποιώντας το Aspose.Words
url: /el/java/document-manipulation/how-to-rotate-chart-in-a-word-document-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να περιστρέψετε διάγραμμα σε έγγραφο Word χρησιμοποιώντας Aspose.Words

Αν χρειάζεστε **how to rotate chart** μέσα σε αρχείο Microsoft Word, αυτός ο οδηγός σας δείχνει τα ακριβή βήματα. Θα μάθετε επίσης πώς να **modify chart in Word** για **change doughnut chart size** χωρίς να αφήσετε τον κώδικα Java.

Η αυτοματοποίηση του Word συχνά φαίνεται σαν μια σειρά από αποσυνδεδεμένες κλήσεις API, αλλά με το Aspose.Words μπορείτε να αντιμετωπίσετε ένα διάγραμμα όπως οποιονδήποτε άλλο κόμβο του εγγράφου. Στο τέλος αυτού του tutorial θα έχετε ένα εκτελέσιμο πρόγραμμα που φορτώνει ένα υπάρχον `.docx`, περιστρέφει ένα διάγραμμα δακτυλίου κατά 45°, μειώνει το κενό στο 50 % της ακτίνας, και αποθηκεύει το αποτέλεσμα ως νέο αρχείο.

## Προαπαιτούμενα

* Εγκατεστημένο Java 17 ή νεότερο.
* Maven (ή Gradle) για διαχείριση εξαρτήσεων.
* Ένα αρχείο εισόδου Word (`input.docx`) που ήδη περιέχει διάγραμμα δακτυλίου.
* Ένα έγκυρο license Aspose.Words for Java (ή χρήση της λειτουργίας αξιολόγησης).

## Βήμα 1: Ρύθμιση του έργου Maven

Δημιουργήστε ένα νέο έργο Maven ή προσθέστε την ακόλουθη εξάρτηση στο υπάρχον `pom.xml` σας:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest version available -->
</dependency>
```

Η εκτέλεση του `mvn clean install` θα κατεβάσει τη βιβλιοθήκη και θα κάνει τις κλάσεις διαθέσιμες στο classpath σας.

## Βήμα 2: Φόρτωση του εγγράφου Word που περιέχει διάγραμμα

Η πρώτη ενέργεια είναι το άνοιγμα του υπάρχοντος εγγράφου. Η κλάση `Document` αντιπροσωπεύει ολόκληρο το αρχείο.

```java
import com.aspose.words.*;

public class RotateDoughnutChart {
    public static void main(String[] args) throws Exception {
        // Load a document that already contains a chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

Η φόρτωση του αρχείου **δεν** το τροποποιεί· δημιουργεί απλώς μια αναπαράσταση στη μνήμη που μπορείτε να ερωτήσετε και να επεξεργαστείτε.

## Βήμα 3: Δημιουργία DocumentBuilder για πλοήγηση

`DocumentBuilder` σας παρέχει ένα API τύπου κέρσορα για περιήγηση στο δέντρο του εγγράφου. Θα το χρησιμοποιήσουμε για να εντοπίσουμε το πρώτο σχήμα διαγράμματος.

```java
        // Create a DocumentBuilder for the loaded document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Ο builder ξεκινά στην αρχή του εγγράφου, αλλά μπορείτε να τον μετακινήσετε σε οποιονδήποτε κόμβο αργότερα, εάν χρειαστεί.

## Βήμα 4: Ανάκτηση του πρώτου σχήματος διαγράμματος

Τα διαγράμματα αποθηκεύονται ως κόμβοι `Shape`. Φιλτράροντας τα παιδικά κόμβους τύπου `NodeType.SHAPE` μπορούμε να εξάγουμε το αντικείμενο διαγράμματος.

```java
        // Retrieve the first chart shape from the document
        Shape chartShape = (Shape) builder.getCurrentParagraph()
                .getChildNodes(NodeType.SHAPE, true)
                .get(0);

        // Cast the shape's renderer to a Chart object
        Chart chart = chartShape.getChart();
```

Αν το έγγραφο περιέχει πολλαπλά διαγράμματα, μπορείτε να επαναλάβετε μέσω του `getChildNodes` και να ελέγξετε κάθε `Shape` για `hasChart()` πριν το μετατρέψετε.

## Βήμα 5: Περιστροφή του διαγράμματος (how to rotate chart)

Ένα διάγραμμα δακτυλίου είναι ουσιαστικά ένα διάγραμμα πίτας με τρύπα. Η περιστροφή του αλλάζει τη γωνία έναρξης του πρώτου τμήματος.

```java
        // Rotate the chart by setting its start angle to 45 degrees
        chart.setStartAngle(45.0);
```

Η μέθοδος `setStartAngle` αναμένει ένα double που αντιπροσωπεύει μοίρες. Οι θετικές τιμές περιστρέφουν δεξιόστροφα, ενώ οι αρνητικές τιμές αριστερόστροφα.

## Βήμα 6: Αλλαγή του μεγέθους της τρύπας του δακτυλίου (change doughnut chart size)

Το μέγεθος της τρύπας εκφράζεται ως κλάσμα της ακτίνας του διαγράμματος. Μια τιμή `0.5` σημαίνει ότι η τρύπα καταλαμβάνει το 50 % της συνολικής ακτίνας.

```java
        // Adjust the doughnut hole size to 50 %
        chart.setDoughnutHoleSize(0.5);
```

**Συμβουλή:** Η έγκυρη περιοχή είναι `0.0` (χωρίς τρύπα, δηλαδή κανονική πίτα) έως `0.9` (πολύ λεπτός δακτύλιος). Τιμές εκτός αυτής της περιοχής θα προκαλέσουν `IllegalArgumentException`.

## Βήμα 7: Αποθήκευση του τροποποιημένου εγγράφου

Τέλος, γράψτε τις αλλαγές πίσω στο δίσκο.

```java
        // Save the modified document
        doc.save("YOUR_DIRECTORY/DoughnutFormatted.docx");
    }
}
```

Όταν ανοίξετε το `DoughnutFormatted.docx` στο Microsoft Word, θα δείτε το διάγραμμα δακτυλίου να έχει περιστραφεί 45° και η τρύπα να έχει μειωθεί στο μισό του αρχικού μεγέθους.

## Πλήρες, εκτελέσιμο παράδειγμα

Συνδυάζοντας όλα τα κομμάτια, εδώ είναι το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε‑επικολλήσετε στο IDE σας:

```java
import com.aspose.words.*;

public class RotateDoughnutChart {
    public static void main(String[] args) throws Exception {
        // Load a document that already contains a chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Create a DocumentBuilder for the loaded document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Retrieve the first chart shape from the document
        Shape chartShape = (Shape) builder.getCurrentParagraph()
                .getChildNodes(NodeType.SHAPE, true)
                .get(0);

        // Ensure the shape actually contains a chart
        if (!chartShape.hasChart()) {
            System.out.println("No chart found in the first shape.");
            return;
        }

        // Cast the shape's renderer to a Chart object
        Chart chart = chartShape.getChart();

        // Rotate the chart by setting its start angle to 45 degrees
        chart.setStartAngle(45.0);

        // Adjust the doughnut hole size to 50 %
        chart.setDoughnutHoleSize(0.5);

        // Save the modified document
        doc.save("YOUR_DIRECTORY/DoughnutFormatted.docx");

        System.out.println("Chart rotated and doughnut size changed successfully.");
    }
}
```

### Αναμενόμενη έξοδος

Η εκτέλεση του προγράμματος εμφανίζει:

```
Chart rotated and doughnut size changed successfully.
```

Ανοίγοντας το `DoughnutFormatted.docx` εμφανίζεται ένα διάγραμμα δακτυλίου του οποίου το πρώτο τμήμα ξεκινά στη θέση 45° και η εσωτερική ακτίνα καταλαμβάνει το μισό της εξωτερικής ακτίνας.

## Συνηθισμένες παραλλαγές και περιπτώσεις άκρων

| Κατάσταση | Τι να προσαρμόσετε | Γιατί είναι σημαντικό |
|-----------|--------------------|------------------------|
| **Multiple charts** | Επανάληψη μέσω `getChildNodes(NodeType.SHAPE, true)` και έλεγχος `shape.hasChart()` για κάθε ένα | Εξασφαλίζει ότι τροποποιείτε το επιθυμητό διάγραμμα αντί για το πρώτο |
| **Bar or line chart** | `setStartAngle` δεν εφαρμόζεται· χρησιμοποιήστε `chart.getSeries().get(0).setFillFormat(...)` για άλλες οπτικές προσαρμογές | Δεν υποστηρίζουν όλα τα είδη διαγραμμάτων την περιστροφή· μόνο τα διαγράμματα δακτυλίου/πίτας έχουν γωνία έναρξης |
| **Chart without a doughnut hole** | Παραλείψτε το `setDoughnutHoleSize` ή πρώτα μετατρέψτε τον τύπο διαγράμματος σε δακτύλιο μέσω `chart.setChartType(ChartType.DONUT)` | Η αλλαγή του μεγέθους της τρύπας σε διάγραμμα που δεν είναι δακτύλιος προκαλεί εξαίρεση |
| **Large documents** | Χρησιμοποιήστε `DocumentBuilder.moveToDocumentStart()` και `builder.moveToNode(chartShape)` για στοχευμένη πλοήγηση | Βελτιώνει την απόδοση αποφεύγοντας την πλήρη διάσχιση μη σχετικών κόμβων |

## Επαγγελματικές συμβουλές για αξιόπιστη διαχείριση διαγραμμάτων

* **Cache the chart reference** – Εάν σκοπεύετε να τροποποιήσετε πολλές ιδιότητες, κρατήστε μια τοπική μεταβλητή `Chart` αντί να καλείτε επανειλημμένα το `chartShape.getChart()`.
* **Validate input values** – Πριν καλέσετε `setStartAngle` ή `setDoughnutHoleSize`, επαληθεύστε το εύρος για να αποφύγετε σφάλματα χρόνου εκτέλεσης.
* **Use a license** – Η λειτουργία αξιολόγησης προσθέτει υδατογράφημα στην πρώτη σελίδα. Η εφαρμογή άδειας (`License license = new License(); license.setLicense("Aspose.Words.lic");`) το αφαιρεί.

## Επόμενα βήματα

Τώρα που γνωρίζετε **how to rotate chart** και **change doughnut chart size**, μπορείτε να εξερευνήσετε άλλα σενάρια **modify chart in Word**:

* Αλλάξτε τα χρώματα των τμημάτων με `chart.getSeries().get(0).getDataPoints().get(i).getFillFormat().setForeColor(Color.getRed())`.
* Προσθέστε ετικέτες δεδομένων καλώντας `chart.getSeries().get(0).setHasDataLabel(true)`.
* Εξάγετε το διάγραμμα ως εικόνα χρησιμοποιώντας `chart.toImage(300, 300, ImageType.PNG)`.

Κάθε μία από αυτές τις επεκτάσεις ακολουθεί το ίδιο μοτίβο: αποκτήστε το αντικείμενο `Chart`, καλέστε την κατάλληλη μέθοδο setter και αποθηκεύστε το έγγραφο.

**Μόλις κατακτήσατε την περιστροφή και την αλλαγή μεγέθους των διαγραμμάτων δακτυλίου στο Word χρησιμοποιώντας Java.** Μη διστάσετε να προσαρμόσετε τον κώδικα για άλλους τύπους διαγραμμάτων, να τον ενσωματώσετε σε μια μεγαλύτερη αλυσίδα δημιουργίας εγγράφων ή να το συνδυάσετε με το Aspose.Slides για αυτοματοποίηση PowerPoint. Καλή προγραμματιστική!

## Τι Θα Πρέπει Να Μάθετε Στη Σειρά;

Τα παρακάτω tutorials καλύπτουν στενά σχετικές θεματικές που βασίζονται στις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει πλήρη παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Πώς να δημιουργήσετε διάγραμμα στήλης χρησιμοποιώντας Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Απόκρυψη Άξονα Διαγράμματος σε Έγγραφο Word](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Εισαγωγή Διάγραμμα Φούσκας σε Έγγραφο Word](/words/english/net/programming-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}