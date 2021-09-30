Dette dokument beskriver indholdet af zip-filen. Variabelnavnene, som beskrives nedenfor, refererer til søjlenavne medmindre andet er beskrevet. 

BEMÆRKNINGER: 
Den 9/5-2022 er en overestimering af antal testede personer blevet korrigeret i "Fil 9: Test_pos_over_time". Overestimeringen har ikke haft betydning for beregningen af positivprocenterne i filen. Siden den 23. marts 2022, hvor reinfektioner blev implementeret i zip-filen med overvågningsdata, har antallet af testede personer i kolonnerne PrevPos, Tested og Tested_kumulativ i filen Test_pos_over_time været overestimeret. 
Fra d. 23/3-2022 indeholder filerne reinfektioner. Dog kører gennembrudsinfektionsfiler (se senere sektion) videre på en tidligere algoritme, som beregnede reinfektioner lidt anderledes i nogle filer og slet ikke i andre.
Fra d. 23/3-2022 udgår Cases_by_age og Municipality_test_pos fra zip-filen.

Forkortelser:
LPR: Landspatientregistret.
CPR-registret: Det Centrale Personregister.




Generelle definitioner:
Dødsdato: Dagen hvor en person er registreret død.
Covid-19-relateret indlæggelse: En indlæggelse, hvor patienten blev indlagt inden for 14 dage efter prøvetagningsdato for den første positive SARS-CoV-2-PCR-prøve. Data baseres på de daglige øjebliksbilleder fra regionernes IT-systemer, som sendes hver dag kl. 7 og 15 og Landspatientregistret (LPR). Indlæggelser omfatter patienter, der har været registreret i mindst ét øjebliksbillede, eller som ifølge LPR er eller har været indlagt mere end 12 timer. Indlæggelser registeret i LPR på intensivafdeling inkluderes også når de varer mindre end 12 timer.
Covid-19-relaterede indlæggelsesdatoer: Indlægges en person mere end 48 timer før deres første positive PCR-test for Covid-19 er taget, så tæller deres prøvetagningsdato som COVID-19-indlæggelsesdatoen. I alle andre tilfælde er det indlæggelsesdatoen, som er angivet.
Prøvedato: Dette er datoen PCR-testen blev taget og ikke datoen, hvor prøvesvaret forelå.
Befolkningstal: Befolkningstal er baseret på CPR-registeret og opdateres d.15 i hver måned. Populationen udgøres af personer i live som har et gyldigt CPR nummer, er bosat i Danmark og opfylder følgende kriterier: Personen skal have en gyldig kommunekode, som matcher en eksisterende kommune, køn skal være angivet og personen skal have en gyldig vejkode. 




Generel struktur:
Rækkerne i filerne er som udgangspunkt stratificeringer efter relevante parametre, eksempelvis aldersgruppering eller tidsopdeling. Der stratificeres generelt efter variablen i første søjle. Mange filer indeholder også en række, som opgiver totalen. Enkelte tabeller kan have rækker, som afviger fra dette mønster. I disse tabeller specificeres dette i "Noter" under tabellens variabelbeskrivelse. Filerne er semikolon-separerede.

Filerne bliver opdateret hver dag og i denne forbindelse kan tidsserier også ændre sig tilbage i tiden, hvis nyere data foreligger. Derfor anbefales det altid at benytte det senest tilgængelige data og for så vidt muligt, ikke at gemme filer og lave tidsserier på basis af gamle filer.

Typer af tests:
Filerne bygger som udgangspunkt på PCR-test, som er den test, der bruges til at definere bekræftede covid-19-tilfælde. Antigen-test (også kaldet for lyntest, kviktest, ag-test og hurtigtest) anvendes i teststrategien som screeningsværktøj og bruges i overvågningen til at definere mistænkte tilfælde. Der er nogle filer, som viser data for antigen-tests, hvis andet ikke er angivet bygger filen på PCR-tests. Data indeholder ikke serologitest, som er den test, der udføres, når man skal undersøge, om raske mennesker tidligere har haft covid-19.

------------------------------------------------------

Fil 1: Cases_by_sex:

