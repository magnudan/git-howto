# Begreper
*   HEAD peker på den aktive branchen.
*   origin er github, og branchene i github vil bli representert som origin/<...>, der <...> er navnet til branchen.
*   Å committe betyr at man lagrer endringene lokalt. Ingen endringer blir gjort i github før man pusher-

# How to git

## For å få oversikt
```
git status
```

Gir en oversikt over filer som er endret, added og committed.
```
git branch
```

Lister opp alle branchene lokalt på egen PC. Hvis man legger til -a ser man alle branches i hele prosjektet.
```
git log --all --decorate --oneline --graph
```

Gir en enkel oversiktsgraf av prosjektet: Alle committer, hvordan prosjektet er branchet, hvor branchene er.

## Når man vil oppdatere fra github
```
git fetch origin
```

Henter oppdateringer fra github, men endrer ingen ting lokalt. På denne måten velger man selv hvilke branches man merger inn lokalt. Detaljer om merging kommer under.

### Eventuelt kan man oppdatere og merge samtidig. Her må man være litt forsiktigere enn når man fetcher.
```
git pull origin
```

## Når man har lagret filene, og vil committe:
```
git add <...>
```

I stedet for <...> kan man skrive -A eller . for å legge til alle endrede filer, eller filename.extension for å legge til enkeltfiler.
```
git commit -m "<...>"
```

I stedet for <...> skriver man en kort beskjed om hva man har endret.


## Når man vil lage en ny branch
```
git branch <...>
```

I stedet for <...> skriver man navnet på branchen man vil opprette.

### Eventuelt
```
git checkout -b <...>
```

For å opprette og bytte til branchen med en gang.


## Når man vil bytte branch
```
git checkout <...>
```

Der ... er en eksisterende branch, for eksempel master.

## Når man vil merge to brancher
```
git merge <...>
```

Da vil man merge branchen man er i inn i <...>. Altså hvis man skal merge en branch inn i master må man være i master og skrive git merge <...>.
Når to brancher merges, kan dette skje på to forskjellige måter: Fast-forward og Recursive.
Fast-forward vil skje når det er en rett linje mellom branchene. Hvis branchene er i parallell vil det bli en Recursive merge.
Det kan være at man får opp en ny side i kommandolinja, der man kan skrive inn en kommentar til mergingen.
Vanligvis er ikke dette noe poeng, og det er bare å lagre og lukke vinduet med kommandoene som står nederst.

Hvis man prøver å merge to filer der det har vært *endringer* på de samme stedene, vil det resultere i en conflict. Hvis man her åpner filen det gjelder, vil man på det aktuelle stedet se noe linende:
```
<<<<<<<<<<<<<<<< HEAD

kode kode kode

kode kode kode

================

kode kode kode

kode kode kode

>>>>>>>>>>>>>>>> branch-name
```

Her må man ta et valg angående hvilken versjon man vil bruke, eller om man vil bruke en kombinasjon. Når konflikten er løst, fjerner man alle <, >; =, "HEAD" og "branch-name", lagrer og commiter filen på nytt.

Det er også mulig å avbryte mergingen med
```
git merge --abort
```

## Når man vil slette en branch
```
git branch -d <...>
```

Der <...> er branchen man vil slette.

## Når man vil laste filene med endringer opp til github
```
git fetch
```

For å forsikre seg om at man har de nyeste versjonene, må man laste ned før man laster opp.
```
git push origin <...>
```

Der <...&#62 er den aktuelle branchen i github man ønsker å oppdatere. Vær veldig forsiktige med å pushe til origin master.

# Forkaste endringer

## Når man vil endre en fil tilbake til sånn den var ved forrige commit
```
git checkout -- <...>
```

Der <...&#62 er filnavnet på den aktuelle filen. Kommandoen "git checkout -- ." vil endre alle filer tilbake til forrige commit.

Man vil altså forkaste alle endringer man har gjort i aktuelle filer siden forrige commit.

## Når har brukt git add, og vil gå tilbake
```
git reset
```

Filene vil nå være like det de var før git add. Dersom man ønsker å også forkaste endringene siden forrige commit, kan man legge til kommandoen --hard:
```
git reset --hard
```

## Når man har committed, og vil gå tilbake
```
git reset HEAD~
```

Med denne kommandoen vil man beholde alle endringer i filer siden forrige commit, men ingen filer er addet. Også her vil kommandoen --hard forkaste endringene siden forrige commit:
```
git reset --hard HEAD~
```

**OBS: Hver gang man kjører denne kommandoen vil man gå tilbake én commit!**

For å komme seg tilbake til der man var, kan man kjøre git pull.

# Kilder
[Video om branching og merging](https://www.youtube.com/watch?v=FyAAIHHClqI)

[Video om Git remotes](https://www.youtube.com/watch?v=Gg4bLk8cGNo)

[How to undo (almost) anything with Git](https://github.blog/2015-06-08-how-to-undo-almost-anything-with-git/)
