# U.S. Real Estate Listings (Standardized)

**Records:** 1761  
**Files:** CSV + JSONL  
**Source:** Zillow listing pages (public)  
**Scrape Window:** Derived from source file timestamps in `scrape_datetime`

## Schema
- address_full (str)
- street_address (str)
- city (str)
- state (str)
- zipcode (str)
- price_usd (float) — USD
- currency (str) — default "USD"
- bedrooms (int, nullable)
- bathrooms (float, nullable)
- living_area_sqft (float, nullable)
- lot_size_sqft (float, nullable; acres converted to sqft)
- property_tax_rate_percent (float)
- built_year (int, nullable)
- last_sold_price (float, nullable)
- days_on_zillow (int)
- status (str, as scraped)
- brokerage_name (str)
- listing_provided_by (str)
- listing_url (str, validated URL)
- image_url (str, validated URL)
- source (str) — "Zillow"
- _source_file (str) — original file name
- scrape_datetime (ISO8601)
- description (str)

## Notes
- Numeric parsing removes commas/suffixes and converts to floats/ints.
- Lot sizes in acres converted to square feet (× 43,560).
- Deduplication by `listing_url || address_full || zipcode` (first occurrence kept).
- Some fields may be missing from the original source and remain null.
