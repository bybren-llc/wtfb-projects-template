# Marketing Directory

This directory contains everything needed to market your project through the WTFB platform and GitHub Pages.

## Directory Structure

```
marketing/
├── wtfb-marketing.json    # Platform integration configuration
├── assets/                # Visual marketing assets
│   ├── poster.png         # Movie poster / book cover
│   ├── banner.png         # Wide banner (1200x630)
│   └── social/            # Social media cards
│       ├── twitter-card.png
│       └── og-image.png
└── pages/                 # GitHub Pages content
    ├── _config.yml        # Jekyll configuration
    └── index.md           # Landing page template
```

## wtfb-marketing.json

This is the central configuration file that integrates your project with the WTFB platform. It controls:

### Project Identity
```json
{
  "project": {
    "id": "your-project-slug",
    "title": "Your Project Title",
    "subtitle": "A Short Film",
    "logline": "One sentence pitch",
    "type": "screenplay|novel|film-production",
    "status": "development|pre-production|production|completed",
    "year": 2026
  }
}
```

### Metadata
Genres, themes, keywords, runtime, rating, language, and setting. Used for discovery and categorization on the WTFB platform.

### Creators
Primary creator and contributors with WTFB user IDs for platform linking and payment routing.

### Marketing Assets
References to poster, banner, and social card images. These are used by:
- GitHub Pages for your project site
- WTFB platform for discovery pages
- Social sharing previews (OpenGraph, Twitter Cards)

### Platform Settings
```json
{
  "platform": {
    "visibility": "private|public",
    "featured": false,
    "allowFunding": true,
    "allowInquiries": true,
    "contactEmail": "you@example.com"
  }
}
```

### Commerce
Enable digital downloads, merchandise, and services:

```json
{
  "commerce": {
    "enabled": true,
    "stripeAccountId": "acct_xxx",
    "products": [
      {
        "id": "screenplay-pdf",
        "type": "digital",
        "name": "Screenplay PDF",
        "price": 0,
        "access": "free-download"
      },
      {
        "id": "tshirt",
        "type": "merch",
        "name": "Official T-Shirt",
        "price": 2500,
        "fulfillment": "printful"
      }
    ]
  }
}
```

### Analytics
PostHog integration for tracking page views, downloads, and conversions:

```json
{
  "analytics": {
    "posthogProjectId": "phc_xxx",
    "trackingEvents": [
      "page_view",
      "screenplay_download",
      "funding_inquiry"
    ]
  }
}
```

### Funding
Crowdfunding tiers for project financing:

```json
{
  "funding": {
    "enabled": true,
    "goal": 50000,
    "tiers": [
      {"id": "supporter", "amount": 25, "description": "Digital thanks"},
      {"id": "producer", "amount": 1000, "description": "Producer credit"}
    ]
  }
}
```

### Rights
Ownership and licensing information:

```json
{
  "rights": {
    "ownership": "creator",
    "registrations": [{"type": "WGA", "number": "123456"}],
    "licensing": {
      "optionAvailable": true,
      "purchaseAvailable": true
    }
  }
}
```

## Assets Directory

### Required Assets

| Asset | Dimensions | Purpose |
|-------|------------|---------|
| `poster.png` | 800x1200 | Movie poster, book cover |
| `banner.png` | 1200x630 | Header images, social sharing |
| `social/twitter-card.png` | 1200x600 | Twitter card image |
| `social/og-image.png` | 1200x630 | Facebook/OpenGraph image |

### Asset Guidelines

- Use PNG or WebP format for quality
- Keep file sizes under 500KB for fast loading
- Include project title in images for social sharing
- Maintain consistent visual branding

## Pages Directory

GitHub Pages content for your project's marketing site.

### How It Works

1. The `deploy-pages.yml` workflow triggers on changes to `marketing/`
2. It reads `wtfb-marketing.json` and generates a static site
3. The site deploys to `https://[username].github.io/[project-name]`

### Customization

Edit `pages/_config.yml` for Jekyll settings:
- Site title and description
- Theme selection
- Build settings

Edit `pages/index.md` for custom landing page content.

## Integration with WTFB Platform

When you register your project on wordstofilmby.com:

1. **Sync**: WTFB reads your `wtfb-marketing.json` via GitHub API
2. **Display**: Your project appears in the WTFB discovery catalog
3. **Commerce**: Products are synced to WTFB's Stripe integration
4. **Analytics**: Events flow to your PostHog project
5. **Payments**: Revenue routes to your connected Stripe account

## Workflow

1. **Configure**: Fill out `wtfb-marketing.json` with your project details
2. **Create Assets**: Add poster, banner, and social card images
3. **Enable Pages**: Go to repo Settings > Pages > Enable GitHub Pages
4. **Register**: Connect your repo to wordstofilmby.com
5. **Promote**: Share your GitHub Pages URL for marketing

## Validation

The CI/CD pipeline validates your marketing config:

```bash
# Validates JSON syntax
jq empty marketing/wtfb-marketing.json

# Full schema validation (when registered with WTFB)
# WTFB platform validates against https://wtfb.io/schemas/wtfb-marketing.v1.json
```
