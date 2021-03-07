### Zadanie 1 - Insecure Data Storage
1. Jeśli jeszcze tego nie zrobiłeś - uruchom obydwie maszyny wirtualne (jak w instrukcji wyżej).
2. Naszym pierwszym zadaniem jest odnalezienie źle przechowywanego hasła w bazie danych aplikacji. W przeglądarkowej wersji wchodzimy w zakładkę *Private/Insecure Data Storage*. Czytamy opis zadania. 
3. Uruchamiamy aplikację na maszynie mobilnej, patrzymy na komunikaty (Databases created).
4. Jak sam opis podpowiada, dane aplikacji zazwyczaj znajdują się w katalogu 
/data/data/com.app.***przykladowaaplikacja***, więc przechodzimy do terminalu, i odnajdujemy folder naszej aplikacji *InsecureData*.
	
	***cd /data/data*** - przechodzimy do wspomnianego katalogu
	***ls*** - odnajdujemy naszą aplikację (com.mobshep.insecuredata)
	***cd com.mobshep.insecuredata*** - wchodzimy w niego
	***ls*** - sprawdzamy zawartość folderu
5. W folderze możemy zauważyć kolejne 3 katalogi - ze względu na pokazany wcześniej przez aplikację komunikat, chyba jasne jest, dlaczego wchodzimy do katalogu databases :)
	***cd databases***
6. W folderze możemy zauważyć dwa pliki - wyświetlamy obydwa poleceniem *cat*.
	***cat Members***
	***cat Members-journal***
7. Gołym okiem bardziej ciekawy wydaje się pierwszy plik - mamy tutaj dane, które potencjalnie mogą być danymi logowania administratora. Sprawdzamy uzyskane dane w wersji przeglądarkowej.

