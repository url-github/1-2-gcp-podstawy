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

1. Compute Engine.
2. Zrzuty dysku.
3. Utwórz zrzót.
4. Wybieram dysk źródłowy z wcześniej utworzonej instancji maszyny wirtualnej. 
5. Wybór lokalizacji: wiele regionów, region.
6. Utwórz.

Tworzenie harmonogramu tworzenia migawek: https://cloud.google.com/compute/docs/disks/scheduled-snapshots

# Przenoszenie instancji pomiędzy strefami

Najlepiej przenosić instancję automatycznie za pomocą moveInstance API jak poniżej. Jeśli nie jest to możliwe poprzez API należy wykonać to ręcznie. 

1. Compute Engine.
2. Uruchamiam Cloud Shell.
3. Komenda: 
> gcloud compute instances move gclab3 --zone europe-west3-a --destination-zone europe-west3-b 
lub
> gcloud compute instances move instance-1 --zone us-central1-b --destination-zone us-entral1-f
4. Po zakończonym procesie mam komunikat: "Moving gce instance instance_name…done"

# Przenoszenie instancji pomiędzy regionami (za pomocą Cloud Shell)

1. Sprawdzam jakie posiadam migawki dysku: 
> gcloud compute snapshots list
2. Tworzę dysk z wcześniej utworzonej migawki w nowym regionie:
> gcloud compute disks create gclab3-new --source-snapshot migawka-05-12-19
3. Po poprawnym wykonaniu komendy automatycznie wyświetli się lista dostępnych regionów, w których mogę utworzyć dysk, ponieważ nie zdefiniowaliśmy tej własności w naszej komendzie za pomocą odpowiedniego przełącznika. Wybieram inny region / strefę np. asia-northeast1-a.
4. Kiedy posiadam dysk w odpowiednim regionie i strefie tworzę instancję z dyskiem
> gcloud compute instances create <instance_name> --machine-type f1-micro --disk name=<disk_name>,boot=yes,mode=rw
5. Did you mean zone [region] for instance: (Y/n)? n
6. Ponownie automatycznie wyświetli się lista dostępnych regionów oraz stref. Wskazuję na ten sam region, w którym utworzyłem wcześniej dysk (inaczej konsola zwróci błąd o niedostępności). Wskazuję na region oraz strefę asia-northeast1-a ponownie wpisując odpowiadający tej lokalizacji numer.

# Uruchomienie skryptów startowych

1. Compute Engine.
2. Instancje maszyn wirtualnych.
3. Zapora sieciowa - zezwalaj na ruch HTTP. Pozwoli to zweryfikować poprawność działania skryptu. 
4. Rozwijam listę "Zarządzanie...".
5. W polu skrypt startowy wklejam kod. Jest to polecenie, które instaluje serwer Apache oraz modyfikuje stronę startową.
> #! /bin/bash
> apt-get update
> apt-get install -y apache2
> cat <<EOF > /var/www/html/index.html
> <html><body><h1>Hello World</h1>
> <p>This page was created from a simple startup script!</p>
> </body></html>















