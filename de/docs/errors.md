# Fehlermeldungen

Die OpenHolidays API liefert Fehlermeldungen als RFC 9457-formatierte JSON-Objekte zurück.

## Was ist RFC 9457?

[RFC 9457](https://www.rfc-editor.org/rfc/rfc9457) ist ein Standard der Internet Engineering Task Force (IETF), der ein strukturiertes Format zur Darstellung von Fehlern in HTTP-APIs definiert. 

## Problem Details

Im Zentrum von RFC 9457 steht das *Problem Details*-Objekt, ein JSON-Dokument, das bei Fehlern im Response-Body der API-Abfrage enthalten ist. OpenHolidays API implementiert es mit folgenden Feldern:

`type` (string)

:   Eine URI-Referenz, die den Typ des Fehlers identifiziert. Dies ist in der Regel ein Verweis auf die Spezifikation des HTTP-Statuscodes im Web.

    Beispiel: `"https://tools.ietf.org/html/rfc9110#section-15.5.1"`

`title` (string)

:   Eine kurze, menschenlesbare Zusammenfassung des Problems.

    Beispiel: `"One or more validation errors occurred."`

`status` (integer)

:   Der HTTP-Statuscode, der den Fehler beschreibt. Er sollte mit dem Statuscode im HTTP-Response-Header übereinstimmten.

    Beispiel: 400

`errors` (object)

:   (Optional) Eine JSON-Objekt mit weiteren Details zum Fehler.
   
    Beispiel: 
    ```
    {
        "validTo": [
          "The validTo field is required."
        ]
    }
    ```

`traceId` (string)

:   Ein eindeutiger Identifikator, der zur Nachverfolgung in verteilten Systemen genutzt werden kann.

    Beispiel: `"00-abc123def456789ghi-xyz987uvw654321tqr-01"`

!!! note "Extension Members"

    Die Felder `type`, `title` und `status` sind wohldefiniert in RFC 9457. Die Felder `errors` und `traceId` sind sogenannte *Extension Members*, also eine Erweiterung der Standardfelder.

## Beispiel

Der API-Aufruf

``` 
https://openholidaysapi.org/PublicHolidays?countryIsoCode=DE&validFrom=2020-01-01&validTo=2023-12-31
``` 

resultiert in folgender Fehlermeldung:

``` json
{
  "type": "https://tools.ietf.org/html/rfc9110#section-15.5.1",
  "title": "Bad Request",
  "status": 400,
  "detail": "The maximum date range is 1095 days.",
  "traceId": "00-abc123def456789ghi-xyz987uvw654321tqr-01"
}
```

Die Analyse des Fehlers:

+ Der Server kann die Anfrage nicht bearbeiten, da der Aufruf nicht korrekt formuliert ist (HTTP-Fehler-Code 400: Bad Request).

+ Und ja, so ist es auch, die Datumsspanne ist größer als 3 Jahre.
