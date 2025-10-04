# 👻 Ghost Bezpečnostný Modul
**PowerShell nástroj na posilnenie bezpečnosti Windows a Azure**

> **Proaktívne posilnenie bezpečnosti pre Windows koncové body a Azure prostredia.** Ghost poskytuje funkcie na posilnenie založené na PowerShell, ktoré môžu pomôcť znížiť bežné vektory útokov vypnutím nepotrebných služieb a protokolov.

## ⚠️ Dôležité upozornenia

**TESTOVANIE POVINNÉ**: Vždy najprv testujte Ghost v neprodukčných prostrediach. Vypnutie služieb môže ovplyvniť legitímne obchodné funkcie.

**ŽIADNE ZÁRUKY**: Hoci Ghost ciela na bežné vektory útokov, žiadny bezpečnostný nástroj nemôže zabrániť všetkým útokom. Toto je jeden komponent v komplexnej bezpečnostnej stratégii.

**PREVÁDZKOVÝ DOPAD**: Niektoré funkcie môžu ovplyvniť funkcionalitu systému. Pred nasadením starostlivo preskúmajte každé nastavenie.

**PROFESIONÁLNE HODNOTENIE**: Pre produkčné prostredia sa poraďte s bezpečnostnými expertmi, aby ste zabezpečili, že nastavenia sú v súlade s potrebami vašej organizácie.

## 📊 Bezpečnostná krajina

Škody od ransomware dosiahli **57 miliárd dolárov v roku 2025**, výskum ukazuje, že mnoho úspešných útokov využíva základné služby Windows a nesprávne konfigurácie. Bežné vektory útokov zahŕňajú:

- **90% incidentov ransomware** zahŕňa zneužitie RDP
- **Zraniteľnosti SMBv1** umožnili útoky ako WannaCry a NotPetya
- **Makrá dokumentov** zostávajú primárnou metódou doručovania malvéru
- **Útoky založené na USB** naďalej cielene útočia na air-gap siete
- **Zneužívanie PowerShell** sa výrazne zvýšilo v posledných rokoch

## 🛡️ Ghost bezpečnostné funkcie

Ghost poskytuje **16 funkcií na posilnenie Windows** plus **integráciu bezpečnosti Azure**:

### Posilnenie Windows koncových bodov

| Funkcia | Účel | Úvahy |
|----------|---------|----------------|
| `Set-RDP` | Spravuje prístup Remote Desktop | Môže ovplyvniť vzdialenú správu |
| `Set-SMBv1` | Kontroluje starý protokol SMB | Potrebný pre veľmi staré systémy |
| `Set-AutoRun` | Kontroluje AutoPlay/AutoRun | Môže ovplyvniť pohodlie používateľa |
| `Set-USBStorage` | Obmedzuje USB úložné zariadenia | Môže ovplyvniť legitímne používanie USB |
| `Set-Macros` | Kontroluje vykonávanie Office makier | Môže ovplyvniť dokumenty s povolenými makrami |
| `Set-PSRemoting` | Spravuje PowerShell remoting | Môže ovplyvniť vzdialenú správu |
| `Set-WinRM` | Kontroluje Windows Remote Management | Môže ovplyvniť vzdialenú správu |
| `Set-LLMNR` | Spravuje protokol rozlíšenia mien | Zvyčajne bezpečné na vypnutie |
| `Set-NetBIOS` | Kontroluje NetBIOS cez TCP/IP | Môže ovplyvniť staršie aplikácie |
| `Set-AdminShares` | Spravuje administratívne zdieľania | Môže ovplyvniť vzdialený prístup k súborom |
| `Set-Telemetry` | Kontroluje zber údajov | Môže ovplyvniť diagnostické schopnosti |
| `Set-GuestAccount` | Spravuje účet hosťa | Zvyčajne bezpečné na vypnutie |
| `Set-ICMP` | Kontroluje ping odpovede | Môže ovplyvniť sieťovú diagnostiku |
| `Set-RemoteAssistance` | Spravuje Remote Assistance | Môže ovplyvniť operácie help desk |
| `Set-NetworkDiscovery` | Kontroluje objavovanie siete | Môže ovplyvniť prehliadanie siete |
| `Set-Firewall` | Spravuje Windows Firewall | Kritické pre sieťovú bezpečnosť |

