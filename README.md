# Praktyczny Machine Learning z PyCaret – Kurs Podstawowy (12 Tygodni)

[![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/ArtuDitu/ML_WDIB?quickstart=1)

Praktyczny kurs uczenia maszynowego dla **zupełnie początkujących**: 12 spotkań po 90 minut, po jednym notebooku Jupyter na tydzień.
Kurs jest oparty na książce **Giannisa Toliosa _Simplifying Machine Learning with PyCaret_** ([Leanpub, 2023](https://leanpub.com/pycaretbook))
i jej [repozytorium z kodem](https://github.com/derevirn/pycaret-book). Zaczynamy od pojęć podstawowych, a kończymy na
**działającej aplikacji internetowej z modelem ML**, opublikowanej w chmurze.

Całe środowisko (Python 3.10, PyCaret, pandas, Seaborn, Streamlit…) instaluje się **automatycznie** w GitHub Codespaces.
Na swoim komputerze nie trzeba nic instalować, wystarczy przeglądarka.

---

## 📑 Spis treści
1. [Szybki start: GitHub Codespaces](#-szybki-start-github-codespaces-zalecane)
2. [Praca w lokalnym VS Code połączonym z Codespaces](#-praca-w-lokalnym-vs-code-połączonym-z-codespaces)
3. [Inne sposoby uruchomienia](#-inne-sposoby-uruchomienia)
4. [Harmonogram 12 tygodni](#-harmonogram-12-tygodni)
5. [Jak zbudowany jest każdy notebook](#-jak-zbudowany-jest-każdy-notebook)
6. [Struktura repozytorium](#-struktura-repozytorium)
7. [Różnice względem książki](#-różnice-względem-książki-pycaret-30--332)
8. [Rozwiązywanie problemów](#-rozwiązywanie-problemów-faq)
9. [Źródła i licencje](#-źródła-i-licencje)

---

## 🚀 Szybki start: GitHub Codespaces (zalecane)

**GitHub Codespaces** to komputer w chmurze z edytorem VS Code otwieranym w przeglądarce. Konfiguracja z pliku
[`.devcontainer/devcontainer.json`](.devcontainer/devcontainer.json) sama instaluje Pythona 3.10 i wszystkie biblioteki
z [`requirements.txt`](requirements.txt).

### Krok po kroku
1. **Załóż konto / zaloguj się na [GitHub](https://github.com)** (wystarczy darmowe konto).
   🎓 Studenci mogą bezpłatnie dostać [GitHub Student Developer Pack](https://education.github.com/pack), który zwiększa limit godzin Codespaces.
2. **Kliknij przycisk** [![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/ArtuDitu/ML_WDIB?quickstart=1)
   (albo na stronie repozytorium: zielony przycisk **`<> Code`** → zakładka **Codespaces** → **Create codespace on main**).
3. Na stronie konfiguracji kliknij **Create new codespace** (domyślna maszyna 2-rdzeniowa, 8 GB RAM wystarczy).
4. **Poczekaj na zbudowanie środowiska.** ⏳ Pierwsze uruchomienie trwa **ok. 5–10 minut**, bo instaluje się PyCaret
   (postęp widać w logu *Setting up your codespace*). Kolejne uruchomienia tego samego codespace'a trwają kilkanaście sekund.
5. Gdy otworzy się VS Code w przeglądarce, w panelu plików po lewej otwórz
   `notebooks/tydzien_01_wstep_do_ml_i_pycaret.ipynb`.
6. W prawym górnym rogu notebooka kliknij **Select Kernel** → **Python Environments…** → **Python 3.10** (`/usr/local/bin/python`).
7. Uruchamiaj kolejne komórki skrótem **Shift + Enter**. Gotowe! 🎉

### 🐍 Czy muszę instalować Pythona? **Nie!**
W codespace **wszystko jest już zainstalowane**: Python 3.10, PyCaret i pozostałe biblioteki są w kontenerze w chmurze,
a rozszerzenia VS Code (Python, Jupyter) instalują się same. Na swoim komputerze nie instalujesz niczego.

**Szybki test:** otwórz terminal (menu **Terminal → New Terminal**) i wpisz:
```bash
python --version                                          # powinno być: Python 3.10.x
python -c "import pycaret; print(pycaret.__version__)"    # powinno być: 3.3.2
```

Jeśli VS Code prosi o **instalację Pythona** albo testy pokazują inną wersję (np. 3.12) lub błąd `No module named 'pycaret'`, sprawdź po kolei:

| Objaw | Przyczyna | Co zrobić |
|---|---|---|
| Okienko *„Install/Enable suggested extensions: Python + Jupyter”* przy wyborze jądra | VS Code mówi o **rozszerzeniach** edytora, nie o samym Pythonie. Zwykle pojawia się, gdy notebook otwarto, zanim rozszerzenia się doinstalowały | Kliknij **Install/Enable**, poczekaj kilka sekund i wybierz jądro **Python 3.10** |
| `python --version` pokazuje inną wersję niż 3.10, brakuje PyCaret | Codespace powstał **bez konfiguracji kursu** – np. utworzono go, zanim folder `.devcontainer/` trafił na GitHuba, albo z innej gałęzi | <kbd>F1</kbd> → **Codespaces: Rebuild Container** (albo usuń codespace na [github.com/codespaces](https://github.com/codespaces) i utwórz nowy z gałęzi `main`) |
| Na dole ekranu komunikat *„running in recovery mode”* | Budowanie kontenera się nie powiodło | <kbd>F1</kbd> → **Codespaces: View Creation Log**, a potem **Rebuild Container**. Jeśli błąd się powtarza – zgłoś go prowadzącemu (z logiem) |
| Pracujesz w **lokalnym** VS Code, ale z folderem otwartym z dysku (a nie z codespace'em) | Lokalny komputer nie ma Pythona 3.10 i bibliotek | Połącz się z codespace'em (sekcja niżej) – lewy dolny róg VS Code musi pokazywać **„Codespaces”** |

### Dobrze wiedzieć ⚠️
- **Limit darmowych godzin:** konto GitHub Free ma **120 „godzin rdzeniowych” miesięcznie** (= ok. **60 godzin** pracy na maszynie 2-rdzeniowej)
  i 15 GB miejsca. GitHub Pro / Student Developer Pack: 180 godzin rdzeniowych (ok. 90 godzin). Cały kurs to ok. 18 godzin zajęć.
- **Zatrzymuj codespace po zajęciach**, żeby nie zużywać limitu: [github.com/codespaces](https://github.com/codespaces) → **⋯** przy codespace → **Stop codespace**.
  Codespace sam zatrzymuje się po 30 minutach bezczynności.
- **Twoje pliki zostają w codespace** po jego zatrzymaniu. Nieużywany codespace jest jednak **automatycznie usuwany po 30 dniach**,
  więc ważne rzeczy zapisuj na swoim GitHubie (*commit* + *push*; przy repozytorium prowadzącego Codespaces zaproponuje utworzenie **forka**).
- Kolejne kliknięcie przycisku *Open in GitHub Codespaces* (z `?quickstart=1`) **wznawia istniejący** codespace zamiast tworzyć nowy.

> 🧑‍🏫 **Wskazówka dla prowadzącego:** włącz **prebuildy** (repozytorium → *Settings* → *Codespaces* → *Set up prebuild*).
> Gotowy obraz środowiska jest wtedy budowany z wyprzedzeniem i studenci startują w kilkadziesiąt sekund zamiast 5–10 minut.
> Prebuildy zużywają miejsce na koncie właściciela repozytorium. Repozytorium musi być **publiczne**
> (albo studenci muszą mieć do niego dostęp), a każdy student tworzy codespace na **własnym** koncie i z własnego limitu.

---

## 💻 Praca w lokalnym VS Code połączonym z Codespaces

Wolisz pracować w zainstalowanym na komputerze VS Code? Możesz podłączyć go do codespace'a. **Obliczenia nadal dzieją się
w chmurze**, więc lokalnie nie instalujesz Pythona ani bibliotek.

1. Zainstaluj [Visual Studio Code](https://code.visualstudio.com/) i rozszerzenie
   **[GitHub Codespaces](https://marketplace.visualstudio.com/items?itemName=GitHub.codespaces)** (`GitHub.codespaces`).
2. Połącz się z codespace'em w jeden z dwóch sposobów:
   - **z przeglądarki:** w codespace otwartym w przeglądarce kliknij menu **☰** (lewy górny róg) → **Open in VS Code Desktop**;
   - **z VS Code:** naciśnij <kbd>F1</kbd> (lub <kbd>Ctrl/Cmd</kbd> + <kbd>Shift</kbd> + <kbd>P</kbd>) → **Codespaces: Connect to Codespace…**
     → zaloguj się kontem GitHub → wybierz codespace (lub **Create New Codespace** → repozytorium `ArtuDitu/ML_WDIB`).
3. Lewy dolny róg VS Code pokaże **„Codespaces: nazwa”**, co znaczy, że jesteś połączony.
4. Porty (np. **8501** aplikacji Streamlit z tygodni 11–12) są automatycznie przekierowywane: aplikacja otworzy się pod `http://localhost:8501`.

---

## 🧰 Inne sposoby uruchomienia

<details>
<summary><b>🐳 Lokalnie w kontenerze (Docker + Dev Containers)</b>, to samo środowisko co w Codespaces</summary>

1. Zainstaluj [Docker Desktop](https://www.docker.com/products/docker-desktop/) i w VS Code rozszerzenie
   **Dev Containers** (`ms-vscode-remote.remote-containers`).
2. Sklonuj repozytorium: `git clone https://github.com/ArtuDitu/ML_WDIB.git` i otwórz folder w VS Code.
3. VS Code zaproponuje **Reopen in Container** (albo <kbd>F1</kbd> → **Dev Containers: Reopen in Container**).
4. Pierwsze budowanie kontenera trwa kilka–kilkanaście minut.
</details>

<details>
<summary><b>🐍 Lokalnie bez Dockera</b> (dla zaawansowanych)</summary>

Wymagany **Python 3.10 lub 3.11**. PyCaret 3 **nie działa** na Pythonie 3.12 i nowszych!

```bash
git clone https://github.com/ArtuDitu/ML_WDIB.git
cd ML_WDIB
python3.10 -m venv .venv
source .venv/bin/activate            # Windows: .venv\Scripts\activate
python -m pip install --upgrade pip
pip install -r requirements.txt      # ok. 5–10 minut
python -m nltk.downloader stopwords wordnet omw-1.4
```

- **macOS:** biblioteka LightGBM wymaga OpenMP: `brew install libomp`.
- Potem otwórz folder w VS Code i wybierz jądro z `.venv`.
</details>

---

## 📅 Harmonogram 12 tygodni

| Tydz. | Notebook | Temat | Cel zajęć | Dane | Rozdział książki |
|:---:|---|---|---|---|---|
| 1 | [`tydzien_01_wstep_do_ml_i_pycaret`](notebooks/tydzien_01_wstep_do_ml_i_pycaret.ipynb) | Wstęp do ML i PyCaret | Zrozumieć, czym jest ML (nadzorowane vs nienadzorowane), uruchomić PyCaret i wczytać pierwszy zbiór danych | `get_data('index')`, `insurance`, `iris`, `diabetes` | 1 |
| 2 | [`tydzien_02_regresja_eda`](notebooks/tydzien_02_regresja_eda.ipynb) | Regresja: EDA | Poznać regresję liniową i przeprowadzić eksploracyjną analizę danych: histogramy, wykresy rozrzutu, korelacje | `insurance` | 2 (model liniowy, dane, EDA) |
| 3 | [`tydzien_03_regresja_pycaret_setup`](notebooks/tydzien_03_regresja_pycaret_setup.ipynb) | Regresja: `setup()` i `compare_models()` | Zrozumieć podział train/test, one-hot, normalizację, walidację krzyżową; porównać ok. 20 modeli | `insurance` | 2 (*Initializing*, *Comparing*) |
| 4 | [`tydzien_04_regresja_tuning_i_predykcja`](notebooks/tydzien_04_regresja_tuning_i_predykcja.ipynb) | Regresja: strojenie i zapis | Dostroić hiperparametry, ocenić model na zbiorze testowym, narysować błędy, zapisać i wczytać model | `insurance` | 2 (*Creating*–*Saving*) |
| 5 | [`tydzien_05_klasyfikacja_eda_i_setup`](notebooks/tydzien_05_klasyfikacja_eda_i_setup.ipynb) | Klasyfikacja: EDA i `setup()` | Poznać klasyfikację i regresję logistyczną, sprawdzić balans klas, przygotować dane (kodowanie etykiet) | `iris` | 3 (wstęp, dane, EDA, *Initializing*) |
| 6 | [`tydzien_06_klasyfikacja_macierz_bledow_i_granice`](notebooks/tydzien_06_klasyfikacja_macierz_bledow_i_granice.ipynb) | Klasyfikacja: ocena modeli | Porównać klasyfikatory, czytać macierz pomyłek i granice decyzyjne, rozpoznać gatunek nowego kwiatu | `iris` | 3 (*Comparing*–*Saving*) |
| 7 | [`tydzien_07_grupowanie_clustering`](notebooks/tydzien_07_grupowanie_clustering.ipynb) | Grupowanie (K-Means) | Zrozumieć uczenie nienadzorowane, dobrać liczbę grup metodą łokcia, ocenić sylwetkę, zwizualizować PCA | syntetyczne (`make_blobs`) | 4 |
| 8 | [`tydzien_08_detekcja_anomalii`](notebooks/tydzien_08_detekcja_anomalii.ipynb) | Wykrywanie anomalii | Wykryć nietypowych klientów modelem LOF (i Isolation Forest), ocenić efekt, zwizualizować UMAP | `wholesale` | 5 |
| 9 | [`tydzien_09_przetwarzanie_jezyka_naturalnego_nlp`](notebooks/tydzien_09_przetwarzanie_jezyka_naturalnego_nlp.ipynb) | NLP: chmury słów i tematy | Zamienić tekst na liczby (worek słów), narysować chmurę słów, wykryć tematy metodą LDA, sklasyfikować artykuły | `data/bbc-text.csv` | 6 |
| 10 | [`tydzien_10_szeregi_czasowe_forecasting`](notebooks/tydzien_10_szeregi_czasowe_forecasting.ipynb) | Szeregi czasowe | Rozłożyć szereg na trend i sezonowość, przetestować stacjonarność, prognozować CO₂ na 3 lata | `data/mauna_loa_co2.csv` | 7 |
| 11 | [`tydzien_11_aplikacja_streamlit_cz1`](notebooks/tydzien_11_aplikacja_streamlit_cz1.ipynb) | Streamlit cz. 1: formularz | Napisać i uruchomić aplikację Streamlit, zbudować formularz z widżetami dla danych ubezpieczeniowych | – | 8 (wstęp, Streamlit, *Insurance App*) |
| 12 | [`tydzien_12_wdrazanie_modelu_deployment`](notebooks/tydzien_12_wdrazanie_modelu_deployment.ipynb) | Wdrożenie modelu | Podłączyć zapisany model do aplikacji, przetestować ją automatycznie, opublikować w Streamlit Community Cloud; podsumować kurs | model z tygodnia 4 | 8 (*Developing*–*Deploying*), 9 |

---

## 🧩 Jak zbudowany jest każdy notebook

Każdy notebook ma tę samą, powtarzalną strukturę, żeby studenci wiedzieli, czego się spodziewać:

1. **🎯 Cel zajęć i plan 90 minut**: co będziemy umieć po zajęciach i ile czasu na co przeznaczamy.
2. **📚 Część 1: wprowadzenie teoretyczne** (Markdown, po polsku): proste analogie z życia codziennego zamiast trudnej matematyki,
   a kluczowe pojęcia podane dwujęzycznie, np. *podział na zbiór treningowy i testowy / train-test split*.
3. **👣 Część 2: krok po kroku**: bardzo małe komórki z kodem (zwykle 1–3 linie) ze szczegółowymi komentarzami po polsku
   i krótkim komentarzem „🔎 Co widzimy?” po ważniejszych wynikach.
4. **🧑‍💻 Część 3: ćwiczenie podstawowe** na zajęcia (proste) – ✅ **obowiązkowe: na jego podstawie zaliczasz zajęcia**
   (zaliczone / niezaliczone). Zawiera polecenie, ukrytą **podpowiedź** (rozwijaną), pustą komórkę na własny kod
   i komórkę **„✍️ Twoje odpowiedzi”** na odpowiedzi do pytań i wnioski.
5. **🏋️ Część 4: ćwiczenia dodatkowe – trochę trudniejsze** (po 2 w każdym notebooku: ⭐⭐ średnie i ⭐⭐⭐ wyzwanie),
   **nieobowiązkowe** – dla szybszych osób albo do domu. Łączą kilka poznanych narzędzi i czasem wprowadzają jedną nową
   funkcję (opisaną w podpowiedzi). Każde ma podpowiedź i miejsce na Twój kod i odpowiedzi.
6. **📝 Podsumowanie** i **📖 słowniczek PL / EN** najważniejszych pojęć.

Notebooki są zapisane **bez wyników** (studenci uruchamiają je samodzielnie). Wszystkie zostały przetestowane:
uruchamiają się w całości bez błędów w środowisku z `requirements.txt`. Na komputerze testowym każdy notebook liczy się
w całości w mniej niż minutę. Na 2-rdzeniowej maszynie Codespaces trzeba liczyć się z kilkukrotnie dłuższym czasem
(najdłużej trwają `compare_models()` i `tune_model()`).

---

## 📁 Struktura repozytorium

```
ML_WDIB/
├── .devcontainer/
│   └── devcontainer.json        # konfiguracja Codespaces / Dev Containers (Python 3.10 + biblioteki)
├── data/
│   ├── README.md                # opis i źródła danych
│   ├── bbc-text.csv             # artykuły BBC News (tydzień 9)
│   └── mauna_loa_co2.csv        # stężenie CO₂ Mauna Loa (tydzień 10)
├── notebooks/                   # 12 notebooków – po jednym na tydzień
│   ├── tydzien_01_wstep_do_ml_i_pycaret.ipynb
│   ├── …
│   └── tydzien_12_wdrazanie_modelu_deployment.ipynb
├── requirements.txt             # lista bibliotek z przypiętymi wersjami
├── modele/                      # (powstaje w trakcie kursu) zapisane modele .pkl – ignorowany przez git
└── aplikacja/                   # (powstaje w tygodniach 11–12) aplikacja Streamlit: app.py, model, requirements.txt
```

Notebooki uruchamiają się w folderze `notebooks/`, dlatego odwołują się do danych i modeli ścieżkami względnymi
`../data/…`, `../modele/…`, `../aplikacja/…`.

---

## 🔀 Różnice względem książki (PyCaret 3.0 → 3.3.2)

Książka powstała dla PyCaret 3.0 (rozdział NLP: PyCaret 2). W kursie używamy nowszych wersji bibliotek, dlatego
część kodu została dostosowana. Każda zmiana jest też wyjaśniona w odpowiednim notebooku.

| W książce | W kursie | Powód |
|---|---|---|
| moduł `pycaret.nlp` (rozdz. 6) | `CountVectorizer` + `LatentDirichletAllocation` ze scikit-learn, potem klasyfikacja w PyCaret | moduł NLP został usunięty z PyCaret 3 |
| `@st.cache(allow_output_mutation=True)` | `@st.cache_resource` | `st.cache` usunięto z nowych wersji Streamlit |
| `data.corr()` na tabeli z kolumnami tekstowymi | `data.corr(numeric_only=True)` lub `data[numeric].corr()` | pandas 2 zgłasza błąd dla kolumn nieliczbowych |
| `plt.style.use('seaborn-whitegrid')` | pominięte | nazwa stylu zmieniona w Matplotlib ≥ 3.6 |
| siatka strojenia z `'subsample': 1.1` | wartości ≤ 1.0 | scikit-learn nie pozwala na `subsample > 1` |
| strojenie: `n_iter=100` (regresja), CatBoost + scikit-optimize `n_iter=50` (klasyfikacja) | `n_iter=15` (GBR), drzewo decyzyjne `n_iter=20` | czas obliczeń na 2-rdzeniowej maszynie Codespaces |
| `compare_models()` dla szeregów czasowych na wszystkich ok. 30 modelach | wybrane 7 modeli (`include=[…]`) | czas obliczeń (sam Auto ARIMA liczy się ok. 40 s) |
| spaCy `STOP_WORDS` | `wordcloud.STOPWORDS` + własne słowa, stopwords z NLTK | jedna biblioteka mniej do instalacji |
| model zapisany w folderze notebooka | modele w `modele/`, aplikacja w `aplikacja/` | porządek w repozytorium, łatwe wdrożenie |
| Streamlit Cloud: domyślny Python | wybór **Python 3.10/3.11** w *Advanced settings* | PyCaret 3 nie działa na Pythonie 3.12+ |

**Znane ograniczenia PyCaret 3.3.2** (opisane w notebookach):
- przy klasyfikacji **wieloklasowej** część modeli pokazuje w tabelach **AUC = 0.0000**. To błąd biblioteki, a nie modelu,
  dlatego oceniamy modele dokładnością (*Accuracy*);
- `predict_model()` dla **grupowania** na nowych danych zgłasza błąd typu danych, więc w tygodniu 7 używamy `assign_model()` (tak jak w książce);
- w `requirements.txt` przypięto `dask==2024.12.1`, bo nowsze wersje psują moduł szeregów czasowych (sktime 0.26).

---

## 🔧 Rozwiązywanie problemów (FAQ)

| Problem | Rozwiązanie |
|---|---|
| VS Code prosi o instalację Pythona | **Nie instaluj** – zobacz sekcję [Czy muszę instalować Pythona?](#-czy-muszę-instalować-pythona-nie) |
| `ModuleNotFoundError: No module named 'pycaret'` | Wybrano złe jądro. Kliknij **Select Kernel** → **Python 3.10** (`/usr/local/bin/python`). Jeśli nie pomaga – sprawdź wersję Pythona w terminalu (sekcja wyżej). |
| `streamlit: command not found` | Uruchom przez Pythona: `python -m streamlit run aplikacja/app.py` (albo przebuduj codespace: <kbd>F1</kbd> → **Codespaces: Rebuild Container**). |
| Instalacja w Codespaces trwa bardzo długo | Pierwsze budowanie trwa 5–10 min (PyCaret ma dużo zależności). Postęp: <kbd>F1</kbd> → **Codespaces: View Creation Log**. |
| Biblioteki się nie zainstalowały / instalacja przerwana | W terminalu: `pip install --user -r requirements.txt`, a następnie **Restart** jądra notebooka. |
| `FileNotFoundError: ../data/…` | Notebook musi działać w folderze `notebooks/` (ustawienie `jupyter.notebookFileRoot` jest już w konfiguracji). Nie przenoś notebooków do innych folderów. |
| `get_data()` zgłasza błąd połączenia | `get_data()` pobiera dane z internetu. Sprawdź połączenie i uruchom komórkę ponownie. |
| Komórka działa bardzo długo / jądro „umarło” | Zamknij inne notebooki, kliknij **Restart** i uruchom komórki od początku. Strojenie (`tune_model`) można przyspieszyć, zmniejszając `n_iter`. |
| W tygodniu 12 brakuje pliku `regression_model.pkl` | Notebook ma komórkę „🆘 plan awaryjny”, która sama wytrenuje i zapisze model. |
| `app.py` ma zdublowany kod | Uruchom ponownie komórkę z `%%writefile` (bez `-a`), a potem kolejne komórki `%%writefile -a` **po jednym razie**. |
| Aplikacja Streamlit nie otwiera się w Codespaces | Zakładka **PORTS** → port **8501** → ikona 🌐. Jeśli strona „kręci się” w nieskończoność, uruchom: `streamlit run aplikacja/app.py --server.enableCORS false --server.enableXsrfProtection false`. |
| `Address already in use` przy `streamlit run` | Poprzednia aplikacja nadal działa. Zatrzymaj ją <kbd>Ctrl</kbd> + <kbd>C</kbd> w jej terminalu albo zamknij ten terminal (ikona 🗑️). |
| Czerwone komunikaty `WARNING` / `missing ScriptRunContext` | To ostrzeżenia, nie błędy. Można je zignorować. |

---

## 📚 Źródła i licencje

- **Książka:** Giannis Tolios, *Simplifying Machine Learning with PyCaret: A Low-code Approach for Beginners and Experts!*, Leanpub, 2023, https://leanpub.com/pycaretbook
- **Kod źródłowy książki:** https://github.com/derevirn/pycaret-book
- **Dokumentacja:** [PyCaret](https://pycaret.readthedocs.io) · [Streamlit](https://docs.streamlit.io) · [scikit-learn](https://scikit-learn.org)
- **Dane:** opis i źródła w [`data/README.md`](data/README.md). Zbiory danych podlegają licencjom ich autorów (do celów edukacyjnych).
- **Materiały kursu** (notebooki, konfiguracja): licencja MIT, patrz [`LICENSE`](LICENSE).