Aldersgruppe: Aldersgrupperingerne som bekræftede tilfælde er stratificeret efter.
Kvinder_(procent): Antallet af kvinder i den givne aldersgruppe, som er testet positive for covid-19. Tallet i parentes er procent af totalen for denne aldersgruppe, som er kvinder, og kan udregnes som tallet før parentesen i Kvinder_(procent) divideret med værdien i I_alt i samme række.
Mænd_(procent): Antallet af mænd i den givne aldersgruppe, som er testet positive for covid-19. Tallet i parentes er procent af totalen for denne aldersgruppe, som er mænd, og kan udregnes som tallet før parentesen i Mænd_(procent) divideret med værdien i I_alt i samme række.
I_alt: Alle bekræftede covid-19-tilfælde i den givne aldersgruppe. Udregnes som summen af tallene for kvinder og mænd.

------------------------------------------------------

Fil 2: Deaths_over_time:

Dato: Datoer i formatet YYYY-MM-DD, som der stratificeres efter.
Antal_døde: Antal døde registreret på en given dag. En person indgår, hvis de er registreret i enten CPR eller Dødsårsagsregisteret. Er en person registreret både i CPR og Dødsårsagsregisteret med forskellige dødsdatoer, bruges datoen angivet i CPR. Dødsfald relateret til covid-19 defineres som et covid-19 bekræftet tilfælde, der er død indenfor 30 dage efter påvist covid-19-infektion. Covid-19 er ikke nødvendigvis den tilgrundliggende årsag til dødsfaldet.

------------------------------------------------------

Fil 3: Deaths_o_weeks_covid_cause:

Dato: Kalenderuge-år i formatet Uuu-YYYY 
Ugentlig antal døde som i Fil 3 og yderligere stratificeret efter tilgrundliggende dødsårsag (baseret på ugentlige opgørelser af Dødsårsagsregisterets løbende validering af Covid-19-relaterede dødsattester, leveret af Sundhedsdatastyrelsen).
Se den ugentlige tendensrapport covid19.ssi.dk for yderligere beskrivelser og figurer.

------------------------------------------------------

Fil 4: Municipality_cases_time_series: 
Dette er en krydstabel over antallet af bekræftede covid-19-tilfælde for kommunerne på en given dag. Kolonnenavne angiver kommunen, og rækkenavne angiver testdatoen. Cellerne indeholder antallet af bekræftede covid-19-tilfælde for en given kombination af kommune og testdato.

------------------------------------------------------

Fil 5: Municipality_tested_persons_time_series: 
Dette er en krydstabel over antallet af personer, som er testede for covid-19 for kommunerne på en given dag. Kolonnenavne angiver kommunen, og rækkenavne angiver testdatoen. Cellerne indeholder antallet af testede personer for en given kombination af kommune og testdato. En person kan bidrage op til en gang hver dag, såfremt de ikke tidligere er testet positive.

------------------------------------------------------

Fil 6: Newly_admitted_over_time:
Indlæggelsestal i denne tabel er baseret både på LPR og de daglige øjebliksbilleder, som indrapporteres af regionerne hver dag, og en person medregnes, når blot de er registreret indlagt i en af disse. Er en person registreret i begge med forskellige datoer, så bruges den første. Denne opgørelse er udelukkende baseret på covid-19 bekræftede tilfælde. Læs mere om definitionen for covid-19 relateret indlæggelse på Datakilder og definitioner (ssi.dk)

Dato: Datoer i formatet YYYY-MM-DD som der stratificeres efter.
Hovedstaden: Antal nyindlagte på en given dag i Region Hovedstaden.
Sjælland: Antal nyindlagte på en given dag i Region Sjælland.
Syddanmark: Antal nyindlagte på en given dag i Region Syddanmark.
Midtjylland: Antal nyindlagte på en given dag i Region Midtjylland.
Nordjylland: Antal nyindlagte på en given dag i Region Nordjylland.
Ukendt Region: Antal nyindlagte på en given dag, som ikke har en registreret bopæl i nogen region.
Total: Det totale antal nyindlagte på en given dag, dette tal er summen af værdierne i Hovedstaden, Sjælland, Syddanmark, Midtjylland, Nordjylland og Ukendt Region.

------------------------------------------------------

Fil 7: Region_summary:

Region: De fem danske regioner som der stratificeres efter.
Testede: Antal testede personer i en given region. Hver person kan kun bidrage en gang. Er man testet i flere regioner, tæller den region, man først er testet positiv i for personer, der er testet positive, og ellers tæller den første region man er testet negativ i.
Positive: Antal personer med bekræftet covid-19 i en given region.
Indlagt_total: Antal indlagte i en given region.
Døde: Antal døde i en given region. En person indgår, hvis de er registreret i enten CPR eller Dødsårsagsregisteret. Er en person registreret både i CPR og Dødsårsagsregisteret med forskellige dødsdatoer bruges datoen angivet i CPR.

------------------------------------------------------

Fil 8: Rt_cases_YYYY_MM_DD: 
Denne fil indeholder den estimerede tidsserie af kontakttalsværdier beregnet på baggrund af antallet af bekræftede covid-19-tilfælde.

date_sample: Datoen, hvor kontakttallet estimeres.
Estimate: Den estimerede værdi af kontakttallet på den angivne dag.
uncertainty_lower: Den estimerede nedre grænse, når der tages højde for usikkerhed på den angivne dag.
uncertainty_upper: Den estimerede øvre grænse, når der tages højde for usikkerhed på den angivne dag.

------------------------------------------------------

Fil 9: Test_pos_over_time: 
Tabellen indeholder kun personer testet ved PCR-test. 
Denne tabel fokuserer på testede personer per dag frem for personer testet i hele perioden. I modsætning til de andre tabeller kan en person derfor bidrage flere gange til denne tabel, dog kun en gang per dag.

Dette er modsat dashboardet (www.ssi.dk/covid19data), hvor positivprocenten beregnes over en uge, med antal personer som er testet positive seneste syv komplette dage over antallet af alle personer testet seneste syv komplette dage.

Date: Datoer i formatet YYYY-MM-DD som der stratificeres efter.
NewPositive: Antallet af personer, som for første gang er testet positive for covid-19, på en given dag. Hvis det er en reinfektion skal der være gået mindst 60 dage siden starten af forrige infektion for at en person tælles med i denne kategori.
NotPrevPos: Antallet af personer testet på en given dag, hvor sidste infektion ligger mere end 60 dage tilbage i tiden. Indeholder negative tests for personer, som ikke har testet positive før, samt den første positive test for hver infektion.
PosPct: Andelen (%) af personer som er testet positive. Dette er beregnet som NewPositive divideret med NotPrevPos. 
PrevPos: Antallet af personer testet på en given dag, som tidligere har testet positive hvor sidste infektion ligger indenfor de sidste 60 dage. Den positive test som indikerer infektionsstart indgår ikke her.
Tested: Det samlede antal testede personer på en given dag, som har fået konklusivt svar (positiv eller negativ). Dette kan udregnes som NotPrevPos plus PrevPos.
Tested_kumulativ: Det kumulerede antal personer testet op til og med en given dag, som har fået konklusivt svar (positiv eller negativ). Udregnes som summen af værdierne i Tested frem til den givne dag. En person, der er testet på flere forskellige dage, kan bidrage mere end en gang i denne sum.

Noter: I den sidste række (Antal personer) er den totale opgørelse opgjort således, at en person kun kan indgå en gang i hver søjle, i modsætning til de andre. Af denne grund er Tested det samme som NotPrevPos i denne række, og ikke en sum af NotPrevPos og PrevPos, som i de andre.

------------------------------------------------------

Fil 10: Test_pos_over_time_antigen: 
Denne tabel indeholder - i modsætning til test_pos_over_time - kun personer testet ved antigen-test og personer tæller bestandigt som tidligere positive efter den allerførste positive antigen-test.
Denne tabel fokuserer ligeledes på testede personer per dag frem for personer testet i hele perioden. I modsætning til de andre tabeller kan en person derfor bidrage flere gange til denne tabel, dog kun en gang per dag. I denne fil indgår udelukkende personer testet med antigen-test.
Fra 1/9-2021 ændres filen til at indeholde samtlige personer med gyldigt CPR nummer uanset om de har været testet med PCR før. Før denne dato har filerne udelukkende indeholdt personer med gyldigt CPR nummer som samtidig også havde fået foretaget en PCR test. Personer uden gyldigt CPR nummer kan ikke følges korrekt og tæller derfor ikke med i denne opgørelse.


