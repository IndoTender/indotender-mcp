# IndoTender MCP

Connect your AI assistant to [IndoTender](https://indotender.com) — Indonesian government procurement data via the Model Context Protocol.

Search LPSE tenders, procurement realisasi, BPS trade statistics, company profiles, treasury payments, and government agency directories — all from your AI chat.

## Connect

```
https://indotender.com/mcp
```

Add this URL as a custom MCP connector in Claude, Cursor, or any MCP-compatible client. Sign in with Google when prompted.

- Transport: Streamable HTTP
- Auth: Google OAuth (sign in once, stays authorized)
- Docs: [indotender.com/mcp/connect](https://indotender.com/mcp/connect)

## Tools

### LPSE Tenders

| Tool | Description |
|---|---|
| `Indonesia_search_tenders` | Search Indonesian government tenders from LPSE with filters: winner, agency, date range, value |
| `Indonesia_get_tender` | Full tender detail by id — parties, applicants, and attachments |
| `Indonesia_search_companies` | Fuzzy search LPSE-registered companies by name |
| `Indonesia_get_company` | Full procurement profile for a company by NPWP — recent wins, totals |
| `Indonesia_top_winners_by_lpse` | Rank companies by value won on a specific LPSE portal |

### Inaproc / SAKTI

| Tool | Description |
|---|---|
| `Inaproc_search_instansi` | Search government agencies (kementerian, lembaga, provinsi, kabupaten) |
| `Inaproc_search_satker` | Search work units (satker) by name, optionally scoped to an agency |
| `Inaproc_search_realisasi` | Search procurement packages (realisasi pengadaan) by agency or vendor |
| `Inaproc_top_vendors` | Rank vendors by total contract value won from an agency or work unit |
| `Inaproc_search_pembayaran` | Search SP2D treasury payment records from SAKTI |

### BPS — Trade statistics

Official Indonesian import/export aggregates from [BPS dataexim](https://www.bps.go.id/). Values in IDR; net weight in kg.

| Tool | Description |
|---|---|
| `Bps_search_hs_codes` | Search HS code reference — filter by code prefix (2/4/6/8 digits) and/or product name keyword |
| `Bps_search_trade` | Paginated trade lines — filter by year, month, flow (export/import), HS code, partner country, port of discharge |
| `Bps_aggregate_trade` | Aggregate trade by dimensions (country, year, HS code, etc.) — e.g. top export partners for a commodity |

### Company Registry

| Tool | Description |
|---|---|
| `Company_search` | Search the global company registry by name or id |
| `Company_extended_search` | Advanced search with filters on industry, capital, incorporation date, country |
| `Company_get_by_id` | Full company profile by id |

## Example prompts

- *"Which companies won the most tenders from the Ministry of Health in 2024?"*
- *"Search LPSE tenders for construction projects over 10 billion rupiah"*
- *"What tenders has PT Waskita Karya won recently?"*
- *"Show me SP2D payments from the Ministry of Finance in Q1 2024"*
- *"Find all government agencies (instansi) related to education"*
- *"Which countries import rice from Indonesia in 2024?"*
- *"Aggregate Indonesian coffee exports by destination country for 2024"*
- *"Search BPS HS codes for palm oil"*

## Setup — Claude

1. Go to [claude.ai/customize/connectors](https://claude.ai/customize/connectors)
2. Click **Add custom connector**
3. Name it **IndoTender** and paste `https://indotender.com/mcp`
4. Save and sign in with Google when prompted

## Setup — Cursor / other MCP clients

```json
{
  "mcpServers": {
    "indotender": {
      "url": "https://indotender.com/mcp"
    }
  }
}
```
