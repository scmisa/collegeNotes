

Algorytmy o tej właściwości nazywa się algorytmami z nawrotami (backtracking). Charakteryzują się tym, że kolejny krok, który może prowadzić do rozwiązania, jest zapamiętywany; gdy później okaże się, że nie prowadzi do rozwiązania, następuje usunięcie jego zapisu i wycofanie się do stanu poprzedzającego błędną decyzję. Najbardziej naturalnym opisem algorytmów z nawrotami jest rekurencja.

## Dyskretny problem plecakowy

Poszukiwanie optymalnego rozwiązania metodą prób i błędów polega na systematycznym podejmowaniu kolejnych prób doboru przedmiotów — aż zostaną wyczerpane wszystkie dopuszczalne kombinacje. Dla każdego przedmiotu istnieją dwie możliwości: pozostawić go lub wziąć, co daje łącznie wszystkie kombinacje podzbiorów zbioru przedmiotów.

## Złożoność obliczeniowa oraz notacja asymptotyczna

Złożoność obliczeniową algorytmu definiuje się jako ilość zasobów komputerowych potrzebnych do jego wykonania. Podstawowymi zasobami rozważanymi podczas analizy algorytmu są czas wykonania oraz ilość zajmowanej pamięci. Nie zawsze możliwe jest wyznaczenie złożoności jako funkcji konkretnych danych wejściowych (np. drzewa, grafy, tablice, ciągi).

Zwykle z zestawem danych wejściowych wiąże się jego rozmiar, rozumiany jako liczba elementów składowych.

### Przykład

- Sortowanie (rozmiar -> liczba elementów w ciągu wejściowym)
- Problem przejścia drzewa binarnego (rozmiar -> liczba węzłów w drzewie)
- Problem wyznaczania wartości wielomianu (rozmiar -> stopień wielomianu)

Na złożoność obliczeniową składa się:

- złożoność pamięciowa
- złożoność czasowa

W przypadku złożoności pamięciowej za jednostkę przyjmuje się zwykle słowo pamięci maszyny. Złożoność czasowa powinna być własnością samego algorytmu jako metody rozwiązania problemu, niezależnie od komputera, języka programowania czy sposobu kodowania. W tym celu wyróżnia się w algorytmie operacje dominujące, takie że łączna ich liczba jest proporcjonalna do liczby wykonania wszystkich operacji jednostkowych w dowolnej implementacji.

### Przykłady

- Algorytmy sortowania (operacja dominująca: porównanie dwóch elementów)
- Algorytmy wyznaczania wartości wielomianu (operacja dominująca: operacje arytmetyczne)

Za jednostkę złożoności czasowej przyjmuje się wykonanie jednej operacji dominującej.

Złożoność obliczeniową algorytmu traktuje się jako funkcję rozmiaru danych $n$. Wyróżnia się złożoność pesymistyczną (worst-case) — zasoby potrzebne dla najgorszych danych wejściowych rozmiaru $n$ — oraz złożoność oczekiwaną (average-case) — zasoby potrzebne dla typowych danych wejściowych rozmiaru $n$.

$$
D_n\text{ — zbiór danych wejściowych rozmiaru }n\\
t(d)\text{ — liczba operacji wykonywanych dla danych }d\in D_n\\
X_n\text{ — zmienna losowa, której wartością jest }t(d)\\
p_{n,k}=\Pr(X_n=k)\text{ — rozkład prawdopodobieństwa zmiennej }X_n
$$

Rozkład prawdopodobieństwa zmiennej losowej $X_n$ wyznacza się na podstawie informacji o zastosowaniach rozważanego algorytmu, gdy zbiór danych jest opisywalny przez pewien rozkład.

## Pesymistyczna złożoność algorytmu

$$
W(n)=\sup_{d\in D_n} t(d)
$$

## Oczekiwana złożoność algorytmu

$$
A(n)=\sum_{k\ge 0} k\,p_{n,k}
$$

Aby ocenić, w jakim stopniu funkcje $W(n)$ i $A(n)$ reprezentują zachowanie algorytmu dla danych wejściowych rozmiaru $n$, rozważa się miary wrażliwości algorytmu:

- miara wrażliwości pesymistycznej — jak bardzo najgorsze przypadki wpływają na zachowanie algorytmu
- miara wrażliwości oczekiwanej — jak rozkład danych wpływa na średni czas działania

### Miary wrażliwości algorytmu

**Miara wrażliwości pesymistycznej:**

$$
\omega(n) = \sup \left\{ |t(d_1) - t(d_2)| : d_1, d_2 \in D_n \right\}
$$

**Wariancja (miara wrażliwości oczekiwanej):**

$$
\sigma(n) = D(X_n) = \sqrt{\text{Var}\,X_n} = \sqrt{\sum_{k\ge 0}(k - EX_n)^2 \cdot p_{n,k}}
$$

**Wartość oczekiwana:**

$$
EX_n = \sum_{k=1}^{n} \frac{1}{n}(1 + 2 + \ldots + n) = \frac{1}{n} \cdot \frac{n(n+1)}{2} = \frac{n+1}{2}
$$

Im większe są wartości liczbowe $\omega(n)$ i $\sigma(n)$, tym bardziej algorytm jest wrażliwy na dane wejściowe i tym bardziej może odbiegać od zachowania opisanego funkcjami $W(n)$ i $A(n)$.

### Przykład: Wyszukiwanie liniowe

Załóżmy, że prawdopodobieństwo znalezienia elementu `a` na każdym z $n$ możliwych miejsc jest takie samo, to znaczy $p_{n,k} = \frac{1}{n}$ dla $k = 1, 2, \ldots, n$.

Pesymistyczna złożoność czasowa: $W(n) = n + 1$

