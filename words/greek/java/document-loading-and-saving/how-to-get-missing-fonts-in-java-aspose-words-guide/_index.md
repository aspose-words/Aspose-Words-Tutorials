---
category: general
date: 2026-02-15
description: Μάθετε πώς να εντοπίζετε τις ελλιπείς γραμματοσειρές κατά τη φόρτωση
  ενός εγγράφου Word σε Java χρησιμοποιώντας το Aspose.Words. Περιλαμβάνει κλήσεις
  επιστροφής προειδοποιήσεων και διαχείριση αντικατάστασης γραμματοσειρών.
draft: false
keywords:
- how to get missing fonts
- Aspose.Words missing font
- font substitution warning
- Java LoadOptions warning callback
- document processing Java
language: el
og_description: Πώς να εντοπίσετε τις ελλιπείς γραμματοσειρές σε Java με το Aspose.Words.
  Ανακαλύψτε τις κλήσεις επιστροφής προειδοποιήσεων, τη διαχείριση αντικατάστασης
  γραμματοσειρών και τις βέλτιστες πρακτικές για την επεξεργασία εγγράφων.
og_title: Πώς να αποκτήσετε τις ελλείπουσες γραμματοσειρές στη Java – Οδηγός Aspose.Words
tags:
- Aspose.Words
- Java
- Font Management
title: Πώς να βρείτε τις ελλείπουσες γραμματοσειρές στη Java – Οδηγός Aspose.Words
url: /el/java/document-loading-and-saving/how-to-get-missing-fonts-in-java-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να Λάβετε Τα Ελλιπή Γραμματοσειρές σε Java – Οδηγός Aspose.Words

Έχετε ανοίξει ποτέ ένα έγγραφο Word σε Java και έχετε δει παράξενες αντικαταστάσεις γραμματοσειρών, αναρωτιέται **πώς να λάβετε τα ελλιπή γραμματοσειρές**; Δεν είστε ο πρώτος που αντιμετωπίζει αυτή την έκπληξη. Σε πολλές επιχειρηματικές εφαρμογές, οι προειδοποιήσεις για ελλιπείς γραμματοσειρές μπορούν να διαταράξουν την οπτική πιστότητα αναφορών, συμβάσεων ή διαφημιστικού υλικού.

Τα καλά νέα; Το Aspose.Words σας παρέχει έναν καθαρό τρόπο να συλλάβετε αυτές τις προειδοποιήσεις μέσω ενός callback, ώστε να μπορείτε να καταγράψετε, να αντικαταστήσετε ή ακόμη και να ειδοποιήσετε τους χρήστες πριν το έγγραφο αποδοθεί. Σε αυτό το tutorial θα περάσουμε από ένα πλήρες, εκτελέσιμο παράδειγμα που δείχνει **πώς να λάβετε τα ελλιπή γραμματοσειρές**, εξηγεί γιατί το callback είναι σημαντικό και καλύπτει μερικά κόλπα για ειδικές περιπτώσεις που μπορεί να χρειαστείτε σε πραγματικά έργα.

> **Pro tip:** Εάν χρησιμοποιείτε ήδη το Aspose.Words 22.12 ή νεότερο, το παρακάτω API λειτουργεί αμέσως χωρίς επιπλέον ρυθμίσεις.

---

![Διάγραμμα που απεικονίζει πώς να λάβετε ελλιπείς γραμματοσειρές χρησιμοποιώντας το callback προειδοποίησης του Aspose.Words](how-to-get-missing-fonts-diagram.png "διάγραμμα πώς να λάβετε ελλιπείς γραμματοσειρές")

## Τι Καλύπτει Αυτός Ο Οδηγός

- Ρύθμιση ενός **Java LoadOptions warning callback** για τη σύλληψη προειδοποιήσεων αντικατάστασης γραμματοσειρών.  
- Φιλτράρισμα των προειδοποιήσεων ώστε να βλέπετε μόνο εκείνες που σχετίζονται με ελλιπείς γραμματοσειρές.  
- Εκτύπωση μιας σαφούς, ανθρώπινα αναγνώσιμης αναφοράς για το ποιες γραμματοσειρές αντικαταστάθηκαν και με τι αντικαταστάθηκαν.  
- Συμβουλές για τη διαχείριση μεγάλων εγγράφων, την προσαρμογή του επιπέδου προειδοποίησης και την ενσωμάτωση της λύσης σε μεγαλύτερο pipeline επεξεργασίας.

