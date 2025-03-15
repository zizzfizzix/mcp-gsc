# Google Search Console MCP

A tool that connects [Google Search Console](https://search.google.com/search-console/about) (GSC) with Claude AI, allowing you to analyze your SEO data through natural language conversations. This integration gives you access to property information, search analytics, URL inspection, and sitemap management—all through simple chat with Claude.

---

## What Can This Tool Do For SEO Professionals?

1. **Property Management**  
   - See all your GSC properties in one place
   - Get verification details and basic site information

2. **Search Analytics & Reporting**  
   - Discover which search queries bring visitors to your site
   - Track impressions, clicks, and click-through rates
   - Analyze performance trends over time
   - Compare different time periods to spot changes
   - **Visualize your data** with charts and graphs created by Claude

3. **URL Inspection & Indexing**  
   - Check if specific pages have indexing problems
   - See when Google last crawled your pages
   - Inspect multiple URLs at once to identify patterns
   - Get actionable insights on how to improve indexing

4. **Sitemap Management**  
   - View all your sitemaps and their status
   - Submit new sitemaps directly through Claude
   - Check for errors or warnings in your sitemaps
   - Monitor sitemap processing status

---

## Available Tools

Here's what you can ask Claude to do once you've set up this integration:

| **What You Can Ask For**        | **What It Does**                                            | **What You'll Need to Provide**                                 |
|---------------------------------|-------------------------------------------------------------|----------------------------------------------------------------|
| `list_properties`               | Shows all your GSC properties                               | Nothing - just ask!                                             |
| `get_site_details`              | Shows details about a specific site                         | Your website URL                                                |
| `get_search_analytics`          | Shows top queries and pages with metrics                    | Your website URL and time period                                |
| `get_performance_overview`      | Gives a summary of site performance                         | Your website URL and time period                                |
| `check_indexing_issues`         | Checks if pages have indexing problems                      | Your website URL and list of pages to check                     |
| `inspect_url_enhanced`          | Detailed inspection of a specific URL                       | Your website URL and the page to inspect                        |
| `get_sitemaps`                  | Lists all sitemaps for your site                            | Your website URL                                                |
| `submit_sitemap`                | Submits a new sitemap to Google                             | Your website URL and sitemap URL                                |

*For a complete list of all 17 available tools and their detailed descriptions, ask Claude to "list tools" after setup.*

---

## Getting Started (No Coding Experience Required!)

### 1. Set Up Google Search Console API Access

Before using this tool, you'll need to create API credentials that allow Claude to access your GSC data:

1. Create a Google Cloud account if you don't have one
2. Set up a service account (like a special user for API access)
3. Download the credentials file (a JSON file)
4. Grant this service account access to your GSC properties

**🎬 Watch this beginner-friendly tutorial:**

<div align="center">
  <a href="https://www.youtube.com/watch?v=UeEuJAD0ZsU">
    <div style="position: relative; display: inline-block;">
      <img src="https://i.ytimg.com/vi/UeEuJAD0ZsU/maxresdefault.jpg" alt="How to Get Google Search Console API Credentials & Add a Service Account" width="600" style="border-radius: 12px; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
      <div style="position: absolute; top: 50%; left: 50%; transform: translate(-50%, -50%);">
        <svg width="80" height="80" viewBox="0 0 68 48" xmlns="http://www.w3.org/2000/svg">
          <path d="M66.52,7.74c-0.78-2.93-2.49-5.41-5.42-6.19C55.79,.13,34,0,34,0S12.21,.13,6.9,1.55 C3.97,2.33,2.27,4.81,1.48,7.74C0.06,13.05,0,24,0,24s0.06,10.95,1.48,16.26c0.78,2.93,2.49,5.41,5.42,6.19 C12.21,47.87,34,48,34,48s21.79-0.13,27.1-1.55c2.93-0.78,4.64-3.26,5.42-6.19C67.94,34.95,68,24,68,24S67.94,13.05,66.52,7.74z" fill="#f00"></path>
          <path d="M 45,24 27,14 27,34" fill="#fff"></path>
        </svg>
      </div>
    </div>
  </a>
</div>

*Click the image above to watch the step-by-step video tutorial (right-click and select "Open link in new tab" to keep this page open)*

### 2. Install Required Software

You'll need two things installed on your computer:

- [Python](https://www.python.org/downloads/) (version 3.11 or newer) - This runs the connection between GSC and Claude
- [Claude Desktop](https://claude.ai/desktop) - The AI assistant you'll chat with

### 3. Download the GSC Tool

You need to download this tool to your computer. The easiest way is:

1. Click the green "Code" button at the top of this page
2. Select "Download ZIP"
3. Unzip the downloaded file to a location you can easily find (like your Documents folder)

Alternatively, if you're familiar with Git:

```bash
git clone https://github.com/AminForou/mcp-gsc.git
```

### 4. Install Required Components

Open your computer's Terminal (Mac) or Command Prompt (Windows):

1. Navigate to the folder where you unzipped the files:
   ```bash
   # Example (replace with your actual path):
   cd ~/Documents/mcp-gsc
   ```

2. Install the required components:
   ```bash
   # If you're comfortable with newer tools:
   pip install uv
   uv install -r requirements.txt

   # OR if you prefer the standard approach:
   pip install -r requirements.txt
   ```

### 5. Connect Claude to Google Search Console

1. Download and install [Claude Desktop](https://claude.ai/desktop) if you haven't already
2. Make sure you have your Google service account credentials file saved somewhere on your computer
3. Open your computer's Terminal (Mac) or Command Prompt (Windows) and type:

   ```bash
   # For Mac users:
   nano ~/Library/Application\ Support/Claude/claude_desktop_config.json
   
   # For Windows users:
   notepad %APPDATA%\Claude\claude_desktop_config.json
   ```

4. Add the following text (this tells Claude how to connect to GSC):

   ```json
   {
     "mcpServers": {
       "gscServer": {
         "command": "python",
         "args": ["/FULL/PATH/TO/mcp-gsc/gsc_server.py"],
         "env": {
           "GSC_CREDENTIALS_PATH": "/FULL/PATH/TO/service_account_credentials.json"
         }
       }
     }
   }
   ```

   **Important:** Replace both paths with the actual locations of the files on your computer:
   
   - The first path should point to the `gsc_server.py` file inside the folder you unzipped
   - The second path should point to your Google service account credentials JSON file
   
   Examples:
   - Mac: `/Users/yourname/Documents/mcp-gsc/gsc_server.py`
   - Windows: `C:\\Users\\yourname\\Documents\\mcp-gsc\\gsc_server.py`

   **Pro Tip:** To get the full path of a file:
   - Mac: Right-click the file, hold Option key, and select "Copy as Pathname"
   - Windows: Shift+Right-click the file and select "Copy as path"

5. Save the file:
   - Mac: Press Ctrl+O, then Enter, then Ctrl+X to exit
   - Windows: Click File > Save, then close Notepad

6. Restart Claude Desktop
7. When Claude opens, you should now see GSC tools available in the tools section

### 6. Start Analyzing Your SEO Data!

Now you can ask Claude questions about your GSC data! Claude can not only retrieve the data but also analyze it, explain trends, and create visualizations to help you understand your SEO performance better.

Here are some powerful prompts you can use with each tool:

| **Tool Name**                   | **Sample Prompt**                                                                                |
|---------------------------------|--------------------------------------------------------------------------------------------------|
| `list_properties`               | "List all my GSC properties and tell me which ones have the most pages indexed."                 |
| `get_site_details`              | "Analyze the verification status of mywebsite.com and explain what the ownership details mean."  |
| `get_search_analytics`          | "Show me the top 20 search queries for mywebsite.com in the last 30 days, highlight any with CTR below 2%, and suggest title improvements." |
| `get_performance_overview`      | "Create a visual performance overview of mywebsite.com for the last 28 days, identify any unusual drops or spikes, and explain possible causes." |
| `check_indexing_issues`         | "Check these important pages for indexing issues and prioritize which ones need immediate attention: mywebsite.com/product, mywebsite.com/services, mywebsite.com/about" |
| `inspect_url_enhanced`          | "Do a comprehensive inspection of mywebsite.com/landing-page and give me actionable recommendations to improve its indexing status." |
| `batch_url_inspection`          | "Inspect my top 5 product pages, identify common crawling or indexing patterns, and suggest technical SEO improvements." |
| `get_sitemaps`                  | "List all sitemaps for mywebsite.com, identify any with errors, and recommend next steps." |
| `list_sitemaps_enhanced`        | "Analyze all my sitemaps for mywebsite.com, focusing on error patterns, and create a prioritized action plan." |
| `submit_sitemap`                | "Submit my new product sitemap at https://mywebsite.com/product-sitemap.xml and explain how long it typically takes for Google to process it." |
| `get_sitemap_details`           | "Check the status of my main sitemap at mywebsite.com/sitemap.xml and explain what the warnings mean for my SEO." |
| `get_search_by_page_query`      | "What search terms are driving traffic to my blog post at mywebsite.com/blog/post-title? Identify opportunities to optimize for related keywords." |
| `compare_search_periods`        | "Compare my site's performance between January and February. What queries improved the most, which declined, and what might explain these changes?" |
| `get_advanced_search_analytics` | "Analyze my mobile search performance for queries with high impressions but positions below 10, and suggest content improvements to help them rank better." |

You can also ask Claude to combine multiple tools and analyze the results. For example:

- "Find my top 20 landing pages by traffic, check their indexing status, and create a report highlighting any pages with both high traffic and indexing issues."

- "Analyze my site's performance trend over the last 90 days, identify my fastest-growing queries, and check if the corresponding landing pages have any technical issues."

- "Compare my desktop vs. mobile search performance, visualize the differences with charts, and recommend specific pages that need mobile optimization based on performance gaps."

- "Identify queries where I'm ranking on page 2 (positions 11-20) that have high impressions but low CTR, then inspect the corresponding URLs and suggest title and meta description improvements."

Claude will use the GSC tools to fetch the data, present it in an easy-to-understand format, create visualizations when helpful, and provide actionable insights based on the results.

---

## Data Visualization Capabilities

Claude can help you visualize your GSC data in various ways:

- **Trend Charts**: See how metrics change over time
- **Comparison Graphs**: Compare different time periods or dimensions
- **Performance Distributions**: Understand how your content performs across positions
- **Correlation Analysis**: Identify relationships between different metrics
- **Heatmaps**: Visualize complex datasets with color-coded representations

Simply ask Claude to "visualize" or "create a chart" when analyzing your data, and it will generate appropriate visualizations to help you understand the information better.

---

## Troubleshooting

If you're having trouble connecting:

1. Make sure all file paths in your configuration are correct and use the full path
2. Check that your service account has access to your GSC properties
3. Restart Claude Desktop after making any changes
4. Look for error messages in Claude's response when you try to use a tool

---

## Contributing

Found a bug or have an idea for improvement? We welcome your input! Open an issue or submit a pull request on GitHub.

---

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
