# Finálky – Architektura počítačů

---

## TÉMA 1: Úvod (Von Neumann, Hardware)

### Otázka 1: Co je základní myšlenka Von Neumannovy architektury?
John von Neumann (1945) stanovil základní principy pro fungování jakéhokoliv počítače:
1. Počítač používá dvojkovou soustavu.
2. Je řízen centrem, které vykonává příkazy dle nějakého programu.
3. Program a data musí být v paměti počítače.
4. Sám je univerzální, ale používá speciální programy.

*(Zdroj: Historie-a-vývoj-počítačů.txt)*

### Otázka 2: Jaké jsou hlavní součásti CPU podle Von Neumanna?
Podle Von Neumannova schématu:
- **ALJ** (Aritmeticko Logická Jednotka) – vybírá z paměti příkazy programu a vykonává je, může z paměti vybírat i další údaje (data) a může do paměti zapisovat.
- **Řadič** – koordinuje činnost celého systému.
- **Paměť** – uchovává program a data.
- **Vstup / Výstup** – komunikace s okolím.

*(Zdroj: Historie-a-vývoj-počítačů.txt)*

### Otázka 3: Jaký je hlavní rozdíl mezi Von Neumannovou a Harvardskou architekturou?
*(Odpověď nebyla nalezena v prezentacích.)*

### Otázka 4: Co umožňuje 64-bitový systém oproti 32-bitovému?
64-bitový systém umožňuje rozšíření instrukční sady o instrukce pro práci s 64-bitovými čísly, implementaci 64-bitových registrů pro uložení instrukcí a dat a zvýšení adresového prostoru operační paměti nad rámec 4 GB (2³² = 4 GB) díky technologii EM64T. Podporuje plně 64-bitové výpočetní jednotky a registry.

*(Zdroj: Architektura procesorů Intel.txt)*

### Otázka 5: Co je virtualizace paměti a k čemu slouží?
Virtuální paměť pracuje nad HW implementací stránkování (převod virtuální na fyzickou adresu). Každý proces má adresář stránek – obsahuje 1024 položek, každá odkazuje na tabulku stránek, ty zase na 4KB stránky ve fyzické paměti. Pokud stránka není platná, vyvolá se chyba stránkování (page fault), kernel zachytí chybu a pokud je stránka odložena ve stránkovacím souboru, nahraje ji do fyzické paměti. Umožňuje každému procesu mít svůj vlastní chráněný adresový prostor.

*(Zdroj: Sprava pameti.txt)*

---

## TÉMA 2: Čipová sada

### Otázka 6: Co je čipová sada (chipset) a k čemu slouží?
Čipová sada (chipset) je hlavní logický integrovaný obvod základní desky. Jeho úkolem je řídit komunikaci mezi procesorem a ostatními zařízeními a obvody. V obvodech čipové sady jsou integrovány řadiče těchto zařízení, které řídí jejich činnost pomocí řídících signálů přenášených po sběrnici. Čipová sada vykonává funkci mostů mezi sběrnicemi.

*(Zdroj: Čipová sada.txt)*

### Otázka 7: Jaké jsou dva hlavní obvody v architektuře mostů?
Dva hlavní obvody jsou:
- **Northbridge (severní most)** – zajišťuje komunikaci mezi procesorem, operační pamětí a grafickým rozhraním.
- **Southbridge (jižní most)** – zajišťuje komunikaci s periferními zařízeními (USB, ATA, Super I/O).

*(Zdroj: Čipová sada.txt)*

### Otázka 8: Co zajišťuje Northbridge?
Northbridge zajišťuje komunikaci mezi procesorem, operační pamětí (obsahuje řadič operační paměti) a grafickým rozhraním (AGP). Zároveň umožňuje spojení procesoru s jižním mostem pomocí 32-bitové PCI sběrnice. Sběrnice mezi procesorem a severním mostem je FSB (Front Side Bus), je obousměrná a má šířku 64 bitů (8 Bajtů).