Date: Datoer i formatet YYYY-MM-DD som der stratificeres efter.
NewPositive: Antallet af personer, som for første gang er testet positive for covid-19, på en given dag.
NotPrevPos: Antallet af personer testet på en given dag, som ikke har testet positive på en tidligere dato. Indeholder negative tests for folk, som ikke har testet positive før, samt første positive test.
PosPct: Andelen af personer som er testet positive. Dette er beregnet som NewPositive divideret med NotPrevPos. Bemærk at prøver taget på folk, som tidligere har testet positive ikke er medregnet her.
PrevPos: Antallet af personer testet på en given dag blandt personer, som tidligere har testet positive. Den første test, som er positiv, indgår ikke her.
Tested: Det samlede antal testede personer på en given dag, som har fået konklusivt svar (positiv eller negativ). Dette kan udregnes som NotPrevPos plus PrevPos.
Tested_kumulativ: Det kumulerede antal personer testet op til og med en given dag, som har fået konklusivt svar (positiv eller negativ). Udregnes som summen af værdierne i Tested frem til den givne dag. En person, der er testet på flere forskellige dage, kan bidrage mere end en gang i denne sum.

Noter: I den sidste række (Antal personer) er den totale opgørelse opgjort således, at en person kun kan indgå en gang i hver søjle, i modsætning til de andre. Af denne grund er Tested det samme som NotPrevPos i denne række, og ikke en sum af NotPrevPos og PrevPos, som i de andre.

------------------------------------------------------

Fil 11: Test_regioner: Dette er en tabel over offentlige tests. Der indgår kun PCR-tests

Ugenr: Tidsperioderne der stratificeres efter. Dette er dage for indeværende uge og ugenumre for forrige uger.
Region Hovedstaden: Antal tests gennemført i Region Hovedstaden den givne dag eller uge.
Region Midtjylland: Antal tests gennemført i Region Midtjylland den givne dag eller uge.
Region Nordjylland: Antal tests gennemført i Region Nordjylland den givne dag eller uge.
Region Sjælland: Antal tests gennemført i Region Sjælland den givne dag eller uge.
Region Syddanmark: Antal tests gennemført i Region Syddanmark den givne dag eller uge.
Statens Serum Institut: Antal tests gennemført på Statens Serum Institut (eksklusiv Testcenter Danmark) den givne dag eller uge.
Testcenter Danmark: Antal tests gennemført hos Testcenter Danmark den givne dag eller uge.
Total: Det samlede antal tests gennemført i hele landet. Dette kan udregnes som summen af Region Hovedstaden, Region Midtjylland, Region Nordjylland, Region Sjælland, Region Syddanmark, Statens Serum Institut og Testcenter Danmark.
Kumulativ_total: Det kumulerede antal tests gennemført på en given dag eller uge. Udregnes som summen af værdierne i Tested frem til den givne dag eller uge.


------------------------------------------------------

Fil 12: Antigentests_pr_dag: 

Dette er en opgørelse af antallet af antigentests per dag. Personer med flere antigentests på en dag vil kun tælles en gang per dag. Et positivt svar vil vægtes højere end et negativt svar, og et negativt svar vil vægtes højere end intet svar. 
Derudover opgøres hvor mange personer, som er blevet testet med PCR-test på samme dag eller dagen efter antigen-test. 
Antigentest-svar sammenholdes med de fundne svar fra PCR. En PCR-test kan tælle flere gange i denne opgørelse.
Eksempelvis vil en person med en positiv antigentest den 1/2-2021 og 2/2-2021, som får lavet en positiv PCR test den 3/2-2021 tælle to gange; første gang med en positiv antigen-test som ikke er blevet be- eller afkræftet og anden gang med en positiv antigen-test, som er blevet bekræftet.
Hvis en person har flere PCR-tests inden for samme vindue vil den nærmeste PCR-test tages. Hvis en person har flere PCR på en dag, vægtes 
PCR-svar på samme måde som antigentestene. Et positivt svar vil vægtes højere end et negativt svar, og et negativt svar vil vægtes 
højere end intet svar. 
Fra 1/9-2021 ændres filen til at indeholde samtlige personer med gyldigt CPR nummer uanset om de har været testet med PCR før. Før denne dato har filerne udelukkende indeholdt personer med gyldigt CPR nummer som samtidig også havde fået foretaget en PCR test. Personer uden gyldigt CPR nummer kan ikke følges korrekt og tæller derfor ikke med i denne opgørelse.

