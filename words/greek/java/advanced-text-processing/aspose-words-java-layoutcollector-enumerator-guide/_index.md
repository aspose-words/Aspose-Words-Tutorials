---
date: '2026-01-14'
description: Μάθετε πώς να επανεκκινήσετε την αρίθμηση σελίδων με το Aspose.Words
  Java και να χρησιμοποιήσετε το LayoutCollector για την εξαγωγή δεδομένων σελιδοποίησης,
  την ενημέρωση της διάταξης της σελίδας και την απόδοση των σελίδων ως εικόνες.
keywords:
- Aspose.Words Java LayoutCollector
- Java document layout management
- LayoutEnumerator traversal
title: Επανεκκίνηση αρίθμησης σελίδων με το Aspose.Words Java – LayoutCollector &
  LayoutEnumerator
url: /el/java/advanced-text-processing/aspose-words-java-layoutcollector-enumerator-guide/
weight: 1
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Επανεκκίνηση αρίθμησης σελίδων με Aspose.Words Java – LayoutCollector & LayoutEnumerator

## Εισαγωγή

Αντιμετωπίζετε δυσκολίες με την **επανεκκίνηση αρίθμησης σελίδων** σε μεγάλα έγγραφα Java, ενώ χρειάζεστε επίσης ανάλυση της σελιδοποίησης ή απόδοση σελίδων ως εικόνες; Με το **Aspose.Words for Java**, μπορείτε να αξιοποιήσετε το `LayoutCollector` και το `LayoutEnumerator` για να μην μόνο επανεκκινήσετε την αρίθμηση σελίδων αλλά και να **εξάγετε δεδομένα σελιδοποίησης**, **ενημερώσετε τη διάταξη σελίδας**, και **αποδώσετε σελίδες ως εικόνες** για προεπισκοπήσεις ή PDF. Αυτός ο οδηγός σας καθοδηγεί βήμα προς βήμα, από τη ρύθμιση της βιβλιοθήκης μέχρι την υλοποίηση callbacks που σας δίνουν πλήρη έλεγχο στην απόδοση του εγγράφου.

**Τι θα μάθετε**
- Πώς να χρησιμοποιήσετε το `LayoutCollector` για την εξαγωγή δεδομένων σελιδοποίησης και τον καθορισμό των εύρους σελίδων.
- Περιήγηση στη διάταξη του εγγράφου με το `LayoutEnumerator`.
- Υλοποίηση callbacks διάταξης σελίδας για **απόδοση σελίδων ως εικόνες**.
- **Επανεκκίνηση αρίθμησης σελίδων** σε συνεχόμενες ενότητες χρησιμοποιώντας επιλογές διάταξης.
- Συμβουλές για **αποτελεσματική ενημέρωση της διάταξης σελίδας**.

## Γρήγορες Απαντήσεις
- **Πώς επανεκκινώ την αρίθμηση σελίδων σε ένα έγγραφο Java;** Χρησιμοποιήστε `doc.getLayoutOptions().setContinuousSectionPageNumberingRestart(...)` και καλέστε `doc.updatePageLayout()`.
- **Ποια κλάση εξάγει δεδομένα σελιδοποίησης;** Το `LayoutCollector` παρέχει δείκτες αρχικής/τελικής σελίδας για οποιονδήποτε κόμβο.
- **Μπορώ να αποδώσω κάθε σελίδα ως εικόνα;** Ναι—υλοποιήστε το `IPageLayoutCallback` και χρησιμοποιήστε το `ImageSaveOptions`.
- **Πρέπει να καλέσω χειροκίνητα την ενημέρωση διάταξης σελίδας;** Μετά την αλλαγή των επιλογών διάταξης, πάντα καλέστε `doc.updatePageLayout()`.
- **Ποια έκδοση του Aspose.Words απαιτείται;** Τα παραδείγματα λειτουργούν με Aspose.Words for Java 25.3 (ή νεότερη).

## Τι είναι η επανεκκίνηση αρίθμησης σελίδων;

Η επανεκκίνηση αρίθμησης σελίδων σας επιτρέπει να ξεκινήσετε μια νέα ακολουθία αρίθμησης σε συγκεκριμένη ενότητα του εγγράφου, κάτι που είναι απαραίτητο για εκθέσεις, βιβλία ή συμβάσεις που απαιτούν ξεχωριστή αρίθμηση για κεφάλαια ή παραρτήματα. Το Aspose.Words παρέχει μια επιλογή διάταξης που σας επιτρέπει να ελέγχετε αυτή τη συμπεριφορά χωρίς χειροκίνητες τεχνικές διακοπής σελίδας.

## Γιατί να χρησιμοποιήσετε το LayoutCollector και το LayoutEnumerator;

