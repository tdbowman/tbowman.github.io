# Working with Web APIs in Python

## What Is an API?

An **API** (Application Programming Interface) is a doorway one program opens so other programs can ask it for things. When you check the weather on your phone, the app doesn't own the weather data — it asks a weather service's API for it and displays the answer.

You have already used APIs without the name. `len()` is part of Python's API. What's new this week is that the program you're asking lives on **someone else's computer**, and you reach it over the internet.

```python
# Everything so far: data you typed or read from a file
temperatures = [72, 68, 75, 80]

# This week: data that is live, and that you did not create
# (fetched from a weather service over the internet)
```

```{note}
A **web API** is just a URL that returns data instead of a web page. Open one in your browser and you'll see raw text — usually JSON.
```

## How a Request Works

Every API call is the same four steps:

1. Your program **sends a request** to a URL
2. The server **does something** (looks up data, runs a search)
3. The server **sends back a response** — a status code plus a body
4. Your program **reads the response** and uses the data

### HTTP Methods

| Method | Means | You'll use it to |
|--------|-------|------------------|
| `GET` | "Give me this" | Retrieve data — 95% of what you do this week |
| `POST` | "Here's something new" | Create a record, submit a form |
| `PUT` | "Replace this" | Update an existing record |
| `DELETE` | "Remove this" | Delete a record |

### Status Codes

The server always tells you how it went. Learn these five:

| Code | Meaning | What to do |
|------|---------|------------|
| `200` | OK — it worked | Read the data |
| `400` | Bad request | You sent something malformed. Check your parameters |
| `401` / `403` | Unauthorized / Forbidden | Missing or wrong API key |
| `404` | Not found | Check the URL and the ID you asked for |
| `429` | Too many requests | You hit a rate limit. Slow down |
| `500` | Server error | Their problem, not yours. Try again later |

```{tip}
The first digit tells you who to blame: `2xx` success, `4xx` your mistake, `5xx` their mistake.
```

## Installing requests

Python's built-in tools for HTTP are clumsy. Everyone uses the `requests` library instead.

```bash
pip install requests --break-system-packages
```

```python
import requests
```

## Your First Request

We'll start with **JSONPlaceholder**, a free practice API that needs no key and no signup.

```python
import requests

response = requests.get("https://jsonplaceholder.typicode.com/posts/1")

print(response.status_code)   # 200
print(response.json())        # a Python dictionary
```

That's the whole pattern. `requests.get()` goes and fetches; `.json()` turns the response body into a Python dictionary or list you already know how to work with.

## Reading the Response

The response object carries more than the data:

```python
response = requests.get("https://jsonplaceholder.typicode.com/posts/1")

response.status_code   # 200 — the numeric code
response.ok            # True if status is under 400
response.text          # the raw body, as a string
response.json()        # the body parsed into Python objects
response.headers       # dictionary of response headers
response.url           # the full URL that was actually requested
```

**Always check before you parse.** A 404 page is not JSON, and `.json()` will raise an error on it:

```python
response = requests.get("https://jsonplaceholder.typicode.com/posts/1")

if response.ok:
    data = response.json()
    print(data["title"])
else:
    print(f"Request failed with status {response.status_code}")
```

## Query Parameters

Most APIs let you narrow what you're asking for. You could paste values into the URL by hand:

```python
# Works, but fragile — spaces and special characters will break it
url = "https://jsonplaceholder.typicode.com/posts?userId=1"
response = requests.get(url)
```

Better: hand `requests` a dictionary and let it build the URL.

```python
params = {"userId": 1}

response = requests.get(
    "https://jsonplaceholder.typicode.com/posts",
    params=params
)

print(response.url)   # https://jsonplaceholder.typicode.com/posts?userId=1
print(len(response.json()))   # 10 posts by user 1
```

```{important}
Use `params=` rather than building URL strings yourself. `requests` handles the encoding — spaces, ampersands, accented characters — that would otherwise silently corrupt your request.
```

