---
date: '2026-02-03'
description: Μάθετε πώς να ορίζετε το φάκελο πόρων και να αποθηκεύετε έγγραφα σε σταθερού
  τύπου XAML χρησιμοποιώντας το Aspose.Words for Java, με διαχείριση πόρων και συμβουλές
  απόδοσης.
keywords:
- Aspose.Words Java XAML saving
- fixed-form XAML document saving
- Java document conversion
title: Ορισμός φακέλου πόρων για Fixed-Form XAML με Aspose.Words Java
url: /el/java/document-operations/aspose-words-java-fixed-form-xaml-saving/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Κατάκτησηκευση εγγράφων Fixed‑Form XAML

## Εισαγωγή

Αν δυσκολεύεστε να **set resources folder** κατά την αποθήκευση εγγράφων σε μορφή fixed‑form XAML χρησιμοποιώντας Java, δεν είστε μόνοι. Πολλοί προγραμματιστές αντιμετωπίζουν εμπόδια όταν διαχειρίζονται σύνθετα σενάρια αποθήκευσης εγγράφων, ειδικά όταν εμπλέκτοσειρές. Αυτό το διαμόρφωση και χρήση της κλάσης `XamlFixedSaveOptions` από το Aspose.Words for Java, ώστε να με και αποδοτικότητα.

**Τι θα μάθετε**
- Πώς να διαμορφώσετε το `XamlFixedSaveOptions` για **set resources folder** κατά την αποθήκευση σε fixed‑form XAML.  
θήκετικές συνδεδεμένων πόρων κατά τη μετατροπή εγγράφων.  
- Πραγματικές περιπτώσεις χρήσης απόδοσης.

## Γρήγορες Απαντήσεις
- **Ποια κλάση;Χρειάζεται άδεια για παραγωγή;** Ναι, μια έγκυρη άδεια Aspose.Words αφαιρεί τα υδατογραφήματα και τους περιορισμούς.ται;** JDK 8 ή νεότερηπουμο του φακέλου;** Χρησιμοποιήστε `setResourcesFolderAlias()` για να ορίσετε μια εικονική διαδρομή.  
- **Υποστηρίζ να επαναλάβ επιλογές.

## Xaml `setResourcesFolder` καθ τα εξωτερικά περιουσιακά στοιχεία (εικόνες, γραμματοσειρές κ.λπ.) όταν ένα έγγραφο αποθηκεύεται ως fixed‑form XAML. Κατευθύνοντας αυτούς τουςιερωμένο φάκελο, διατηρείτε την έξοδο οργανωμένη και διευ να χρησιμοποιήσετε έναν αφιερωμένο φά όλα τα συνδεδεμένα περιουσιακά στοιχείαταστασία στον φάκελο του έργου.  
- **Φορητότητα** – Μπορείτε να μετακινήσετε το φάκελο μαζί με τοδοση αρχ αποδίδεται αργότερα.

## Προαπαιτούμενα

