# Tilbakemelding på product brief

| | |
|---|---|
| **Gruppe** | G12 – G12-bergfald-bergfald |
| **Product brief** | `Jippy-Product-Brief.md` (commit `3116300`) |
| **Tilbakemelding fra** | Faglærer i IBE160 (utarbeidet med KI-støtte) |
| **Dato** | 2026-10-06 |

## Samlet vurdering

- **Bør revideres før dere går videre.** Rett punktene markert «Endre» før dere lager PRD og arkitektur.

Vi har vurdert `Jippy-Product-Brief.md` (Draft v1.0, 25. september 2026). Briefen er godt skrevet og gjennomtenkt. Endringene som trengs er få og avgrensede, men de bør gjøres før PRD-en, fordi de styrer hvordan dere skal teste og kjøre appen.

**Det som er bra:**

1. Problemet og primærbrukeren er tydelige: universitetsstudenter med tunge lesefag som bruker mer tid på å *forberede* seg enn på å øve. Brukerhistorien «uploaded today's lecture after class, did a 10-minute quiz on the bus» gjør det lett å se kjerneflyten for seg.
2. «Scope test» og listen «OUT: not now» (håndskrift, deling, mobilapp, Canvas-integrasjon og tutor-chat) viser at dere har tenkt bevisst på avgrensning. Dere er også ærlige om at fortrinnet er arbeidsflyt og kildehenvisninger, ikke teknologi.

**De viktigste endringene:**

1. Alle suksesskriteriene er forretnings- og pilotmål (≥ 40 % ukentlig aktive, 3–5 % konvertering, ≥ 70 % «better prepared») som ikke kan måles i løpet av emnet. Legg til funksjonelle kriterier som kan bli testtilfeller.
2. «Accounts with freemium limits (monthly free cap, paid upgrade)» står i v1. Ekte betaling gir mye ekstra arbeid og risiko. Ta betalingen ut av v1, og behold eventuelt bare en enkel bruksgrense.
3. Beskriv hvordan appen skal kunne kjøres uten gruppens API-nøkkel til språkmodellen, for eksempel med en testmodus med forhåndslagde svar, slik at sensor kan kjøre den etter README.

## Vanskelighetsgrad og gjennomførbarhet

### Vurdert vanskelighetsgrad

- **Enkel**

**Sammenlignbart med:** 1) AI Study Buddy (enkel). Jippy er i praksis dette forslaget, med elementer fra 8) Foredragsnotater → sammendrag og quizgenerator (enkel). Kildehenvisninger og PDF-lesing gjør det noe mer krevende enn de enkleste variantene.

**Begrunnelse:**

| Faktor | Nivå (lav / middels / høy) | Kommentar |
|---|---|---|
| Domenelogikk – hvor mange og hvor kompliserte regler og beregninger må stemme? | lav | Få regler. Quizretting og «weak topics» er enkel logikk, og spaced repetition er utsatt. |
| Datamodell – antall entiteter og relasjoner mellom dem | middels | Bruker, fag, dokument, sammendrag, flashcard-kortstokk med kort, quiz med spørsmål og svarforsøk. |
| Brukere, roller og innlogging | middels | Én rolle, men kontoer med innlogging. Freemium-grenser gir ekstra logikk. |
| KI-funksjonalitet i appen, f.eks. kall til språkmodell, prompts i koden og håndtering av usikre svar | middels | Tre genereringer (sammendrag, kort og quiz) med kildehenvisning. Kildehenvisningene og håndtering av feil i KI-svar er det mest krevende. |
| Integrasjoner og eksterne tjenester, f.eks. API-er, betaling og e-post | middels | Språkmodell-API. Betaling for «paid upgrade» ville løftet dette til høy, og bør tas ut. |
| Sanntid, samtidighet eller flere brukere som påvirker hverandre | lav | Hver student jobber med sitt eget materiale. |
| Filhåndtering, f.eks. opplasting, PDF-lesing og eksport | middels | Opplasting av PDF og lysbilder. Pålitelig tekstuttrekk fra lysbilder er erfaringsmessig vanskeligere enn det ser ut til. |
| Sikkerhet og personvern | lav | Studentenes egne notater. Kontoer og lagring krever likevel grunnleggende tilgangskontroll. |

**Hva vanskelighetsgraden betyr for dere:**

- _Enkel:_ Et enkelt prosjekt gir stor sjanse for å bli ferdig. Vanskelighetsgraden inngår likevel i vurderingen, så for å nå helt opp må dere vise mer i gjennomføringen. Det betyr særlig et gjennomarbeidet design, grundig testing, en tydelig dokumentert prosess og en README som virker. Kildehenvisningene («each wrong answer points back to the right passage») og oversikten over svake tema er gode steder å vise kvalitet.

