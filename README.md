# normalizer
Python script to normalize data from a csv for further analysis/processing/prodding.

Goals:
* The entire CSV is in the UTF-8 character set.
* The `Timestamp` column should be formatted in ISO-8601 format.
* The `Timestamp` column should be assumed to be in US/Pacific time;
  please convert it to US/Eastern.
* All `ZIP` codes should be formatted as 5 digits. If there are less
  than 5 digits, assume 0 as the prefix.
* The `FullName` column should be converted to uppercase. There will be
  non-English names.
* The `Address` column should be passed through as is, except for
  Unicode validation. Please note there are commas in the Address
  field; your CSV parsing will need to take that into account. Commas
  will only be present inside a quoted string.
* The `FooDuration` and `BarDuration` columns are in HH:MM:SS.MS
  format (where MS is milliseconds); please convert them to the
  total number of seconds expressed in floating point format.
  You should not round the result.
* The `TotalDuration` column is filled with garbage data. For each
  row, please replace the value of `TotalDuration` with the sum of
  `FooDuration` and `BarDuration`.
* The `Notes` column is free form text input by end-users; please do
  not perform any transformations on this column. If there are invalid
  UTF-8 characters, please replace them with the Unicode Replacement
  Character.

## Usage
`./normalizer < test.csv`
