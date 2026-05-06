# Standards & API Reference

> Project: Returns & Reverse Logistics · Generated: 2026-05-03

## Industry Standards & Specifications

### ISO Standards

**ISO/IEC 19987 — EPCIS (Electronic Product Code Information Services)**
- URL: https://www.gs1.org/standards/epcis
- The formal ISO standardisation of GS1's EPCIS 2.0 standard for event-based supply chain visibility. Provides the core data model for tracking "what, when, where, why, and how" events across a product's lifecycle, including return and disposition events. The companion ISO/IEC 19988 covers the Core Business Vocabulary (CBV), which defines standardised disposition values (e.g. `in_progress`, `recalled`, `destroyed`, `sellable_accessible`) used to categorise returned inventory states.

**ISO 14001:2015 — Environmental Management Systems**
- URL: https://www.iso.org/standard/60857.html
- Specifies requirements for an environmental management system. Directly relevant to reverse logistics operations that must account for carbon-efficient collection routing, packaging recycling, and product end-of-life disposal. Returns platforms targeting sustainability-conscious retailers often need to demonstrate ISO 14001 alignment.

**ISO 28000:2022 — Security Management Systems for the Supply Chain**
- URL: https://www.dnv.com/services/iso-28000-2022-security-management-systems-4344/
- Specifies requirements for a security management system covering transportation, warehousing, and in-transit handling of goods — all present in reverse logistics networks. Aligns with ISO 9001, ISO 14001, and ISO/IEC 27001 via the Annex SL high-level structure for integrated management systems.

**ISO/IEC 27001 — Information Security Management**
- URL: https://www.iso.org/standard/27001
- Returns portals process sensitive consumer data (purchase history, payment details, addresses). ISO/IEC 27001 is the baseline information security standard required by enterprise retailers when evaluating returns management vendors. GDPR Article 32 technical safeguard obligations effectively require ISO 27001-level controls.

### GS1 Standards

**GS1 EPCIS 2.0 & CBV (Core Business Vocabulary)**
- URL: https://www.gs1.org/standards/epcis and https://ref.gs1.org/guidelines/epcis-cbv/
- The practical implementation layer above ISO/IEC 19987/19988. EPCIS 2.0 (released 2022) supports both XML and JSON-LD representations and introduces a REST/HTTP binding alongside the legacy SOAP interface. Defines the event types (ObjectEvent, AggregationEvent, TransactionEvent, TransformationEvent) needed to track returned items from customer drop-off through warehouse processing to restocking or disposal.

**GS1 GTIN (Global Trade Item Number)**
- URL: https://www.gs1.org/standards/id-keys/gtin
- The universal product identifier underpinning returns workflows. A returns management system must resolve GTINs to determine original product metadata, applicable return policies, and disposition routing rules. GS1 also defines GRAI (Global Returnable Asset Identifier) for tracking reusable transport equipment in reverse logistics networks.

**GS1 GLN (Global Location Number)**
- URL: https://www.gs1.org/standards/id-keys/gln
- Uniquely identifies physical locations (warehouses, return centres, retail stores, carrier hubs). Essential for routing return shipments to the correct processing facility and for EPCIS event location attributes.

### ANSI X12 EDI Standards

**EDI 180 — Return Merchandise Authorization and Notification**
- URL: https://www.truecommerce.com/edi-transaction-codes/edi-180/
- The ANSI X12 transaction set that formally defines the electronic data interchange format for RMA requests, authorisations, and disposition notifications between trading partners. Used extensively in B2B retail and supplier returns workflows. Supports four use cases: return request, authorisation/disposition, return notification, and consumer return notification.

**EDI 814 — General Request, Response or Confirmation**
- URL: https://x12.org/products/transaction-sets
- Used alongside EDI 180 in some trading partner relationships for general-purpose return status confirmations and acknowledgements. X12 also maintains standardised external code lists for return reason codes at https://x12.org/codes.

### W3C & IETF Standards

