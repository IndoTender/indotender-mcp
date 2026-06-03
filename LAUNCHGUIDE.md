# LAUNCHGUIDE

## Server Name
IndoTender

## Tagline
AI access to Indonesian government procurement — tenders, contracts, payments, and company profiles.

## Description
IndoTender MCP connects AI assistants to Indonesian government procurement data. Search LPSE tenders from thousands of government portals, query Inaproc/SAKTI realisasi and treasury payment records, look up company profiles, and rank vendors by contract value — all from your AI chat.

Data covers:
- LPSE (Layanan Pengadaan Secara Elektronik) — the official Indonesian e-procurement platform
- Inaproc / SAKTI — procurement realisasi and treasury disbursements
- Company registry — Indonesian and regional company profiles

## Category
Government Data, Business Intelligence, Indonesia

## Tags
indonesia, procurement, government, tenders, lpse, inaproc, sakti, contracts, sp2d, company-registry

## Pricing
Free (but sign up at indotender.com)

## Auth
OAuth — sign in with Google via the MCP authorization flow. No API key needed.

## Transport
Streamable HTTP — `https://indotender.com/mcp`

## Tools

### Indonesia_search_tenders
Search Indonesian government tenders from LPSE portals. Filters: winner, agency, value range, date range. Returns paginated tender rows.

### Indonesia_get_tender
Full tender detail by id — core fields, applicants, and file attachments.

### Indonesia_search_companies
Fuzzy company name search across LPSE-registered procurement participants. Returns NPWP and company rows sorted by total value won.

### Indonesia_get_company
Procurement profile for one company by NPWP — recent wins, total values, and company registry match.

### Indonesia_top_winners_by_lpse
Rank vendors by contract value won on a specific LPSE portal. Supports year and year-range filters.

### Inaproc_search_instansi
Search government agencies (kementerian, lembaga, provinsi, kabupaten, kota) by name.

### Inaproc_search_satker
Search work units (satker) by name, optionally scoped to an agency id.

### Inaproc_search_realisasi
Search procurement packages (realisasi pengadaan) by agency, work unit, or vendor.

### Inaproc_top_vendors
Rank vendors by total procurement value won from a specific agency or work unit.

### Inaproc_search_pembayaran
Search SP2D treasury payment records from SAKTI. Negative values indicate reversals.

### Company_search
Search the global company registry by name (contains / startsWith / endsWith) with optional country filter.

### Company_extended_search
Advanced company search with filters on industry, capital range, incorporation date, country, address, and more.

### Company_get_by_id
Full company profile by primary key id.

## Setup Instructions

### Claude
1. Open [claude.ai/customize/connectors](https://claude.ai/customize/connectors)
2. Click **Add custom connector**
3. Name it **IndoTender** and enter the server URL: `https://indotender.com/mcp`
4. Save — you will be redirected to sign in with Google

### Cursor / other MCP clients
Add to your MCP config:
```json
{
  "mcpServers": {
    "indotender": {
      "url": "https://indotender.com/mcp"
    }
  }
}
```

## Example Use Cases
- "Which companies won the most LPSE tenders from the Ministry of Public Works in 2024?"
- "Search for road construction tenders over 5 billion rupiah"
- "Show payments from Kementerian Keuangan in Q1 2024"
- "What has PT Adhi Karya won recently on government contracts?"
- "Find all kabupaten-level agencies in East Java"
