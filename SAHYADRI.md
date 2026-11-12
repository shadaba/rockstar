# Rockstar for the Sahyadri simulations

This repository carries Rockstar (Peter Behroozi, https://bitbucket.org/gfcstanford/rockstar; upstream history on
branches `main` and `master`) and, on branch `sahyadri`, the changes used by the Sahyadri simulation pipeline
(https://github.com/a-paranjape/sahyadri-sandbox, `scripts/pkdgrav3_pipeline/`). `sahyadri` starts at upstream
commit 36ce9ee and adds, one commit each with the original authors:

- Curvature term in H(z), Gadget-4 HDF5 header reading, Tipsy behind `HAVE_TIRPC` (Aseem Paranjape, 2024)
- Evolving dark energy (w0-wa) in the merger-tree configuration (Saee Dhawalikar, 2026)
- A native reader for pkdgrav3 compressed snapshots, `FILE_FORMAT = "PKC"` (`io/io_pkc.c`, `io/pkc_core.c`), with
  the snapshot cosmology including w0-wa passed to the writers and the catalog headers, and tests in `tests_pkc/`
  (Shadab Alam, 2026)

These were previously kept as an overlay of changed files in sahyadri-sandbox (`code/Rockstar/`); the source of
this branch is byte-identical to that overlay applied to 36ce9ee.

Build with the PKC reader (needs zstd): `make with_pkc ZSTD_INC=... ZSTD_LIB=...`, or `make with_hdf5_pkc` to
also read HDF5.
