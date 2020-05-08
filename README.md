# Instalacja SDK

https://cloud.google.com/sdk 

# Eksport danych rozliczeniowych do BigQuery

1. Płatności
2. Eksport rozliczeń
3. Edytuj ustawienia
4. Wybór projektu
5. Utworzenie zbioru danych 
6. W interfejsie BigQuery "Utwórz zbiór danych"

Ze względu na to, że zbiór danych będzie gromadził tylko dane rozliczeniowe, warto zastanowić się jaki czas wygaśnięcia tych danych ustawić (Data expiration). Najlepiej nigdy lub na minimum okres 3 miesiący.

7. Przechodzę spowrotem do panelu płatności. Eksport rozliczeń. Zapisz.

Po włączeniu funkcji eksportu do BigQuery może minąć kilka godzin, zanim zaczniesz widzieć swoje dane. Dane rozliczeniowe automatycznie eksportują Twoje dane do BigQuery w regularnych odstępach czasu, ale częstotliwość aktualizacji w BigQuery różni się w zależności od usług, z których korzystasz.

# Eksport danych rozliczeniowych do pliku

1. Przechowywanie danych
2. Utwórz zasobnik
3. Zalecany wybór lokalizacji regionalnej europe-west3
4. Wybór klasy pamięci masowej. Zalacana klasa: Standard
5. Wybór sposobu kontrolowania dostępu do obiektów. Zalecana #szczegółowa kontrola dostępu. 