*(Zdroj: Čipová sada.txt)*

### Otázka 9: Co je FSB a k čemu slouží?
FSB (Front Side Bus) je obousměrná procesorová sběrnice mezi procesorem a severním mostem čipové sady. Šířka FSB je 64 bitů (8 Bajtů). Od základní frekvence této sběrnice se odvíjí taktovací frekvence procesoru, operační paměti, sběrnice grafického rozhraní atd. Po sběrnici FSB se data přenášela obousměrně jak z/do operační paměti, tak k periferiím.

*(Zdroj: Čipová sada.txt)*

### Otázka 10: Jaký je rozdíl mezi QPI a FSB?
QPI (QuickPath Interconnect) je náhrada procesorové sběrnice FSB. U QPI sběrnice je celková kapacita (propustnost) k dispozici pouze pro periferie – moduly operační paměti jsou řízeny řadičem integrovaným v procesoru a nezatěžují QPI. Na rozdíl od FSB, kde se data přenášela obousměrně jak z/do operační paměti tak k periferiím a u víceprocesorových systémů jednotlivé procesory sdílely sběrnici FSB. QPI navíc u víceprocesorových systémů umožňuje vzájemnou přímou komunikaci jednotlivých procesorů.

*(Zdroj: Čipová sada.txt)*

---

## TÉMA 3: Paměti obecně

### Otázka 11: Jaké jsou hlavní 3 druhy pamětí podle pohledu na médium?
1. **Polovodičové** – RAM (SRAM, DRAM), ROM (ROM, PROM, EPROM, EEPROM, Flash ROM)
2. **Paměti s pohyblivou magnetickou vrstvou (PMV)** – HDD, FDD, páskové
3. **Optické** – CD, DVD, BluRay, HD-DVD

*(Zdroj: Paměti úvod.txt)*

### Otázka 12: Co je rozdíl mezi RAM a ROM z hlediska zápisu?
- **RWM / RAM** (Read Write Memory) – paměť pro čtení i zápis.
- **ROM** (Read Only Memory) – paměť pouze pro čtení. Informace je do paměti uložena jednorázově při výrobním procesu, nelze ji změnit.

*(Zdroj: Paměti úvod.txt)*

### Otázka 13: Jaký je rozdíl mezi EPROM a EEPROM?
- **EPROM** (Erasable Programmable ROM) – informaci zapsanou v paměti je možné vymazat UV zářením a znovu přeprogramovat.
- **EEPROM** (Electric Erasable PROM) – obdoba EPROM, mazání však probíhá pomocí elektrického impulsu, maže se buňka po buňce. Počet zápisů je omezen – cca 100 000 přepisů.

*(Zdroj: Paměti úvod.txt)*

### Otázka 14: Co je Flash ROM a kde se používá?
Flash ROM je elektricky programovatelná paměť. Flash paměť uchovává informace v paměťových buňkách stejně jako DRAM a SRAM, ale současně pracuje jako pevný disk, jelikož si uložené informace zachová i po odpojení od elektrického napájení. Ve Flash paměti nemusí být informace neustále obnovovány jako v DRAM, nebo neustále pod napájením jako SRAM. Používá se v BIOS, Flash discích, SSD, paměťových kartách apod.

*(Zdroj: Paměti úvod.txt)*

### Otázka 15: Co je SLC, MLC, TLC, QLC u Flash pamětí?
*(Odpověď nebyla nalezena v prezentacích.)*

---

## TÉMA 4: Polovodičové paměti

### Otázka 16: Jaký je rozdíl mezi SRAM a DRAM?
- **SRAM** (Static RAM) – paměťová buňka tvořena bistabilním klopným obvodem (BKO, min. 4 tranzistory). Je velice rychlá, vyžaduje menší proud, ale fyzicky zabírá velký prostor → malá kapacita. Využití: registry, vyrovnávací paměť CACHE.
- **DRAM** (Dynamic RAM) – paměťová buňka tvořena kondenzátorem a tranzistorem MOSFET. Je pomalejší (kvůli refreshi a destruktivnímu čtení), ale menší velikost buňky → větší kapacity. Využití: operační paměť, videopaměť.