### Azure cloudová bezpečnosť

| Funkcia | Účel | Požiadavky |
|----------|---------|--------------|
| `Set-AzureSecurityDefaults` | Povoľuje základnú bezpečnosť Azure AD | Oprávnenia Microsoft Graph |
| `Set-AzureConditionalAccess` | Konfiguruje politiky prístupu | Licencovanie Azure AD P1/P2 |
| `Set-AzurePrivilegedUsers` | Audituje privilegované účty | Oprávnenia Global Admin |

### Možnosti podnikového nasadenia

| Metóda | Prípad použitia | Požiadavky |
|--------|----------|--------------|
| **Priame spustenie** | Testovanie, malé prostredia | Lokálne admin práva |
| **Group Policy** | Doménové prostredia | Domenový admin, GP správa |
| **Microsoft Intune** | Cloudové spravované zariadenia | Licencovanie Intune, Graph API |

## 🚀 Rýchly štart

### Hodnotenie bezpečnosti
```powershell
# Načítajte modul Ghost
IEX(Invoke-WebRequest 'https://raw.githubusercontent.com/jimrtyler/Ghost/main/Ghost.ps1')

# Skontrolujte aktuálny bezpečnostný postoj
Get-Ghost
```

### Základné posilnenie (najprv testovať)
```powershell
# Základné posilnenie - najprv testovať v laboratórnom prostredí
Set-Ghost -SMBv1 -AutoRun -Macros

# Preskúmajte zmeny
Get-Ghost
```

### Podnikové nasadenie
```powershell
# Nasadenie Group Policy (doménové prostredia)
Set-Ghost -SMBv1 -AutoRun -GroupPolicy

# Nasadenie Intune (cloudové spravované zariadenia)
Set-Ghost -SMBv1 -RDP -USBStorage -Intune
```

## 📋 Metódy inštalácie

### Možnosť 1: Priame stiahnutie (testovanie)
```powershell
IEX(Invoke-WebRequest 'https://raw.githubusercontent.com/jimrtyler/Ghost/main/Ghost.ps1')
```

### Možnosť 2: Inštalácia modulu
```powershell
# Nainštalovať z PowerShell Gallery (keď je dostupné)
Install-Module Ghost -Scope CurrentUser
Import-Module Ghost
```

### Možnosť 3: Podnikové nasadenie
```powershell
# Skopírovať na sieťové umiestnenie pre nasadenie Group Policy
# Nakonfigurovať Intune PowerShell skripty pre cloudové nasadenie
```

## 💼 Príklady prípadov použitia

### Malý podnik
```powershell
# Základná ochrana s minimálnym dopadom
Set-Ghost -SMBv1 -AutoRun -Macros -ICMP
```

### Zdravotnícke prostredie
```powershell
# HIPAA zamerané posilnenie
Set-Ghost -SMBv1 -RDP -USBStorage -AdminShares -Telemetry
```

### Finančné služby
```powershell
# Vysoká bezpečnostná konfigurácia
Set-Ghost -RDP -SMBv1 -AutoRun -USBStorage -Macros -PSRemoting -AdminShares
```

### Cloud-First organizácia
```powershell
# Intune spravované nasadenie
Connect-IntuneGhost -Interactive
Set-Ghost -SMBv1 -RDP -AutoRun -Macros -Intune
```

## 🔍 Podrobnosti funkcií

### Hlavné funkcie posilnenia

#### Sieťové služby
- **RDP**: Blokuje prístup k vzdialenej ploche alebo randomizuje port
- **SMBv1**: Vypína starý protokol zdieľania súborov
- **ICMP**: Zabraňuje ping odpovediam pre reconnaissance
- **LLMNR/NetBIOS**: Blokuje staré protokoly rozlíšenia mien

#### Bezpečnosť aplikácií
- **Makrá**: Vypína vykonávanie makier v Office aplikáciách
- **AutoRun**: Zabraňuje automatickému spusteniu z odstrániteľných médií

