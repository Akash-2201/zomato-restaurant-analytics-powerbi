# Zomato Restaurant Analytics Dashboard (Power BI)

An interactive Power BI dashboard that analyses restaurants and menu items across 13 major Indian cities: where the outlets are, how they are rated, what they sell and how prices vary.

> Independent portfolio project. Not affiliated with or endorsed by Zomato.

## Business Questions

- Which cities have the most restaurants, and how big is each city's share?
- How do ratings and menu prices compare across cities and cuisines?
- Which cuisines dominate the market?
- Which restaurants are the most popular, and are popular restaurants also well rated?

## Dashboard Pages

| Page | What it shows |
|---|---|
| **Overview** | KPI cards (outlets, menu items, average rating, average price), cuisine breakdown, item tag mix and a map of outlets by city |
| **City Deep Dive** | City ranking by outlet count and share, rating vs price scatter, outlet share by city |
| **Restaurant Explorer** | Most popular restaurants, votes vs rating, dining vs delivery ratings by cuisine |


## Dataset

- **Source:** Zomato Restaurants Dataset for Metropolitan Areas (Kaggle): ADD_KAGGLE_LINK
- **Size:** about 124K menu items from about 900 restaurant outlets in 13 cities
- **Fields:** restaurant name, area, city, cuisine, dining and delivery ratings and votes, item name, item tag, price

**Note:** this is a scraped public dataset. It has no order, customer or sales history, so the analysis covers the restaurant and menu market, not revenue or trends over time.

## What I Did

**Data preparation (Power Query)**
- Trimmed stray spaces in text columns (for example `" Hyderabad"`)
- Converted scraped text columns such as `Prices` to numbers
- Standardised the item tag column and replaced blanks with `Regular`
- Merged neighbourhood names that were wrongly listed as cities into their parent city

**Data model (star schema)**
- `dim_City`: one row per city
- `dim_Restaurant`: one row per outlet, with cuisine, ratings and votes
- `Menu_Items`: one row per dish, with price, tag and votes
- One-to-many relationships on `City` and `RestaurantID`, with single-direction filtering

**DAX measures**
- `Total Outlets`, `Total Menu Items`, `Avg Item Price`, `Avg Dining Rating`
- `City Rank` using `RANKX` with `ALL`
- `Outlet Share %` using `DIVIDE` and `CALCULATE`
- `Avg Delivery Rating` and `Total Dining Votes`

**Visuals and interactivity**
- Slicers for city, cuisine and item tag
- Map, donut chart, bar charts, scatter plots and column charts
- Conditional formatting and a custom red, white and gold theme
- Page navigation buttons

## Key Insights

> Check these against your final dashboard before publishing.

- **Hyderabad has the most outlets** in the dataset (about 14% of the total), followed by Jaipur, Chennai, Bangalore and Mumbai.
- **Average dining rating is about 3.8 out of 5**, and the average menu item price is about ₹241.
- **Beverages, pizza, fast food and desserts** are the largest cuisine groups by outlet count.
- **About 79% of menu items carry no special tag**. Only a small share are marked Bestseller, Must Try or Chef's Special.

## Tools Used

Power BI Desktop, Power Query, DAX


## Author

**Akash j**
[LinkedIn](https://www.linkedin.com/in/akash-j-8305a0372/)
