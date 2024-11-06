The OpenHolidays API web service is [Open Source](https://github.com/openpotato/openholidaysapi) on GitHub.
The detailed [commit history](https://github.com/openpotato/openholidaysapi/commits/develop/) can be viewed there. This change log serves as a summarised overview of the changes.

We largely adhere to the recommendations from the community project [Keep a Changelog](https://keepachangelog.com).

## 0.1.0 <small>_ November 06, 2024</small>

**Added:**

+ New countries added to AppSettings

**Changed:**

+ Breaking API change: New enumeration type `RegionalScope` with 3 values (`National`, `Regional`, `Local`) added
+ Breaking API change: New enumeration type `TemporalScope` with 2 values (`FullDay`, `HalfDay`) added
+ Breaking API change: The attribute `quality` (enumeration type `HolidayQuality`) removed
+ Breaking API change: The enumeration type `HolidayType` has now (again) 3 values (`National`, `Regional`, `Local`) less and at the same time one value (`Optional`) added.

## 0.0.9 <small>_ December 12, 2023</small>

**Added:**

+ New countries added to AppSettings

**Changed:**

+ Update to .NET 8
+ Breaking API change: Enum type `HolidayType` has got 3 new values (`National`, `Regional`, `Local`)
+ Breaking API change: Added new enum type `HolidayQuality` (`Mandatory` oder `Optional`)

## 0.0.8 <small>_ October 24, 2023</small>

**Added:**

+ New countries added to AppSettings

## 0.0.7 <small>_ August 10, 2023</small>

**Added:**

+ New countries added to AppSettings

## 0.0.6 <small>_ January 21, 2023</small>

**Added:**

+ Added CORS support
+ New countries added to AppSettings

**Changed:**

+ Breaking API change: `Categories`, `Names` and `Comments` renamed to `Category`, `Name` and `Comment`
+ Breaking API change: Removed entity `OUnit`
+ Breaking API change: Removed enum type `HolidayDetails`

## 0.0.5 <small>_ January 05, 2023</small>

**Changed:**

+ Breaking change: Added `Categories` and `Parent` to administrative units (subdivisions)
+ Breaking change: Removed `OfficalNames` from countries

## 0.0.4 <small>_ December 21, 2022</small>

**Changed:**

+ Breaking change: Refactoring for official country names and holiday type

## 0.0.3 <small>_ December 01, 2022</small>

**Changed:**

+ Update to .NET 7

## 0.0.2 <small>_ September 16, 2022</small>

+ First publication
