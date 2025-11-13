#DynamicProgramming
To technika programowania algorytmów polegająca na rozwiązywaniu podproblemów i zapamiętywaniu ich wyników. W technice tej podobnie jak w metodzie #DivideAndConquer problemy dzielone sa na mniejsze podproblemy. Wyniki rozwiązywania podproblemów zapisywane sa w tabeli dzieki czemu w przypadku natrafienia na ten sam podproblem nie trzeba go ponownie rozwiązywać. Wykorzystując programowanie dynamiczne można zastosować metodę zstępujacą zapamietywaniem lub metode wstępującą.

1. Metoda stepujaca z zapamietywaniem polega na rekurencyjnym wywolaniem funkcji z zapamietywaniem wyników, metoda ta podobna jest do metody #DivideAndConquer rozni sie od niej tym że jesli rozwiazanie danego problemu jest juz w tabeli z wynikami, to nalezy je z tamtad odczytac.
2. Metoda wstepujaca polega na rozwiazywaniu wszystkich mozliwych podproblemow, zaczynajac od tych o najmniejszym rozmiarze, wówczas w momencie rozwiazania podproblemu, na pewno sa juz dostepne rozwiazania jego podproblemów. W tym podejsciu nie zużywa sie pamiecy na rekurencyjne wywolanie funkcji. Moze sie jednak okazac ze czesc problemow zostala rozwiazana nadmiarowo.

Programowanie Dynamiczne jest stosowane do rozwiazywania problemow...

Wlasnosc ta oznacza ze optymalne rozwiazanie problemu jest funkcją optymalnych rozwiazan podproblemów (czyli znajac optymalne rozwiazanie podproblemow mozna efektywnie roziwazani problem)

### Proces projektowania algorytmu opartego na programowaniu dynamicznym mozna podzielic na 4 etapy:
1. Scharakteryzowanie struktury optymalnego rozwiazania
2. Rekurencyjne zdefiniowanie kosztu optymalnego rozwiązania
3. Obliczenie optymalnego kosztu metoda wstepujaca
*4. Konstruowanie optymalnego rozwiazania na podstawie wczesniejszych obliczen *

### Dyskretny problem plecakowy:
Złodziej rabujący sklep znalazl n - przedmiotów i ten przedmiot maja C_i zł i waży W_i kg.
Dąży on do zabrania jak najwartosciowszego łupu, ale do swojego plecaka nie moze wziac wiecej niz W (kg)
Złodziej nie moze dzielic przedmiotów, ani zabrac wielokrotnosci przedmiotow.
Jakie przedmioty z puli `n` - wybranych przedmiotow moze zabrac zlodziej przy wymienionych wyzej ograniczeniach.


Dyskretny problem plecakowy nie moze byc rozwiazany metoda zachlanna, nie ma wlasnosci wyboru zachlannego.
Kontrprzyklad:
![[Pasted image 20251023091934.png]]
![[Pasted image 20251023092032.png]]Kryterium wyboru przy zastosowaniu metody zachlannej jest cena jednostkowa.

Przedmiot 1 zostal by wybrany jako 1-wszy nastepny bylby P2, do plecaka by nie trafil przedmiot 3 bo wszystkie 3 prezdmioty maja za duza wage. Rozwiazanie polegajace na wyborze przedmiotow 1 i 2 nie jest optymalne. Rozwiazanie optymalne jest wybor P2 i P3


**Dyskretny problem plecakowy** ma wlasnosc optymalnej podstruktury. Rozwazmy najwartosciowszy ladunek plecaka o masie nie wiekszej niz `W` jesli usuniemy z tego ladunku, przedmiot J o wadze W_J to pozostajacy ladunek jest najwartosciowszym zbiorem przedmiotow. O wadze nie przekraczajacej W ... Jakie zlodzej moze wybrac originalnych przedmiotow ....

 Dyskretny problem plecakowy można rozwiązać metodą dynamiczną
 1. Scharakteryzowanie struktury optymalnego rozwiązania $$ A = [0 \ldots n,; 0 \ldots b] \ 1 \le i \le n,\quad 0 \le s \le b \ A[i,s] \in {1, R, \ldots, i} $$ Jeśli obliczymy wszystkie elementy tej macierzy, to znajdziemy wartości wszystkich podproblemów — a więc także rozwiązanie optymalne dla całego problemu.
 2. Rekurencyjne zdefiniowanie kosztu optymalnego rozwiązania $$ \begin{aligned} V[0,S] &= 0 \quad \text{dla } 0 \le S \le b [6pt] V[i,s] &= \max \big( V[i-1,s],; w(a_i) + V[i-1,,s - s(a_i)] \big) \end{aligned} $$
 3. Obliczenie optymalnego kosztu metodą wstępującą Iteracyjnie wypełniamy macierz ( V[i,s] ) dla ( i = 1, 2, \ldots, n ) i ( s = 0, 1, \ldots, b ), stosując powyższą rekurencję. Wartość optymalnego rozwiązania otrzymujemy w ( V[n,b] ).

### Ciagly problem plecakowy

Ciągły problem plecakowy różni sie od dyskretnego tym że zlodziej może zabierać ułamkowe części przedmiotów (wygodniej jest wtedy mówic o substancji)
Uwaga: Ciągły problem plecakowy może byc rozwiązany metodą zachłanną.

### Algorytm
1. Obliczyć cenę jednostkowa kazdego przedmiotu
2. Zebrac najwiekszą możliwą ilość najbardziej wartościowych substancji
3. Jeśli zapas tej substancji sie wyczerpal a w plecaku jest jeszcze wolne miejsce złodziej wybiera nastepna pod wzgledem ceny jednostkowej, substancje i wypelnia ja plecak
4. Kroki 1, ,2, 3 sa powtarzane do momentu gdy plecak bedzie pełen
