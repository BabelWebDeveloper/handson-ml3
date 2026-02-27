### Explanations

# 📊 Interpretacja kolumn `cv_results` (Punkt 12 – RandomizedSearchCV)

Tabela `cv_results` to pełny raport eksperymentu strojenia hiperparametrów.
Każdy wiersz = jeden zestaw parametrów.
Każda kolumna = informacja diagnostyczna o tym eksperymencie.

---

# 🟦 1️⃣ Kolumny czasowe (wydajność obliczeniowa)

### mean_fit_time
Średni czas trenowania modelu (sekundy), uśredniony po foldach.
Mówi jak kosztowny obliczeniowo jest dany zestaw hiperparametrów.

### std_fit_time
Odchylenie czasu trenowania między foldami.
Duża wartość może oznaczać niestabilność obliczeniową.

### mean_score_time
Średni czas liczenia metryki (F1 / accuracy).

### std_score_time
Zmienność czasu liczenia metryki.

---

# 🟦 2️⃣ Hiperparametry modelu

### param_model__min_samples_leaf
Minimalna liczba próbek w liściu.
Większa wartość → większa regularyzacja → większy bias, mniejsza variance.
działa jak regularyzacja

### param_model__max_leaf_nodes
Maksymalna liczba liści drzewa.
Większa wartość → większa złożoność modelu.

### param_model__max_depth
Maksymalna głębokość drzewa.
Większa wartość → większe ryzyko overfittingu.

### param_model__learning_rate
Tempo uczenia (boosting).
Mniejsze → stabilniejsze, wolniejsze.
Większe → szybsze, bardziej agresywne.

### param_model__l2_regularization
Regularyzacja L2.
Większa wartość → mniejsza wariancja.

### params
Pełny słownik parametrów (czytelna forma).

---

# 🟦 3️⃣ Wyniki F1 — walidacja (CV test folds)

### split0_test_f1 … split4_test_f1
F1 w każdym foldzie (różne okresy czasowe).
F1-score to miara jakości modelu klasyfikacyjnego - średnia harmoniczna precision i recall, innnymi słowy - jak dobrze model wykrywa klasę pozytywną, równoważąc fałszywe alarmy i przegapienia w różnych reżimach rynku.
Precision - Jak często model miał rację, gdy powiedział „wzrost”?
Recall - Jak dużo prawdziwych wzrostów model wykrył?

### mean_test_f1
Średni F1 ze wszystkich foldów.
Główna metryka jakości (jeśli refit="f1").

### std_test_f1
Zmienność F1 między okresami.
Mała wartość = model stabilny w czasie.

### rank_test_f1
Ranking modeli po F1.
1 = najlepszy.

---

# 🟦 4️⃣ Wyniki F1 — trening

### split0_train_f1 … split4_train_f1
F1 na danych treningowych w każdym foldzie.

### mean_train_f1
Średni F1 na train.

### std_train_f1
Zmienność F1 na train.

---

# 🟦 5️⃣ Wyniki Accuracy — walidacja

### splitX_test_accuracy
Accuracy w każdym foldzie.
Czyli procent z jakim model trafnie przewidział wartość (decyzję)

### mean_test_accuracy
Średni accuracy.

### std_test_accuracy
Zmienność accuracy.

### rank_test_accuracy
Ranking po accuracy.

---

# 🟦 6️⃣ Wyniki Accuracy — trening

### splitX_train_accuracy
Accuracy na train w każdym foldzie.

### mean_train_accuracy
Średni accuracy na train.

### std_train_accuracy
Zmienność accuracy na train.

---

# 🟦 7️⃣ Kolumny diagnostyczne (dodane ręcznie)

## generalization_gap_f1
mean_train_f1 - mean_test_f1

Duża wartość → overfitting  
Mała wartość → dobra generalizacja
bliski 0 → dobra generalizacja

---

## worst_fold_f1
Najniższy F1 ze wszystkich foldów.

Symuluje najgorszy okres rynkowy.

---

## stability_ratio_f1
std_test_f1 / mean_test_f1

Mierzy względną zmienność modelu.
Niższa wartość = większa stabilność.

---

## generalization_gap_accuracy
mean_train_accuracy - mean_test_accuracy

Analogicznie do F1, ale dla accuracy.

---

## worst_fold_accuracy
Najgorszy okres dla accuracy.

---

## stability_ratio_accuracy
Zmienność accuracy względem średniej.

---

# 🎯 Jak interpretować w tradingu? - Najważniejsze

Interpretacja zawsze powinna być względna względem baseline.
Same liczby nie mają znaczenia bez punktu odniesienia.

Najpierw patrz na:

1. mean_test_f1
2. std_test_f1
3. generalization_gap_f1
4. worst_fold_f1

Accuracy traktuj jako metrykę pomocniczą.

# Przykład 1 – model naprawdę lepszy

Baseline
mean_test_f1 = 0.55
std = 0.04
gap = 0.02
worst_fold = 0.50

Tuned model
mean_test_f1 = 0.63
std = 0.02
gap = 0.01
worst_fold = 0.60

To jest realna poprawa:

+0.08 mean
- większa stabilność (bo mniejszy std)
- mniejszy gap (mniejsza szansa na overfitting)
- wyższy najgorszy okres

# Przykład 2 – model wygląda dobrze, ale nie jest

Baseline
mean_test_f1 = 0.61
std = 0.02
gap = 0.01

Tuned
mean_test_f1 = 0.63
std = 0.07
gap = 0.15

Tu różnica +0.02 jest marginalna, a model jest:
- mniej stabilny (większe std)
- bardziej przeuczony (większe gap)