## Working with the JSON You Get Back

API responses are dictionaries and lists nested inside each other. Everything you learned in Weeks 6 and 7 applies directly.

```python
response = requests.get("https://jsonplaceholder.typicode.com/users/1")
user = response.json()

# Top-level values
print(user["name"])            # Leanne Graham
print(user["email"])           # Sincere@april.biz

# Nested dictionary
print(user["address"]["city"])          # Gwenborough
print(user["company"]["name"])          # Romaguera-Crona
```

When the response is a **list**, loop over it:

```python
response = requests.get("https://jsonplaceholder.typicode.com/posts")
posts = response.json()

print(f"Got {len(posts)} posts")

for post in posts[:5]:
    print(f"#{post['id']}: {post['title']}")
```

### When You Don't Know the Shape

Print the keys before you guess at them:

```python
data = response.json()

print(type(data))       # dict or list?
if isinstance(data, dict):
    print(data.keys())  # what fields exist?
else:
    print(data[0].keys())   # what fields does each item have?
```

```{tip}
`import json` then `print(json.dumps(data, indent=2))` prints nested JSON in a readable, indented shape. It's the fastest way to understand an unfamiliar response.
```

## API Keys and Authentication

Many useful APIs want to know who is calling. They issue you a **key** — a long string that identifies your account.

Two common ways to send it:

```python
# As a query parameter
params = {"q": "Chicago", "appid": API_KEY}
response = requests.get(url, params=params)

# As a header (more common for newer APIs)
headers = {"Authorization": f"Bearer {API_KEY}"}
response = requests.get(url, headers=headers)
```

```{warning}
**Never paste an API key into code you commit to GitHub.** Bots scan public repositories for keys within minutes of a push, and you are responsible for what gets billed to your account.
```

Keep the key outside your code — in an environment variable:

```python
import os
import requests

API_KEY = os.environ.get("WEATHER_API_KEY")

if not API_KEY:
    print("Set WEATHER_API_KEY before running this script")
else:
    response = requests.get(url, params={"appid": API_KEY})
```

Set it in your terminal before running:

```bash
export WEATHER_API_KEY="your-key-here"     # macOS / Linux
setx WEATHER_API_KEY "your-key-here"       # Windows
```

## Errors, Timeouts, and Failure

Your file-reading code from Week 9 failed for one reason: the file wasn't there. Network code fails for many more — the wifi drops, the server is down, the response takes forever, the JSON is malformed.

```python
import requests

try:
    response = requests.get(
        "https://jsonplaceholder.typicode.com/posts/1",
        timeout=5                       # give up after 5 seconds
    )
    response.raise_for_status()         # turn 4xx/5xx into an exception
    data = response.json()
    print(data["title"])

except requests.exceptions.Timeout:
    print("The server took too long to answer.")

except requests.exceptions.ConnectionError:
    print("Couldn't reach the server — check your internet connection.")

except requests.exceptions.HTTPError as e:
    print(f"The server returned an error: {e}")

except ValueError:
    print("The response wasn't valid JSON.")
```

```{important}
**Always pass `timeout=`.** Without it, a request can hang indefinitely and your program will simply stop, with no error and no output.
```

## Rate Limits and Being a Good Citizen

APIs are run by people paying for servers. Hammering one with a thousand requests a second is rude, and will get you blocked.

```python
import requests
import time

user_ids = [1, 2, 3, 4, 5]
users = []

for user_id in user_ids:
    response = requests.get(f"https://jsonplaceholder.typicode.com/users/{user_id}")
    if response.ok:
        users.append(response.json())
    time.sleep(0.5)      # pause half a second between calls

print(f"Fetched {len(users)} users")
```

Three habits worth forming:

- **Pause between requests** in a loop — `time.sleep()` costs you nothing
- **Save what you fetch** to a file, so re-running your analysis doesn't re-hit the API
- **Read the documentation** for the rate limit before you write the loop, not after you get a `429`

