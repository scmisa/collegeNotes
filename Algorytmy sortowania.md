## Sortowanie Bąbelkowe
Prosta metoda sortowania o złożoności czasowej $O(n^2)$ i pamieciowej $O(1)$ polega ona na porownaniu 2 kolejnych elementów i zamianie ich kolejności jeśli ona zaburza porządek w jakim sortuje się tablice. Sortowanie kończy się jak podczas kolejnego przejścia nie dokonano żadnej zmiany.

Algorytm opiera się na zasadzie maksimum, tzn. każda liczba jest mniejsza lub równa liczbie maksymalnej. Porównując kolejno liczby można wyznaczyć największą z nich, następnie ciąg częściowo posortowany (mający liczbę maksymalną) można skrócić o tę liczbe i ponowić szukanie maksimum już bez elementów odrzuconych tak długo aż zostanie nam jeden element. Otrzymane kolejne maksima są coraz mniejsze przez co ciąg jest uporządkowany.

**Uwaga:**
Algorytm sortowania bąbelkowego jest uważany za bardzo zły algorytm sortujący, można go stosować tylko dla nie wielkiej liczby elementów w zbiorze. (Literatura podaje że 5000 elementów jest granicą)

## Sortowanie przez Selekcje (Sortowanie przez wybór)
Załóżmy że chcemy posortować zbiór liczbowy rosnąco, zatem element najmniejszy powinien znaleść się na 1 pozycji, szukamy w zbiorze elementu najmniejszego i wymieniamy go z elementem na 1 pozycji. Analogicznie postępujemy z pozostałymi elementami zbioru.
Algorytm tego typu ma zlozonosc $O(n^2)$ wiec podobnie jak sortowanie bąbelkowe nie poradzi sobie przy porzadkowaniu duzych zbiorów.

## Sortowanie przez wstawianie
Algorytm sortowania przez wstawianie można porównać do sposobu układania kart pobieranych z talii, najpierw bierzemy 1 kartę, nastepnie pobieramy kolejne. Każdą pobraną karte porównujemy z kartami, które już trzymamy w ręce i szukamy dla niej miejsca, przed pierwszą kartą starszą. Gdy znajdziemy takie miejsce, rozsuwamy karty i nową wstawiamy na przygotowane w ten sposób miejsce, jeśli nasza karta jest najstarsza, to umieszczamy ją na samym końcu.
Algorytm sortowania przez wstawianie będzie składał się z dwóch pętli, pętla głowna (zewnetrzna) symuluje pobieranie kart (elementu zbioru), odpowiednikiem kart na ręce, jest tzw. lista uporządkowana, którą sukcesywnie będziemy tworzyli na końcu zbioru. Pętla sortująca wewnętrzna szuka dla pobranego elementu, miejsca w liście uporządkowanej, jeśli takie miejsce zostanie znalezione, to elementy listy są odpowiednio rozsuwane, aby tworzyć miejsce na nowy element, i element wybrany przez petle glowna tam trafia, jesli na liscie uporzadkowanej nie ma elementu wiekszego od wybranego to element trafia na koniec listy. Sortowanie kończymy gdy pętla głowna przejdzie przez wszysktie elementy

**Uwaga**
Klasa czasowej zlozonosci $O(n^2)$

Algorytm sortowania przez wstawianie wykorzystuje poszukiwanie liniowe w celu znalezienia miejsca, wstawiania wybranego elementu na liscie uporzadkowanej.

Są 3 możliwości:
1. Element wybrany jest mniejszy bądź równy 1 elementowi listy uporządkowanej. Uwaga: w takim przypadku zostanie wykonane tylko jedno porównanie.
2. Element wybrany jest większy od ostatniego elementu listy uporządkowanej. Jeśli element znajduje się na $j$ pozycji to algorytm musi wykonać $n-j$ porównań elementu wybranego z elementami listy oraz tyle samo przesunięć elementów listy na puste miejsce
3. W pozostałych przypadkach element trafia do wnętrza listy uporządkowanej, statystycznie będzie to jej środek, zatem średnio algorytm wykona $\frac{1}{2} \cdot (n-j)$ porównań i przesunięć elementów. 

Ponieważ lista jest uporządkowana, możemy zastosować do niej algorytm przeszukiwania binarnego. 

Algorytm zoptymalizowanego sortowania przez wstawianie zbudowany jest z 3 pętli.
Pętla zewnętrzna `1` wybiera ze zbioru element leżący przed listą uporządkowaną, pętla wewn. `2`, poszukuje miejsca wykorzystując przeszukiwanie binarne, pętla wewn. 3 przesuwa elementy listy by zrobić miejsce dla elementu wybranego.
