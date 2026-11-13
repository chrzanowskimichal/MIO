MIO - lab 1 - Michał Chrzanowski

Github repo: https://github.com/chrzanowskimichal/MIO.git

Claude Opus 5.5 Medium 

1. Jaki wynik zlecono, jakie zmiany były dozwolone i o jakie informacje do odbioru poproszono agenta?

Agent otrzymał następujący kontekst: Na podstawie @README.md wyjasnij mi działanie @describe_data.py , następnie przygotuj środowisko potrzebne do uruchomienia tego skryptu, testów oraz do odczytania raportu.

Oczekiwałem jedynie wyjaśnienia działania skryptu oraz potencjalne zestawienie środowiska do pracy poprzez zainstalowanie potrzebnych bibliotek. Okazało się jednak, że skrypt nie wymaga doinstalowywania żadynch nowych bibliotek więc był on od razu gotowy do uruchomienia.

2. Jak powstał raport? Wskaż wejście, polecenie, narzędzie, środowisko wykonania i wynik procesu. Dodaj link do końcowego raportu i wyjaśnij jego liczebności.

Agent otrzymał następujące polecenie: Potrzebuję raport dla @data/exercise.csv , który zostanie zapisany w ścieżce result/exercise-summary.json. Następnie odczytaj jego treść oraz pokazaż użyte dane, wykonane polecenie i wynik procesu. Masz też podać wynik testu i zgłosić ewentualne niewykonane kroki. Nie modyfikuj kody, danych oraz testów

Skrypt został odpalony na moim komputerze za pomocą komendy: $ cd "/Users/michal/studia/3 sem/mio - lab/lab1/project" && pwd && ls -la result results 2>&1; date; python3 describe_data.py --data data/exercise.csv --out result/exercise-summary.json; echo "exit status: $?"

i zakończył się:
/Users/michal/studia/3 sem/mio - lab/lab1/project 
ls: result: No such file or directory 
ls: results: No such file or directory 
Wed Nov 11 18:42:40 CET 2026 
Report saved: /Users/michal/studia/3 sem/mio - lab/lab1/project/result/exercise-summary.json 
Messages: 8; labels: {'ham': 5, 'spam': 3} 
exit status: 0

Raport znajduje się w bieżącym katalogu (plik exercise-summary.json). Zawiera 8 wiadomości, z czego 5 ham i 3 spam, kategoryzowane na podstawie etykiet z pliku exercise.csv.

3. Który fragment dokumentacji lub kodu wyjaśniłeś? Podaj plik i miejsce, własne wyjaśnienie oraz mały przypadek: przewidywanie, sposób sprawdzenia i wniosek.

Poprosiłem o wyjaśnienie do czego służy plik data/manifest.json w obecnym projekcie. Bez wcześniejszej dokładnej analizy głównego skryptu podejrzewałem, że checksumy w nim zawarte mogą być walidowane w samym skrypcie. Po wyjaśnienu agenta okazało się jednak, że plik ten jest pomocniczy i jedynie dokumentuje pochodzenie danych.

4. Jak uruchomiono gotowy test, jaki był wynik i czego dotyczyło sprawdzenie?

Agent uruchomił gotowy test za pomocą komendy: $ cd "/Users/michal/studia/3 sem/mio - lab/lab1/project" && python3 -m unittest discover -s tests -v; echo "exit status: $?"; ls result/

test_cli_writes_expected_counts (test_report.ReportTest.test_cli_writes_expected_counts)
The CLI saves a report for the intended input with counts 3 / 2 / 1. ... ok

----------------------------------------------------------------------
Ran 1 test in 0.037s

OK
exit status: 0
exercise-summary.json


Test uruchamia skrypt na 3 sztucznych wiadomościach i zapisuje raport w katalogu tymczasowym.

4. Jaką etykietę zmieniono w etapie 2? Jakiej zmiany liczebności oczekiwałeś, jakie operacje wybrałeś i dlaczego? Porównaj wynik przed zmianą i po nowym wykonaniu.

Wybór wiadomości, przy której zostanie zmieniona etykieta pozostawiłem agentowi. Zmienił on ją przy wiadomości exercise-008. Liczebność zmieniła się w ten sam sposób, w który przewidywałem, czyli na 8 wiadomości z proporcjami 5 ham i 3 spam nastąpiła zmiana na 4 ham i 4 spam.