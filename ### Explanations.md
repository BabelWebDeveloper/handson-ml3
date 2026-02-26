### Explanations

1. splitN_test_score - Foldy, wyniki metryki (np. F1) dla kolejnych okien czasowych
* F1-score to miara jakości modelu klasyfikacyjnego - średnia harmoniczna precision i recall
** Precision - Jak często model miał rację, gdy powiedział „wzrost”?
** Recall - Jak dużo prawdziwych wzrostów model wykrył?
** Interpretacja F1
*** Jeśli baseline (początkowa strategia używana dotychczas którą chcemy pokonać MLem) daje:
*** F1 = 0.50
*** A Twój model daje:
*** F1 = 0.71
*** Znaczy że ML działa dobrze
2. mean_test_score - średnia z foldów
3. std_test_score - odchylenie standardowe z foldów
** Interpretacja mean_test_score & std_test_score
*** Jeśli:
*** mean F1 = 0.63
*** std = 0.02
*** To znaczy:
**** model działa podobnie w różnych okresach
**** sygnał jest stabilny
**** mniejsze ryzyko „rozpadu” w przyszłości
*** Jeśli:
*** mean F1 = 0.63
*** std = 0.08