### Zadanie 2 - Broken Crypto
1. Naszym drugim zadaniem, jest aplikacja czatu ze słabym użytym algorytmem szyfrującym. W przeglądarce wchodzimy w zakładkę *Corporal/Broken Crypto* i czytamy opis zadania. 
2. Przechodzimy do maszyny mobilnej i uruchamiamy aplikację BrokenCrypto. Aplikacja wyświetla nam kilka zaszyfrowanych wiadomości. Spróbuj zauważyć jakąś zależność w tych szyfrogramach, jeśli nie zauważysz żadnej, możesz spróbować posłużyć się jakimś [identyfikatorem szyfrów](https://www.boxentriq.com/code-breaking/cipher-identifier). 
3. Zależnością jaką można zauważyć w tych szyfrogramach jest to, że składają się z cyfer 0-9 oraz liter a-f. To już pierwsza przesłanka, że został tu po prostu użyty HEX.
4. Sprawdzamy wiadomości przy pomocy [konwertera Hex to ASCII](https://www.rapidtables.com/convert/number/hex-to-ascii.html), jedna z wiadomości będzie zawierała klucz, który jest odpowiedzią do zadania, którą wklejamy w przeglądarkowej wersji. 
### Zadanie 3 - Poor Authentication
1. Zadanie 3 to niejako inna wersja 3 - poruszać się będziemy również po plikach aplikacji. W przeglądarce wchodzimy w zakładkę *Corporal/Poor authentication* i czytamy opis zadania. 
2. Jak dowiedzieliśmy się z opisu, aplikacja PoorAuthentication mimo że funkcja logowania jest zabezpieczona, to logi tego co wpisywał użytkownik do aplikacji notatek mogą być przechowywane jawnie. Włączamy aplikację i próbujemy zresetować hasło. Jak możemy zauważyć, potrzebujemy poznać odpowiedzi na dwa pytania - ulubione jedzenie oraz nazwisko panieńskie matki. 
3. Przechodzimy do terminalu, w którym tak jak w pierwszym zadaniu, przechodzimy do katalogu */data/data*
	***cd /data/data***
	***ls*** - odnajdujemy pliki naszej aplikacji (com.mobshep.poorauthentication)
	***cd com.mobshep.poorauthentication*** - przechodzimy do katalogu z plikami
4. Teraz poleceniami *cd i ls* sprawdzamy zawartości katalogów w naszym folderze, jak możemy zauważyć - folder *files* przechowuje logi aplikacji. 
5. Sprawdzamy kolejno wszystkie logi aplikacji komendą *cat*. W owych logach możemy poznać odpowiedzi na nurtujące nas pytania i dostać się do konta użytkownika Jack. 
6. Gdy uda nam się zalogować przy użyciu zresetowanego hasła, ukaże nam się odpowiedź do zadania, którą wpisujemy w wersji przeglądarkowej. 
### Zadanie 4 - Insecure Data Storage 1
1. Kolejne zadanie z źle przechowywanymi bazami danych. W przeglądarkowej wersji przechodzimy do *Sergeant/Insecure Data Storage 1* i czytamy opis zadania. 
2. Uruchamiamy aplikację i zauważamy komunikat (Databases created)
3. Identycznie jak w pierwszej wersji tego zadania, przechodzimy do terminalu, do folderu /data/data i odnajdujemy naszą aplikację. 
	***cd /data/data***
	***ls*** - odnajdujemy pliki naszej aplikacji
	***cd com.mobshep.insecuredata1***
4. Przeszukujemy foldery poleceniami *cd* i *ls*, możemy zauważyć, że znowu w folderze databases znajdują się dwa pliki - tak jak za pierwszym razem, interesować nas będzie głównie plik bez *"-journal"* w nazwie. 
5. Wykonujemy polecenie ***cat Users***, jednak tym razem sprawa nie wydaje się tak prosta jak za pierwszym razem. Interesujące nas dane wydają się w jakiś sposób zaszyfrowane. Wobec tego przyda nam się również wiedza z zadania drugiego - spróbujemy znaleźć jakąś zależność w tym co widzimy w terminalu. Jeśli nie mamy pomysłu, możemy także posłużyć się [identyfikatorem szyfrów](https://www.boxentriq.com/code-breaking/cipher-identifier). 
6. Będzie nas oczywiście interesować hasło użytkownika Root, więc zależnością którą możemy zauważyć jest to, że w szyfrogramach pojawia się znak =, który jest często na końcu szyfrogramu w **Base64**. Szyfrogram przepisujemy do [konwertera base64 to ASCII](http://practicalcryptography.com/ciphers/base64-cipher/). Otrzymany w ten sposób plaintext to rozwiązanie naszego zadania. 
### Zadanie 5 - Reverse Engineering
1. Teraz zajmiemy się inżynierią odwrotną aplikacji na androida, przechodzimy do zakładki *Corporal/Reverse Engineering 2*, czytamy opis zadania. 
2. Tym razem nie musimy używać naszej mobilnej maszyny - wszystkie narzędzia znajdują się w rozpakowanym przez nas katalogu który tę maszynę zawiera. Wobec tego do niego wchodzimy.
3. Najpierw musimy nasz plik .apk zamienić na .jar. Służy do tego narzędzie dex2jar zawarte w naszym katalogu. Rozpakowujemy paczkę dex2jar-2.0.zip, kopiujemy plik ReverseEngineer2.apk i wrzucamy go do rozpakowanej paczki. Uruchamiamy w tym katalogu (tym w którym jest teraz nasz apk i wszystkie pliki dex2jara) terminal/wiersz poleceń i wykonujemy komendę ***d2j-dex2jar.bat ReverseEngineer2.apk*** która skonwertuje nasz apk do pliku .jar
4. Teraz wychodzimy z tego folderu, i w głównym katalogu z plikami maszyny mobilnej odnajdujemy ***jd-gui-1.4.0***, który uruchamiamy. 
5. Uruchomi nam się dekompilator java, którym możemy "pobawić się" z naszą aplikacją. Wobec tego klikamy ***File/Open file*** i odnajdujemy przekonwertowany przez nas wcześniej plik. 
6. Mamy wobec tego zdekompilowany kod naszej aplikacji, w którym możemy teraz poszukać jakichś "słabości" kodu. Przeglądając klasy, możemy trafić na jedną, która w nieodpowiedni sposób przechowuje dane logowania, rozwiązaniem wobec tego jest hasło w owej klasie. 
### Zadanie 6 - Content Provider Leakage
1. Do ostatniego zadania wracamy do naszej maszyny mobilnej, zajmiemy się problemem [źle skonfigurowanego Content Providera](https://resources.infosecinstitute.com/topic/android-hacking-security-part-2-content-provider-leakage/). 
2. W wersji przeglądarkowej przechodzimy do zakładki *Private/Content Provider Leakage* i czytamy opis zadania.
3. Jest to bardzo proste zadanie, dlatego polecam przeczytać link podany wyżej, żeby zrozumieć co robimy :)
4. Do uzyskania odpowiedzi wystarczy nam wykonanie komendy 
	***adb shell content query --uri content://com.somewhere.hidden.SecretProvider/data***
klucz, którym odpowie nam adb jest rozwiązaniem zadania. 


