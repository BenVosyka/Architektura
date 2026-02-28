# Architektura – Zápočtové otázky a odpovědi

---

## TÉMA 1: Úvod (Von Neumann, Hardware)

**Otázka 1: Co je základní myšlenka Von Neumannovy architektury?**

> *Odpověď:*

**Otázka 2: Jaké jsou hlavní součásti CPU podle Von Neumanna?**

> *Odpověď:*

**Otázka 3: Jaký je hlavní rozdíl mezi Von Neumannovou a Harvardskou architekturou?**

> *Odpověď:*

**Otázka 4: Co umožňuje 64-bitový systém oproti 32-bitovému?**

> *Odpověď:* 64-bitový systém umožňuje rozšíření instrukční sady o instrukce pro práci s 64-bitovými čísly, implementaci 64-bitových registrů a zvýšení adresového prostoru operační paměti nad 4 GB (32-bit = 2³² = max 4 GB). Technologie Intel EM64T / Intel 64.

**Otázka 5: Co je virtualizace paměti a k čemu slouží?**

> *Odpověď:*

---

## TÉMA 2: Čipová sada

**Otázka 6: Co je čipová sada (chipset) a k čemu slouží?**

> *Odpověď:*

**Otázka 7: Jaké jsou dva hlavní obvody v architektuře mostů?**

> *Odpověď:*

**Otázka 8: Co zajišťuje Northbridge?**

> *Odpověď:* Northbridge (severní most, MCH) zajišťuje komunikaci CPU s operační pamětí a grafickou sběrnicí. V novějších architekturách (od Nehalem) jsou obvody severního mostu integrovány přímo do CPU (řadič OP, řadič PCI-E x16, případně i GPU).

**Otázka 9: Co je FSB a k čemu slouží?**

> *Odpověď:* FSB (Front Side Bus) je procesorová sběrnice, která propojuje CPU se severním mostem (MCH). V architektuře NetBurst využívá technologii QPB (Quad Pumped Bus) – až 4 přenosy dat během 1 hodinového taktu.

**Otázka 10: Jaký je rozdíl mezi QPI a FSB?**

> *Odpověď:* FSB je starší procesorová sběrnice propojující CPU se severním mostem. QPI (QuickPath Interconnect) ji nahradila v architektuře Nehalem – je to point-to-point spoj s vyšší propustností, který propojuje CPU přímo s okolními komponenty, protože řadič paměti a další obvody severního mostu jsou již integrovány v CPU.

---

## TÉMA 3: Paměti obecně

**Otázka 11: Jaké jsou hlavní 3 druhy pamětí podle pohledu na médium?**

> *Odpověď:*

**Otázka 12: Co je rozdíl mezi RAM a ROM z hlediska zápisu?**

> *Odpověď:*

**Otázka 13: Jaký je rozdíl mezi EPROM a EEPROM?**

> *Odpověď:*

**Otázka 14: Co je Flash ROM a kde se používá?**

> *Odpověď:*

**Otázka 15: Co je SLC, MLC, TLC, QLC u Flash pamětí?**

> *Odpověď:*

---

## TÉMA 4: Polovodičové paměti

**Otázka 16: Jaký je rozdíl mezi SRAM a DRAM?**

> *Odpověď:*

**Otázka 17: Proč DRAM potřebuje refresh?**

> *Odpověď:*

**Otázka 18: Jaké jsou hlavní rozdíly mezi DDR generacemi (DDR, DDR2, DDR3, DDR4, DDR5)?**

> *Odpověď:*

**Otázka 19: Co je Dual Channel a jak funguje?**

> *Odpověď:*

**Otázka 20: Co je DIMM a kolik má pinů?**

> *Odpověď:*

---

## TÉMA 5: Podpůrné obvody CPU

**Otázka 21: Co je DMA a k čemu slouží?**

> *Odpověď:*

**Otázka 22: Jaké jsou dva režimy práce DMA?**

> *Odpověď:*

**Otázka 23: Co je IRQ a k čemu slouží?**

> *Odpověď:*

**Otázka 24: Jaký má IRQ má nejvyšší prioritu?**

> *Odpověď:*

**Otázka 25: Vyjmenuj fáze obsluhy přerušení (zjednodušeně).**

> *Odpověď:*

---

## TÉMA 6: Procesory

**Otázka 26: Co je ALU a co dělá?**

