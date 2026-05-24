---
category: general
date: 2026-05-23
description: Καταχωρίστε τη συνάρτηση επιστροφής προειδοποίησης σε Java για να εντοπίζετε
  ελλείπουσες γραμματοσειρές και να διαχειρίζεστε τις αντικαταστάσεις γραμματοσειρών.
  Μάθετε βήμα‑βήμα με ένα πλήρες παράδειγμα.
draft: false
keywords:
- register warning callback
- detect missing fonts
- Java font handling
- Aspose.Words warning callback
- font substitution detection
language: el
og_description: Καταχωρίστε την κλήση επιστροφής προειδοποίησης σε Java για τον εντοπισμό
  ελλιπών γραμματοσειρών. Αυτό το σεμινάριο παρουσιάζει μια πλήρη λύση με κώδικα,
  εξηγήσεις και βέλτιστες πρακτικές.
og_title: Καταχώρηση Callback Προειδοποίησης σε Java – Πλήρης Οδηγός
schemas:
- author: Aspose
  dateModified: '2026-05-23'
  description: Register warning callback in Java to detect missing fonts and handle
    font substitutions. Learn step‑by‑step with a full example.
  headline: Register Warning Callback in Java – Complete Programming Guide
  type: TechArticle
tags:
- Java
- Aspose.Words
- FontSettings
- DocumentProcessing
title: Καταχώρηση Callback Προειδοποίησης σε Java – Πλήρης Οδηγός Προγραμματισμού
url: /el/java/document-rendering/register-warning-callback-in-java-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Καταχώρηση Callback Προειδοποίησης σε Java – Πλήρης Οδηγός Προγραμματισμού

Έχετε ποτέ χρειαστεί να **καταχωρήσετε callback προειδοποίησης** σε Java αλλά δεν ήξερτε πώς να εντοπίσετε προβλήματα με ελλιπείς γραμματοσειρές; Δεν είστε μόνοι. Όταν τα έγγραφα εξαρτώνται από προσαρμοσμένες γραμματοσειρές, οι σιωπηλές αντικαταστάσεις γραμματοσειρών μπορούν να χαλάσουν τη διάταξη, και ο μόνος αξιόπιστος τρόπος για να τις εντοπίσετε είναι ακούγοντας τις προειδοποιήσεις. Σε αυτόν τον οδηγό θα περάσουμε από μια πρακτική λύση που όχι μόνο **καταχωρεί ένα callback προειδοποίησης** αλλά επίσης **ανιχνεύει ελλιπείς γραμματοσειρές** πριν αυτές σιωπηρά σπάσουν το αποτέλεσμα σας.

Το θέμα είναι—η Aspose.Words για Java σας παρέχει ένα καθαρό API για τη διαχείριση γραμματοσειρών, ωστόσο πολλοί προγραμματιστές παραλείπουν το βήμα του callback προειδοποίησης και καταλήγουν με PDF που δεν μοιάζουν καθόλου με το αρχικό αρχείο Word. Στο τέλος αυτού του tutorial θα έχετε ένα έτοιμο‑για‑εκτέλεση απόσπασμα κώδικα, θα καταλάβετε γιατί κάθε γραμμή είναι σημαντική, και θα ξέρετε πώς να επεκτείνετε την προσέγγιση για πιο σύνθετα σενάρια.

## Τι Θα Μάθετε

* Πώς να δημιουργήσετε `LoadOptions` και να ενεργοποιήσετε την προσαρμοσμένη διαχείριση γραμματοσειρών.  
* Πώς να **καταχωρήσετε callback προειδοποίησης** για να συλλάβετε συμβάντα `FONT_SUBSTITUTION`.  
* Πώς να **ανιχνεύσετε ελλιπείς γραμματοσειρές** και να καταγράψετε χρήσιμες πληροφορίες για αποσφαλμάτωση.  
* Ένα πλήρες, εκτελέσιμο παράδειγμα Java που μπορείτε να επικολλήσετε στο IDE σας σήμερα.

Δεν απαιτούνται εξωτερικές βιβλιοθήκες εκτός από την Aspose.Words, και ο κώδικας λειτουργεί με Java 8+ και Aspose.Words 23.9 (ή νεότερη έκδοση). Αν έχετε ήδη ένα έργο που φορτώνει αρχεία `.docx`, θα χρειαστεί να προσθέσετε μόνο μερικές γραμμές—χωρίς μεγάλη αναδιάρθρωση.

