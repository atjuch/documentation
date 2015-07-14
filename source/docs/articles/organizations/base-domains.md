---
title: Customizing Your Base Domain
description: Replace "pantheon.io" within Pantheon environments by adding a custom development domain.
category:
  - managing
keywords: development domain, base domain, change dev url, change development domain, change base domain, dev url, wildcard, cname, edge, dns
---
Pantheon Partners, Strategic Partners, Enterprise accounts, Resellers, and OEM Partners have the ability to replace pantheon.io as the base domain for each environment on every site they run or are developing on the platform.

The base development domain should be a subdomain of your marketing site, such as sites.awesomeagency.com. A newly created site named "supersite" will then have a development environment urls of dev-supersite.sites.example.com.  


## Request the Base Domain

From your Organization Dashboard, go to Support and open a ticket. Select **Pantheon One** as the ticket type, check **non site-related issue**, and use "Custom Base Domain for <Agency Name>" as the subject. The body of the ticket must state the base domain required on the site, like sites.example.com.

## Create a Wildcard CNAME Record

The only action required on your end is creating a Wildcard CNAME DNS entry for the development domain you choose, at your DNS hosting service, pointing to our edge. If you go with sites.example.com, the record would need to be created as follows:

*.sites.example.com CNAME edge.live.getpantheon.com

## Effects and Considerations

Sites associated with your organization will receive the appropriate base URL for all environments created while the organization remains a supporting organization. Multidev environments will also receive the URL. If the supporting organization is removed from the team, new environments will receive URL's following the default .pantheon.io pattern. This includes new Multidev environments and Test and Live environments created **after** the organization was removed.

Environment URLs are permanent. If an organization is removed as the supporting organization, any environment created during its association will keep the original URL after removal. Paid sites can add custom URL's to any environment, as a workaround for those wishing to use different URL's after launch and disassociation of the site with the organization.

## Robots.txt with Custom Base Domains

For SEO and to prevent duplicate content, the robots.txt file attached to the custom base domain will contain the following by default:

```
# http://live-sitename.agencyname.com/robots.txt
User-agent: *
Disallow: /
```
To present an alternate robots.txt file from within the source code, a custom domain needs to be [added to the site's Dashboard](/docs/articles/sites/domains#step-2-add-a-domain-to-a-site-environment) and the appropriate DNS record created.
