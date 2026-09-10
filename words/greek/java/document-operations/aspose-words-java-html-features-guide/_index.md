---
date: '2026-02-06'
description: Μάθετε πώς να φορτώνετε HTML VML με το Aspose.Words for Java, να κρυπτογραφήσετε
  αρχεία HTML Java, να ορίζετε τη βασική διεύθυνση URI του HTML και να διαμορφώνετε
  τις επιλογές ελέγχου HTML.
keywords:
- Aspose.Words for Java
- HTML document processing
- document encryption
title: Φόρτωση HTML VML με το Aspose.Words for Java – Πλήρης οδηγός
url: /el/java/document-operations/aspose-words-java-html-features-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Συνολικές δυνατότητες HTML με Aspose.Words for Java: Οδηγός για Προγραμματιστές

## Εισαγωγή

Η πλοήγηση στον πολύπλοκο κόσμο της επεξεργασίας εγγράφων μπορεί να είναι αποθαρρυντική, ειδικά όταν πρέπει να διαχειριστείτε διάφορες δυνατότητες HTML. Είτε ασχολείστε με υποστήριξη Vector Markup Language (VML), κρυπτογραφημένα έγγραφα ή συγκεκριμένες συμπεριφορές εισαγωγής HTML, το **Aspose.Words for Java** προσφέρει μια ισχυρή λύση. Σε αυτόν τον οδηγό, θα μάθετε **πώς να φορτώνετε html vml** αποδοτικά και με ασφάλεια, καλύπτοντας επίσης συναφείς εργασίες όπως **encrypt html java**, **set html base uri** και **configure html control**.

**Τι θα μάθετε:**
- Πώς να φορτώνετε έγγραφα HTML με υποστήριξη VML.
- Τεχνικές για διαχείριση σταθερής‑σελίδας HTML και προειδοποιήσεων.
- Μεθόδους κρυπτογράφησης και φόρτωσης HTML εγγράφων με κωδικό πρόσβασης.
- Χρήση base URIs στις επιλογές φόρτωσης HTML.
- Εισαγωγή στοιχείων εισόδου HTML ως Structured Document Tags ή πεδία φόρμας.
- Παράβλεψη στοιχείων `<noscript>` κατά τη φόρτωση HTML.
- Διαμόρφωση λειτουργιών εισαγωγής block για έλεγχο διατήρησης της δομής HTML.
- Υποστήριξη κανόνων `@font-face` για προσαρμοσμένες γραμματοσειρές.

## Γρήγορες Απαντήσεις
- **Ποιος είναι ο κύριος τρόπος ενεργοποίησης του VML κατά τη φόρτωση HTML;** Ορίστε `loadOptions.setSupportVml(true)`.
- **Μπορώ να φορτώσω HTML αρχεία με κωδικό πρόσβασης;** Ναι, περάστε τον κωδικό στο `HtmlLoadOptions`.
- **Πώς λύνω σχετικές διαδρομές εικόνων;** Χρησιμοποιήστε `loadOptions.setBaseUri("your/base/uri")`.
- **Μπορεί να εισαχθεί το `<select>` ως πεδίο φόρμας;** Ορίστε `loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag)`.
- **Ποια κλάση καταγράφει προειδοποιήσεις κατά τη φόρτωση;** Υλοποιήστε το `IWarningCallback` και αναθέστε το στο `loadOptions.setWarningCallback(...)`.

## Προαπαιτούμενα

Πριν ξεκινήσουμε την υλοποίηση διαφόρων δυνατοτήτων HTML με το Aspose.Words for Java, βεβαιωθείτε ότι το περιβάλλον σας είναι σωστά ρυθμισμένο:

- **Απαιτούμενες βιβλιοθήκες:** Χρειάζεστε τη βιβλιοθήκη Aspose.Words έκδοση 25.3 ή νεότερη.
- **Περιβάλλον ανάπτυξης:** Αυτός ο οδηγός υποθέτει ότι χρησιμοποιείτε Maven ή Gradle για τη διαχείριση εξαρτήσεων.
- **Βάση γνώσεων:** Μια βασική κατανόηση της Java και εξοικείωση με έγγραφα HTML θα είναι χρήσιμη.

## Ρύθμιση Aspose.Words

Για να αρχίσετε να εργάζεστε με το Aspose.Words, πρέπει πρώτα να το προσθέσετε στο έργο σας. Ακολουθούν τα βήματα για τη ρύθμιση της βιβλιοθήκης με Maven και Gradle:

### Maven

Προσθέστε την ακόλουθη εξάρτηση στο αρχείο `pom.xml`:

```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### Gradle

Συμπεριλάβετε αυτό στο αρχείο `build.gradle`:

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

#### Απόκτηση Άδειας

Το Aspose.Words απαιτεί άδεια για πλήρη λειτουργικότητα. Μπορείτε να αποκτήσετε δωρεάν δοκιμαστική έκδοση, να ζητήσετε προσωρινή άδεια ή να αγοράσετε μόνιμη. Επισκεφθείτε τη [σελίδα αγοράς](https://purchase.aspose.com/buy) για περισσότερες λεπτομέρειες.

Για να αρχικοποιήσετε το Aspose.Words στο έργο Java, βεβαιωθείτε ότι έχετε ρυθμίσει σωστά την άδεια:

```java
import com.aspose.words.License;

