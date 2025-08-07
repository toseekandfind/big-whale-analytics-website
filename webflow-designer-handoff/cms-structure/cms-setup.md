# CMS Structure Setup - Big Whale Analytics

## 📚 CMS Collections Overview

### 1. Blog Posts Collection
**Purpose:** Regular content marketing and thought leadership

#### Fields
- **Title** (Plain Text, Required)
- **Slug** (Plain Text, Required, Unique)
- **Featured Image** (Image, Required)
- **Excerpt** (Plain Text, 150 characters max)
- **Content** (Rich Text, Required)
- **Author** (Plain Text, Required)
- **Publish Date** (Date, Required)
- **Tags** (Multi-Reference, Optional)
- **Meta Title** (Plain Text, Optional)
- **Meta Description** (Plain Text, Optional)
- **Status** (Dropdown: Draft, Published, Archived)

#### Sample Blog Posts
1. **"Why Your Data Warehouse is Slowing You Down"**
   - Tags: Performance, Data Engineering
   - Excerpt: "Common performance issues and solutions for modern data stacks"

2. **"The Hidden Costs of Bad Data Models"**
   - Tags: Data Modeling, Technical Debt
   - Excerpt: "How poor data modeling creates technical debt that slows your entire organization"

3. **"How to Build a Data Team That Scales"**
   - Tags: Team Building, Hiring
   - Excerpt: "Hiring and team structure best practices for data teams"

4. **"Modern Data Stack: What You Need to Know"**
   - Tags: Data Stack, Tools
   - Excerpt: "Overview of current tools and trends in the data ecosystem"

### 2. Case Studies Collection
**Purpose:** Showcase client success stories and build credibility

#### Fields
- **Company Name** (Plain Text, Required)
- **Industry** (Dropdown: SaaS, E-commerce, B2B, Healthcare, Finance, Other)
- **Challenge** (Rich Text, Required)
- **Solution** (Rich Text, Required)
- **Results** (Rich Text, Required)
- **Timeline** (Plain Text, Required)
- **Featured Image** (Image, Required)
- **Full Case Study Content** (Rich Text, Required)
- **Client Quote** (Plain Text, Optional)
- **Client Name** (Plain Text, Optional)
- **Client Title** (Plain Text, Optional)
- **Client Company** (Plain Text, Optional)
- **Technologies Used** (Multi-Reference, Optional)
- **Services Used** (Multi-Reference, Optional)
- **Status** (Dropdown: Draft, Published, Featured)

#### Sample Case Studies
1. **"SaaS Company Data Modernization"**
   - Company: TechFlow Inc.
   - Industry: SaaS
   - Challenge: Legacy data warehouse couldn't handle 10x growth
   - Results: 90% faster query performance, 24/7 data availability

2. **"E-commerce Analytics Overhaul"**
   - Company: RetailMax
   - Industry: E-commerce
   - Challenge: Inconsistent metrics across teams
   - Results: Single source of truth, 50% reduction in reporting time

3. **"Marketing Attribution Framework"**
   - Company: GrowthCo
   - Industry: B2B SaaS
   - Challenge: Couldn't track marketing ROI effectively
   - Results: Clear ROI visibility, 30% improvement in marketing efficiency

### 3. Resources Collection
**Purpose:** Lead generation through valuable content

#### Fields
- **Title** (Plain Text, Required)
- **Type** (Dropdown: Guide, Template, Blog Post, Webinar, Case Study)
- **Description** (Plain Text, Required)
- **Featured Image** (Image, Required)
- **Download Link** (Link, Optional)
- **Content** (Rich Text, Optional)
- **File Size** (Plain Text, Optional)
- **Tags** (Multi-Reference, Optional)
- **Requires Email** (Boolean, Default: True)
- **Status** (Dropdown: Draft, Published, Featured)

#### Sample Resources
1. **"Data Strategy Framework"**
   - Type: Assessment Tool
   - Description: "Comprehensive 11-pillar assessment tool for evaluating your organization's data maturity"
   - Requires Email: True

2. **"Building Your First dbt Model"**
   - Type: Guide
   - Description: "Step-by-step guide to creating your first data model"
   - Requires Email: True

3. **"Data Stack Selection Guide"**
   - Type: Guide
   - Description: "Framework for choosing the right tools for your business"
   - Requires Email: True

3. **"KPI Framework Template"**
   - Type: Template
   - Description: "Template for building business-aligned metrics"
   - Requires Email: True

4. **"Data Quality Checklist"**
   - Type: Template
   - Description: "Comprehensive checklist for ensuring data reliability"
   - Requires Email: True

### 4. Team Members Collection
**Purpose:** Build trust through team transparency

#### Fields
- **Name** (Plain Text, Required)
- **Title** (Plain Text, Required)
- **Bio** (Rich Text, Required)
- **Photo** (Image, Required)
- **LinkedIn URL** (Link, Optional)
- **GitHub URL** (Link, Optional)
- **Expertise Areas** (Multi-Reference, Optional)
- **Order** (Number, Required)
- **Status** (Dropdown: Active, Inactive)