Στο τέλος αυτού του οδηγού θα μπορείτε να απαντήσετε στην ερώτηση “**πώς να λάβετε τα ελλιπή γραμματοσειρές**?” με ένα έτοιμο προς εκτέλεση απόσπασμα κώδικα και μια στέρεη κατανόηση των υποκείμενων μηχανισμών.

### Προαπαιτήσεις

- Εγκατεστημένο Java 8 ή νεότερο.  
- Βιβλιοθήκη Aspose.Words for Java (κατεβάστε από την επίσημη ιστοσελίδα ή προσθέστε μέσω Maven/Gradle).  
- Ένα έγγραφο Word που αναφέρει μια γραμματοσειρά που δεν είναι εγκατεστημένη στο σύστημά σας (π.χ., `MissingFont.docx`).  

Εάν λείπει κάποιο από τα παραπάνω, αποκτήστε τη βιβλιοθήκη τώρα—η προσθήκη της στο Maven είναι τόσο απλή όσο:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version> <!-- replace with the latest version -->
</dependency>
```

---

## Βήμα 1: Προετοιμασία Συλλογής για Προειδοποιήσεις Αντικατάστασης Γραμματοσειρών

Πριν φορτώσουμε το έγγραφο, χρειαζόμαστε ένα μέρος για να αποθηκεύσουμε τυχόν προειδοποιήσεις που εκδίδει το Aspose.Words. Ένα `ArrayList<WarningInfo>` λειτουργεί άψογα επειδή διατηρεί τη σειρά και μας επιτρέπει να επαναλάβουμε αργότερα.

```java
import com.aspose.words.*;
import java.util.ArrayList;
import java.util.List;

