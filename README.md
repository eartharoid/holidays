# Holidays

A REST API, JavaScript library, and static data files for information about public holidays in [supported countries](#countries),
created because [Nager.Date](https://github.com/nager/Nager.Date) wasn't good enough, and $349/year for [HolidayAPI](https://holidayapi.com/) is ridiculous.

Although it can be if someone puts the time in, this shouldn't be expected to be historically accurate.

## [API](https://github.com/eartharoid/holidays/tree/main/api)

The code for the API is in the [`api`](https://github.com/eartharoid/holidays/tree/main/api) directory.

[**Read the documentation.**](https://github.com/eartharoid/holidays/tree/main/api#readme)

## [Javascript library](https://github.com/eartharoid/holidays/tree/main/lib)

The code for the library is in the [`lib`](https://github.com/eartharoid/holidays/tree/main/lib) directory.

[**Read the documentation.**](https://github.com/eartharoid/holidays/tree/main/lib#readme)

## Static files

The library is used to build static files that you can use in your non-JavaScript projects.
All of the last decade, the current decade, and the next decade are available (currently 2010-2039 inclusive).
The files are available in the `dist` directory and can be downloaded from the CDN:

```
https://cdn.jsdelivr.net/gh/eartharoid/holidays/dist/v1/[year]/[country].json
```

e.g. <https://cdn.jsdelivr.net/gh/eartharoid/holidays/dist/v1/2023/gb.json>

> **Warning** You should update local copies at least every 3 months to ensure new holidays are included.
> 
## Countries

**Please consider sponsoring (or donating to) your country's contributors.**

- [x] **United Kingdom (GB)** - [@eartharoid](https://github.com/eartharoid)

## Contributing

Please help to add countries and missing or incorrect holidays.

**Read the [contributing guidelines](/eartharoid/holidays/blob/main/CONTRIBUTING.md) for more information.**

## License

Data (`data/*.yml`, `dist/v1/*.json`, and output from the library and API) is available under the [Open Database License](/eartharoid/holidays/blob/main/dist/LICENSE).

Everything else is licensed under the [MIT License](/eartharoid/holidays/blob/main/LICENSE).