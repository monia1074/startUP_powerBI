### Init PowerBI

## Plan nauki (1–2 h dziennie)

Dzień 1: Podstawy interfejsu

Instalacja Power BI Desktop, przegląd: Report/Data/Model.
Import prostego Excela (tabela sprzedaży).
Pierwsze wizualizacje: Clustered column, Line, Card, Slicer.
Cel: Umiesz wczytać dane i zrobić prosty raport z filtrami.

Dzień 2: Power Query (ETL)

Transformacje: usuwanie kolumn, zmiana typów, Unpivot (Rozwiń/Przestaw), łączenie zapytań (Append/Merge).
Zasada: czyść w Power Query, licz w DAX.
Cel: Potrafisz przygotować „czyste” dane do modelu.

Dzień 3: Model danych

Relacje: 1:* (star schema), kierunek filtrowania, kardynalność.
Tabele wymiarów (Dim) i faktów (Fact); kalendarz jako osobna tabela dat.
Cel: Masz prosty model gwiazdy i rozumiesz kontekst filtrowania.

Dzień 4: DAX – miary podstawowe

Measures vs calculated columns.
SUM, COUNTROWS, DISTINCTCOUNT, AVERAGE; kontekst wiersza vs filtra.
Pierwsze miary: Sprzedaż = SUM(Fact[Amount]), Liczba klientów = DISTINCTCOUNT(DimCustomer[CustomerID]).
Cel: Kilka działających miar i zrozumienie, gdzie je tworzyć.

Dzień 5: DAX – czas i filtry

Tabela kalendarza (Date), funkcje TIME INTELLIGENCE: TOTALYTD, SAMEPERIODLASTYEAR, DATEADD.
Funkcje filtrujące: CALCULATE, FILTER, ALL, ALLEXCEPT.
Cel: YTD, YoY, % zmiany r/r na karcie i wykresie.

Dzień 6: Formatowanie i UX raportu

Formatowanie miar (tys., waluta), KPI/conditional formatting, Tooltips.
Slicery, hierarchie, Drill-through, Bookmarks (np. przełączanie widoków).
Cel: Czytelny dashboard z filtrami i tooltipami.

Dzień 7: Publikacja i refresh (jeśli masz Power BI Service)

Publikacja do Service, udostępnianie, Scheduled refresh, gateway (jeśli on-prem).
Najlepsze praktyki wersjonowania pliku .pbix.
Cel: Umiesz opublikować i odświeżać raport.

## Materiały polecane (krótkie i skuteczne)

YouTube: Guy in a Cube – świetne, konkretne filmy o DAX, modelowaniu i błędach dla początkujących.
Microsoft Learn: ścieżki „Get started with Power BI”, „Model data in Power BI” – darmowe, krok po kroku.
SQLBI (Marco Russo, Alberto Ferrari): „Introduction to DAX” i blog – świetne wytłumaczenie CALCULATE i kontekstu.
AdventureWorks lub Contoso sample dataset – dobre dane treningowe (sprzedaż, klienci, produkt).
Ćwiczenie minimum (wykonaj end‑to‑end)

## Dane:
Tabela sprzedaży: Data, Klient, Produkt, Kategoria, Region, Ilość, Cena, Kwota.
Słowniki: DimDate, DimCustomer, DimProduct, DimRegion.
Power Query:
Typy danych, usunięcie duplikatów klientów, unpivot promocji jeśli są w kolumnach, standard nazw kolumn.
Model:
Relacje 1:* z tabel wymiarów do faktów; kierunek Single; tabela kalendarza z pełnym zakresem dat.
Miary:
Sprzedaż = SUM(FactSales[Amount])
Ilość = SUM(FactSales[Quantity])
Marża = SUM(FactSales[Amount]) - SUM(FactSales[Cost])
Sprzedaż YTD = TOTALYTD([Sprzedaż], 'DimDate'[Date])
Sprzedaż YoY = CALCULATE([Sprzedaż], DATEADD('DimDate'[Date], -1, YEAR))
% YoY = DIVIDE([Sprzedaż] - [Sprzedaż YoY], [Sprzedaż YoY])

## Raport:
1 strona: Karty (Sprzedaż, Marża, % YoY), wykres kolumnowy (Sprzedaż wg Kategorii), liniowy (Sprzedaż miesięcznie), mapa wg Regionu, slicery: Rok, Kategoria, Region.
Dopracowanie:
Format liczbowy, jednostki (tys./mln), sortowanie wg miar, opis tooltipów.
Typowe pułapki i krótkie rady

Za dużo obliczeń w kolumnach – przenoś logikę do miar.
Relacje „both directions” bez potrzeby – powodują nieoczekiwane filtrowanie. Zostaw Single, a wyjątkowe przypadki rozwiązuj funkcjami DAX.
Brak tabeli dat – time intelligence nie zadziała poprawnie.
Łączenie wielu źródeł w jednej gigantycznej tabeli – lepiej model gwiazdy.
Zanim piszesz CALCULATE, upewnij się, jaki jest kontekst filtra na wizualizacji.
Jeśli chcesz, mogę:

Przygotować Ci plik .pbix z przykładowym modelem i ćwiczeniami.
Dać checklistę do weryfikacji modelu przed publikacją.
Odpowiedzieć na pytania po polsku podczas nauki (np. czemu miara daje BLANK itp.).