### Gjennomførbarhet med BMAD og Claude Code

Dere skal planlegge med BMAD (product brief → PRD → arkitektur → epics og stories) og implementere med Claude Code. Vurderingen under tar hensyn til at det må være tid til hele denne flyten, og til testing, retting og README til slutt.

| Spørsmål | Vurdering (OK / risiko / stor risiko) | Kommentar |
|---|---|---|
| **Tid og omfang** – kan v1 realistisk bli ferdig og stabil i løpet av semesteret, med tid til flere iterasjoner? | OK | Fem punkter i v1 er overkommelig. Det forutsetter at betaling tas ut. |
| **BMAD-flyten** – er briefen konkret nok til at PRD, arkitektur og stories kan lages uten store hull, og blir det overkommelig mange stories? | OK | Løsning, brukere og avgrensning er konkrete nok. Dere har ikke laget PRD ennå, så det er god tid til å rette suksesskriteriene først. |
| **Egnet for Claude Code** – bruker løsningen en vanlig, godt dokumentert teknologistakk som Claude Code håndterer godt, eller krever den nisjeteknologi, spesialmaskinvare eller mye manuell konfigurasjon? | OK | En vanlig webapp med filopplasting og LLM-kall er godt egnet. Teknologien er bevisst utsatt til arkitekturen, og det er greit. |
| **Kontroll på KI-ens arbeid** – kan gruppen selv avgjøre om koden gjør det riktige? Krever domenet kunnskap gruppen ikke har, f.eks. avanserte beregninger eller fagregler, så er det vanskelig å kvalitetssikre. | risiko | Koden kan dere kontrollere, men kvaliteten på genererte kort og spørsmål er vanskeligere. Bruk testdokumenter fra et fag dere kjenner (for eksempel IBE160) og vurder om svarene og kildehenvisningene stemmer. |
| **Testbarhet** – finnes det tydelige regler og forventede resultater som tester kan skrives mot? | risiko | Logikk som quizretting, redigering av kort og bruksgrenser kan testes. KI-genereringen må testes med faste mock-svar, og det må planlegges. |
| **Kjørbar for sensor** – kan appen kjøres lokalt etter README, uten gruppens nøkler, betalte kontoer eller egen infrastruktur? | risiko | Briefen sier ikke noe om dette. Uten testmodus trenger sensor en egen API-nøkkel. |
| **Avhengigheter og kostnader** – krever løsningen betalte API-er, f.eks. språkmodeller, og finnes det en plan for kostnad, testmodus eller mock-data? | risiko | Dere nevner «AI cost per active user» som forretningsmål, men ikke kostnadene under utviklingen. Velg en modell med gratisnivå eller lav pris, og lag en mock-modus. |

**Konklusjon om gjennomførbarhet:**

- **Gjennomførbart med justert omfang.** Se forslagene under.

**Forslag til justering av omfang eller vanskelighetsgrad:**

1. Erstatt «paid upgrade» i v1 med en enkel, konfigurerbar bruksgrense (for eksempel maks antall genereringer per måned) uten betaling. Flytt betaling til «OUT».
2. Når kjerneflyten virker, kan dere løfte prosjektet med én tydelig utvidelse, for eksempel enkel spaced repetition (Leitner-bokser) eller oversikten over svake tema. Reglene der er tydelige og kan testes godt.

## Hvorfor product brief er viktig for mappen

Product brief er utgangspunktet for PRD, arkitektur, stories og til slutt koden. Del 1 av mappen vurderes blant annet på om sensor kan følge en sporbar vei fra plan til ferdig app. Den vurderes også på om appen gjør det dere har beskrevet, om den er testet, om den er godt designet, og om den kan kjøres etter README. Et uklart, for stort eller for lite brief gjør alt dette vanskeligere senere. Det er mye enklere å rette nå enn sent i semesteret.

## 1. Gjennomgang av briefens deler