- **Aspose.Words for Java** (έκδοση  
-J IDEA ή το Eclipse.  
- Βασικές γνώσεις Java και εξοικείωση με τη διαχείριση αρχείων.

## Ρύθords

Προσθέστε τη βιβλιοθήκη στο έργο σας με Maven ή Gradle.

### Maven

```xml
<dependency>
  <groupId>com.aspose</groupId>
  <artifactId>aspose-words</artifactId>
  <version>25.3</version>
</dependency>
```

### Gradle

```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### Βήματα Απόκτησης Άδειας

1. **Δωρεάν Δοκιμή**: Ξεκινήστε με μια [free trial](https://releases.aspose.com/words/java/) για να εξερευνήσετε τις δυνατότητες.  
2. **Προσωρινή Άδεια**: Αιτηθείτε μια [temporary license](https://purchase.aspose.com/temporary-license/) εάν χρειάζεστε βραχυπρόθεσμη αξιολόγηση χωρίς υδατογραφήματα.  
3. **Αγορά**: Όταν είστε έτοιμοι, αγοράστε πλήρη άδεια από την [Aspose website](https://purchase.aspose.com/buy).

### Βασική Αρχικοποίηση

```java
import com.aspose.words.Document;

public class Main {
    public static void main(String[] args) throws Exception {
        Document doc = new Document("path/to/your/document.docx");
        System.out.println("Document loaded successfully!");
    }
}
```

## Οδηγός Υλοποίησης

### Ρύθμιση και Χρήση του XamlFixedSaveOptions

#### Βήμα 1: Φόρτωση του Εγγράφου

```java
import com.aspose.words.Document;

Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Rendering.docx");
```

#### Βήμα 2: Ρύθμιση Callback Αποθήκευσης Πόρων

Δημιουργήστε μια παρουσία ενός προσαρμοσμένου callback που θα καταγράφει κάθε URI πόρου.

```java
ResourceUriPrinter callback = new ResourceUriPrinter();
```

#### Βήμα 3: Διαμόρφωση του `XamlFixedSaveOptions` (συμπεριλαμβανομένου του **set resources folder**)

```java
import com.aspose.words.XamlFixedSaveOptions;

XamlFixedSaveOptions options = new XamlFixedSaveOptions();

assert SaveFormat.XAML_FIXED == options.getSaveFormat();
options.setResourcesFolder("YOUR_OUTPUT_DIRECTORY/XamlFixedResourceFolder");   // <-- set resources folder
options.setResourcesFolderAlias("YOUR_OUTPUT_DIRECTORY/XamlFixedFolderAlias");
options.setResourceSavingCallback(callback);

new File(options.getResourcesFolderAlias()).mkdir();
```

#### Βήμα 4: Αποθήκευση του Εγγράφου

```java
doc.save("YOUR_OUTPUT_DIRECTORY/XamlFixedSaveOptions.ResourceFolder.xaml", options);
```

### Υλοποίηση του ResourceUriPrinter

#### Επισκόπηση

`ResourceUriPrinter` υλοποιεί το `IResourceSavingCallback` για να καταγράφει κάθε πόρο που το Aspose.Words γράφει στο δίσκο.

#### Βήμα 1: Υλοποίηση του Callback

```java
import com.aspose.words.*;

private static class ResourceUriPrinter implements IResourceSavingCallback {
    public ResourceUriPrinter() {
        mResources = new ArrayList<>();
    }

    @Override
    public void resourceSaving(ResourceSavingArgs args) throws Exception {
        getResources().add(MessageFormat.format("Resource \"{0}\"\n\t{1}",
            args.getResourceFileName(), args.getResourceFileUri()));
        args.setResourceStream(new FileOutputStream(args.getResourceFileUri()));
        args.setKeepResourceStreamOpen(false);
    }

    public ArrayList<String> getResources() {
        return mResources;
    }

    private final ArrayList<String> mResources;
}
```

#### Βήμα 2: Προσομοίωση Αποθήκευσης Πόρων (για δοκιμή)

```java
ResourceUriPrinter printer = new ResourceUriPrinter();
ResourceSavingArgs exampleArgs = new ResourceSavingArgs() {
    public String getResourceFileName() { return "example.png"; }
    public String getResourceFileUri() { return "YOUR_OUTPUT_DIRECTORY/XamlFixedFolderAlias/example.png"; }

    @Override
    public void setResourceStream(java.io.OutputStream resourceStream) {}
};

try {
    printer.resourceSaving(exampleArgs);
    for (String resource : printer.getResources()) {
        System.out.println(resource);
    }
} catch (Exception e) {
    e.printStackTrace();
}
```

## Πρακτικές Εφαρμογές

1. **Συστήματα Διαχείρισης Εγγράφων** – Διατηρήστε όλα τα περιουσιακά στοιχεία μαζί για αξιόπιστη απόδοση σε browsers.  
2. **Διασυστημική Δημοσίευση** – Χρησιμοποι τους πόρους του για προβολείς σε Windows, macOS ή Linux.  
3. **Εργαλεία Επιχειρησιακής Αναφοράς** – Εν αποθηκεύονται εικόνες και γραμματοσειρές.

## Σκέψεις για την Απόδοση

- **Διαχείρισηκά στοιχεία σε αφιερωμένο φάκελο για να αποφύγετε επαναλαμβανόμενες I/O λειτουργίες.  
- **Διαχείριση Ροών** – Κλείστε τις ροές άμεσα (`setKeepResourceStreamOpen(false)`).  
- **Επεξεργασία σε Batch** – Επανάληψη σε μια συλλογή εγγράφων, επαναχρησιμοποιώντας το ίδιο αντικείμενο `XamlFixedSaveOptions` για μείωση του κόστους.

## Συχνά Προβλήματα και Λύσεις

| Πρόβλημα | Λύση |
|----------|------|
| Οι πόροι δεν βρίσκονται μετά την αποθήκευση | Επαληθεύστε ότι το `setResourcesFolder` δείχνει σε έναν υπάρχοντα, εγγράψιμο φάκελο και ότι το `setResourcesFolderAlias` ταιριάζει με τη εικονική διαδρομή που χρησιμοποιείται στο XAML. |
| Διαρροή μνήμης σε μεγάλα έγγραφα | Βεβαιωθείτε ότι έχετε ορίσει `setKeepResourceStreamOpen(false)` και απελευθερώστε το αντικείμενο `Document` μετά την αποθήκευση. |
| Λάθος μορφή εικόνας | Χρησιμοποιήστε τις κατάλληλες ρυθμίσεις εξαγωγής εικόναςτροπήές Ερωτήσεις

**Ε: Για τι χρησιμοποιείται το `XamlFixedSaveOptions`;**  
Α: Επιτρέπει την αποθήκευση ενός εγγράφου ως fixed‑form XAML παρέχοντας έλεγχο των συνδεδεμένων πόρων μέσω των ιδιοτήτων **set resources folder**.

**Ε: Πώςαιρέσεις κατά την αποθήκευση;**  
Α: Τυλίξτε την κλήση αποθήκευσης σε block ``. Μπορείτε επίσης να εξετάσετε το `ResourceSavingArgs` για επιπλέον πληροφορίες.

**Ε: Μπορώ να χρησιμοποιήσω το Aspose.Words for Java χωρίς άδεια;**  
Α: Ναι, αλλά η έξοδος θα περιέχει υδατογραφήματα αξιολόγησης. Εφαρμόστε μια [temporary license](https://purchase.aspose.com/temporary-license/) για απεριόριστη δοκιμή.

**Ε: Είναι δυνατόν να αλλάξω το φάκελο εξόδου κατά το χρόνο εκτέλεσης;**  
Α: Σίγουρα – απλώςλήσηείία έγγραφα;**  
Α: Φορτώστε το κρυπτογραφημένο έγγραφο με τον κατάλληλο κωδικό πρόσβασης χρησιμοποιώντας `new Document(stream, loadOptions)` πριν εφαρμόσετε τις επιλογές αποθήκευσης XAML.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Τελευταία ενημέρωση:** 2026-02-03  
**Δοκιμή με:** Aspose.Words for Java 25.3  
**Συγγραφέας:** Aspose  

---