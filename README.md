# Hands on day!

Dziś to Wy pokażecie na co Was stać. Poniżej znajdują się instrukcje potrzebne do zrealizowania zadań zaplanowanych na dzisiejszy dzień.

Generalnie pytajcie śmiało jeśli utkniecie, ale zróbcie to poprzez **wiadomość na slacku**. Jak wiecie w nauce i poznawaniu nowych technologii nic nie pomaga tak jak 2h spędzone na debugowaniu dziwnego problemu, bo przecież powinno działać, prawda?

---

## Zadanie 1

Aby zadanie pierwsze zostało zaliczone należy:

- zainstalować Ansibla ;)
- napisać playbook, który:

1. Wypisze na terminal najważniejsze informacje o waszej maszynie - ilość pamięci, RAMu, coreów, OS itd
1. Zainastaluje dockera
1. Sprawi, że daemon dockera będzie uruchamiany automatycznie przy każdym reboocie maszyny
1. Użytkownik, kórego używacie będzie mógł używać komendy `docker` bez używania `sudo`
1. Stworzy 3 kontenery dockera - nazwy kontenerów powinny być konfigurowalne poprzez zmienne roli - więcej informacji poniżej
1. Pobierze o kontenerach użyteczne informacje
1. Stworzy plik `zadanie-2-inventory.ini` lub `zadanie-2-inventory.yaml`, który ma byc prawidłowym, gotowym plikiem inventory dla zadania 2

- kontenery powinny używać obrazów ubuntu oraz centos (ilość poszczególnych obrazów dowolna) - pogrupujcie je odpowiednio (przeczytajcie zadanie 2 w celu lepszej identyfikacji inventory groups)
- używajcie modułów ansibla np. do kopiowania plików słuzy moduł `copy`, a nie `shell: cp ./foo ./bar/boo/foo` ;)
- wasza maszyna to ansible-host, z niej będziecie odpalać wszystkie komendy ansibla
- aby przejść do zadania 2 nalezy na slacku podesłać nastepujące materiały weryfkacyjne:

1. Wynik komendy ansible-lint, która potwierdzi, że wszystko jest w porządku z kodem
1. Screen kodu - w jaki sposób logicznie pogrupujecie taski, może będzie więcej niż jeden plik z taskami, może jakieś `block`
1. Screen podsumowania wykonania się playbooka
1. Screen zawartości powstałego pliku (dla chętnych: skorzystajcie z katalogu `templates` do stworzenia pliku `inventory.j2`, który będzie dynamicznie wypełniany informacjami --- szukajcie pod `ansible jinja templates`)
1. Screen z komendy `tree`

## Zadanie 2

Zadanie drugie polega na skonfigurowaniu kontenerów stworzonych w zadaniu 1.

1. Wasza maszyna to ansible host, a kontenery to workery
1. Stwórzcie odpowiednie `host varsy` oraz `group varsy`
1. Na jednym z kontenerów ma działać apache server
1. Na jednym z kontenerów ma działać nginx server
1. Na jednym z kontenerów mają być zainstalowane paczki potrzebne do pracy z python3 i wirtualnymi środowiskami pythona
1. Playbook, który napiszecie powinien rozróżniać systemy operacyjne np. instalacja paczki `foo` będzie się odbywać inaczej na ubuntu i centos

Walidacja tożsama z tą z zadania 1, a dodatkowo:

1. Screen zawartości host varsów i group varsów
1. Screen wyniku komend `curl` (web servery mają swoją domyślną stronę) oraz `python --version`

Dla chętnych:

- dodajcie w kataogu `templates` templejty stron internetowych dla nginx oraz apache
- w host varsach dodajcie sekcje, która pozwoli na personalizację templateu
- wasza powitalna, domyślna strona powinna zostać umieszczona przez playbook w odpowiednim miejscu
- na kontenerze z pythonem umieście plik z katalogu `files`, który będzie zawierał apkę `hello world` napisaną np. we flasku (doksy mają ready-to-use przykład)
- uruchomcie apkę
- walidacja tak jak dla typowego zadania 2, tylko bez `python --version` raczej pokażcie, że hello world działa :)
