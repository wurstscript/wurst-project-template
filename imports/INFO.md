# imports/

All files placed in this folder are imported into any built map, preserving the same
folder hierarchy they have here.

With map-folder mode, this is largely obsolete for map projects: you can just put files
directly in the map folder and they'll be available in the map *and* usable in the editor
(imports/ files are not selectable in the editor, e.g. for models/icons).

Still useful for:
- Libraries/dependencies that ship file imports (models, icons, etc.) — dependencies don't
  provide a map folder, so this is their only way to deliver assets to consuming maps.
- Compatibility with older WC3 patches/editors that don't support map folders.

If you don't need either of these, feel free to delete this folder.

## dummy.mdx

A workaround model used for spawning special effects on units without attaching a visible
model (dummy caster tricks, etc.). Whether you need this depends on the patch you target:
in Reforged it's no longer necessary since the native effect API (e.g.
`AddSpecialEffect`/`DestroyEffect` and related) can create/destroy effects directly without
a dummy unit — but it's still required when targeting older, pre-Reforged patches. Remove
it if you only target Reforged.
