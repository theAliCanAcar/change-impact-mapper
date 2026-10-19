# Change Impact Mapper

Map changed artifacts to affected criteria and tests.

Standalone ES module. No npm install required. Works in **Node.js 20+** and modern browsers (serve over HTTP for browser demos).

## Install / import

Copy the files into your project, or clone this repository:

```js
import { mapChangeImpact } from './change-impact-mapper.js';
console.log(mapChangeImpact({changedArtifacts:['data.json'],
 dependencies:{'invoice.json':['data.json'],'report.html':['invoice.json']},
 criteria:[{id:'total',artifactIds:['invoice.json']}],
 tests:[{id:'report-test',artifactIds:['report.html']}]
}));
```

## Use cases

### 1. Rerun checks affected by a change

- **Scenario:** A source data file feeds an invoice and a generated report.
- **Outcome:** Follow reverse dependencies to identify the affected artifacts and tests.

### 2. Explain why evidence was invalidated

- **Scenario:** A seemingly unrelated input change invalidates a downstream check.
- **Outcome:** Show the dependency path that connects the changed input to the check.

## Exports

- `mapChangeImpact`
- `createChangeImpactMapper`

## Notes

- Keep API keys and secrets out of this module and out of browser storage.
- Treat verification callbacks, ledger writers, and permission checks as trusted application code.
- This library is intentional local reliability plumbing, not a claim of cryptographic attestation unless stated in the source comments.

## License

MIT
