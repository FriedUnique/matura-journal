# matura-journal
Dieses Journal dokumentiert meinen Fortschritt in meiner Maturaarbeit ([Maturaarbeit-Repo](https://github.com/FriedUnique/matura-project)). </br>
Im Journal werden Tage oder Zeitabschnitte in Untertiteln angegeben


## 27.05.2023
Ich begann das Projekt in dem ich das "Market Sentiment" aus News-Artikel von Reuters herauslesen lies von meinem [Modul](https://github.com/FriedUnique/matura-project/tree/44829c7a32de6ba5c229c001fc2ed692ae5d50eb/Sentiment).

Beispiel der resultierenden Daten:

Index | Date | Sentiment
--- | --- | ---
0 | 2023-05-27 | 0.807
1 | 2023-05-26 | 0.672
2 | 2023-05-25 | -0.321
... | ... | ...

## 30.05.2023
Aus dem Gespräch mit meinem Lehrer ging folgendes heraus:
1. Daten, welches das Modul [`NLTK`](https://www.nltk.org/) herausgibt, besser verstehen und mathematisch wiedergeben können.
2. Mehrere und verschiedene Datenquellen verwenden, wie zum Beispiel Twitter und andere sozialen Netzwerke.
3. Projektvereinbarung ausfüllen.

## 17.06.2023 - 27.06.2023
In dieser Zeit hatte ich Zeit um meine Codebase einwenig aufzuräumen, damit der Code verständlicher wird. 
Als nächstes nahm ich mir vor wie man mein eigentliches Problem, nähmlich dem Vorhersagen eines Aktien-Trendes, angehen soll. Ich sammelte alle bisherigen Daten in einer Dataframe. -> [Code](https://github.com/FriedUnique/matura-project/blob/44829c7a32de6ba5c229c001fc2ed692ae5d50eb/DataFrameComputer.py). </br>
Die Dataframe sah dann beispielsweise so aus:

Index | O | H | L | C | Sentiment | C -1 | C -2 | C -3 | C -4 | C -5 | Sentiment -1 | Sentiment -2 | Sentiment -3 | Sentiment -4 | Sentiment -5 | Trend (label)
--- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
0 | 196.020 | 197.200 | 192.560 | 193.220 | 0.49 | 193.220 | 194.500 | 193.620 | 192.750 | 191.940 | 0.49 | 0.31 | 0.55 | -0.25 | 0.96 | 1 |
1 | ... | ... | ... | ... | ... | ... | ... | ... | ... | ... | ... | ... | ... | ... | ... | ... |

Um mir ein wenig Motivation zu verschaffen implementierte ich einen bereits existierenden Algorithmus mit dem ich die Richtung einer Aktie in 10 Tagen vorhersagen kann. Ich wähle den Random Forest Classifier (welcher kein DL-Algorithmus ist) aus, da er relativ simple ist und ich eigentlich nur ihn als Test brauchen wollte. In den Algorithmus speisste ich die aktuelle Aktien information ein (OHLC) und das aktuelle Sentiment. Dazu kommen noch vorherige Close- und Sentiment-Daten. Dabei dachte ich mir, dass diese Daten dem "simplen" Algorithmus helfen kann Zusammenhänge zu erkennen und diese (hoffentlich) Richtig zu Klassifizieren. <br>

## 30.07.2023
Ich habe mich zu 90% dazu entschlossen den LSTM-Algorithmus ([Paper](https://www.bioinf.jku.at/publications/older/2604.pdf)) zu gebrauchen. Ich fürchte es wird schwer zu implementieren und deshalb bin ich nicht 100% sicher ob ich diesen Weg wählen soll. Alternativ könnte ich eine "einfache" RNN implementation versuchen, welche jedoch weniger für time-series predictions gebaut ist und zudem schlechter long-term Zusammehänge erkennen kann. 