// Step 1: Create a list that will hold warning information.
List<WarningInfo> fontWarnings = new ArrayList<>();
```

*Γιατί είναι σημαντικό:* Το callback προειδοποίησης μπορεί να ενεργοποιηθεί δεκάδες φορές για ένα μόνο αρχείο—σκεφτείτε κάθε ελλιπές γλύφη, κάθε πρόβλημα ενσωματωμένης εικόνας κ.λπ. Συλλέγοντας τα πρώτα, διατηρείτε τη φάση φόρτωσης γρήγορη και αναβάλλετε την επεξεργασία σε έναν ελεγχόμενο βρόχο.

## Βήμα 2: Διαμόρφωση LoadOptions με Warning Callback

Το Aspose.Words σας επιτρέπει να συνδέσετε ένα `IWarningCallback`. Μέσα στο callback θα προσθέσουμε κάθε `WarningInfo` στη λίστα μας από το Βήμα 1.

```java
// Step 2: Set up LoadOptions with a custom warning callback.
LoadOptions loadOptions = new LoadOptions();
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Capture every warning; we'll filter later.
        fontWarnings.add(info);
    }
});
```

*Εξήγηση:* Η μέθοδος `warning` καλείται **συγχρονισμένα** κατά τη φόρτωση του εγγράφου. Με το απλό άπλωμα του `WarningInfo` στο `fontWarnings`, αποφεύγουμε οποιοδήποτε βαρέως βάρους I/O (όπως καταγραφή σε αρχείο) που θα μπορούσε να επιβραδύνει τη φόρτωση. Αυτό το μοτίβο—συλλογή‑μετά‑επεξεργασία—είναι η προτεινόμενη προσέγγιση για μεγάλες παρτίδες προειδοποιήσεων.

## Βήμα 3: Φόρτωση του Εγγράφου Χρησιμοποιώντας τις Διαμορφωμένες Επιλογές

Τώρα διαβάζουμε πραγματικά το αρχείο Word. Εάν το έγγραφο περιέχει γραμματοσειρές που δεν είναι εγκατεστημένες, το Aspose.Words θα τις αντικαταστήσει αυτόματα και θα ενεργοποιήσει το callback προειδοποίησης που μόλις ρυθμίσαμε.

```java
// Step 3: Load the document with the warning‑aware LoadOptions.
String filePath = "YOUR_DIRECTORY/MissingFont.docx"; // adjust to your environment
Document doc = new Document(filePath, loadOptions);
```

*Τι συμβαίνει στο παρασκήνιο;* Το Aspose.Words αναλύει τον πίνακα γραμματοσειρών του αρχείου, τον συγκρίνει με τις γραμματοσειρές που είναι διαθέσιμες στο λειτουργικό σύστημα και για κάθε ελλιπή καταχώρηση δημιουργεί ένα `WarningInfo` με `WarningSource.FontSubstitution`. Αυτή η πηγή είναι το κλειδί που θα χρησιμοποιήσουμε για να απομονώσουμε τις προειδοποιήσεις ελλιπών γραμματοσειρών.

## Βήμα 4: Φιλτράρισμα και Εμφάνιση Μόνο Προειδοποιήσεων Αντικατάστασης Γραμματοσειρών

Μετά τη φόρτωση, το `fontWarnings` μπορεί να περιέχει ένα μίγμα μηνυμάτων (π.χ., παρωχημένες λειτουργίες, προβλήματα εικόνας). Ενδιαφερόμαστε μόνο για τις ελλιπείς γραμματοσειρές, οπότε διατρέχουμε τη λίστα και εκτυπώνουμε μια συνοπτική αναφορά.

```java
// Step 4: Output any font‑substitution warnings that were captured.
for (WarningInfo warning : fontWarnings) {
    if (warning.getSource() == WarningSource.FontSubstitution) {
        System.out.println("Substituted '" + warning.getDescription() + "' with '" +
                           warning.getAdditionalInfo() + "'");
    }
}
```

**Δείγμα εξόδου**

```
Substituted 'Comic Sans MS' with 'Arial'
Substituted 'Times New Roman PS' with 'Times New Roman'
```

*Γιατί είναι χρήσιμο:* Το πεδίο `description` σας λέει ποια γραμματοσειρά ζήτησε το έγγραφο, ενώ το `additionalInfo` σας δείχνει τι χρησιμοποίησε στην πραγματικότητα το Aspose.Words. Με αυτά τα δεδομένα μπορείτε:

- Να προτρέψετε τον χρήστη να εγκαταστήσει τη λείπουσα γραμματοσειρά.  
- Να ενσωματώσετε προγραμματιστικά μια εναλλακτική γραμματοσειρά στο έγγραφο (`doc.getFontInfos().add(...)`).  
- Να καταγράψετε το συμβάν για ελέγχους συμμόρφωσης.

## Διαχείριση Ειδικών Περιπτώσεων και Συνηθισμένων Παραλλαγών

### 1. Καταστολή Μη‑Γραμματοσειρικών Προειδοποιήσεων

Εάν θέλετε μόνο μηνύματα σχετιζόμενα με γραμματοσειρές, μπορείτε να σφιχτοποιήσετε το callback:

```java
loadOptions.setWarningCallback(info -> {
    if (info.getSource() == WarningSource.FontSubstitution) {
        fontWarnings.add(info);
    }
});
```

Αυτό μειώνει την κατανάλωση μνήμης όταν επεξεργάζεστε τεράστιες παρτίδες.

### 2. Προσαρμογή Βαρύτητας Προειδοποίησης

Το Aspose.Words κατηγοριοποιεί τις προειδοποιήσεις κατά `WarningType`. Για ελλιπείς γραμματοσειρές συνήθως βλέπετε `WarningType.FontSubstitution`. Εάν χρειάζεται να τις αντιμετωπίσετε ως σφάλματα (π.χ., να διακόψετε τη φόρτωση), ρίξτε μια εξαίρεση μέσα στο callback:

```java
loadOptions.setWarningCallback(info -> {
    if (info.getSource() == WarningSource.FontSubstitution) {
        throw new RuntimeException("Missing font detected: " + info.getDescription());
    }
});
```

### 3. Εργασία με Streams Αντί για Αρχεία

Μερικές φορές τα έγγραφα προέρχονται από βάση δεδομένων ή αίτημα HTTP. Η ίδια προσέγγιση λειτουργεί με ένα `InputStream`:

```java
InputStream docStream = new ByteArrayInputStream(bytesFromDb);
Document doc = new Document(docStream, loadOptions);
```

Απλώς θυμηθείτε να κλείσετε το stream μετά τη φόρτωση.

### 4. Χρήση Προσαρμοσμένου Φακέλου Γραμματοσειρών

Εάν διαθέτετε μια συλλογή εταιρικών γραμματοσειρών αποθηκευμένη σε κοινόχρηστο δίσκο, υποδείξτε το φάκελο στο Aspose.Words:

```java
loadOptions.setFontSettings(new FontSettings());
loadOptions.getFontSettings().setFontsFolder("C:/CorporateFonts", true);
```

Τώρα η βιβλιοθήκη θα ψάξει εκεί *πριν* καταφύγει στις συστημικές γραμματοσειρές, μειώνοντας δραστικά τον αριθμό των προειδοποιήσεων ελλιπών γραμματοσειρών.

---

## Πλήρες Παράδειγμα Εργασίας

Συνδυάζοντας όλα τα παραπάνω, εδώ είναι μια αυτόνομη κλάση που μπορείτε να ενσωματώσετε σε οποιοδήποτε έργο Java:

```java
import com.aspose.words.*;
import java.util.ArrayList;
import java.util.List;