## Προαπαιτούμενα

* Java Development Kit (JDK) 8 ή νεότερο.  
* Aspose.Words για Java (κατεβάστε από την επίσημη ιστοσελίδα ή προσθέστε την εξάρτηση Maven).  
* Πρόσβαση στον φάκελο που περιέχει το έγγραφο Word που θέλετε να φορτώσετε.  
* Βασική εξοικείωση με τις Java lambdas ή τις ανώνυμες κλάσεις (θα χρησιμοποιήσουμε μια ανώνυμη κλάση για σαφήνεια).

Αν κάποιο από αυτά σας φαίνεται άγνωστο, μην πανικοβληθείτε—κάθε βήμα εξηγείται με απλή αγγλική, και τα σχόλια του κώδικα καλύπτουν τα κενά.

---

## Βήμα 1: Δημιουργία Load Options και Ενεργοποίηση Προσαρμοσμένης Διαχείρισης Γραμματοσειρών

Πριν μπορέσουμε να ακούσουμε προειδοποιήσεις σχετικές με γραμματοσειρές, χρειαζόμαστε μια παρουσία `LoadOptions` που λέει στην Aspose.Words να χρησιμοποιήσει το δικό μας `FontSettings`. Σκεφτείτε το `LoadOptions` ως το “τσάντα ρυθμίσεων” που δίνετε στον φορτωτή εγγράφων.

```java
// Step 1: Create load options and enable custom font handling
LoadOptions loadOptions = new LoadOptions();               // Holds loading configuration
loadOptions.setFontSettings(new FontSettings());           // Attach a fresh FontSettings object
```

**Γιατί είναι σημαντικό:**  
`FontSettings` είναι η πύλη για όλα όσα κάνει η βιβλιοθήκη με τις γραμματοσειρές—διαδρομές αναζήτησης, κανόνες αντικατάστασης, και, κρίσιμα, callbacks προειδοποίησης. Δημιουργώντας ένα αφιερωμένο αντικείμενο `FontSettings`, αποκτάτε πλήρη έλεγχο στο πώς αντιμετωπίζονται οι ελλιπείς γραμματοσειρές αντί να βασίζεστε στις προεπιλογές της βιβλιοθήκης.

> **Συμβουλή:** Αν η εφαρμογή σας παρέχει ήδη ένα κοινό `FontSettings` (π.χ., για μετατροπή σε PDF), χρησιμοποιήστε το ξανά εδώ για να διατηρήσετε τη συνεπή επίλυση γραμματοσειρών σε όλο το pipeline.

---

## Βήμα 2: Καταχώρηση Callback Προειδοποίησης για Ανίχνευση Ελλιπών Γραμματοσειρών

Τώρα έρχεται η καρδιά του tutorial: **καταχωρούμε ένα callback προειδοποίησης** στο `FontSettings` που μόλις δημιουργήσαμε. Το callback λαμβάνει ένα αντικείμενο `WarningInfo` για κάθε προειδοποίηση που εκδίδεται κατά τη φόρτωση του εγγράφου.

```java
// Step 2: Register a warning callback to be notified of font substitutions
loadOptions.getFontSettings().setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Filter only font substitution warnings
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            // This is where we **detect missing fonts**
            System.out.println("Substituted: " + info.getDescription());
        }
    }
});
```

**Εξήγηση της λογικής:**

* Το `setWarningCallback` συνδέει τον προσαρμοσμένο ακροατή μας.  
* Μέσα στο `warning(WarningInfo info)`, ελέγχουμε το `info.getWarningType()`.  
* Όταν ο τύπος ισούται με `WarningType.FONT_SUBSTITUTION`, η βιβλιοθήκη μας λέει ότι δεν μπόρεσε να βρει την αρχική γραμματοσειρά και έπρεπε να αντικαταστήσει μια άλλη.  
* Το `info.getDescription()` περιέχει ένα ανθρώπινα αναγνώσιμο μήνυμα όπως *«Font 'MyCustomFont' not found, substituted with 'Arial'.»*  

