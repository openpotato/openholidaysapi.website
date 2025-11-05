Der CodeListHub API Web-Service ist [Open Source](https://github.com/openpotato/codelisthub) unter GitHub. Dort kann die detailierte [Commit-Historie](https://github.com/openpotato/codelisthub/commits/develop/) eingesehen werden. Dieses Änderungslog dient als zusammenfassender Überblick der Änderungen.

Wir halten uns dabei weitestgehend an die Empfehlungen aus dem Community-Projekt [Keep a Changelog](https://keepachangelog.com/de).

## 0.2.0 <small>_ 05. November 2025</small>

**Hinzugefügt:**:

+ Neue `Holiday`-Eigenschaft `Tags` mit möglichen Werten `Recommended`, `Provisional`, `OneTime` und `Exception` hinzugefügt.
+ Neue `Holiday`-Eigenschaft `Groups` für das (besssere) Abbilden von Gruppierungen, die keine Verwaltungseinheiten sind (z.B. Ferienzonen), hinzugefügt.

**Geändert:**

+ Umfangreiches internes Refactoring 

## 0.1.0 <small>_ 06. November 2024</small>

**Hinzugefügt:**:

+ Neue `Holiday`-Eigenschaften `RegionalScope` und `TemporalScope` hinzugefügt.

**Geändert:**

+ Breaking change: `Holiday`-Eigenschaft `Quality` wurde in `Status` umbenannt.

## 0.0.2 <small>_ 16. September 2022</small>

+ Erste Veröffentlichung