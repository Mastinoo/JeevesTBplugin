# Changelog

## 1.0.0 public RC2

- Replaced the temporary direct-IP registry connection with the stable public
  edge at `https://jeeves.metahub.gg/v1/community-registry.txt`.
- Enabled HTTPS certificate validation through Windows WinHTTP.
- Kept the registry URL compile-time only; it remains unavailable as a user
  setting so guild identity data cannot be redirected accidentally.
- Added release-bundle checks that reject a stale direct-IP RC1 DLL.
- No chat parsing, GHKey matching, nameplate mutation or rendering behavior was
  changed from the proven RC1 implementation.

## 1.0.0 public RC1

- Promoted the proven native-inline nameplate implementation to the public-release line.
- Complete opposite-faction native overhead `[TAG]` is colored, including `[` and `]`.
- Character-name color remains native.
- Native Guild Wars nameplate stacking, hiding and UI occlusion are preserved.
- Removed the experimental 0.7.x renderer/probe wall from the visible settings panel.
- Removed the overlay-anchor debug option from the public settings UI.
- Replaced the long development explanation with a compact **What it does** section, status summary and small advanced diagnostics panel.
- Added player and developer installation instructions.
- Added a public bundle helper for packaging a tested DLL.

### Proven baseline

The rendering behavior in this release is based on the working 0.8.3 pre-consume native full-bracket color implementation. The public-release cleanup intentionally changes presentation/documentation, not the working nameplate architecture.
