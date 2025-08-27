# Merge Combinator Template Rebranding Plan

## Project Overview
Transform the existing MDPI academic journal template into a professional corporate document template for Merge Combinator, LLC.

## Current State Analysis

### Existing Assets
- **Template System**: Well-structured Typst package based on MDPI journal format
- **Logo Available**: `arrows.png` (1322x904) - Merge Combinator logo
- **Font System**: TeX Gyre Pagella (professional serif font)
- **Layout Engine**: Flexible Typst template with parameterized configuration

### Items Requiring Modification
1. Package identity (name, description, metadata)
2. Visual branding (logos, colors, typography)
3. Layout structure (from academic to corporate)
4. Default content and examples
5. Documentation and README

## Rebranding Implementation Plan

### Phase 1: Asset Migration and Setup
**Timeline**: Immediate
**Priority**: High

#### Tasks:
- [ ] Move `arrows.png` to `src/` directory for template access
- [ ] Remove MDPI logos (`ijms.png`, `mdpi.svg`)
- [ ] Create logo variants if needed (header version, watermark)

#### File Operations:
```bash
mv arrows.png src/arrows.png
rm src/ijms.png src/mdpi.svg
```

### Phase 2: Package Identity Update
**Timeline**: Day 1
**Priority**: High

#### Update `typst.toml`:
```toml
[package]
name = "merge-combinator"
version = "0.2.0"
entrypoint = "src/lib.typ"
authors = ["Merge Combinator, LLC"]
license = "MIT"
description = "Professional corporate document template for Merge Combinator"
repository = "https://github.com/merge-combinator/typst-template"
keywords = ["template", "corporate", "business", "professional", "merge-combinator"]
```

### Phase 3: Template Styling Modification
**Timeline**: Day 1-2
**Priority**: High

#### Key Changes in `src/impl.typ`:

1. **Logo Integration**:
```typst
// Replace line 17
venue: image("arrows.png", height: 1.5cm),

// Remove or repurpose line 20 (publisher logo)
```

2. **Color Scheme**:
```typst
// Define Merge Combinator colors
#let mc-primary = rgb("#1E3A8A")    // Deep blue
#let mc-secondary = rgb("#3B82F6")  // Bright blue
#let mc-accent = rgb("#10B981")     // Green for highlights
#let mc-gray = rgb("#6B7280")       // Professional gray
```

3. **Layout Adjustments**:
- Header: Company logo + document title
- Footer: Page numbers + confidentiality notice (optional)
- Body: Flexible single or multi-column layout
- Sidebar: Optional for navigation or highlights

4. **Typography Updates**:
```typst
// Professional font stack
set text(font: ("TeX Gyre Pagella", "Georgia", "serif"), size: 11pt)

// Heading hierarchy
show heading.where(level: 1): set text(size: 24pt, fill: mc-primary)
show heading.where(level: 2): set text(size: 18pt, fill: mc-secondary)
show heading.where(level: 3): set text(size: 14pt, weight: "semibold")
```

### Phase 4: Template Parameters Restructuring
**Timeline**: Day 2
**Priority**: High

#### New Template Parameters:
```typst
#let template(
  // Document metadata
  title: "Document Title",
  subtitle: none,
  document-type: "Report",  // Report, Proposal, Brief, Memo
  
  // Author/Team information
  author: "Author Name",
  department: "Department",
  email: none,
  
  // Document control
  date: datetime.today(),
  version: "1.0",
  status: "Draft",  // Draft, Review, Final
  confidential: false,
  
  // Branding
  logo: image("arrows.png", height: 1.5cm),
  company: "Merge Combinator, LLC",
  
  // Layout options
  columns: 1,  // 1 or 2 column layout
  show-toc: false,  // Table of contents
  
  body
) = {
  // Implementation
}
```

### Phase 5: Example Document Creation
**Timeline**: Day 2-3
**Priority**: Medium

#### Update `template/main.typ`:
```typst
#import "@preview/merge-combinator:0.2.0": template

#show: template.with(
  title: "Strategic Technology Integration",
  subtitle: "Q4 2024 Planning Document",
  document-type: "Report",
  author: "Jane Smith",
  department: "Technology Strategy",
  email: "j.smith@mergecombinator.com",
  date: datetime.today(),
  version: "2.1",
  status: "Final",
  columns: 1,
  show-toc: true,
)

= Executive Summary

This document outlines our strategic approach to technology integration...

= Introduction

Merge Combinator specializes in bringing together disparate technology systems...

== Background

Our methodology focuses on...

= Proposed Solution

...
```

### Phase 6: Documentation Update
**Timeline**: Day 3
**Priority**: Medium

#### Files to Update:
1. **README.md**: Complete rewrite for Merge Combinator
2. **docs/manual.typ**: Update usage guide
3. **LICENSE**: Verify licensing terms

### Phase 7: Testing and Refinement
**Timeline**: Day 3-4
**Priority**: High

#### Test Cases:
1. Single-page memo
2. Multi-page report with TOC
3. Technical proposal with code blocks
4. Executive brief with charts
5. Two-column newsletter format

#### Commands:
```bash
just test
just doc
just install
# Test with various document types
```

## Design Specifications

### Visual Identity
- **Primary Logo**: arrows.png (positioned in header)
- **Color Palette**:
  - Primary: Deep Blue (#1E3A8A)
  - Secondary: Bright Blue (#3B82F6)
  - Accent: Green (#10B981)
  - Text: Dark Gray (#111827)
  - Background: White (#FFFFFF)

### Typography
- **Headers**: Sans-serif for modern look (optional)
- **Body**: TeX Gyre Pagella (serif) for readability
- **Code**: Monospace font for technical content

### Layout Principles
- Clean, professional appearance
- Ample whitespace for readability
- Consistent margins and spacing
- Flexible column options
- Professional header/footer

## Success Criteria
- [ ] Template installs without errors
- [ ] Logo displays correctly in header
- [ ] All test documents render properly
- [ ] Typography is consistent and professional
- [ ] Color scheme applied throughout
- [ ] Examples demonstrate various use cases
- [ ] Documentation is complete and accurate

## File Structure After Rebranding
```
merge_template/
├── src/
│   ├── lib.typ
│   ├── impl.typ (modified)
│   └── arrows.png (moved here)
├── template/
│   └── main.typ (updated examples)
├── docs/
│   └── manual.typ (updated guide)
├── _docs/
│   ├── merge-combinator-rebrand-plan.md (this file)
│   └── template-usage-guide.md (to be created)
├── typst.toml (updated metadata)
└── README.md (rewritten)
```

## Risk Mitigation
- **Backup**: Create git branch before major changes
- **Testing**: Run tests after each phase
- **Rollback**: Keep original files until rebrand is complete
- **Documentation**: Document all changes for future reference

## Next Steps
1. Review and approve this plan
2. Create feature branch for rebranding
3. Execute phases in sequence
4. Test thoroughly
5. Merge to main branch
6. Tag release v0.2.0