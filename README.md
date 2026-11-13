# Harbor PDF

Independent native Windows PDF editor maintained for @durtyrobbin, derived from PdfCraft.

This fork preserves detachable document tabs, tab reordering, transfers between windows, and drops into Organize Pages. Printing retains architectural paper presets and scale controls with the native Windows printing backend.

Harbor has separate settings, recovery and IPC identities. Startup update checks are disabled; the manual updater points only to durtyrobbin/harbor-pdf. It never migrates the installed PdfCraft settings.

## Build

Use the repository's Rust toolchain and documented dependencies in docs/development.md. Supply the pinned craft-i18n build input and optional craft-fonts input as documented there, then run `cargo build --release -p pdfcraft`. Internal crate/binary names remain compatible; the Windows portable distribution uses Harbor-PDF.exe and portable.txt.

Only the Windows portable fork is being qualified. Legacy upstream installer recipes are not Harbor installers and must not be used to install this fork.

## Provenance

Fork base: db9955a2c7fa971d91ae966a7d26693434580bf7, including the original tab-window contribution. Full history and original copyright/credit remain intact. Original project: https://github.com/storytold/pdfcraft. This is not an official ArtCraft product.

Code remains MIT OR Apache-2.0; see LICENSE-MIT, LICENSE-APACHE, NOTICE and ATTRIBUTION.toml. Harbor's geometric H icon is original and carries the same license. Upstream trademark artwork is excluded from the current tree.

Windows portable development build: release compilation and 91 focused tests passed. See [HARBOR-QUALIFICATION.md](HARBOR-QUALIFICATION.md) for validation and remaining limits. No production release is claimed.
