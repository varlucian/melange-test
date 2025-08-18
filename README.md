# melange-test

## Renovate

Dry-run

```bash
renovate --dry-run=full varlucian/melange-test
```

Look for relevant output

```bash
renovate --dry-run=full varlucian/melange-test 2>&1 | grep -A 5 -B 5 "nexthink-oss/gitea-mirror\|nexthink-oss/ghup\|newVersion\|currentVersion"
```

Actually create the Pull Request

```bash
renovate varlucian/melange-test
```
