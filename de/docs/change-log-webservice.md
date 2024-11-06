Der OpenHolidays API Web-Service ist [Open Source](https://github.com/openpotato/openholidaysapi) unter GitHub.
Dort kann die detailierte [Commit-Historie](https://github.com/openpotato/openholidaysapi/commits/develop/) eingesehen werden. Dieses Änderungslog dient als zusammenfassender Überblick der Änderungen.

Wir halten uns dabei weitestgehend an die Empfehlungen aus dem Community-Projekt [Keep a Changelog](https://keepachangelog.com/de).

## 0.1.0 <small>_ 06. November 2024</small>

**Hinzugefügt:**

+ Neue Länder zu AppSettings hinzugefügt

**Geändert:**

+ Breaking API change: Neuer Aufzählungstyp `RegionalScope` mit 3 Werten (`National`, `Regional`, `Local`) hinzugefügt
+ Breaking API change: Neuer Aufzählungstyp `TemporalScope` mit 2 Werten (`FullDay`, `HalfDay`) hinzugefügt
+ Breaking API change: Das Attribut `quality` (Aufzählungstyp `HolidayQuality`) gibt es nicht mehr
+ Breaking API change: Der Aufzählungstyp `HolidayType` hat jetzt (wieder) 3 Werte (`National`, `Regional`, `Local`) weniger und gleichzeitig einen Wert (`Optional`) hinzubekommen.

## 0.0.9 <small>_ 12. Dezember 2023</small>

**Hinzugefügt:**

+ Neue Länder zu AppSettings hinzugefügt

**Geändert:**

+ Update auf .NET 8
+ Breaking API change: Der Aufzählungstyp `HolidayType` hat 3 neue Werte bekommen (`National`, `Regional`, `Local`)
+ Breaking API change: Neuer Aufzählungstyp `HolidayQuality` (`Mandatory` oder `Optional`) hinzugefügt

## 0.0.8 <small>_ 24. Oktober 2023</small>

**Hinzugefügt:**

+ Neue Länder zu AppSettings hinzugefügt

## 0.0.7 <small>_ 10. August 2023</small>

**Hinzugefügt:**

+ Neue Länder zu AppSettings hinzugefügt

## 0.0.6 <small>_ 21. Januar 2023</small>

**Hinzugefügt:**

+ CORS-Unterstützung hinzugefügt
+ Neue Länder zu AppSettings hinzugefügt

**Geändert:**

+ Breaking API change: `Categories`, `Names` und `Comments` umbenannt in `Category`, `Name` und `Comment` 
+ Breaking API change: Entität `OUnit` entfernt. 
+ Breaking API change: Aufzählungstyp `HolidayDetails` entfernt. 

## 0.0.5 <small>_ 05. Januar 2023</small>

**Geändert:**

+ Breaking API change: `Categories` und `Parent` für Verwaltungseinheiten hinzugefügt
+ Breaking API change: `OfficalNames` von Ländern entfernt

## 0.0.4 <small>_ 21. Dezember 2022</small>

**Geändert:**

+ Breaking API change: Refactoring der Ländernamen und der Ferientypen

## 0.0.3 <small>_ 01. Dezember 2022</small>

**Geändert:**

+ Update auf .NET 7

## 0.0.2 <small>_ 16. September 2022</small>

+ Erste Veröffentlichung