*(Zdroj: Polovodičové paměti.txt)*

### Otázka 17: Proč DRAM potřebuje refresh?
Protože kapacita paměťové buňky je reálná (má svůj svod vlivem konečného odporu nevodivé vrstvy kondenzátoru) a velmi malá, dochází k rychlému samovolnému vybíjení (ztrátě informace). Aby ke ztrátě informace nedošlo, provádí se periodická obnova dat – tzv. refresh. Refresh se provádí po celých řádcích. Navíc je DRAM destruktivní paměť při čtení – čtením dojde k vybití kondenzátoru, přečtenou hodnotu je nutné opět zapsat.

*(Zdroj: Polovodičové paměti.txt)*

### Otázka 18: Jaké jsou hlavní rozdíly mezi DDR generacemi (DDR, DDR2, DDR3, DDR4, DDR5)?
| Generace | Napětí | Kmitočet | Propustnost | Kapacita modulu |
|----------|--------|----------|-------------|-----------------|
| DDR | 2,5 V | 200–600 MHz | 1,6–4,8 GB/s | 64 MB – 2 GB |
| DDR2 | 1,8 V | 400–1066 MHz | až 8,5 GB/s | 256 MB – 4 GB |
| DDR3 | 1,5 V | 800–2133 MHz | až 17 GB/s | 512 MB – 8 GB |
| DDR4 | 1,2 V | 2133–2400 MHz | – | 8 GB – 128 GB |
| DDR5 | – | 4,8–6 GHz | – | až 128 GB |

Všechny DDR generace přenášejí data jak během náběžné, tak sestupné hrany hodinového impulsu (2 operace za takt).

*(Zdroj: Polovodičové paměti.txt)*

### Otázka 19: Co je Dual Channel a jak funguje?
Dual Channel = 2 přenosové kanály. Místo jedné paměťové sběrnice spojující operační paměť s řadičem paměti jsou použity sběrnice dvě. Propustnost tak teoreticky vzroste dvakrát.

*(Zdroj: Polovodičové paměti.txt)*

### Otázka 20: Co je DIMM a kolik má pinů?
DIMM (Dual In-line Memory Module) – všechny novější paměti (SDRAM, DDR, DDR2, DDR3) jsou umístěny na modulech typu DIMM. Šířka datové sběrnice je 64 bitů. Paměťové moduly DIMM mají po stranách otvory pro zajištění v patici na základní desce. Mezi kontakty jsou otvory (klíče/zámky) uspořádané asymetricky pro zajištění správné orientace. DDR5 má 288 pinů.

*(Zdroj: Polovodičové paměti.txt)*

---

## TÉMA 5: Podpůrné obvody CPU

### Otázka 21: Co je DMA a k čemu slouží?
DMA (Direct Memory Access) – řadič DMA umožňuje periferním zařízením přímý přístup do operační paměti bez účasti CPU. Řadič DMA provádí 2 typy operací: přenos dat z OP do periferních zařízení a přenos dat z periferních zařízení do OP. Použití DMA řadiče je vhodné pro přenosy blokového charakteru s důrazem na velkou rychlost (diskové paměti, zvukové karty, rychlé síťové karty).

*(Zdroj: Podpůrné obvody CPU.txt)*

### Otázka 22: Jaké jsou dva režimy práce DMA?
1. **Kradení cyklů** – DMA řadič v případě požadavku na přenos obsadí sběrnici a provede jeden elementární přenos dat, potom sběrnici opět uvolní. Na sběrnici se střídají přenosové cykly procesoru a DMA řadiče.
2. **Blokový režim (Burst Mode)** – DMA řadič obsadí sběrnici na začátku blokového přenosu a v průběhu celého přenosu ji drží obsazenou. Zvyšuje rychlost přenosu, ale procesor je po celou dobu ve stavu HOLD.

