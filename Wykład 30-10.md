# Metoda prób i błędów (Trial and Error)

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
Złożoność obliczeniową algorytmu traktuje się jako funkcję rozmiaru danych n. Wyróżnia się złożoność pesymistyczną (worst-case) — zasoby potrzebne dla najgorszych danych wejściowych rozmiaru n — oraz złożoność oczekiwaną (average-case) — zasoby potrzebne dla typowych danych wejściowych rozmiaru n.

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


..Wynika stąd duza wrazliwosc liczby operacji dominujacych na dane wejsciowe


Faktyczna złożoność algorytmu (czas dzialania) -  w chwili jego uzycia jako programu różni sie od wyliczonej teoretycznie współczynnikiem proporcjonalności, który zależy od konkretnej realizacji tego algorytmu. Istotną zatem częścią informacji ktora jest zawarta w funkcjach zlozonosci A(n) i W(n) jest rząd wielkosci czyli ich zachowanie asymptotyczne przy `n` dązącym do nieskonczonosci. Zwykle staramy się podac jak najprostszą funkcje charakteryzujaca rzad wielkosci W(n) i A(n).

Niech $f, g, h: N -> R_t 0$ mówimy ze f jest rzędu g $f(n)=O(g(n))$ jeśli istnieją stała rzeczywista, $c>0$ oraz $n_0 \in N$ , $f(n) <= g(n)$ 

$$n^2 +2n = O(n^2)$$ *,bo*
$$n^2+2n<=3n^2$$ $$\forall _n \in N$$
$f(n) = \Omega(g(n))$ $g(n)=O(f(n))$
$f(n)=O(g(n))$ i $f(n)=\Omega(g(n))$



Rzędy 2 wielkosci f i g moga byc porownywane dzieki granicy