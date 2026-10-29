# Local patch to gpui-component 0.8.1

Upstream: https://github.com/longbridge/gpui-kit (Apache-2.0).

Two small methods in `src/diff/state.rs`:

- `DiffState::sticky_file_header()` exposes the file whose header has started
  scrolling out and the next header's painted position. Read after prepaint,
  it allows same-frame sticky rendering and push-off without estimating row
  heights, tracking wheel deltas, app rerenders on scroll, or idle polling.
  Wheel, scrollbar, keyboard, file jumps, and wrapping share the same geometry.
- `DiffState::set_collapsed_files()` applies saved review state in one rebuild,
  avoiding a full list rebuild for every viewed file.

Based on upstream commit 99576db58ec8103417c41a092e891b4022d24e7e (the published 0.8.1 source).

Remove this patch when the upstream component exposes equivalent APIs.