*(Zdroj: Podpůrné obvody CPU.txt)*

### Otázka 23: Co je IRQ a k čemu slouží?
IRQ (Interrupt ReQuest) označuje signál, kterým požádá zařízení (např. klávesnice, časovač) procesor o věnování pozornosti – tedy požádá o přerušení probíhajícího procesu (vykonávání sledu instrukcí) za účelem provedení obsluhy požadavku. Úkolem řadiče přerušení je zajistit synchronizaci programu probíhajícího v CPU s požadavky na obsluhu od vnějších zařízení.

*(Zdroj: Podpůrné obvody CPU.txt)*

### Otázka 24: Jaký IRQ má nejvyšší prioritu?
Požadavky s nejnižším číslem mají nejvyšší prioritu. Tedy **IRQ 0** (systémový časovač) má nejvyšší prioritu. Klávesnice má IRQ 1 – tedy druhou nejvyšší prioritu.

*(Zdroj: Podpůrné obvody CPU.txt)*

### Otázka 25: Vyjmenuj fáze obsluhy přerušení (zjednodušeně).
1. Vnější zařízení vyvolá požadavek o přerušení přes linku IRQ.
2. Řadič přerušení vybere požadavek s nejvyšší prioritou a vyšle signál INTR k procesoru.
3. Procesor dokončí rozpracovanou instrukci a vysílá potvrzovací signál INTA.
4. Řadič identifikuje zařízení a odešle po datové sběrnici 8-bitové číslo typu přerušení.
5. Procesor uloží obsah svých registrů do zásobníku.
6. Procesor zpracuje typ přerušení a vyhledá obslužný podprogram v paměti.
7. Vykoná obslužný podprogram.
8. Obnoví původní obsah registrů ze zásobníku a přerušený program pokračuje dál.

*(Zdroj: Podpůrné obvody CPU.txt)*

---

## TÉMA 6: Procesory

### Otázka 26: Co je ALU a co dělá?
ALU (Aritmeticko-logická jednotka) je část procesoru, která provádí veškeré aritmetické operace (sčítání, odčítání, násobení, dělení) a logické operace (AND, OR, NOT, XOR, porovnání) s operandy (čísly ve dvojkovém vyjádření). Procesor obsahuje více jednotek ALU pro zvýšení výkonu.

*(Zdroj: Procesory.txt, Architektura procesorů Intel.txt)*

### Otázka 27: Co je Řadič (CU) a jaká je jeho funkce?
Řadič (CU – Control Unit) je aktivní částí procesoru. Jeho úkolem je řídit pořadí, v němž jsou prováděny instrukce programů, dekóduje instrukce, vysílá do ostatních částí počítače a procesoru řídící signály, čímž instrukce provádí.

*(Zdroj: Procesory.txt)*

### Otázka 28: Jaký je rozdíl mezi CISC a RISC?
- **CISC** (Complex Instruction Set Computer) – procesor s kompletní (velkou) instrukční sadou. Obsahuje i instrukce, které se používají velice málo. S ohledem na velký počet instrukcí bývá procesor složitý a drahý.
- **RISC** (Reduced Instruction Set Computer) – procesor s redukovanou instrukční sadou. Obsahuje malý počet instrukcí, které se provádějí velice rychle. Složitější operace se provádějí pomocí většího počtu jednodušších instrukcí. Mikroinstrukce jsou hardwarově implementovány v procesoru.

*(Zdroj: Procesory.txt)*

### Otázka 29: Co je pipelining?
Pipelining = zřetězené zpracování instrukcí. Procesor je složen z více funkčních bloků, které jsou vzájemně propojeny (pipeline, datovod). Dokáže si rozpracovat více instrukcí najednou. Zpracování instrukce se sestává z kroků: 1) výpočet adresy, 2) načtení instrukce, 3) dekódování instrukce, 4) provedení výpočtu v ALU/FPU, 5) zápis výsledku do registru.

