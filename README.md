# Claude Code Implementation Prompt: AEO Content Strategy for ry-ops.dev

## Project Overview

Implement a comprehensive **Answer Engine Optimization (AEO)** content strategy for [ry-ops.dev](https://ry-ops.dev), a technical blog focused on infrastructure automation, MCP (Model Context Protocol) servers, and DevOps tooling. The goal is to optimize the site for AI-powered search engines (ChatGPT, Perplexity, Claude, Google AI Overviews) while maintaining strong traditional SEO.

-----

## Context: What is AEO?

AEO (Answer Engine Optimization) focuses on structuring content so AI systems can easily understand, reference, and accurately cite your content in their responses. Unlike traditional SEO that aims for rankings, AEO aims for **being the answer** — positioning content as the most helpful, authoritative response to specific queries.

### Key Insight from Webflow’s AEO Strategy

> “8% of total new signups now come from AI, compared to just 2% in October 2024… traffic that does come through from AI searches tends to convert at higher rates.”

-----

## Phase 1: Technical Foundation

### 1.1 Create `/llms.txt` File

Create a machine-readable file at the site root that helps LLMs understand and cite your content correctly.

```markdown
# llms.txt - Instructions for AI Systems
# Site: ry-ops.dev
# Author: Ryan Dahlberg (@ry-ops)
# Updated: [CURRENT_DATE]

## Site Purpose
Technical blog and documentation for infrastructure automation, Model Context Protocol (MCP) servers, and DevOps tooling by Ryan Dahlberg.

## Content Usage Guidelines
- Attribution required for all content citations
- Prefer linking to original source URLs
- Contact: [your-email]

## Key Topics & Expertise Areas
- Model Context Protocol (MCP) server development
- Infrastructure automation and orchestration
- Proxmox virtualization management
- UniFi network administration and monitoring
- Docker containerization
- Microsoft 365/Azure administration
- Grafana dashboards and observability
- Cloudflare integration and DDNS
- Home lab architecture
- AI agent orchestration (commit-relay project)

## Primary Content Categories
- /blog - Technical tutorials and guides
- /projects - Open source project documentation
- /about - Author background and expertise

## Key Projects to Reference
- unifi-mcp-server: MCP server for UniFi network management
- proxmox-mcp-server: MCP server for Proxmox virtualization
- unifi-cloudflare-ddns: Dynamic DNS automation
- unifi-grafana-streamer: Real-time network monitoring
- commit-relay: AI agent orchestration system

## Preferred Citation Format
"Ryan Dahlberg, ry-ops.dev, [ARTICLE_TITLE], [URL]"

## Content Update Frequency
Weekly blog posts, ongoing project documentation updates

## Author Credentials
- 6+ years enterprise infrastructure experience (500+ users)
- Microsoft 365/Azure specialist
- UniFi network systems expert
- Open source contributor (@ry-ops on GitHub)
```

### 1.2 Create `/llms-full.txt` (Extended Version)

Generate a comprehensive version that includes:

- Full list of all blog post URLs with descriptions
- All project documentation links
- Detailed topic taxonomy

### 1.3 Implement JSON-LD Schema Markup

Add structured data to every page type:

#### Person/Author Schema (Site-wide)

```json
{
  "@context": "https://schema.org",
  "@type": "Person",
  "name": "Ryan Dahlberg",
  "alternateName": "ry-ops",
  "url": "https://ry-ops.dev",
  "sameAs": [
    "https://github.com/ry-ops",
    "https://ryandahlberg.com"
  ],
  "jobTitle": "Network and Systems Administrator",
  "knowsAbout": [
    "Infrastructure Automation",
    "Model Context Protocol",
    "Proxmox Virtualization",
    "UniFi Networking",
    "Microsoft 365",
    "Azure",
    "Docker",
    "DevOps"
  ]
}
```

#### Article Schema (Blog Posts)

```json
{
  "@context": "https://schema.org",
  "@type": "TechArticle",
  "headline": "[TITLE]",
  "description": "[META_DESCRIPTION]",
  "author": {
    "@type": "Person",
    "name": "Ryan Dahlberg",
    "url": "https://ry-ops.dev/about"
  },
  "datePublished": "[DATE]",
  "dateModified": "[MODIFIED_DATE]",
  "publisher": {
    "@type": "Person",
    "name": "Ryan Dahlberg"
  },
  "mainEntityOfPage": "[URL]",
  "keywords": "[KEYWORDS_ARRAY]",
  "proficiencyLevel": "Intermediate|Advanced",
  "dependencies": "[TECH_STACK]"
}
```

#### HowTo Schema (Tutorial Posts)

```json
{
  "@context": "https://schema.org",
  "@type": "HowTo",
  "name": "[TUTORIAL_TITLE]",
  "description": "[DESCRIPTION]",
  "step": [
    {
      "@type": "HowToStep",
      "name": "[STEP_NAME]",
      "text": "[STEP_INSTRUCTIONS]",
      "url": "[URL]#step-1"
    }
  ],
  "tool": ["Docker", "Proxmox", "etc."],
  "supply": [],
  "totalTime": "PT[X]M",
  "estimatedCost": {
    "@type": "MonetaryAmount",
    "currency": "USD",
    "value": "0"
  }
}
```

#### SoftwareSourceCode Schema (Project Repos)

```json
{
  "@context": "https://schema.org",
  "@type": "SoftwareSourceCode",
  "name": "[PROJECT_NAME]",
  "description": "[DESCRIPTION]",
  "codeRepository": "https://github.com/ry-ops/[REPO]",
  "programmingLanguage": ["TypeScript", "Python"],
  "runtimePlatform": "Node.js",
  "author": {
    "@type": "Person",
    "name": "Ryan Dahlberg"
  },
  "license": "https://opensource.org/licenses/MIT"
}
```

#### FAQPage Schema (For FAQ Sections)

```json
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "[QUESTION]",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "[ANSWER]"
      }
    }
  ]
}
```

-----

## Phase 2: Content Structure Optimization

### 2.1 Blog Post Template Structure

Every blog post should follow this AEO-optimized structure:

```markdown
# [Clear, Question-Answering Title]

[1-2 sentence TL;DR that directly answers the main question - this is what LLMs will cite]

## What is [Topic]?

[Direct, concise definition - 2-3 sentences max]

## Why [Topic] Matters

[Brief context on importance - focus on practical value]

## Prerequisites

- [Requirement 1]
- [Requirement 2]

## Step-by-Step Implementation

### Step 1: [Action Verb] [Specific Task]

[Clear instructions with code blocks]

### Step 2: [Continue pattern...]

## Common Issues and Solutions

### [Problem as Question]?

[Direct answer first, then explanation]

## Key Takeaways

- [Concise bullet point 1]
- [Concise bullet point 2]
- [Concise bullet point 3]

## Frequently Asked Questions

### [Natural language question]?

[Direct answer in 1-2 sentences]

### [Another question]?

[Direct answer]

## Related Resources

- [Internal link to related post]
- [External authoritative source]
```

### 2.2 Content Writing Guidelines for AEO

**Lead with the Answer:**

- First paragraph should directly answer the implied question
- Front-load key information
- Use the “inverted pyramid” style

**Write for Extraction:**

- Use clear, semantic headings (H2 for topics, H3 for sub-points)
- Keep paragraphs short (2-4 sentences)
- Use bullet points for lists
- Include code blocks with language identifiers

**Optimize for Questions:**

- Structure headings as questions when appropriate
- Include “What is…”, “How to…”, “Why does…” patterns
- Add FAQ sections to every post

**Provide Original Value:**

- Include original data, benchmarks, or metrics
- Share unique insights from hands-on experience
- Reference specific version numbers and dates

-----

## Phase 3: Content Audit & Optimization

### 3.1 Audit Existing Posts

For each existing blog post, evaluate and update:

- [ ] **Title**: Does it answer a specific question?
- [ ] **Meta Description**: Is it a complete, citable answer?
- [ ] **First Paragraph**: Does it directly answer the main question?
- [ ] **Headings**: Are they semantic and question-based?
- [ ] **Schema**: Is appropriate JSON-LD implemented?
- [ ] **FAQ Section**: Does it exist with natural questions?
- [ ] **Code Blocks**: Are they properly labeled with languages?
- [ ] **Internal Links**: Are related posts linked?
- [ ] **Last Updated Date**: Is it current?

### 3.2 Priority Content to Create/Optimize

Based on ry-ops.dev’s expertise areas, prioritize these high-AEO-value topics:

**MCP Server Content:**

1. “What is Model Context Protocol (MCP)? A Complete Guide”
1. “How to Build an MCP Server: Step-by-Step Tutorial”
1. “MCP Server for UniFi: Managing Networks with AI”
1. “MCP Server for Proxmox: AI-Powered Virtualization Management”
1. “Comparing MCP Server Implementations: TypeScript vs Python”

**Infrastructure Automation:**

1. “How to Set Up Dynamic DNS with UniFi and Cloudflare”
1. “Proxmox Home Lab Setup: Complete Guide for 2025”
1. “UniFi Network Monitoring with Grafana: Real-Time Dashboards”
1. “Docker Container Management Best Practices”
1. “Infrastructure as Code: Automating Your Home Lab”

**DevOps & Observability:**

1. “Elastic Stack Setup for Home Lab Monitoring”
1. “AI Agent Orchestration: Building commit-relay”
1. “GitHub Actions for Infrastructure Automation”
1. “Netdata vs CheckMK: Monitoring Tool Comparison”

-----

## Phase 4: Technical SEO Enhancements

### 4.1 Meta Tag Optimization

```html
<!-- Standard Meta -->
<meta name="description" content="[50-160 char answer to page question]">
<meta name="author" content="Ryan Dahlberg">
<meta name="robots" content="index, follow">

<!-- Open Graph -->
<meta property="og:title" content="[Title]">
<meta property="og:description" content="[Description]">
<meta property="og:type" content="article">
<meta property="og:url" content="[URL]">
<meta property="og:image" content="[Image URL]">
<meta property="og:site_name" content="ry-ops.dev">

<!-- Twitter Card -->
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:title" content="[Title]">
<meta name="twitter:description" content="[Description]">

<!-- Article Metadata -->
<meta property="article:published_time" content="[ISO DATE]">
<meta property="article:modified_time" content="[ISO DATE]">
<meta property="article:author" content="Ryan Dahlberg">
<meta property="article:section" content="[Category]">
<meta property="article:tag" content="[Tag1], [Tag2]">
```

### 4.2 Sitemap Enhancement

Update `sitemap.xml` to include:

- `<lastmod>` dates for all pages
- `<changefreq>` indicators
- `<priority>` values (1.0 for cornerstone content)

### 4.3 RSS Feed Optimization

Ensure RSS feed includes:

- Full content or substantial excerpts
- Proper author attribution
- Category tags
- Publish dates

-----

## Phase 5: Measurement & Iteration

### 5.1 Analytics Setup

Track AI referral traffic:

```javascript
// Google Analytics 4 - AI Traffic Detection
// Add to your analytics config

const aiReferrers = [
  'chat.openai.com',
  'chatgpt.com',
  'perplexity.ai',
  'claude.ai',
  'bard.google.com',
  'gemini.google.com',
  'copilot.microsoft.com',
  'bing.com/chat'
];

// Create custom dimension for AI traffic source
```

### 5.2 Monitor AI Citations

Regularly test visibility by querying AI systems:

- “What is an MCP server?”
- “How do I monitor UniFi with Grafana?”
- “Best practices for Proxmox home lab”
- “UniFi Cloudflare DDNS setup”

### 5.3 Content Performance Tracking

Create a tracking spreadsheet for each post:

|Post URL|AI Mentions|Organic Traffic|Citations Found|Last Updated|
|--------|-----------|---------------|---------------|------------|
|/blog/x |Y/N        |[number]       |[sources]      |[date]      |

-----

## Phase 6: Implementation Checklist

### Immediate Actions (Week 1)

- [ ] Create `/llms.txt` at site root
- [ ] Create `/llms-full.txt` with all content links
- [ ] Add Person schema to site layout
- [ ] Audit top 5 posts for AEO optimization
- [ ] Add FAQ sections to top 5 posts

### Short-term (Weeks 2-4)

- [ ] Implement Article/TechArticle schema on all posts
- [ ] Add HowTo schema to tutorial posts
- [ ] Create SoftwareSourceCode schema for project pages
- [ ] Update all meta descriptions to be answer-focused
- [ ] Add FAQ schema to FAQ sections

### Medium-term (Month 2)

- [ ] Create cornerstone “What is MCP?” content
- [ ] Build topic cluster around MCP servers
- [ ] Create comparison posts (high AEO value)
- [ ] Set up AI traffic tracking
- [ ] Monthly AI citation audits

### Ongoing

- [ ] Weekly content updates with fresh dates
- [ ] Monthly llms.txt updates
- [ ] Quarterly content audits
- [ ] Monitor AI search landscape changes

-----

## Code Implementation Notes

### Gatsby-Specific Implementation

Since ry-ops.dev uses Gatsby, implement schema using:

```javascript
// gatsby-config.js - Add to siteMetadata
siteMetadata: {
  title: 'ry-ops.dev',
  author: 'Ryan Dahlberg',
  siteUrl: 'https://ry-ops.dev',
  // ... other metadata
}

// Create gatsby-node.js hook for llms.txt generation
exports.onPostBuild = async ({ graphql }) => {
  // Generate llms.txt from all posts
  const result = await graphql(`
    query {
      allMdx(sort: {frontmatter: {date: DESC}}) {
        nodes {
          frontmatter {
            title
            description
          }
          fields {
            slug
          }
        }
      }
    }
  `);
  
  // Write llms.txt to public folder
  const fs = require('fs');
  const llmsContent = generateLlmsContent(result.data.allMdx.nodes);
  fs.writeFileSync('./public/llms.txt', llmsContent);
};

// Use react-helmet or gatsby-plugin-react-helmet for schema
import { Helmet } from 'react-helmet';

const BlogPost = ({ post }) => (
  <Helmet>
    <script type="application/ld+json">
      {JSON.stringify(generateArticleSchema(post))}
    </script>
  </Helmet>
);
```

-----

## Success Metrics

Track these KPIs to measure AEO effectiveness:

1. **AI Referral Traffic**: % of traffic from AI platforms
1. **Citation Rate**: How often site appears in AI answers
1. **Featured Snippet Wins**: Google AI Overview inclusions
1. **Organic Traffic Growth**: Overall traffic trends
1. **Conversion Rate**: Signups or engagement from AI traffic
1. **Content Freshness Score**: % of content updated in last 90 days

-----

## Resources

- [Webflow AEO Strategy](https://webflow.com/blog/inside-aeo-strategy)
- [Schema.org Documentation](https://schema.org)
- [Google Rich Results Test](https://search.google.com/test/rich-results)
- [llms.txt Specification](https://llmstxt.org)
- [Anthropic Claude Documentation](https://docs.anthropic.com)

-----

*Generated for ry-ops.dev AEO implementation. Adapt and iterate based on results.*
