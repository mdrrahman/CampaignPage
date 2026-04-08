CampaignCraft AI
No-code email campaign builder  ·  SFMC + AI + Product thinking
Built by mdrrahman  ·  Phase 1: Live  ·  Phase 2: SFMC CloudPage


What this is
CampaignCraft AI is a lightweight no-code email builder that removes developer dependency from campaign execution. Marketers fill a simple form, see a live preview, and generate ready-to-send HTML — with AI-powered subject lines, CTA suggestions, and body rewrites built in.

The SFMC version runs as a CloudPage, saves every submission to a Data Extension, and can fire a real preview email via Triggered Send — all without touching a line of HTML.

The problem it solves
•	Every headline change, image swap, or CTA update required a developer
•	HTML email templates broke easily — high risk, high dependency
•	Multi-brand, multi-language campaigns multiplied the bottleneck
•	Off-the-shelf WYSIWYG tools forced template compromises

Features
Phase 1 — Web version (live)
•	Form-based content input: headline, body, CTA, image, brand colour, language
•	Live email preview — updates in real time as you type
•	Desktop / mobile preview toggle
•	AI subject line generation via Claude API
•	AI CTA label suggestions
•	AI body text rewrite
•	Copy HTML to clipboard / download as .html file
•	RTL language support (Arabic)

Phase 2 — SFMC CloudPage version
•	Full AMPscript backend — no external dependencies
•	Saves every submission to CampaignCraft_Submissions Data Extension
•	Unique SubmissionID (GUID) per campaign for audit trail
•	Optional Triggered Send preview to any email address
•	Success / error handling with AMPscript result codes
•	Scales across multi-BU environments with zero code changes

Tech stack

 HTML    JavaScript    AMPscript    SFMC CloudPages    Claude API    Data Extensions    Triggered Sends    GitHub Pages 

SFMC Data Extension schema
Create this DE before deploying the CloudPage. Name must be exact: CampaignCraft_Submissions

Field name	Type	Length	Primary key
SubmissionID	Text	50	Yes
CampaignName	Text	200	No
Headline	Text	500	No
BodyText	Text	2000	No
ImageURL	Text	500	No
CTALabel	Text	100	No
CTALink	Text	500	No
BrandColor	Text	10	No
Language	Text	50	No
SubmittedAt	Date	—	No
Status	Text	50	No

Deployment — SFMC CloudPage
1.	Create the Data Extension using the schema above. Set SubmissionID as primary key.
2.	In Email Studio, create a Triggered Send with external key CampaignCraft_Preview. Attach an email template using %%Headline%%, %%BodyText%%, %%CTALabel%%, %%CTALink%%, %%BrandColor%%, %%ImageURL%% as personalisation strings.
3.	In Web Studio → CloudPages, create a new page. Paste the full contents of campaigncraft-sfmc-cloudpage.html into the code editor.
4.	Publish the CloudPage. Test by submitting the form and checking the Data Extension for the new row.

Project structure
campaigncraft-ai/
  ├── index.html                     Web version (Phase 1 — live on GitHub Pages)
  └── campaigncraft-sfmc-cloudpage.html   SFMC CloudPage version (Phase 2)

Interview talking points

What you built
A no-code email campaign builder that removes developer dependency for template updates.
Marketers input content via a form — the tool generates structured HTML in real time.
The SFMC version saves to a Data Extension and can fire real preview emails via Triggered Send.


Why it matters
Reduces campaign turnaround time by removing the dev bottleneck.
Standardises templates across brands and languages — built-in, not bolted on.
Enables self-service marketing operations at scale.
Aligns with composable architecture — tools that fit your process, not the other way around.


The bigger idea — CaaS (Custom as a Standard)
Instead of adapting to SaaS tool limitations, this approach builds exactly what the process needs.
AI reduced build time from weeks to days — making custom tooling feasible where it wasn't before.
The value is not just execution — it's identifying what shouldn't need to be manual.

