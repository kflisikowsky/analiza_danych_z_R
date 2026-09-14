---
title: "Rozdział 1. Wstęp do języka R"
subtitle: Podstawy składni, obiektów i programowania w R
---

# Rozdział 1. Wstęp do języka R

## Cele rozdziału

Po ukończeniu tego rozdziału będziesz umieć:

- wykonywać obliczenia i przypisywać wartości do obiektów,
- rozpoznawać podstawowe typy danych w R,
- tworzyć wektory, listy i ramki danych,
- korzystać z funkcji oraz operatorów indeksowania,
- zapisywać proste warunki i pętle.

## Czym jest R?

R jest językiem programowania i środowiskiem obliczeniowym używanym przede
wszystkim do analizy danych, statystyki i wizualizacji. Polecenia można
wykonywać pojedynczo w konsoli albo zapisać w skrypcie `.R`, aby analiza była
powtarzalna.

Komentarze zaczynają się od znaku `#` i nie są wykonywane:

```{code-cell} r
# To jest komentarz
2 + 2
```

## Obliczenia i przypisania

R obsługuje podstawowe działania matematyczne. Wynik można przypisać do
obiektu za pomocą operatora `<-`:

```{code-cell} r
podstawa <- 8
wykladnik <- 2
pole <- podstawa^wykladnik
pole
```

Do wyświetlenia wartości można użyć `print()`, a do sprawdzenia obiektów
znajdujących się w środowisku funkcji `ls()`:

```{code-cell} r
print(pole)
ls()
```

## Typy danych

Najczęściej spotykane typy atomowe w R to liczby, teksty, wartości logiczne
i wartości brakujące `NA`:

```{code-cell} r
liczba <- 3.14
tekst <- "język R"
logiczna <- TRUE
brak_danych <- NA

typeof(liczba)
typeof(tekst)
typeof(logiczna)
```

Funkcja `class()` opisuje klasę obiektu, a `is.numeric()` i podobne funkcje
pozwalają sprawdzić jego typ:

```{code-cell} r
class(liczba)
is.numeric(liczba)
is.character(tekst)
is.logical(logiczna)
```

## Wektory i indeksowanie

Wektor tworzymy funkcją `c()`. Wszystkie elementy wektora powinny mieć
zgodny typ:

```{code-cell} r
temperatury <- c(18, 21, 19, 23, 20)
temperatury
length(temperatury)
```

Elementy wybieramy za pomocą indeksu w nawiasach kwadratowych. Indeksowanie
w R zaczyna się od `1`:

```{code-cell} r
temperatury[1]
temperatury[2:4]
temperatury[temperatury > 20]
```

Wektor nazw można połączyć z wektorem wartości logicznych, aby wybrać
konkretne elementy:

```{code-cell} r
names(temperatury) <- c("pon", "wt", "sr", "czw", "pt")
temperatury[c("pon", "pt")]
```

## Podstawowe struktury danych

Ramka danych (`data.frame`) przechowuje dane w kolumnach o tej samej liczbie
wierszy:

```{code-cell} r
dane <- data.frame(
  imie = c("Anna", "Bartek", "Celina"),
  wiek = c(21, 25, 23),
  student = c(TRUE, FALSE, TRUE)
)

dane
str(dane)
```

Listy mogą przechowywać elementy różnych typów:

```{code-cell} r
profil <- list(
  imie = "Anna",
  wiek = 21,
  zainteresowania = c("R", "statystyka")
)

profil$imie
profil$zainteresowania
```

## Funkcje

Funkcja składa się z nazwy, argumentów i ciała. Własną funkcję definiujemy
operatorem przypisania:

```{code-cell} r
powitaj <- function(imie) {
  paste("Witaj,", imie, "!")
}

powitaj("R")
```

Argument może mieć wartość domyślną:

```{code-cell} r
potega <- function(x, wykladnik = 2) {
  x^wykladnik
}

potega(3)
potega(3, 3)
```

## Warunki i pętle

Instrukcja `if` wykonuje kod tylko wtedy, gdy warunek jest prawdziwy:

```{code-cell} r
wynik <- 78

if (wynik >= 60) {
  print("Zaliczone")
} else {
  print("Nie zaliczone")
}
```

Do powtarzania operacji można użyć pętli `for`:

```{code-cell} r
for (liczba in 1:5) {
  print(liczba^2)
}
```

## Podsumowanie

W tym rozdziale poznaliśmy podstawy języka R:

- komentarze, działania i przypisania,
- liczby, teksty, wartości logiczne i `NA`,
- wektory, ramki danych i listy,
- indeksowanie od pozycji `1`,
- definiowanie i wywoływanie funkcji,
- instrukcje warunkowe i pętle.

Te elementy są fundamentem dalszej pracy z danymi oraz pakietami takimi jak
`dplyr`, `ggplot2` i `tidyr`.
