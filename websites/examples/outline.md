# Export Content

While you might want to only access the [`headings`](/examples/headings) to process, for example, the number or length of the headings it might not always be enough. In some case you might need to identify the actual structure of the content. For these use-cases you might want to consider one of these methods:

 - `outline` works similar as the previously mentioned `headings` method. It also returns all headings, but it keeps the structure of the original document in place and provides the heading levels (e.g. `h1`) alone with the output.

 - `outlineWithParagraphs` works similar as `outline` does, the difference is that this call also includes the paragraphs.

The following examples should help to understand the functionality better.


## Export the Outline

The outline of the content allows you build an index of the document. The following example builds a markdown version of the headings in the requested document:

```php
$web = new \spekulatius\phpscraper();

// Navigate to the test page.
$web->go('https://test-pages.phpscraper.de/content/outline.html');
/**
 * this page contains:
 *
 * <h1>We are testing here!</h1>
 * <p>This page contains an example structure to be parsed. It comes with a number of headings and nested paragraphs as an scrape example.</p>
 *
 * <h2>Examples</h2>
 * <p>There are numerous examples on the website. Please check them out to get more context on how scraping works.</p>
 *
 * <h3>Example 1</h3>
 * <p>Here would be an example.</p>
 *
 * <h3>Example 2</h3>
 * <p>Here would be the second example.</p>
 *
 * <h3>Example 3</h3>
 * <p>Here would be another example.</p>
 */


// Get the content outline
$outline = $web->outline;
/**
 * $outline now contains:
 *
 * [
 *    [
 *      "tag" => "h1",
 *      "content" =>  "We are testing here!"
 *    ], [
 *      "tag" => "h2",
 *      "content" => "Examples"
 *    ], [
 *      "tag" => "h3",
 *      "content" => "Example 1"
 *    ], [
 *      "tag" => "h3",
 *      "content" => "Example 2"
 *    ], [
 *      "tag" => "h3",
 *      "content" => "Example 3"
 *    ]
 * ]
 */
```

## Export the Outline with Paragraphs

The following method works in a similar manner as `outline`, but it does include any paragraphs as part of the returned array:

```php
$web = new \spekulatius\phpscraper();

// Navigate to the test page.
$web->go('https://test-pages.phpscraper.de/content/outline.html');
/**
 * this page contains:
 *
 * <h1>We are testing here!</h1>
 * <p>This page contains an example structure to be parsed. It comes with a number of headings and nested paragraphs as an scrape example.</p>
 *
 * <h2>Examples</h2>
 * <p>There are numerous examples on the website. Please check them out to get more context on how scraping works.</p>
 *
 * <h3>Example 1</h3>
 * <p>Here would be an example.</p>
 *
 * <h3>Example 2</h3>
 * <p>Here would be the second example.</p>
 *
 * <h3>Example 3</h3>
 * <p>Here would be another example.</p>
 */


// Get the content outline
$outline = $web->outline;
/**
 * $outline now contains:
 *
 * [
 *    [
 *      "tag" => "h1",
 *      "content" =>  "We are testing here!"
 *    ], [
 *      "tag" => "p",
 *      "content" => "This page contains an example structure to be parsed. It comes with a number of headings and nested paragraphs as an scrape example."
 *    ], [
 *      "tag" => "h2",
 *      "content" => "Examples"
 *    ], [
 *      "tag" => "p",
 *      "content" => "There are numerous examples on the website. Please check them out to get more context on how scraping works."
 *    ], [
 *      "tag" => "h3",
 *      "content" => "Example 1"
 *    ], [
 *      "tag" => "p",
 *      "content" => "Here would be an example."
 *    ], [
 *      "tag" => "h3",
 *      "content" => "Example 2"
 *    ], [
 *      "tag" => "p",
 *      "content" => "Here would be the second example."
 *    ], [
 *      "tag" => "h3",
 *      "content" => "Example 3"
 *    ], [
 *      "tag" => "p",
 *      "content" => "Here would be another example."
 *    ]
 * ]
 */
 */
```