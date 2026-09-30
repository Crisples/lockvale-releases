# Lockvale

**Lockvale** to przenośny, szyfrowany sejf haseł dla Windows - jeden plik `Lockvale.exe`, bez instalacji.
Można go nosić na pendrivie razem z plikiem sejfu.

> Wcześniej program nazywał się **pCrypt**. Wersja pCrypt 1.1.0 aktualizuje się do Lockvale automatycznie,
> a pliki `pcrypt.vault` i `pcrypt.ini` są odczytywane bez zmian.

![Lockvale](screenshots/3-szczegoly.png)

## Pobierz

**[⬇ Pobierz najnowszą wersję Lockvale.exe](https://github.com/Crisples/lockvale-releases/releases/latest/download/Lockvale.exe)**
· [wszystkie wydania](https://github.com/Crisples/lockvale-releases/releases)

Wymagania: Windows 10 lub 11 (.NET Framework 4.8 jest wbudowany w system).

> Przy pierwszym uruchomieniu pliku pobranego przeglądarką Windows SmartScreen może pokazać ostrzeżenie
> „Nieznany wydawca”. Wybierz wtedy **Więcej informacji → Uruchom mimo to** albo we Właściwościach pliku
> zaznacz **Odblokuj**. Kolejne wersje instalują się już same, bez tego ostrzeżenia.

## Najważniejsze funkcje

- Szyfrowanie **AES-256** + **HMAC-SHA256**, klucz z hasła głównego przez **PBKDF2-SHA256** (600 000 iteracji).
- Dane tylko lokalnie, w jednym pliku `.vault` - bez chmury i bez kont.
- Generator haseł, wyszukiwarka, historia poprzedniego hasła dla każdego wpisu.
- Kopiowanie do schowka z automatycznym czyszczeniem po 30 s (bez historii schowka Windows).
- Automatyczna blokada po 5 minutach bezczynności i przy zablokowaniu Windows.
- Automatyczne aktualizacje z podpisem cyfrowym - Lockvale instaluje tylko pliki podpisane przez autora.

## Pierwsze kroki

1. Wrzuć `Lockvale.exe` do folderu, w którym ma leżeć sejf (np. na pendrive).
2. Uruchom i ustaw **hasło główne** (min. 12 znaków). **Nie da się go odzyskać** - zapamiętaj je.
3. Rób kopie zapasowe pliku `lockvale.vault` (poprzednia wersja po każdym zapisie trafia też do `lockvale.vault.bak`).

Ustawienia są w pliku `lockvale.ini` obok programu. `aktualizacje=0` wyłącza sprawdzanie nowych wersji.

## Aktualizacje i ich weryfikacja

Przy starcie Lockvale sprawdza najnowsze wydanie w tym repozytorium i pyta o instalację. Każde wydanie zawiera
`Lockvale.update` - manifest z numerem wersji i skrótem SHA-256 pliku, podpisany kluczem ECDSA P-256 autora.
Aplikacja odrzuci plik z błędnym podpisem, innym skrótem albo starszą wersją.

Skrót pobranego pliku sprawdzisz ręcznie w PowerShellu i porównasz z linią `sha256=` w `Lockvale.update`:

```powershell
(Get-FileHash .\Lockvale.exe -Algorithm SHA256).Hash.ToLower()
```

## Licencja

Lockvale jest darmowy (freeware) do użytku prywatnego i firmowego. Szczegóły: [LICENSE.txt](LICENSE.txt).
Copyright © 2026 by Michał Surdyka.

Program zawiera czcionki Nunito i DM Mono na licencji SIL Open Font License 1.1.

## Zgłoszenia

Błędy i pomysły: [Issues](https://github.com/Crisples/lockvale-releases/issues).
