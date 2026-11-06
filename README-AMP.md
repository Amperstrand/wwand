# Amperstrand wwand fork (feat/nr7101-rg502q) — NR7101 / RG502Q-EA

One patch on top of upstream ddimension/wwand: this modem's QMI
server never answers CTL GET_VERSION_INFO (the exact message where
uqmi-class clients die at init). The patch treats that query as
best-effort — everything else then works (client allocation, WDS,
NAS, UIM, eSIM via QMI-UIM).

## Ready-made artifacts (no compiling needed)
Flash-and-go OpenWrt 25.12.6 image + every piece (addon files, libs,
vendor fallback stack, lpac, bench toolset):
https://github.com/Amperstrand/conwrt-bench/releases/tag/nr7101-wwand-v2c

## If you want the details
- Evidence chain + deployment recipe:
  conwrt-bench `docs/nr7101/NR7101-WWAND-ANALYSIS.md`
- Build-it-yourself (SDK procedure):
  conwrt-bench `docs/nr7101/NR7101-WWAND-SDK-BUILD.md`
- Proven numbers: 45.7 Mbit/s (QMAPv5), 63 ms flat, cold-boot
  zero-touch (RUN-4), kernel-exact tollgate byte quotas on-box.
