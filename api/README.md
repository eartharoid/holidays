# API

## Authentication

The API is **free** and unauthenticated, but **please [sponsor me](https://github.com/eartharoid/holidays?sponsor=1) if your project will make a lot of requests.**

I'd also appreciate it if you set the [`User-Agent`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/User-Agent) header to include your project's name and website.

Example:

```http
User-Agent: DiscordTickets/4.0.0 (https://discordtickets.app)
```

## Routes

**Prefix:** [`https://holidays.eartharoid.me/api/v1`](https://holidays.eartharoid.me/api/v1)

### `/list`

Returns all of a country's holidays for a given (or the current) year.

#### Request

##### Query parameters

Required parameters are marked with an asterisk (`*`).

| Name           | Type       | Default      | Description                                                                 |
| -------------- | ---------- | ------------ | --------------------------------------------------------------------------- |
| `country`*     | `string`   |              | ISO 3166-1 alpha-2 country code                                             |
| `year`         | `number`   | Current year | The year to get holidays of                                                 |
| `subdivisions` | `string[]` |              | Comma-separated list of the second part of the ISO 3166-2 subdivision codes |

###### Notes

- The `subdivisions` (country/province/region) codes are the **second part** of the ISO 3166-2 code, e.g. [`GB-SCT`](https://en.wikipedia.org/wiki/ISO_3166-2:GB) → `SCT`.
- If `subdivisions` are specified, the response will include holidays that apply to the whole country and holidays that apply to the specified subdivisions.
- If no `subdivisions` are specified, only holidays that apply to the whole country are returned.

##### Examples

###### Get this year's holidays for the UK

> **Note** Most holidays are slightly different in Scotland, so this won't return many results.

```http
GET https://holidays.eartharoid.me/api/v1/list?country=gb HTTP/1.1
```

###### Get 2024 holidays for England and Wales

> **Note** `eaw` also works.

```http
GET https://holidays.eartharoid.me/api/v1/list?country=gb&year=2024&subdivisions=eng,wls HTTP/1.1
```

#### Response

```json
[
  {
	"name": "Christmas Day",
	"localName": "Christmas Day",
	"actualDate": "2023-12-25",
	"observedDate": "2023-12-25",
	"subdivisions": null
  }
]
```


##### 404 Not Found

```json
{
  "error": "Invalid or unsupported country code"
}
```

### `/today`

Get today's holidays for a given country.

#### Request

##### Query parameters

Required parameters are marked with an asterisk (`*`).

| Name           | Type       | Default | Description                                       |
| -------------- | ---------- | ------- | ------------------------------------------------- |
| `country`*     | `string`   |         | ISO 3166-1 alpha-2 country code                   |
| `offset`       | `integer`  | 0       | UTC offset in minutes (to decide what *today* is) |
| `subdivisions` | `booelan`  | `false` | Include subdivision-specific holidays?            |
| `include`      | `string[]` |         | Ignore any holidays not listed                    |
| `exclude`      | `string[]` |         | Ignore listed holidays                            |

###### Notes

- If `subdivisions` is not set, the response will only include holidays that apply to the whole country.
- If you only want to check if today is a holiday in a specific subdivision, use `&subdivisions=true` and filter the response array, if response is not empty. 
- `include` and `exclude` can't be used together.

##### Examples

###### Check if today is a holiday in the UK

```http
GET https://holidays.eartharoid.me/api/v1/today?country=gb&offset=60 HTTP/1.1
```

#### Response

##### 200 OK

Today is a public holiday in `country`.

```json
[
  {
	"name": "Christmas Day",
	"localName": "Christmas Day",
	"actualDate": "2023-12-25",
	"observedDate": "2023-12-25",
	"subdivisions": null
  }
]
```

###### Notes

- If the `subdivisions` query parameter is `true`, `subdivisions` in the response may be an array of subdivisions (e.g. `["SCT"]`) that the holiday applies to.

##### 204 No Content

Today is not a public holiday in `country`.

##### 404 Not Found

```json
{
  "error": "Invalid or unsupported country code"
}
```