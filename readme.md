### Instalacja MicroPython na ESP32-S2 Mini

- Na początku instalujemy Thonny IDE [Thonny IDE](https://github.com/thonny/thonny/releases)
- W dodatku musimy zainstalować sterowniki do obsługi esp32 wchodzimy na strone [Silicon Labs](https://www.silabs.com/developer-tools/usb-to-uart-bridge-vcp-drivers?tab=downloads)
- Wybieramy `CP210x Windows Drivers`
  ![](https://github.com/TomaszRainski/esp32s2/blob/main/ss/drivers.png)
- Wypakujemy pliki i uruchamiamy `CP210xVCPInstaller_x64`
- Po instalacji otwieramy program, przechodzimy do zakładki "Narzędzia" i wybieramy opcję "Zarządzaj wtyczkami"
- Wyszukujemy `esptool`  
  ![](https://github.com/TomaszRainski/esp32s2/blob/main/ss/esptool.PNG)
- Klikamy w pierwszą pozycję na liście wyszukiwania i instalujemy `esptool`. Tak wygląda gotowy `esptool`:  
  ![](https://github.com/TomaszRainski/esp32s2/blob/main/ss/instal.PNG)
- Zamykamy okno instalacji, przechodzimy do zakładki "Uruchom" i wybieramy opcję "Skonfiguruj interpreter" (pierwsza opcja)  
  ![](https://github.com/TomaszRainski/esp32s2/blob/main/ss/interpeter.PNG)
- W opcji "Którego interpretera ma używać Thonny do uruchomienia twojego kodu?" wybieramy `MicroPython (ESP32)`
- Port do WebREPL na razie zostawiamy jako `spróbuj wykryć port automatycznie`
- Teraz klikamy "Zainstaluj lub zaktualizuj MicroPython (esptool)"  
  ![](https://github.com/TomaszRainski/esp32s2/blob/main/ss/interpeter2.PNG)
- Przytrzymujemy przycisk `0` i `RST`, a następnie podłączamy ESP do komputera
- ESP32-S2 przejdzie w tryb pobierania
- W oknie "Target Port" wybieramy port, do którego ESP jest podłączone
- W "MicroPython family" wybieramy `ESP32-S2`
- W "Variant" wybieramy `Wemos S2 mini`
- Teraz nasze okno powinno wyglądać tak:  
  ![](https://github.com/TomaszRainski/esp32s2/blob/main/ss/pobieranie.png)
- Klikamy w wolną przestrzeń obok przycisku "Install", co pozwoli nam zobaczyć logi `esptool`
- Klikamy "Install" i czekamy na zakończenie procesu

## UWAGA
- W modelu ESP32-S2 program za każdym razem może wyrzucić błąd:
  ```
  Leaving...
  Error: ESP32-S2FNR2 (revision v0.0) chip was placed into download mode using GPIO0.
  esptool.py can not exit the download mode over USB. To run the app, reset the chip manually.
  To suppress this note, set --after option to 'no_reset'.
  Command returned with error code 1
  ```
- Nie jest to problem, jednak trzeba pamiętać o tym podczas instalacji
- Należy kliknąć przycisk `RST` na ESP i zamknąć okno instalacyjne  
  ![](https://github.com/TomaszRainski/esp32s2/blob/main/ss/po%20instalacji.png)
- Wrócimy w ten sposób do poprzedniego okna – tutaj wybieramy port do WebREPL i ustawiamy go na ESP32
- Klikamy "OK" – jeśli wszystko zostało wykonane poprawnie, powinniśmy zobaczyć okno "Powłoka"
- Dla testu wpisujemy:
  ```python
  print("Tu ESP32")
  ```
  ![](https://github.com/TomaszRainski/esp32s2/blob/main/ss/print.png)
- Jeśli otrzymaliśmy odpowiedź, MicroPython został poprawnie zainstalowany na ESP32-S2

### Zapisywanie kodu w Thonny IDE

- Aby zapisać plik, wybieramy `Plik` → `Zapisz jako...`
- Możemy zapisać plik lokalnie (`Ten komputer`) lub bezpośrednio na ESP32-S2 (`MicroPython device`)
- Zaleca się zapisywanie głównego pliku jako `main.py`, aby uruchamiał się automatycznie po restarcie
- Do odczytu plików z ESP32-S2 można używać eksploratora plików w Thonny (`Plik` → `Otwórz` → `MicroPython device`)
### Dodawanie bibliotek w Thonny IDE

- Aby dodać bibliotekę, otwieramy `Narzędzia` → `Zarządzaj pakietami...`
- Wyszukujemy potrzebną bibliotekę i klikamy `Zainstaluj`
- Biblioteki instalowane są na komputerze, ale jeśli chcemy dodać je do ESP32-S2, musimy skopiować je na urządzenie
- Można to zrobić ręcznie, kopiując pliki `.py` do urządzenia
  
### Przykład Programu wykonanego z uzyciem esp32 i micropythonem
 ![](https://github.com/TomaszRainski/esp32s2/blob/main/ss/wifi.gif)
