# Amazon Product Page Scraper

This Python script scrapes details from Amazon product pages, including the following information:

- Product Name
- Price
- Short Description
- Full Product Description
- Image URLs
- Rating
- Number of Reviews
- Variant ASINs
- Sales Rank
- Link to all Reviews Page

## Requirements

To run the scraper, you need to install the following libraries:

- `requests`
- `selectorlib`
- `json`
- `time`

You can install these dependencies using `pip`:

```bash
pip install requests selectorlib
```

## Project Setup

1. Clone or download this repository.
2. Create a virtual environment and install the required dependencies (if using a virtual environment).

   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   pip install -r requirements.txt
   ```

3. Download the `selectors.yml` file which contains the necessary CSS/XPath selectors for scraping Amazon product details. The scraper uses this YAML file to extract the product data. You can customize the selectors in this file based on the specific structure of the Amazon product pages you're targeting.

## How to Use

1. Modify the `url` variable with the Amazon product page URL you want to scrape.

   Example:

   ```python
   url = "https://www.amazon.com/dp/B0BYW2FNFN"
   ```

2. Run the script:

   ```bash
   python scraper.py
   ```

   The script will print out the extracted data from the product page. The output will contain details such as:

   - Product Name
   - Price
   - Short Description
   - Full Product Description
   - Image URLs
   - Rating
   - Number of Reviews
   - Variant ASINs
   - Sales Rank
   - Link to all Reviews Page

3. You can also handle blocked pages (Amazon's anti-scraping measures) by using better proxies or waiting for a while before retrying if you encounter status code 503.

## How the Script Works

- The script sends an HTTP request to the Amazon product page using the `requests` library.
- It uses the `selectorlib` library to parse and extract relevant data from the HTML page.
- The `selectors.yml` file contains the CSS or XPath selectors for the required product details. You can modify the selectors in this file if you need to scrape additional or different data.
- The script handles the response status code and checks if the page is blocked by Amazon, providing an appropriate message.

## Example Output

Example output data for a product might look like this:

```json
{
  "product_name": "Sample Product",
  "price": "$199.99",
  "short_description": "This is a short description of the product.",
  "full_description": "Here is the full description of the product with more details.",
  "image_urls": [
    "https://example.com/image1.jpg",
    "https://example.com/image2.jpg"
  ],
  "rating": "4.5 out of 5 stars",
  "number_of_reviews": "200",
  "variant_asins": [
    "B08XXXXXXXX",
    "B08YYYYYYYY"
  ],
  "sales_rank": "1,000 in Electronics",
  "reviews_page": "https://www.amazon.com/product-reviews/B08XXXXXXXX"
}
```

## Handling Blocked Pages

Amazon may block scraping attempts by detecting automated requests. If the page is blocked:

- A status code greater than 500 will be returned.
- The script will display a message suggesting using better proxies or retrying after some time.

## Contributing

Feel free to fork the repository and submit issues or pull requests for improvements or bug fixes.

## License

This project is licensed under the MIT License.

---

Developed by [Your Name]. Happy scraping!
```
