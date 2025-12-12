# Building an eCommerce Data Pipeline

Over the next few months, while I develop SQL, Python and automation skills, I will be applying everything I learn to improve my business systems. I will document certain stages to showcase what I have learned, and if anyone is interested in any of these fields and wants to collab, or discuss anything then I'd be more than happy to connect.

**Connect:** [LinkedIn](https://www.linkedin.com/in/JamesFoxEcom/) | [GitHub](https://github.com/JamesFoxDevTech)

---

## The Project

Building an AI-powered data pipeline for my eCommerce business.

**The Problem:** Managing 15,000+ products from multiple suppliers with messy, inconsistent data.

**What I'm Building:** 
```
Supplier CSV → AI Transformation → Database → Marketplace Exports
```

---

## Tech Skills I'm Learning/Developing

- **SQL** - PostgreSQL database design, normalisation, complex queries
- **Python** - Data processing, API integration, validation scripts
- **Low-code automation** - n8n workflows for orchestration
- **AI integration** - Claude API for SEO, local LLM for attribute extraction
- **Prompt engineering** - Structured outputs, validation loops, multi-agent systems

---

## The System

### Database Structure
Five core tables:
- **products_core** - Universal product data (SKU, title, description, dimensions)
- **products_pricing** - Cost and pricing data
- **products_inventory** - Stock levels
- **products_images** - Image URLs (S3 storage)
- **products_marketplace_specifics** - Flexible attributes for different marketplaces (eBay, Amazon, etc.)

### Transformation Pipeline
1. **Input** - Supplier CSV with unstructured data
2. **Pre-processing** - Clean HTML, normalise text
3. **AI Extraction** - Pull structured attributes using category-specific schemas
4. **SEO Generation** - Multi-agent system creates optimised content
5. **Validation** - Quality checks and flagging for manual review
6. **Database Load** - Insert into PostgreSQL
7. **Export** - Generate marketplace-ready CSV templates

---

## Hardest Challenges

**1. Character Counting (Not Token Counting)**
Marketplace title limits are in characters (e.g., 80 chars), but LLMs think in tokens. A 79-token title might be 95 characters. 

Solution: Python validation function that counts `len(string)` and feeds back corrections to the LLM until it's exactly right.

**2. AI Quality at Scale**
Batch API calls produce templated, generic SEO content. AI starts reusing phrases and loses focus.

Solution: Multi-agent system where each agent handles a specific stage separately, then compiles into structured output. Process one product at a time with full context to maintain quality.

**3. Brand Consistency Across 15,000+ Products**
Need to remove supplier brand mentions and maintain our brand voice consistently.

Solution: Dedicated validation agent with brand-specific rules, keyword requirements, and SEO guidelines. Category-specific files ensure relevance.

**4. Flexible Marketplace Requirements**
eBay, Amazon, and Wayfair all want different attributes for the same product type.

Solution: Core product table for universal data + flexible marketplace_specifics table with key-value pairs. One product, many marketplace representations.

---

## The Stages

### Stage 1: Foundation
- Design database schema
- Build category-specific extraction rules  
- Create AI transformation pipeline
- Develop multi-agent SEO system

### Stage 2: Testing
- Process first category (~50 products) end-to-end
- Identify what breaks
- Refine prompts and validation
- Manual data completion where needed

### Stage 3: Refinement
- Add more categories
- Build multi-marketplace export templates
- Improve automation and error handling
- Document patterns and edge cases

### Stage 4: Scale
- Process entire 15,000 product catalogue
- Create 100+ category schemas
- Daily batch processing
- Quality monitoring

---

## Current Progress

**Stage 1:** 🟡 In Progress
- ✅ Database schema designed
- 🔄 Building transformation pipeline
- 🔄 Testing AI extraction
- 🔄 Developing SEO agent system

---

## Multi-Agent SEO System

The trickiest part of this project. My approach:

**Agent 1: SEO Specialist**
- Takes product attributes + category keywords
- Generates optimised title, description, bullet points
- Focuses on quality, not character count

**Agent 2: Character Counter** (Python Function)
- Validates exact character count (78-80 chars for titles)
- Feeds back corrections if needed
- Loops until perfect

**Agent 3: Brand Consistency Checker**
- Validates brand voice
- Checks for supplier brand leakage
- Ensures keyword presence
- Validates bullet point formatting

**Agent 4: Compilation**
- Assembles final approved content
- Structures for database insertion

Sequential processing prevents the templating problem. Each product gets full attention before moving to the next.

---

## What's Shared vs. What's Not

**Shared:**
✅ System architecture and approach  
✅ Problem-solving methodology  
✅ Technical learnings as I go  
✅ Example implementations (generic)

**Not Shared:**
❌ Production code  
❌ Specific category schemas (100+ categories worth of rules)  
❌ Brand-specific prompts and SEO strategies  
❌ Supplier relationships or data

I'm documenting the journey and approach, not giving away the complete solution.

---

## Repository Structure (Building This Out)

```
ecommerce-data-pipeline/
├── README.md (this file)
├── docs/
│   ├── database-schema.md
│   ├── transformation-pipeline.md
│   └── lessons-learned.md
├── examples/
│   ├── sample_category_schema.json
│   ├── character_counter.py
│   └── sample_workflow.txt
└── diagrams/
    └── pipeline-flow.png
```

---

## Let's Connect

If you're working on similar problems, learning the same stack, or just think this is interesting - I'd be happy to chat.

**LinkedIn:** [JamesFoxEcom](https://www.linkedin.com/in/JamesFoxEcom/)  
**GitHub:** [JamesFoxDevTech](https://github.com/JamesFoxDevTech)

---

*This is a work in progress. I'll update as I build.*