**RFC 6749 — The OAuth 2.0 Authorization Framework**
- URL: https://datatracker.ietf.org/doc/html/rfc6749
- The foundational authentication standard used by all major carrier APIs (FedEx, UPS, ShipStation, EasyPost) and returns platform APIs (AfterShip, Loop Returns). Any returns management platform integrating with carrier or merchant systems must implement OAuth 2.0 client credentials or authorisation code flows.

**OAuth 2.1 (draft-ietf-oauth-v2-1)**
- URL: https://datatracker.ietf.org/doc/html/draft-ietf-oauth-v2-1-10
- The consolidated successor to RFC 6749, removing implicit flow and other deprecated patterns. FedEx's REST API migration (deadline mid-2026) and other carrier modernisation efforts are targeting OAuth 2.1 compliance.

**RFC 7231 — HTTP/1.1 Semantics and Content**
- URL: https://datatracker.ietf.org/doc/html/rfc7231
- Governs the HTTP method semantics underlying all REST-based returns APIs. Correct use of POST (create return), GET (retrieve status), PATCH (update return items), DELETE (cancel return) must conform to RFC 7231 semantics.

### Data Model & API Specifications

**OpenAPI Specification 3.1**
- URL: https://spec.openapis.org/oas/v3.2.0.html and https://swagger.io/specification/
- The dominant API description standard. AfterShip Returns, Loop Returns, and ShipStation all publish or support OpenAPI Schema downloads for their returns APIs. OpenAPI 3.1 introduced full JSON Schema alignment and native webhook object support — both critical for returns platforms that push asynchronous status updates to merchant systems.

**JSON Schema (draft-07 / 2020-12)**
- URL: https://json-schema.org/
- The data validation layer used within OpenAPI specs and standalone webhook payload schemas. Returns events (return created, items received, refund issued, restocking decision) are typically defined as JSON Schema objects for validation and documentation.

**GS1 EANCOM / GS1 XML**
- URL: https://www.gs1.org/standards/edi
- EDI standards for retail supply chain data exchange. GS1 XML is the modern alternative to EANCOM for B2B returns communications, widely used among European grocery and FMCG retailers.

### Security & Compliance

**GDPR — General Data Protection Regulation (EU 2016/679)**
- URL: https://gdpr.eu/
- Returns portals collect and process consumer personal data (name, address, purchase history, refund payment details). GDPR mandates lawful basis for processing, data minimisation, right-to-erasure obligations, and breach notification within 72 hours. Especially relevant for platforms operating in or serving EU customers. Non-compliance risks fines up to €20 million or 4% of global turnover.

**OWASP API Security Top 10**
- URL: https://owasp.org/www-project-api-security/
- Returns management APIs expose sensitive order and customer data. OWASP API Security Top 10 (2023 edition) provides the baseline threat model for broken object-level authorisation (BOLA), broken authentication, excessive data exposure, and injection — all applicable to returns APIs handling RMA tokens and customer PII.

**EU WEEE Directive (Waste Electrical and Electronic Equipment)**
- URL: https://environment.ec.europa.eu/topics/waste-and-recycling/waste-electrical-and-electronic-equipment-weee_en
- Mandates producer take-back and recycling obligations for electronic returns across EU member states. Returns management platforms handling consumer electronics must support WEEE-compliant disposition routing (repair, refurbishment, certified recycling) and maintain audit records.

---

## Similar Products — Developer Documentation & APIs

### AfterShip Returns

- **Description:** Multi-carrier global returns management platform with a branded self-service portal, analytics, and carrier label generation. Supports 60+ carriers worldwide.
- **API Documentation:** https://www.aftership.com/docs/returns/quickstart/api-quick-start
- **API Overview:** https://www.aftership.com/docs/returns/929047a0ecf1b-api-overview
- **OpenAPI Schema:** Available for download from the AfterShip Docs portal (OAS file)
- **SDKs/Libraries:** JavaScript, Python, Ruby, PHP, Java (listed in AfterShip Docs)
- **Standards:** REST/JSON, OpenAPI 3.1, versioned quarterly (e.g. 2025-07, 2025-10)
- **Authentication:** API Key (Bearer token in Authorization header)
- **Key Endpoints:** Create Return, Approve Return, Reject Return, Resolve Return, Receive Items, Attach Shipments, Remove Return Items, Record Drop-off

