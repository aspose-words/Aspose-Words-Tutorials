---
title: Χρήση υδατογραφημάτων σε έγγραφα στο Aspose.Words για Java
linktitle: Χρήση υδατογραφημάτων σε έγγραφα
second_title: Aspose.Words Java Document Processing API
description: Μάθετε πώς να προσθέτετε υδατογραφήματα σε έγγραφα στο Aspose.Words για Java. Προσαρμόστε τα υδατογραφήματα κειμένου και εικόνας για έγγραφα επαγγελματικής εμφάνισης.
weight: 15
url: /el/java/document-conversion-and-export/using-watermarks-to-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Χρήση υδατογραφημάτων σε έγγραφα στο Aspose.Words για Java


## Εισαγωγή στην προσθήκη υδατογραφημάτων σε έγγραφα στο Aspose.Words για Java

Σε αυτό το σεμινάριο, θα διερευνήσουμε τον τρόπο προσθήκης υδατογραφημάτων σε έγγραφα χρησιμοποιώντας το Aspose.Words for Java API. Τα υδατογραφήματα είναι ένας χρήσιμος τρόπος για την επισήμανση εγγράφων με κείμενο ή γραφικά για να υποδεικνύεται η κατάστασή τους, η εμπιστευτικότητα ή άλλες σχετικές πληροφορίες. Θα καλύψουμε τόσο τα υδατογραφήματα κειμένου όσο και εικόνων σε αυτόν τον οδηγό.

## Ρύθμιση του Aspose.Words για Java

Πριν αρχίσουμε να προσθέτουμε υδατογραφήματα σε έγγραφα, πρέπει να ρυθμίσουμε το Aspose.Words για Java. Ακολουθήστε αυτά τα βήματα για να ξεκινήσετε:

1.  Κατεβάστε το Aspose.Words για Java από[εδώ](https://releases.aspose.com/words/java/).
2. Προσθέστε τη βιβλιοθήκη Aspose.Words for Java στο έργο σας Java.
3. Εισαγάγετε τις απαραίτητες κλάσεις στον κώδικα Java σας.

Τώρα που έχουμε ρυθμίσει τη βιβλιοθήκη, ας προχωρήσουμε στην προσθήκη υδατογραφημάτων.

## Προσθήκη υδατογραφημάτων κειμένου

Τα υδατογραφήματα κειμένου είναι μια κοινή επιλογή όταν θέλετε να προσθέσετε πληροφορίες κειμένου στα έγγραφά σας. Δείτε πώς μπορείτε να προσθέσετε ένα υδατογράφημα κειμένου χρησιμοποιώντας το Aspose.Words για Java:

```java
// Δημιουργήστε μια παρουσία εγγράφου
Document doc = new Document("Document.docx");

// Ορισμός Επιλογών TextWatermark
TextWatermarkOptions options = new TextWatermarkOptions();
options.setFontFamily("Arial");
options.setFontSize(36f);
options.setColor(Color.BLACK);
options.setLayout(WatermarkLayout.HORIZONTAL);
options.setSemitransparent(false);

//Ορίστε το κείμενο και τις επιλογές του υδατογραφήματος
doc.getWatermark().setText("Test", options);

// Αποθηκεύστε το έγγραφο με το υδατογράφημα
doc.save("DocumentWithWatermark.docx");
```

## Προσθήκη υδατογραφημάτων εικόνας

Εκτός από τα υδατογραφήματα κειμένου, μπορείτε επίσης να προσθέσετε υδατογραφήματα εικόνας στα έγγραφά σας. Δείτε πώς μπορείτε να προσθέσετε ένα υδατογράφημα εικόνας:

```java
// Δημιουργήστε μια παρουσία εγγράφου
Document doc = new Document("Document.docx");

// Φορτώστε την εικόνα για το υδατογράφημα
byte[] imageBytes = Files.readAllBytes(Paths.get("watermark.png"));
Shape watermark = new Shape(doc, ShapeType.IMAGE);
watermark.getImageData().setImage(imageBytes);

// Ρυθμίστε το μέγεθος και τη θέση του υδατογραφήματος
watermark.setWidth(200.0);
watermark.setHeight(100.0);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.CENTER);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.CENTER);

// Προσθέστε το υδατογράφημα στο έγγραφο
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// Αποθηκεύστε το έγγραφο με το υδατογράφημα
doc.save("DocumentWithImageWatermark.docx");
```

## Προσαρμογή υδατογραφημάτων

Μπορείτε να προσαρμόσετε τα υδατογραφήματα προσαρμόζοντας την εμφάνιση και τη θέση τους. Για τα υδατογραφήματα κειμένου, μπορείτε να αλλάξετε τη γραμματοσειρά, το μέγεθος, το χρώμα και τη διάταξη. Για τα υδατογραφήματα εικόνας, μπορείτε να τροποποιήσετε το μέγεθος και τη θέση τους όπως φαίνεται στα προηγούμενα παραδείγματα.

## Αφαίρεση υδατογραφημάτων

Για να αφαιρέσετε υδατογραφήματα από ένα έγγραφο, μπορείτε να χρησιμοποιήσετε τον ακόλουθο κώδικα:

```java
// Δημιουργήστε μια παρουσία εγγράφου
Document doc = new Document("DocumentWithWatermark.docx");

// Αφαιρέστε το υδατογράφημα
for (Shape shape : doc.getShapes())
{
    if (shape.getName().contains("Watermark"))
    {
        shape.remove();
    }
}

// Αποθηκεύστε το έγγραφο χωρίς το υδατογράφημα
doc.save("DocumentWithoutWatermark.docx");
```


## Σύναψη

Σε αυτό το σεμινάριο, μάθαμε πώς να προσθέτουμε υδατογραφήματα σε έγγραφα χρησιμοποιώντας το Aspose.Words για Java. Είτε θέλετε να προσθέσετε υδατογραφήματα κειμένου είτε εικόνας, το Aspose.Words παρέχει τα εργαλεία για την αποτελεσματική προσαρμογή και διαχείριση τους. Μπορείτε επίσης να αφαιρέσετε υδατογραφήματα όταν δεν χρειάζονται πλέον, διασφαλίζοντας ότι τα έγγραφά σας είναι καθαρά και επαγγελματικά.

## Συχνές ερωτήσεις

### Πώς μπορώ να αλλάξω τη γραμματοσειρά ενός υδατογραφήματος κειμένου;

 Για να αλλάξετε τη γραμματοσειρά ενός υδατογραφήματος κειμένου, τροποποιήστε το`setFontFamily` ιδιοκτησία στο`TextWatermarkOptions`. Για παράδειγμα:

```java
options.setFontFamily("Times New Roman");
```

### Μπορώ να προσθέσω πολλά υδατογραφήματα σε ένα μόνο έγγραφο;

 Ναι, μπορείτε να προσθέσετε πολλά υδατογραφήματα σε ένα έγγραφο δημιουργώντας πολλά`Shape` αντικείμενα με διαφορετικές ρυθμίσεις και την προσθήκη τους στο έγγραφο.

### Είναι δυνατή η περιστροφή ενός υδατογραφήματος;

 Ναι, μπορείτε να περιστρέψετε ένα υδατογράφημα ρυθμίζοντας το`setRotation` ιδιοκτησία στο`Shape` αντικείμενο. Οι θετικές τιμές περιστρέφουν το υδατογράφημα δεξιόστροφα και οι αρνητικές τιμές το περιστρέφουν αριστερόστροφα.

### Πώς μπορώ να κάνω ένα υδατογράφημα ημιδιαφανές;

 Για να κάνετε ένα υδατογράφημα ημιδιαφανές, ορίστε το`setSemitransparent`ιδιοκτησία σε`true` στο`TextWatermarkOptions`.

### Μπορώ να προσθέσω υδατογραφήματα σε συγκεκριμένες ενότητες ενός εγγράφου;

Ναι, μπορείτε να προσθέσετε υδατογραφήματα σε συγκεκριμένες ενότητες ενός εγγράφου επαναλαμβάνοντας τις ενότητες και προσθέτοντας το υδατογράφημα στις επιθυμητές ενότητες.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
