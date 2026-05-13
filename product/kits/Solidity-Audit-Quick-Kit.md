# Solidity Audit Quick Kit

Price: $10

A compact pre-audit kit for Solidity developers who want to catch obvious issues before asking for a formal review.

This is not a professional security audit. It is a practical checklist and template pack for preparing a cleaner codebase.

## Who It Is For

- solo smart contract developers
- hackathon teams
- protocol founders preparing for review
- AI-assisted Solidity builders
- open-source contributors submitting contract PRs

## 30-Minute Pre-Audit Checklist

### Access Control

- Every privileged function has an explicit access modifier or role check.
- Role names match the actual authority granted.
- Ownership transfer has a safe handoff path.
- Emergency functions are documented.
- Admin functions emit events.
- No test-only admin functions exist in production contracts.

### External Calls

- External calls happen after state updates where possible.
- Reentrancy-sensitive functions use a guard or a pull-payment pattern.
- Return values are checked.
- Trusted and untrusted addresses are named clearly.
- Low-level calls have comments explaining why they are needed.

### Token Handling

- ERC20 return values are handled safely.
- Fee-on-transfer tokens are either supported or explicitly rejected.
- Decimal assumptions are documented.
- Native ETH and ERC20 paths are tested separately.
- Rescue functions cannot steal user funds.

### Math and Accounting

- Rounding direction is intentional.
- Fees cannot exceed sensible maximums.
- Empty-pool and first-deposit cases are tested.
- Total supply and per-user balances remain consistent.
- No division by zero on edge states.

### Upgrades and Initialization

- Initializers cannot be called twice.
- Implementation contracts are locked when needed.
- Storage gaps or layout rules are documented.
- Upgrade authority is explicit.
- Migration steps are written down.

### Oracle and Price Inputs

- Stale price checks exist.
- Decimals are normalized.
- Zero and negative price values are rejected.
- Manipulation assumptions are documented.
- Fallback behavior is clear.

### Signature and Permit Logic

- Nonces cannot be reused.
- Chain ID is included where relevant.
- Domain separator is correct.
- Deadlines are enforced.
- Signature malleability is handled.

### Testing

- Happy path tests exist.
- Revert tests exist.
- Boundary tests exist.
- Invariant or fuzz tests exist for accounting.
- Fork tests exist if external protocols are integrated.

## Risk Register Template

```markdown
# Risk Register

## Critical
- 

## High
- 

## Medium
- 

## Low
- 

## Known Assumptions
- 

## Out of Scope
- 
```

## Finding Template

```markdown
## Title

Severity: Critical / High / Medium / Low / Informational

### Impact

### Root Cause

### Proof or Scenario

### Recommendation

### Status
Open / Fixed / Accepted Risk
```

## Audit Prep README Section

```markdown
## Security Notes

### Roles

### Trusted Addresses

### External Integrations

### Upgradeability

### Known Limitations

### Test Commands
```

## PR Description Template

```markdown
## Summary
- 

## Security-Relevant Changes
- 

## Verification
- 

## Assumptions
- 
```

## AI Prompt: Contract Review

```text
Review this Solidity contract as a pre-audit pass.

Focus on:
- access control
- reentrancy
- accounting invariants
- unsafe external calls
- oracle assumptions
- upgrade and initialization risks
- missing tests

Return:
1. findings by severity
2. affected functions
3. exploit scenario
4. suggested fix
5. tests to add

Contract:
<paste contract>
```

## AI Prompt: Test Plan

```text
Create a focused Foundry test plan for this Solidity contract.

Include:
- happy path tests
- revert tests
- boundary tests
- fuzz tests
- invariant tests

Contract behavior:
<paste summary>
```

## Foundry Command Checklist

```bash
forge test
forge test -vvv
forge coverage
forge snapshot
forge fmt --check
slither .
```

## Buyer Note

Use this kit before submitting code to a reviewer. It will not replace an audit, but it can make the first review much less painful.