### Loop Returns

- **Description:** Exchange-first returns automation platform, primarily for Shopify merchants. Focuses on retaining revenue through instant exchanges and store credit incentives.
- **API Documentation:** https://docs.loopreturns.com/api-reference/getting-started
- **Developer Docs Home:** https://www.docs.loopreturns.com/
- **SDKs/Libraries:** Webhook-based integration; REST API for return lifecycle management
- **Standards:** REST/JSON; webhook payloads for return creation and status changes
- **Authentication:** API Key scopes (read, write, admin — 401 returned on scope mismatch)
- **Key Capabilities:** Webhooks on return creation and status change; custom integrations for OMS/WMS synchronisation

### Happy Returns (UPS)

- **Description:** Label-free in-person return drop-off network (8,000+ Return Bar locations). Acquired by UPS. Targets US retailers seeking frictionless consumer return experiences.
- **API Documentation:** https://developer.happyreturns.com/partner/api/
- **Retailer Integration Guide:** https://developer.happyreturns.com/retailer-integration/
- **API Specification:** https://developer.happyreturns.com/retailer-integration/specification/
- **Standards:** REST/JSON
- **Authentication:** HTTP Header `X-Hr-Apikey` with value provided during onboarding
- **Key Capabilities:** Return initiation, QR code generation for label-free drop-off, return status webhooks

### FedEx Ship API (Returns)

- **Description:** FedEx's REST Ship API supports return label creation, email return shipments, and package pickup scheduling. Migrating from SOAP to REST (deadline mid-2026).
- **API Documentation:** https://developer.fedex.com/api/en-us/catalog/ship/docs.html
- **Developer Portal:** https://developer.fedex.com/api/en-us/home.html
- **Standards:** REST/JSON, OpenAPI
- **Authentication:** OAuth 2.0 (client credentials flow); tokens expire every 60 minutes
- **Key Capabilities:** Return label generation, email return shipment creation, Cancel Shipment (with `emailreturnshipment` boolean flag), scheduled pickup

### UPS Returns API

- **Description:** UPS Developer Portal provides return label generation, service point locator for drop-off, and return shipment tracking via REST APIs.
- **Developer Portal:** https://developer.ups.com/
- **REST API Documentation:** https://developer.ups.com/api/reference
- **SDK/Libraries:** Available via UPS Developer Portal (credentials required)
- **Standards:** REST/JSON, OAuth 2.0
- **Authentication:** OAuth 2.0 (Client ID + Client Secret via Developer Portal app registration)
- **Key Capabilities:** Return label creation, closest service point lookup, return shipment tracking

### ShipStation API (Returns & Labels)

- **Description:** Multi-carrier shipping and fulfilment platform with return label generation. V2 REST API added return labels as a first-class capability.
- **API Documentation:** https://docs.shipstation.com/
- **Return Labels Guide:** https://docs.shipstation.com/return-labels
- **OpenAPI Reference:** https://docs.shipstation.com/openapi/addresses
- **Standards:** REST/JSON, OpenAPI
- **Authentication:** Basic Auth (API Key + API Secret)
- **Key Capabilities:** Return label creation (POST /v2/labels with `return_label: true`), void labels, tracking retrieval

### EasyPost API (Returns & Refunds)