- **LayoutCollector** σας δίνει προγραμματιστική πρόσβαση σε λεπτομέρειες σελιδοποίησης, επιτρέποντας την **εξαγωγή δεδομένων σελιδοποίησης** όπως η πρώτη και η τελευταία σελίδα οποιουδήποτε κόμβου.
- **LayoutEnumerator** σας επιτρέπει να περιηγηθείτε στο δέντρο οπτικής διάταξης, καθιστώντας εύκολο τον εντοπισμό σελίδων, παραγράφων ή γραμμών για προσαρμοσμένη απόδοση ή ανάλυση.
- Μαζί απλοποιούν πολύπλοκες εργασίες διάταξης που διαφορετικά θα απαιτούσαν δαπανηρές μετατροπές PDF ή χειροκίνητους υπολογισμούς.

## Προαπαιτούμενα

### Απαιτούμενες βιβλιοθήκες και εκδόσεις
Βεβαιωθείτε ότι έχετε εγκατεστημένο το Aspose.Words for Java έκδοση 25.3 (ή νεότερη).

**Maven:**
```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>25.3</version>
</dependency>
```

**Gradle:**
```gradle
implementation 'com.aspose:aspose-words:25.3'
```

### Απαιτήσεις ρύθμισης περιβάλλοντος
- Java Development Kit (JDK) εγκατεστημένο.
- IntelliJ IDEA, Eclipse ή οποιοδήποτε Java IDE της επιλογής σας.
- Έγκυρη άδεια Aspose.Words (η δωρεάν δοκιμή λειτουργεί για αξιολόγηση).

### Προαπαιτούμενες γνώσεις
Βασικές γνώσεις προγραμματισμού Java είναι επαρκείς.

