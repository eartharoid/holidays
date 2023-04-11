# Holidays

A REST API, JavaScript library, and static data files for information about public holidays.

Created because [Nager.Date](https://github.com/nager/Nager.Date) wasn't good enough, and $349/year for [HolidayAPI](https://holidayapi.com/) is ridiculous.


## [API](https://github.com/eartharoid/holidays/tree/main/api)

[**Read the documentation.**](https://github.com/eartharoid/holidays/tree/main/api#readme)

## [Javascript library](https://github.com/eartharoid/holidays/tree/main/lib)

```
npm install @eartharoid/holidays
```

[**Read the documentation.**](https://github.com/eartharoid/holidays/tree/main/lib#readme)

## Static files

The library is used to build static files that you can use in your non-JavaScript projects.

All of the last decade, the current decade, and the next decade are available (currently 2010-2039 inclusive).


> **Warning**
> You should update local copies at least every 3 months to ensure new holidays are included.

The files are available in the `dist` directory and can be downloaded from the CDN:

```
https://cdn.jsdelivr.net/gh/eartharoid/holidays/dist/v1/[year]/[country].json
```

e.g. <https://cdn.jsdelivr.net/gh/eartharoid/holidays/dist/v1/2023/gb.json>

## Countries

- [x] **United Kingdom (GB)** - @eartharoid

## Contributing

Please help to add countries and missing or incorrect holidays.

**Read the [contributing guidelines](/eartharoid/holidays/blob/main/CONTRIBUTING.md) for more information.**

## License

Data (files in `dist/`) is licensed under the [Open Database License](/eartharoid/holidays/blob/main/dist/LICENSE).

All code (everything else) is licensed under the [MIT License](/eartharoid/holidays/blob/main/LICENSE).