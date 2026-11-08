# ESPHome OpenTherm PL

### Otwarty regulator kotła CO oparty na ESPHome, OpenTherm i Home Assistant

**Projekt społecznościowy | Polska dokumentacja | DIY | Open Source**

## 1. O projekcie

ESPHome OpenTherm PL to projekt otwartego regulatora centralnego ogrzewania, wykorzystującego protokół OpenTherm do komunikacji z kotłem gazowym.

Celem projektu jest stworzenie niedrogiego, elastycznego i możliwego do samodzielnej rozbudowy regulatora, który daje użytkownikowi kontrolę nad sposobem sterowania ogrzewaniem.

W przeciwieństwie do tradycyjnych termostatów ON/OFF rozwiązanie wykorzystuje komunikację OpenTherm, umożliwiającą m.in. zadawanie temperatury wody grzewczej i wykorzystanie możliwości modulacji kotła.

Projekt powstał w oparciu o rzeczywistą instalację ogrzewania podłogowego i jest rozwijany oraz testowany w praktyce.

Główne założenia:
- Niski koszt wykonania.
- Wykorzystanie popularnych i łatwo dostępnych komponentów.
- Własny algorytm regulacji temperatury.
- Integracja z Home Assistant.
- Diagnostyka działania regulatora i komunikacji z kotłem.
- Możliwość dalszej rozbudowy i dostosowania do własnej instalacji.

## 2. Aktualne funkcjonalności

### Komunikacja OpenTherm
- Dwukierunkowa komunikacja z kotłem.
- Odczyt dostępnych parametrów pracy kotła.
- Zadawanie temperatury wody grzewczej.
- Wykorzystanie możliwości sterowania modulacyjnego kotła.

### Regulacja ogrzewania
- Własna logika wyznaczania zapotrzebowania na ciepło.
- Regulacja PI.
- Krzywa grzewcza zależna od temperatury zewnętrznej.
- Korekta pracy na podstawie temperatury wewnętrznej.
- Możliwość konfiguracji parametrów regulacji.
- Ograniczenia minimalnej i maksymalnej temperatury zadanej.

### Integracja z Home Assistant
- Komunikacja przez ESPHome.
- Wykorzystanie temperatury pomieszczeń udostępnianych przez Home Assistant.
- Możliwość wykorzystania średniej temperatury z wielu czujników.
- Udostępnianie parametrów pracy regulatora.
- Możliwość monitorowania zapotrzebowania na ciepło.
- Diagnostyka i wizualizacja pracy w Home Assistant.

### Diagnostyka i niezawodność

Jednym z istotnych założeń projektu jest kontrola rzeczywistej realizacji poleceń.

Regulator nie powinien zakładać, że samo wysłanie polecenia do kotła oznacza jego wykonanie.

Rozwijany mechanizm nadzoru obejmuje:
- Kontrolę realizacji żądań grzewczych.
- Weryfikację odpowiedzi kotła.
- Ponawianie poleceń w przypadku braku oczekiwanej reakcji.
- Ograniczenie liczby prób.
- Rejestrowanie stanów błędów.
- Udostępnianie informacji diagnostycznych w Home Assistant.

Docelowo mechanizm kontrolny pracuje w cyklu dwuminutowym.

## 3. Sprzęt

Aktualna wersja prototypowa wykorzystuje:

| Element | Zastosowanie |
|---|---|
| Wemos D1 mini | Mikrokontroler ESP8266 |
| DIYLESS OpenTherm Master Shield | Interfejs OpenTherm |
| Zasilacz USB 5 V | Zasilanie regulatora |
| Obudowa | Ochrona elektroniki |

### Połączenia

W aktualnej konfiguracji:
- OpenTherm IN – GPIO4.
- OpenTherm OUT – GPIO5.
- Mikrokontroler – Wemos D1 mini.
- Oprogramowanie – ESPHome.

Schemat połączeń zostanie uzupełniony w kolejnej wersji dokumentacji.

## 4. Oprogramowanie

Projekt wykorzystuje:
- ESPHome – oprogramowanie mikrokontrolera.
- Home Assistant – integracja, automatyzacja i wizualizacja.
- OpenTherm – komunikacja z kotłem.
- YAML – konfiguracja regulatora.

Kod jest rozwijany z naciskiem na czytelność, możliwość konfiguracji i łatwość dalszej rozbudowy.

## 5. Przykładowe zastosowanie

Pierwsza instalacja testowa wykorzystuje:
- Kocioł Beretta Exclusive 25R.
- Ogrzewanie podłogowe niskotemperaturowe.
- Instalację bez mieszacza.
- Czujniki temperatury zintegrowane z Home Assistant.
- Własną krzywą grzewczą i regulator PI.

Projekt nie jest ograniczony do jednej konkretnej instalacji. Możliwość wykorzystania z innymi kotłami zależy od zgodności ich implementacji OpenTherm i dostępnych funkcji protokołu.

## 6. Plany rozwoju

Projekt jest rozwijany etapami.

Planowane kierunki:
- Dalsze udoskonalanie algorytmu regulacji.
- Rozbudowa diagnostyki i mechanizmów nadzorczych.
- Uporządkowanie konfiguracji i parametrów użytkownika.
- Rozbudowa dokumentacji i schematów.
- Dedykowana płytka PCB.
- Wersja sprzętowa z ESP32.
- Wyświetlacz i lokalna obsługa przyciskami.
- Lokalny interfejs WWW.
- Możliwość pracy bez Home Assistant.
- Rozszerzenie integracji o dodatkowe funkcje OpenTherm.

## 7. Dla kogo jest ten projekt?

Projekt jest przeznaczony dla:
- Użytkowników Home Assistant.
- Entuzjastów ESPHome i elektroniki DIY.
- Osób chcących rozbudować lub zastąpić standardowy regulator kotła.
- Osób zainteresowanych własnymi algorytmami sterowania ogrzewaniem.
- Społeczności rozwijającej otwarte rozwiązania automatyki domowej.

Wymagana jest podstawowa wiedza z zakresu elektroniki, konfiguracji ESPHome i instalacji grzewczych.

## 8. Bezpieczeństwo

Projekt ma charakter hobbystyczny i rozwojowy.

Nie zastępuje fabrycznych zabezpieczeń kotła ani jego układów bezpieczeństwa.

Przed podłączeniem należy sprawdzić zgodność interfejsu i kotła z OpenTherm. Prace przy urządzeniu gazowym powinny być wykonywane zgodnie z zaleceniami producenta i przez osoby posiadające odpowiednie kwalifikacje.

Nie należy ingerować w fabryczne zabezpieczenia urządzenia.

## 9. Współpraca i rozwój

Projekt jest otwarty na uwagi, testy, propozycje usprawnień i współpracę.

Jeżeli budujesz własny regulator OpenTherm, korzystasz z ESPHome lub Home Assistant i chcesz rozwijać niezależne rozwiązania sterowania ogrzewaniem – zapraszam do współpracy.

Każda informacja z rzeczywistej instalacji może pomóc w poprawie projektu.