> *Odpověď:* ALU (Arithmetic Logic Unit) je výpočetní jednotka procesoru. Je to základní obvod architektury CPU, který provádí aritmetické a logické operace (ADD, SUB, AND, OR apod.). Přijímá operandy ze dvou registrů a řídicí signály, provádí výpočet a výsledek ukládá do registru. Generuje příznaky (flags): Z (zero), C (carry), O (overflow).

**Otázka 27: Co je Řadič (CU) a jaká je jeho funkce?**

> *Odpověď:* Řadič (Control Unit, CU) je základní obvod architektury procesoru, který řídí celý průběh zpracování instrukcí. Dekóduje instrukce, generuje řídicí signály pro ALU, paměti, registry a sběrnice. Určuje, jaká operace se má provést, odkud vzít operandy a kam uložit výsledek.

**Otázka 28: Jaký je rozdíl mezi CISC a RISC?**

> *Odpověď:*

**Otázka 29: Co je pipelining?**

> *Odpověď:* Pipelining (zřetězené zpracování instrukcí) znamená, že procesor je složen z více funkčních bloků vzájemně propojených do pipeline (datovodu). Díky tomu si dokáže rozpracovat více instrukcí najednou – zatímco se jedna instrukce vykonává v ALU, další se dekóduje a další se načítá z paměti. Fáze: 1) výpočet adresy, 2) načtení instrukce (fetch), 3) dekódování instrukce, 4) provedení operace v ALU/FPU (execute), 5) zápis výsledku do registru.

**Otázka 30: Co je superskalární architektura?**

> *Odpověď:* Superskalární architektura obsahuje více prováděcích jednotek (především ALU) a umožňuje paralelní pipelining – dokončení více instrukcí během jednoho hodinového taktu (pouze na sobě nezávislé instrukce). Dále zahrnuje predikci skoků, CACHE paměť L1 (instrukční + datová) a L2, a podporu SIMD instrukcí.

**Otázka 31: Co je SIMD?**

> *Odpověď:* SIMD (Single Instruction, Multiple Data) je rozšíření instrukční sady o instrukce, které dokáží za určitých podmínek zpracovat více celých či reálných čísel najednou pomocí 64/128/256-bitových registrů. Příklad: místo 4 samostatných násobení 5×2, 5×3, 5×1, 5×8 se provede jedna SIMD instrukce 5×(2;3;1;8)=(10;15;5;40). Implementace: MMX, 3DNow!, SSE, SSE2–5, AVX, AVX-512. Vhodné pro multimédia, 2D/3D grafiku, video, kompresi a matematické aplikace.

**Otázka 32: Co je CACHE paměť a jaké má úrovně?**

> *Odpověď:* CACHE je velmi rychlá statická paměť typu RAM umístěná blízko jádra procesoru. Slouží k uložení části operační paměti (instrukce, data), se kterou procesor momentálně pracuje. Úrovně: **L1** – nejmenší a nejrychlejší, dělí se na instrukční a datovou (desítky kB); **L2** – pomalejší, větší kapacita (stovky kB), může být sdílená mezi jádry (Advanced Smart Cache); **L3** – sdílená mezi všemi jádry (jednotky MB), slouží i pro GPU (LLC – Last Level Cache).

**Otázka 33: Co je FPU?**

> *Odpověď:* FPU (Floating Point Unit) je matematický koprocesor – výpočetní jednotka integrovaná přímo v jádře procesoru, specializující se na operace s reálnými čísly s plovoucí řádovou čárkou. Je součástí CPU od architektury 80486 a vyšší.

**Otázka 34: Co je TDP u procesorů?**

> *Odpověď:* TDP (Thermal Design Power) je maximální tepelný výkon procesoru, tedy množství tepla, které musí chladič odvést. Vyšší TDP = potřeba masivnějšího chlazení a výkonnějšího zdroje. Technologie jako TurboBoost dokáží krátkodobě přetaktovat CPU nad rámec maximální hodnoty TDP (chladič má setrvačnost při zahřívání). Technologie SpeedStep a Speed Shift upravují frekvenci dle zátěže pro snížení spotřeby a TDP.

**Otázka 35: Co je Multi-Core?**

