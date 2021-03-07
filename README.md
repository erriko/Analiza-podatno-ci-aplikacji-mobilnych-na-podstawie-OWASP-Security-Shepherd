## Opis projektu
###  Jaki jest cel projektu?
Celem projektu jest analiza podatności aplikacji mobilnych na podstawie narzędzia OWASP Security Shepherd.
Przeanalizujemy zagadnienia z listy OWASP TOP 10, zbadamy jakie podatności występują w aplikacjach oraz jakie są ich konsekwencje.
###  Przygotowanie środowiska pracy

 - Pobieramy pliki **owaspSecurityShepherd_v3.1_VM.zip** oraz **owaspSecurityShepherd_v3.2.3_MobileDevice.7z** z najnowszej dostępnej wersji na [stronie producenta](https://github.com/OWASP/SecurityShepherd/releases) (na 24.01.2020 jest to 3.1).
 - Pliki rozpakowujemy (np. 7zip) i montujemy obraz pierwszy w programie Oracle VM Virtual Box (zalecany) bądź innym programie do obsługi maszyn wirtualnych. 
 - Zmieniamy ustawienia sieciowe maszyny na tryb "Host Only"
 - Uruchamiamy maszynę, po chwili powinien ukazać nam się wiersz poleceń Linuxa, maszyna poprosi nas o zalogowanie - logujemy się używając loginu ***securityshepherd*** i hasła ***shepherd3.1***
 - Po zalogowaniu, wpisujemy w terminal komendę *ifconfig* i sprawdzamy pierwszy adres na liście i wpisujemy go w przeglądarkę na naszym komputerze (hoście maszyny wirtualnej). 
 - Logujemy się używając loginu ***admin*** i hasła ***password***
 - W zakładce *Admin* przechodzimy pod *Module Management*, a następnie do *Change Module Layout*, w której włączamy tryb *Tournament.* 

Pierwsza maszyna wirtualna służy do poznawania treści oraz weryfikacji poprawności zadań, teraz przejdziemy do części właściwej.

 - Importujemy do VM Virtual Box drugi obraz (Mobile Device).
 - Gdy maszyna wystartuje, przechodzimy do ustawień i łączymy maszynę z internetem w trybie *Bridged*.
 - Dodatkowo, "odklikujemy" w zakładce *Wejście* Virtual Boxa integrację myszki. 
 - Maszyna jest gotowa do działania. Aby poruszać się między GUI, a terminalem, używamy skrótu klawiszowego ALT+F1 (terminal), lub ALT+F7 (GUI). 

### Narzędzia i przydatne komendy do wykonania laboratorium.
Laboratorium możemy w całości wykonać używając tylko narzędzi załączonych w pobranych plikach, zauważ, że w folderze z maszyną mobilną, mamy paczkę z dex2jar, oraz Java Decompiler. 
Ponadto przydatnymi komendami będą głównie te podstawowe "unixowe" - cd, cat, ls.



