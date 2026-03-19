---
category: general
date: 2026-03-19
description: Μάθετε πώς να καταγράφετε προειδοποιήσεις στο Aspose.Words for Java και
  να εντοπίζετε ελλείπουσες γραμματοσειρές. Αυτός ο βήμα‑βήμα οδηγός δείχνει επίσης
  πώς να διαχειρίζεστε τις ελλείπουσες γραμματοσειρές με χάρη.
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- how to detect missing fonts
- handle missing fonts
language: el
og_description: Πώς να καταγράψετε προειδοποιήσεις στο Aspose.Words for Java, να εντοπίσετε
  ελλείπουσες γραμματοσειρές και να διαχειριστείτε τις ελλείπουσες γραμματοσειρές
  με ένα πλήρες παράδειγμα κώδικα.
og_title: Πώς να καταγράψετε προειδοποιήσεις – Εντοπισμός ελλιπών γραμματοσειρών στο
  Aspose.Words
tags:
- Aspose.Words
- Java
- Font Substitution
- Document Processing
title: Πώς να καταγράψετε προειδοποιήσεις – Εντοπισμός ελλιπών γραμματοσειρών στο
  Aspose.Words
url: /el/java/document-rendering/how-to-capture-warnings-detect-missing-fonts-in-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να Καταγράψετε Προειδοποιήσεις – Ανίχνευση Ελλειπούσων Γραμματοσειρών στο Aspose.Words

Έχετε αναρωτηθεί ποτέ **πώς να καταγράψετε προειδοποιήσεις** όταν ένα έγγραφο Word φορτώνεται και κάποιες γραμματοσειρές δεν είναι διαθέσιμες στο μηχάνημα; Δεν είστε μόνοι. Σε πολλά πραγματικά έργα, οι ελλειπούσες γραμματοσειρές προκαλούν σιωπηλές αλλαγές διάταξης, και ο μόνος τρόπος να μάθετε τι συνέβη είναι ακούγοντας το ρεύμα προειδοποιήσεων που εκδίδει το Aspose.Words.

Σε αυτό το σεμινάριο θα περάσουμε από ένα πλήρες, έτοιμο‑για‑εκτέλεση παράδειγμα που **ανιχνεύει ελλειπούσες γραμματοσειρές**, σας δείχνει **πώς να ανιχνεύσετε ελλειπούσες γραμματοσειρές** προγραμματιστικά, και ακόμη δίνει μια γρήγορη συμβουλή για **τη διαχείριση ελλειπούσων γραμματοσειρών** ώστε η έξοδός σας να παραμένει προβλέψιμη.

> **Σύντομη σημείωση:** Ο κώδικας λειτουργεί με Aspose.Words 23.9 (ή νεότερη) και απαιτεί Java 8+.

---

## Τι Θα Χρειαστείτε

- **Aspose.Words for Java** (εξάρτηση Maven/Gradle ή JAR στην κλάση‑διαδρομή)  
- Ένα αρχείο Word (`input.docx`) που αναφέρει μια γραμματοσειρά που δεν είναι εγκατεστημένη στο σύστημά σας (π.χ., “Comic Sans MS”)  
- Ένα Java IDE ή απλή ρύθμιση γραμμής εντολών `javac`/`java`  

Δεν απαιτούνται άλλες βιβλιοθήκες—όλα τα υπόλοιπα βρίσκονται μέσα στο πακέτο Aspose.Words.

## Βήμα 1 – Ρύθμιση LoadOptions για Καταγραφή Προειδοποιήσεων  

Για να αρχίσετε να ακούτε προειδοποιήσεις πρέπει να δημιουργήσετε μια παρουσία `LoadOptions`. Αυτό το αντικείμενο λέει στον φορτωτή να παρακολουθεί τυχόν προβλήματα που συναντά, όπως ελλειπούσες γραμματοσειρές.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Create LoadOptions that will store warning information
        LoadOptions loadOptions = new LoadOptions();

        // ... the rest of the code follows
```

**Γιατί είναι σημαντικό:** Χωρίς `LoadOptions` ο φορτωτής αντικαθιστά σιωπηρά τις ελλειπούσες γραμματοσειρές με την προεπιλεγμένη γραμματοσειρά του συστήματος, και δεν θα μάθετε ποτέ ότι έγινε αντικατάσταση. Η ενεργοποίηση των προειδοποιήσεων σας δίνει πλήρη ορατότητα.

## Βήμα 2 – Φόρτωση του Εγγράφου Χρησιμοποιώντας το LoadOptions  

Τώρα φορτώνουμε πραγματικά το έγγραφο. Το `LoadOptions` που δημιουργήσαμε μόλις τώρα περνιέται στον κατασκευαστή, ώστε τυχόν προειδοποιήσεις που δημιουργούνται κατά την ανάλυση να καταγραφούν.

```java
        // Step 2: Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**Συμβουλή:** Αν επεξεργάζεστε πολλά αρχεία σε παρτίδα, επαναχρησιμοποιήστε την ίδια παρουσία `LoadOptions` για να αποφύγετε περιττή δημιουργία αντικειμένων.

