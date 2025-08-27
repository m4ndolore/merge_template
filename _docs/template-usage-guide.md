# Merge Combinator Template Usage Guide

## Quick Start

### Installation
```bash
# Install the template locally for development
just install

# Or use directly in your Typst document
#import "@preview/merge-combinator:0.2.0": template
```

## Document Types

### 1. Executive Report
Professional reports for leadership and stakeholders.

```typst
#import "@preview/merge-combinator:0.2.0": template

#show: template.with(
  title: "Quarterly Business Review",
  subtitle: "Q4 2024 Performance Analysis",
  document-type: "Report",
  author: "Leadership Team",
  department: "Executive Office",
  date: datetime.today(),
  version: "1.0",
  status: "Final",
  show-toc: true,
)

= Executive Summary
Key achievements and metrics for Q4 2024...

= Performance Metrics
Detailed analysis of quarterly performance...
```

### 2. Technical Proposal
Structured proposals for technical initiatives.

```typst
#show: template.with(
  title: "Cloud Migration Strategy",
  document-type: "Proposal",
  author: "Technical Architecture Team",
  department: "Engineering",
  confidential: true,
  columns: 1,
)

= Proposal Overview
Migration strategy for legacy systems to cloud infrastructure...

= Technical Approach
Detailed technical implementation plan...
```

### 3. Business Memo
Quick communications and updates.

```typst
#show: template.with(
  title: "Policy Update Notice",
  document-type: "Memo",
  author: "HR Department",
  date: datetime.today(),
  status: "Final",
)

= To: All Staff
= From: Human Resources
= Re: Updated Remote Work Policy

Effective immediately, the following changes...
```

### 4. Project Brief
Concise project summaries and overviews.

```typst
#show: template.with(
  title: "Project Phoenix",
  subtitle: "Digital Transformation Initiative",
  document-type: "Brief",
  author: "Project Management Office",
  version: "2.3",
  columns: 2,
)

= Project Overview
Strategic initiative to modernize...

= Key Deliverables
- Phase 1: Assessment
- Phase 2: Implementation
- Phase 3: Optimization
```

## Template Parameters

### Required Parameters
- `title`: Main document title (string)

### Optional Parameters

#### Document Metadata
- `subtitle`: Secondary title line (string, default: none)
- `document-type`: Type of document (string, default: "Report")
  - Options: "Report", "Proposal", "Brief", "Memo", "White Paper"
- `date`: Document date (datetime, default: today)
- `version`: Version number (string, default: "1.0")
- `status`: Document status (string, default: "Draft")
  - Options: "Draft", "Review", "Final", "Approved"

#### Author Information
- `author`: Author name(s) (string)
- `department`: Department or division (string)
- `email`: Contact email (string, default: none)

#### Layout Options
- `columns`: Number of columns (integer, default: 1)
  - Options: 1 or 2
- `show-toc`: Display table of contents (boolean, default: false)
- `confidential`: Mark as confidential (boolean, default: false)

#### Branding
- `logo`: Company logo (image, default: arrows.png)
- `company`: Company name (string, default: "Merge Combinator, LLC")

## Styling Components

### Headings
```typst
= Level 1 Heading  // Main sections
== Level 2 Heading // Subsections
=== Level 3 Heading // Sub-subsections
```

### Lists
```typst
// Bullet points
- First item
- Second item
  - Nested item
  - Another nested item

// Numbered lists
+ First step
+ Second step
  + Sub-step A
  + Sub-step B
```

### Tables
```typst
#table(
  columns: 3,
  [*Metric*], [*Q3 2024*], [*Q4 2024*],
  [Revenue], [$2.3M], [$2.8M],
  [Growth], [15%], [22%],
)
```

### Code Blocks
```typst
```python
def merge_combinator(data):
    """Process and combine data streams."""
    return process(data)
```​
```

### Callout Boxes
```typst
#block(
  fill: rgb("#EFF6FF"),
  inset: 10pt,
  radius: 4pt,
  [*Note:* Important information highlighted here.]
)
```

### Images and Figures
```typst
#figure(
  image("chart.png", width: 80%),
  caption: "Quarterly Revenue Trends"
)
```

## Advanced Features

### Custom Headers and Footers
```typst
#show: template.with(
  title: "Custom Document",
  // Custom header content
  header-content: [Custom Header Text],
  // Custom footer content  
  footer-content: [Confidential - Page #counter(page)],
)
```

### Multi-column Layouts
```typst
#show: template.with(
  columns: 2,
)

// Content will automatically flow into two columns

// Force single column for specific sections
#columns(1)[
  This content spans the full width.
]
```

### Table of Contents
```typst
#show: template.with(
  show-toc: true,
  toc-depth: 3,  // Show up to level 3 headings
)

// TOC will be automatically generated
```

## Color Palette Reference

The template includes Merge Combinator brand colors:

- **Primary Blue**: `mc-primary` - Deep blue for headers
- **Secondary Blue**: `mc-secondary` - Bright blue for accents  
- **Accent Green**: `mc-accent` - Green for highlights
- **Text Gray**: `mc-gray` - Professional gray for body text

Usage in content:
```typst
#text(fill: mc-primary)[Important text in brand color]
```

## Best Practices

### Document Structure
1. Start with clear executive summary
2. Use consistent heading hierarchy
3. Include page breaks between major sections
4. Use tables and figures for data presentation

### Content Guidelines
1. Keep paragraphs concise (3-5 sentences)
2. Use bullet points for lists of 3+ items
3. Include figure captions for all images
4. Number all tables and figures

### Version Control
1. Update version number for significant changes
2. Use status field to indicate document stage
3. Include date for time-sensitive documents
4. Mark confidential documents appropriately

## Troubleshooting

### Common Issues

**Logo not displaying:**
- Ensure `arrows.png` is in `src/` directory
- Check file path in template parameters

**Incorrect formatting:**
- Run `just test` to validate template
- Check for syntax errors in Typst code

**Package not found:**
- Run `just install` to install locally
- Verify package name in import statement

## Examples Repository

Find complete examples in `template/` directory:
- `main.typ` - Basic usage example
- `report.typ` - Full report example
- `proposal.typ` - Business proposal example
- `memo.typ` - Internal memo example

## Support

For issues or questions:
- Check documentation in `docs/manual.typ`
- Review test cases in `tests/` directory
- Consult Typst documentation at https://typst.app/docs