# AceWork Platform Overview and Purpose Statement for Allegro Advertising Data Integration

*Application Registration Supporting Document*

**Submitted to:** Allegro Developer Portal Application Review Team

**Prepared by:** Technology Department · Cross-Border E-Commerce Engineering Team

**Document version:** v1.0

---

## Table of Contents

- Executive Summary
- 1. Purpose and Scope of This Document
  - 1.1 Purpose
  - 1.2 Scope
  - 1.3 Terminology
- 2. AceWork Platform Overview
  - 2.1 Platform Positioning
  - 2.2 Intended Users
  - 2.3 Deployment and Data Ownership
- 3. Core Functional Modules of AceWork
  - 3.1 Multi-Platform Store Data Aggregation
  - 3.2 Operational Metrics Dashboard
  - 3.3 Advertising Performance Analysis
  - 3.4 Product and Selection Analysis
  - 3.5 Reporting and Scheduled Delivery
  - 3.6 Natural-Language Query (Insight Q&A)
  - 3.7 Connector Center
- 4. Why We Need to Integrate Allegro Advertising Data
  - 4.1 Business Context
  - 4.2 Current Pain Points
  - 4.3 Business Value After Integration
- 5. Analytics Scenarios in Detail
  - 5.1 Base Analysis Dimensions
  - 5.2 Advertising Metrics
  - 5.3 Aggregation and Comparison
  - 5.4 Correlation with Store-Level Daily Sales Data
  - 5.5 Derived Metrics
  - 5.6 Overall Analytical Capabilities
  - 5.7 Output Formats
- 6. Data Flow and Security Boundaries
  - 6.1 Data Flow
  - 6.2 Developer Credential Management
  - 6.3 Authorization Method
  - 6.4 Access Control
  - 6.5 Requested Permission Scope
- 7. Compliance and Declaration
- 8. Key Terminology Mapping
- Appendix A: Application Information at a Glance

---

# Executive Summary

AceWork is our company's internal operations analytics platform, built and operated exclusively for our own cross-border e-commerce business. It is not a commercial SaaS product, it is not offered to external customers, and it does not act as an intermediary between Allegro and any third party.

The application described in this submission is a read-only data connector that we register for our own Allegro seller account. Its sole purpose is to bring our own Allegro advertising performance data — impressions, clicks, CTR, average CPC, ad spend, interest, units sold, sales value and ROAS — into our internal analytics platform, so that our own business teams can analyse advertising effectiveness alongside our own order and sales data.

We register this application under our own credentials only. Our Client ID and Client Secret are held by our own technical staff inside our own server configuration. They are never distributed, displayed, or shared with any third party, external customer, or end user. End users of the platform are never asked to provide their own Allegro credentials.

Access requested is read-only: profile:read, sale:offers:read, orders:read. The application does not create, edit, or delete offers, orders, or sale settings.

# 1. Purpose and Scope of This Document

## 1.1 Purpose

This document accompanies our company's application registration submission to the Allegro Developer Portal. It sets out three matters for the review team: first, what the AceWork platform is, whom it serves, and which business functions it performs; second, why the company needs to obtain Allegro advertising performance data through the API; and third, the boundaries, security measures, and compliance commitments that apply to this data integration.

## 1.2 Scope

The application described in this submission is used solely to connect our company's own Allegro seller account and to support internal management analysis. It does not involve any third-party seller account and does not provide services to external parties.

## 1.3 Terminology

**Table 1. Terminology**

| Term | Meaning |
|---|---|
| AceWork | The company's internally developed cross-border e-commerce operations analytics platform; an internal system |
| Connector | A standardized data integration module within AceWork used to connect to external e-commerce platforms |
| Advertising Data | Performance data for Sponsored Offers and graphic and video advertising under the Allegro Ads system |
| Organic Sales | Sales not generated through advertising channels, i.e. total store sales less advertising-attributed sales |

# 2. AceWork Platform Overview

## 2.1 Platform Positioning

AceWork is an internally developed, self-operated operations analytics platform that serves as the data hub for the company's cross-border e-commerce business. The platform consolidates operational data from the company's own store accounts across multiple e-commerce platforms (including Allegro, Amazon, and other marketplaces), standardizes it into comparable and traceable business metrics, and supports day-to-day operational decision-making on the business side.

The platform has three defining characteristics:

| Attribute | Description |
|---|---|
| Internal | Accessible only from the company intranet and authorized office devices; not open for public registration and not sold to external customers |
| Self-use | All data originates from the company's own store accounts; data ownership and usage rights rest entirely with the company |
| Analytical | The platform's core function is data aggregation, processing, comparison, and presentation. It is not an ordering system, not a listing system, and not a payment system |

## 2.2 Intended Users

**Table 2. Platform Users and Typical Use Cases**

| Role | Typical Use Case |
|---|---|
| Advertising Operations | Monitor advertising performance and adjust budgets and bidding strategies |
| Category Operations | Analyse advertising contribution and sales structure at the product level |
| Business Analysis | Prepare weekly and monthly business reports and identify operational anomalies |
| Management | Review overall business dashboards and assess advertising return on investment |

All of these roles are internal company employees who sign in through the company's unified account system. There are no external users.

## 2.3 Deployment and Data Ownership

The platform is deployed on company-owned servers, and both the database and file storage are company-owned resources. All aggregated data is stored in company-owned storage and is not transmitted back to any external organization, service provider, or third-party platform.

# 3. Core Functional Modules of AceWork

## 3.1 Multi-Platform Store Data Aggregation

Through standardized connector modules, operational data from the company's own store accounts on each e-commerce platform is brought into the platform in a unified manner. Connectors establish and maintain the authorized connection to each platform, pull incremental data on a defined schedule, perform standardized field mapping, and record the execution status and exceptions of each synchronization run to support operational troubleshooting.

## 3.2 Operational Metrics Dashboard

Presents core operational metrics — including sales revenue, units sold, average order value, gross margin, and return rate — by store, marketplace, category, and product, with support for switching between daily, weekly, and monthly time granularities and for trend comparison.

## 3.3 Advertising Performance Analysis

Performs multi-dimensional performance evaluation of advertising data. This is one of the platform's core analysis modules and the direct business driver behind this request for Allegro advertising data integration. Its capabilities are detailed in Chapter 5.

## 3.4 Product and Selection Analysis

Combines traffic, conversion, and advertising performance at the product level to help identify high-potential products, inefficiently advertised products, and products requiring optimization, providing a basis for product selection and inventory decisions.

## 3.5 Reporting and Scheduled Delivery

Generates reports from detail data and weekly and monthly aggregate data on a configured schedule, and delivers them to the relevant business roles through internal company channels. Reports can be exported to common spreadsheet formats for further offline analysis.

## 3.6 Natural-Language Query (Insight Q&A)

The platform provides a natural-language query interface through which business users can ask questions directly (for example, "Which advertising campaign had the lowest ROAS last week?"). The platform translates the question into a query against data already aggregated within the platform and returns the result.

> This capability operates solely on data already aggregated within the platform. It does not directly access any external platform API, and it does not hold, transmit, or otherwise come into contact with any developer credentials. It is an internal data-consumption mechanism of the platform and is fully isolated from the API credentials requested in this application.

## 3.7 Connector Center

An administrative interface for operations staff, used to configure platform connectors, review authorization status, and manage synchronization tasks. The developer's Client ID and Client Secret are maintained only in the server-side configuration of this module. The interface never displays the full secret — it is shown only in masked form — and access is restricted to company technical staff.

# 4. Why We Need to Integrate Allegro Advertising Data

## 4.1 Business Context

Allegro is one of the company's core sales channels in the Central and Eastern European market, covering four marketplaces: Poland, Czechia, Slovakia, and Hungary. As advertising spend has grown, it has become a significant component of operating costs, and advertising efficiency now directly affects overall profitability.

## 4.2 Current Pain Points

Advertising data is currently obtained manually: business staff filter by date range and metrics in the Allegro Ads back office, export a spreadsheet, and then compile it by hand into analysis workbooks. This approach has three serious problems:

| Pain Point | Details |
|---|---|
| Low efficiency | Repeated exports across multiple marketplaces, campaigns, and periods consume substantial manual effort |
| Error-prone reconciliation | Manual compilation readily produces inconsistent definitions, undermining the reliability of conclusions |
| No correlation | Advertising data and store sales data sit in separate reports, making it difficult to automatically separate advertising from organic sales — and that separation is precisely what determines the true value of advertising |

## 4.3 Business Value After Integration

Bringing advertising data into the platform through the API delivers the following value:

1. Advertising metrics and store sales data are automatically correlated under a single set of definitions, enabling precise separation of advertising and organic sales.
2. Daily, weekly, and monthly aggregation and period-over-period calculation are automated, replacing manual consolidation.
3. A long-term, traceable advertising data archive is established to support trend assessment and period comparison.
4. Anomaly detection and hierarchical drill-down move problem localization from "an overall change" to "a specific campaign, ad group, or product."

# 5. Analytics Scenarios in Detail

The platform provides seven layers of analytical capability around advertising data, forming a complete analytical loop.

## 5.1 Base Analysis Dimensions

**Table 3. Base Analysis Dimensions**

| Dimension | Description |
|---|---|
| Marketplace | Reported separately for the four marketplaces: Poland, Czechia, Slovakia, and Hungary |
| Date | Calendar-day granularity |
| Week | Calendar-week granularity |
| Month | Calendar-month granularity |
| Campaign | The highest level of the advertising hierarchy |
| Ad Group | The grouping unit within a campaign |
| Offer (Product) | The specific advertised product within an ad group |
| Ad Type | Differentiation by type, such as Sponsored Offers and graphic and video advertising |

## 5.2 Advertising Metrics

**Table 4. Advertising Metric Set**

| Metric | Description |
|---|---|
| Impressions (Views) | Number of times the ad was displayed |
| Clicks | Number of times the ad was clicked |
| CTR | Click-through rate, i.e. clicks divided by impressions |
| Average CPC | Average cost per click |
| Ad Spend (Cost) | Total cost incurred by advertising |
| Interest | Number of purchase-intent expressions generated by ad exposure |
| Units Sold (Sold) | Number of units sold attributed to advertising |
| Sales Value | Sales amount attributed to advertising |
| ROAS | Return on ad spend, i.e. advertising sales value divided by ad spend |

## 5.3 Aggregation and Comparison

The platform supports aggregation at three granularities — daily, weekly, and monthly — and automatically calculates the following comparisons:

| Comparison | Description |
|---|---|
| Period-over-period | Change versus the immediately preceding period |
| Year-over-year | Change versus the same period of the previous year |
| Magnitude of change | Change expressed both as a percentage and as an absolute value |

Note: The API's historical data is available only over a limited lookback window. Full year-over-year capability requires twelve months of accumulated archiving within the platform; the initial phase will focus on period-over-period comparison and weekly and monthly aggregation.

## 5.4 Correlation with Store-Level Daily Sales Data

Advertising data is correlated with store operational data under the same date definitions, producing the following comparison metrics:

| Metric | Description |
|---|---|
| Total Store Units Sold | Total units sold in the period |
| Total Store Sales | Total sales amount in the period |
| Organic Units Sold | Total store units sold less advertising-attributed units |
| Organic Sales | Total store sales less advertising-attributed sales |

## 5.5 Derived Metrics

Calculated on top of the base metrics, these derived metrics are used to assess the structural impact of advertising:

| Derived Metric | Description |
|---|---|
| Advertising Sales Share | Advertising sales as a proportion of total store sales |
| Organic Sales Share | Organic sales as a proportion of total store sales |
| Advertising Incrementality Assessment | Assessed alongside trends in organic sales, to determine whether advertising spend is generating incremental sales or mainly displacing organic sales |

## 5.6 Overall Analytical Capabilities

**Table 5. Overall Analytical Capabilities**

| Capability | Description |
|---|---|
| Periodic volatility and anomaly detection | Detects and flags abnormal fluctuations in sales, spend, ROAS, and other metrics |
| Advertising cannibalization diagnosis | Compares advertising sales growth against changes in organic sales to determine whether advertising is substituting for organic sales |
| Ad ROAS evaluation | Evaluates return on spend by campaign, ad group, and product to identify efficient and inefficient advertising |
| Advertising hierarchy drill-down | Supports progressive expansion from campaign down to ad group and individual product to localize the issue |

## 5.7 Output Formats

| Output Type | Description |
|---|---|
| Detail data | Complete data at base-dimension granularity, exportable |
| Weekly and monthly aggregates | Aggregated results by week and by month |
| Trend charts | Time-series visualization of key metrics |
| Diagnostic recommendations | Optimization guidance generated from the analysis results |

# 6. Data Flow and Security Boundaries

## 6.1 Data Flow

The entire data path can be summarized as the following unidirectional process, in which data does not flow from the company to any external party:

| Stage | Party | Description |
|---|---|---|
| Data source | Company's own Allegro seller account | User-initiated authorization, read-only scope |
| Data retrieval | AceWork Connector | Runs on company-owned servers |
| Data storage | AceWork internal database | Company-owned storage |
| Data processing | Analytics engine | Processing, aggregation, correlation |
| Data consumption | Internal dashboards, reports, insight Q&A | Accessible only to internal company employees |
| End users | Internal business staff | No external users |

## 6.2 Developer Credential Management

Regarding the Client ID and Client Secret issued for this application, the company states the following:

| No. | Requirement |
|---|---|
| 1 | The credentials are held solely by company technical staff in the platform's server-side encrypted configuration |
| 2 | The credentials are used solely for this application's authorization requests to Allegro and for no other purpose |
| 3 | The credentials are not distributed, displayed, or shared with any third party, external customer, or end user of the platform |
| 4 | The credentials are shown in masked form in the administrative interface; the full value is accessible only to a very small number of technical staff in operational scenarios |
| 5 | The platform neither requires nor accepts end users submitting their own Client ID and Client Secret |

## 6.3 Authorization Method

The application uses the standard OAuth authorization flow. An authorized company representative completes a one-time authorization confirmation using the company's own Allegro account, with the granted scope strictly limited to the read-only permissions declared at registration. The access token is securely stored and automatically refreshed on the server side. Business users do not come into contact with any credential information when using the analytics features.

## 6.4 Access Control

| Control | Measure |
|---|---|
| Platform access | Restricted to the company intranet and authorized office devices; unified account sign-in |
| Data access | Data permissions assigned by role; business users can see only the data within the scope of their responsibilities |
| Audit | Key operations are logged to support after-the-fact traceability |
| Permission scope | API permissions are limited to read-only; the application cannot modify any store data |

## 6.5 Requested Permission Scope

This application requests only the following read-only permissions:

**Table 6. Requested Permissions (Read-Only)**

| Permission | Purpose |
|---|---|
| allegro:api:profile:read | Verify authorization status and read basic account information |
| allegro:api:sale:offers:read | Read product data for product-level correlation of advertising data |
| allegro:api:orders:read | Read order and sales data for correlation with advertising data |

> This application does not request any write permissions and cannot create, modify, or delete offers, orders, or store settings.

# 7. Compliance and Declaration

The company hereby declares that:

| No. | Declaration |
|---|---|
| 1 | This application is an internal, self-use data analytics tool. It does not provide services to external customers and does not act as an intermediary. |
| 2 | The application connects only to the company's own Allegro seller account and does not involve any third-party seller account. |
| 3 | The Client ID and Client Secret are held by the company itself and will never be shared with any third party or end user. |
| 4 | Data obtained through the API is used solely for the company's internal business analysis. It is neither resold nor disclosed externally. |
| 5 | The permissions requested by the application are strictly limited to read-only; the application does not perform any operation that modifies store data. |
| 6 | The company will continue to comply with the Allegro REST API terms of use and security rules. |

# 8. Key Terminology Mapping

For ease of cross-checking by the review team, the following table maps the concepts used in this document to their corresponding Allegro platform terms:

**Table 7. Terminology Mapping to Allegro Platform Terms**

| Concept | Allegro Platform Term |
|---|---|
| Advertising campaign | Campaign |
| Ad group | Ad Group |
| Product listing | Offer |
| Impressions | Views |
| Clicks | Clicks |
| Click-through rate | CTR |
| Average cost per click | Average CPC |
| Ad spend | Cost |
| Interest | Interest |
| Units sold (attributed) | Sold |
| Sales value (attributed) | Sales Value |
| Return on ad spend | ROAS |
| Sponsored offers advertising | Sponsored Offers |
| Graphic and video advertising | Graphic and video advertising |

# Appendix A: Application Information at a Glance

**Table 8. Application Information**

| Item | Detail |
|---|---|
| Application name | AceWork Allegro MCP Connector |
| Application type | Internal data integration application (server-side) |
| Purpose | Internal company use; internal operations analysis |
| Target account | Company's own Allegro seller account |
| Permission scope | Read-only (profile:read, sale:offers:read, orders:read) |
| Data destination | Company-owned servers and database; no external transmission |
| Intended users | Internal company business staff |
| Commercial use | None (no external service, no resale) |

This document was prepared by the Technology Department in support of our application registration submission to the Allegro Developer Portal. The company is ready to provide any additional materials the review team may require.