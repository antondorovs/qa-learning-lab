# Commands

## Test Commands

Run all tests:

```bash
npm test
```

Run all tests in Chromium:

```bash
npm run test:chromium
```

Run API tests:

```bash
npm run test:api -- --project=chromium
```

Run UI tests:

```bash
npm run test:ui -- --project=chromium
```

Open Playwright report:

```bash
npm run test:report
```

## Git Commands

Check status:

```bash
git status --short
```

Show changed files summary:

```bash
git diff --stat
```

Show last commits:

```bash
git log --oneline -5
```

Push to GitHub and GitLab:

```bash
git push origin main
git push gitlab main
```

## Project Review Commands

List tracked files:

```bash
git ls-files
```

Estimate language/file size balance:

```powershell
$files = git ls-files
$files | ForEach-Object {
  $f = $_
  $len = (Get-Item -LiteralPath $f).Length
  [PSCustomObject]@{
    Ext = if ([IO.Path]::GetExtension($f)) { [IO.Path]::GetExtension($f) } else { [IO.Path]::GetFileName($f) }
    Length = $len
  }
} | Group-Object Ext | ForEach-Object {
  [PSCustomObject]@{
    Ext = $_.Name
    Bytes = ($_.Group | Measure-Object Length -Sum).Sum
    Files = $_.Count
  }
} | Sort-Object Bytes -Descending | Format-Table -AutoSize
```
