# /check-continuity

Validate consistency across the screenplay.

## Arguments
- `[scope]` - Optional: `full`, `act1`, `act2`, `act3`, `scenes X-Y`

## Workflow

### Step 1: Determine Scope
- Default: Full screenplay
- Or specific act/scene range

### Step 2: Run Checks

#### Timeline Check
```markdown
## Timeline Validation

| Scene | Heading Time | Prev Scene | Status |
|-------|--------------|------------|--------|
| 1 | DAY | - | ✓ |
| 2 | DAY | DAY | ✓ |
| 3 | NIGHT | CONTINUOUS | ⚠️ |
```

Flags:
- ⚠️ DAY after NIGHT-CONTINUOUS (or vice versa)
- ⚠️ Impossible time jumps
- ⚠️ Missing time indicators

#### Character Check
```markdown
## Character Continuity

### [CHARACTER]
| Scene | Location | Issue |
|-------|----------|-------|
| 5 | Office | ✓ |
| 6 | Home | ✓ |
| 7 | Office | ⚠️ No travel time |
```

Flags:
- ⚠️ Character in impossible location
- ⚠️ Knowledge inconsistency
- ⚠️ Wardrobe impossible change

#### Prop Check
```markdown
## Prop Continuity

### [PROP]
| Scene | Status | Issue |
|-------|--------|-------|
| Intro: 5 | Active | ✓ |
| Used: 20 | Active | ✓ |
| After: 40 | ? | ⚠️ Unresolved |
```

Flags:
- ⚠️ Prop appears without introduction
- ⚠️ Prop used after destroyed
- ⚠️ Chekhov's gun unused

### Step 3: Generate Report

```markdown
## Continuity Report: [TITLE]

### Status: [CLEAN / X ISSUES]

### Timeline Issues
[List or "None found"]

### Character Issues
[List or "None found"]

### Prop Issues
[List or "None found"]

### Recommendations
1. [Specific fix]
2. [Specific fix]
```

## Success Criteria
- [ ] All scenes checked
- [ ] Timeline validated
- [ ] Character tracking verified
- [ ] Props accounted for
- [ ] Report generated

## Example Output

```markdown
## Continuity Report: Seoul Identity

### Status: 3 ISSUES FOUND

### Timeline Issues
1. Scene 15: NIGHT after CONTINUOUS from DAY scene
   → Fix: Change to DAY or add transition scene

### Character Issues
1. Sarah: In office (Sc.8) then warehouse (Sc.9) CONTINUOUS
   → Fix: Add travel time or break continuous

### Prop Issues
1. Gun: Introduced Sc.10, never resolved
   → Consider: Use in climax or remove setup

### Recommendations
1. Review scenes 14-16 for time of day consistency
2. Add brief transition between office and warehouse
3. Determine gun's story purpose
```
