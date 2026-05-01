Short Answer Questions
Worknoon WordPress Assessment - Section E
1. Difference Between Google Knowledge Graph and Google Knowledge Panel
These two terms are related but describe different things and are commonly confused.
The Google Knowledge Graph is Google's internal database,  a massive, interconnected map of entities (people, places, organisations, concepts) and the relationships between them. It was introduced in 2012 and powers much of Google's ability to understand meaning rather than just match keywords. It draws from sources including Wikipedia, Wikidata, Google Business Profiles, Schema.org structured data, and authoritative web content. The Knowledge Graph is infrastructure it is not something a user ever sees directly.
The Google Knowledge Panel is the visual card that appears on the right side of Google search results (on desktop) or at the top of results (on mobile) when someone searches for a well-known entity. It is a display layer,  a front-end presentation of data that Google has already confirmed in the Knowledge Graph.
The relationship between them:
The Knowledge Graph is the database
The Knowledge Panel is the display of a record from that database
A practical way to think about it: the Knowledge Graph is the library, and the Knowledge Panel is what gets shown to you when you look up a specific book. An entity can exist in the Knowledge Graph without having a Knowledge Panel.  Google only generates a panel when it has enough confidence in the entity and determines that a panel would be useful for searchers.
For Worknoon, the goal is first to get the brand into the Knowledge Graph (through schema, citations, and consistent signals), which then creates the conditions under which a Knowledge Panel may appear.
2. How Google Determines Entity Identity
Google determines entity identity through a process called entity disambiguation,  establishing that a name refers to one specific, distinct thing in the world and not something else with a similar name.
Google uses several signals to confirm and define an entity's identity:
Structured data (Schema.org) is the most direct signal. When a website publishes JSON-LD markup with "@type": "Organisation" or "@type": "Person", it explicitly declares what the entity is, who it is connected to, and where it can be corroborated.
The sameAs property is particularly powerful. Each URL listed in sameAs  LinkedIn, GitHub, Crunchbase, and a Wikidata item  is a node that Google can traverse to confirm that the same entity exists across multiple independent sources. The more authoritative and consistent these nodes are, the more confident Google becomes in the entity's identity.
NAP consistency (Name, Address, Phone) across directories and listings tells Google that multiple sources agree on the same facts about the same entity. Inconsistencies, such as  different spellings of a name, different phone formats, and different addresses,  create ambiguity and weaken entity confidence.
Co-citation and co-occurrence,  when authoritative third-party sources mention the entity name alongside consistent attributes (founder name, location, industry) without a direct link, Google still uses this as a corroborating signal.
Wikipedia and Wikidata carry significant weight because they are structured, editable-by-the-public sources that Google has deeply integrated into the Knowledge Graph. An entity with a Wikidata item is much easier for Google to identify and confirm than one without.
User behaviour signals  when many users search for "Worknoon" as a navigational query and consistently click through to the same website. Google interprets this as confirmation that the entity is real and that the website is its canonical home.
In summary, Google does not determine entity identity from a single source. It builds confidence incrementally by finding agreement across structured data, independent citations, user behaviour, and authoritative reference databases.
3. When to Create Custom Post Types Instead of Pages
Pages in WordPress are for static, standalone content that sits outside the normal flow of the site, such as  the homepage, About page, Contact page, and Services page. They have no category, no archive, and are typically organised in a simple parent-child hierarchy.
Custom Post Types (CPTs) should be created when you have a repeatable content type that shares the same structure across many entries and benefits from its own archive, taxonomy, or query logic. The decision is essentially: will I need more than one of these, and do they all follow the same pattern?
Create a Custom Post Type when:
The content is repeatable and structured,  for example, a portfolio of client projects, a team member directory, a testimonials library, a services catalogue, or a case study archive. Each entry has the same fields: title, featured image, description, category.
You need a dedicated archive page.  CPTs automatically generate archive URLs like /projects/ or /case-studies/ that list all entries, which is not possible with standard pages
You need custom taxonomies  if you want to filter or group entries (e.g. filter projects by industry, or filter team members by department). CPTs support custom taxonomies that pages do not
You want to query the content dynamically.  CPTs integrate cleanly with WP_Query, Elementor's loop builder, and tools like ACF (Advanced Custom Fields), making it straightforward to display filtered or sorted collections anywhere on the site
The content is managed by non-developers. A CPT with ACF fields gives clients a clean, structured form to fill in rather than a blank Gutenberg editor, reducing errors and maintaining design consistency
Stick with Pages when:
The content is unique, one-off, and doesn't repeat (About, Contact, Privacy Policy)
There is no need for filtering, archiving, or dynamic queries
The content structure varies significantly between entries
For Worknoon specifically, a Portfolio CPT and a Testimonials CPT would be appropriate additions to the current site. Each has a repeatable structure, and both would benefit from a dedicated archive and the ability to query and display them dynamically using Elementor's loop widget.
4. Recommended Plugins for Speed Optimisation and Why
Page speed directly affects both user experience and Google's decision to crawl and index pages. The following plugins address the most common performance bottlenecks on WordPress and Elementor sites.
LiteSpeed Cache
Why: LiteSpeed Cache is the most comprehensive free caching plugin available for WordPress. It handles full-page caching, browser caching, object caching, database optimisation, image lazy loading, CSS and JavaScript minification, and CDN integration  all in a single plugin. For sites hosted on LiteSpeed servers (common with cPanel hosting), it integrates directly with the server-level cache for significantly faster response times than software-only solutions.
It is the recommended first install for any new WordPress site before any other optimisation work begins.
Smush or ShortPixel (Image Optimisation)
Why: Images are the single largest contributor to slow page load times on most landing pages, especially sites built in Elementor with full-width hero sections and background images. Both plugins compress images on upload without visible quality loss:
Smush  free tier compresses images on upload and bulk-compresses existing uploads; simple interface, good for most use cases
ShortPixel has  slightly better compression ratios, supports WebP conversion (the modern image format Google recommends), and handles PDF optimisation; the free tier gives 100 credits per month
WebP conversion is particularly important because  Google's PageSpeed Insights flags non-WebP images as a performance issue, and switching to WebP typically reduces image file size by 25–35% compared to JPEG.
Cloudflare (Free CDN)
Why: Cloudflare is not strictly a plugin but a DNS-level service that acts as a CDN (Content Delivery Network), serving cached copies of your site from servers closest to each visitor. For a Lagos-based site that may be accessed by clients across Nigeria or internationally, Cloudflare significantly reduces Time to First Byte (TTFB)  one of the key metrics Google uses when evaluating page speed. The free tier includes DDoS protection, SSL, and basic performance optimisation at no cost. The WordPress plugin allows cache purging directly from the dashboard.
Asset CleanUp or Perfmatters (Script Manager)
Why: WordPress loads JavaScript and CSS files for every active plugin on every page, even when those scripts are not needed on that particular page. Asset CleanUp and Perfmatters both allow you to disable specific scripts on specific pages  for example, disabling the WPForms scripts on pages that have no contact form. This reduces page weight and eliminates render-blocking resources that delay page paint. Perfmatters also includes database cleanup, DNS prefetching, and lazy loading controls in a very lightweight package.
Summary
Plugin	What It Solves	Priority
LiteSpeed Cache: Full-page caching, minification, lazy loading. Install first
Smush / ShortPixel	Image file size, WebP conversion,	Install second
Cloudflare	CDN, global delivery speed, TTFB,	Set up early
Asset CleanUp / Perfmatters	Render-blocking scripts, unused CSS/JS	Fine-tuning stage
The correct order of implementation matters: set up caching first, then optimise images, then configure the CDN, then fine-tune scripts. Doing it in the wrong order makes it harder to measure the impact of each change.
Document prepared for: Worknoon WordPress Assessment Submission 
Author: Kofoworola Ajani 
GitHub: github.com/kofoworolaaj 
Date: May 2026