## Βήμα 3 – Επανάληψη πάνω στις Καταγεγραμμένες Προειδοποιήσεις  

Το Aspose.Words αποθηκεύει κάθε προειδοποίηση ως αντικείμενο `WarningInfo`. Εμείς ενδιαφερόμαστε μόνο για προειδοποιήσεις σχετικές με γραμματοσειρές, έτσι φιλτράρουμε για `FontSubstitutionWarningInfo`.

```java
        // Step 3: Loop through all warnings generated while loading
        for (WarningInfo warning : document.getWarnings()) {
            // Step 3a: Keep only font substitution warnings
            if (warning instanceof FontSubstitutionWarningInfo) {
                FontSubstitutionWarningInfo fontWarning = (FontSubstitutionWarningInfo) warning;

                // Step 4: Output the requested and actual font names
                System.out.println("Requested: " + fontWarning.getRequestedFontName()
                        + " → Substituted: " + fontWarning.getActualFontName());
            }
        }
    }
}
```

**Explanation:**  
- `document.getWarnings()` επιστρέφει μια λίστα με κάθε προειδοποίηση που συνέβη κατά τη φόρτωση.  
- `FontSubstitutionWarningInfo` περιέχει δύο κρίσιμα στοιχεία δεδομένων: τη **ζητούμενη γραμματοσειρά** (αυτή που ζήτησε το DOCX) και την **πραγματική γραμματοσειρά** στην οποία επανέλθε το Aspose.Words.  
- Με την εκτύπωση και των δύο, βλέπετε αμέσως ποιες γραμματοσειρές λείπουν και ποια αντικατάσταση πραγματοποιήθηκε.

## Βήμα 4 – (Προαιρετικό) Διαχείριση Ελλειπούσων Γραμματοσειρών Προγραμματιστικά  

Η καταγραφή των προειδοποιήσεων είναι μόνο το ήμισυ της ιστορίας. Μόλις γνωρίζετε ότι λείπει μια γραμματοσειρά, μπορεί να θέλετε να **διαχειριστείτε ελλειπούσες γραμματοσειρές** παρέχοντας μια προσαρμοσμένη αντικατάσταση ή καταγράφοντας το ζήτημα για μελλοντική ανασκόπηση.

```java
                // Optional: Replace the missing font with a known fallback
                FontSettings fontSettings = new FontSettings();
                fontSettings.getSubstitutionSettings().getTableSubstitution()
                    .addSubstitutes(fontWarning.getRequestedFontName(), "Arial");
                document.setFontSettings(fontSettings);
```

**Γιατί το κάνετε;**  
- Εγγυάται συνεπή απόδοση σε διαφορετικές μηχανές.  
- Αποτρέπει απροσδόκητες αλλαγές διάταξης σε PDFs ή εικόνες που δημιουργούνται αργότερα.  

Μπορείτε επίσης να αποθηκεύσετε τις λεπτομέρειες της προειδοποίησης σε μια βάση δεδομένων, να στείλετε email στην ομάδα περιεχομένου, ή ακόμη και να διακόψετε τη διαδικασία εάν λείπει μια κρίσιμη γραμματοσειρά.

## Πλήρες Παράδειγμα Λειτουργίας  

