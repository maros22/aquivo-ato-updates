# Aquivo ATO · aktualizácie firmvéru

Verejné podpísané vydania pre **Aquivo ATO**, ESP32-C6. Aktuálna verzia: **1.0.2**.

## Aktualizácia

Vo webe ATO otvor **Nové verzie firmvéru** → **Overiť nové vydanie**. Novšiu verziu nainštaluj v SERVICE so zastavenou pumpou. Kontrola beží aj automaticky; inštalácia vyžaduje tvoj pokyn. Nie je potrebný GitHub účet ani kľúč.

Pri ručnej aktualizácii stiahni z [Releases](https://github.com/maros22/aquivo-ato-updates/releases/latest) súbory `Aquivo-ATO-OTA-X.Y.Z.bin` a zodpovedajúci `.manifest.json`. Vyber oba na webe ATO. ZIP nie je firmvér.

Prvý prechod z RC13 vyžaduje USB balík výrobcu; starší firmvér ešte OTA nemá. Po migrácii skontroluj zachovanie kalibrácie, zásobníka a počítadiel. Tento balík nie je určený pre Dose 3 ani Z-Wave ATO.

## Overenie

ATO kontroluje model, veľkosť, verziu, SHA256 a podpis ECDSA-P256. Neplatný balík sa neaktivuje. Pre kontrolu cez HTTPS potrebuje Wi-Fi a synchronizovaný čas. Pri OTA sa zapisuje neaktívny oddiel; funkčnosť novej aplikácie sa overí po štarte a pri zlyhaní sa použije predchádzajúci oddiel.

Podpisy chránia cestu aktualizácie. Hardvérové Secure Boot ani Flash Encryption tým nie sú zapnuté. Zdrojový kód, súkromný podpisový kľúč, konfigurácie a zálohy zariadení sa tu nezverejňujú.

## Karta Home Assistant

[Karta, HACS a návod](https://github.com/maros22/aquivo-ato-card). Kartu a lokálny návod možno stiahnuť aj priamo z webu ATO cez **Karta pre Home Assistant**.

## Vydanie 1.0.2

Úplné označenie Aquivo: model AQUIVO-ATO-ZB, výrobca Aquivo, karta custom:aquivo-ato-card, súbory aquivo-ato-card.js a integrácia aquivo_ato. MQTT témy sú aquivo/ato-<MAC>/…; pri prechode v Homey nahraď Topics v existujúcom zariadení podľa exportu z webu ATO. Existujúce zariadenie a jeho históriu v HASS nemaž. Pri migrácii obnov interview a konfiguráciu v Zigbee2MQTT.



Pribalená karta1.0.2 a lokálny návod. Riadenie pumpy, kalibrácia, počítadlá a prihlasovacie údaje pripojení sa nemenia.

## Základ vydania1.0.0

- Produkčný web, karta a automatický odkaz na aktuálnu DHCP adresu.
- Verejné podpísané OTA bez zákazníckych kľúčov.
- Zachovanie kalibrácie, konfigurácie, objemov a Zigbee/MQTT pripojenia pri migrácii.
- Trvalé ochranné 24-hodinové obdobie aj po reštarte. Bez overeného času sa neznámy čas bez napájania nezapočíta.

Ochranný 24-hodinový limit ATO a údaj „Dopustené dnes“ z histórie HASS sú samostatné hodnoty. Objemy sú odhad podľa kalibrácie pumpy.