> *Odpověď:* Multi-Core znamená více fyzických procesorových jader v jednom CPU, což umožňuje paralelní zpracování více aplikací najednou nebo rozložení jedné aplikace na více jader. Příklady: 2 jádra (Core i3), 4 jádra (Core i5, i7), 6+ jader (Xeon). Moderní procesory (Raptor Lake) používají hybridní architekturu – výkonná jádra (P-cores, s HyperThreadingem) + efektivní jádra (E-cores, úsporná, 4 zabírají místo 1 výkonného). HW scheduler zajišťuje správné přidělování vláken.

---

## TÉMA 7: Sběrnice

**Otázka 36: Co je sběrnice a jak jsou uspořádány v PC?**

> *Odpověď:*

**Otázka 37: Jak se vypočítá přenosová rychlost sběrnice?**

> *Odpověď:*

**Otázka 38: Jaký je rozdíl mezi paralelní a sériovou sběrnicí?**

> *Odpověď:*

**Otázka 39: Co je PCI sběrnice a jaké má parametry?**

> *Odpověď:*

**Otázka 40: Jaké jsou výhody PCI Express oproti PCI?**

> *Odpověď:*

**Otázka 41: Kolik linků má PCIe x16 a jaká je rychlost PCIe 4.0 x16?**

> *Odpověď:*

**Otázka 42: Co je AGP a k čemu sloužilo?**

> *Odpověď:*

**Otázka 43: Co je PCMCIA a kde se používá?**

> *Odpověď:*

**Otázka 44: Co je ExpressCard?**

> *Odpověď:*

**Otázka 45: Jaké jsou 3 lokální sběrnice?**

> *Odpověď:*

---

## TÉMA 8: Rozhraní

**Otázka 46: Jaký je rozdíl mezi PATA a SATA?**

> *Odpověď:*

**Otázka 47: Co je eSATA?**

> *Odpověď:*

**Otázka 48: Co je SAS a kde se používá?**

> *Odpověď:*

**Otázka 49: Jaké jsou rychlosti USB 2.0, 3.0 a 3.1?**

> *Odpověď:*

**Otázka 50: Co je USB Type-C?**

> *Odpověď:*

**Otázka 51: Jaké jsou parametry Bluetooth?**

> *Odpověď:*

**Otázka 52: Co je Thunderbolt 3?**

> *Odpověď:*

---

## TÉMA 9: Pevné disky

**Otázka 53: Jak funguje princip magnetického záznamu na HDD?**

> *Odpověď:*

**Otázka 54: Co je GMR hlava?**

> *Odpověď:*

**Otázka 55: Co je stopa, sektor, cylindr?**

> *Odpověď:*

**Otázka 56: Co je cluster (alokační jednotka)?**

> *Odpověď:*

**Otázka 57: Jaké jsou hlavní parametry HDD?**

> *Odpověď:*

**Otázka 58: Co je S.M.A.R.T.?**

> *Odpověď:*

**Otázka 59: Jaký je rozdíl mezi PMR a SMR zápisem?**

> *Odpověď:*

**Otázka 60: Co je NCQ?**

> *Odpověď:*

---

## TÉMA 10: Grafické karty

**Otázka 61: Co je GPU a k čemu slouží?**

> *Odpověď:*

**Otázka 62: Jaký je rozdíl mezi integrovanou a dedikovanou grafikou?**

> *Odpověď:* Integrovaná grafika (např. Intel HD Graphics, Intel Iris, Intel UHD Graphics) je grafický procesor integrovaný přímo na čipu CPU – sdílí L3 cache s CPU, má vlastní napájení a možnost úpravy frekvence dle potřeby aplikace; výkon stačí na 3D efekty OS, 4K videa a více monitorů. Dedikovaná grafika je samostatná grafická karta s vlastním GPU a pamětí, nabízí výrazně vyšší výkon pro hry a náročné aplikace.

**Otázka 63: Co je RAMDAC?**

> *Odpověď:*

**Otázka 64: Jaké jsou hlavní typy video výstupů?**

> *Odpověď:*

**Otázka 65: Co je Multi-GPU (SLI, CrossFireX)?**

> *Odpověď:*

---

## TÉMA 11: Zvukové karty

**Otázka 66: Co byla první "zvuková karta" PC?**

> *Odpověď:*

**Otázka 67: Co přinesla Sound Blaster (1989)?**

> *Odpověď:*

**Otázka 68: Co je ASIO?**

> *Odpověď:*

**Otázka 69: Jaké jsou hlavní parametry zvukových karet?**

> *Odpověď:*

**Otázka 70: Co je EAX?**

> *Odpověď:*