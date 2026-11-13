# Harbor PDF qualification — 2026-11-13

Scope: independent Windows portable development build, derived from `db9955a2c7fa971d91ae966a7d26693434580bf7`. Original history and credits are retained.

## Passed

- Optimized native Windows release build and application launch with two synthetic PDFs.
- Move Tab to New Window produced two native Harbor PDF windows.
- 49 print tests; 17 tab-window tests; 1 update-identity test; 9 widget tests; 6 portable-settings tests; 3 clipboard/image-name tests; 6 platform-settings tests: **91 passed, none failed**.
- Tab tests cover raw tear-off input, horizontal reorder, cross-window transfers, Organize-page insertion, undo, encryption permissions, save guards, recovery identity and external-file-change protection.
- Formatting, strict clippy for changed PDF app/UI/engine targets, dependency layering and asset attribution checks.
- WebAssembly compile check of the changed UI/engine crates.

The settings module uses only std; its six tests were compiled directly with `rustc --edition=2024 --test apps/pdfcraft/src/settings.rs`. The remaining focused tests ran from release test binaries built by Cargo.

## Printing

Uses the pinned craft-print native Windows backend (in-process XPS/GDI, without PowerShell). Architectural paper presets and PDF scale controls remain available. This preserves upstream backend authorship as well as the original paper-size contribution. No throughput comparison or physical printer job was performed for this build.

## Limits

The native menu command was observed creating a second window. Automated raw-input drag tests passed; the manual drag gesture was not conclusively verified because Windows capture intermittently returned the foreground application rather than the requested window. Do not represent that as a passed manual drag test.

Only the Windows portable build is qualified here. Legacy upstream installer recipes are not Harbor installers. No production release, installer, signing or updater distribution has been qualified. The manual update target is durtyrobbin/harbor-pdf, with automatic startup checking disabled.

## Windows installer qualification — 2026-11-13

The independent `packaging/harbor` Inno Setup recipe supersedes the portable-only packaging limitation above. The unsigned x64 setup passed an isolated install → same-version upgrade → uninstall round trip. The installed executable matched the staged binary's SHA-256 and an unowned synthetic document survived upgrade and uninstall. No personal documents were used. Setup registers per-user shortcuts, App Paths and an Installed apps entry; it does not forcibly close running apps or change file associations. Windows Search discovery remains unverified: `Get-StartApps` did not list the new shortcuts on the test machine.
