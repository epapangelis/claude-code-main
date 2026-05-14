Κάναμε την πρώτη συνεδρία QA για το Kill Pipedrive. Φτάσαμε μέχρι το στάδιο Docs Received και Credit Check. Συνεχίζουμε την Τρίτη.

Κατηγοριοποιήσαμε τα ευρήματα σε blockers και non-blockers:

---

🔴 Blockers (2)

1. Filters & Views
Χρειαζόμαστε πιο ολοκληρωμένα φίλτρα στη λίστα των bookings (owner, stage, labels κ.α.). Προσωρινά μπορούμε να δουλέψουμε με τα υπάρχοντα φίλτρα, αλλά χρειάζεται να προγραμματιστεί η ανάπτυξη πριν το rollout.

2. Credit & Validation Process
Δεν ολοκληρώσαμε το QA αυτού του κομματιού. Θα το καλύψουμε ολοκληρωτικά την Τρίτη (validation rules, credit comments, counter-offer flow, car ID change logic).

---

🟡 Non-blockers (υπάρχουν αλλά δεν εμποδίζουν το rollout)

3. Booking Creation Modal
Βελτιώσεις που χρειάζονται: total amount display, extra KMS auto-populate από SKU, fetch campaign από SKU, prefill labels, αντικατάσταση 12ος/24ος με 1/2/3, διόρθωση dropdown μηνών.

4. instastart - Πεδίο Months
Το πεδίο Months στο instastart πρέπει να απενεργοποιηθεί ή να αφαιρεθεί από το booking modal.

5. Offer & PDF Flow
Preview του PDF πριν το submit, διόρθωση discrepancy μεταξύ products και offer.pdf, δυνατότητα discounts, custom extra KMS.

6. Sync με Pipedrive
Εκκρεμεί sync για: Origin/Holding Company, Company, Referral ID (synergatis), Billing detail (να εμφανίζεται το επιλεγμένο).

7. Communication & History
Τα auto emails/SMS ανά stage δεν καταγράφονται στο History. Επίσης: magic link στο Send Offer, ακύρωση reminder όταν αλλάζει stage το Tel Contact 1, αφαίρεση BCC drive@ από "Αδυναμία επικοινωνίας", templates SMS/mail.

8. User & Data Management
Merge duplicates, duplicate detection, delete permissions, AFM filter στα Subscriptions, εμφάνιση company identifier (AFM/organization) στο Users > Subscriptions.
