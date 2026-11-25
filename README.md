# clay-printer-interface

A browser interface for driving a 3D printer over Web Serial, split out of
[3D-printer-interface](https://github.com/vina-setiawaty/3D-printer-interface)
for work on clay printing. It contains three pages:

| Page | Path |
|---|---|
| Sewing editor (printer controls, raw G-code, LLM G-code) | `sewingeditor/index.html` |
| Texture actions (texture strokes and brushes) | `sewingeditor/texture-actions/texture-actions.html` |
| Parametric, staged pipeline (manager → geometry / texture / ui, gate, judge) | `sewingeditor/parametric-with-tool/parametric-with-tool.html` |

Shared code: `sewingeditor/script.js` (printer controls), `nav.js`,
`llm.js`, `lib/p5.fab.sewing.js`, `main/`, and the Vercel functions in
`sewingeditor/api/`.

## Tests

```sh
node sewingeditor/texture-actions/tests/run.mjs
node tests/parametric/compile-fixtures.mjs
node tests/parametric/golden-brushes.mjs
node tests/parametric/pipeline.mjs
node tests/parametric/print-constraints.mjs
node tests/parametric/prompt-assembly.mjs
node tests/parametric/session-file.mjs
```

Some of these already failed in the source repo when this was split off
(texture-actions run.mjs, 6 freeformSegmented golden cases, and the
prompt-budget check in prompt-assembly).