- **Description:** Multi-carrier shipping API supporting return label creation via `is_return: true` flag on Shipment objects. Offers refund processing for voided USPS labels.
- **API Documentation:** https://docs.easypost.com/
- **Return Labels Guide:** https://www.easypost.com/usps-return-labels
- **Refund Documentation:** https://docs.easypost.com/docs/shipments/shipping-refund
- **SDKs/Libraries:** Python, Node.js, Ruby, PHP, Java, C#, Go — https://docs.easypost.com/libraries
- **Standards:** REST/JSON; Basic Auth
- **Authentication:** API Key (test and production keys; Basic Auth with API key as username)
- **Key Capabilities:** Return shipment creation, carrier rate comparison for return routes, label refund processing, multi-carrier support

### Shopify Admin GraphQL API (Returns)

- **Description:** Shopify's primary API for returns management since 2024 (REST Admin API deprecated for new apps from April 2025). Full return lifecycle management including self-serve customer return requests.
- **API Documentation:** https://shopify.dev/docs/api/admin-graphql/latest/objects/Return
- **Build for Returns Guide:** https://shopify.dev/docs/apps/build/orders-fulfillment/returns-apps/build-return-management
- **Customer Accounts API:** https://shopify.dev/changelog/returns-now-supported-in-customer-accounts-api
- **SDKs/Libraries:** Shopify API JS library; official Admin API clients in Ruby, Python, PHP, Go
- **Standards:** GraphQL; versioned quarterly (e.g. 2025-07 introduced Returns Processing APIs)
- **Authentication:** OAuth 2.0 (app installation flow); Admin API access tokens
- **Key Capabilities:** Return object creation, return line items, refund issuance, exchange creation, customer self-serve return requests via Customer Accounts API

### Narvar Returns API

- **Description:** Post-purchase platform covering order tracking, proactive notifications, and returns. Used by large retailers for branded post-purchase journeys.
- **API Tracker Reference:** https://apitracker.io/a/narvar
- **Integration Guide:** https://support.narvar.com/hc/en-us/articles/360052681514-Integration-Guide
- **Webhook Spec (RMA):** https://speca.io/Narvar/narvar-returns-webhook
- **Standards:** REST/JSON; webhook-based return status notifications
- **Authentication:** API key (header-based)
- **Key Capabilities:** Return initiation, refund method capture (original payment or gift card), branded return portal, post-return communication triggers

### ReverseLogix Platform API

- **Description:** Purpose-built SaaS returns management system for retailers and 3PLs. Open API-first design for integration with OMS, WMS, TMS, and ERP systems.
- **Integration Overview:** https://www.reverselogix.com/returns-management/smarter-business/platform-integrations/
- **Pandium Connector Docs:** https://docs.pandium.com/connectors/connectors-101/reverselogix
- **Standards:** REST/JSON (API-first design); integrates via out-of-the-box connectors to major platforms
- **Authentication:** API key (details via vendor onboarding)
- **Key Integrations:** Shopify, Salesforce, SAP Commerce Cloud, Oracle Cloud, NetSuite, Magento, Blue Yonder WMS, Manhattan SCALE, FedEx Ship Manager

---

## Notes

**Emerging Standards:**
- GS1 is transitioning the industry from 1D barcodes (UPC/EAN) to 2D QR codes ("Sunrise 2027" initiative). Dynamic QR codes can encode return instructions post-sale, linking scan events directly into EPCIS return flows. Returns management platforms should anticipate this as a primary item-identification mechanism for consumer returns by 2027–2028.
- The MCP (Model Context Protocol) is not yet established in the returns management or logistics domain. AI-native returns platforms may pioneer MCP server definitions for return reason classification, disposition recommendation, and restocking intelligence tools.

**Data Standardisation Gaps:**
- There is no universal standard for return condition grading codes across the industry (e.g. "Like New", "Good", "Fair", "Damaged"). Each platform defines its own taxonomy. An AI-native platform has an opportunity to propose or adopt an open grading vocabulary (potentially extending GS1 CBV disposition codes).
- Return reason codes are partially standardised via ANSI X12 EDI 180 for B2B trading partners, but consumer-facing reason taxonomies remain vendor-specific. Standardisation here would unlock cross-platform analytics.
