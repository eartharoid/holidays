# Holidays

An API, JavaScript library, and static data files for information about public holidays in [supported countries](#countries),
created because [Nager.Date](https://github.com/nager/Nager.Date) wasn't good enough, and $349/year for [HolidayAPI](https://holidayapi.com/) is ridiculous.

Although it can be if someone puts the time in, this shouldn't be expected to be historically accurate.

## [HTTP API](https://github.com/eartharoid/holidays/tree/main/api#readme)

Data for the years 1950 to 2050 inclusive is available for [supported countries](#countries) with the free API.

[**Read the documentation.**](https://github.com/eartharoid/holidays/tree/main/api#readme)

## Libraries

### JavaScript

#### [`@eartharoid/holidays-calculator`](https://github.com/eartharoid/holidays/tree/main/packages/holidays-calculator.js#readme)

This is the core library that calculates the dates of holidays in a given year using [the rules data](https://github.com/eartharoid/holidays/tree/main/data).
it is used to generate the static data files in [`dist`](https://github.com/eartharoid/holidays/tree/main/dist) and [`@eartharoid/holidays-static`](https://github.com/eartharoid/holidays/tree/main/packages/holidays-static.js#readme).


[**Read the documentation →**](https://github.com/eartharoid/holidays/tree/main/packages/holidays-calculator.js#readme)

#### [`@eartharoid/holidays-helpers`](https://github.com/eartharoid/holidays/tree/main/packages/holidays-helpers.js#readme)

This provides some helper functions for working with the computed data, such as getting the next holiday, checking if today is a holiday, etc.
It doesn't have any bundled data.


[**Read the documentation →**](https://github.com/eartharoid/holidays/tree/main/packages/holidays-helpers.js#readme)

#### [`@eartharoid/holidays`](https://github.com/eartharoid/holidays/tree/main/packages/holidays.js#readme)

This combines
[`@eartharoid/holidays-calculator`](https://github.com/eartharoid/holidays/tree/main/packages/holidays-calculator.js#readme)
and
[`@eartharoid/holidays-helpers`](https://github.com/eartharoid/holidays/tree/main/packages/holidays-helpers.js#readme)
to make working with holidays easier.

Computing the data on the fly is slow, so you should use the faster
[`@eartharoid/holidays-static`](https://github.com/eartharoid/holidays/tree/main/packages/holidays-static.js#readme)
library if possible, as it comes with pre-computed data.

[**Read the documentation →**](https://github.com/eartharoid/holidays/tree/main/packages/holidays.js#readme)

#### [`@eartharoid/holidays-static`](https://github.com/eartharoid/holidays/tree/main/packages/holidays-static.js#readme) **(recommended)**

This is the same as,
[`@eartharoid/holidays-helpers`](https://github.com/eartharoid/holidays/tree/main/packages/holidays-helpers.js#readme),
but with precomputed data for all of the last decade, the current decade, and the next decade is available (currently 2010-2039 inclusive).

[**Read the documentation →**](https://github.com/eartharoid/holidays/tree/main/packages/holidays-static.js#readme)

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

**Please consider sponsoring (or donating to) your country's contributors.**

- [x] **United Kingdom (GB)** - [@eartharoid](https://github.com/eartharoid)

## Contributing

Please help to add countries and missing or incorrect holidays.

**Read the [contributing guidelines](/eartharoid/holidays/blob/main/docs/CONTRIBUTING.md) for more information.**

## License

Data (`data/*.yml`, `dist/v1/*.json`, and output from the library and API) is available under the [Open Database License](/eartharoid/holidays/blob/main/dist/LICENSE).

Everything else is licensed under the [MIT License](/eartharoid/holidays/blob/main/LICENSE).