*(Zdroj: Architektura procesorů Intel.txt)*

### Otázka 30: Co je superskalární architektura?
Superskalární architektura obsahuje více prováděcích jednotek (především ALU), umožňuje paralelní zřetězení (paralelní pipelining) – dokončení více instrukcí během jednoho hodinového taktu (pouze na sobě nezávislé instrukce). Zahrnuje předvídání (predikci) skoku v programu a vyrovnávací paměť CACHE L1 a L2.

*(Zdroj: Architektura procesorů Intel.txt)*

### Otázka 31: Co je SIMD?
SIMD (Single Instruction Multiple Data) – rozšíření instrukční sady o instrukce, které za určitých podmínek dokáží zpracovat více celých (resp. reálných) čísel najednou. Vhodné pro multimediální a matematické aplikace (2D/3D grafika, zvuk, video, komprese). Implementace 64-bitových resp. 128-bitových registrů. Technologie: MMX, 3DNow!, SSE, SSE2, SSE3, SSE4, AVX atd.

*(Zdroj: Architektura procesorů Intel.txt)*

### Otázka 32: Co je CACHE paměť a jaké má úrovně?
CACHE je velmi rychlá, statická paměť typu RAM, umístěná uvnitř procesoru (blízko jádra). Slouží k uložení části operační paměti (instrukce, data), se kterou procesor momentálně pracuje.
- **L1** – malá kapacita (řádově desítky kB), přímo součástí procesoru, stejně rychlá jako procesor. Dělí se na instrukční a datovou cache.
- **L2, L3** – pomalejší, ale s větší kapacitou (řádově jednotky MB). Obsahuje data a instrukce, které procesor aktuálně nepoužívá, ale pravděpodobně bude potřebovat.

*(Zdroj: Procesory.txt, Architektura procesorů Intel.txt)*

### Otázka 33: Co je FPU?
FPU (Floating Point Unit) = matematický koprocesor. Výpočetní jednotka integrovaná přímo v jádře procesoru, specializující se na operace s reálnými čísly s plovoucí řádovou čárkou. Je součástí CPU od architektury 80486 a vyšší.

*(Zdroj: Architektura procesorů Intel.txt)*

### Otázka 34: Co je TDP u procesorů?
TDP (Thermal Design Power) – tepelný výkon procesoru. Jednotkou je watt [W]. AMD udává TDP jako maximální dosažitelný tepelný výkon, INTEL jako typický, tedy dosažitelný při pracovní zátěži procesoru.

*(Zdroj: Procesory.txt)*

### Otázka 35: Co je Multi-Core?
Multi-Core = více fyzických jader uvnitř procesoru. Více fyzických jader procesoru umožňuje paralelní zpracování instrukcí a dat během jednoho hodinového taktu. Výrazně zvyšuje výkon procesoru, pokud paralelní zpracování podporuje operační systém a programová aplikace.

*(Zdroj: Procesory.txt)*

---

## TÉMA 7: Sběrnice

### Otázka 36: Co je sběrnice a jak jsou uspořádány v PC?
Sběrnice je soustava vodičů, které zajišťují propojení jednotlivých obvodů počítače. Používají se k přenosu dat, adres, řídicích a stavových signálů. Sběrnice v PC jsou uspořádány hierarchicky podle přenosových rychlostí – pomalejší sběrnice je vždy připojena do rychlejší. Sběrnice jsou propojeny mosty (severní, jižní), které obsahují řadiče zařízení.

*(Zdroj: Sběrnice.txt)*

### Otázka 37: Jak se vypočítá přenosová rychlost sběrnice?
Přenosová rychlost = kmitočet × šířka sběrnice [b/s]. Intel zavedl jednotku [GT/s] (Gigatransfers per second), kde 1 transfer = přenesení dat o velikosti šířky sběrnice v bajtech.

