SEO Technical Troubleshooting
Scenario: Worknoon Website Not Indexing After Sitemap Submission
Overview
Sitemap submission does not guarantee indexing. Google treats submitted sitemaps as requests, not instructions. When a new site fails to index, the cause is almost always one of six categories: crawlability barriers, canonical conflicts, robots or noindex directives, sitemap errors, page speed thresholds, or unresolved Search Console signals.
This document walks through each category systematically, starting with the most common causes.
1. Crawlability Tests
Crawlability is the first thing to check. If Google cannot reach the page, nothing else matters.
URL Inspection Tool (First Step)
In Google Search Console, use the URL Inspection Tool on your homepage:
1.Go to Search Console → paste https://kofoworola-worknoon.htwcleaning.com/ into the top bar
2. Hit Enter and wait for the report
3. Read the Coverage status: 
1. URL is on Google already indexed, no crawl issue
2. URL is not on Google, not indexed; check the reason shown
3. Discovered currently not indexed, Google found it, but hasn't crawled it yet
4. Crawled currently not indexed. Google visited but decided not to index it
Fetch and Render Test
Still in the URL Inspection Tool:
1. Click "Test Live URL."
2. Then click "View Tested Page" → Screenshot tab
3. Check whether the page renders visually; if it looks broken or blank, Google sees the same thing and will not index it
4. Check the "More Info" tab for blocked resources (JavaScript, CSS files that are disallowed in robots.txt)
Check for Server Errors
Run this command in your terminal or use a tool like httpstatus.io:
curl -I https://kofoworola-worknoon.htwcleaning.com/
Look for the HTTP status code in the response:
200 OK: page is reachable
301/302: redirect chain; confirm it resolves to the correct final URL
403 Forbidden: server is blocking access; check hosting settings
500 Server Error: WordPress or server issue; check error logs in cPanel
Check DNS and Hosting Propagation
For brand new sites, DNS propagation can take up to 48 hours. Verify the site is globally accessible using dnschecker.org:enter your domain and confirm green check marks across all regions.
2. Canonical Checks
A misconfigured canonical tag tells Google that a different URL is the "real" version of your page, causing Google to ignore the page you actually want indexed.
How to Inspect Canonical Tags
In your browser on the Worknoon homepage:
1. Right-click → View Page Source
2. Press Ctrl+F and search for canonical
3. You should find exactly one line like this:
<link rel="canonical" href="https://kofoworola-worknoon.htwcleaning.com/" />
Common Canonical Problems to Look For
Self-referencing canonical is missing: without it, Google may choose a canonical URL itself, which might not be the one you want
Canonical points to HTTP instead of HTTPS: if the tag reads http:// but your site runs on https://, fix it immediately in WordPress → Settings → General
Canonical points to a different domain: this can happen with staging sites or when WordPress General Settings still contain the old URL
Multiple canonical tags: some plugins add their own canonical tags; if two appear on the same page, Google ignores both. Check for conflicts between Rank Math and your theme
Fixing Canonicals in WordPress
In Rank Math → Titles & Meta → Homepage:
Ensure "Canonical URL" field is either blank (auto) or set to your exact homepage URL with HTTPS
In WordPress → Settings → General, confirm both "WordPress Address" and "Site Address" are set to https://kofoworola-worknoon.htwcleaning.com
3. Robots.txt & Noindex Audit
This is the most common cause of indexing failure for new WordPress sites: a setting left over from the development phase that tells Google to stay away.
Check the Robots.txt File
Visit this URL directly in your browser:
https://kofoworola-worknoon.htwcleaning.com/robots.txt
A healthy robots.txt for Worknoon should look like this:
User-agent: *
Disallow:

Sitemap: https://kofoworola-worknoon.htwcleaning.com/sitemap_index.xml
Red flags to look for:
Disallow: /          ← blocks ALL crawling : critical error
Disallow: /?         ← blocks query string pages
User-agent: Googlebot
Disallow: /          ← blocks Google specifically
If you see Disallow: /, your entire site is blocked from crawling. Fix it immediately.
Fix Robots.txt in WordPress
Go to Rank Math → General Settings → Edit robots.txt and correct the rules. Alternatively, use the Yoast SEO or All in One SEO robots.txt editor if Rank Math is unavailable.
Check the WordPress "Discourage Search Engines" Setting
This is the most frequently missed cause on new WordPress sites:
1. Go to WordPress → Settings → Reading
2. Look for the checkbox: "Discourage search engines from indexing this site."
3. If it is checked, uncheck it immediately
This single checkbox adds Disallow: / to your robots.txt and a noindex meta tag to every page on your site.
Check for Noindex Meta Tags
In the page source, search for:
<meta name="robots" content="noindex">
If this appears on your homepage or any page you want indexed, it must be removed. In Rank Math:
Go to the page → Rank Math SEO box → Advanced tab
Ensure "Robots Meta" is set to Index, not No Index
4. Sitemap Structure Issues
A submitted sitemap that contains errors will not result in indexing, and Google Search Console may not always make the error obvious.
Check Sitemap Accessibility
Visit your sitemap URL directly:
https://kofoworola-worknoon.htwcleaning.com/sitemap_index.xml
It should load as an XML file listing your child sitemaps. If it returns a 404 error:
1. Go to WordPress → Settings → Permalinks
2. Click Save Changes without changing anything: this flushes the rewrite rules and usually regenerates the sitemap
Common Sitemap Errors
Sitemap contains noindex URLs: pages flagged as noindex should not appear in the sitemap; Rank Math handles this automatically, but verify by checking the sitemap XML for pages you know are set to noindex
Sitemap contains 404 pages: deleted pages that still appear in the sitemap confuse Googlebot and waste crawl budget
Sitemap URL does not match submitted URL: if you submitted sitemap.xml but Rank Math generates sitemap_index.xml, Google will report a fetch error
Sitemap is blocked by robots.txt: confirm your robots.txt includes Sitemap: pointing to the correct URL and that the sitemap path is not under a Disallow rule
Validate the Sitemap
Use XML Sitemap Validator at xmlsitemaps.com/validate-xml-sitemap or paste your sitemap URL into the Google Search Console → Sitemaps report and read the status:
Success: sitemap was read without errors
Couldn't fetch: URL is wrong or blocked
Has errors: open the sitemap and look for malformed XML
5. Page Speed Indexing Blockers
Google allocates crawl resources differently depending on site quality, performance, and authority: slow pages get deprioritised and may not be indexed promptly or at all. Core Web Vitals scores also influence how aggressively Google crawls a new site.
Run a Core Web Vitals Test
Go to pagespeed.web.dev and enter your homepage URL. Focus on:
LCP (Largest Contentful Paint): should be under 2.5 seconds; if above 4s, Google may deprioritise crawling
FID / INP (Interaction to Next Paint): should be under 200ms
CLS (Cumulative Layout Shift): should be under 0.1
Common Speed Blockers on New WordPress Sites
No caching plugin active: install and activate LiteSpeed Cache or W3 Total Cache; enable page caching as a minimum
Unoptimised images: large PNG or uncompressed JPEG files in the hero section are the most common culprit; use Smush or ShortPixel to compress all uploads
Render-blocking JavaScript: scripts loading in the <head> that delay page paint; in LiteSpeed Cache → Page Optimisation → defer JavaScript
No CDN: for a Lagos-based site, enabling Cloudflare's free CDN significantly reduces load time for international crawlers
Check for JavaScript-Rendered Content
Googlebot can render JavaScript, but heavy client-side rendering or blocked resources can still delay indexing. In the URL Inspection Tool → "View Tested Page" → Screenshot, if the page appears blank or partially rendered, your content may be invisible to Google. Elementor pages are generally fine, but confirm by comparing the screenshot to what you see in a browser.
6. Search Console Debugging Steps
Google Search Console is the authoritative source of truth for indexing issues. Use it in this order after all the above checks are complete.
Step 1: Confirm Ownership Verification
Go to Search Console → Settings → Ownership Verification. Confirm that at least one verification method shows as verified. If verification has lapsed (common with HTML tag methods), re-verify immediately :an unverified property does not receive indexing data.
Step 2: Check the Coverage Report
Go to Search Console → Indexing → Pages:
"Not indexed" tab: read every reason listed and the number of pages affected
Common reasons and their fixes:
Reason Shown	What It Means	Fix
Crawled: currently not indexed. Google visited but chose not to index. Improve content quality and internal links
Discovered: currently not indexed. In the queue, but not yet crawled. Request indexing; check crawl budget
Blocked by robots.txt. robots.txt is blocking the URL	Fix Disallow rules
Noindex tag detected. A noindex directive is present. Remove the noindex tag
Duplicate without canonical	Google found a preferred version elsewhere. Fix the canonical tag
Redirect error: Broken redirect chain. Fix in WordPress redirects or .htaccess
Not found (404)	Page returns 404. Restore the page or set up a redirect
Step 3: Request Indexing
For your homepage and key pages:
1. Paste the URL into the URL Inspection Tool
2. Click "Request Indexing"
3. Google adds it to a priority crawl queue: results typically appear within 24–72 hours for new sites
Note: you can only request indexing a limited number of times per day, so prioritise your homepage and services page first.
Step 4: Check the Sitemaps Report
Go to Search Console → Indexing → Sitemaps:
Confirm your sitemap shows Success status
Check "Discovered URLs" vs "Indexed URLs": a large gap means Google is finding pages but not indexing them, pointing to a quality or crawl budget issue
If the status shows an error, delete the sitemap entry and resubmit the correct URL
Step 5: Check Manual Actions and Security Issues
Go to Search Console → Security & Manual Actions:
Manual Actions: if Google has manually penalised the site, a message will appear here explaining why; this is rare for new sites, but worth checking
Security Issues: If Google has detected malware or hacked content, the site will not be indexed until the issue is resolved
Step 6: Monitor Crawl Stats
Go to Search Console → Settings → Crawl Stats:
Check "Total crawl requests" over the past 90 days
For a new site, if this number is zero or very low, it confirms Google has not discovered or visited the site yet: go back to Step 1 and verify robots.txt and DNS
Summary Diagnostic Checklist
Work through this list top to bottom. The issue is almost always found within the first three sections.
Check	Tool	Expected Result
"Discourage search engines" unchecked	WordPress → Settings → Reading	Unchecked
robots.txt has no Disallow: /	Browser → /robots.txt	Disallow: empty
No noindex on homepage	Page source → search "noindex"	Not found
Canonical tag points to correct HTTPS URL	Page source → search "canonical"	Correct URL
Sitemap loads without errors	Browser → /sitemap_index.xml	Valid XML
Sitemap submitted and shows Success	Search Console → Sitemaps	Success
URL Inspection shows page renders	Search Console → URL Inspection	Page visible in screenshot
Core Web Vitals LCP under 2.5s	pagespeed.web.dev	Green score
No Manual Actions or Security Issues	Search Console → Security	No issues
Indexing requested for key pages. Search Console → URL Inspection	Request sent

Conclusion
Most indexing issues on new WordPress websites are caused by technical misconfigurations rather than penalties. A systematic approach: starting with crawlability, robots directives, canonical tags, sitemap validation, and Search Console diagnostics, usually identifies the root cause quickly.
For Worknoon, maintaining clean technical SEO foundations alongside strong content quality and performance optimisation will improve crawl efficiency and increase indexing reliability over time.
Document prepared for: Worknoon WordPress Assessment Submission 
Author: Kofoworola Ajani 
GitHub: github.com/kofoworolaaj 
Date: May 2026
