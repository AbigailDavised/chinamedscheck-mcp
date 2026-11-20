---
name: chinamedscheck
description: "Screen 38 controlled, banned, and allowed medications against China Customs GACC Decree 442 rules, compute 7/15/90-day carry-in limits, verify CAAC syringe/cold-chain flight rules, and generate Chinese pharmacist show cards via ChinaMedsCheck's stateless MCP server."
homepage: https://chinamedscheck.com
version: 1.0.0
license: MIT
compatibility: "Works with Hermes Agent, Claude Code, Cursor, Windsurf, and any MCP client supporting Streamable HTTP."
metadata:
  homepage: "https://chinamedscheck.com"
  mcp_endpoint: "https://chinamedscheck.com/api/mcp"
  version: "1.0.0"
  hermes:
    category: travel
    tags: [china-customs, medication-legality, gacc-decree-442, adhd-china, airport-red-channel]
---

# ChinaMedsCheck — Stateless China Customs Medication Legality MCP Skill

Connect any MCP-compatible AI agent to ChinaMedsCheck's public read-only Streamable HTTP server at `https://chinamedscheck.com/api/mcp`. Zero sign-in or API keys required.

## Endpoint Configuration

```json
{
  "mcpServers": {
    "chinamedscheck": {
      "type": "streamable-http",
      "url": "https://chinamedscheck.com/api/mcp"
    }
  }
}
```

## Direct JSON-RPC 2.0 Verification

```bash
curl -s -X POST https://chinamedscheck.com/api/mcp \
  -H "Content-Type: application/json" \
  -d '{"jsonrpc":"2.0","id":1,"method":"tools/call","params":{"name":"screen_medication_gacc_customs_legality","arguments":{"medicationQuery":"Adderall"}}}'
```

## Tools Inventory (8 Read-Only Tools)

- `screen_medication_gacc_customs_legality`: Match brands, INN generics, CAS numbers, RxNorm CUIs, and multilingual aliases against 38 regulated entries.
- `calculate_medication_supply_allowance`: Evaluate carried supply days against 7-day Class I, 15-day Class II, and 90-day personal-use limits.
- `evaluate_caac_cabin_sharps_and_cold_chain`: Check CAAC aviation rules for insulin pens, EpiPen injectors, needles, and cold packs.
- `generate_bilingual_china_pharmacy_card`: Output simplified Chinese doctor/pharmacist cards, Pinyin, domestic OTC equivalents, and declaration draft fields.
- `check_china_hospital_refill_and_clinic_pathway`: Determine domestic hospital refill eligibility, specialist tier, and documentation checklist.
- `audit_multi_medication_travel_bag_manifest`: Scan an entire luggage drug list simultaneously to determine Red/Green Channel status.
- `query_airport_red_channel_meds_walkthrough`: Terminal customs Red Channel counters & CT lock guidance for PVG, PEK, CAN, and PKX.
- `lookup_therapeutic_substitute_mesh`: Surface legal domestic alternatives when an inbound prescription is prohibited or heavily restricted.