#### Vzdialená správa
- **PSRemoting**: Vypína vzdialené PowerShell relácie
- **WinRM**: Zastavuje Windows Remote Management
- **Remote Assistance**: Blokuje pripojenia vzdialenej pomoci

#### Kontrola prístupu
- **Admin Shares**: Vypína C$, ADMIN$ zdieľania
- **Guest Account**: Vypína prístup účtu hosťa
- **USB Storage**: Obmedzuje používanie USB zariadení

### Azure integrácia
```powershell
# Pripojte sa k Azure tenant
Connect-AzureGhost -Interactive

# Povoľte predvolené nastavenia bezpečnosti
Set-AzureSecurityDefaults -Enable

# Nakonfigurujte podmienený prístup
Set-AzureConditionalAccess -BlockLegacyAuth -RequireMFA

# Auditujte privilegovaných používateľov
Set-AzurePrivilegedUsers -AuditOnly
```

### Intune integrácia (nové vo v2)
```powershell
# Pripojte sa k Intune
Connect-IntuneGhost -Interactive

# Nasaďte cez Intune politiky
Set-IntuneGhost -Settings @{
    RDP = $true
    SMBv1 = $true
    USBStorage = $true
    Macros = $true
}
```

## ⚠️ Dôležité úvahy

### Požiadavky na testovanie
- **Laboratórne prostredie**: Najprv testujte všetky nastavenia v izolovanom prostredí
- **Postupné nasadenie**: Postupne nasadzujte na identifikáciu problémov
- **Plán návratnosti**: Zabezpečte, že môžete vrátiť zmeny v prípade potreby
- **Dokumentácia**: Zaznamenajte, ktoré nastavenia fungujú pre vaše prostredie

### Potenciálny dopad
- **Produktivita používateľa**: Niektoré nastavenia môžu ovplyvniť denné pracovné toky
- **Staršie aplikácie**: Staršie systémy môžu vyžadovať špecifické protokoly
- **Vzdialený prístup**: Zvážte dopad na legitímnu vzdialenú správu
- **Obchodné procesy**: Overte, že nastavenia nerušia kritické funkcie

### Bezpečnostné obmedzenia
- **Obrana do hĺbky**: Ghost je jedna vrstva bezpečnosti, nie kompletné riešenie
- **Nepretržité riadenie**: Bezpečnosť vyžaduje nepretržité monitorovanie a aktualizácie
- **Školenie používateľov**: Technická kontrola musí byť spárovaná s bezpečnostným povedomím
- **Evolúcia hrozieb**: Nové metódy útokov môžu obísť súčasnú ochranu

## 🎯 Príklady scenárov útokov

Hoci Ghost ciela na bežné vektory útokov, špecifická prevencia závisí od správnej implementácie a testovania:

### Útoky v štýle WannaCry
- **Zmierňovanie**: `Set-Ghost -SMBv1` vypína zraniteľný protokol
- **Úvahy**: Zabezpečte, že žiadny starý systém nevyžaduje SMBv1

### RDP založený ransomware
- **Zmierňovanie**: `Set-Ghost -RDP` blokuje prístup k vzdialenej ploche
- **Úvahy**: Môže vyžadovať alternatívne metódy vzdialeného prístupu

### Malvér založený na dokumentoch
- **Zmierňovanie**: `Set-Ghost -Macros` vypína vykonávanie makier
- **Úvahy**: Môže ovplyvniť legitímne dokumenty s povolenými makrami

### USB doručené hrozby
- **Zmierňovanie**: `Set-Ghost -USBStorage -AutoRun` obmedzuje USB funkcionalitu
- **Úvahy**: Môže ovplyvniť legitímne používanie USB zariadení

## 🏢 Podnikové funkcie

### Podpora Group Policy
```powershell
# Aplikujte nastavenia cez Group Policy registry
Set-Ghost -SMBv1 -RDP -AutoRun -GroupPolicy

# Nastavenia sa aplikujú v celej doméne po GP obnove
gpupdate /force
```

### Microsoft Intune integrácia
```powershell
# Vytvorte Intune politiky pre Ghost nastavenia
Set-IntuneGhost -Settings $GhostSettings -Interactive

# Politiky sa automaticky nasadia na spravované zariadenia
```

