**OpenHolidays API** is a small [Open Data project](https://opendatahandbook.org/guide/en/what-is-open-data/) that collects public holiday and school holiday data and makes it available via an open REST API interface. The following countries are currently supported:

+ Albanien (public holidays and school holidays from 2020)
+ Andorra (public holidays and school holidays from 2020)
+ Austria (public holidays and school holidays from 2020)
+ Belarus (public holidays and school holidays from 2020)
+ Belgium (public holidays and school holidays from 2020)
+ Bulgaria (public holidays and school holidays from 2020)
+ Croatia (public holidays and school holidays from 2020)
+ Czechia (public holidays and school holidays from 2020)
+ Estonia (public holidays and school holidays from 2020)
+ France (public holidays and school holidays from 2020)
+ Germany (public holidays and school holidays from 2020)
+ Hungary (public holidays and school holidays from 2020)
+ Ireland (public holidays and school holidays from 2020)
+ Italy (public holidays and school holidays from 2020)
+ Latvia (public holidays and school holidays from 2020)
+ Liechtenstein (public holidays and school holidays from 2020)
+ Lithuania (public holidays and school holidays from 2020)
+ Luxembourg (public holidays and school holidays from 2020)
+ Malta (public holidays and school holidays from 2020)
+ Moldova (public holidays and school holidays from 2020)
+ Monaco (public holidays and school holidays from 2020)
+ Netherlands (public holidays and school holidays from 2020)
+ Poland (public holidays and school holidays from 2020)
+ Portugal (public holidays and school holidays from 2020)
+ Romania (public holidays and school holidays from 2020)
+ San Marino (public holidays and school holidays from 2020)
+ Slovakia (public holidays and school holidays from 2020)
+ Slovenia (public holidays and school holidays from 2020)
+ Spain (public holidays and school holidays from 2020)
+ Switzerland (public holidays and school holidays from 2020)
+ Vatican City (public holidays from 2020)

Public holidays and school holidays are returned optionally as [JSON](https://datatracker.ietf.org/doc/html/rfc7159) or in [iCal format](https://datatracker.ietf.org/doc/html/rfc5545).

## Let's start

The easiest way to use the API is via the command line. We will work with the command line application [curl](https://curl.se/) in this chapter. 

Under Linux, `curl` is usually pre-installed. Under Windows, `curl` is defined as an alias of the [Invoke-WebRequest](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.utility/invoke-webrequest) cmdlet, so it can be used via Powershell. The command sequences used here vary slightly, so they are given separately for Powershell 7 (Windows) and Bash (Linux).

### Countries

First, we query which countries are supported by the OpenHolidays API:

=== "Powershell 7"

    ``` powershell
    curl -X GET 'https://openholidaysapi.org/Countries' -H 'accept: text/json' | ConvertFrom-Json | ConvertTo-Json
    ```

=== "Bash"

    ``` bash
    curl -X GET 'https://openholidaysapi.org/Countries' -H 'accept: text/json' | json_pp
    ```

The codes of the countries correspond to the standard [ISO 3166-1](https://www.iso.org/iso-3166-country-codes.html).

### Languages

The names of public holidays or school holidays are stored in several languages. Usually there are translations in the respective official languages of a country (e.g. Polish for Poland) as well as a translation into German and English. 

The languages currently used by OpenHolidays API can be queried as follows: 

=== "Powershell 7"

    ``` powershell
    curl -X GET 'https://openholidaysapi.org/Languages' -H 'accept: text/json' | ConvertFrom-Json | ConvertTo-Json
    ```

=== "Bash"

    ``` bash
    curl -X GET 'https://openholidaysapi.org/Languages' -H 'accept: text/json' | json_pp
    ```

The codes of the languages correspond to the standard [ISO 639-1](https://www.iso.org/iso-639-language-codes.html).

### Subdivisions

For each country, the relevant principal subdivisions (e.g. federal states, Swiss cantons or holiday zones) can be queried. Administrative units are only returned if they are relevant for the filtering of public holidays and/or school holidays.

Here is an example query for Germany (DE): 

=== "Powershell 7"

    ``` powershell
    curl -X GET 'https://openholidaysapi.org/Subdivisions?countryIsoCode=DE' -H 'accept: text/json' | ConvertFrom-Json | ConvertTo-Json
    ```

=== "Bash"

    ``` bash
    curl -X GET 'https://openholidaysapi.org/Subdivisions?countryIsoCode=DE' -H 'accept: text/json' | json_pp
    ```

The codes of the subdivisions are based on the standard [ISO 3166-2](https://www.iso.org/iso-3166-country-codes.html) as well as the coding list [Hierarchical administrative subdivision codes (HASC)](http://www.statoids.com/ihasc.html).

### Public holidays

Public holidays can be queried per country and for any period (which must not be greater than three years). Optionally, the names of the public holidays can be restricted to a specific language. 

Here is an example query for Swiss public holidays between 1 January 2022 and 30 June 2022 with German output language: 

=== "Powershell 7"

    ``` powershell
    curl -X GET 'https://openholidaysapi.org/PublicHolidays?countryIsoCode=CH&languageIsoCode=DE&validFrom=2022-01-01&validTo=2022-06-30' -H 'accept: text/json' | ConvertFrom-Json | ConvertTo-Json
    ```

=== "Bash"

    ``` bash
    curl -X GET 'https://openholidaysapi.org/PublicHolidays?countryIsoCode=CH&languageIsoCode=DE&validFrom=2022-01-01&validTo=2022-06-30' -H 'accept: text/json' | json_pp
    ```

If you wish, you can also have the data returned in iCal format:

=== "Powershell 7"

    ``` powershell
    curl -X GET 'https://openholidaysapi.org/PublicHolidays?countryIsoCode=CH&languageIsoCode=DE&validFrom=2022-01-01&validTo=2022-06-30' -H 'accept: text/calendar'
    ```

=== "Bash"

    ``` bash
    curl -X GET 'https://openholidaysapi.org/PublicHolidays?countryIsoCode=CH&languageIsoCode=DE&validFrom=2022-01-01&validTo=2022-06-30' -H 'accept: text/calendar'
    ```

### School holidays

School holidays can be queried per country and administrative unit as well as for any period (which must not be longer than three years). Optionally, the names of the school holidays can be restricted to a specific language. 

Here is an example query for school holidays in Austria between 1 January 2022 and 31 December 2022 for the federal state of Carinthia with English output language: 

=== "Powershell 7"

    ``` powershell
    curl -X GET 'https://openholidaysapi.org/SchoolHolidays?countryIsoCode=AT&subdivisionCode=AT-KÄ&languageIsoCode=EN&validFrom=2022-01-01&validTo=2022-12-31' -H 'accept: text/json' | ConvertFrom-Json | ConvertTo-Json
    ```

=== "Bash"

    ``` bash
    curl -X GET 'https://openholidaysapi.org/SchoolHolidays?countryIsoCode=AT&subdivisionCode=AT-KÄ&languageIsoCode=EN&validFrom=2022-01-01&validTo=2022-12-31' -H 'accept: text/json' | json_pp
    ```

Here, too, the data can optionally be returned in iCal format:

=== "Powershell"

    ``` powershell
    curl -X GET 'https://openholidaysapi.org/SchoolHolidays?countryIsoCode=AT&subdivisionCode=AT-KÄ&languageIsoCode=EN&validFrom=2022-01-01&validTo=2022-12-31' -H 'accept: text/calendar'
    ```

=== "Bash"

    ``` bash
    curl -X GET 'https://openholidaysapi.org/SchoolHolidays?countryIsoCode=AT&subdivisionCode=AT-KÄ&languageIsoCode=EN&validFrom=2022-01-01&validTo=2022-12-31' -H 'accept: text/calendar'
    ```

## Tips and tricks

To write the screen output of `curl` to a file, the parameter `-o` can be used. The following example saves all German public holidays for 2022 in an iCal file that can be imported into Outlook, for example.

=== "Powershell 7"

    ``` powershell
    curl -X GET 'https://openholidaysapi.org/PublicHolidays?countryIsoCode=DE&validFrom=2022-01-01&validTo=2022-12-31' -H 'accept: text/calendar' -o 'kalendar.ics'
    ```

=== "Bash"

    ``` bash
    curl -X GET 'https://openholidaysapi.org/PublicHolidays?countryIsoCode=DE&validFrom=2022-01-01&validTo=2022-12-31' -H 'accept: text/calendar' -o 'kalendar.ics'
    ```
