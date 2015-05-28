# Development - Rails - Standardize Dates and Times

This document outlines best practices regarding the format standardization of
dates and times within a Rails application.

## Define all formats within locale files

* Update the en.yml (and other locale files) to include date and time formatting

* Below is an example of how to format several Date and Time types:

```

en:
  date:
    formats:
      standard: "%m/%d/%Y"
      unique: "%Y-%m-%d"

  datetime:
    formats:
      standard: "%b %d %Y %H:%M"

  time:
    formats:
      standard: "%b %d %Y %H:%M"

```

## Use the locale formats for both display and for testing

* In order to use the locale-defined formats, use the following syntax:

```

I18n.l(Date.today, format: :standard)

```

** The `I18n.l` method pulls the format from the configured locale file.
** This makes universal formatting changes are simple.
