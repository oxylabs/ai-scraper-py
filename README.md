# AI-Scraper

[![AI-Scraper Header](https://github.com/oxylabs/ai-crawler-py/blob/main/Ai-studio%20.png)](https://aistudio.oxylabs.io/apps/crawl?utm_source=877&utm_medium=affiliate&utm_campaign=ai_studio&groupid=877&utm_content=ai-crawler-py-github&transaction_id=102f49063ab94276ae8f116d224b67)

[![](https://dcbadge.limes.pink/api/server/Pds3gBmKMH?style=for-the-badge&theme=discord)](https://discord.gg/Pds3gBmKMH) [![YouTube](https://img.shields.io/badge/YouTube-Oxylabs-red?style=for-the-badge&logo=youtube&logoColor=white)](https://www.youtube.com/@oxylabs)

The [**AI-Scraper**](https://aistudio.oxylabs.io/apps/scrape) is an experimental scraping tool by [**Oxylabs AI Studio**](https://aistudio.oxylabs.io/) that extracts data from a single webpage using AI. It identifies and parses relevant information based on a natural language prompt, then delivers results in either **structured JSON** (for automation and APIs) or **Markdown format** (best for readable outputs and AI workflows).

This AI scraper removes the need for CSS/XPath selectors or custom parsers, so it integrates seamlessly with various automation pipelines. **Automatic schema generation** and flexible output formats provide users with an easy way to extract clean, structured data without ever needing to maintain parsing logic.

## Key features

- **Natural language prompt-based extraction** – Define your needs in plain English, and the scrape agent will retrieve the relevant information.  
- **Multiple output formats** – Choose JSON for structured workflows or Markdown for human-readable results and AI workflows.  
- **Automatic schema generation** – Generate a schema automatically from a prompt or define it manually for precise JSON parsing.  
- **Works on any public webpage** – Extract from e-commerce, news, blogs, or any other accessible source.  

## How it works

To scrape a webpage with AI-Scraper, follow these steps:

1. **Provide the webpage URL** you want to scrape.  
2. **Describe the data to extract** in natural language (e.g. “Get all product names and prices”).  
3. **Select the output format** – structured JSON or Markdown.  
4. **(Optional) Define a schema** – Let AI-Scraper generate one automatically, or provide your own OpenAPI schema for the exact structure you desire.  

### Installation

To begin, make sure you have access to an AI Studio API key (or [get a free trial](https://aistudio.oxylabs.io/register) with 1000 credits) and `Python ver. 3.10` or above installed. You can install the `oxylabs-ai-studio` package using pip:

```bash
pip install oxylabs-ai-studio
```

### Code examples (Python)

The following examples show how to use `AiScraper` to extract data from a sample page.

```python
from oxylabs_ai_studio.apps.ai_scraper import AiScraper

# Initialize the AI Scraper with your API key
scraper = AiScraper(api_key="YOUR_API_KEY")

# Generate a schema automatically from natural language
schema = scraper.generate_schema(prompt="want to parse developer, platform, type, price game title, and genre (array)")
print(f"Generated schema: {schema}")

# Scrape a specific webpage and extract structured data
url = "https://sandbox.oxylabs.io/products/3"
result = scraper.scrape(
    url=url,
    output_format="json",
    schema=schema,
    render_javascript=False,
    geo_location="US",
)
# Print the scrape output
print("Results:")
for item in result.data['games']:
    print(item, "\n")
```
Learn more about AI-Scraper and Oxylabs AI Studio Python SDK in our [PyPI repository](https://pypi.org/project/oxylabs-ai-studio/). You can also check out our [AI Studio JavaScript SDK](https://github.com/oxylabs/oxylabs-ai-studio-js) guide for JS users.

### Request parameters

| Parameter           | Description                                                    | Default Value |
|---------------------|----------------------------------------------------------------|---------------|
| `url`*              | Target URL to scrape                                           | –             |
| `output_format`     | Output format (`json`, `markdown`)                             | `markdown`      |
| `schema`            | OpenAPI schema for structured extraction (mandatory for JSON)  | –             |
| `render_javascript` | Enable render JavaScript                                       | `False`         |
| `geo_location`      | Proxy location in ISO2 format                                  | –             |

`*` – mandatory parameters

### Output samples

The AI-Scraper can return parsed, ready-to-use output that is easy to integrate into your applications.

This is a structured JSON of the response output:

```json
Results:
{'developer': 'Nintendo EAD Tokyo', 'platform': 'wii', 'type': 'singleplayer', 'price': 91.99, 'title': 'Super Mario Galaxy 2', 'genre': ['Action', 'Platformer', '2D']} 

{'developer': 'Nintendo', 'platform': 'wii', 'type': 'singleplayer', 'price': 88.99, 'title': 'Metroid Prime 3: Corruption', 'genre': ['Action', 'Shooter', 'First-Person', 'Sci-Fi', 'Arcade']} 

{'developer': 'Nintendo', 'platform': 'wii', 'type': 'singleplayer', 'price': 83.99, 'title': 'Tomena Sanner', 'genre': ['Action', 'General']} 

{'developer': 'Eidos Interactive', 'platform': 'wii', 'type': 'singleplayer', 'price': 80.99, 'title': 'Death Jr.: Root of Evil', 'genre': ['Action', 'Platformer', '3D']} 

{'developer': 'Nintendo', 'platform': 'wii', 'type': 'singleplayer', 'price': 87.99, 'title': "Kirby's Return to Dream Land", 'genre': ['General', 'Action', 'Platformer', '2D']}
```
Alternatively, you can use `output_format=”markdown”` to receive Markdown results instead of parsed JSON.

## Practical use cases

Oxylabs AI-Scraper can be applied to a wide variety of data collection tasks:

1. **Extract product details** – Gather product names, descriptions, and prices from e-commerce sites.  
2. **Parse news articles** – Retrieve article titles, dates, authors, and body text.  
3. **Scrape pricing pages** – Collect structured pricing information for competitor or market research.  
4. **Extract job postings** – Capture job titles, locations, salaries, and posting dates from recruitment portals.  

## FAQ

### How does AI-Scraper differ from normal scrapers?
AI-Scraper doesn’t rely on CSS/XPath selectors or custom parsing logic. Instead, it uses natural language prompts and AI-powered extraction, making it more adaptable to layout changes and much easier to set up.

### Can I scrape any webpage?
Yes, you can scrape any public webpage as long as the page is publicly accessible. AI-Scraper also supports JavaScript rendering for dynamic pages. Private or login-protected content isn’t supported out of the box.

### Is schema mandatory for AI-Scraper?
No, schema is not mandatory, but it’s required if you want structured JSON output. If you don’t provide one, AI-Scraper can generate a schema automatically based on your prompt.

### What happens if the page structure changes?
Unlike traditional scrapers, AI-Scraper is more resilient to layout changes because it interprets content with AI. However, major changes may require you to adjust either your prompt or the schema.

### Is AI-Scraper free?
Oxylabs AI Studio AI-Scraper is free to try by signing up for a free trial that includes 1,000 credits. After the trial, the [monthly plans](https://aistudio.oxylabs.io/pricing) start at just $12/month with 3000 credits and 1 request/s, with higher plans offering more credits and higher request rates.

## Learn more

For a deeper dive into available parameters, advanced integrations, and additional examples, check out the [AI Studio documentation](https://aistudio.oxylabs.io/apps/scrape).

## Contact us

If you have questions or need support, reach out to us at [hello@oxylabs.io](mailto:hello@oxylabs.io), through [live chat](https://oxylabs.drift.click/oxybot), or join our [Discord community](https://discord.gg/Pds3gBmKMH).
