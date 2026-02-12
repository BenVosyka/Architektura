# Poznámky - Počítačová architektura

## Strana 18

**- přenáší data během uměřív - 2x i to ja periféří**  
**- ne s obérnící od uvění obírážd a CPU**

### REŽIMY DMA:

#### 1. **KRADENÝ CIKL**
  • **DMA žujehlední 1 cyklus obětnice a provede 1 ukrutérání přens**  
  • **CPU se a DMA střídají**  
  • **omezí dopad na CPU**

#### 2. **BLOKOVÝ REŽIM (Bunst)**
  • **DMA oboudní obětnici on delší dobu**  
  • **CPU je pozastavon**  
  • **rychlejší pro velmi přenos velkých kloků dat**  
  → **obondí obětnici a práčí jšín 07 po přenru**

---

## Strana 19

## PŘERUŠENÍ - IRQ (interrupt request)

**- ! Co jš potřeba?:**

  • **ko přávanými by CPU muselo uvětělé kontrolovat navření (+ potét ex),**  
    **uší ja nejvělčíná** → **práčo jako navření volá utyněl, když uťco potřebuje**

- **přávanými ja uvynál, kč. navření přenší CPU a provrání (podan tč ho služba), že je připrava pro práče vyšy, debově dáta, kontrolu, čavono**

- **umími k uytletávání propovou a CPU z používáři na obéhu kdo od většých navření**

- **uvgě uěrovou přiovku (nižání → vyšání)**

  **RADIČ PŘERUŠENÍ (IRQ controller)** - **přijímá přiovňový od navření, uměňje přiovku, přídovaní informaci CPU**

  • **dnes se používá APIC (advanced plogrammable interrupt controller) uvázňuje více IRQ čínů, nebému IRQ více navření**

---

## CRILOVA PŘERUŠENÍ

  a) **navržení vyslov přiovňoví a přírením**  
  ii) **čodič přírením rychle nezprovilějšší přiovňoví a vyšle signal NMI do dat. registru nejvja syn přírením a uvěnutél do dat. sektora**

---

## Strana 20

iii) **CPU dokončí instrukcí, ujáu INTA, kterýjmu navržení dokončuje kteří navření čádá a přánení**  
iv) **čodíč onemí do dat. obětnice čísty kopu přánanění**

v) **CPU uloží obtah uvják nejvíštší on stakč**

vi) **CPU uospovuje typ přírením - t.contrúující naříjání se on dvr. používá, kle je podle pokorní přínení (ndes) - jok obslumuvejší uvětor**

[DIAGRAM: Schéma s INTR, INTA, CPU, VEKTOR PŘERUŠENÍ, STACK, OBLÍBANÁ RUTINA]

---

## TYPY PŘERUŠENÍ:

### 1. **HW PŘERUŠENÍ**
  • **přerušní a periférií**  
  • **klížívníčí, myši, disk**  
  • **ovlují řodiče**

### 2. **SW PŘERUŠENÍ**
  • **vyvolání dostávají programem**  
  • **kopřítý nebo sluzád OS**

### 3. **VNITŘNÍ PŘERUŠENÍ**
  • **děljení 0**  
  • **pravání odkary paměti**  
  • **chyby instrukce**

---

## Strana 21

## OBSLUHA PŘERUŠENÍ II. (DETAILED)

### 1. **UZNK UDÁLOSTÍ**
  • **vč. dokončí se dřív a uděla navrátél obfcha klíštěm**  
  • **navírením ujáu utyněl IRQ do řodiče přánení (APIC)**

### 2. **RADIČ PŘERUŠENÍ (APIC)**
  • **APIC:**
    - a **přijme přiovňoví**  
    - a **vyhodnční přiovitu** (> a čavno? > klíčovníči)  
    - a **pošle je CPU připrovce, počle CPU utyněl:**
      • **jo do přirením číslo X**

### 3. **REAKCE CPU**
  • **obnovní současovou instrukce**  
  • **uloží datu přírením (hořízing uvp. uveumél vbon)**  
  • **automuticly:**  
    - **uloží sbov svého na uaprobá:**  
      - **program counter (klerjam 64)**  
      - **registry**  
      - **obnoví registr**  
  • **přijme x do lével mode (chráning ovím)**

→ **podle uví dotél CPU koduvatoví**

---

## Strana 22

### 4. **URČENÍ OBSLUZMÉ RUTINY**

  • **CPU:**  
    - a **pouze za věktor přínění (číslo přivúšténé)**  
    - **"nahlídne do tabully vektorů (IDT)**  
    - a **ujtští adresu ISR - interrupt service routinu**  
      Co **specielíční fco v jádře OS**

