# Kofoworola-worknoon-wordpress-assessment
Kofoworola Worknoon - WordPress Assessment
A fully documented WordPress assessment submission covering landing page development, structured data, Knowledge Panel strategy, technical SEO, and system thinking.
Candidate: Kofoworola Ajani Live Site: kofoworola-worknoon.htwcleaning.com LinkedIn: Kofoworola Taiwo Ajani Instagram: @kofoworola.aj Email: kofoworolaajani1@gmail.com
Repository Structure
Kofoworola-worknoon-wordpress-assessment/
├── schema/
│   ├── organization-schema.json
│   ├── person-schema.json
│   └── website-logo-sameas-schema.json
├── docs/
│   ├── knowledge-panel-strategy.md
│   ├── seo-diagnosis.md
│   └── short-answers.md
├── wp-content/
│   ├── themes/
│   └── plugins/
└── README.md
Deliverables
Section	Deliverable	Description
A	live site, responsive WordPress landing page built with Elementor
B	/schema	JSON-LD structured data for Organisation, Person, and Website
C	knowledge-panel-strategy.md	Google Knowledge Panel optimisation strategy
D	seo-diagnosis.md	Technical SEO troubleshooting guide
E	short-answers.md	Answers to four technical assessment questions
F	README.md	Project reflection and system thinking
Section A - Landing Page
The landing page was built in WordPress using Elementor. It covers all four required sections:
Hero  bold headline, sub-copy, two CTAs, social proof stats (50+ projects, 98% satisfaction, 4× traffic growth), and a laptop UI mockup
Services  four service cards covering Web Development, SEO Optimisation, Analytics, and Automation
Testimonials:  three realistic client stories from Lagos-based businesses with specific, measurable results
Contact  WPForms Lite contact form with phone, email, and address
Plugin stack used:
Elementor 4.0.5  page builder (Hello Elementor theme)
WPForms Lite  contact form
Rank Math SEO 1.0.269  meta tags, sitemap, Open Graph, schema
WP-Optimize 4.5.3  database cleaning, image compression, page caching
Site Kit by Google 1.177.0  Google Analytics and Search Console integration
Section B  Schema Markup
Three JSON-LD files are included in the /schema folder:
organization-schema.json
Declares Worknoon as a real organisation with name, URL, logo, address, services, and sameAs social profiles. The sameAs array is the primary mechanism by which Google connects the entity across multiple independent sources.
person-schema.json
Declares the founder (Kofoworola Ajani) and links her to the organisation via the worksFor property, creating a person-to-organisation relationship that Google can traverse in the Knowledge Graph.
website-logo-sameas-schema.json
Uses the @graph format to declare the Website, Organisation, and Logo as interconnected nodes in a single JSON-LD document. The @id properties create internal links that Google uses to build a coherent entity record.
Deployment method: Injected via the Insert Headers and Footers plugin using <script type=" application/ld+json"> tags in the site header.
Validation: Tested at search.google.com/test/rich-results
Section C  Knowledge Panel Strategy
See knowledge-panel-strategy.md
Covers:
Three-phase entity recognition process (Creation → Confirmation → Potential Panel Appearance)
Step-by-step entity building: Google Business Profile, Wikidata, LinkedIn Company Page, Nigerian directories
Schema requirements and deployment
Brand identity consistency signals (NAP, logo, description)
Press and authority signals: TechCabal, Techpoint Africa, Clutch.co, ProductHunt
About page hierarchy (H1 entity declaration through to contact NAP)
Monitoring and validation tools
Section D  SEO Technical Troubleshooting
See seo-diagnosis.md
Scenario: A new Worknoon website is not being indexed after a sitemap submission.
Covers a systematic six-step diagnostic:
1. Crawlability tests  URL Inspection Tool, Fetch & Render, curl server check, DNS propagation
2. Canonical checks  how to inspect, four common mistakes, Rank Math fix
3.Robots.txt & noindex audit  the "Discourage search engines" WordPress checkbox, robots.txt red flags
4. Sitemap structure issues  validation, four common errors, permalink flush fix
5. Page speed indexing blockers,  Core Web Vitals targets, caching, image compression, JS deferral
6. Search Console debugging steps: a  six-step sequence with a full coverage error table
Section E  Short Answer Questions
See short-answers.md
1. Knowledge Graph vs Knowledge Panel:  the database vs the display layer
2. How Google determines entity identity  schema, sameAs, NAP consistency, co-citation, and user behaviour
3. Custom Post Types vs Pages  decision criteria with a Worknoon-specific recommendation
4. Recommended speed plugins:  LiteSpeed Cache, Smush/ShortPixel, Cloudflare, Asset CleanUp, with implementation order
Section F  Project Reflection
The Problem
The brief was to build a functional, optimised WordPress landing page that demonstrates real-world capability across development, technical SEO, structured data, and systems thinking. The challenge was not to build something that looks good;  it was to build something that is technically sound, semantically structured, and genuinely ready for search engine discovery.
Approach
I started with brand definition before touching WordPress. Having a clear identity,  Worknoon, as a Lagos-based digital studio with four core services,  made every subsequent decision coherent: the copy, the layout, the schema, and the entity strategy all follow from a well-defined brand.
Page architecture followed conversion principles: Hero establishes credibility → Services demonstrate capability → Testimonials provide proof → Contact gives a low-friction next step.
Schema was built as a separate layer after the page was complete, using the @graph format to create interconnected entity nodes rather than isolated declarations.
Key Decisions
Decision	Rationale
Elementor + Hello Elementor theme	Fastest path to a polished, responsive layout with complex sections (ticker, stats row, dark contact section)
Rank Math over Yoast	Free tier includes schema, Open Graph, and sitemap  features that require Yoast Premium
WP-Optimise over LiteSpeed Cache: All-in-one database cleaning, image compression, and caching in a single lightweight plugin
Site Kit by Google, an officially supported Google plugin that connects GA4 and Search Console directly,  satisfies the analytics requirement with zero configuration risk
Real testimonials 
@graph schema format	produces interconnected entity nodes rather than isolated declarations; matches Google's recommended approach
Lagos-specific positioning. Geographic grounding strengthens Knowledge Graph entity signals more than vague global positioning
Tradeoffs
Speed vs visual richness  Elementor adds page weight; mitigated with WP-Optimise caching and image compression, but a hand-coded page would score higher on Core Web Vitals
Plugin reliance vs custom code  managed plugins are appropriate at this scale; for a high-traffic enterprise site, I would reconsider
Subdomain vs custom domain,  the htwcleaning.com subdomain was the available hosting environment; in a real deployment, Worknoon would have its own domain, which is a meaningful trust and entity signal
Depth vs breadth in documentation  chose depth over breadth; each document demonstrates genuine understanding rather than surface familiarity
Challenges and Resolutions
Schema deployment  Rank Math's form-based schema builder limits output control. Resolved by using Insert Headers and Footers to inject hand-authored JSON-LD blocks directly into the site header.
Placeholder content  Elementor's testimonial widget auto-populates with lorem ipsum that looks "filled in" during building. Caught during final review and replaced with realistic client testimonials before submission.
Responsive stats row  the hero stats (50+ Projects, 98% Satisfaction, 4× Traffic Growth) collapsed awkwardly on mobile. Resolved by adjusting Elementor column gaps and setting a custom breakpoint for a centred 1×3 vertical stack.
Sitemap URL mismatch:  Rank Math generates /sitemap_index.xml, but Search Console initially showed an error against /sitemap.xml. Resolved by submitting the correct URL directly and confirming the success status.
Affiliate Tracking and Onboarding Systems
This assessment did not require building an affiliate or onboarding system, but I understand the standard WordPress implementation approaches:
FirstPromoter is a SaaS affiliate tracking platform for subscription businesses. WordPress integration involves adding the tracking script via Insert Headers and Footers or functions.php, with referral ID capture on sign-up or checkout pages. For WooCommerce sites, FirstPromoter's dedicated plugin handles cookie-based attribution, conversion tracking, and commission calculation automatically.
AffiliateWP is the preferred native WordPress alternative when client data should not leave the WordPress environment. It handles referral links, commission tracking, and affiliate dashboards entirely within the CMS.
For onboarding systems, the typical WordPress stack is: WPForms or Gravity Forms (multi-step intake) → FluentCRM or HubSpot (automated welcome sequence) → WP Customer Area (client portal for documents and project access).
If rebuilding Worknoon as a full platform, I would implement FluentCRM for onboarding and AffiliateWP for referral tracking,  both self-hosted, both avoiding recurring SaaS costs.
What I Would Improve
1. Portfolio Custom Post Type: The site describes services but shows no evidence of work; a Portfolio CPT with ACF fields would add credibility and internal linking depth
2. Custom domain: A dedicated Worknoon domain strengthens entity signals and canonical structure
3. Hybrid architecture for performance: A static GeneratePress front page with Elementor only on interior pages would produce sub-1-second LCP scores worth showing to clients
4.GA4 with custom event tracking,  CTA clicks, form submissions, and scroll depth tracked as custom events would provide the behavioural data to demonstrate the analytics service the site sells
5. Dedicated About page,  a full entity-hierarchy /about page (founder biography, headshot, mission, NAP) would significantly strengthen Knowledge Graph signals
6. Case studies as a content type,  detailed case studies (problem → approach → result) with ItemList schema would serve as both sales content and topical authority signals
Thank you for reviewing this submission. All schema files, strategy documents, and theme/plugin files are included in this repository. Live site: kofoworola-worknoon.htwcleaning.com