*(Zdroj: Sběrnice.txt)*

### Otázka 38: Jaký je rozdíl mezi paralelní a sériovou sběrnicí?
- **Paralelní** – více než 1 bit se přenáší současně (více vodičů). Problémy s parazitní kapacitou a rušením mezi vodiči při vyšších frekvencích.
- **Sériová** – 1 bit se přenáší po jednom vodiči. Přešlo se k ní z důvodu nemožnosti dalšího zvyšování rychlosti u paralelních rozhraní. Je kompaktnější, vyžaduje méně vodičů.

*(Zdroj: Sběrnice.txt)*

### Otázka 39: Co je PCI sběrnice a jaké má parametry?
PCI (Peripheral Component Interconnect) je systémová sběrnice pro připojení rozšiřujících karet do základní desky. Používá paralelní přenos dat (šířka 32 nebo 64 bitů). Nabízí standard Plug and Play (PnP). Podporuje bus mastering. Pracovní kmitočty: 33 MHz (32-bit) a 66/133 MHz (64-bit, PCI-X).

*(Zdroj: Sběrnice.txt)*

### Otázka 40: Jaké jsou výhody PCI Express oproti PCI?
PCI Express je založena na sériové komunikaci – je kompaktnější, vyžaduje méně vodičů, zlevňuje výrobu. Spoje typu point-to-point (Full Duplex) – dva jednosměrné spoje, datový tok není omezován žádným dalším zařízením na sběrnici (u PCI je datový tok sdílen všemi připojenými zařízeními). Mnohem vyšší přenosové rychlosti.

*(Zdroj: Sběrnice.txt)*

### Otázka 41: Kolik linků má PCIe x16 a jaká je rychlost PCIe 4.0 x16?
PCIe x16 má 16 linků (16 párů jednosměrných spojů). PCIe 5.0 je 2× rychlejší než verze 4.0.

*(Odpověď na přesnou rychlost PCIe 4.0 x16 nebyla nalezena v prezentacích.)*

### Otázka 42: Co je AGP a k čemu sloužilo?
AGP (Accelerated Graphics Port) je vysokorychlostní lokální sběrnice napojena přímo na severní most (obvod MCH) čipové sady. Pomocí této sběrnice bylo možné připojit k počítači výhradně grafickou kartu. V současné době je AGP sběrnice vytlačena rychlejší sériovou sběrnicí PCI Express x16.

*(Zdroj: Sběrnice.txt)*

### Otázka 43: Co je PCMCIA a kde se používá?
*(Odpověď nebyla nalezena v prezentacích – text byl oříznut.)*

### Otázka 44: Co je ExpressCard?
*(Odpověď nebyla nalezena v prezentacích – text byl oříznut.)*

### Otázka 45: Jaké jsou 3 lokální sběrnice?
1. **Procesorová** – nejrychlejší sběrnice na základní desce, slouží k přenášení dat mezi procesorem a čipovou sadou (FSB, QPI, HyperTransport).
2. **Paměťová** – přenos dat mezi procesorem a operační pamětí, propojuje řadič operační paměti s moduly.
3. **Grafická** – rychlý přenos dat mezi grafickou kartou, procesorem a operační pamětí (AGP, PCI Express x16).

*(Zdroj: Sběrnice.txt)*

---

## TÉMA 8: Rozhraní

### Otázka 46: Jaký je rozdíl mezi PATA a SATA?
- **PATA** (Parallel ATA) – paralelní rozhraní, max. rychlost 133 MB/s, široký 40-žilový kabel, max. délka 45 cm, konfigurace Master/Slave, nemožnost přistupovat k oběma diskům zároveň.
- **SATA** (Serial ATA) – sériové rozhraní, mnohem vyšší rychlost (SATA I: 1,5 Gb/s, SATA II: 3 Gb/s, SATA III: 6 Gb/s), úzký kabel, podpora Hot Plug a Hot Swap, každé zařízení je vždy Master, 20× méně energie.

