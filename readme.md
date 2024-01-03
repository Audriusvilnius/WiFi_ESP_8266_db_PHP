## NodeMCU ESP8266 exam project
Requirements:
Setup:
1. Start code from repo:
   * `https://github.com/Audriusvilnius/Two-Factor-Authentication`
2. Start code from repo:
   * `https://github.com/Audriusvilnius/arduino_php`
  
3. ĮVADAS
* Darbo projekto pavadinimas – Apsaugos sistema skirta namų ar panašaus objekto apsaugai, valdoma per WEB sąsaja, apsaugota dviejų faktorių autentifikacija (2FA) ir rodmenų duomenų baze. 
<img width="468" alt="image" src="https://github.com/Audriusvilnius/WiFi_ESP_8266_db_PHP/assets/101082768/e2add462-830f-4fe6-9805-f979227b4fa3">
###  Darbo užduotis: 
Pagrindinė užduotis: Surinkti pateiktą schemą ir pateikti apsaugos sistemos prototipą valdomą per WEB vartotojo sąsaja su integruota dvigubos autentifikacijos sistema, pateikti sketch.ino failą su veikiančiu sprendimu. Vartotojo sąsajoje turi būti galimybė valdyti objekto apsaugos sistema:
* 1.	Įjungti / išjungti apsaugos sistema;
* 2.	Fiksuot apsaugos sistemos objekto statusą ir pokyčius sistemoje realiuoju laiku;
* 4.	Valdyti atskirus objekto mazgus (atrakint / užrakint vartus, duris);
* 5.	Įjungti / išjungti papildomu modulius neatjungiant pagrindinių sistemų;
* 6.	Duomenų ir pokyčių valdymo fiksavimas įrašant ir nuskaitant duomenis į duomenų bazės serverius naudojant MySQL duomenų baze;
* 7.	Vartotojo sąsaja (realizuota su responsive web design);
* 8.	Įrenginio sąsaja;
* 9.	Apsaugos sistemos įrenginys naudoja Wifi duomenų perdavimo ryši prisijungimui prie interneto;
* 10.	Duomenų perdavimas į duomenų baze iš įrenginio pusės vyksta per html POST formos užklausą įrašant duomenys tiesiai į duomenų bazes;
* 11.	Įrenginio duomenų nuskaitymui iš duomenų bazių duomenys pateikiami JSON formatu.
* 12.	Vartotojas per vartotojo sąsaja įgalina programa įrašyti duomenis į duomenų baze.
### Schemą sudaro šie elementai:
* 1.	ESP8266 NodeMCU įrenginys;
* 2.	SparkFun CD74HC4067 analoginis / skaitmeninis multiplekserio modulis - 16 kanalų
* 3.	WEB serveris vartotojo sąsajai;
* 4.	Duomenų bazės serveris dirbantis su MySQL duomenų baze;
* 5.	4 LED diodai;
* 6.	4 mygtukai daviklių imitacijai;
* 7.	4 varžos 220Ω LED diodų pajungimui;
* 8.	4 varžos 1kΩ mygtuku pajungimui;
* 9.	Laidai schemos sujungimui. 
### Naudojama įranga: Personalinis kompiuteris Macbook.
Darbo eiga:
* 1.	Darbo eigos rezultatų fiksavimas pateikiant vaizdo įrašą su veikiančios schemos realizavimu;
* 2.	„Arduino“ security.ino failo pateikimas.
 
### VEIKIMO PRINCIPAS
* Daviklių, jutiklių ir valdiklių sistema nuskaito duomenų rodmenis. Surinktus duomenis siunčia interneto pagalbą į MySQL duomenų bazės serverius. Duomenų bazes serveris atlieka duomenų įpašymą į domenų baze. Prieiga prie duomenų ir apsaugos sistemos vartotojas gali valdyti tik atlikęs dvigubos autentifikacijos procedūrą. Sistema tikrina langų, durų, vartų, kiemo vartų, patalpų judesio daviklių, stiklo dūžių, gaisro bei perimetro jutiklių rodmenys. Sistema valdo durų, vartų ir perimetro sistema aktyvioje ir neaktyvioje sistemos būsenoje t.t. gali būti valdomi šie mazgai nepriklausomai nuo pagrindinės sistemos statuso (pav. 1).
* 
<img width="333" alt="image" src="https://github.com/Audriusvilnius/WiFi_ESP_8266_db_PHP/assets/101082768/e0c5285e-6b18-4b10-bc08-0d1bcfa6d47b">
* REALIZAVIMAS
Vartotojo sąsajos kodas realizuotas pasitelkiant LARAVEL v10.25.2  plugin v0.8.1 versija. Vartotojo sąsajos vaizdas (pav. 2). Vartotojo sąsajoje sistemos įjungimas / išjungimas. Pokyčiu atvaizdavimas skirtingų spalvų jungikliais, bei informaciniais užrašais.
<img width="211" alt="image" src="https://github.com/Audriusvilnius/WiFi_ESP_8266_db_PHP/assets/101082768/5238cd2f-f92d-4279-902d-e87bc3c09252">
###  Padidiname NodeMCU  analoginių jungčių kieki iki 16 prijungiant skaitmeninį multiplekserio modulį per A0 skaitmeninę jungtį ir jungtis D0, D1, D2, D3 pagal pateiktą schemą (pav. 3).
 
pav. 3 SparkFun CD74HC4067 analoginis / skaitmeninio multiplekserio modulio - 16 kanalų pajungimas prie NodeMCU
Papildomu NodeMCU jungčių D5, D6, D7, D8 pajungimas prie LED diodų per 220Ω varžą schema.  (pav. 4). 
 <img width="211" alt="image" src="https://github.com/Audriusvilnius/WiFi_ESP_8266_db_PHP/assets/101082768/da7aaa93-5a4c-4041-8be0-0536b802a7bf">

pav. 4 LED pajungimas D5, D6, D7, D8 jungtys
Skaitmeninio multiplekserio modulio kontaktų C0, C1, C3 pajungimas prie kontrolinių jungiklių imituojančių suveikimo jungiklius (pav. 5).
 <img width="211" alt="image" src="https://github.com/Audriusvilnius/WiFi_ESP_8266_db_PHP/assets/101082768/7d7702c1-e612-49b8-945f-bde21f20f297">

pav. 5 Skaitmeninio multiplekserio modulio kontaktų pajungimas
Skaitmeninio multiplekserio modulio kontaktų C4, C5, C6, C7  pajungimas prie kontrolinių jungiklių imituojančių suveikimo jungiklius, pajungimas per vieną jungiklį (pav. 6).
 <img width="251" alt="image" src="https://github.com/Audriusvilnius/WiFi_ESP_8266_db_PHP/assets/101082768/eff23b6c-5909-47ff-ba4d-d47ae73803a5">

pav. 6 Skaitmeninio multiplekserio modulio kontaktų C4, C5, C6, C7 pajungimas
![image](https://github.com/Audriusvilnius/WiFi_ESP_8266_db_PHP/assets/101082768/c5ab55a3-a2a9-407a-a0fc-eba56f25422e)