> **Γιατί να μην πιάσουμε απλώς μια εξαίρεση;**  
> Οι ελλιπείς γραμματοσειρές σπάνια προκαλούν εξαίρεση· εκδίδουν προειδοποιήσεις. Χωρίς ένα callback, αυτές οι προειδοποιήσεις εξαφανίζονται στο κενό, και δεν ξέρετε ποτέ ότι η οπτική πιστότητα του εγγράφου έχει υποβαθμιστεί.

### Προαιρετικό: Χρήση Lambda (Java 8+)

Αν προτιμάτε πιο σύντομη σύνταξη, το ίδιο callback μπορεί να εκφραστεί με μια lambda:

```java
loadOptions.getFontSettings().setWarningCallback(info -> {
    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
        System.out.println("Substituted: " + info.getDescription());
    }
});
```

Και οι δύο προσεγγίσεις επιτυγχάνουν τον ίδιο στόχο—επιλέξτε το στυλ που ταιριάζει στον κώδικά σας.

---

## Βήμα 3: Φόρτωση του Εγγράφου με τις Ρυθμισμένες Επιλογές

Με το callback στη θέση του, το τελευταίο βήμα είναι η φόρτωση του εγγράφου. Ο κατασκευαστής `Document` δέχεται τη διαδρομή και τα `LoadOptions` που προετοιμάσαμε.

```java
// Step 3: Load the document using the configured options
Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**Τι συμβαίνει στο παρασκήνιο;**  
Κατά την κλήση αυτή η Aspose.Words αναλύει το αρχείο `.docx`, επιλύει κάθε αναφερόμενη γραμματοσειρά και ενεργοποιεί το callback προειδοποίησης για οποιαδήποτε ελλιπή γραμματοσειρά. Αν όλα είναι παρόντα, δεν θα δείτε έξοδο στην κονσόλα· διαφορετικά, θα λάβετε γραμμές όπως:

```
Substituted: Font 'OpenSans-Regular' not found, substituted with 'Times New Roman'.
Substituted: Font 'CustomIconFont' not found, substituted with 'Arial'.
```

Αυτή η έξοδος είναι το σαφές αποδεικτικό ότι **καταχωρήσαμε το callback προειδοποίησης** με επιτυχία και **ανιχνεύουμε ελλιπείς γραμματοσειρές**.

---

## Πλήρες Παράδειγμα Εργασίας

Παρακάτω βρίσκεται το πλήρες, αυτόνομο πρόγραμμα Java που μπορείτε να αντιγράψετε‑επικολλήσετε σε ένα αρχείο `Main.java` και να το εκτελέσετε. Βεβαιωθείτε ότι το JAR της Aspose.Words βρίσκεται στο classpath σας.

```java
import com.aspose.words.*;

