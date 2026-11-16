# Check CSV column widths

Check that each CSV record has the same number of fields as the header.

Prerequisites — Python 3 and a UTF-8 comma-separated file with a header. Install the YAML using the [registry instructions](../../README.md).

```sh
sir run python-check-csv-columns --non-interactive --input=path=data.csv
```
