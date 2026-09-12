---
category: general
date: 2026-09-11
description: Αποθηκεύστε το έγγραφο Word μετά την επεξεργασία ενός διαγράμματος δακτυλίου
  με το Aspose.Words for Java. Μάθετε πώς να αλλάξετε το μέγεθος της τρύπας του δακτυλίου,
  να περιστρέψετε το διάγραμμα δακτυλίου και να επεξεργαστείτε τις ιδιότητες του διαγράμματος
  δακτυλίου.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save word document
- rotate doughnut chart
- edit doughnut chart
- change doughnut hole
- change chart hole size
language: el
lastmod: 2026-09-11
og_description: Αποθηκεύστε το έγγραφο Word μετά την επεξεργασία ενός διαγράμματος
  ντόνατ χρησιμοποιώντας το Aspose.Words for Java. Αυτό το σεμινάριο δείχνει πώς να
  αλλάξετε το μέγεθος της τρύπας του ντόνατ, να περιστρέψετε το διάγραμμα ντόνατ και
  να προσαρμόσετε την εμφάνιση του διαγράμματος.
og_image_alt: Java code editing a doughnut chart before saving Word document
og_title: Αποθήκευση εγγράφου Word μετά την επεξεργασία διαγράμματος δακτυλίου – Οδηγός
  Java
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Save Word document after editing a doughnut chart with Aspose.Words
    for Java. Learn how to change doughnut hole size, rotate doughnut chart, and edit
    doughnut chart properties.
  headline: Save Word document after editing doughnut chart in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word
- Chart
- Doughnut
title: Αποθήκευση εγγράφου Word μετά την επεξεργασία διαγράμματος δακτυλίου σε Java
url: /el/java/using-document-elements/save-word-document-after-editing-doughnut-chart-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Αποθήκευση εγγράφου Word μετά την επεξεργασία διαγράμματος δακτυλίου σε Java

Αν χρειάζεστε **αποθήκευση εγγράφου Word** που περιέχει προσαρμοσμένο διάγραμμα δακτυλίου, αυτός ο οδηγός σας δείχνει ακριβώς πώς. Σε λίγες μόνο γραμμές Java μπορείτε να αλλάξετε το κενό του δακτυλίου, να περιστρέψετε το διάγραμμα δακτυλίου και, στη συνέχεια, να γράψετε το αποτέλεσμα πίσω στο δίσκο.

Θα δείτε ένα πλήρες, εκτελέσιμο παράδειγμα που χρησιμοποιεί το Aspose.Words for Java, καθώς και συμβουλές για τη διαχείριση πολλαπλών διαγραμμάτων, την επαλήθευση τύπων κόμβων και την αποφυγή κοινών παγίδων. Δεν απαιτούνται εξωτερικές αναφορές — όλα όσα χρειάζεστε περιλαμβάνονται.

## Προαπαιτούμενα

- Εγκατεστημένο Java 17 ή νεότερο
- Maven ή Gradle για διαχείριση εξαρτήσεων
- Aspose.Words for Java (έκδοση 23.9 ή νεότερη) προστέθηκε στο έργο σας  
  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.9</version>
  </dependency>
  ```
- Αρχείο Word (`input.docx`) που περιέχει ένα μόνο διάγραμμα δακτυλίου

## Βήμα 1: Φόρτωση του εγγράφου Word

Το πρώτο βήμα είναι το άνοιγμα του αρχείου προέλευσης. Αυτό το βήμα είναι απαραίτητο επειδή κάθε επόμενη λειτουργία εργάζεται πάνω στο αντικείμενο `Document` στη μνήμη.

```java
import com.aspose.words.*;

