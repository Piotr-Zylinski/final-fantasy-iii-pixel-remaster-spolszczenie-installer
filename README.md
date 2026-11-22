> **Language Note / Uwaga językowa:** This document contains the exact same documentation in two languages: **English** (below) and **Polish** (further down). / Ten dokument zawiera dokładnie tę samą dokumentację w dwóch językach: **angielskim** (poniżej) oraz **polskim** (niżej).

---

# [ENGLISH VERSION] FINAL FANTASY III Pixel Remaster - Polish Translation Installer (Inno Setup)

Source script for the automated installer of the Polish localization (`Spolszczenie PL`) for **FINAL FANTASY III Pixel Remaster** (Steam, AppID 1173790). Built with **Inno Setup 7** (7.1.1).

## What the installer does
1. Automatically detects the game folder via the Windows Registry (Steam uninstall key, 64- and 32-bit view), the Steam library list (`libraryfolders.vdf`) or by scanning drives C:–Z:.
2. Always shows the folder selection page with a **Browse...** button and a **Skanuj dyski** (scan drives) button; it refuses to continue if the chosen folder does not contain `FINAL FANTASY III.exe` and `FINAL FANTASY III_Data\StreamingAssets\aa\catalog.json`.
3. If `.bak` files already exist (translation installed before), it asks whether to install again.
4. Creates `.bak` backups of the 10 original files (if they do not exist yet): `aa\catalog.json`, `aa\StandaloneWindows64\message_assets_all_07fb59bf9938266640c0a811664e1596.bundle`, `aa\StandaloneWindows64\miss_sprite_assets_all_bfad4e62c8010fe65066042f5e85ad90.bundle` (battle "MISS" graphic), `aa\StandaloneWindows64\hit_sprite_assets_all_6380dd1917bb4b39bda7a83852ce0447.bundle` (battle hit counter graphic) and `font_de/en/es/fr/it/pt.bundle` (all inside `FINAL FANTASY III_Data\StreamingAssets`).
5. Copies the modified files: the text bundle (Polish text replacing the English text assets), the battle graphics ("PUDŁO" instead of "MISS", "TRAF." / "TRAF!" instead of "HIT" / "HITS"), the matching `catalog.json` (CRC check disabled for these bundles), and the game fonts with added Polish characters (ą ć ę ł ń ś ź ż).
6. Places a hidden uninstaller in `_spolszczenie_deinstalator`, creates a `Usunięcie spolszczenia` (*Remove Polish Translation*) shortcut in the game folder and an "Add or remove programs" entry. The installer stores SHA-256 checksums of the installed files. Uninstalling restores the original files from `.bak` only if the game file is still the translated one; if Steam has updated the file in the meantime, the outdated backup is removed and the uninstaller recommends **Verify integrity of game files** in Steam. The uninstaller never deletes game files on its own.

