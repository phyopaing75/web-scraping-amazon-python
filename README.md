# Automated Amazon Price Tracker

An automated Python data pipeline that monitors and logs real-time product price fluctuations on Amazon using BeautifulSoup and Requests.

## Project Overview

Online retail prices fluctuate dynamically based on demand, stock levels, and promotional cycles. This project implements a scheduled web scraping script that periodically checks the listing page of a specified Amazon product, extracts its current price and title, cleans irregular HTML text formatting, and appends timestamped records to a persistent CSV log for longitudinal price tracking.

## Features and Implementation

* Realistic HTTP Headers: Configures browser-like request headers (User-Agent, Accept-Language, Accept-Encoding) to reliably bypass standard anti-bot filters and retrieve live DOM content.

* HTML Parsing & Extraction: Uses BeautifulSoup to parse the response DOM and isolate targeted selectors (`#productTitle` and `.a-price-whole`).

* String Cleansing: Strips leading/trailing whitespaces, newlines, and stray punctuation marks to ensure numeric pricing clarity.

* Timestamped Persistence: Automatically captures the current execution date using Python's `datetime` module and appends new observations to `output_data_from_web-scraper_amazon.csv` without overwriting historical records.

* Automated Monitoring Loop: Incorporates a timed execution loop via `time.sleep()` to trigger scheduled price checks at fixed hourly intervals.

## Dataset Schema

The script writes to a local CSV file with the following column structure:

| Column Name | Data Type | Description |
| :--- | :--- | :--- |
| `Product` | String | Full title and description of the monitored product. |
| `Price` | String / Numeric | Extracted whole currency price figure. |
| `Date` | Date (YYYY-MM-DD) | Calendar date when the scrape check was executed. |

## Tech Stack and Libraries

* Language: Python

* Web Scraping: BeautifulSoup4 (`bs4`), Requests

* Automation and Utilities: `datetime`, `time`, `csv`

## Output Sample

```
Product,Price,Date
Apple iPhone 17 Pro Max US Version 256GB eSIM Cosmic Orange- Unlocked (Renewed),36822,2026-08-13
Apple iPhone 17 Pro Max US Version 256GB eSIM Cosmic Orange- Unlocked (Renewed),36822,2026-08-14
Apple iPhone 17 Pro Max US Version 256GB eSIM Cosmic Orange- Unlocked (Renewed),35999,2026-08-15
```
