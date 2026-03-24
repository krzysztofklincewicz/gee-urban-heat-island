# Analiza Miejskiej Wyspy Ciepła (UHI) i Temperatury Powierzchni Ziemi (LST)

Projekt zawiera zautomatyzowany skrypt dla platformy Google Earth Engine (GEE), służący do przetwarzania zdjęć satelitarnych w celu wyznaczenia Temperatury Powierzchni Ziemi (Land Surface Temperature - LST) oraz analizy zjawiska Miejskiej Wyspy Ciepła (Urban Heat Island - UHI). 

Całość działa jako skrypt w Google Earth Engine i pozwala szybko wygenerować mapę temperatury powierzchni oraz proste statystyki dla wybranego miasta.

## Cel projektu
Głównym założeniem skryptu jest:
- Wygenerowanie wysokorozdzielczej mapy termalnej (GeoTIFF) dla dowolnego miasta.
- Przeprowadzenie analizy statystycznej polegającej na zestawieniu średnich temperatur LST z poszczególnymi klasami pokrycia terenu.
- Wygenerowanie czytelnego wykresu kolumnowego ułatwiającego interpretację wyników.

## Wykorzystane dane
1. Landsat 8 (C02/T1_L2):
- pasma optyczne → do NDVI
- pasmo termalne (Band 10) → do temperatury
- maskowanie chmur (QA_PIXEL)
- skalowanie zgodne z Collection 2

2. ESA WorldCover 2021 (v200):
- pokrycie terenu w rozdzielczości 10 m
- używane do podziału obszaru na klasy (np. zabudowa, roślinność, woda)

## Metodyka obliczeniowa
Algorytm przekształca surowe dane satelitarne w mapę LST poprzez następujące etapy:
1. NDVI – wskaźnik roślinności
2. FV (Fractional Vegetation) – ile jest roślinności na piksel
3. EM (Emissivity) – emisyjność powierzchni
4. LST – końcowa temperatura (na podstawie równania Plancka)

## Jak używać skryptu?
1. Skopiuj zawartość pliku .js do edytora Google Earth Engine.
2. W sekcji 1. PARAMETRY ANALIZY zmodyfikuj zmienne:
   - targetCity - nazwa miasta w języku angielskim (zgodnie z bazą FAO GAUL).
   - dateStart / dateEnd - ramy czasowe analizy (zalecane miesiące letnie maj-sierpień dla najlepszej widoczności UHI).
   - exportFileName - nazwa pliku wyjściowego.
3. Kliknij przycisk Run.
4. W zakładce Tasks uruchom eksport pliku GeoTIFF na swój Google Drive. Wykres statystyczny wygeneruje się automatycznie w konsoli edytora.
