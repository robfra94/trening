# Trening A/B – aplikacja na iPhone i komputer

To jest **działająca statyczna aplikacja webowa (PWA)**, którą można dodać do ekranu początkowego iPhone'a. Nie wymaga App Store, konta Apple Developer ani serwera z bazą danych. Po pierwszym wczytaniu działa także offline.

## Co robi

- Trening A i B naprzemiennie, bez przypisywania do dni tygodnia.
- Jedna karta na ćwiczenie, osobne pola **powtórzenia** i **kg**.
- Dowolna liczba serii 1–6 na treningu, edycja planu, celu i kroku ciężaru.
- Automatyczny zapis niezakończonego treningu na danym urządzeniu.
- Data ostatniego ukończonego treningu i kolejne zalecane A/B.
- Historia, poprawianie zapisanej sesji, sugestie ciężaru z zachowawczą podwójną progresją.
- Import obecnego Excela **Trening_AB_Model_Sily_v5.xlsx** i eksport do nowego, edytowalnego Excela.
- Import wcześniej wyeksportowanych arkuszy **PLAN A, PLAN B, HISTORIA**.

## Instalacja iPhone (GitHub Pages)

1. Utwórz na GitHubie repozytorium, np. `trening-ab`.
2. Otwórz rozpakowany katalog aplikacji i prześlij **pliki z jego wnętrza do katalogu głównego repozytorium**: `index.html`, `app.js`, `styles.css`, `jszip.min.js`, `sw.js`, `manifest.webmanifest`, `icon-192.png`, `icon-512.png`. (Nie trzeba publikować instrukcji.)
3. W repozytorium otwórz **Settings → Pages → Build and deployment → Deploy from a branch → main → / (root) → Save**.
4. Otwórz powstały adres `https://TWOJ-LOGIN.github.io/trening-ab/` w Safari na iPhonie.
5. Safari → **Udostępnij → Dodaj do ekranu głównego → Otwórz jako aplikację → Dodaj**.
6. Uruchom aplikację z ikony na ekranie telefonu. Zawiera od razu wyjściowe plany A i B. Jeśli masz wyniki w starym Excelu, wejdź w **Excel → Importuj Excel**.

Po instalacji aplikacja buforuje pliki i powinna działać offline. Zapis treningów jest lokalny.

## Komputer

Otwórz ten sam adres GitHub Pages na komputerze. Pliki mogą również działać po otwarciu `index.html` bezpośrednio na komputerze, ale instalacja i offline na iPhone wymagają adresu HTTPS.

## Synchronizacja danych i bezpieczeństwo

**Nie ma automatycznej synchronizacji danych między telefonem a komputerem.** GitHub Pages publikuje kod aplikacji, a nie przechowuje wpisanych treningów. Dla kontynuacji na innym urządzeniu użyj **Excel → Eksportuj**, zapisz plik do iCloud Drive/OneDrive, otwórz aplikację na drugim urządzeniu i użyj **Excel → Importuj**. Import zastępuje istniejące dane na danym urządzeniu.

Dane przechowywane są lokalnie w pamięci witryny na urządzeniu. Przed czyszczeniem danych Safari, reinstalacją aplikacji lub jej zmianą **wyeksportuj kopię Excel**. Aplikacja nie przesyła danych na żadne serwery.

## O progresji

- Gdy ostatnie serie wykonano na jednym ciężarze, zalecenie pozostaje bez zmian, dopóki wszystkie planowane serie nie osiągną górnej granicy zakresu. Dopiero potem może wzrosnąć o ustawiony krok (standardowo 2,5 kg dla złożonych, 1 kg dla izolowanych), jeśli oszacowany spadek powtórzeń jest akceptowalny.
- Gdy w treningu były różne ciężary, aplikacja wykorzystuje wszystkie serie w ważonej estymacji Epleya; nie obniża ciężaru poniżej najwyższego wykonanego z minimum planowanych powtórzeń.
- Bez rzeczywistego RIR (liczby powtórzeń w zapasie) nie można dokładnie określić bliskości upadku mięśniowego. Sugerowany ciężar jest wskazówką do oceny na siłowni, nie gwarancją.

## Struktura eksportu Excel

- **START** – ostatni trening i następny zalecany.
- **PLAN A** i **PLAN B** – edytowalna lista ćwiczeń, serii, min/max, krok kg, stabilny ID.
- **HISTORIA** – jedna sesja/ćwiczenie = jeden wiersz; do 6 par kolumn powtórzenia/kg (wygodne do analizy w Excelu).
- **INSTRUKCJA** – wskazówki w samym Excelu.

Jeśli plan będzie modyfikowany przez ChatGPT, najlepiej przekazać **ostatni plik wyeksportowany z aplikacji** i po poprawkach ponownie go zaimportować.

## Ograniczenia

Nie jest to natywna aplikacja ze sklepu App Store, tylko instalowana aplikacja webowa. Nie ma kont użytkowników ani synchronizacji w chmurze. Testy automatyczne sprawdziły import starszego Excela, eksport, ponowny import, zachowanie historii oraz reguły rekomendacji; wygląd i zachowanie na fizycznym iPhonie należy sprawdzić po publikacji.

Zależność: JSZip (MIT / GPLv3), licencja dołączona jako `LICENCJA_JSZip.md`.