public class InitializeAspose {
    public static void main(String[] args) throws Exception {
        License license = new License();
        license.setLicense("path/to/your/license/file.lic");
        
        System.out.println("Aspose.Words is ready to use!");
    }
}
```

## Οδηγός Υλοποίησης

Θα χωρίσουμε την υλοποίηση σε ενότητες βάσει των λειτουργιών που θέλουμε να εφαρμόσουμε.

### Πώς να φορτώσετε html vml με Aspose.Words

**Επισκόπηση:**  
Η φόρτωση ενός εγγράφου HTML με υποστήριξη VML επιτρέπει ευέλικτη απόδοση διανυσματικών γραφικών όπως διαγράμματα και σχήματα. Αυτό είναι το κεντρικό βήμα για τη βασική φράση **load html vml**.

#### Βήμα‑βήμα

1. **Ρύθμιση Load Options**

```java
import com.aspose.words.Document;
import com.aspose.words.HtmlLoadOptions;

HtmlLoadOptions loadOptions = new HtmlLoadOptions();
loadOptions.setSupportVml(true); // Enable VML support
```

2. **Φόρτωση του Εγγράφου**

```java
Document doc = new Document("path/to/VML conditional.htm", loadOptions);
```

3. **Επαλήθευση Τύπου Εικόνας**

```java
import com.aspose.words.NodeType;
import com.aspose.words.Shape;

Shape imageShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
String expectedImageType = "JPG"; // Adjust based on actual logic

if (!imageShape.getImageData().getImageType().toString().equals(expectedImageType)) {
    throw new AssertionError("Unexpected image type loaded.");
}
```

### Φόρτωση Fixed HTML και Διαχείριση Προειδοποιήσεων

**Επισκόπηση:**  
Η φόρτωση εγγράφων HTML σταθερής σελίδας μπορεί να παράγει προειδοποιήσεις που πρέπει να διαχειριστούν για ακριβή επεξεργασία.

#### Βήμα‑βήμα

1. **Ορισμός Callback Προειδοποίησης**

```java
import com.aspose.words.IWarningCallback;
import com.aspose.words.WarningInfo;
import java.util.ArrayList;

private static class ListDocumentWarnings implements IWarningCallback {
    private final ArrayList<WarningInfo> mWarnings = new ArrayList<>();

    public void warning(WarningInfo info) { 
        mWarnings.add(info); 
    }

    public ArrayList<WarningInfo> warnings() { return mWarnings; }
}
```

2. **Διαμόρφωση Load Options**

```java
HtmlLoadOptions loadOptions = new HtmlLoadOptions();
ListDocumentWarnings warningCallback = new ListDocumentWarnings();
loadOptions.setWarningCallback(warningCallback);
```

3. **Φόρτωση Εγγράφου και Έλεγχος Προειδοποιήσεων**

```java
Document doc = new Document("path/to/HtmlFixed.html", loadOptions);

if (warningCallback.warnings().size() != 1) {
    throw new AssertionError("Unexpected number of warnings.");
}
```

### Κρυπτογράφηση HTML Εγγράφων

**Επισκόπηση:**  
Η κρυπτογράφηση ενός εγγράφου HTML με κωδικό πρόσβασης εξασφαλίζει ασφαλή πρόσβαση, κάτι που είναι απαραίτητο για ευαίσθητες πληροφορίες—αυτό καλύπτει το σενάριο **encrypt html java**.

#### Βήμα‑βήμα

1. **Προετοιμασία Επιλογών Ψηφιακής Υπογραφής**

```java
import com.aspose.words.CertificateHolder;
import com.aspose.words.DigitalSignatureUtil;
import com.aspose.words.SignOptions;

CertificateHolder certificateHolder = CertificateHolder.create("path/to/morzal.pfx", "aw");
SignOptions signOptions = new SignOptions();
signOptions.setComments("Comment");
signOptions.setSignTime(new Date());
signOptions.setDecryptionPassword("docPassword");
```

2. **Υπογραφή και Κρυπτογράφηση Εγγράφου**

```java
String inputFileName = "path/to/Encrypted.docx";
String outputFileName = "path/to/output/directory/HtmlLoadOptions.EncryptedHtml.html";

DigitalSignatureUtil.sign(inputFileName, outputFileName, certificateHolder, signOptions);
```

3. **Φόρτωση Κρυπτογραφημένου Εγγράφου**

```java
import com.aspose.words.Document;

HtmlLoadOptions loadOptions = new HtmlLoadOptions("docPassword");
Document doc = new Document(outputFileName, loadOptions);

