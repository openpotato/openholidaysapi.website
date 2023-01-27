**OpenHolidays API** ist ein kleines [Open Data-Projekt](https://opendatahandbook.org/guide/de/what-is-open-data/), das öffentliche Daten zu gesetzlichen Feiertagen und Schulferien sammelt und über eine offene REST-API-Schnittstelle verfügbar macht. Unterstützt werden derzeit folgende Länder:

+ Belgien (Feiertage und Schulferien ab 2020)
+ Bulgarien (Feiertage und Schulferien ab 2020)
+ Deutschland (Feiertage und Schulferien ab 2020)
+ Estland (Feiertage und Schulferien ab 2020)
+ Frankreich (Feiertage und Schulferien ab 2020)
+ Irland (Feiertage und Schulferien ab 2020)
+ Kroatien (Feiertage und Schulferien ab 2020)
+ Lettland (Feiertage und Schulferien ab 2020)
+ Liechtenstein (Feiertage und Schulferien ab 2020)
+ Litauen (Feiertage und Schulferien ab 2020)
+ Luxemburg (Feiertage und Schulferien ab 2020)
+ Niederlande (Feiertage und Schulferien ab 2020)
+ Polen (Feiertage und Schulferien ab 2020)
+ Schweiz (Feiertage und Schulferien ab 2020)
+ Slowakei (Feiertage und Schulferien ab 2020)
+ Tschechien (Feiertage und Schulferien ab 2020)
+ Ungarn (Feiertage und Schulferien ab 2020)
+ Österreich (Feiertage und Schulferien ab 2020)

Feiertage und Ferientermine werden wahlweise als [JSON](https://datatracker.ietf.org/doc/html/rfc7159) oder im [iCal-Format](https://datatracker.ietf.org/doc/html/rfc5545) zurückgeliefert.

## Los geht's

Der einfachste Weg, die API zu nutzen, ist der Weg über die Kommandozeile. Wir werden in diesem Kapitel mit der Kommandozeilenanwendung [curl](https://curl.se/) arbeiten. 

Unter Linux ist `curl` in der Regel vorinstalliert. Unter Windows ist `curl` als Alias des Cmdlet [Invoke-WebRequest](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/invoke-webrequest) definiert, kann also via Powershell genutzt werden. Die hier verwendeten Befehlsfolgen variieren leicht, daher werden sie für Powershell 7 (Windows) und Bash (Linux) getrennt angegeben.

### Staaten

Zunächst fragen wir ab, welche Länder von der OpenHolidays API unterstützt werden:

=== "Powershell 7"

    ``` powershell
    curl -X GET 'https://openholidaysapi.org/Countries' -H 'accept: text/json' | ConvertFrom-Json | ConvertTo-Json
    ```

=== "Bash"

    ``` bash
    curl -X GET 'https://openholidaysapi.org/Countries' -H 'accept: text/json' | json_pp
    ```

Die Codes der Länder entsprechen dem Standard [ISO 3166-1](https://www.iso.org/iso-3166-country-codes.html).

### Sprachen

Die Namen der Feiertage bzw. Schulferien sind mehrsprachig gespeichert. In der Regel gibt es die Übersetzungen in den jeweiligen Amtssprachen eines Landes (z.B. polnisch für Polen) sowie eine Übersetzung ins Deutsche und Englische. 

Die von OpenHolidays API derzeit genutzten Sprachen lassen sich wie folgt abfragen: 

=== "Powershell 7"

    ``` powershell
    curl -X GET 'https://openholidaysapi.org/Languages' -H 'accept: text/json' | ConvertFrom-Json | ConvertTo-Json
    ```

=== "Bash"

    ``` bash
    curl -X GET 'https://openholidaysapi.org/Languages' -H 'accept: text/json' | json_pp
    ```

Die Codes der Sprachen entsprechen dem Standard [ISO 639-1](https://www.iso.org/iso-639-language-codes.html).

### Verwaltungseinheiten 

Pro Land können die relevanten subnationale Verwaltungseinheiten (z.B. Bundesländer, Schweizer Kantone oder Ferienzonen) abgefragt werden. Es werden nur dann Verwaltungseinheiten zurückgeliefert, wenn sie relevant für die Filterung von Feiertagen und/oder Schulferien sind.

Hier eine Beispielabfrage für Deutschland (DE): 

=== "Powershell 7"

    ``` powershell
    curl -X GET 'https://openholidaysapi.org/Subdivisions?countryIsoCode=DE' -H 'accept: text/json' | ConvertFrom-Json | ConvertTo-Json
    ```

=== "Bash"

    ``` bash
    curl -X GET 'https://openholidaysapi.org/Subdivisions?countryIsoCode=DE' -H 'accept: text/json' | json_pp
    ```

Die Codes der Verwaltungseinheiten orientieren sich an dem Standard [ISO 3166-2](https://www.iso.org/iso-3166-country-codes.html) sowie an der Kodierliste [Hierarchical administrative subdivision codes (HASC)](http://www.statoids.com/ihasc.html).

### Feiertage

Feiertage können pro Land und für einen beliebigen Zeitraum (der nicht größer als drei Jahre sein darf) abgefragt werden. Optional können die Namen der Feiertage auf eine bestimmte Sprache eingeschränkt werden. 

Hier eine Beispielabfrage für Schweizer Feiertage zwischen dem 1. Januar 2022 und dem 30. Juni 2022 mit deutscher Ausgabesprache: 

=== "Powershell 7"

    ``` powershell
    curl -X GET 'https://openholidaysapi.org/PublicHolidays?countryIsoCode=CH&languageIsoCode=DE&validFrom=2022-01-01&validTo=2022-06-30' -H 'accept: text/json' | ConvertFrom-Json | ConvertTo-Json
    ```

=== "Bash"

    ``` bash
    curl -X GET 'https://openholidaysapi.org/PublicHolidays?countryIsoCode=CH&languageIsoCode=DE&validFrom=2022-01-01&validTo=2022-06-30' -H 'accept: text/json' | json_pp
    ```

Wer möchte, kann sich die Daten auch im iCal-Format zurückliefern lassen:

=== "Powershell 7"

    ``` powershell
    curl -X GET 'https://openholidaysapi.org/PublicHolidays?countryIsoCode=CH&languageIsoCode=DE&validFrom=2022-01-01&validTo=2022-06-30' -H 'accept: text/calendar'
    ```

=== "Bash"

    ``` bash
    curl -X GET 'https://openholidaysapi.org/PublicHolidays?countryIsoCode=CH&languageIsoCode=DE&validFrom=2022-01-01&validTo=2022-06-30' -H 'accept: text/calendar'
    ```

### Schulferien

Schulferien können pro Land und Verwaltungseinheit sowie für einen beliebigen Zeitraum (der nicht größer als drei Jahre sein darf) abgefragt werden. Optional können die Namen der Schulferien auf eine bestimmte Sprache eingeschränkt werden. 

Hier eine Beispielabfrage für Schulferien in Österreich zwischen dem 1. Januar 2022 und dem 31. Dezember 2022 für das Bundesland Kärnten mit englischer Ausgabesprache: 

=== "Powershell 7"

    ``` powershell
    curl -X GET 'https://openholidaysapi.org/SchoolHolidays?countryIsoCode=AT&subdivisionCode=AT-2&languageIsoCode=EN&validFrom=2022-01-01&validTo=2022-12-31' -H 'accept: text/json' | ConvertFrom-Json | ConvertTo-Json
    ```

=== "Bash"

    ``` bash
    curl -X GET 'https://openholidaysapi.org/SchoolHolidays?countryIsoCode=AT&subdivisionCode=AT-2&languageIsoCode=EN&validFrom=2022-01-01&validTo=2022-12-31' -H 'accept: text/json' | json_pp
    ```

Auch hier können die Daten wahlweise im iCal-Format zurückgeliefert werden:

=== "Powershell"

    ``` powershell
    curl -X GET 'https://openholidaysapi.org/SchoolHolidays?countryIsoCode=AT&subdivisionCode=AT-2&languageIsoCode=EN&validFrom=2022-01-01&validTo=2022-12-31' -H 'accept: text/calendar'
    ```

=== "Bash"

    ``` bash
    curl -X GET 'https://openholidaysapi.org/SchoolHolidays?countryIsoCode=AT&subdivisionCode=AT-2&languageIsoCode=EN&validFrom=2022-01-01&validTo=2022-12-31' -H 'accept: text/calendar'
    ```

## Tipps und Tricks

Um die Bildschirmausgabe von `curl` in eine Datei zu schreiben, kann der Parameter `-o` genutzt werden. Das folgende Beispiel speichert alle deutschen Feiertage für 2022 in eine iCal-Datei, die man z.B. nach Outlook importieren kann. 

=== "Powershell 7"

    ``` powershell
    curl -X GET 'https://openholidaysapi.org/PublicHolidays?countryIsoCode=DE&validFrom=2022-01-01&validTo=2022-12-31' -H 'accept: text/calendar' -o 'kalendar.ics'
    ```

=== "Bash"

    ``` bash
    curl -X GET 'https://openholidaysapi.org/PublicHolidays?countryIsoCode=DE&validFrom=2022-01-01&validTo=2022-12-31' -H 'accept: text/calendar' -o 'kalendar.ics'
    ```
