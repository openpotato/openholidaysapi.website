# Error Messages

The OpenHolidays API returns error messages as JSON objects formatted according to RFC 9457.

## What is RFC 9457?

[RFC 9457](https://www.rfc-editor.org/rfc/rfc9457) is a standard by the Internet Engineering Task Force (IETF) that defines a structured format for representing errors in HTTP APIs.

## Problem Details

At the core of RFC 9457 is the *Problem Details* object, a JSON document included in the response body of an API query when errors occur. The OpenHolidays API implements it with the following fields:

`type` (string)

:   A URI reference that identifies the type of error. This is typically a reference to the specification of the HTTP status code on the web.

    Example: `"https://tools.ietf.org/html/rfc9110#section-15.5.1"`

`title` (string)

:   A short, human-readable summary of the problem.

    Example: `"One or more validation errors occurred."`

`status` (integer)

:   The HTTP status code describing the error. It should match the status code in the HTTP response header.

    Example: `400`

`errors` (object)

:   (Optional) A JSON object containing additional details about the error.

    Example: 
    ```json
    {
        "validTo": [
          "The validTo field is required."
        ]
    }
    ```

`traceId` (string)

:   A unique identifier that can be used for tracing in distributed systems.

    Example: `"00-abc123def456789ghi-xyz987uvw654321tqr-01"`

!!! note "Extension Members"

    The fields `type`, `title`, and `status` are well-defined in RFC 9457. The fields `errors` and `traceId` are known as *Extension Members*, which extend the standard fields.

## Example

The API call

``` 
https://openholidaysapi.org/PublicHolidays?countryIsoCode=DE&validFrom=2020-01-01&validTo=2023-12-31
``` 

results in the following error message:

``` json
{
  "type": "https://tools.ietf.org/html/rfc9110#section-15.5.1",
  "title": "One or more validation errors occurred.",
  "status": 400,
  "errors": {
    "pageSize": [
      "The field pageSize must be between 1 and 50."
    ]
  },
  "traceId": "00-0274bb16dcdf462bf27a7faedeacc79f-05c5cd5b5d411f8e-00"
}
```

Analysis of the error:

+ The server cannot process the request because it is not properly formulated (HTTP error code 400: Bad Request).

+ And yes, the date range is greater than 3 years.
