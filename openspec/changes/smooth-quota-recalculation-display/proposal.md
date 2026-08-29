## Why

Account quota refreshes can briefly return an unknown percentage while the next
snapshot is calculated. The dashboard currently renders that transient state as
zero, so quota bars drain and rows reflow before the real value arrives.

## What Changes

- Keep the last known account quota percentage visible for a bounded refresh gap.
- Ease later percentage changes over 500 ms in account cards, list rows, and the
  account detail usage panel.
- Preserve reduced-motion behavior and keep raw values for sorting and routing.

## Capabilities

### Modified Capabilities

- `account-quota-presentation`: define stable presentation during quota refresh.

## Impact

- Frontend presentation only. Backend quota calculation and routing are unchanged.
- Account quota rows remain stable for up to 90 seconds while a value is unknown.
