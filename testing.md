# Testing and Reliability

Record each test's date, scenario, input, expected result, actual result, execution evidence, and pass/fail status.

## Topic generation
| Test | Expected result |
|---|---|
| Five valid strings | All five stored |
| Fewer than five topics | No partial batch published |
| Malformed JSON | Parse failure handled; no rows inserted |
| Empty topic | Validation rejects batch |
| Duplicate topic | Duplicate policy applied |

## Telegram selection
| Test | Expected result |
|---|---|
| Reply `1`–`5` while open | Corresponding topic selected |
| Reply `0`, `6`, or text | Invalid-input message |
| Reply `I choose 3` | Rejected by strict single-digit validation |
| Reply while closed | Closed-selection message; no selection saved |
| Duplicate update | No duplicate selected-topic row |
| Reply to an old prompt | Old reply rejected |

## Paper retrieval and analysis
| Test | Expected result |
|---|---|
| arXiv returns papers | Metadata parsed |
| No arXiv results | Controlled no-results path |
| Malformed XML | Error handled and reported |
| Gemini analysis fails | No misleading success report |
| Gmail send fails | Failure visible and recoverable |
| Database insert fails | Failure visible and recoverable |
| Paper retrieved twice | Duplicate policy applied |

Do not claim reliability metrics until they have been measured across recorded executions.