### Hlásenie súladu
```powershell
# Vygenerujte správu hodnotenia bezpečnosti
Get-Ghost | Export-Csv -Path "SecurityAudit-$(Get-Date -Format 'yyyy-MM-dd').csv"

# Azure správa bezpečnostného postoja
Get-AzureGhost | Out-File "AzureSecurityReport.txt"
```

## 📚 Najlepšie postupy

### Pred nasadením
1. **Dokumentujte súčasný stav**: Spustite `Get-Ghost` pred zmenami
2. **Starostlivo testujte**: Validujte v neprodukčnom prostredí
3. **Naplánujte rollback**: Vedzte, ako vrátiť každé nastavenie
4. **Preskúmanie zainteresovaných strán**: Zabezpečte, že obchodné jednotky schvália zmeny

### Počas nasadenia
1. **Postupný prístup**: Najprv nasaďte do pilotných skupín
2. **Monitorujte dopad**: Sledujte sťažnosti používateľov alebo systémové problémy
3. **Dokumentujte problémy**: Zaznamenajte akékoľvek problémy pre budúce referencie
4. **Komunikujte zmeny**: Informujte používateľov o bezpečnostných vylepšeniach

### Po nasadení
1. **Pravidelné hodnotenie**: Periodicky spúšťajte `Get-Ghost` na overenie nastavení
2. **Aktualizujte dokumentáciu**: Udržujte aktuálne bezpečnostné konfigurácie
3. **Preskúmajte efektívnosť**: Monitorujte bezpečnostné incidenty
4. **Nepretržité zlepšovanie**: Upravujte nastavenia na základe hrozbovej krajiny

## 🔧 Riešenie problémov

### Bežné problémy
- **Chyby oprávnení**: Zabezpečte zvýšenú PowerShell reláciu
- **Závislosti služieb**: Niektoré služby môžu mať závislosti
- **Kompatibilita aplikácií**: Testujte s obchodnými aplikáciami
- **Sieťové pripojenie**: Overte, že vzdialený prístup stále funguje

### Možnosti obnovenia
```powershell
# Znovu povoľte špecifické služby v prípade potreby
Set-RDP -Enable
Set-SMBv1 -Enable
Set-AutoRun -Enable
Set-Macros -Enable
```

## 👨‍💻 O autorovi

**Jim Tyler** - Microsoft MVP pre PowerShell
- **YouTube**: [@PowerShellEngineer](https://youtube.com/@PowerShellEngineer) (10,000+ odberateľov)
- **Newsletter**: [PowerShell.News](https://powershell.news) - Týždenné bezpečnostné spravodajstvo
- **Autor**: "PowerShell for Systems Engineers"
- **Skúsenosti**: Desaťročia PowerShell automatizácie a Windows bezpečnosti

## 📄 Licencia a zrieknutie sa zodpovednosti

### MIT licencia
Ghost je poskytovaný pod MIT licenciou pre bezplatné používanie, úpravy a distribúciu.

### Bezpečnostné zrieknutie sa zodpovednosti
- **Žiadna záruka**: Ghost je poskytovaný "ako je" bez záruky akéhokoľvek druhu
- **Testovanie potrebné**: Vždy najprv testujte v neprodukčných prostrediach
- **Profesionálne vedenie**: Poraďte sa s bezpečnostnými profesionálmi pre produkčné nasadenia
- **Prevádzkový dopad**: Autori nie sú zodpovední za žiadne prevádzkové narušenia
- **Komplexná bezpečnosť**: Ghost je jeden komponent v kompletnej bezpečnostnej stratégii

### Podpora
- **GitHub Issues**: [Nahláste chyby alebo požiadajte o funkcie](https://github.com/jimrtyler/Ghost/issues)
- **Dokumentácia**: Použite `Get-Help <function> -Full` pre podrobnú pomoc
- **Komunita**: PowerShell a bezpečnostné komunitné fóra

---

**🔒 Posilnite svoj bezpečnostný postoj s Ghost - ale vždy najprv testujte.**

```powershell
# Začnite s hodnotením, nie s predpokladmi
Get-Ghost
```

**⭐ Označte hviezdicou tento repozitár, ak Ghost pomáha zlepšiť váš bezpečnostný postoj!**