### 5. **SPUŠTĚNÍ ISR**
  
  • **CPU skočí na odkazu ISR,**  
    **svíče 7y konjená kód obslují přirnštem**  
    
    **ISR typicky:**  
      • **ujtští, kč. navřámi přirnšení uvpúlo**  
      • **přečte sbov navřími**  
      • **obnoví přínění**  
      • **uloží data (p5 ovuá a klávesuníci)**  
      • **proběhná celkují stavus (ovbude výjaš čího)**

---

## Strana 23

### 6. **SKALOVÁNÍ 1. OS (scheduler)**

  • **projují se a multi-taskingem:**  
    - **poklad ja přínění čvouněš:**  
      - **OS uvětí a scheduler,**  
        - **uněří se uvlodovoá:**  
          - **pokarovuoná se ulejšem větání vloho utyňu novau**

→ **přennášějí multitasking**

---

### 7. **NÁVRAT Z PŘERUŠENÍ**

**Po dokončení ISR:**

  a) **OS povede uvěténu IRET / RETI**  
  
b) **CPU:**  
    - **obnoví uložení registry**  
    - **obnoví program counter**  
    - **počle do user mode**  
  
c) **provram pokračuje přesně tam, kde byl přerušem (jako od učší jšná učálem - podle uvlodovoší scheduler)**

---

## Strana 24

## 6. PROCESORY

### CO TO JE PROCESOR?

**- výkonný automat, kč.:**  
  • **včetá instrukci a paměti**  
  • **dekoduje jé**  
  • **vykonává jé (práčí, čítní, připravní skoky)**  
  • **as ůčdá dán časuná obítá výsledtá**

---

## TYPY:

• **MCU** = **mikrokontrolen**  
  - **levnovnú**  
  - **1 nevjářjčků časuvú**

• **CPU**  
  - **kloniký procesot**  
  - **výkonný, univerzální**  
  - **ovládáuj většní DM1, chipsét, periférie**

• **DSP** - **digitál processor**  
  - **optimalisovny pro matematické a výpočty (audíár filtry, občem)**

• **NPU** - **network processor**  
  - **sítoví / specializovaný procesory (routery, switches)**

• **GPU**  
  - **uměvění parelělní, navjedétá a vellkoná výpočty**

• **APU** - **CPU + GPU dohromady v 1 občem**

---

## Strana 25

## CISC

• **všíhý uodcn složítá instrukcí, on kódou optraší jé instrukce**

• **většíma instrukcí můlé dobu truší**

• **ARM**

---

**vs.**

## RISC

• **nedokovaní instrukcí uvdců, jédnodušší**

• **instrukcí fyzují použují dlouku, více 1 koló (5ikloá)**

• **MIPS**

• **instrukce se výkomvají rychlý (5ran HW implementový v uv)**

---

## ŠÍŘKA OPERANDŮ

• **4,8 bil (procesy, a uvdusný, kalkulačky**

• **16 bil (mikroby**

• **32,64 bit**

---

## Strana 26

## PARAMETRY

i) **Rychlost - frekvenco jádru (uvžími v kla / Gka), kč. uvěční práč výkle, více pocsuné**  
   - **vyšší frekvenco → více**
  
ii) **Rychlouse navpběle frekvenco procesoru ablémíce**

iii) **MIPS - milion instrukción per second**

iv) **FLOPS - floating point operations per second**

v) **IDP - koybový výkon procesoru, POJ během ovučí milnkovat**

vi) **Cpočká - počká on uvklé obuvš Pro CPU, uvužuje instalaci prosovou**

vii) **počká fyzických jáder procesoru a výjel výjálení uvpjé**

viii) **výklenté cache - více obymi**

---

## ZAKL. ČASTI PROCESOU

### ŘADIČE (CONTROL UNIT-CU)

**- "diriguje procesoru"**

**- řídí pohodu a stov jsém provedou instrukce, skláduje ja**

**- ovčéná co a pomčá**

**- provuje řídicí uvynělo pro ALU, nejvých, paměti, obérnící**

---

## Strana 27

## CO SE DĚJE PO ZAPNUTÍ?

### 1) NAČÍST CPU

**- Plogram counter / IP/RIP (instruction pointer) se navtyním defualční (první domu adresy)** → **z umďjší všímíčka firmware jdoupou x**

**- u x86 je to adresa, kde je BIOS / UEFI firmware, čítní se jší uvzel uvztov**

**kombdělí BIOS**  
Co - **basic input / output system**  
  • **uvědí se jeko 1 po uvpnutí, provedá kontrolu HW, ovítulísuje komponénly a připraví začnu OS**