## Ρύθμιση Aspose.Words
Πρώτα, ενσωματώστε τη βιβλιοθήκη Aspose.Words στο έργο σας. Μπορείτε να αποκτήσετε δωρεάν άδεια δοκιμής [εδώ](https://releases.aspose.com/words/java/) ή να χρησιμοποιήσετε προσωρινή άδεια για δοκιμές.

```java
import com.aspose.words.*;

public class SetupAsposeWords {
    public static void main(String[] args) throws Exception {
        // Set up the license (if available)
        License license = new License();
        license.setLicense("path/to/your/license.lic");

        System.out.println("Aspose.Words is ready to use!");
    }
}
```

Με τη βιβλιοθήκη έτοιμη, μπορούμε να προχωρήσουμε στις βασικές λειτουργίες.

## Οδηγός Υλοποίησης

### Δυνατότητα 1: Χρήση LayoutCollector για ανάλυση εύρους σελίδων
Η δυνατότητα `LayoutCollector` σας επιτρέπει να καθορίσετε πώς οι κόμβοι εκτείνονται σε σελίδες, κάτι που αποτελεί τη βάση για **εξαγωγή δεδομένων σελιδοποίησης**.

#### Επισκόπηση
Αξιοποιώντας το `LayoutCollector`, μπορείτε να ανακτήσετε τους δείκτες αρχικής και τελικής σελίδας οποιουδήποτε κόμβου και να υπολογίσετε το σύνολο των σελίδων που καταλαμβάνει.

#### Βήματα Υλοποίησης

**1. Αρχικοποίηση Document και LayoutCollector**
```java
Document doc = new Document();
LayoutCollector layoutCollector = new LayoutCollector(doc);
```

**2. Συμπλήρωση του εγγράφου**
Εδώ, θα προσθέσουμε περιεχόμενο που εκτείνεται σε πολλές σελίδες:
```java
DocumentBuilder builder = new DocumentBuilder(doc);
builder.write("Section 1");
builder.insertBreak(BreakType.PAGE_BREAK);
builder.insertBreak(BreakType.SECTION_BREAK_EVEN_PAGE);
builder.write("Section 2");
builder.insertBreak(BreakType.PAGE_BREAK);
```

**3. Ενημέρωση διάταξης και ανάκτηση μετρικών**
```java
layoutCollector.clear();
doc.updatePageLayout();

assert layoutCollector.getNumPagesSpanned(doc) == 5;
```

#### Εξήγηση
- **`DocumentBuilder`** εισάγει κείμενο και διακοπές σελίδας/ενότητας.
- **`updatePageLayout()`** επαναϋπολογίζει τις πληροφορίες διάταξης ώστε τα δεδομένα σελιδοποίησης να είναι ακριβή.

### Δυνατότητα 2: Περιήγηση με LayoutEnumerator
Το `LayoutEnumerator` επιτρέπει αποδοτική πλοήγηση μέσα στο δέντρο οπτικής διάταξης.

#### Επισκόπηση
Μπορείτε να περιηγηθείτε σε σελίδες, παραγράφους, γραμμές και άλλα στοιχεία διάταξης, κάτι που είναι χρήσιμο για προσαρμοσμένη απόδοση ή διαγνωστικούς σκοπούς.

#### Βήματα Υλοποίησης

**1. Αρχικοποίηση Document και LayoutEnumerator**
```java
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Layout entities.docx");
LayoutEnumerator layoutEnumerator = new LayoutEnumerator(doc);
```

**2. Περιήγηση προς τα εμπρός και προς τα πίσω**
```java
layoutEnumerator.moveParent(LayoutEntityType.PAGE);

// Traverse forward
traverseLayoutForward(layoutEnumerator, 1);

// Traverse backward
traverseLayoutBackward(layoutEnumerator, 1);
```

#### Εξήγηση
- **`moveParent()`** μετακινεί τον enumerator στο γονικό στοιχείο (σε αυτήν την περίπτωση, στο επίπεδο σελίδας).
- Οι αναδρομικές μέθοδοι περιήγησης σας επιτρέπουν να εξερευνήσετε ολόκληρη την ιεραρχία διάταξης.

### Δυνατότητα 3: Callbacks Διάταξης Σελίδας
Υλοποιήστε callbacks για την παρακολούθηση γεγονότων διάταξης και **απόδοση σελίδων ως εικόνες** όταν χρειάζεται.

#### Επισκόπηση
Η διεπαφή `IPageLayoutCallback` σας ενημερώνει όταν ένα τμήμα του εγγράφου ολοκληρώνει την επαναρροή ή όταν η μετατροπή ολοκληρώνεται.

#### Βήματα Υλοποίησης

**1. Ορισμός Callback**
```java
doc.getLayoutOptions().setCallback(new RenderPageLayoutCallback());
doc.updatePageLayout();
```

**2. Υλοποίηση μεθόδων Callback**
```java
private static class RenderPageLayoutCallback implements IPageLayoutCallback {
    public void notify(PageLayoutCallbackArgs a) throws Exception {
        if (a.getEvent() == PageLayoutEvent.PART_REFLOW_FINISHED) {
            notifyPartFinished(a);
        } else if (a.getEvent() == PageLayoutEvent.CONVERSION_FINISHED) {
            notifyConversionFinished(a);
        }
    }

    private void renderPage(PageLayoutCallbackArgs a, int pageIndex) throws Exception {
        ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.PNG);
        saveOptions.setPageSet(new PageSet(pageIndex));

        try (FileOutputStream stream = new FileOutputStream("YOUR_ARTIFACTS_DIR/PageLayoutCallback.page-" + (pageIndex + 1) + ".png")) {
            a.getDocument().save(stream, saveOptions);
        }
    }
}
```

#### Εξήγηση
- **`notify()`** αντιδρά σε γεγονότα διάταξης.
- **`ImageSaveOptions`** σε συνδυασμό με `PageSet` σας επιτρέπει να **αποδώσετε σελίδες ως εικόνες** (PNG σε αυτό το παράδειγμα).

### Δυνατότητα 4: Επανεκκίνηση αρίθμησης σελίδων σε συνεχόμενες ενότητες
Έλεγχος της αρίθμησης σελίδων όταν έχετε πολλαπλές ενότητες που ρέουν συνεχόμενα.

#### Επισκόπηση
Ορίζοντας την επιλογή `ContinuousSectionRestart`, μπορείτε να αποφασίσετε αν οι αριθμοί σελίδων θα επανεκκινούν σε νέα σελίδα ή θα συνεχίζονται αδιάσπαστα.

#### Βήματα Υλοποίησης

**1. Φόρτωση εγγράφου**
```java
Document doc = new Document("YOUR_DOCUMENT_DIRECTORY/Continuous section page numbering.docx");
```

**2. Διαμόρφωση επιλογών αρίθμησης σελίδων**
```java
doc.getLayoutOptions().setContinuousSectionPageNumberingRestart(ContinuousSectionRestart.FROM_NEW_PAGE_ONLY);
doc.updatePageLayout();
```

#### Εξήγηση
- **`setContinuousSectionPageNumberingRestart()`** καθορίζει στο Aspose.Words πώς θα διαχειριστεί την αρίθμηση σε συνεχόμενες ενότητες.
- Μετά την αλλαγή της επιλογής, **ενημερώστε τη διάταξη σελίδας** για να εφαρμοστούν οι αλλαγές.

## Πρακτικές Εφαρμογές
1. **Ανάλυση Σελιδοποίησης Εγγράφου** – Χρησιμοποιήστε το `LayoutCollector` για να ελέγξετε πώς το περιεχόμενο διανέμεται σε σελίδες και προσαρμόστε περιθώρια ή διακοπές ανάλογα.
2. **Απόδοση PDF** – Συνδυάστε το `LayoutEnumerator` με το callback για να δημιουργήσετε εικόνες υψηλής πιστότητας πριν από τη μετατροπή σε PDF.
3. **Δυναμικές Ενημερώσεις Εγγράφου** – Αντιδράστε σε γεγονότα διάταξης (π.χ., μετά από επέκταση πίνακα) και αυτόματα επανααποδώστε τις επηρεαζόμενες σελίδες.
4. **Πολλαπλές Ενότητες Αναφορών** – Εφαρμόστε **επανεκκίνηση αρίθμησης σελίδων** ώστε κάθε κεφάλαιο να έχει τη δική του αρίθμηση, διατηρώντας ταυτόχρονα τη συνεχή ροή.

## Παράγοντες Απόδοσης
- Αφαιρέστε αχρησιμοποίητες ενότητες ή κρυφό περιεχόμενο πριν καλέσετε `updatePageLayout()` για να διατηρήσετε την επεξεργασία γρήγορη.
- Χρησιμοποιήστε streaming APIs για μεγάλα έγγραφα ώστε να αποφύγετε τη φόρτωση ολόκληρου του αρχείου στη μνήμη.
- Περιορίστε το βάθος της αναδρομικής περιήγησης στο `LayoutEnumerator` αν χρειάζεστε μόνο πληροφορίες επιπέδου σελίδας.

## Κοινά Προβλήματα και Λύσεις
| Πρόβλημα | Αιτία | Διόρθωση |
|----------|-------|----------|
| `layoutCollector.getNumPagesSpanned()` returns 0 | Η διάταξη δεν έχει ενημερωθεί | Καλέστε `doc.updatePageLayout()` πριν από την ερώτηση |
| Images not generated in callback | Λείπει η διαμόρφωση `ImageSaveOptions` | Βεβαιωθείτε ότι έχει οριστεί `saveOptions.setPageSet(new PageSet(pageIndex))` |
| Page numbers don’t restart | Λανθασμένη τιμή `ContinuousSectionRestart` | Χρησιμοποιήστε `ContinuousSectionRestart.FROM_NEW_PAGE_ONLY` για πραγματική επανεκκίνηση |

## Συχνές Ερωτήσεις

**Q: Μπορώ να εξάγω τον ακριβή αριθμό σελίδας ενός συγκεκριμένου παραγράφου;**  
A: Ναι—χρησιμοποιήστε το `LayoutCollector` για να λάβετε τη σελίδα έναρξης του κόμβου παραγράφου και, στη συνέχεια, καλέστε `doc.updatePageLayout()` ώστε να διασφαλίσετε ότι τα δεδομένα είναι ενημερωμένα.

**Q: Η `update page layout` επηρεάζει το περιεχόμενο του εγγράφου;**  
A: Όχι. Επαναϋπολογίζει μόνο τις πληροφορίες διάταξης· το κείμενο και η μορφοποίηση παραμένουν αμετάβλητα.

**Q: Πώς αποδίδω όλες τις σελίδες ενός μεγάλου εγγράφου ως εικόνες αποδοτικά;**  
A: Υλοποιήστε το `IPageLayoutCallback` και επεξεργαστείτε κάθε σελίδα διαδοχικά, προαιρετικά χρησιμοποιώντας πολυνηματική επεξεργασία για αποθήκευση I/O‑bound.

**Q: Είναι δυνατόν να επανεκκινήσω την αρίθμηση μόνο για ορισμένες ενότητες;**  
A: Ναι—εφαρμόστε `setContinuousSectionPageNumberingRestart` στις επιλογές διάταξης της συγκεκριμένης ενότητας πριν καλέσετε `updatePageLayout()`.

**Q: Ποια έκδοση του Aspose.Words εισήγαγε το `LayoutCollector`;**  
A: Το `LayoutCollector` είναι διαθέσιμο από τις αρχές του 2020· τα παραδείγματα χρησιμοποιούν την έκδοση 25.3.

## Συμπέρασμα
Με την κατανόηση της **επανεκκίνησης αρίθμησης σελίδων**, του `LayoutCollector` και του `LayoutEnumerator`, έχετε πλέον ένα ισχυρό σύνολο εργαλείων για προχωρημένη επεξεργασία κειμένου στο Aspose.Words for Java. Είτε χρειάζεστε **εξαγωγή δεδομένων σελιδοποίησης**, **απόδοση σελίδων ως εικόνες**, είτε απλώς έλεγχο της αρίθμησης σελίδων μεταξύ ενοτήτων, αυτά τα API σας παρέχουν ακριβή, προγραμματιστικό έλεγχο διατηρώντας υψηλή απόδοση.

---

**Τελευταία ενημέρωση:** 2026-01-14  
**Δοκιμή με:** Aspose.Words for Java 25.3  
**Συγγραφέας:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}