if (!doc.getText().trim().equals("Test encrypted document.")) {
    throw new AssertionError("Unexpected document text.");
}
```

### Base URI για HtmlLoadOptions

**Επισκόπηση:**  
Ο καθορισμός ενός **set html base uri** βοηθά στην επίλυση σχετικών URI, ειδικά όταν πρόκειται για εικόνες ή άλλους συνδεδεμένους πόρους.

#### Βήμα‑βήμα

1. **Διαμόρφωση Load Options με Base URI**

```java
HtmlLoadOptions loadOptions = new HtmlLoadOptions(LoadFormat.HTML, "", "path/to/imageDir");
```

2. **Φόρτωση Εγγράφου και Επαλήθευση Εικόνας**

```java
import com.aspose.words.Document;
import com.aspose.words.NodeType;

Document doc = new Document("path/to/Missing image.html", loadOptions);
Shape imageShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);

if (!imageShape.isImage()) {
    throw new AssertionError("Expected an image shape.");
}
```

### Εισαγωγή HTML Select ως Structured Document Tag

**Επισκόπηση:**  
Για να **configure html control** συμπεριφορά, μπορείτε να εισάγετε στοιχεία `<select>` ως Structured Document Tags, προσφέροντας πιο ακριβή έλεγχο των πεδίων φόρμας μέσα σε έγγραφα Word.

#### Βήμα‑βήμα

1. **Ορισμός Προτιμώμενου Τύπου Ελέγχου**

```java
import com.aspose.words.HtmlLoadOptions;
import com.aspose.words.ControlType;

HtmlLoadOptions loadOptions = new HtmlLoadOptions();
loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag);
```

2. **Φόρτωση Εγγράφου και Επαλήθευση Δομής**

```java
import com.aspose.words.Document;
import com.aspose.words.NodeType;
import com.aspose.words.StructuredDocumentTag;

Document doc = new Document("path/to/Input HTML with select element.html", loadOptions);
StructuredDocumentTag sdt = (StructuredDocumentTag)doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (!sdt.getTagName().equals("Select")) {
    throw new AssertionError("Expected a Structured Document Tag with tag name 'Select'.");
}
```

## Συχνά Προβλήματα και Λύσεις

| Πρόβλημα | Αιτία | Διόρθωση |
|----------|-------|----------|
| Τα γραφικά VML δεν εμφανίζονται | Η σημαία `supportVml` παραμένει στην προεπιλογή (`false`) | Βεβαιωθείτε ότι έχετε ορίσει `loadOptions.setSupportVml(true)` πριν τη φόρτωση. |
| Οι εικόνες λείπουν μετά τη φόρτωση | Δεν μπορούν να επιλυθούν σχετικές διαδρομές | Χρησιμοποιήστε **set html base uri** (`loadOptions.setBaseUri(...)`) για να δείξετε στο σωστό φάκελο. |
| Το HTML με κωδικό πρόσβασης προκαλεί εξαίρεση | Δεν παρασχέθηκε κωδικός | Περάστε τον κωδικό στο `new HtmlLoadOptions("yourPassword")`. |
| Τα στοιχεία ελέγχου εμφανίζονται ως απλό κείμενο | Λανθασμένος `HtmlControlType` | Ορίστε `loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag)` ή `FormField` ανάλογα. |
| Απρόσμενες προειδοποιήσεις | Μη διαχειρισμένα στοιχεία HTML | Υλοποιήστε `IWarningCallback` για να καταγράψετε και να ελέγξετε τις προειδοποιήσεις. |

## Συχνές Ερωτήσεις

**Ε: Μπορώ να φορτώσω HTML αρχεία που περιέχουν τόσο VML όσο και σύγχρονα SVG γραφικά;**  
Α: Ναι. Ενεργοποιήστε το VML με `setSupportVml(true)`· το SVG διαχειρίζεται αυτόματα από το Aspose.Words.

**Ε: Πώς κρυπτογραφώ ένα HTML έγγραφο χωρίς χρήση ψηφιακού πιστοποιητικού;**  
Α: Χρησιμοποιήστε τον κατασκευαστή `HtmlLoadOptions` που δέχεται κωδικό πρόσβασης και αποθηκεύστε το έγγραφο με `Document.save(..., SaveFormat.HTML)` αφού ορίσετε τον κωδικό.

**Ε: Τι συμβαίνει αν το base URI δείχνει σε φάκελο που δεν υπάρχει;**  
Α: Το Aspose.Words θα ρίξει `FileNotFoundException` για τους χαμένα πόρους. Επαληθεύστε τη διαδρομή πριν τη φόρτωση.

**Ε: Μπορώ να αλλάξω τον προεπιλεγμένο τύπο ελέγχου για όλα τα HTML στοιχεία φόρμας;**  
Α: Ναι. Χρησιμοποιήστε `loadOptions.setHtmlControlType(HtmlControlType.StructuredDocumentTag)` για καθολική εφαρμογή.

**Ε: Είναι τα callbacks προειδοποίησης thread‑safe;**  
Α: Η υλοποίηση του callback πρέπει να είναι thread‑safe εάν σκοπεύετε να φορτώνετε έγγραφα ταυτόχρονα. Χρησιμοποιήστε συγχρονισμένες συλλογές ή thread‑local αποθήκευση.

---

**Τελευταία ενημέρωση:** 2026-02-06  
**Δοκιμασμένο με:** Aspose.Words for Java 25.3  
**Συγγραφέας:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}