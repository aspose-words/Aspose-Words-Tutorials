---
date: 2026-02-19
description: Μάθετε πώς να δημιουργείτε έγγραφα με υδατογράφημα χρησιμοποιώντας το
  Aspose.Words για Java και να προσθέτετε υδατογράφημα εικόνας σε Java για επαγγελματικά
  έγγραφα.
linktitle: Using Watermarks to Documents
second_title: Aspose.Words Java Document Processing API
title: Δημιουργία εγγράφου με υδατογράφημα χρησιμοποιώντας το Aspose.Words για Java
url: /el/java/document-conversion-and-export/using-watermarks-to-documents/
weight: 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία εγγράφου με υδατογράφημα χρησιμοποιώντας το Aspose.Words for Java

Σε αυτό το tutorial θα **δημιουργήσετε έγγραφο με υδατογράφημα** χρησιμοποιώντας το API Aspose.Words for Java. Τα υδατογραφήματα—είτε κείμενο είτε εικόνες—σας βοηθούν να επισημάνετε ένα αρχείο ως εμπιστευτικό, πρόχειρο ή εγκεκριμένο, και μπορούν να εφαρμοστούν προγραμματιστικά σε οποιοδήποτε έγγραφο Word. Θα περάσουμε από τη ρύθμιση της βιβλιοθήκης, την προσθήκη τόσο κειμενικών όσο και εικόνων υδατογραφήματος, την προσαρμογή της εμφάνισής τους, και ακόμη και την αφαίρεσή τους όταν δεν χρειάζονται πια.

## Γρήγορες Απαντήσεις
- **Τι κάνει ένα υδατογράφημα;** Επικαλύπτει κείμενο ή εικόνα σε κάθε σελίδα για να μεταφέρει κατάσταση ή branding.  
- **Ποια βιβλιοθήκη προσθέτει υδατογραφήματα σε Java;** Το Aspose.Words for Java παρέχει ενσωματωμένη υποστήριξη υδατογραφημάτων.  
- **Μπορώ να προσθέσω υδατογράφημα εικόνας;** Ναι—χρησιμοποιήστε την κλάση `Shape` και την προσέγγιση `add image watermark java`.  
- **Το υδατογράφημα είναι ημιδιαφανές;** Μπορείτε να ελέγξετε την αδιαφάνεια μέσω του `setSemitransparent` για κειμενικά υδατογραφήματα.  
- **Χρειάζομαι άδεια;** Μια δωρεάν δοκιμή λειτουργεί για δοκιμές· απαιτείται εμπορική άδεια για παραγωγή.

## Τι είναι ένα υδατογράφημα και γιατί να το χρησιμοποιήσετε;

Ένα υδατογράφημα είναι μια αχνή επικάλυψη—κειμενική ή γραφική—που προστίθεται σε κάθε σελίδα ενός εγγράφου. Χρησιμοποιείται συνήθως για να υποδείξει **εμπιστευτικότητα**, **κατάσταση πρόχειρου**, ή **branding** χωρίς να αλλάζει το υποκείμενο περιεχόμενο. Η προσθήκη υδατογραφημάτων προγραμματιστικά εξασφαλίζει συνέπεια σε μεγάλες παρτίδες αρχείων και εξοικονομεί χρόνο σε σύγκριση με την χειροκίνητη επεξεργασία.

## Ρύθμιση του Aspose.Words for Java

Πριν αρχίσουμε να προσθέτουμε υδατογραφήματα, βεβαιωθείτε ότι η βιβλιοθήκη είναι έτοιμη στο έργο σας:

