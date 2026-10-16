REPLICATION FILES: Group 5 (Giant River Turtle), Question 5, Peru
"What should FZS track every year?" Five indicators for illegal gold mining

The five indicators
  1  Gold price in soles, after inflation, compared with its 3 year average   (early, monthly)
  2  Peru's gold gap: gold exported minus gold declared as produced           (early, monthly)
  3  New mining in FZS landscapes, hectares per quarter                       (now, quarterly)
  4  Forest that became mining: reserves and buffer zones; all Madre de Dios  (late, yearly)
  5  New mining outside Madre de Dios                                         (now, quarterly)
  Other signals (Colombia, Brazil, mercury, coca, dredges, excavators) are reported as context.

Software:      R 4.6.1 with tidyverse, readxl, jsonlite, sf, terra, patchwork, zoo, rmarkdown, knitr
               install.packages(c("tidyverse","readxl","jsonlite","sf","terra","patchwork","zoo","rmarkdown","knitr"))
               (sf and terra need the GDAL/GEOS/PROJ system libraries; on Windows and macOS the CRAN binaries include them)
               The notebook sets a UTF-8 locale (place names have accents, e.g. "Amazonía"). On Windows, if a
               check fails with 0 ha, run R with a UTF-8 locale.
To reproduce:  open code/group5_kpis.Rmd and click Knit, or run from the code/ folder:
                 Rscript -e 'rmarkdown::render("group5_kpis.Rmd", output_dir = "../output")'
               Run time: about 2 to 4 minutes (plus first downloads: the two large Amazon Mining Watch files and, if
               missing, the regional files in data_raw/regional/, about 4 minutes because UN Comtrade limits the call rate).
               The notebook stops with "check failed" if any number differs from the publisher's (26 checks,
               including checks that detect a changed Amazon Mining Watch file).
Output:        output/group5_kpis.html            the full notebook: every table, figure and number, with the code
               (code/group5_kpis.html is the same file, kept next to the Rmd)
               output/fig_main.png                the figure in the brief
               output/table8_kpi_summary.csv      the five indicators: value today, source, delay, red line, action, limits
               output/table6_red_lines.csv        the red line of each indicator and why
               output/table7_backtest.csv         when each indicator would have turned red, and when it was public
               output/numbers_in_brief.csv        every number in the brief: computed ones, and published figures typed by
                                                  hand (marked "typed by hand", with report and date)
               output/table1 ... table5 (.csv)    flows, comparisons and the tables behind each indicator
               output/table_scar_hectares_by_zone.csv   Amazon Mining Watch scar map hectares by period and zone (Peru)
               output/fig_*.png, map1 ... map3    supporting figures and maps
               output/tableR1 ... tableR10, figR_*     context: Peru gold gap, Colombia, Brazil, mercury, coca, dredges
Raw data:      data_raw/ contains every file exactly as downloaded. DOWNLOAD_LOG.csv has one row per file.
Left out:      Two Amazon Mining Watch files are above the 50 MB limit. They are kept in ../data_large/, next to
               (not inside) this folder, and the notebook downloads them automatically if they are missing:
                 amazon_basin_detections.geojson     (113 MB; 232,030 features; MD5 e55d422588158e0ef4772892d45b8137)
                 https://data.source.coop/earthgenome/amazon-mining-watch/amazon_basin_detections.geojson
                 amazon_basin_mining_scar_masks.tif   (62 MB; MD5 fe26c8ac69f642589fe6cd635bb744ce)
                 https://data.source.coop/earthgenome/amazon-mining-watch/amazon_basin_mining_scar_masks.tif
               Amazon Mining Watch replaces these files when its model changes. We used the version described by the
               README dated 3 October 2026. If the files have changed, the notebook stops at the Amazon Mining Watch checks.

Presentation:  presentation/group5_presentation.html   the 10 minute deck (one file; open in any browser;
                                                     arrow keys to move, N for speaker notes, F for full screen)
               presentation/group5_presentation.pdf    the same slides as a PDF
               The charts in the deck are the PNG figures in output/, made by code/group5_kpis.Rmd.
               Live version: https://santiagosierraiba.github.io/fzs-gold-mining-kpis/

Brief:         Brief/Group_5_DFG_Brief.pdf               the two page brief (page 3: references and appendix)
               Brief/Group_5_DFG_Brief.tex               its LaTeX source
Dashboard:     dashboard.html                          an interactive page with the five indicators; it reads this
                                                     repository on GitHub when it opens (or a built in copy)
               index.html                              opens the presentation on the live version

Folder structure (what goes in the zip)
  README.txt
  DOWNLOAD_LOG.csv
  data_raw/
  code/group5_kpis.Rmd
  output/
  presentation/
  Brief/
  dashboard.html, index.html
Do not include: .git/, .Rproj.user/, .RData, .Rhistory (RStudio and git private files). group5_replication.Rproj is optional.
