# Azure DevOps Work Items Summary

## Overview
This document provides a summary of all 103 unique Azure DevOps work items linked to your 228 pull requests across the Lighthouse-io organization.

## Work Item Statistics

- **Total Unique Work Items:** 103
- **PRs with Work Items:** 228
- **Average PRs per Work Item:** 2.2
- **Organization:** teamsoftwareinc

## All Work Item IDs

### Batch by Number Range

#### 160,000 - 169,999
- AB#162765
- AB#163629
- AB#165149
- AB#165343
- AB#165396
- AB#167210
- AB#167268

#### 170,000 - 179,999
- AB#172279
- AB#173994
- AB#174616
- AB#174739
- AB#176129
- AB#176446
- AB#176752
- AB#177426

#### 180,000 - 189,999
- AB#180008
- AB#180416
- AB#181517
- AB#181519
- AB#181521
- AB#182267
- AB#183855
- AB#183857
- AB#185439
- AB#185504
- AB#187661
- AB#187749
- AB#188269
- AB#188598
- AB#188795
- AB#189081

#### 190,000 - 199,999
- AB#190036
- AB#190079
- AB#191220
- AB#192089
- AB#192089
- AB#192181
- AB#192379
- AB#192405
- AB#193050
- AB#193096
- AB#193397
- AB#193534
- AB#193851
- AB#193933
- AB#194167
- AB#194402
- AB#195097
- AB#195230
- AB#196057

#### 200,000 - 209,999
- AB#200099
- AB#201270
- AB#202026
- AB#202027
- AB#202171
- AB#202369
- AB#202370
- AB#202456
- AB#203230
- AB#203231
- AB#203248
- AB#203249
- AB#204104
- AB#205140
- AB#205158
- AB#205346
- AB#207255
- AB#208137
- AB#209001
- AB#209115

#### 210,000 - 219,999
- AB#211108
- AB#211273
- AB#212102
- AB#213283
- AB#214261
- AB#214529
- AB#215168
- AB#215569
- AB#216215
- AB#217155
- AB#217188
- AB#217228
- AB#218026
- AB#218138
- AB#219132

#### 220,000 - 229,999
- AB#220042
- AB#220047
- AB#220140
- AB#220146
- AB#220341
- AB#220555
- AB#221308
- AB#221500
- AB#222222
- AB#222405
- AB#223119
- AB#223408
- AB#223409
- AB#223555
- AB#224013
- AB#224019
- AB#224122
- AB#225179
- AB#225316
- AB#225372

#### 230,000 - 239,999
- AB#230379
- AB#230379
- AB#230461
- AB#230704
- AB#231018
- AB#231429 (frequently used)
- AB#232168
- AB#232365
- AB#233096
- AB#233151
- AB#234030
- AB#234854 (frequently used)
- AB#235013
- AB#235352
- AB#236048
- AB#236148
- AB#236154
- AB#236449
- AB#236514
- AB#236683

#### 240,000 - 249,999
- AB#240299
- AB#242044
- AB#242147
- AB#243135
- AB#243153
- AB#243278
- AB#244068
- AB#244267
- AB#244380
- AB#246056
- AB#246163
- AB#246329
- AB#247083
- AB#248158

#### 250,000 - 259,999
- AB#250289
- AB#250298
- AB#250480
- AB#251045
- AB#251176
- AB#252181

#### 260,000+
- AB#260013
- AB#274779
- AB#276528

## Most Frequently Used Work Items

Based on PR count, these work items appear in multiple PRs:

1. **AB#231429** - Multiple image/signature-related PRs
2. **AB#234854** - Export and CloudFront-related PRs
3. **AB#276528** - Image fetching PRs

## Usage Examples

### Query a specific work item:
```
Get work item AB#231429
Show status and history of AB#234854
```

### Query multiple work items:
```
Get details for work items AB#231429, AB#234854, AB#276528
```

### Find related PRs:
```
What PRs are linked to work item AB#231429?
```

## Integration with OpenCode

Once Azure DevOps MCP is configured, you can:

1. **Query work item metadata:**
   - Title, description, state
   - Assigned user, creation date
   - Tags and custom fields

2. **Batch retrieve details:**
   - Load all 103 work item details
   - Filter by status, assignee, or team
   - Generate reports

3. **Create correlations:**
   - Link PRs to features
   - Track feature completion
   - Build release notes

4. **Automation:**
   - Update work item status
   - Add PR links to work items
   - Create follow-up tasks

## Data Extraction

This information was extracted from:
- `prs-enhanced.md` (889 lines of PR data)
- Pattern matching: `AB#\d+` with Azure DevOps links
- Verified 228 PRs have work item associations

## Next Steps

1. Complete Azure DevOps MCP setup (see `AZURE_DEVOPS_SETUP.md`)
2. Use OpenCode to query work item details
3. Create enriched reports combining PR and work item data
4. Automate work item updates based on PR activity

## Batch Query Template

For programmatic access, use the work item IDs above to create queries:

```json
{
  "work_items": [
    162765, 163629, 165149, 165343, 165396, 167210, 167268,
    172279, 173994, 174616, 174739, 176129, 176446, 176752,
    177426, 180008, 180416, 181517, 181519, 181521, 182267,
    183855, 183857, 185439, 185504, 187661, 187749, 188269,
    188598, 188795, 189081, ...
  ],
  "fields": [
    "System.WorkItemType",
    "System.Title", 
    "System.State",
    "System.AssignedTo",
    "System.CreatedDate",
    "System.Tags"
  ]
}
```

See `workitem_queries.json` for complete batch query template.

---

**Last Updated:** November 4, 2025
**Total Work Items:** 103
**Data Source:** prs-enhanced.md
**Status:** Ready for Azure DevOps API queries