### 5. Services Collection
**Purpose:** Detailed service information

#### Fields
- **Service Name** (Plain Text, Required)
- **Slug** (Plain Text, Required, Unique)
- **Description** (Rich Text, Required)
- **Icon** (Image, Required)
- **Key Features** (List, Required)
- **Deliverables** (List, Required)
- **Expected Outcomes** (Rich Text, Required)
- **Process Steps** (List, Optional)
- **Technologies** (Multi-Reference, Optional)
- **Case Studies** (Multi-Reference, Optional)
- **Status** (Dropdown: Active, Inactive)

## 🔧 CMS Configuration

### 1. Collection Settings
For each collection, configure:
- **URL Structure:** `/blog/[slug]`, `/case-studies/[slug]`, etc.
- **SEO Settings:** Enable custom meta titles and descriptions
- **Pagination:** Set appropriate items per page
- **Sorting:** Default sort order (usually by date)

### 2. Reference Fields
Create these reference fields for cross-linking:

#### Tags Collection
- **Name** (Plain Text, Required)
- **Slug** (Plain Text, Required, Unique)
- **Description** (Plain Text, Optional)

#### Technologies Collection
- **Name** (Plain Text, Required)
- **Icon** (Image, Optional)
- **Description** (Plain Text, Optional)

### 3. Dynamic Lists Setup

#### Blog Posts List
- **Filter:** Published posts only
- **Sort:** By publish date (newest first)
- **Pagination:** 6 posts per page
- **Template:** Blog post card with excerpt

#### Case Studies List
- **Filter:** Published case studies only
- **Sort:** By publish date (newest first)
- **Pagination:** 4 case studies per page
- **Template:** Case study card with results highlights

#### Resources List
- **Filter:** Published resources only
- **Sort:** By type, then by title
- **Pagination:** 9 resources per page
- **Template:** Resource card with download CTA

## 📱 Dynamic Content Implementation

### 1. Blog Posts Page
```html
<!-- Blog Posts List -->
<div class="blog-posts-grid">
  <div class="blog-post-card">
    <img src="{{post.featured-image.url}}" alt="{{post.title}}">
    <h3>{{post.title}}</h3>
    <p>{{post.excerpt}}</p>
    <span class="date">{{post.publish-date}}</span>
    <a href="{{post.url}}" class="read-more">Read More</a>
  </div>
</div>
```

### 2. Case Studies Page
```html
<!-- Case Studies List -->
<div class="case-studies-grid">
  <div class="case-study-card">
    <img src="{{case-study.featured-image.url}}" alt="{{case-study.company-name}}">
    <h3>{{case-study.company-name}}</h3>
    <p class="industry">{{case-study.industry}}</p>
    <p class="results">{{case-study.results}}</p>
    <a href="{{case-study.url}}" class="read-case-study">Read Full Case Study</a>
  </div>
</div>
```

### 3. Resources Page
```html
<!-- Resources List -->
<div class="resources-grid">
  <div class="resource-card">
    <img src="{{resource.featured-image.url}}" alt="{{resource.title}}">
    <h3>{{resource.title}}</h3>
    <p>{{resource.description}}</p>
    <span class="type">{{resource.type}}</span>
    <a href="{{resource.download-link}}" class="download-btn">Download</a>
  </div>
</div>
```

## 🔍 Search and Filtering

### 1. Search Functionality
Implement search across:
- Blog post titles and content
- Case study company names and content
- Resource titles and descriptions

### 2. Filtering Options
- **Blog Posts:** By tags, date range, author
- **Case Studies:** By industry, services used, technologies
- **Resources:** By type, tags, file size

### 3. URL Parameters
Set up URL parameters for:
- Search queries
- Filter selections
- Pagination
- Sort options

## 📊 Analytics Integration

### 1. Content Performance Tracking
Track metrics for:
- Most popular blog posts
- Most downloaded resources
- Most viewed case studies
- Search queries
- Content engagement

### 2. Lead Generation Tracking
Monitor:
- Resource downloads
- Newsletter signups
- Contact form submissions
- Consultation bookings

## 🚀 Content Management Workflow

### 1. Content Creation Process
1. **Draft Creation:** Create content in CMS
2. **Review Process:** Internal review and approval
3. **SEO Optimization:** Add meta tags and keywords
4. **Publishing:** Set status to published
5. **Promotion:** Share on social media and email

### 2. Content Calendar
- **Weekly:** Blog posts
- **Monthly:** Case studies
- **Quarterly:** Major resources and guides
- **As Needed:** Team updates and announcements

### 3. Content Maintenance
- **Monthly:** Review and update existing content
- **Quarterly:** Archive outdated content
- **Annually:** Content audit and strategy review

---

**This CMS structure provides a scalable foundation for managing dynamic content that drives leads and builds credibility for Big Whale Analytics.** 