# cidr-overlap-checker

Find overlapping IP networks in a proposed address inventory.

## Run

Python 3.8 or later; no third-party packages or cloud credentials are required.

```sh
python3 tool.py examples/input.json
cat examples/input.json | python3 tool.py -
python3 -m unittest -v
```

## Example

Input:

```json
{
  "networks": [
    "10.0.0.0/24",
    "10.0.0.128/25",
    "10.1.0.0/24"
  ]
}
```

Result:

```json
{
  "overlaps": [
    [
      "10.0.0.0/24",
      "10.0.0.128/25"
    ]
  ]
}
```

The command writes JSON to standard output. Exit 0 means evaluation completed;
a finding in the output may still require attention. Invalid input returns exit 2,
with an error on standard error and no result on standard output.

## Operational scope

Compares CIDRs only; does not read routes, peering relationships, or cloud accounts.

The tool evaluates supplied data locally. It does not change hosts, deploy
resources, or establish production compliance. Example identifiers and observations
are test fixtures. Keep credentials and private inventory out of Git.

## Design and verification

See [NOTES.md](NOTES.md) for the input contract, verification, and integration notes.
Related utilities: [url-health-manifest](https://github.com/sal-s-root/url-health-manifest), [tcp-retry-budget](https://github.com/sal-s-root/tcp-retry-budget).

## Project status

A small standalone learning exercise using supplied fixtures. The related
[infrastructure toolbox](https://github.com/sal-s-root/infra-toolbox) collects these
checks in one place.

The assigned historical dates form a retrospective learning schedule; this
exercise was created or reconstructed in 2026. See [history and scope](HISTORY.md).