*(Zdroj: Rozhrani.txt)*

### Otázka 47: Co je eSATA?
eSATA (External Serial ATA) umožňuje připojení disků a jiných zařízení přes SATA rozhraní externě mimo počítač. Nabízí vyšší rychlost přenosů dat oproti USB 2.0 a FireWire. Konektory jsou robustnější, kabely pevně uchyceny pomocí pružinového mechanismu, kabel může mít délku až 2 metry.

*(Zdroj: Rozhrani.txt)*

### Otázka 48: Co je SAS a kde se používá?
SAS (Serial Attached SCSI) je sériové rozhraní nahrazující dřívější paralelní SCSI. Používá příkazy SCSI i SATA. Nabízí komunikaci bod-bod, vyšší přenosovou rychlost (1.5, 3, 6 Gb/s), podporu hot swap a vylepšenou schopnost proti selhání řadiče. Umožňuje propojit jediný disk ke dvěma řadičům (zvyšuje bezpečnost u serverů). SAS řadiče podporují i SATA zařízení. Používá se především v serverech.

*(Zdroj: Rozhrani.txt)*

### Otázka 49: Jaké jsou rychlosti USB 2.0, 3.0 a 3.1?
*(Odpověď nebyla nalezena v prezentacích – text byl oříznut.)*

### Otázka 50: Co je USB Type-C?
*(Odpověď nebyla nalezena v prezentacích – text byl oříznut.)*

### Otázka 51: Jaké jsou parametry Bluetooth?
*(Odpověď nebyla nalezena v prezentacích – text byl oříznut.)*

### Otázka 52: Co je Thunderbolt 3?
*(Odpověď nebyla nalezena v prezentacích – text byl oříznut.)*

---

## TÉMA 9: Pevné disky

### Otázka 53: Jak funguje princip magnetického záznamu na HDD?
Magnetický záznam dat je prováděn silovým působením magnetického pole na feromagnetický materiál (záznamová vrstva). Celý povrch disku je tvořen mikroskopickými magnetickými částicemi – doménami. Záznam je prováděn záznamovou indukční hlavou – cívkou elektromagnetu prochází záznamový proud, který podle Ampérova pravidla vytvoří magnetický tok. V místě štěrbiny dojde k rozptylu magnetického toku a zmagnetování domény. Změnou směru proudu se mění směr magnetizace domén.

*(Zdroj: Harddisky.txt)*

### Otázka 54: Co je GMR hlava?
GMR (Giant Magnetoresistive) hlava je moderní čtecí hlava pevného disku, která mění svůj elektrický odpor při změně orientace magnetického pole, tedy při přechodu mezi dvěma různě orientovanými doménami. Čtecí hlavou prochází elektrický proud, který dle velikosti elektrického odporu GMR snímače vytvoří úbytek napětí. Vyznačuje se velmi malými rozměry a rychlou reakcí. Umožňuje vysokou hustotu záznamu dat na plotnu.

*(Zdroj: Harddisky.txt)*

### Otázka 55: Co je stopa, sektor, cylindr?
- **Stopa (track)** – oblast pro ukládání dat ve tvaru soustředné kružnice. Každá stopa je rozdělena na menší části – sektory.
- **Sektor (sector)** – část jedné stopy, ohraničená identifikačními značkami. Jde o základní jednotku pro ukládání dat. Standardní velikost 512 B.
- **Cylindr** – soubor stop se stejným poloměrem na všech plotnách disku.

*(Zdroj: Harddisky.txt)*

### Otázka 56: Co je cluster (alokační jednotka)?
Cluster (alokační jednotka) je nejmenší logická jednotka, se kterou pracuje souborový systém. Menší cluster je výhoda pro malé soubory, ale nevýhoda pro velké (velká fragmentace). Větší cluster je výhoda pro velké soubory, ale nevýhoda pro malé (neefektivní využití prostoru).

*(Zdroj: Harddisky.txt)*