## Practical Examples

### Example 1: Live Weather, No API Key

[Open-Meteo](https://open-meteo.com/) is a free weather API that requires no signup — good for classwork.

```python
import requests

def get_current_weather(latitude, longitude):
    """Return the current temperature and wind speed for a location."""
    url = "https://api.open-meteo.com/v1/forecast"
    params = {
        "latitude": latitude,
        "longitude": longitude,
        "current": "temperature_2m,wind_speed_10m",
        "temperature_unit": "fahrenheit"
    }

    try:
        response = requests.get(url, params=params, timeout=5)
        response.raise_for_status()
    except requests.exceptions.RequestException as e:
        return f"Could not get weather: {e}"

    current = response.json()["current"]
    return f"{current['temperature_2m']}°F, wind {current['wind_speed_10m']} mph"

# River Forest, Illinois
print(get_current_weather(41.90, -87.81))
```

### Example 2: Fetch, Filter, Report

```python
import requests

response = requests.get("https://jsonplaceholder.typicode.com/posts", timeout=5)
response.raise_for_status()
posts = response.json()

# Which users write the most?
counts = {}
for post in posts:
    author = post["userId"]
    counts[author] = counts.get(author, 0) + 1

for author, total in sorted(counts.items(), key=lambda pair: pair[1], reverse=True):
    print(f"User {author}: {total} posts")
```

### Example 3: API Data Into a CSV

This is where Week 9 and Week 10 meet — fetch live data, then store it so you can analyze it later without calling the API again.

```python
import requests
import csv

response = requests.get("https://jsonplaceholder.typicode.com/users", timeout=5)
response.raise_for_status()
users = response.json()

with open("users.csv", "w", newline="") as file:
    writer = csv.DictWriter(file, fieldnames=["id", "name", "email", "city"])
    writer.writeheader()

    for user in users:
        writer.writerow({
            "id": user["id"],
            "name": user["name"],
            "email": user["email"],
            "city": user["address"]["city"]
        })

print(f"Saved {len(users)} users to users.csv")
```

## Common Mistakes

| Mistake | What happens | Fix |
|---------|--------------|-----|
| Calling `.json()` without checking status | `JSONDecodeError` on an error page | Check `response.ok` first |
| No `timeout=` | Program hangs forever | Always pass a timeout |
| Building URLs with `+` and f-strings | Breaks on spaces and symbols | Use `params=` |
| Hardcoding an API key | Key leaks when you push to GitHub | Read it from an environment variable |
| Looping with no pause | Rate limited, then blocked | `time.sleep()` between calls |
| Guessing at response keys | `KeyError` | Print the keys first |

## Finding APIs to Practice On

These need no key and are safe to experiment with:

- **[JSONPlaceholder](https://jsonplaceholder.typicode.com/)** — fake posts, users, comments; perfect for practice
- **[Open-Meteo](https://open-meteo.com/)** — real weather and forecast data
- **[REST Countries](https://restcountries.com/)** — population, currency, languages by country
- **[Open Library](https://openlibrary.org/developers/api)** — book records by ISBN, title, author
- **[CoinGecko](https://www.coingecko.com/en/api)** — cryptocurrency prices

```{tip}
The Open Library API is worth a look for anyone in an information program — it returns real bibliographic records, which is the same kind of structured metadata you'll meet in cataloging work.
```

## Summary

✅ **API** — a program you can ask for data over the internet  
✅ **requests.get()** — fetch a URL; `params=` for query strings  
✅ **response.ok / .status_code** — check before you parse  
✅ **response.json()** — turns the body into dictionaries and lists  
✅ **timeout= and try/except** — networks fail, plan for it  
✅ **API keys** — from environment variables, never hardcoded  
✅ **time.sleep()** — pause between calls, save what you fetch
