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

3. **URL Inspection & Indexing**  
   - Check if specific pages have indexing problems
   - See when Google last crawled your pages
   - Inspect multiple URLs at once to identify patterns

4. **Sitemap Management**  
   - View all your sitemaps and their status
   - Submit new sitemaps directly through Claude
   - Check for errors or warnings in your sitemaps

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

**Watch this beginner-friendly tutorial:**

[![How to Get Google Search Console API Credentials & Add a Service Account](https://img.youtube.com/vi/UeEuJAD0ZsU/0.jpg)](https://www.youtube.com/watch?v=UeEuJAD0ZsU)

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

Now you can ask Claude questions about your GSC data like:

- "Show me the top search queries for my site in the last 30 days"
- "Check if these URLs have any indexing issues"
- "What's my site's overall performance trend?"
- "List all the sitemaps for my property"

Claude will use the GSC tools to fetch the data and present it to you in an easy-to-understand format.

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