public class Main {
    public static void main(String[] args) {
        try {
            // 1️⃣ Create LoadOptions and enable custom font handling
            LoadOptions loadOptions = new LoadOptions();
            loadOptions.setFontSettings(new FontSettings());

            // 2️⃣ Register warning callback to detect missing fonts
            loadOptions.getFontSettings().setWarningCallback(new IWarningCallback() {
                @Override
                public void warning(WarningInfo info) {
                    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                        System.out.println("Substituted: " + info.getDescription());
                    }
                }
            });

            // 3️⃣ Load the document using the configured options
            Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

            // Optional: Save as PDF to verify visual fidelity
            doc.save("output.pdf");
            System.out.println("Document loaded and saved successfully.");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Αναμενόμενη έξοδος** (όταν λείπουν γραμματοσειρές):

```
Substituted: Font 'MyCustomFont' not found, substituted with 'Arial'.
Document loaded and saved successfully.
```

Αν όλες οι γραμματοσειρές είναι διαθέσιμες, θα δείτε μόνο το μήνυμα επιτυχίας.

---

## Διαχείριση Ακραίων Περιπτώσεων και Συνηθισμένων Παγίδων

| Κατάσταση | Τι να Προσέξετε | Προτεινόμενη Διόρθωση |
|-----------|-------------------|---------------|
| **Πολλαπλές ελλιπείς γραμματοσειρές** | Το callback μπορεί να ενεργοποιηθεί πολλές φορές, γεμίζοντας τα logs. | Συγκεντρώστε τα μηνύματα ή γράψτε τα σε αρχείο για μεταγενέστερη ανάλυση. |
| **Επίπτωση στην απόδοση** | Η υπερβολική καταγραφή μπορεί να επιβραδύνει τη φόρτωση μεγάλων παρτίδων. | Φιλτράρετε τις προειδοποιήσεις ανά σοβαρότητα ή απενεργοποιήστε την έξοδο στην κονσόλα στην παραγωγή. |
| **Προσαρμοσμένοι φάκελοι γραμματοσειρών** | `FontSettings` προεπιλεγμένα χρησιμοποιεί μόνο τις συστημικές γραμματοσειρές. | Καλέστε `fontSettings.setFontsFolder("path/to/custom/fonts", true);` πριν καταχωρήσετε το callback. |
| **Σιωπηλή αντικατάσταση** | Ορισμένες γραμματοσειρές μπορεί να αντικατασταθούν χωρίς προειδοποίηση αν θεωρούνται παρόμοιες. | Ορίστε `fontSettings.setSubstitutionSettings(new FontSubstitutionSettings());` και ρυθμίστε λεπτομερώς τους κανόνες αντικατάστασης. |

---

## Επέκταση της Λύσης

Τώρα που ξέρετε πώς να **καταχωρήσετε callback προειδοποίησης** και **ανιχνεύσετε ελλιπείς γραμματοσειρές**, ίσως θέλετε να:

* **Διακόψετε τη φόρτωση** όταν λείπει μια κρίσιμη γραμματοσειρά (ρίξτε εξαίρεση μέσα στο callback).  
* **Συλλέξτε τα ονόματα των ελλιπών γραμματοσειρών** σε ένα `Set<String>` για μια σύνοψη αναφοράς μετά τη φόρτωση του εγγράφου.  
* **Ενσωματώστε με σύστημα παρακολούθησης** (π.χ., στείλτε ειδοποιήσεις στο Slack ή στο Azure Monitor).  

Όλες αυτές οι επεκτάσεις βασίζονται στο ίδιο μοτίβο callback που παρουσιάσαμε.

---

## Συμπέρασμα

Διασχίσαμε ένα πλήρες, έτοιμο για παραγωγή παράδειγμα που δείχνει πώς να **καταχωρήσετε callback προειδοποίησης** σε Java, επιτρέποντάς σας να **ανιχνεύσετε ελλιπείς γραμματοσειρές** τη στιγμή που φορτώνεται ένα έγγραφο. Τα βασικά σημεία είναι:

* Δημιουργήστε ένα `LoadOptions` με προσαρμοσμένο `FontSettings`.  
* Συνδέστε ένα `IWarningCallback` που φιλτράρει τις προειδοποιήσεις `FONT_SUBstitution`.  
* Φορτώστε το έγγραφο χρησιμοποιώντας αυτές τις επιλογές και αντιδράστε σε οποιαδήποτε συμβάντα ελλιπών γραμματοσειρών.

Με αυτή τη γνώση μπορείτε να προστατεύσετε τις γραμμές επεξεργασίας εγγράφων, να εξασφαλίσετε οπτική πιστότητα και να παρέχετε σαφή διαγνωστικά στους τελικούς χρήστες.  

Έτοιμοι για το επόμενο βήμα; Δοκιμάστε να προσθέσετε έναν φάκελο γραμματοσειρών, πειραματιστείτε με διαφορετικές πολιτικές αντικατάστασης, ή ενσωματώστε το callback στο υπάρχον σύστημα καταγραφής σας. Οι δυνατότητες είναι τόσο ευρείες όσο οι βιβλιοθήκες γραμματοσειρών που διαχειρίζεστε.

Καλή προγραμματιστική, και τα PDF σας να αποδίδουν πάντα ακριβώς όπως προορίζεται!

## Σχετικά Μαθήματα

- [Καταγραφή Προειδοποιήσεων Αντικατάστασης Γραμματοσειρών σε Java με Aspose.Words – Πλήρης Οδηγός](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Callback Προειδοποίησης σε Έγγραφο Word](/words/english/net/programming-with-loadoptions/warning-callback/)
- [Πώς να Φορτώσετε DOCX και να Ανιχνεύσετε Ελλιπείς Γραμματοσειρές – Πλήρης Οδηγός C#](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}