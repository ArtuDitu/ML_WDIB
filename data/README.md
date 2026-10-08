# Dane do kursu

Większość zbiorów danych (`insurance`, `iris`, `wholesale`) notebooki pobierają automatycznie funkcją
`pycaret.datasets.get_data()`, więc nie ma ich w tym folderze. Tutaj są tylko dwa pliki, których PyCaret nie udostępnia.
Oba pochodzą z [repozytorium książki](https://github.com/derevirn/pycaret-book).

| Plik | Tydzień | Opis | Źródło |
|---|---|---|---|
| `bbc-text.csv` | 9 (NLP) | 2225 artykułów BBC News z lat 2004–2005; kolumny `category` (business, entertainment, politics, sport, tech) i `text` | D. Greene, P. Cunningham, *Practical Solutions to the Problem of Diagonal Dominance in Kernel Document Clustering*, ICML 2006; zbiór udostępniony przez University College Dublin do celów edukacyjnych i naukowych: http://mlg.ucd.ie/datasets/bbc.html |
| `mauna_loa_co2.csv` | 10 (szeregi czasowe) | miesięczne stężenie CO₂ w atmosferze (ppm), obserwatorium Mauna Loa, 03.1958–12.2021; kolumny `datetime`, `CO2` | Scripps CO₂ Program, Scripps Institution of Oceanography (C. D. Keeling i in.): https://scrippsco2.ucsd.edu |

Zbiory pobierane przez `get_data()`:
- `insurance`: z książki B. Lantza *Machine Learning with R* (Packt),
- `iris`: R. A. Fisher (1936), UCI Machine Learning Repository,
- `wholesale`: *Wholesale customers*, UCI Machine Learning Repository.
