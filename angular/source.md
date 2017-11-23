# Štruktúra projektu
### Module
- Časť tvojej appky, ktorá zoskupuje komponenty, direktívy, pipy a servisy do samostatného celku. 
- Tvoje dielo je napokon spojené z viacerých modulov. 
- Tip: Zamysli sa, či naozaj potrebuješ univerzálny modul kvôli jedinej funkcii. 
### Router
- Nasmeruj požiadavku klienta tam, kam potrebuješ. 
- Nedaj Angularu vydýchnuť a využívaj všetky metódy ako je napríklad canActivate(), canDeactivate() alebo canLoad(), atď.
### Direktíva
- Výkonáva zmeny vzhľadu, správania sa, alebo pozície DOM elementu. 
- Pre pokoj v tíme, kde môžeš použiť komponent, nepoužívaj direktívu.
### Šablóny
- Zabezpečujú vzhľad tvojho projektu. 
- Tipy: Nie je hanba používať základné komponenty, direktívy a rekurzívne šablóny.  
-  Ak chceš aby tvoja appka bola rýchlejšia, tak použi konštrukciu trackBy. 
- Nezahlť sa “if-mi”, ale použi *ngIf-else konštrukciu, ktorá sprehľadňuje a zrýchľuje generovanie DOMka. 

### Komponent
- Úžasná fúzia šablóny s direktívou, ktorú navyše môžeš vo svojom projekte používať opakovane.  
- Tip: V bart.sk sme si rozdelili komponenty na také, ktoré nezabezpečujú žiadnu logiku (hlúpe) a také, ktoré sú mozgom celej operácie (múdre).

### Pipy [paɪps]
- Angular nemá so sebou Pipi dlhú pančuchu. Má však nadupané funkcie podobné tým z Linuxu. 
- "Nezabi" si aplikáciu hneď na začiatku. Rob veci jednoduchšie.

```html
<p>The hero's birthday is {{ birthday | date:"dd.MM.yyyy" }} </p>
```
###Servis
- Nie je v tom úplne sám, ale je single...ton. 
- Je dostupný pre celý modul, preto je vhodný napríklad na vykonávanie komunikácie s API alebo na uchovanie dočasných dát. 
- Komponenty nechaj vykonávať ich prácu a logiku presuň práve sem.

# Základné zásady a nástroje

### HTTP Servis
- V prípade Angular appky potrebuješ komunikovať s API. Pomôže ti s tým HTTP Servis.
- Tip:  Často pracujeme v kóde priamo s JSON formátom, odpoveď od HTTP API si radšej pretransformuj do podoby entity. 

### Change detection
- Sleduj každú change detection vykonanú nad komponentami.

### Preklady
- Môžu ti poriadne zamotať hlavu. 
- Preto mysli na preklady hneď od začiatku. 
- Pomoc nájdeš na: bart.sk/angular-i18n

### Autentifikácia
- Zabráň nezvaným hosťom aby narušili pohodu tvojej appky. 
- Router je miesto, na ktorom môžeš autentifikovať používateľov. 
- Viac nájdeš na bart.sk/angular-guards

### Testy
- E2E či Unit, každý o tom hovorí, nikto to nerobí. Zmeň to!

### Refaktoring
- Pravidelne sa staraj o svoj kód. 
- Pokús sa odstrániť čo najviac duplicít, udržuj aktuálne závislosti. 
- Mysli aj na to, že každým tvojim riadkom vzrastá technologický dlh projektu. Nedovoľ mu narásť.

### Linter
-Nástroj na overenie nesprávnej syntaxe kódu je viac než užitočný. 
- Použiť môžeš napríklad: bart.sk/tslint, bart.sk/codelyzer
 
# Typescript
### Využi ho naplno.
- Používaj všetky možnosti ktoré Typescript ponúka. 
- Rozhrania, triedy, generické funkcie by sa mali stať bežnou súčasťou tvojho projektu.

### Prepni sa do striktného módu
- Ak sa chceš vo svojom projekte dobre orientovať, vyhýbaj sa používaniu “any” alebo automatickému typovaniu. 
- Ak chceš byť v prvej lige použi: 
```sh
$ compiler --noImplicitAny=true ...
```

### DefinitelyTyped
- Ak má byť tvoje striktné typovanie skutočne striktné, stiahni si aktuálnu zbierku pre väčšinu knižníc z: bart.sk/definitelyTyped

### Polyfill
- Nezabudni na podporu starších prehliadačov. 
- Pomôže ti: bart.sk/corejs
 
### Externé knižnice
- Pre import modulov používaj úplné cesty. 
- Ak potrebuješ iba zopár metód nenačítaj celú knižnicu. 
```ts
import { Observable } from 'rxjs/Observable';
````

# Optimalizácia
### ProdMode
- Keď budeš ready a tvoja appka pôjde do produkcie, nezabudni na prodMode(), užitočnú funkciu, ktorá vypne všetko, čo ostrá verzia kódu nepotrebuje.
 
```ts
import { enableProdMode } from '@angular/core';
enableProdMode();
```

### Výkon
- Mysli na výkon. 
- Používaj lazy loading, vyhni sa iterátorom v get metódach (getteroch), pipách, ngClass či inputoch komponentov.

### Lazy loading
- Skvelá optimalizácia. 
- Všetko, čo aplikácia potrebuje pre svoj chod si načíta postupne. 

### Server-side rendering
- Efektívne zrýchľuje načítanie stránky. 
Napriek tomu, že použiješ Angular, tvoj projekt bude rovnako rýchly ako statický web. 
Veľkou výhodou je zároveň, že ti umožní robiť SEO. 

### AOT
- AOT predkompiluje moduly, komponenty a vykoná tree-shaking. 
- Odhadom táto operácia zmenší tvoj kód na polovicu. 

### Uglify
- Prehliadaču nezáleží na tom, ako veľmi škaredý kód číta. 
- Uglify zmení názvy, odstráni medzery, čím zredukuje veľkosť kódu. 
- Čo viac si môžeme želať? - Tureckú kávu, čerstvo pomletú. bart.sk/uglifyjs

# Nástroje
 
###Angular-CLI
- Angular pre teba pripravil nástroj, s ktorým môžeš “vybuildovať” aplikáciu na produkciu alebo si pomôcť pri vytváraní šablón a komponentov. 
- Všetko čo dokáže nájdeš na: bart.sk/cli-angular

### Webpack
- Pri správnom nastavení ti dokáže zefektívniť a sprehľadniť celý proces vývoja aplikácie. 

### Node
- V dnešnej dobe sa človek bez NodeJS a balíčkového nástroja ako je napríklad npm alebo yarn vo svete JavaScriptu nezaobíde.

 
# Knižnice, ktoré chceš mať
### RXJS
- Angular využíva práve túto knižnicu. 
- Skús to aj ty a zabudni na callback funkcie. 
bart.sk/rxjs

### NGRX
- Súbor reaktívnych nástrojov pre Angular. 
- V bart.sk najčastejšie využívame ngrx/store, ktorý je užitočný pri komunikácií medzi komponentmi, ale aj pri sledovaní stavu entít v úložisku.
bart.sk/ngrx 

### MomentJS
- Ak potrebuješ lepšie pracovať s časom použi MomentJS. 
bart.sk/momentjs

### Lodash
- Súbor užitočných funkcií, ktoré ti môžu uľahčiť vývoj. 
- Zbytočne budeš vymýšľať teplú vodu. Ak však potrebuješ iba niektorú z funkcii neimportuj celý balíček. 
bart.sk/loadash