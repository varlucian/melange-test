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

Check the dry-run summary of current and new versions

```sh
echo "Package,Current,New" && LOG_LEVEL=debug GITHUB_TOKEN=$(gh auth token) renovate --dry-run=full varlucian/melange-test 2>&1 | grep -A 20 -B 5 '"packageName":'
 | grep -E '"packageName":|"currentValue":|"newValue":' | sed 'N;N;s/\n/ /g' | grep -E '"packageName".*"currentValue".*"newValue"' | sed 's/.*"packageName": "\([^"]
*\)".*"currentValue": "\([^"]*\)".*"newValue": "\([^"]*\)".*/\1,\2,\3/' | sort -u
```