---

### 2) NAČÍST INSTRUKCE JE OPČÍN NA ADRESNÉ ČÍSŤNÍCÍ

**- obsal Ix se počle na obéresovou ubímičin do považování kontrolem**

---

### 3) NAČÍTÁNÍ INSTRUKCE Z PAMĚTI (FETCH)

**- poméť podlé odčery poší obsal bus, kubo obsal ja obcyjášé instrukce**

**- instrukce se uloží do IR (instruction register)**

---

### 4) INKRIMENTACE PC

**- jakmalé ja instrukce uvčítena Pc se inkrumanjé kudí 0 1, uko a dalša instrukcí (u děle rozuovú délce)**
  Co **PC uná udrújé na další instrukci**

---

### 5) DEKODOVÁNÍ INSTRUKCE → DECODE

**- čodíč ovčazuje obsal IR, ujtští:**

---

## Strana 28

• **jaky operaci se má provedá**  
• **obkal voliť operandy**  
• **kam uložiť výsledek**

**- podle tcho:**  
  • **generuje řídicí signály**  
  • **ovládá výběr registry**  
  • **rovzoší registry**  
  • **ukláduje ALU / FPU / rozviť**

---

→ **! Čodíč ja uvětí problění přísou uvěčev na větších odvsu, uvětí instrukcí a paméti do registru instrukce, dekoduje ja a povel kečnéční uvyněů uvěčí časový kla, uvgístďu a uvěčev**

---

[DIAGRAM: Schéma s VECTOR KOMBINÝ, registry v instrukcí, registry v instrukce, instrukcí kontrolou, řídicí signály a ALU s časovým přikovány]

---

### 6) VYKONÁNÍ INSTRUKCE → EXECUTE

**- ALU provdá operaci**

**- připadá se čte / zapisuje paměť**

**- výsledek se uloží do registru**

**- cyclus se opakuje od FETCH**

---

## Strana 29

## ALU - aritmetická-logické jednotka

**- čte z RAM, ukládují a výkonává operace**

**- uvčením kloá - uvčovuvání operandy získáni na 2 vstupy, výk as přidušíní 1 výstupem**

**- získána - registry po uvíténou dat**

**- ex. přídání - obrovnů registry, kontroluje jšní časňší a uvauje podlé uťjí Co čeni, todi,...**

**- částí CPU / Lč:**  
  • **uvísčení**  
  • **porovnání**  
  • **provádí logické operace**

**- CO PO ALU VSTUPUJE:**  
  • **operuje 4 a B (2x register)**  
  • **řídicí uvynály časičů** → **joku operni provenť (ADD, SUB, AND, OR)**

**- CO ALU DĚLÁ UVNITŘ:**  
  • **uuětě jsou odosvuuší, logické hraden multyplexery**  
  • **podle řídicích uvynělo se výkon uvíčení operace, ovende as výjání**

**- CO Z ALU VYCHÁZÍ?:**  
  • **z dědů ovenes** → **uvytší se do uvětného uvgistru, nebo do paměti:**  
    - **příčuoxy (flags): Z - uxus** → **výsledejé 0    f - uvgn** → **uměnčku**  
      **C - carry** → **přenos    0 - overflow** → **přetečení**

---

## Strana 30

## PRINCIP ČINNOSTI ALU

**- každá částečna on uložedá jo struktčin OP**  
**- pouze vstupuvají - uvěchodusovnosti instrukción, který uví síťání uvězí 3 instrukce - odčč 1 odčč 2, odvění uvzúledu**

**- 1 uvéčovu se instrukci uvěle uvvoř a 0P on 2 uvtupy 01, blede**  
**- výjá se uvnění do občíadčin a tou další instrukci do 0P**

[DIAGRAM: Schéma s FLAGS, výsledná, OP ALGO, OUT s různými vstupními a výstupními signály]

---

### 6) VYKONÁNÍ INSTRUKCE → EXECUTE

**- ALU provdá operaci**

**- připadá se čte / zapisuje paměť**

**- výsledek se uloží do registru**

**- cyclus se opakuje od FETCH**

---

## Strana 31

## INSTRUKCE

i) **příčením - uvní RAM a registry**  
ii) **výčtu-ubity**  
iii) **logické**  
iv) **školoví**  
v) **ovládne výjáučn**  
vi) **ovkání - řídicí, uvěení**

---

## ARCHITEKTURY

**- stavební funkce a 0d. CPU**

### SKALÁRNÍ ARCHITEKTURA

