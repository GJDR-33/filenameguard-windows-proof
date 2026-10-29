# filenameguard-windows-proof

Verified on real Microsoft Windows Server 2022 Datacenter (10.0.20348), October 29, 2026.

**Result: all 33 file checks passed.** [Successful run](https://github.com/GJDR-33/filenameguard-windows-proof/actions/runs/40835737350)

| Extraction method | Converted files: NFC, no decomposed Hangul, exact contents | Deliberately NFD control correctly detected |
| --- | --- | --- |
| PowerShell Expand-Archive | 10 / 10 | 1 / 1 |
| .NET ZipFile | 10 / 10 | 1 / 1 |
| Windows Explorer Shell ZIP | 10 / 10 | 1 / 1 |

The inputs include the exact ZIP downloaded from the browser-local filename converter (3 files) and a core-generated ZIP (7 files, including an empty file, emoji filename and a binary file over 1 MB). Every filename was checked with ordinal Unicode comparison, NFC normalization and Hangul Jamo detection. Every file was opened and its bytes were checked against the expected SHA-256 and size. Fixture ZIP bytes were also verified before extraction.

The exact UTF-8 JSON report is preserved as a base64 record in the successful job logs. Verification commit: `a4f9b798c5c7f885b50041a1c872f9addf1846a4`.

This validates these ZIP fixtures and the three Windows extraction paths. It does not validate a fresh Google Drive upload/download in a Windows browser, Windows 11 font rendering, or video playback. The first run failed before checking files because of PowerShell JSON-array handling; that harness issue was corrected before the successful run.

Only synthetic test data and the verification harness are included. No business videos, app source, private documents or credentials were uploaded. The workflow runs only on changes to its own file or manual dispatch, uses a standard public-repository runner, has read-only repository permissions, and is disabled if the repository is private.
