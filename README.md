# Instalacja SDK

https://cloud.google.com/sdk 

# Eksport danych rozliczeniowych do BigQuery

1. Płatności.
2. Eksport rozliczeń.
3. Edytuj ustawienia.
4. Wybór projektu.
5. Utworzenie zbioru danych.
6. W interfejsie BigQuery "Utwórz zbiór danych".

Ze względu na to, że zbiór danych będzie gromadził tylko dane rozliczeniowe, warto zastanowić się jaki czas wygaśnięcia tych danych ustawić (Data expiration). Najlepiej nigdy lub na minimum okres 3 miesiący.

7. Przechodzę spowrotem do panelu płatności. Eksport rozliczeń. Zapisz.

Po włączeniu funkcji eksportu do BigQuery może minąć kilka godzin, zanim zaczniesz widzieć swoje dane. Dane rozliczeniowe automatycznie eksportują Twoje dane do BigQuery w regularnych odstępach czasu, ale częstotliwość aktualizacji w BigQuery różni się w zależności od usług, z których korzystasz.

# Eksport danych rozliczeniowych do pliku

1. Przechowywanie danych.
2. Utwórz zasobnik.
3. Zalecany wybór lokalizacji regionalnej europe-west3.
4. Wybór klasy pamięci masowej. Zalacana klasa "Standard".
5. Wybór sposobu kontrolowania dostępu do obiektów. Zalecana "szczegółowa" kontrola dostępu.
6. Utwórz.

Teraz kiedy mam utworzony zasobnik mogę przejść do eksportu danych rozliczeniowych.

1. Płatności. 
2. Wybieram konto rozliczeniowe.
3. Eksport rozliczeń.
4. Wybieram zakładkę "Eksport pliku".
5. Edytuj ustawienia.
6. W polu "Nazwa zasobnika" podaję nazwę zasobnika utworzonego w poprzednich krokach. 

Eksport plików do CSV i JSON przechwytuje mniejszy zbiór danych niż eksport do BigQuery.

# Utworzenie i uruchomienie własnej instancji:

1. Compute Engine.
2. Instancje maszyn wirtualnych (za pierwszym razem platforma nicjalizuje API Google Compute Engine.
3. Utwórz.
4. Wskazanie regionu i strefy.
5. Wybór rodzaju maszyny np. seria N1
6. Utwórz.

# Odłączanie i ponowne mocowanie dysków startowych

1. Przed odłączeniem dysku należy zatrzymać instancję maszyny wirtualnej. 
2. Klikam w nazwę swojej instancji, aby wejść w szczegóły maszyny wirtualnej.
3. Edycja.
4. Usuwam dysk. Zapisz.

# Ponowne zamontowanie dysku 

1. Edycja.
2. Boot Disk. Dodaj element.
3. Zapisz.

# Tworzenie trwałych zrzutów z dysków twardych

Migawki mogą być przechowywane w lokalizacji wieloregionalnej Cloud Storage, takiej jak asia, lub w lokalizacji regionalnej, takiej jak asia-south1.

https://cloud.google.com/compute/docs/disks/create-snapshots







