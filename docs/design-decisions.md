# Design decisions

| Area | Decision |
|---|---|
| Trigger | A customer's periodic review date, or a trigger event such as a change of ownership |
| Architecture | LangGraph supervisor with four specialist agents: records, ownership, screening, drafting |
| Why multi-agent here | Each step uses different tools and sources, and can be tested on its own |
| Ownership | 25% ownership prong and one control person, per the FinCEN CDD rule |
| Indirect ownership | Calculated in code through each layer of entities |
| Sanctions screening | OFAC SDN list through an MCP tool; fuzzy matching with scores |
| Match handling | Possible matches go to the analyst with evidence; the agent never clears them |
| Output | Draft review: changes found, owners and controllers, screening results, open questions |
| Human in the loop | An analyst signs off every review |
| Never | Updates the customer file, changes a risk rating, or clears a sanctions hit |

## Planned evaluation

Synthetic company structures with known owners, including layered ownership, ownership changes and names close
to SDN entries. Measures: correct beneficial owners and control person, every change caught, no true sanctions
match missed, and the false-positive rate on screening.
