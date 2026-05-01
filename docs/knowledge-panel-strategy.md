Knowledge Panel Optimization Strategy
Worknoon - Digital Systems Studio, Lagos
1. How Worknoon Can Trigger or Strengthen a Google Knowledge Panel
A Google Knowledge Panel appears when Google has sufficient confidence that an entity, a person, brand, or organization is real, distinct, and well-documented across the web. It is not something you apply for; it is earned by consistently publishing structured, connected, and authoritative signals about your brand.
One of the strongest approaches to increasing the likelihood of triggering a Knowledge Panel is combining JSON-LD schema markup, consistent brand signals across platforms, and at least one strong third-party authority mention.
For Worknoon, the goal is to move from an unknown entity to a recognized entity in Google's Knowledge Graph. This happens in three phases:
Phase 1- Entity Creation: Google discovers that Worknoon exists as a distinct organization with a founder, a location, a set of services, and a consistent identity across multiple platforms.
Phase 2 -Entity Confirmation: Google corroborates that the entity across multiple independent sources, your website, social profiles, directories, press mentions, and schema markup all agree on the same facts.
Phase 3 - Potential Knowledge Panel Appearance: Once Google has sufficient confidence, a panel may appear for branded searches like "Worknoon" or "Kofoworola Ajani Worknoon", pulling from your confirmed entity data.
2. Entity Building Steps
Step 1- Claim and Complete All Platform Profiles
Create and fully complete profiles on the following platforms, using an identical brand name, description, logo, and contact details across all of them:
Google Business Profile: the single most important signal; go to business.google.com, create a profile for Worknoon, set the category to "Web Design Company", add your Lagos address, phone, website, and logo
LinkedIn Company Page: create a company page for Worknoon, separate from your personal profile
GitHub:  your profile at GitHub.com/kofoworolaaj already exists; add a bio mentioning Worknoon
Instagram: already active; switch to a Business account and add the website URL
Crunch base: create a free organization profile for Worknoon
AboutMe or Linktree: a simple hub page linking all your profiles
Step 2: Establish a Wikidata Presence
Google's Knowledge Graph draws heavily from Wikidata. Even without a Wikipedia article:
Create a Wikidata item for Worknoon at wikidata.org → Create new item
Add properties: name, instance of (business), country (Nigeria), website URL, founded date, founder
This directly signals to Google that Worknoon is a recognized entity in the linked data web
Step 3: Build Your Personal Entity Alongside the Brand
Google often triggers a brand panel by first recognizing the founder as a person entity. Strengthen the Kofoworola Ajani entity by:
Keeping your LinkedIn profile complete and active: it ranks highly in Google searches
Writing bylined articles or guest posts on Nigerian tech platforms, mentioning your role at Worknoon
Ensuring your name appears consistently as "Kofoworola Ajani" across all platforms: not a nickname, not an abbreviation
Step 4: Create Consistent NAP Citations
List Worknoon in Nigerian and global business directories with identical details:
VConnect Nigeria: vconnect.com
Nigerian Yellow Pages: yellowpages.com.ng
Finelib Nigeria: finelib.com (strong local directory for Lagos businesses)
Clutch.co: create a free agency profile, add your services and location
GoodFirms: digital agency directory with strong domain authority
Every listing must use exactly:
Worknoon | Lagos, Lagos State, Nigeria | +2348114324225 | kofoworolaajani1@gmail.com
3. Schema Requirements
The following JSON-LD schema types are required to build a complete entity profile for Google's Knowledge Graph. All three files are included in the /schema folder of this repository.
organization-schema.json
Tells Google that Worknoon is a real organization. Key fields that directly influence the Knowledge Panel:
"name": must match exactly across all platforms
"url": the canonical homepage
"logo": a direct image URL; Google uses this as the panel image
"sameAs": the most important field; each URL listed here is a node Google uses to connect your entity across the web. The more authoritative the sameAs URLs, the stronger the entity signal
"address": confirms geographic entity (Lagos, Nigeria)
"foundingDate": establishes entity age and stability
person-schema.json
Ties the founder to the organisation. Key fields:
"name": must be consistent with LinkedIn and all public profiles
"worksFor": links the Person entity to the Organization entity, creating a relationship Google can map
"sameAs": LinkedIn is the strongest signal here; LinkedIn profiles are commonly treated by Google as strong authority signals for person entities
website-logo-sameas-schema.json
The @graph format is the most advanced and preferred approach. It allows Google to see the Website, Organization, and Logo as interconnected nodes in a single declaration. The @id fields create internal links between entities that Google can traverse, strengthening the overall entity graph.
Deploying the Schema in WordPress
Paste each JSON-LD block into your homepage using one of these methods:
1.Rank Math → Schema → Custom Schema → paste the JSON
2.Insert Headers and Footers plugin → paste wrapped in <script type="application/ld+json"> tags
3. Validate at search.google.com/test/rich-results after deployment
4. Brand Identity Consistency Signals
Google's entity recognition depends on consistency. If your brand name, logo, description, or contact details differ across platforms, Google treats them as separate or uncertain entities and may withhold the Knowledge Panel.
Name Consistency
Use exactly "Worknoon" everywhere: not "Work Noon", not "worknoon studio", not "Worknoon Digital". One brand name, same capitalization, every platform.
Logo Consistency
Use the same logo file across:
Website favicon and header
Google Business Profile
LinkedIn Company Page
"logo" field in organization-schema.json
Open Graph image (set in Rank Math → Social tab)
Description Consistency
Write one canonical brand description and use it everywhere:
"Worknoon is a Lagos-based digital studio building high-performance websites, SEO strategies, analytics dashboards, and automation systems."
Use this on your Google Business Profile, LinkedIn About section, Crunchbase, and all directory listings.
Contact Consistency
Phone number, email, and address must be identical across every platform. Even small differences (+234 vs 0811...) can confuse Google's entity matching algorithm.
5. Press & Authority Signals
Third-party mentions are one of the most powerful triggers for a Knowledge Panel. Google needs to see that independent, authoritative sources have written about Worknoon.
Tier 1: Nigerian Tech Media (Highest Impact)
TechCabal: techcabal.com; pitch a founder story or opinion piece about digital infrastructure for Nigerian SMEs
Techpoint Africa: techpoint. Africa; submit a guest post on automation or SEO in the Nigerian market
BusinessDay Nigeria: businessday.ng; pitch a feature on web development trends
Tier 2: Global Directories with Editorial Credibility
Clutch.co: publish at least 3 client reviews; Clutch profiles rank highly in Google and serve as strong sameAs candidates
GoodFirms: a completed profile with reviews signals legitimacy
Product Hunt: launch Worknoon as a product/agency; Product Hunt pages are indexed quickly and rank well
Tier 3: Community & Forum Mentions
Publish answers on Quora mentioning Worknoon in your bio
Post case studies on Medium or Hashnode under your name with Worknoon branding
Contribute to Nigerian tech communities with your Worknoon identity
Press Release Strategy
Write a simple press release announcing the launch of Worknoon and distribute via:
PR.com: free distribution
OpenPR.com: free, indexed by Google
PRLog: free tier available
Even low-tier press distribution creates indexed pages mentioning Worknoon, which Google uses as corroborating entity signals.
6. About Page Hierarchy
The About page is one of the most important pages for entity building. Google reads it as a primary source of truth about who you are. It should follow this structure:
H1: Entity Declaration
State the brand name and core identity clearly:
About Worknoon
Immediately below, the first paragraph should state who you are, what you do, where you are based, and who you serve. This is the paragraph Google is most likely to pull as the Knowledge Panel description.
"Worknoon is a digital systems studio founded by Kofoworola Ajani in Lagos, Nigeria. We design and engineer high-performance websites, SEO strategies, analytics systems, and automation pipelines for growing businesses across Africa and beyond."
H2: Founder Section
A dedicated section introducing the founder, with:
Full name: Kofoworola Ajani
Professional background and credentials
A headshot (helps Google associate a face with the person entity)
Links to LinkedIn and GitHub profiles
This section should have Person schema markup pointing directly at it.
H2 : Mission & Values
A brief section on what Worknoon stands for. This gives Google additional entity context: industry, values, and target market, which helps correctly categorise the brand.
H2: Services Summary
A brief list of core services with internal links to the relevant homepage sections. This reinforces topical authority signals for each service.
H2 : Contact & Location
End the About page with a clear contact section, including:
Full address: Lagos State, Nigeria
Phone: +2348114324225
Email: kofoworolaajani1@gmail.com
Links to all social profiles
This structured NAP data on the About page, combined with schema markup, gives Google two consistent sources to cross-reference.
7. Monitoring & Validation
After deployment, the following tools should be used to monitor entity growth and schema health:
Google Rich Results Test: search.google.com/test/rich-results; validates that your JSON-LD schema is correctly parsed
Google Search Console: monitors indexing status, crawl errors, and how Google sees your site
Schema Markup Validator: validator.schema.org; checks your schema against the official schema.org specification
Google Knowledge Panel Feedback: once a panel appears, use the "Suggest an edit" or "Claim this Knowledge Panel" link to verify ownership and correct any inaccuracies
Brand SERP Monitoring: search "Worknoon" and "Kofoworola Ajani" monthly to track how Google's understanding of the entity evolves over time
These tools help validate structured data, monitor indexing, and identify opportunities to strengthen entity recognition over time.
Document prepared for: Worknoon WordPress Assessment Submission 
Author: Kofoworola Ajani 
GitHub: github.com/kofoworolaaj 
Date: May 2026