public class MissingFontDetector {

    public static void main(String[] args) {
        // 1️⃣ Prepare a collection for warnings.
        List<WarningInfo> fontWarnings = new ArrayList<>();

        // 2️⃣ Create LoadOptions with a warning callback.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(info -> fontWarnings.add(info));

        // (Optional) Point to a custom font folder.
        // FontSettings fontSettings = new FontSettings();
        // fontSettings.setFontsFolder("C:/CorporateFonts", true);
        // loadOptions.setFontSettings(fontSettings);

        // 3️⃣ Load the document.
        String docPath = "YOUR_DIRECTORY/MissingFont.docx";
        Document doc;
        try {
            doc = new Document(docPath, loadOptions);
        } catch (Exception e) {
            System.err.println("Failed to load document: " + e.getMessage());
            return;
        }

        // 4️⃣ Print missing‑font warnings.
        System.out.println("=== Missing Font Report ===");
        for (WarningInfo warning : fontWarnings) {
            if (warning.getSource() == WarningSource.FontSubstitution) {
                System.out.println("Substituted '" + warning.getDescription() + "' with '" +
                                   warning.getAdditionalInfo() + "'");
            }
        }
        System.out.println("=== End of Report ===");
    }
}
```

Εκτελέστε αυτό το πρόγραμμα και θα δείτε μια καθαρή λίστα με κάθε γραμματοσειρά που το Aspose.Words έπρεπε να αντικαταστήσει. Χωρίς επιπλέον βιβλιοθήκες, χωρίς κρυφή μαγεία—απλώς καθαρή Java και η δύναμη του **Aspose.Words missing font** API.

---

## Συμπέρασμα

Απαντήσαμε στην κεντρική ερώτηση **πώς να λάβετε τα ελλιπή γραμματοσειρές** σε περιβάλλον Java χρησιμοποιώντας το Aspose.Words. Συνδέοντας ένα callback προειδοποίησης `LoadOptions`, συλλέγοντας αντικείμενα `WarningInfo` και φιλτράροντας για πηγές `FontSubstitution`, αποκτάτε πλήρη ορατότητα στα προβλήματα γραμματοσειρών πριν από οποιαδήποτε απόδοση. Η προσέγγιση κλιμακώνεται από εργαλεία μονής αρχείου μέχρι τεράστιους επεξεργαστές παρτίδων και είναι αρκετά ευέλικτη ώστε να υποστηρίζει προσαρμοσμένους φακέλους γραμματοσειρών, διαχείριση βαρύτητας ή εισροές βασισμένες σε stream.

Τι ακολουθεί; Δοκιμάστε να ενσωματώσετε τις αντικατεστημένες γραμματοσειρές απευθείας στο έγγραφο (`doc.getFontInfos().add(...)`) ώστε το τελικό αρχείο να είναι πραγματικά αυτόνομο, ή ενσωματώστε την αναφορά προειδοποίησης σε έναν πίνακα παρακολούθησης. Μπορείτε επίσης να ερευνήσετε συναφή θέματα όπως **document processing Java**, **Aspose.Words font substitution warning**, και **Java LoadOptions warning callback** για να εμβαθύνετε τις γνώσεις σας.

Καλό κώδικα, και εύχομαι τα έγγραφά σας να αποδίδουν πάντα με τις γραμματοσειρές που περιμένετε!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}