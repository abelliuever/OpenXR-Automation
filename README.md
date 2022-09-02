# OpenXR Automation

<!--
Copyright 2022, Collabora, Ltd.
SPDX-License-Identifier: CC-BY-4.0
-->

This is a collection of small scripts I've written over time to simplify my
OpenXR related work.

Right now, many of them involve connecting GitLab to a lightweight, no-charge,
source-available, local-only Kanban-type board app,
[nullboard](https://nullboard.io) . I would recommend using whatever the latest
I've pushed to
[my fork's integration branch](https://github.com/rpavlik/nullboard/tree/integration).
(Nullboard is licensed under
[BSD-2-Clause plus the Commons Clause](https://github.com/rpavlik/nullboard/blob/master/LICENSE),
the latter of which makes it not meet the text of the Open Source Definition,
and thus why I described it in an such an awkward way.) An important feature of
Nullboard, besides its quick setup (clone and open HTML file in a browser) and
minimal environment, is that it has robust JSON import/export support, so we can
easily create/modify/parse the data of each board.

## Files

- `work_item_and_collection.py` is a somewhat-generic (though GitLab-based)
  group of data structures
- `nullboard_gitlab.py` has some shared utilities for Nullboard export (`.nbx`)
  and GitLab interaction, building on the above
- `cts_workboard_update.py`/`cts_workboard_update2.py` and
  `openxr_release_checklist_update.py` are the top-level scripts for doing the
  update for two boards I maintain. They assume you have placed your latest
  Nullboard export of the corresponding board (if available), using the default
  filename, in this root directory before execution.

## Usage

I recommend using a virtual environment to get the dependencies for this repo,
something like the following:

```sh
python3 -m venv venv   # Only needed once to create venv
. venv/bin/activate    # or . venv/bin/activate.fish
                       # or . venv/Scripts/Activate.ps1
                       # or... depending on platform and shell

# Only needed at creation or when deps change
python3 -m pip install -r requirements.txt
```

You will also need to provide a GitLab token either in your environment or in a
`.env` file (recommended, mentioned by gitignore to avoid accidental commit).

Set at least the following:

- `GL_USERNAME`
- `GL_ACCESS_TOKEN`
- `GL_URL` (probably `GL_URL=https://gitlab.khronos.org` for direct usage by
  Khronos members)

Further documentation is in the source files, basically.

## License

In general, the scripts in this repo are all BSL-1.0 licensed. Thanks to my
employer, [Collabora, Ltd.](https://collabora.com), for their "Open First"
philosophy allowing me to publish these easily.

I strive for all my repos to follow the [REUSE](https://reuse.software)
specification, with copyright and license data in each file in a
machine-parsable and human-readable way. See each file for the final word on
license for it. The full, original text for all licenses used by files in this
repo are provided in the `LICENSES` directory.
