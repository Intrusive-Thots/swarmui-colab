# swarmui-colab

This repo holds a Google Colab notebook for installing mcmonkeyprojects/SwarmUI on Google Drive and launching it with a Cloudflare tunnel, plus cells that write image-prompt wildcard files.

Open swarmui-colab.ipynb in Colab.

Source notebook: https://colab.research.google.com/drive/1-DbwbgXOmXh5wmubqO3yDC90IPGGp9B4

## NECGRO skin

Each launch cell applies a NECGRO skin after the git update and before `launch-linux.sh`. The skin is written into that install (`src/Extensions/NECGRO`). This repo does not vendor SwarmUI.

SwarmUI registers themes and selects the user `Theme` setting. Until that setting or the `sui_theme_id` cookie is present, the page layout falls back to `modern_dark`. Extension `StyleSheetFiles` are the extra user CSS injected into the page header; theme stylesheets load after that, so the layout sheet is also the last NECGRO theme file. The layout still hardcodes the product name `SwarmUI` beside `UserAuthorization.InstanceTitle`, so the notebook rewrites those visible strings and sets the instance title to NECGRO. `git reset` restores the upstream layout, and the launch cell applies the skin again after the pull.

Run a launch cell, open the Cloudflare URL, and the page title, version line, and installer heading should say NECGRO on a flat dark background with a tighter layout.
