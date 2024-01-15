Operacje przeprowadzone na danych:
1. Wczytanie danych:
 Dane zostały wczytane z pliku "coin_bitcoin.csv" przy użyciu biblioteki pandas. Wstępna analiza została wykonana za pomocą funkcji `describe()` i `info()`.
2. Usunięcie niepotrzebnych danych: Skasowane zostały kolumny, które nie będą używane w procesie trenowania modelu (SNo, Name, Symbol). Daty zostały przekształcone do formatu `datetime`, a następnie dodano nową kolumnę 'Avg_Close_7days'.
3. Usuwanie wartości zerowych w kolumnie Volume: Usunięte zostały wiersze, w których wartość w kolumnie 'Volume' była równa 0.
4. Dodanie nowych kolumn: Dodano kolumny 'Amount Bitcoins', 'Intra-Day Volatility', 'Percent Intra-Day Volatility', 'Inter-Day Volatility', 'Percent Inter-Day Volatility'.
5. Analiza dystrybucji kolumn: Przeprowadzono analizę dystrybucji kolumn 'High', 'Low', 'Volume', 'Marketcap', 'Open', 'Close', 'Amount Bitcoins' za pomocą wykresów liniowych.
6. Normalizacja danych: Dane w kolumnie 'Close' zostały znormalizowane do zakresu [0,1] przy użyciu MinMaxScaler.
7. Podział danych na zestawy treningowe i testowe: Dane zostały podzielone na zestawy treningowe (x_train, y_train) i testowe (x_test, y_test) z oknem danych o szerokości 30.
8. Budowa modelu LSTM: Zbudowano model LSTM z warstwami Dropout w celu uniknięcia przeuczenia.
9. Trenowanie modelu: Model został wytrenowany przy użyciu danych treningowych.
10. Prognozowanie cen na danych testowych: Ceny zostały przewidziane dla danych testowych, a następnie odwrócono proces normalizacji, aby uzyskać rzeczywiste ceny.
11. Wizualizacja wyników: Porównano prognozowane ceny z rzeczywistymi za pomocą wykresu.
12. Ocena modelu: Wykorzystano metryki RMSE (Root Mean Squared Error) i MAE (Mean Absolute Error) do oceny skuteczności modelu.

Uzasadnienie operacji:
1. Usuwanie wartości zerowych w kolumnie Volume: Wartości zerowe w kolumnie 'Volume' mogą zakłócać analizę, dlatego zostały usunięte.
2. Normalizacja danych: Modely sieci neuronowych często lepiej działają, gdy dane są znormalizowane do zakresu [0,1].
3. Użycie modelu LSTM: Modele LSTM są skuteczne w przewidywaniu szeregów czasowych, takich jak ceny aktywów finansowych.
4. Dodanie nowych kolumn: Dodatkowe kolumny mogą dostarczyć modelowi dodatkowych informacji, co może poprawić jego skuteczność.

Analiza wyników:
Model LSTM wydaje się dobrze radzić z ogólnym trendem cen Bitcoin, jednak obserwuje się rozbieżność w przypadku dużych wzrostów i spadków cen. Prawdopodobnie wynika to z charakterystyki rynku kryptowalut, które są bardziej podatne na gwałtowne zmiany cen w porównaniu do tradycyjnych rynków finansowych.
Dodanie nowych kolumn do datasetu, takich jak ilość Bitcoinów, intra-day i inter-day volatility, może dostarczyć modelowi dodatkowych informacji, ale może również zwiększyć złożoność modelu.
Zmiana wielkości okna (window) może również wpływać na skuteczność modelu. Dłużej okno może uwzględniać bardziej odległe zależności czasowe, ale może również prowadzić do przeuczenia.
Podsumowując, model prezentuje dobrą tendencję do przewidywania cen Bitcoin, ale zjawiska specyficzne dla kryptowalut mogą wpływać na jego dokładność, a dodanie nowych danych i dostrojenie parametrów modelu mogą poprawić jego wydajność.
