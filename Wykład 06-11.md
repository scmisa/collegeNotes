# Przeszukiwanie Sekwencyjne
### Problem:
W n elementowym zbiorze wyszukać element o zadanych własnościach.

Zadanie przeszukiwania sekwencyjnego polega na przeglądaniu kolejnych elementów zbioru znaleziony element zostaje zwrócony, zwykle interesuje nas nie sam element, a jego pozycja w zbiorze, lub algorytm zwraca informacje ze poszukiwanego elementu nie ma. Ponieważ wymagane jest sprawdzenie kolejnych elementów zbioru to w przypadku pesymistycznym (brak lub element jest na samym końcu), algorytm musi wykonać `n` porównań, pesymistyczna złożoność $W(N)=n$

Jeśli elementy są rozłożone losowo to prawdopodobieństwo poszukiwanego elementu na każdej pozycji w zbiorze jest takie samo i wynosi $P_i = 1/n$ zatem oczekiwana zlożoność algorytmu to:

$$A(n)=\sum_{i=1} 1/n$$

Dane wejściowe:
X - wartość poszukiwana
d[] - zbiór elementu

Dane wyjściowe:
p - pozycja elementu w zbiorze D - jesli p jest 0 to elementu w zbiorze nie ma


Lista kroków:
1. p<-1
2. dopóki (p<=n)^(x=/=d[p])
	wykonaj p<-p+1
3. Jeśli p>n to p <- 0
4. Koniec

Opis:
Przeszukiwanie zbioru rozpoczynamy od pierwszego elementu zmienna p przechowuje pozycje sprawdzanego elementu i na początku przyjmuje wartość 1. W pętli warunkowej najpierw sprawdzamy czy pozycja p wzkazuje element wewnątrz zbioru, jeśli nie pętla jest przerywana, drugi test w pętli sprawdza czy element zbioru na pozycji p jest różny od poszukiwanego elementu x jeśli TAK to pozycja p jest inkrementowana wzkazujac kolejny element zbioru i pętla kontynuuje się, jeśli NIE jest różny to element został znaleziony i pętla zostaje przerwana. Wyjście z pętli przeszukującej zbiór następuje w 2 przypadkach.
1. Przejrzany został cały zbiór elementu x nieznaleziono i pozycja p jest wieksza od n
2. Znaleziono x na pozycji p

Uwaga:
Wyzerowanie p jest czytelne i intuicyjne w zbiorze nie ma elementu na pozycji 0. Zwracanie 0-a w przypadku niepowodzenia jest często stosowaną praktyką w programowaniu, jeśli 0 jest możliwą wartością to często zwraca się -1 dla zaznaczenia porażki.


## Przeszukiwanie Binarne
### Problem: 
**W uporządkowanym zbiorze należy wyszukać element o wartości k**

Wyznaczamy element środkowy zbioru sprawdzamy czy jest on poszukiwanym elementem, jeśli TAK to koniec. Jeśli NIE to poszukiwany element jest albo mniejszy od elementu środkowego, albo większy. #DivideAndConquer Zatem w następnym obiegu zbiór możemy zredukować do I lub II połówki, z nowym zbiorem postępujemy identycznie, poszukiwanie kontynuujemy w odpowiedniej połówce zbioru aż znajdziemy poszukiwany element, lub do chwili gdy po podziale połówka nie zawiera dalszych elementów.

Ponieważ w każdym obiegu pętli algorytm redukuje liczbę elementów o połowę to jego klasa złożoności obliczeniowej jest równa $\Theta(n)=log \ n$ jest to bardzo korzystna złożoność. Np. w algorytmie przeszukiwania sekwencyjnego (liniowego) przy milionie elementów trzeba wykonać milion porównań, aby stwierdzić że poszukiwanego elementu nie ma w zbiorze. W algorytmie przeszukiwania binarnego wystarczy 20 porównań.

**Uwaga:**
Algorytm przeszukiwania binarnego może być stosowany tylko i wyłącznie w przypadku zbiorów uporządkowanych. W przeciwieństwie do algorytmu przeszukiwania liniowego, który możemy stosować dla dowolnego zbioru.

