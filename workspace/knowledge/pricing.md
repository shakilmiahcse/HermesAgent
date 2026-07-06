# Pricing Logic & Verification Rules

This file governs pricing data retrieval. Do NOT store hardcoded prices in the knowledge base, as prices are dynamic and subject to updates or seasonal promotions.

## Retrieval Directives
1. **Never guess or estimate pricing**: If asked for course fees or mock costs, search the active database or retrieve page details from https://fluento.org/pricing or product listings.
2. **Consult CRM Catalog**: Always check system database listings first, as prices vary based on special promotional codes or packages.

## Fallback Actions
If pricing queries fail (e.g. database offline or no internet connection), reply exactly as follows:
- *"pricing details are currently unavailable or undergoing update checks. Please visit the official website or connect directly with our admissions officer on WhatsApp at +880 1979-756067 for active batch prices."*

## Dynamic Promotions Rule
- Discount and coupon campaigns (e.g., "50% Eid Discount", "Today's Offer") are strictly dynamic. Do not retain them in static memory files. Query the API or configuration parameters.