Dato					: Dato for prøvetagning 
AG_testede				: Antallet af antigentests (max en per person per dag)
AG_pos					: Antallet af positive antigentests
AGpos_minusPCRkonf			: Antal positive prøver, som ikke er blev be- eller afkræftet med PCR-test inden for to dage af antigentesten
AGpos_PCRpos				: Antal positive antigentests hvor PCR-test også var positiv
AGposPCRneg 				: Antal positive antigentests hvor PCR-test var negativ
AGnegPCRpos				: Antal negative antigentests hvor PCR-test var positiv
AGnegPCRneg				: Antal negative antigentests hvor PCR-test også var negativ

------------------------------------------------------

Fil 13: plejehjem_ugeoversigt:

OBS: Kommer kun ud om tirsdagen. 
Denne fil indeholder en opgørelse over covid-19-tests og -tilfælde på danske plejehjem pr. uge siden uge 11 2020. Dette er dataen bag tabel 7.1, som dog kun indeholder de seneste fem uger. 

År: Årstal, der stratificeres efter.
Uge: Uge, der stratificeres efter. 
Bekræftede tilfælde beboere: Antal beboere på plejehjem, som er testet positiv for covid-19 med en PCR test inden for den givne uge. Alle personer tæller kun med med deres første positive test.
Dødsfald blandt bekræftede beboere: Antal beboere på plejehjem, som er døde i den givne uge, hvis det er inden for 30 dage, efter at de er testet positiv for covid-19 med en PCR-test for første gang. 
Plejehjem med bekræftede beboere: Antal plejehjem, hvor mindst én beboer er testet positiv for covid-19 med en PCR-test inden for den givne uge. Igen tæller kun beboernes første positive test.
Antal tests blandt beboere: Antal PCR-tests for covid-19 udført på beboere på plejehjem inden for den givne uge. Hver beboer kan tælle med flere gange. Beboere, som tidligere er testet positive, tæller fortsat med, hvis de bliver testet igen senere (uafhængigt af resultat).
Plejehjem med testede beboere: Antal plejehjem, hvor mindst én beboer er blevet PCR-testet for covid-19 inden for den givne uge.


------------------------------------------------------

=============== Indlæggelse af og med covid-19 =======

Denne sektion omhandler filerne:
- figurtendensalderdata
- figurtendensdata_1
- figurtendensdata_2
- figurtendensugedata
- figurtendensugedata_10weeks

Filerne indeholder data bag figur 4 og 5 samt tabel 7 og 8 i den ugentlige tendensrapport:
https://covid19.ssi.dk/overvagningsdata/ugentlige-tendenser-for-covid-19-og-andre-luftvejsinfektioner

Nyindlæggelse: Den første Covid-19-relateret indlæggelse registreret efter den første positive SARS-CoV-2-PCR-prøve.


