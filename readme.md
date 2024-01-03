## NodeMCU ESP8266 exam project
Requirements:
Setup:
1. Start code from repo:
   * `https://github.com/Audriusvilnius/Two-Factor-Authentication`
2. Start code from repo:
   * `https://github.com/Audriusvilnius/arduino_php`
  
3. ĮVADAS
Darbo projekto pavadinimas – Apsaugos sistema skirta namų ar panašaus objekto apsaugai, valdoma per WEB sąsaja, apsaugota dviejų faktorių autentifikacija (2FA) ir rodmenų duomenų baze. 
<img width="468" alt="image" src="https://github.com/Audriusvilnius/WiFi_ESP_8266_db_PHP/assets/101082768/e2add462-830f-4fe6-9805-f979227b4fa3">
Darbo užduotis: 
Pagrindinė užduotis: Surinkti pateiktą schemą ir pateikti apsaugos sistemos prototipą valdomą per WEB vartotojo sąsaja su integruota dvigubos autentifikacijos sistema, pateikti sketch.ino failą su veikiančiu sprendimu. Vartotojo sąsajoje turi būti galimybė valdyti objekto apsaugos sistema:
1.	Įjungti / išjungti apsaugos sistema;
2.	Fiksuot apsaugos sistemos objekto statusą ir pokyčius sistemoje realiuoju laiku;
3.	Valdyti atskirus objekto mazgus (atrakint / užrakint vartus, duris);
4.	Įjungti / išjungti papildomu modulius neatjungiant pagrindinių sistemų;
5.	Duomenų ir pokyčių valdymo fiksavimas įrašant ir nuskaitant duomenis į duomenų bazės serverius naudojant MySQL duomenų baze;
6.	Vartotojo sąsaja (realizuota su responsive web design);
7.	Įrenginio sąsaja;
8.	Apsaugos sistemos įrenginys naudoja Wifi duomenų perdavimo ryši prisijungimui prie interneto;
9.	Duomenų perdavimas į duomenų baze iš įrenginio pusės vyksta per html POST formos užklausą įrašant duomenys tiesiai į duomenų bazes;
10.	Įrenginio duomenų nuskaitymui iš duomenų bazių duomenys pateikiami JSON formatu.
11.	Vartotojas per vartotojo sąsaja įgalina programa įrašyti duomenis į duomenų baze.
Schemą sudaro šie elementai:
1.	ESP8266 NodeMCU įrenginys;
2.	SparkFun CD74HC4067 analoginis / skaitmeninis multiplekserio modulis - 16 kanalų
3.	WEB serveris vartotojo sąsajai;
4.	Duomenų bazės serveris dirbantis su MySQL duomenų baze;
5.	4 LED diodai;
6.	4 mygtukai daviklių imitacijai;
7.	4 varžos 220Ω LED diodų pajungimui;
8.	4 varžos 1kΩ mygtuku pajungimui;
9.	Laidai schemos sujungimui. 
Naudojama įranga: Personalinis kompiuteris Macbook.
Darbo eiga:
1.	Darbo eigos rezultatų fiksavimas pateikiant vaizdo įrašą su veikiančios schemos realizavimu;
2.	„Arduino“ security.ino failo pateikimas.
 
VEIKIMO PRINCIPAS
Daviklių, jutiklių ir valdiklių sistema nuskaito duomenų rodmenis. Surinktus duomenis siunčia interneto pagalbą į MySQL duomenų bazės serverius. Duomenų bazes serveris atlieka duomenų įpašymą į domenų baze. Prieiga prie duomenų ir apsaugos sistemos vartotojas gali valdyti tik atlikęs dvigubos autentifikacijos procedūrą. Sistema tikrina langų, durų, vartų, kiemo vartų, patalpų judesio daviklių, stiklo dūžių, gaisro bei perimetro jutiklių rodmenys. Sistema valdo durų, vartų ir perimetro sistema aktyvioje ir neaktyvioje sistemos būsenoje t.t. gali būti valdomi šie mazgai nepriklausomai nuo pagrindinės sistemos statuso (pav. 1).
pav. 1 Schema.
![image](https://github.com/Audriusvilnius/WiFi_ESP_8266_db_PHP/assets/101082768/f9d576ec-c1e7-45fa-aef7-2301186171e3)