### Otázka 57: Jaké jsou hlavní parametry HDD?
1. Počet stop (tracks)
2. Počet sektorů (sectors)
3. Počet cylindrů
4. Počet a velikost clusterů
5. Počet čtecích/zapisovacích hlaviček (heads)
6. Otáčky – 4200, 5400, 7200, 10000, 15000 RPM
7. Přístupová doba – průměrný čas v ms
8. Formát disku – průměr plotny: 1.8'', 2.5'', 3.5'', 5.25''

*(Zdroj: Harddisky.txt)*

### Otázka 58: Co je S.M.A.R.T.? 
S.M.A.R.T. (Self-Monitoring, Analysis and Reporting Technology) – technologie, při které se periodicky měří a sledují významné parametry a chování pevného disku. Při detekci hodnot mimo toleranci stanovenou výrobcem dojde k odeslání varování operačnímu systému. Jde o technologii, která za určitých podmínek dokáže předvídat selhání pevného disku.

*(Zdroj: Harddisky.txt)*

### Otázka 59: Jaký je rozdíl mezi PMR a SMR zápisem?
*(Odpověď nebyla nalezena v prezentacích.)*

### Otázka 60: Co je NCQ?
NCQ (Native Command Queuing) je technologie, která umožňuje zvýšit výkon pevných disků s rozhraním SATA II a novějších. Při použití NCQ pevný disk sám optimalizuje pořadí, ve kterém jsou vykonány požadavky na zápis nebo čtení. Tato optimalizace může redukovat nadbytečný pohyb hlaviček disku, čímž se zvýší rychlost přenosu dat a mírně sníží opotřebení disku.

*(Zdroj: Harddisky.txt)*

---

## TÉMA 10: Grafické karty

### Otázka 61: Co je GPU a k čemu slouží?
GPU (Graphic Processors Units) – speciální procesory, které jsou součástí grafických karet a moderních procesorů. Jejich úkolem je řídit zpracování obrazových dat a výpočty fyzikálního modelu 3D scény. Program i data jsou uloženy buď v operační paměti nebo paměti grafické karty.

*(Zdroj: Procesory.txt, Grafické karty.txt)*

### Otázka 62: Jaký je rozdíl mezi integrovanou a dedikovanou grafikou?
Integrovaná grafika – grafický procesor (GPU) je přímo integrován do struktury hlavního procesoru (součástí jednoho polovodičového čipu, APU). Dedikovaná grafika – samostatná grafická karta s vlastním GPU, vlastní pamětí (GDDR) a vlastním chlazením, připojená přes sběrnici PCI Express x16.

*(Zdroj: Čipová sada.txt, Procesory.txt, Grafické karty.txt)*

### Otázka 63: Co je RAMDAC?
RAMDAC je kombinace tří D/A (Digital-to-Analog) převodníků (pro každou RGB složku jeden) a malé SRAM paměti pro uložení barevné mapy. Slouží k převodu digitálního videosignálu na analogový, který vyžadují CRT monitory, starší LCD displeje a dataprojektory. Jeho rychlost se udává v MHz a ovlivňuje maximální zobrazovací frekvenci při určitém rozlišení obrazu. U dnešních LCD panelů není konverze nutná.

*(Zdroj: Grafické karty.txt)*

### Otázka 64: Jaké jsou hlavní typy video výstupů?
- **D-sub (VGA)** – starší rozhraní, pouze analogový výstup, 15-pinový konektor.
- **DVI** (Digital Visual Interface) – DVI-D (pouze digitální), DVI-I (digitální i analogový). Single link a Dual link.
- **HDMI** – digitální přenos obrazu i zvuku.
- **DisplayPort** – moderní digitální rozhraní.

*(Zdroj: Grafické karty.txt)*

### Otázka 65: Co je Multi-GPU (SLI, CrossFireX)?
*(Odpověď nebyla nalezena v prezentacích – text byl oříznut.)*