------------ figurtendensalderdata -------------------
Denne fil indeholder en opgørelser over antallet af nyindlæggelser i tre grupper, "Indlæggelse pga. covid-19", "Indlæggelse, hvor covid-19 kan have spillet en rolle" og "Indlæggelse pga. andre forhold end covid-19", stratificeret på 10års aldersgrupper, samt andelen i de tre grupper inden for hver aldersgruppe. Opgørelsen er for perioden 01-06-2020 frem til og med søndag to uger før udgivelse af tendensrapporten.
Detaljer vedrørende klassifikation af nyindlæggelser i de tre grupper kan findes i fokusrapporten om covid-19-relaterede hospitalsindlæggelser under SARS-CoV-2-epidemien. (https://www.ssi.dk/aktuelt/nyheder/2022/tre-ud-af-fire-indlagte-pa-hospitalerne-med) 

Aldersgruppe: Aldersgrupperingerne som der er stratificeret efter.
Klassifikation: Klassifikation af nyindlæggelser ud fra diagnoser givet under indlæggelsen. 
Antal nyindlæggelser: Antallet af nyindlæggelser for den givne klassifikation og aldersgruppe.
Andel nyindlæggelser: Andelen af nyindlæggelser for den givne klassifikation inden for den givne aldersgruppe.

------------ figurtendensdata_1 ----------------------
Denne fil indeholder en opgørelse over andelen af nyindlæggelser i tre grupper, "Indlæggelse pga. covid-19", "Indlæggelse, hvor covid-19 kan have spillet en rolle" og "Indlæggelse pga. andre forhold end covid-19", stratificeret på uge og alder.
Detaljer vedrørende klassifikation af nyindlæggelser i de tre grupper kan findes i fokusrapporten om covid-19-relaterede hospitalsindlæggelser under SARS-CoV-2-epidemien. (https://www.ssi.dk/aktuelt/nyheder/2022/tre-ud-af-fire-indlagte-pa-hospitalerne-med) 

Uge: Tidsperiode der stratificeres efter. En nyindlæggelse er indeholdt i den periode den er påbegyndt i.
Aldersgruppe: Aldersgrupperingerne som der er stratificeret efter.
Klassifikation: Klassifikation af nyindlæggelser ud fra diagnoser givet under indlæggelsen. 
Procent af indlæggelser: Procent af indlæggelser med den givne kategori, inden for den givne uge og aldersgruppe.

------------ figurtendensdata_2 ----------------------
Denne fil indeholder en opgørelse over antallet af nyindlæggelser per dag i de to aldersgrupper "0-59 år" og "60+ år".

Dato: Tidsperiode der stratificeres efter. En nyindlæggelse er indeholdt i den periode den er påbegyndt i.
Aldersgruppe: Aldersgrupperingerne som der er stratificeret efter.
Nyindlæggelser pr. dag: Antallet af nyindlæggelser for den givne dag og aldersgruppe.

------------ figurtendensugedata ---------------------
Denne fil indeholder en opgørelse over andelen af Covid-19 relaterede nyindlæggelser i tre grupper,"Indlæggelse pga. covid-19", "Indlæggelse, hvor covid-19 kan have spillet en rolle" og "Indlæggelse pga. andre forhold end covid-19", stratificeret på uge. Opgørelsen er for perioden 01-06-2020 frem til og med søndag to uger før udgivelse af tendensrapporten.
Detaljer vedrørende klassifikation af nyindlæggelser i de tre grupper kan findes i fokusrapporten om covid-19-relaterede hospitalsindlæggelser under SARS-CoV-2-epidemien. (https://www.ssi.dk/aktuelt/nyheder/2022/tre-ud-af-fire-indlagte-pa-hospitalerne-med) 

uge: Uge som den covid-19 relaterede indlæggelser er påbegyndt i.
år: År som den covid-19 relaterede indlæggelser er påbegyndt i.
Klassifikation: Klassifikation af nyindlæggelser ud fra diagnoser givet under indlæggelsen. 
Antal nyindlæggelser: Antallet af nyindlæggelser for den givne uge og klassifikation.
Fordeling af nyindlæggelser [%]: Fordelingen af nyindlæggelser i procent for den givne dag og klassifikation.

------------ figurtendensugedata_10weeks ---------------------
Dette er det samme som ovenstående (figurtendensugedata), men viser kun for de seneste 10 uger. 

------------------------------------------------------

=============== Variant data for covid19 =======

------------ Variant_tabel.xlsx ---------------------
Data for den seneste uge trækkes på udarbejdelsesdatoen. Data opdateres løbende bagudrettet i takt med, at resultater fra sekventering bliver tilføjet. Data er opgjort på prøvedato, og derfor kan der være nogle prøver fra den seneste uge, der endnu ikke er indkommet svar for.

------------------------------------------------------

========= Gennembrudsinfektionsfiler =================

Fra og med tirsdag den 3. maj 2022 er ’Gennembrudsfilerne’ ikke længere en del af zip-filen med overvågningsdata om tirsdagen. Gennembrudsfilerne er blevet offentliggjort på ugentlig basis i en tidsperiode under covid-19-epidemien med stort fokus på gennembrudsinfektioner samt indlæggelse og død opgjort på vaccinestatus. På nuværende tidspunkt er disse oplysninger ikke længere af væsentlig og samfundskritisk betydning, hvorfor filerne udfases. 
