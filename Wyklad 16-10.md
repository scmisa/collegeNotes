Postac programu wyrazona w jezyku programowania okreslona jest jako kod zrodlowy. Na jezyki programowania skladaja sie:
- skladnia - ktora opisuje rodzaje dostepnych symboli i zasady wedlug ktorych symbole moga byc laczone w wieksze struktury
- semantyka - ktora definiuje znaczenie poszczegolnych symboli oraz ich funkcje w programie
- typy danych 
- biblioteki standardowe - ktore zawieraja podstawowy zestaw funkcji pozwalajacy realizowac wszystkie najwazniejsze operacje

## Poprawność Algorytmu

### Definicja
> Przy danej specyfikacji algorytm jest calkowicie poprawny wtedy i tylko wtedy gdy dla kazdych poprawnych danych wejsciowych zachodzą oba ponizsze warunki:

- Algorytm zatrzymuje się po skończonej liczbie kroków (tzw. Własność Stopu)
- Algorytm przy zatrzymaniu zwraca poprawny wynik (tzw. częściowa poprawność algorytmu)


> Algorytm jest częsciowo poprawny jesli spelnia ponizszy warunek:
> 
> Jesli algorytm sie zatrzyma i otrzymal poprawne dane wejsciowe do zwracany jest poprawny wynik

Uwaga:
Częściowa Poprawnosc nie gwarantuje zatrzymania sie algorytmu.

```pseudocode

```

Istone są wszystkie detale nie wystarczy sam wzrost zmiennej, ale wystarczy wzrost o stalą wartosc,
nie wystarczy ze `len` jest stale ale takze ze jest skonczone.

Uwaga:
Dowodzenie czesciowej poprawnosci, wymaga zastosowania **niezmiennika pętli**.

> Niezmiennik Petli to logiczny predykat spelniajacy nastepujacy warunek:
> 
> Jesli predykat jest spelniony przed wejsciem w pewna dowolną iteracje petli to jest takze spelniony po wyjsciu z tej iteracji w petli.

Mozna zauwazyc analogię definicji niezmiennika petli do kroku indukcyjnego.
Idea jest taka ze tworzymy niezmiennik tak aby w momencie zakonczenia dzialania, algorytm byl rownowazny z warunkiem koncowym specyfikacji. 

Jesli predykat jest spelniony tuz przed pierwsza iteracją petli (krok bazowy indukcji) oraz jesli dodatkowo jest niezmiennikiem czyli po wejsciu w petlę zostanie zachowany, przez dowolną skończoną skonczoną liczbe iteracji, to wtedy jest tez spelniony na konczu algorytmu (po wyjsciu z pętli) nie zaleznie od tego ile bylo iteracji algorytmu.


Niezmiennik petli dla algorytmu wyznaczajacego maksimum z len pierwszych liczb zawartych w tablicy Arr. (rys.1)![[Pasted image 20251016092012.png]]

# Metody Projektowania Algorytmów

## - Metoda Dziel i Zwyciężaj #DivideAndConquer

Dziel i Zwyciężaj to technika projektowania algorytmów polegająca na podejściu rekurencyjnym.
Problem dzieliony jest na mniejsze podproblemy aż dojdzie się do przypadków trywialnych.
Jesli rozpatrywany problem wymaga podzielenia na podproblemy jest on okreslany jako przypadek rekurencyjny. Jesli mamy do doczynienia z przypadkiem trywialnym jest to przypadek bazowy tworząc algorytm wykorzystujacy metode dziel i zwyciezaj musimy ustalic:
1. Jak rozwiazac przypadek bazowy
2. Jak wyznaczyc rozwiazanie problemu, majac dostepne rozwiazania podproblemów

Przyklady:
1. Dysponując klockami oraz planszą 2^n na 2^n z brakujacym polem, wypelnic plansze w calosci:
	Przypadek trywialny:
	![[Pasted image 20251016092840.png]]
### Opis:
Oryginalną planszę dzielimy na 4 części 2^n-1 na 2^n-1 ale 3 z nich nie sa podobne do originalnego (nie maja brakujacego pola). Pomysl: umieszczamy jeden klocek na srodku planszy tak aby wszystkie 4 podproblemy spelnialy warunek poczatkowy zadania.

### - Poszukiwanie Binarne 
Odszukac poszukiwanej liczby, posortowanej tablicy
Przypadek trywialny: tablica jedno elementowa

### - Sortowanie Przez łączenie
1. Podziel jesli S posiada przynajmniej 2 elementy (0 lub 1 przypadek trywialny) podziel S na dwie rowne z dokladnoscia do jednego elementu czesci. S_1 i S_2. S_1 zawiera pierwsze pol elementow a S_2 drugie pol (S1 z nadmiarem S2 z niedomiarem)
2. Zwyciezaj - posortuj sekwencje S1 i S2 stosujac merge sort
3. Polacz elementy z dwoch posortowanych sekwencji S1, S2 w sekwencje S z zachowaniem porzadku

## Metoda Zachłanna #GreedyAlgorithm

Algorytm zachłanny to algorytm, który w celu wyznaczenia rozwiązania, w każdym kroku dokonuje zachłannego, to znaczy najlepiej rokujacego w danym momencie, wyboru rozwiazania częściowego. Algorytm zachlanny nie dokonuje oceny czy w kolejnych krokach jest sens wykonywac dane dzialanie, dokonuje decyzji lokalnie optymalnej, dokonuje wyboru wydajacego sie w danej chwili najlepszym, kontynuujac rozwiazanie podproblemu wynikajacego z podjetej decyzji. 

Uwaga:
Algorytmy zachlanne są deterministyczne. Nie ma w nich losowości.

#### Przyklady:
1. Wydawanie reszty. Dane są nominały, K-kwota do wydania, wynik - utworzyc k z najmniejszej liczby banknotów z najmniejszej liczby i monet.

Istniejące w świecie nominały, gdy tylko jest ich dostatecznie duzo w kasie, gwarantują że algorytm zachłanny daje zawsze najmniejsza liczbę banknotow i monet.