public class DoughnutChartEditor {
    public static void main(String[] args) throws Exception {
        // Load the Word document that contains a doughnut chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **Γιατί;** Η φόρτωση του εγγράφου δημιουργεί μια αναπαράσταση DOM που σας επιτρέπει να διασχίζετε σχήματα, πίνακες και διαγράμματα. Εάν το αρχείο δεν μπορεί να ανοιχθεί, το Aspose.Words ρίχνει μια εξαίρεση, ώστε να γνωρίζετε αμέσως ότι η διαδρομή είναι λανθασμένη.

## Βήμα 2: Εντοπισμός του σχήματος του διαγράμματος δακτυλίου

Ένα διάγραμμα αποθηκεύεται μέσα σε έναν κόμβο `Shape`. Ανακτούμε το πρώτο σχήμα που φιλοξενεί διάγραμμα και μετατρέπουμε τον renderer του σε `Chart`.

```java
        // Find the first shape that contains a chart
        Shape chartShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);
        // Ensure the shape actually holds a chart
        if (!chartShape.isChart()) {
            throw new IllegalStateException("The first shape is not a chart.");
        }
        // Get the Chart object for further manipulation
        Chart chart = chartShape.getChart();
```

> **Γιατί;** Ο έλεγχος `isChart()` αποτρέπει ένα `ClassCastException` όταν το έγγραφο περιέχει εικόνες ή άλλα σχήματα πριν από το διάγραμμα. Αυτό κάνει τον κώδικα ανθεκτικό για έγγραφα με μεικτό περιεχόμενο.

## Βήμα 3: Αλλαγή μεγέθους κεντρικού οπού διαγράμματος δακτυλίου

Τώρα επεξεργαζόμαστε το κεντρικό άνοιγμα του δακτυλίου. Η μέθοδος `setHoleSize` αναμένει ένα ποσοστό της ακτίνας του διαγράμματος (10 – 90).

```java
        // Adjust the size of the doughnut hole (percentage of the chart radius)
        chart.setHoleSize(30);   // The hole occupies 30 % of the radius
```

> **Γιατί;** Η αλλαγή του κεντρικού οπού του δακτυλίου (`change doughnut hole` / `change chart hole size`) σας επιτρέπει να τονίσετε ή να μειώσετε την κεντρική περιοχή. Τιμές εκτός 10‑90 % αγνοούνται από το API.

## Βήμα 4: Περιστροφή του διαγράμματος δακτυλίου

Για να ελέγξετε πού ξεκινά το πρώτο τμήμα, ορίστε τη γωνία του πρώτου τμήματος. Αυτό ουσιαστικά **περιστρέφει το διάγραμμα δακτυλίου**.

```java
        // Rotate the chart so that the first slice starts at a custom angle
        chart.setFirstSliceAngle(45);   // Starts the first slice at 45 degrees
```

> **Γιατί;** Η περιστροφή του διαγράμματος είναι χρήσιμη όταν θέλετε ένα συγκεκριμένο τμήμα να εμφανίζεται στην κορυφή ή να ταιριάζει με μια προδιαγραφή σχεδίασης.

## Βήμα 5: Αποθήκευση του ενημερωμένου εγγράφου

Τέλος, γράψτε τις αλλαγές πίσω σε ένα νέο αρχείο. Αυτή είναι η στιγμή που **αποθηκεύετε το έγγραφο Word** με το επεξεργασμένο διάγραμμα.

```java
        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

> **Αναμενόμενο αποτέλεσμα:** Το `output.docx` περιέχει το αρχικό περιεχόμενο, αλλά το διάγραμμα δακτυλίου έχει τώρα κενό 30 % και το πρώτο τμήμα αρχίζει στις 45 °. Το άνοιγμα του αρχείου στο Microsoft Word θα εμφανίσει το μετασχηματισμένο διάγραμμα.

## Πλήρες λειτουργικό παράδειγμα

Παρακάτω είναι το πλήρες πρόγραμμα που μπορείτε να αντιγράψετε‑και‑επικολλήσετε στο IDE σας. Περιλαμβάνει όλες τις εισαγωγές και τη διαχείριση σφαλμάτων που απαιτούνται για την **επεξεργασία διαγράμματος δακτυλίου** και την **αποθήκευση εγγράφου Word** με ασφάλεια.

```java
import com.aspose.words.*;

public class DoughnutChartEditor {
    public static void main(String[] args) throws Exception {
        // 1. Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Locate the first chart shape
        Shape chartShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);
        if (!chartShape.isChart()) {
            throw new IllegalStateException("The first shape is not a chart.");
        }
        Chart chart = chartShape.getChart();

        // 3. Change the doughnut hole size
        chart.setHoleSize(30); // 30 % hole

        // 4. Rotate the doughnut chart
        chart.setFirstSliceAngle(45); // start at 45°

        // 5. Save the modified document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### Αναμενόμενη έξοδος

Όταν ανοίξετε το `output.docx`:

- Το κεντρικό άνοιγμα του διαγράμματος δακτυλίου καταλαμβάνει περίπου το ένα τρίτο της ακτίνας του διαγράμματος.  
- Το πρώτο τμήμα αρχίζει στη θέση των 45 μοιρών, μετατοπίζοντας ολόκληρο το διάγραμμα δεξιόστροφα.  

## Συνηθισμένες παραλλαγές και ακραίες περιπτώσεις

| Κατάσταση | Πώς να το διαχειριστείτε |
|-----------|--------------------------|
| **Πολλαπλά διαγράμματα** | Επανάληψη μέσω `doc.getChildNodes(NodeType.SHAPE, true)` και φιλτράρισμα με `shape.isChart()`· εφαρμόστε `setHoleSize` / `setFirstSliceAngle` σε κάθε `Chart`. |
| **Το διάγραμμα δεν είναι δακτύλιος** | Ελέγξτε `chart.getType()`· καλέστε `setHoleSize` μόνο όταν `chart.getType() == ChartType.DOUGHNUT`. |
| **Απαιτείται δυναμική αλλαγή του μεγέθους του οπού** | Υπολογίστε το επιθυμητό ποσοστό βάσει των τιμών των δεδομένων, στη συνέχεια καλέστε `setHoleSize(computedValue)`. |
| **Αποθήκευση σε ροή** | Use |

## Τι Θα Πρέπει Να Μάθετε Στη Σειρά;

Οι παρακάτω εκπαιδευτικοί οδηγίες καλύπτουν στενά σχετιζόμενα θέματα που επεκτείνουν τις τεχνικές που παρουσιάζονται σε αυτόν τον οδηγό. Κάθε πόρος περιλαμβάνει ολοκληρωμένα παραδείγματα κώδικα με βήμα‑βήμα εξηγήσεις για να σας βοηθήσουν να κατακτήσετε πρόσθετες δυνατότητες του API και να εξερευνήσετε εναλλακτικές προσεγγίσεις υλοποίησης στα δικά σας έργα.

- [Πώς να δημιουργήσετε διάγραμμα στήλης χρησιμοποιώντας το Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Πώς να αποθηκεύσετε έγγραφο ως pdf με το Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Αποθήκευση Word με κωδικό πρόσβασης χρησιμοποιώντας το Aspose.Words for Java](/words/english/java/document-loading-and-saving/advance-saving-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}