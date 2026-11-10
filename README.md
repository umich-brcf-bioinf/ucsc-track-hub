# hg38 track hub and Vitessce example

This static GitHub Pages site links to an hg38 UCSC Genome Browser track hub
and a Vitessce genomic-profiles view. No build step is required.

## Publish

1. In the repository's **Settings → Pages**, select **Deploy from a branch**,
   the branch containing these files, and the `/ (root)` folder.
2. After deployment, open the Pages URL (normally
   `https://umich-brcf-bioinf.github.io/ucsc-track-hub/`) and use either link.
   The site derives the hub and configuration URLs from its own location, so
   it also works under a different repository path or custom domain.
3. In UCSC, check that the **GM12878 H3K27ac** track appears on hg38. In
   Vitessce, wait for the genomic profiles and hg38 annotations to load.

To connect the hub manually, enter the published `hub.txt` URL under
**My Data → Track Hubs** in UCSC. To preview the landing page locally, run
`python3 -m http.server` from the repository root; the external viewers cannot
fetch a hub or configuration from your localhost, so their links require a
publicly accessible deployment.

## Example data

- The UCSC hub uses an [ENCODE GM12878 H3K27ac bigWig](https://genome.ucsc.edu/goldenPath/help/examples/hubExamples/hubGroupings/groupsExample/hg38/trackDb.txt)
  hosted by UCSC. Replace `bigDataUrl` in `hub.txt` with an accessible,
  byte-range-enabled hg38 bigWig to use your own track.
- The Vitessce view uses the public [HuBMAP human intestine snATAC-seq example](https://github.com/vitessce/vitessce/blob/main/examples/configs/src/view-configs/hubmap.js),
  a GRCh38/hg38 genomic-profiles Zarr dataset. Edit `vitessce-config.json` to
  use another compatible dataset. Vitessce requires CORS-enabled data hosting.

These are different datasets and are not linked or synchronized across the
two viewers. Both viewers depend on external data and services.
