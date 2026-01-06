## 1. Przygotowanie danych
## 1.1 Model Sequential dla obrazków
## 1.2 To samo co powyzej ale inaczej napisane
## 1.2.1 Wyświetlenie podsumowania modelu i wizualizacje
## 1.3 Kompilacja modelu
## 1.4 To samo co wyzej ale inaczej napisane
## 1.4.1 Konwersja klasy do hot-one encoder
## 1.5 Trening modelu
## 1.6 Wizualizuj wyniki treningu
## 1.7 Poprawione - Wizualizuj wyniki treningu, z objaśnieniami
## 1.8 Stwórz predykcje
## 1.8.1 Wizualizacja predykcji
## 2. Załaduj dane - domy w Kaliforni
## 2.1 Stwórz warstwy, model, skompiluj i wytrenuj model, stwórz predykcje
## 2.2 Resetuj kod pod tworzenie Interfejsu funkcyjnego - przykład z powyzej
## 2.2.1 Stworzenie interfejsu funkcyjnego
## 2.2.2 Wyświetlenie podsumowania modelu i wizualizacje
## 2.3 Reszta etapów identyczna
## 2.3.1 kompilacja modelu
## 2.3.2 dostosowanie warstwy Normalization
## 2.3.3 dopasowanie modelu
## 2.3.4 ocena modelu
## 2.3.5 prognozowanie modelu
## 2.4 Podział cech na ścieżkę krótką i głęboką
## 2.5 Wybór optymalizera, kompilacja modelu, podział danych treningowych na dwie ściezki, trening modelu, ocena i predykcje
## 2.6 Dodanie dodatkowego wyjścia
## 2.7 Dodanie dodatkowej funkcji straty do kazdego wyjscia
## 2.8 Dodanie warstw normalizacji i trening modelu
## 2.9 Ocena modelu
## 2.10 Predykcje
## 2.11 Stworzenie interfejsu podklasowego
## 2.11.1 Wybór optymalizera
## 2.11.2 Kompliacja modelu
## 2.11.3 Trening modelu
## 2.11.4 Ocena modelu
## 2.11.5 Predykcje
## 2.12 Zapisywanie modelu
## 2.13 Załadowanie zapisanego modelu i odpalenie
## 2.14 Zastosowanie wywołań zwrotnych - umozliwia stworzenie punktów kontrolnych w procesie uczenia
## 2.15 Przerwanie procesu uczenia gdy przez określoną liczbę epok nie wykryje poprawy skuteczności na zbiorze walidacyjnym
## 2.16 Customowe wywołanie zwrotne które wyswietla stosunek między funkcją straty dla zestawu walidacyjnego a funkcją straty dla zestawu uczącego w fazie uczenia np. w celu wykrycia przetrenowania
## 2.17 Uzycie tensorboard jako wywołania zwrotnego w którym mozna analizować proces uczenia
## 2.18 Zapisywanie dodatkowych informacji do TensorBoard
## 3. Powrót do danych z "obrazków"
## 3.1 Budowa funkcji do wyszukiwania najlepszych hiperparametrów
## 3.2 Przeszukiwanie najlepszych parametrów za pomocą RandomSearch oraz zbudowanej funkcji build_model
## 3.3 Dostrajanie hiperparametrów wstępnego przetwarzania danych lub argumentów
## 3.4 Przekazanie klasy do obiektu strojącego
## 3.5 Uruchomienie obiektu Hyperband z wywołaniem TensorBoard - Hyperband przygotuje osobne podkatalogi dla każdej próby