| Del av brief | Status | Kommentar |
|---|---|---|
| Executive Summary – er det klart hva appen er, og hvilket problem den løser? | OK | Klart og konkret: fra eget materiale til sammendrag, flashcards og quiz på få minutter. |
| The Problem – er problemet konkret, med reelle situasjoner og brukere? | OK | Gode eksempler på dagens løsninger (Anki, Quizlet, chatbot, andres kortstokker) og hva de koster. |
| The Solution – beskriver løsningen brukeropplevelsen, ikke bare teknologi? | OK | Beskriver hva som endres for brukeren («an evening spent making flashcards becomes 10 minutes»), og utsetter teknologivalgene bevisst. |
| What Makes This Different – er vurderingen ærlig og realistisk? | OK | Tabellen er nyttig, og «Honest advantage» er realistisk. |
| Who This Serves – er primærbrukerne tydelige, og vet vi hva de trenger? | OK | Én tydelig primærbruker med konkrete behov (fart, tillit, eget fag og rotete notater). |
| Success Criteria – kan kriteriene faktisk sjekkes eller testes? | Endre | Alle fire signalene krever pilot, spørreundersøkelse eller betalende brukere. Legg til kriterier som «en student kan laste opp en PDF og få et sammendrag, minst 10 redigerbare kort og en quiz», «hvert quizspørsmål viser hvilken side det kommer fra», «student A kan ikke se materialet til student B» og «appen gir en forståelig feilmelding når filen ikke kan leses». |
| Scope – er det klart hva som er med i første versjon, og hva som ikke er det? | Juster | Tydelig delt i IN og OUT. Ta betaling ut av punkt 5, og presiser hvilke filtyper som støttes (for eksempel PDF og tekst, ikke PowerPoint). |
| Vision – henger visjonen sammen med resten uten å blåse opp omfanget? | OK | Fint delt i NOW, NEXT og 2–3 år, uten at visjonen trekker funksjoner inn i v1. |

## 2. Utgangspunkt for del 1 av mappen

Punktene følger kriteriene i sensorveiledningen for del 1. Vektene i parentes viser hvor mye hvert kriterium teller i del 1.

| Kriterium i del 1 | Hva briefen bør legge til rette for | Status | Kommentar |
|---|---|---|---|
| **1. Prosess og KI-styring** (30 %) | Brief som er presis nok til at PRD og stories kan bygges direkte på den, slik at krav kan spores fra brief til kode. | Juster | Briefen er presis, men repoet har foreløpig bare briefen og én commit. Legg briefen i BMAD-strukturen, kom i gang med PRD, og commit jevnlig, slik at prosessen blir synlig. |
| **2. Funksjonalitet og omfang** (20 %) | Realistisk omfang for gruppen og semesteret: en tydelig kjerneflyt som kan bli ferdig og stabil, og nok innhold til å vise reell funksjonalitet. | OK | Kjerneflyten «upload → study set → practice → review weak spots» er tydelig og realistisk. |
| **3. Kvalitetssikring og testing** (15 %) | Suksesskriterier og funksjoner som er konkrete nok til å bli testtilfeller. | Endre | Uten funksjonelle suksesskriterier mangler grunnlaget for testtilfeller. Se forslagene over. |
| **4. Design og brukeropplevelse** (10 %) | Tydelige brukere og brukssituasjoner som designet kan bygges rundt, gjerne med de viktigste skjermbildene eller flytene skissert. | OK | Mobilvennlig web og bruk «on the bus» gir tydelige føringer for designet. Skisser gjerne opplasting, kortgjennomgang og quizresultat. |
| **5. Kodekvalitet og arkitektur** (10 %) | Teknologivalg som er begrunnet og ikke mer komplekse enn appen trenger. | OK | Valgene er bevisst utsatt til arkitekturen. Hold stakken enkel. |
| **6. README og kjørbarhet** (10 %) | Løsning som andre kan kjøre lokalt uten betalte kontoer, og uten tilgang til gruppens egne tjenester og nøkler. | Endre | Beskriv en plan for kjøring uten deres LLM-nøkkel (testmodus eller mock-svar) og uten betalingstjeneste. |
| **7. Ryddighet i repoet** (5 %) | En plan for hvor hemmeligheter, testdata og dokumentasjon skal ligge. | Juster | Bestem tidlig hvor test-PDF-er og eksempeldata skal ligge, og hold API-nøkler i `.env` som ikke committes. |

## 3. Neste steg for gruppen

1. Skriv om Success Criteria med 5–8 funksjonelle kriterier som kan testes, og flytt pilotmålene til en egen del for senere validering.
2. Ta betaling ut av v1, og legg inn en kort plan for LLM-kostnad og testmodus, slik at sensor kan kjøre appen uten deres nøkkel.
3. Flytt briefen inn i BMAD-strukturen (for eksempel `_bmad-output/planning-artifacts/briefs/`) og gå videre til PRD.

Oppdater product brief i repoet når dere har gjort endringene, slik at historikken viser hvordan planen utviklet seg. Det er en del av prosessen sensor ser etter.
