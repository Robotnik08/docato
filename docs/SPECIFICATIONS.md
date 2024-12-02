# Specifications

## Configurations

### `docato-config.json`

```json
{
    "output": "path/to/output_folder",

    "header": "path/to/header.html",
    "page_header": "path/to/page_header.md",
    "footer": "path/to/footer.md",
    "index_footer": "path/to/index_footer.md",

    "documentation_config": {
        "output_name": "Documentation",
        "title": "Documentation",
        "index_page": "path/to/index.md",
        "favicon": "path/to/favicon.ico",
        "styles": ["path/to/style.css"],
        "scripts": ["path/to/script.js"],
        "pages": [
            {
                "title": "Page 1",
                "source": "path/to/page1.md"
            },
            {
                "title": "Page 2",
                "source": "path/to/page2.md"
            }
        ],
        "variables": {
            "variable_name": "variable_value"
        }
    }
}
```

- `index` (string): Path to the index file.
- `output` (string): Path to the output folder.
- `header` (string): Path to the header file, this file will be included at the top of every page.
- `footer` (string): Path to the footer file, this file will be included at the bottom of every page (except the index page).

### `index.json`

```json
```

- `title` (string): Title of the documentation.
- `favicon` (string): Path to the favicon.
- `styles` (array of strings): Paths to CSS files.
- `scripts` (array of strings): Paths to JS files.
- `pages` (array of objects): List of pages.
    - page:
        - `title` (string): Title of the page.
        - `source` (string): Path to the markdown file.


## Page Structure

### Content

The content is based on the CommonMark specification. <br>
For more information, refer to the [CommonMark website](https://commonmark.org/).

### Special Items

#### Variables

Any instances of `{$<variable_name>}` in the markdown file will be replaced with the string variable value from the `index.json` file.

#### Built-in Variables

Any instances of `{$title}` in the markdown file will be replaced with the title of the page.<br>
Any instances of `{$main_title}` in the markdown file will be replaced with the title of the documentation.<br>
Any instances of `{$previous_page}` in the markdown file will be replaced with the name of the previous page.<br>
Any instances of `{$next_page}` in the markdown file will be replaced with the name of the next page.<br>
Any instances of `{$all_pages}` in the markdown file will be replaced with a list of all the pages in the documentation. (for the index page)

#### Link to other pages

Any instances of `{#<page_name>}` in the markdown file will be replaced with a link to the specified page, the page name should be the same as the title of the page.
Any instances of `{#<page_name>::<url_extension>}` in the markdown file will be replaced with a link to the specified page with the specified url extension.
Any instances of `{#next}` in the markdown file will be replaced with a link to the next page.
Any instances of `{#previous}` in the markdown file will be replaced with a link to the previous page.