**- býlem 1 další dokončuje 1 instrukci**  
**- příklady: něktoré větbní ovazových instrukce**  
**- FPU, CACHE**

---

### SUPERSCALAR

**- více ALU, uvělící výkonější, více instrukce se žalí**  
**- paralélní složká**  
**- 2x CACHE:** → **L1 - instrukción a datová**  
  **→ L2 - uvýděleví kornízon uvní OP a CPU**

---

## Strana 32

## SIMD - single instruction, multiple data

**- na uvíčých jahrných uvíčeují více dat**  
**- větají 1 ja uvíšku** → **uvjé S (44,3) = (5,45,11)**  
**- 64, 128 bit registry**

---

## PIPELINING

**- procesot každití upcovovní instrukce do kroků**  
**- příčením k pravnů výjál:**  
  Co **uohruž instrukce A se výkonává, instrukce B se dekoduja a instrukce C se uvětá**

---

### FAZE:

i) **uvjačiť odbery instrukce**  
ii) **dekóni valevy a instrukce**  
iii) **dekočování instrukci - nakovaní obvarovlačíní ukosdelou**  
iv) **uvjačiť v ALU**  
v) **uvjnií výsledu**

---

## HYPERTHREADING

**- 1 fyzická jádro uvčovuvání více větání (konvu se julu 2 logické jádru)**  
**- ukážo se obáduji a kla on CPU**  
**- uvíčen více včání**  
**- ukážo uvětání uvěkázi programu**

**- Pluvají:**  
  • **kbý včán A čké (josí on paměť)**  
  • **vádna B uňž uvytí uvgisťry vysutční včkuý**

**- uville ALU a další částá jádru**  
**dupkóuje: uvgistry a skovy ubý 2 včán uněle uvčišíť koubáš (do se dál přípuvení usmů ukášát do praštá)**

→ **uvědovo a Intl Quick**

---

## Strana 33

## CACHE PAMĚTI

**- RAD je uvbdělejší, ukáštající (uvozvuni) instrukce obč. 2-3 výkony**

### PROC EXISTUJE:

**- RAD je uvěším pomalý vs CPU a kdo uvčle to CPU uvčičí čkoá "cache deti": uvji on CPU uví doý uvéte všký → instrukce a data**

**- příčuoxy:**  
  • **Lokalita v části do, as používil uvížši, uvžjímě**  
  • **Lokalita v prostoru: jo u ji klatší, busto uvěsněši**

---

### L1 CACHE

**- nejrující (desítky kB), včinú uvměnčici CPU, ubytější rychlá**  
**- účé se on instrukción a datovou** → **uvládání právě upcovovných instrukce**

---

## Strana 34

## L2,L3 CACHE

**- upomlejší, vyšší kapacity (jednotky MB)**  
**- v povathn uvčla a jádrem (oddšleno)**  
**- duto a instrukce kč CPU ubmédti uvpúšičen, ulle usmění kude**

---

## Strana 35

## SBĚRNICE

### CO TO TO SBĚRNICE:

**- ubérnície ja uvědou komunikační cesta, po kč uví:**  
  • **CPV**  
  • **paměť**  
  • **kovčiče**  
  • **periférie**

**vyšínují duta a řídicí informaci**

---

### PARAMETRY:

**- příčování rychlost - z kký - kortoviČ a šířka obérnící**

**DRUHY SBERNIC - práč paralélních uvěličeš, uňční šířka - uví dat na cyklos**

**FREQUENCY SYSTEM RMIOSCI - količích uměí či ja první datu**

**PROPUSTNOST - kolitů uvěč uví om sbc, výpočtenú - šířka x frekvenco**

---

### TOP SEZD

**TOPOL DIOVO PRODUŠENÍ IRE** → **obsahů 188 (44 biš) - uměžit všé dat se uvění větivou pakésová uvěři občud se čtu a kou na uvjuvají čúční a stavou - říární číslo výpočty**

**TOPOL POSLU VEDUC** → **čolovacú (1 bá) - duta jdou po 1 uvdičeš, vydší frekvenco předěcíš (32-4B) - více uvéčéší, uvi dat uvěnčení**

**TOPOL URCU PROCID** → **pobobněni-uvgla** → **domazničeší-duyln**

**TOPOL SYNCHRONOUSE PROCUN** → **uvyndronní** → **uvyndronní**

**TOPOL MMOJCEM PA CRON CIA IIIDY** → **lelalvani - uvgíční on uvěél kačiga - PIS CPU, AGD Pčc šířková - uvgtični on uavél kačige - PAL x 8,x 16,x 4 uvgči**

---