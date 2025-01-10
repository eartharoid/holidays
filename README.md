# 🚧 Work in progress 🚧

> https://github.com/workalendar/workalendar/blob/master/workalendar/europe/united_kingdom.py
> https://github.com/workalendar/workalendar/blob/master/workalendar/europe/united_kingdom.py
> https://www.ukbankholidays.co.uk/
> https://en.wikipedia.org/wiki/Wedding_of_Princess_Anne_and_Mark_Phillips
> https://en.wikipedia.org/wiki/Public_holidays_in_the_United_Kingdom
> https://github.com/commenthol/date-holidays/blob/master/docs/specification.md#citations-sources-and-attribution
> https://github.com/commenthol/date-holidays/blob/master/docs/specification.md#types-of-holidays

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

#### Limitations

- Although it can be if someone does the research, this shouldn't be expected to be historically accurate.
- https://www.officeholidays.com/countries/united-kingdom https://support.google.com/calendar/answer/6084659

## Usage

You can use the data either

- through the [HTTP API](/api#readme)
- by downloading or building a database (which can optionally queried with a helper library)

## [HTTP API](/api#readme)

Data for the last decade, the current decade, and the next decade (currently 2010-2039 inclusive)
is available for [supported countries](#countries) with the free API.

[**Read the documentation →**](/api#readme)


## Databases

These URLs have a cache time of 1 week.
You should update local copies at least every few months to ensure correctness.

```
https://static.eartharoid.me/holidays/v1/<country>.<size>.<format>
```

> [!NOTE]
> `<country>` may be an ISO 3166-1 alpha-2 country code, or `global`.

### Sizes

| Size | Years                                     |
| ---- | ----------------------------------------- |
| `xs` | (**1**) current year                      |
| `sm` | (**3**) previous, current, & next year    |
| `lg` | (**11**) current year ± 5 years           |
| `xl` | (**30**) previous, current, & next decade |

### Formats

- `sqlite`
- `json`

Examples:
```
https://static.eartharoid.me/holidays/v1/global.xl.sqlite
https://static.eartharoid.me/holidays/v1/gb.sm.json
```

## Libraries

- [JavaScript](/packages/holidays.js#readme)

## Countries

Please consider sponsoring or donating to your country's contributors.

> [!NOTE]
> what about international calendars?

| Country        | Code | From | Contributors                                 |
| -------------- | ---- | ---- | -------------------------------------------- |
| United Kingdom | `GB` | 1995 | [@eartharoid](https://github.com/eartharoid) |


## Contributing

Please help to add countries and missing or incorrect holidays.

**Read the [contributing guidelines](/eartharoid/holidays/blob/main/docs/CONTRIBUTING.md) for more information.**

## License

Data (`data/*.yml`) is available under the [Open Database License](/eartharoid/holidays/blob/main/dist/LICENSE).

Everything else is licensed under the [MIT License](/eartharoid/holidays/blob/main/LICENSE).