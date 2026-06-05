# r.cell.area — development notes for Claude Code

## Repository purpose

This is the **full-history development repository** for the `r.cell.area` GRASS
GIS addon. The canonical release destination is
[OSGeo/grass-addons](https://github.com/OSGeo/grass-addons), which uses a
squash-merge convention. Development work with granular commits happens here so
that the complete history is preserved for provenance and citation.

## Workflow

1. Develop and commit here with granular, descriptive commits (one logical
   change per commit).
2. Open a PR against `OSGeo/grass-addons` from the working branch in the
   grass-addons clone at `~/dataanalysis/grass-addons`. That PR will be
   squash-merged, collapsing all commits into one.
3. After the grass-addons PR merges, sync master here with the squashed commit
   from upstream, then continue development on a new branch.

The squash-merge means grass-addons master and this repo's master will diverge
after a PR lands. That is expected and intentional.

## Commit conventions

- Each commit = one logical change (bug fix, feature, refactor, test, doc).
- Commit messages describe *what changed and why* at a level readable in
  `git log --oneline`.
- Never bundle unrelated changes into one commit.
- When a commit message lists multiple renames, use one line per change.

## Testing

Tests live in `testsuite/test_r_cell_area.py` and use the GRASS `gunittest`
framework. Run them via the standard grass-addons CI or locally with:

```bash
grass --tmp-project EPSG:32614 --exec \
  python3 -m grass.gunittest.main \
    --grassdata $HOME --location nc_spm_full_v2alpha2 --location-type nc \
    testsuite/test_r_cell_area.py
```

The `TestRCellAreaMeters` class requires the NC sample dataset. The
`TestRCellAreaDegrees`, `TestRCellAreaFeet`, and `TestRCellAreaXY` classes
spawn temporary GRASS projects and run anywhere.

## Pending improvements

See the open issue list on this repo and the memory entry in the Claude Code
project memory (`project_r_cell_area_todo.md`) for the backlog of identified
improvements not yet addressed.