Dane wejściowe:
$i_p$ - indeks pierwszego elementu w tablicy z
$i_k$ - indeks ostatniego elementu w tablicy z
$Z[]$ - tablica do wyszukiwania elementu
$k$ - wartość poszukiwanego elementu (klucz)

Dane wyjściowe:
$p$ - indeks elementu o kluczu $k$
p = -1 - elementu nie znaleziono w danym zbiorze
$i_s$ - indeks elementu środkowego

Lista kroków:
1. p <- -1
2. Dopóki $i_p < i_k$ wykonuj kroki $k_2$ .... $k_{10}$
3. $i_s$ = $\frac{i_p - i_k}{2}$
4. jeśli k =/= $Z[i_s]$ 
5. p <- $i_s$
6. idz do $k_11$
7. jeśli $k<Z[i_s]$ to idz do $k_{10}$ 
8. $i_p$ <- $i_s +1$
9. Nastepny obieg pętli $k_2$
10. $i_k$ <- $i_s$ - 1
11. Koniec


### Rekurencja a iteracja
Definicja rekurencja (rekursja) -  to sposób definiowania procedur i funkcji (w algorytmach i programoach zapisany w językach wysokiegopoziomu) polegający na umieszczeniu w treści procedury (funkcji) odwołań do tej samej procedury (funkcji).

Przykład - wyznaczanie silnii

Stosowanie rekurencji jest charakterystyczne dla algorytmów Dziel i Zwycięzaj #DivideAndConquer
Zastosowanie rekurencji:
- algorytmy wyszukiwania
- rekurencyjne struktury danych

### Problemy:
1. Najwiecej problemów związanych z rekurencją wiąże się z ograniczeniami stosu wywołań, a właściwie jego pojemności, na stosie są odkładane kolejne wywołania metody i dopiero gdy dojdziemy do ostatniego elementu dane te są zbierane. Bardzo łatwo więc o sytuacje gdy stos przepełnimy.
	1. Zwiększyć rozmiar stosu (ostateczność)
	2. Wykonać optymalizacje i przerobić metodę na rekurencję ogonową(kolejne wywołanie metody otrzymuje jako kolejny parametr wyliczoną wartość i na stosie nie są wywolane kolejne elementy) (Problem: java nie wspiera tej rekurencji ogonowej)
	3. Przepisać algorytm w wersji iteracyjnej
2. Czas wykonania - tu lepszym rozwiązaniem jest iteracja

**Iteracja** to czynność powtarzania najczęściej wielokrotnego tej samej instrukcji lub wielu instrukcji w pętli, mianem iteracji określa się także operacje wewnątrz takiej pętli, w odróżnieniu do rekursji, która działa do góry, iteracja do obliczenia wartości wykorzystuje poprzednia n-tą iteracje, rekurencja potrzebuje zejść do 1-operacji. W większości języków programowania istnieje conajmniej kilka instrukcji iteracyjnych (for, while, do...while)

### Różnice pomiędzy iteracją a rekurencją
1. Rekurencja występuje wtedy gdy metoda w programie wielokrotnie wywołuje samą siebie podczas gdy iteracja ma miejsce gdy zestaw instrukcji w programie jest wielokrotnie wykonywany.
2. Rekurencja zawiera zestaw instrukcji, wywołanie samej instrukcji, i warunek zakończenia, a instrukcja iteracji zawiera inicjalizacje, inkrementacje, warunek, zestaw instrukcji w pętli i zmienną sterującą
3. Zdanie warunkowe decyduje o zakończeniu rekurencji, a wartości zmiennej sterującej decydują o zakończeniu instrukcji iteracyjnej
4. Jeśli metoda nie doprowadzi do stanu zakończenia, przechodzi w nieskończoną rekurencję, z drugiej strony jeśli zmienna sterująca nigdy nie prowadzi do wartości do zakończenia, instrukcja iteracji, iteruje w nieskończoność
5. Nieskończona rekurencja może doprowadzić do awarii systemu, a nieskończona iteracja pochłania cykle procesora
6. Rekurencja jest zawsze stosowana do metody, podczas gdy iteracja jest stosowana do zbioru instrukcji
7. c.d.n