Παρακάτω βρίσκεται το πλήρες, εκτελέσιμο πρόγραμμα. Απλώς αντικαταστήστε το `YOUR_DIRECTORY/input.docx` με τη διαδρομή του αρχείου δοκιμής σας, προσθέστε το Aspose.Words JAR στην κλάση‑διαδρομή σας, και τρέξτε.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // 1️⃣ Create LoadOptions to capture warnings
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // 3️⃣ Iterate through all warnings
        for (WarningInfo warning : document.getWarnings()) {
            // 3a️⃣ Filter only font substitution warnings
            if (warning instanceof FontSubstitutionWarningInfo) {
                FontSubstitutionWarningInfo fontWarning = (FontSubstitutionWarningInfo) warning;

                // 4️⃣ Display the requested and actual font names
                System.out.println("Requested: " + fontWarning.getRequestedFontName()
                        + " → Substituted: " + fontWarning.getActualFontName());

                // 5️⃣ (Optional) Provide a custom fallback
                FontSettings fontSettings = new FontSettings();
                fontSettings.getSubstitutionSettings().getTableSubstitution()
                    .addSubstitutes(fontWarning.getRequestedFontName(), "Arial");
                document.setFontSettings(fontSettings);
            }
        }

        // 6️⃣ Save the document if you need to see the result with the fallback applied
        document.save("output.docx");
    }
}
```

**Αναμενόμενη έξοδος** (όταν λείπει το “Comic Sans MS”):

```
Requested: Comic Sans MS → Substituted: Arial
```

Μετά την εκτέλεση του προαιρετικού κώδικα εναλλακτικής λύσης, το αποθηκευμένο `output.docx` θα αποδίδει χρησιμοποιώντας **Arial** όπου το “Comic Sans MS” αναφερόταν αρχικά.

## Συχνές Ερωτήσεις & Ακραίες Περιπτώσεις  

| Ερώτηση | Απάντηση |
|----------|--------|
| *Τι γίνεται αν το έγγραφο έχει πολλαπλές ελλειπούσες γραμματοσειρές;* | Ο βρόχος θα εκδώσει μια προειδοποίηση για καθεμία. Μπορείτε να τις συλλέξετε σε ένα `Map<String, String>` για επεξεργασία παρτίδας. |
| *Λειτουργεί αυτό για PDFs που δημιουργούνται από το έγγραφο;* | Απολύτως. Η αντικατάσταση γραμματοσειρών συμβαίνει κατά τη φάση φόρτωσης, έτσι οποιαδήποτε μεταγενέστερη εξαγωγή (PDF, HTML, εικόνα) χρησιμοποιεί τις επιλυμένες γραμματοσειρές. |
| *Μπορώ να καταστέλλω τις προειδοποιήσεις αντί να τις καταγράφω;* | Ναι—ορίστε `loadOptions.setWarningCallback(null);` αλλά θα χάσετε την ορατότητα στις ελλειπούσες γραμματοσειρές. |
| *Καθαρίζεται η λίστα προειδοποιήσεων μετά την αποθήκευση;* | Η συλλογή προειδοποιήσεων ανήκει στην παρουσία `Document`. Μετά την κλήση `document.save()`, η λίστα παραμένει αμετάβλητη εκτός εάν δημιουργήσετε νέο `Document`. |
| *Τι γίνεται με προσαρμοσμένες γραμματοσειρές ενσωματωμένες στο DOCX;* | Οι ενσωματωμένες γραμματοσειρές θεωρούνται διαθέσιμες· το Aspose.Words θα τις χρησιμοποιήσει ακόμη και αν δεν είναι εγκατεστημένες στο σύστημα υποδοχής. |

## Επαγγελματικές Συμβουλές για Χρήση σε Παραγωγή  

- **Cache FontSettings:** Εάν επεξεργάζεστε εκατοντάδες αρχεία, δημιουργήστε ένα ενιαίο `FontSettings` με τις προτιμώμενες εναλλακτικές λύσεις σας και επαναχρησιμοποιήστε το για να αποφύγετε το κόστος.  
- **Log Structured Data:** Αντί σε απλό `System.out`, γράψτε τις προειδοποιήσεις σε ένα JSON log—αυτό κάνει την ανάλυση downstream (π.χ., “πιο συχνές ελλειπούσες γραμματοσειρές”) απλή.  
- **Validate Early:** Εκτελέστε μια γρήγορη “dry‑load” με `LoadOptions` πριν από βαριά επεξεργασία· διακόψτε νωρίς εάν λείπουν κρίσιμες γραμματοσειρές.  
- **Thread Safety:** Τα αντικείμενα `Document` δεν είναι thread‑safe. Διατηρήστε την επεξεργασία κάθε αρχείου στο δικό του νήμα ή χρησιμοποιήστε thread‑local `LoadOptions`.  

## Συμπέρασμα  

Τώρα γνωρίζετε **πώς να καταγράψετε προειδοποιήσεις** στο Aspose.Words για Java, **να ανιχνεύσετε ελλειπούσες γραμματοσειρές**, και **να διαχειριστείτε ελλειπούσες γραμματοσειρές** με μια καθαρή στρατηγική εναλλακτικής λύσης. Χρησιμοποιώντας το `LoadOptions` και επαναλαμβάνοντας το `document.getWarnings()`, αποκτάτε πλήρη εικόνα των γεγονότων αντικατάστασης γραμματοσειρών, εξασφαλίζοντας ότι τα παραγόμενα έγγραφά σας φαίνονται ακριβώς όπως προβλέπεται σε όλα τα περιβάλλοντα.

Έτοιμοι για το επόμενο βήμα; Δοκιμάστε να επεκτείνετε αυτό το μοτίβο για **ανίχνευση ελλειπούσων εικόνων**, **παρακολούθηση μη υποστηριζόμενων χαρακτηριστικών**, ή ακόμη **αυτόματη ενσωμάτωση ελλειπούσων γραμματοσειρών** στο αρχείο εξόδου. Η ίδια προσέγγιση καταγραφής προειδοποιήσεων λειτουργεί για πολλές άλλες περιπτώσεις επεξεργασίας εγγράφων, κάνοντας τον κώδικά σας ανθεκτικό και έτοιμο για το μέλλον.

Καλό κώδικα, και εύχομαι τα έγγραφά σας να αποδίδουν πάντα όμορφα!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}