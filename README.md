# Holidays

Data and APIs for public/bank holidays in [supported countries](#countries).

## Why?

To add a [minor feature](https://github.com/discord-tickets/bot/issues/403) to one of my other projects,
I needed a simple way to check if today is a holiday that worked for most countries, and I wasn't satisfied with the existing solutions.
Unfortunately, holidays are not as simple as they seem (*cough* Scotland).

### What's wrong with existing solutions?

Most of them work, but after looking at several open-source projects that calculate dates,
I was stuck thinking about how the code would be better represented as data.

- <https://www.gov.uk/bank-holidays.json>: only works for the UK
- [Nager.Date](https://github.com/nager/Nager.Date): accurate, but the API isn't flexible enough to overcome regional inconsistencies, not multi-lingual
- [holidayapi.com](https://holidayapi.com/): stupidly expensive
- [timeanddate.com](https://dev.timeanddate.com/holidays/): probably very good, but even more stupidly expensive
- [Azure Open Datasets](https://learn.microsoft.com/en-us/azure/open-datasets/dataset-public-holidays): difficult to access, probably doesn't get updated
- [enrico](https://github.com/jurajmajer/enrico): weird API and uses XML
- [python-holidays](https://github.com/dr-prodigy/python-holidays): excellent, but I didn't want to make an API in python
- [workalendar](https://github.com/workalendar/workalendar): good, but python again
- [date-holidays](https://github.com/commenthol/date-holidays): FINALLY! someone decided to make data with rules instead of code.... but not well.
In my opinion, its far more confusing and difficult to follow or update than any of the solutions above that use code

### Goals and scope

There have been many changed and additional UK holidays in the last few years,
so this was made with the following goals in mind:

## Limitations

- Although it can be if someone does the research, this shouldn't be expected to be historically accurate.
- https://www.officeholidays.com/countries/united-kingdom https://support.google.com/calendar/answer/6084659

## [HTTP API](https://github.com/eartharoid/holidays/tree/main/api#readme)

Data for the last decade, the current decade, and the next decade (currently 2010-2039 inclusive)
is available for [supported countries](#countries) with the free API.

[**Read the documentation →**](https://github.com/eartharoid/holidays/tree/main/api#readme)

## Libraries

### JavaScript

#### [@eartharoid/holidays](https://github.com/eartharoid/holidays/tree/main/packages/holidays.js#readme)

This provides some helper functions for working with the computed data, such as getting the next holiday, checking if today is a holiday, etc.

Must be paired with `@eartharoid/holidays-calculator` or
pre-computed data (e.g. `@eartharoid/holidays-static`)
to be useful.

#### [@eartharoid/holidays-calculator](https://github.com/eartharoid/holidays/tree/main/packages/holidays-calculator.js#readme)

This is the core library that calculates the dates of holidays in a given year using
[the rules data](https://github.com/eartharoid/holidays/tree/main/data).
It is used to generate the static data files in [`dist`](https://github.com/eartharoid/holidays/tree/main/dist)
and `@eartharoid/holidays-static`.

#### [@eartharoid/holidays-static](https://github.com/eartharoid/holidays/tree/main/packages/holidays-static.js#readme)

Pre-computed data, as in [`dist`](https://github.com/eartharoid/holidays/tree/main/dist), ready for use with 
`@eartharoid/holidays`.

## Static files

You can use these JSON files in your non-JavaScript projects.
All of the last decade, the current decade, and the next decade is available (currently 2010-2039 inclusive).
The files are available in the `dist` directory and can be downloaded from the CDN:

```
https://cdn.jsdelivr.net/gh/eartharoid/holidays/dist/v1/[year]/[country].json
```

e.g. <https://cdn.jsdelivr.net/gh/eartharoid/holidays/dist/v1/2023/gb.json>

> **Warning** You should update local copies at least every 3 months to ensure new holidays are included.

## Countries

Please consider sponsoring (or donating to) your country's contributors.

- [x] United Kingdom (GB) - [@eartharoid](https://github.com/eartharoid)

## Contributing

Please help to add countries and missing or incorrect holidays.

**Read the [contributing guidelines](/eartharoid/holidays/blob/main/docs/CONTRIBUTING.md) for more information.**

## License

Data (`data/*.yml`, `dist/v1/*.json`, and output from the library and API) is available under the [Open Database License](/eartharoid/holidays/blob/main/dist/LICENSE).

Everything else is licensed under the [MIT License](/eartharoid/holidays/blob/main/LICENSE).