The translation replaces the English language (the game's default). Other languages stay untouched; no game executables or DLLs are modified.

## How to build the executable
1. Install [Inno Setup 7](https://jrsoftware.org/isdl.php) (tested with 7.1.1, Windows). The Polish language file `Polish.isl` is included with Inno Setup.
2. Download the manual release of the mod and place the files next to the script like this (a `pliki` folder):
   - `pliki\catalog.json`
   - `pliki\StandaloneWindows64\message_assets_all_07fb59bf9938266640c0a811664e1596.bundle`
   - `pliki\StandaloneWindows64\miss_sprite_assets_all_bfad4e62c8010fe65066042f5e85ad90.bundle`
   - `pliki\StandaloneWindows64\hit_sprite_assets_all_6380dd1917bb4b39bda7a83852ce0447.bundle`
   - `pliki\font_de.bundle`, `font_en.bundle`, `font_es.bundle`, `font_fr.bundle`, `font_it.bundle`, `font_pt.bundle`
3. Open `FF3PR_Instalator.iss` in **Inno Setup Compiler** and choose **Build -> Compile** (Ctrl+F9), or run from the script folder:
   `"C:\Program Files\Inno Setup 7\ISCC.exe" FF3PR_Instalator.iss`
4. The result is `output\FF3PR_Spolszczenie_Instalator_v1.0.exe`.

The game data files are not stored in this repository (they derive from the game's own files); only the installer source is public.

## Changelog
- **v1.0** - initial release, replacing English with Polish.

---

# [POLISH VERSION / WERSJA POLSKA] FINAL FANTASY III Pixel Remaster - Instalator Spolszczenia (Inno Setup)

*(To jest dokładne tłumaczenie powyższej dokumentacji angielskiej na język polski / Exact Polish translation of the English documentation above.)*

Skrypt źródłowy automatycznego instalatora polskiej wersji językowej (`Spolszczenie PL`) do gry **FINAL FANTASY III Pixel Remaster** (Steam, AppID 1173790). Zbudowany w **Inno Setup 7** (7.1.1).

## Co robi instalator
1. Automatycznie wykrywa folder gry w rejestrze Windows (wpis Steam, widok 64- i 32-bitowy), na liście bibliotek Steam (`libraryfolders.vdf`) lub przez skanowanie dysków C:–Z:.
2. Zawsze pokazuje ekran wyboru folderu z przyciskiem **Przeglądaj...** oraz **Skanuj dyski**; nie pozwala przejść dalej, jeśli w wybranym folderze nie ma `FINAL FANTASY III.exe` i `FINAL FANTASY III_Data\StreamingAssets\aa\catalog.json`.
3. Jeśli pliki `.bak` już istnieją (spolszczenie było instalowane), pyta, czy zainstalować ponownie.
4. Tworzy kopie zapasowe `.bak` 10 oryginalnych plików (jeśli jeszcze nie istnieją): `aa\catalog.json`, `aa\StandaloneWindows64\message_assets_all_07fb59bf9938266640c0a811664e1596.bundle`, `aa\StandaloneWindows64\miss_sprite_assets_all_bfad4e62c8010fe65066042f5e85ad90.bundle` (grafika „MISS” w walce), `aa\StandaloneWindows64\hit_sprite_assets_all_6380dd1917bb4b39bda7a83852ce0447.bundle` (grafika licznika trafień) oraz `font_de/en/es/fr/it/pt.bundle` (wszystkie w `FINAL FANTASY III_Data\StreamingAssets`).
5. Kopiuje zmodyfikowane pliki: paczkę tekstową (polski tekst w miejscu angielskiego), grafiki walki („PUDŁO” zamiast „MISS”, „TRAF.” / „TRAF!” zamiast „HIT” / „HITS”), pasujący `catalog.json` (wyłączona kontrola CRC tych paczek) oraz czcionki gry z dodanymi polskimi znakami (ą ć ę ł ń ś ź ż).
6. Umieszcza ukryty deinstalator w `_spolszczenie_deinstalator`, tworzy w folderze gry skrót `Usunięcie spolszczenia` oraz wpis w „Dodaj lub usuń programy”. Instalator zapisuje sumy kontrolne SHA-256 zainstalowanych plików. Odinstalowanie przywraca oryginały z `.bak` tylko wtedy, gdy plik gry jest nadal plikiem spolszczenia; jeśli Steam w międzyczasie zaktualizował plik, nieaktualna kopia jest usuwana, a deinstalator zaleca **Sprawdź integralność plików gry** w Steam. Deinstalator nigdy sam nie usuwa plików gry.

Spolszczenie zastępuje język angielski (domyślny język gry). Pozostałe języki zostają bez zmian; pliki wykonywalne i biblioteki DLL gry nie są modyfikowane.

## Jak skompilować plik wykonywalny (.exe)
1. Zainstaluj [Inno Setup 7](https://jrsoftware.org/isdl.php) (sprawdzone na 7.1.1, Windows). Plik języka polskiego `Polish.isl` jest dołączony do Inno Setup.
2. Pobierz paczkę manualną moda i umieść pliki obok skryptu w folderze `pliki`:
   - `pliki\catalog.json`
   - `pliki\StandaloneWindows64\message_assets_all_07fb59bf9938266640c0a811664e1596.bundle`
   - `pliki\StandaloneWindows64\miss_sprite_assets_all_bfad4e62c8010fe65066042f5e85ad90.bundle`
   - `pliki\StandaloneWindows64\hit_sprite_assets_all_6380dd1917bb4b39bda7a83852ce0447.bundle`
   - `pliki\font_de.bundle`, `font_en.bundle`, `font_es.bundle`, `font_fr.bundle`, `font_it.bundle`, `font_pt.bundle`
3. Otwórz `FF3PR_Instalator.iss` w **Inno Setup Compiler** i wybierz **Build -> Compile** (Ctrl+F9) albo uruchom w folderze skryptu:
   `"C:\Program Files\Inno Setup 7\ISCC.exe" FF3PR_Instalator.iss`
4. Wynik: `output\FF3PR_Spolszczenie_Instalator_v1.0.exe`.

Pliki danych gry nie są częścią repozytorium (pochodzą z plików gry); publiczny jest tylko kod źródłowy instalatora.

## Historia zmian
- **v1.0** - pierwsze wydanie, zmieniające język angielski na polski.
