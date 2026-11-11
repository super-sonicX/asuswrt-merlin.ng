# Chrome HTTPS backport on Merlin 3006.102.9

Target: RT-AX86U Pro. Source preparation date: 11 November 2026.

- Stable upstream tag: `3006.102.9`.
- Stable commit: `69838e4a60564e5550e97f11d8a8cf2c6260c4f0`.
- Fork baseline branch: `stable-3006.102.9`.
- Patch branch: `fix/chrome-idle-tls-3006.102.9`.
- Upstream fix: https://github.com/RMerl/asuswrt-merlin.ng/commit/e928d8859eefd1c1917383140fedbed246f0f6f3
- Local backport: `40dabb32619000285658820d09d6f8c0fd7e5a82`.
- Stable patch ID: `b23053eb2cb6945f46a91a5825c5abfb2587124c`.

Only `release/src/router/httpd/httpd.c` changes executable behavior: 26 inserted lines and 3 removed lines. The original upstream patch applies without conflict or editing. Forward application, reverse application, whitespace checking and patch-ID equality passed. This avoids importing unrelated development-branch changes.

The change keeps idle preconnected TLS sessions from blocking the single-threaded web server while awaiting an HTTP request, and changes shutdown handling for expired idle sessions. Upstream identifies Chrome with a certificate error as a particularly visible case.

## Validation limits and next steps

This is source, not a built firmware image. No cross-compilation, hardware deployment, browser retest, firmware upgrade or service restart was performed. Complete the open GitHub review before merging. A build requires the correct model toolchain and substantially more free disk space than this minimal sparse checkout.

Before a separately authorized deployment: preserve settings, JFFS and Entware/syslogging configuration; verify the built image target; retain a known-good rollback image; test HTTPS responsiveness and certificate handling; and verify syslogging delivery, queue state and lifecycle hooks after reboot. Do not factory-reset or erase runtime queues as part of this source backport.

## Upstream references

- Stable model downloads: https://sourceforge.net/projects/asuswrt-merlin/files/RT-AX86U_PRO/Release/
- Stable changelog: https://github.com/RMerl/asuswrt-merlin.ng/blob/3006.102.9/Changelog-3006.txt
- Development changelog: https://github.com/RMerl/asuswrt-merlin.ng/blob/main/Changelog-3006.txt

The .10 changelog is provisional. This branch includes only the identified Chrome fix beyond .9. The fork's upstream-tracking main branch can contain unreleased changes; do not confuse it with the stable baseline or this patch branch.