1. Κατεβάστε το Aspose.Words for Java από [εδώ](https://releases.aspose.com/words/java/).  
2. Προσθέστε το κατεβασμένο JAR (ή την εξάρτηση Maven/Gradle) στο classpath του έργου σας.  
3. Εισάγετε τις απαιτούμενες κλάσεις στο αρχείο πηγαίου κώδικα Java:

```java
import com.aspose.words.*;
import java.awt.Color;
import java.nio.file.*;
```

Τώρα που η βιβλιοθήκη είναι ρυθμισμένη, ας βουτήξουμε στον πραγματικό κώδικα υδατογραφήματος.

## Πώς να προσθέσετε κειμενικό υδατογράφημα

Τα κειμενικά υδατογραφήματα είναι ιδανικά για την επισήμανση ενός εγγράφου ως “CONFIDENTIAL” ή “DRAFT”. Το παρακάτω απόσπασμα δείχνει έναν καθαρό τρόπο για **να δημιουργήσετε έγγραφο με υδατογράφημα** χρησιμοποιώντας το `TextWatermarkOptions`.

```java
// Create a Document instance
Document doc = new Document("Document.docx");

// Define TextWatermarkOptions
TextWatermarkOptions options = new TextWatermarkOptions();
options.setFontFamily("Arial");
options.setFontSize(36f);
options.setColor(Color.BLACK);
options.setLayout(WatermarkLayout.HORIZONTAL);
options.setSemitransparent(false);

// Set the watermark text and options
doc.getWatermark().setText("Test", options);

// Save the document with the watermark
doc.save("DocumentWithWatermark.docx");
```

### Προσαρμογή του κειμενικού υδατογραφήματος
- **Οικογένεια γραμματοσειράς & μέγεθος** – αλλάξτε το `setFontFamily` και το `setFontSize`.  
- **Χρώμα** – χρησιμοποιήστε οποιοδήποτε `java.awt.Color`.  
- **Διάταξη** – επιλέξτε `HORIZONTAL`, `DIAGONAL`, κλπ.  
- **Διαφάνεια** – ενεργοποιήστε το `setSemitransparent(true)` για πιο ελαφριά εμφάνιση.

## Πώς να προσθέσετε υδατογράφημα εικόνας (add image watermark java)

Τα υδατογραφήματα εικόνας είναι ιδανικά για λογότυπα ή προσαρμοσμένα γραφικά. Παρακάτω είναι το παράδειγμα **add image watermark java** που εισάγει ένα PNG στο κέντρο κάθε σελίδας.

```java
// Create a Document instance
Document doc = new Document("Document.docx");

// Load the image for the watermark
byte[] imageBytes = Files.readAllBytes(Paths.get("watermark.png"));
Shape watermark = new Shape(doc, ShapeType.IMAGE);
watermark.getImageData().setImage(imageBytes);

// Set the watermark size and position
watermark.setWidth(200.0);
watermark.setHeight(100.0);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.CENTER);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.CENTER);

// Add the watermark to the document
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// Save the document with the watermark
doc.save("DocumentWithImageWatermark.docx");
```

### Συμβουλές για υδατογραφήματα εικόνας
- **Αλλαγή μεγέθους** χρησιμοποιώντας `setWidth` / `setHeight` ώστε να ταιριάζει στη σελίδα.  
- **Θέση** μπορεί να κεντραριστεί ή να ευθυγραμμιστεί με οποιοδήποτε περιθώριο χρησιμοποιώντας `RelativeHorizontalPosition` / `RelativeVerticalPosition`.  
- **Διαφάνεια** μπορεί να εφαρμοστεί ρυθμίζοντας το κανάλι άλφα της εικόνας πριν τη φόρτωση.

## Πώς να αφαιρέσετε υδατογραφήματα

Όταν ένα έγγραφο δεν χρειάζεται πλέον υδατογράφημα, μπορείτε να το διαγράψετε προγραμματιστικά. Ο παρακάτω κώδικας διασχίζει όλα τα σχήματα και αφαιρεί όσα περιέχουν τη λέξη “Watermark” στο όνομά τους.

```java
// Create a Document instance
Document doc = new Document("DocumentWithWatermark.docx");

// Remove the watermark
for (Shape shape : doc.getShapes())
{
    if (shape.getName().contains("Watermark"))
    {
        shape.remove();
    }
}

// Save the document without the watermark
doc.save("DocumentWithoutWatermark.docx");
```

## Συνηθισμένα προβλήματα και αντιμετώπιση
- **Απουσία υδατογραφήματος μετά την αποθήκευση** – βεβαιωθείτε ότι καλείτε το `doc.save()` μετά τον ορισμό του υδατογραφήματος.  
- **Η εικόνα δεν εμφανίζεται** – ελέγξτε ότι η διαδρομή της εικόνας είναι σωστή και ότι το αρχείο είναι σε υποστηριζόμενη μορφή (PNG, JPEG, BMP).  
- **Η διαφάνεια δεν εφαρμόζεται** – το `setSemitransparent(true)` λειτουργεί μόνο για κειμενικά υδατογραφήματα· για εικόνες, επεξεργαστείτε το κανάλι άλφα του PNG.  
- **Πολλαπλές ενότητες** – εάν το έγγραφό σας έχει πολλές ενότητες, προσθέστε το υδατογράφημα στο σώμα κάθε ενότητας ή χρησιμοποιήστε το `doc.getWatermark().setText(...)` που εφαρμόζει παγκοσμίως.

## Συχνές Ερωτήσεις

**Q: Πώς μπορώ να αλλάξω τη γραμματοσειρά ενός κειμενικού υδατογραφήματος;**  
A: Τροποποιήστε την ιδιότητα `setFontFamily` στο `TextWatermarkOptions`, π.χ., `options.setFontFamily("Times New Roman");`.

**Q: Μπορώ να προσθέσω πολλαπλά υδατογραφήματα σε ένα έγγραφο;**  
A: Ναι. Δημιουργήστε πολλαπλά αντικείμενα `Shape` (για εικόνες) ή καλέστε το `doc.getWatermark().setText(...)` με διαφορετικές επιλογές για κάθε υδατογράφημα.

**Q: Είναι δυνατόν να περιστρέψετε ένα υδατογράφημα;**  
A: Για υδατογραφήματα εικόνας, ορίστε την περιστροφή στο αντικείμενο `Shape` με `watermark.setRotation(angle)`. Για κειμενικά υδατογραφήματα, χρησιμοποιήστε την ιδιότητα `setLayout` (π.χ., `WatermarkLayout.DIAGONAL`).

**Q: Πώς μπορώ να κάνω ένα υδατογράφημα ημιδιαφανές;**  
A: Ορίστε `options.setSemitransparent(true)` στο `TextWatermarkOptions`. Για εικόνες, ρυθμίστε την αδιαφάνεια της εικόνας πριν τη φόρτωση.

**Q: Μπορώ να προσθέσω υδατογραφήματα σε συγκεκριμένες ενότητες ενός εγγράφου;**  
A: Ναι. Διασχίστε το `doc.getSections()` και προσθέστε το υδατογράφημα μόνο στις επιθυμητές ενότητες.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Τελευταία ενημέρωση:** 2026-02-19  
**Δοκιμάστηκε με:** Aspose.Words for Java 24.12 (latest)  
**Συγγραφέας:** Aspose