Oczekiwana złożoność czasowa: $A(n) = \frac{n+1}{2}$

Miara wrażliwości: $\omega(n) = n$

Wynika stąd duża wrażliwość liczby operacji dominujących na dane wejściowe.

## Notacja asymptotyczna

Faktyczna złożoność algorytmu (czas działania) w chwili jego użycia jako programu różni się od wyliczonej teoretycznie współczynnikiem proporcjonalności, który zależy od konkretnej realizacji tego algorytmu. Istotną zatem częścią informacji, która jest zawarta w funkcjach złożoności $A(n)$ i $W(n)$, jest **rząd wielkości**, czyli ich zachowanie asymptotyczne przy $n$ dążącym do nieskończoności. Zwykle staramy się podać jak najprostszą funkcję charakteryzującą rząd wielkości $W(n)$ i $A(n)$.

### Notacja O (duże O)

Niech $f, g, h: \mathbb{N} \to \mathbb{R}_{\geq 0}$. Mówimy, że $f$ jest rzędu $g$, oznaczane jako $f(n) = O(g(n))$, jeśli istnieją stała rzeczywista $c > 0$ oraz $n_0 \in \mathbb{N}$ takie, że:

$$
f(n) \leq c \cdot g(n) \quad \text{dla wszystkich } n \geq n_0
$$

**Przykład:**

$$
n^2 + 2n = O(n^2)
$$

ponieważ:

$$
n^2 + 2n \leq 3n^2 \quad \forall n \in \mathbb{N}
$$

### Notacja Ω (duże Omega)

$f(n) = \Omega(g(n))$ wtedy i tylko wtedy, gdy $g(n) = O(f(n))$.

Oznacza to, że $f$ rośnie co najmniej tak szybko jak $g$.

### Notacja Θ (duże Theta)

$f(n) = \Theta(g(n))$ wtedy i tylko wtedy, gdy:

- $f(n) = O(g(n))$ **i**
- $f(n) = \Omega(g(n))$

Oznacza to, że $f$ i $g$ rosną w tym samym tempie asymptotycznie.

### Porównywanie rzędów wielkości

Rzędy wielkości dwóch funkcji $f$ i $g$ mogą być porównywane dzięki granicy:

$$
\lim_{n \to \infty} \frac{f(n)}{g(n)} = L
$$

gdzie:

- Jeśli $L = 0$, to $f(n) = O(g(n))$ i $f$ rośnie wolniej niż $g$
- Jeśli $0 < L < \infty$, to $f(n) = \Theta(g(n))$ i $f$ i $g$ rosną w tym samym tempie
- Jeśli $L = \infty$, to $f(n) = \Omega(g(n))$ i $f$ rośnie szybciej niż $g$

### Typowe rzędy wielkości (od najwolniejszego wzrostu) #EGZAMIN

1. $O(1)$ — stała
2. $O(\log n)$ — logarytmiczna - czas działania logarytmiczny występuje np. dla algorytmów typu zadanie rozmiaru `n` zostaje sprowadzone do zadania rozmiaru n na 2+pewna stała liczba działań, np. poszukiwanie binarne
3. $O(n)$ — liniowa - złożoność liniowa, czas działania liniowy występuje np. dla algorytmów, w których jest wykonywana pewna stała liczba działań dla każdego z n elementów danych wejściowych np. algorytm hornera
4. $O(n \log n)$ — liniowo-logarytmiczna - czas dzialania wystepuje np. dla algorytmów typu: zadanie rozmiaru n zostaje sprowadzone do 2 podzadań n1/2 +pewna liczba dzialań liniowa względem rozmiaru n potrzebnych do wykonania najpierw rozbicia a nastepnie scalenia rozwiazania rozmiaru n1/2 w rozwiazanie rozmiaru n (merge-sort)
5. $O(n^2)$ — kwadratowa - czas działania kwadratowy występuje np. dla algorytmów, których jest wykonywana pewna stała liczba działań dla każdej pary elementów, podwójna instrukcja iteracyjna
6. $O(n^3)$ — sześcienna
7. $O(2^n)$ — wykładnicza - czas działania $2^n$ ma algorytm w którym jest wykonywana stała liczba działań dla każdego podzbioru danych wejsciowych
8. $O(n!)$ — silnia - wykładnicza - czas działania n! ma np. algorytm w którym jest wykonywana stała liczba działań dla każdej permutacji danych wejściowych

Uwaga:
1. Algorytm o złożoności wykładniczej może byc realizowany dla małych rozmiarów danych, istnieje próg dla którego funkcja zaczyna rosnąć tak szybko że realizacja algorytmu na komputerze staje się nie możliwa
2. Dane wejściowe dla których czas działania jest wykładniczy mogą się nigdy nie pojawić w rzeczywistych okolicznościach np. **metoda simplex programowania liniowego**, choć ta metoda ma złożoność wykładniczą dla najgorszych danych dla pojawiających się w praktyce danych wejściowych działa w czasie wielomianowym, a nawet liniowym

Przy korzystaniu z wyników analizy złożoności algorytmu należy brać pod uwage następujące uwarunkowania:
- algorytm i jego realizacja sa wyrażone w 2 różnych językach
- wrażliwość algorytmu na dane wejściowe może spowodować że faktyczne zachowanie się algorytmu na używanych danych może odbiegać od zachowania opisanego przez $W(n)$ i $A(N)$ 
- może być trudno przewidzieć rozkład $X(n)$
- dla niektórych algorytmów nie są znane matematyczne oszacowania $W(n)$ i $A(N)$ 
- czasami działanie 2 algorytmów jest trudno jednoznacznie porównać jeden działa dla pewnej klasy zestawu danych a drugi dla innych

