# Reflection Tree — Branching Diagram

```mermaid
flowchart TD
    START([START]) --> A0_OPEN
    A0_OPEN[/A0_OPEN\nHow did today feel?\nheavy|flat|alive|scattered/] --> A0_BRIDGE
    A0_BRIDGE[A0_BRIDGE\nTransition to Axis 1] --> A1_Q1

    subgraph AXIS1 [" AXIS 1: LOCUS — Victim ↔ Victor "]
        A1_Q1[/A1_Q1\nWhere did your mind go first?\ninternal_a,internal_b | external_a,external_b/]
        A1_Q1 -->|internal_a or internal_b| A1_Q2_INT
        A1_Q1 -->|external_a or external_b| A1_Q2_EXT

        A1_Q2_INT[/A1_Q2_INT\nWhat did you do with the\nhardest moment today?/]
        A1_Q2_INT --> A1_Q3_INT

        A1_Q3_INT[/A1_Q3_INT\nWhen today went well,\nwhat did you attribute it to?/]
        A1_Q3_INT --> A1_R_INT

        A1_Q2_EXT[/A1_Q2_EXT\nWas there a small moment\nwhere you had a choice?/]
        A1_Q2_EXT -->|ext_yes| A1_R_EXT_SHIFT
        A1_Q2_EXT -->|ext_hindsight,ext_blind,ext_none| A1_R_EXT

        A1_R_INT[["REFLECTION: internal\nYou stayed in the driver's seat…"]]
        A1_R_EXT[["REFLECTION: external\nA hard day pulls your attention outward…"]]
        A1_R_EXT_SHIFT[["REFLECTION: external→shift\nYou found it — the small moment of choice…"]]
    end

    A1_R_INT --> BRIDGE_1_2
    A1_R_EXT --> BRIDGE_1_2
    A1_R_EXT_SHIFT --> BRIDGE_1_2

    BRIDGE_1_2[BRIDGE_1_2\nNow let's shift to what you gave] --> A2_Q1

    subgraph AXIS2 [" AXIS 2: ORIENTATION — Entitlement ↔ Contribution "]
        A2_Q1[/A2_Q1\nWhat was most on your mind\nin today's interaction?/]
        A2_Q1 -->|con_a or con_b| A2_Q2_CON
        A2_Q1 -->|ent_a or ent_b| A2_Q2_ENT

        A2_Q2_CON[/A2_Q2_CON\nDid you do something outside\nyour formal role today?/]
        A2_Q2_CON -->|con_extra,con_unglamorous| A2_R_CON_HIGH
        A2_Q2_CON -->|con_mine,con_intent| A2_R_CON_MED

        A2_Q2_ENT[/A2_Q2_ENT\nHow did input vs output\nfeel today?/]
        A2_Q2_ENT -->|ent_honest| A2_R_ENT_HONEST
        A2_Q2_ENT -->|ent_fair,ent_frustrated,ent_neutral| A2_R_ENT

        A2_R_CON_HIGH[["REFLECTION: contribution-high\nYou gave without a ledger…"]]
        A2_R_CON_MED[["REFLECTION: contribution-mid\nYou were present for your own work…"]]
        A2_R_ENT[["REFLECTION: entitlement\nKeeping score isn't always wrong…"]]
        A2_R_ENT_HONEST[["REFLECTION: entitlement-honest\nThat's a remarkably honest answer…"]]
    end

    A2_R_CON_HIGH --> BRIDGE_2_3
    A2_R_CON_MED --> BRIDGE_2_3
    A2_R_ENT --> BRIDGE_2_3
    A2_R_ENT_HONEST --> BRIDGE_2_3

    BRIDGE_2_3[BRIDGE_2_3\nNow: who else was in the picture?] --> A3_Q1

    subgraph AXIS3 [" AXIS 3: RADIUS — Self-Centrism ↔ Altrocentrism "]
        A3_Q1[/A3_Q1\nWhen you think about today's\nbiggest challenge, who comes to mind?/]
        A3_Q1 -->|self_a| A3_Q2_SELF
        A3_Q1 -->|team_a| A3_Q2_TEAM
        A3_Q1 -->|other_a or mission_a| A3_Q2_OTHER

        A3_Q2_SELF[/A3_Q2_SELF\nDid anyone else depend on\nhow you came through?/]
        A3_Q2_SELF -->|self_aware| A3_R_SELF_SHIFT
        A3_Q2_SELF -->|self_unaware,self_isolated,self_curious| A3_R_SELF

        A3_Q2_TEAM[/A3_Q2_TEAM\nCould you have made it lighter\nfor someone else?/]
        A3_Q2_TEAM -->|team_did,team_tried| A3_R_TEAM_HIGH
        A3_Q2_TEAM -->|team_missed,team_unsure| A3_R_TEAM_MED

        A3_Q2_OTHER[/A3_Q2_OTHER\nDid that outward perspective\nchange how you showed up?/]
        A3_Q2_OTHER -->|other_energized,other_less_self| A3_R_OTHER_HIGH
        A3_Q2_OTHER -->|other_hindsight,other_overwhelmed| A3_R_OTHER_MED

        A3_R_SELF[["REFLECTION: self\nA lot of work happens in a private frame…"]]
        A3_R_SELF_SHIFT[["REFLECTION: self→shift\nYou kept others in the picture…"]]
        A3_R_TEAM_HIGH[["REFLECTION: team-high\nYou tried to make the load lighter…"]]
        A3_R_TEAM_MED[["REFLECTION: team-mid\nBeing stretched makes it hard to hold anyone else…"]]
        A3_R_OTHER_HIGH[["REFLECTION: other-high\nYou discovered something Maslow pointed at…"]]
        A3_R_OTHER_MED[["REFLECTION: other-mid\nYou reached outward, even when it was still hard…"]]
    end

    A3_R_SELF --> SUMMARY
    A3_R_SELF_SHIFT --> SUMMARY
    A3_R_TEAM_HIGH --> SUMMARY
    A3_R_TEAM_MED --> SUMMARY
    A3_R_OTHER_HIGH --> SUMMARY
    A3_R_OTHER_MED --> SUMMARY

    SUMMARY[["SUMMARY\n12 possible summaries keyed on\naxis1.dominant + axis2.dominant + axis3.dominant"]]
    SUMMARY --> END([END])

    style AXIS1 fill:#1a1714,stroke:#6b4c2a,color:#f4f0e8
    style AXIS2 fill:#1a1714,stroke:#6b4c2a,color:#f4f0e8
    style AXIS3 fill:#1a1714,stroke:#6b4c2a,color:#f4f0e8
```

## Node Count

| Type | Count |
|---|---|
| start | 1 |
| question | 11 |
| decision | 7 |
| reflection | 12 |
| bridge | 3 |
| summary | 1 |
| end | 1 |
| **Total** | **36** |

## Possible Paths

- **Axis 1:** 2 main branches (internal → 1 path, external → 2 paths based on "yes I took it") = 3 distinct axis-1 paths
- **Axis 2:** 2 main branches (contribution → 2, entitlement → 2) = 4 distinct axis-2 paths
- **Axis 3:** 3 main branches (self → 2, team → 2, other → 2) = 6 distinct axis-3 paths

**Total distinct full paths:** 3 × 4 × 6 = **72 possible conversations**
**Total distinct summary reflections:** 12 (one per axis-combination key)
