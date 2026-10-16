# ADASS 2026 Proceedings — paper submissions

Every accepted contribution has its own ready-made folder in `papers/`, named after its
paper ID (PID). Find **your** PID in the [list of papers](#papers) below; the folder
with that name is the only one you work in. A PID is a letter and three digits: the
letter is the presentation type (I, C, P, F, B, T), the first digit is the track number,
and the last two digits number the papers within that track.

> [!IMPORTANT]
> **Every pull request must come from your own fork of this repository.** Pull requests
> from a branch in this repository are not accepted, even if you have write access.

## For authors

Submit your paper by **forking** this repository; editing **your own paper's
folder** in your fork; and opening a **pull request** (PR) from your fork back to this
repository. The editors review your paper in that pull request and merge it when it is
accepted.

```
 this repository                      your fork
 (ADASS)                              (your-username)
 ┌──────────────────┐   1. Fork      ┌─────────────────────────────────────┐
 │ main             │ ─────────────▶ │ main                                │
 │                  │                │   │ 2. branch YOURPID               │
 │                  │                │   ▼                                 │
 │                  │                │ YOURPID: edit papers/YOURPID/ only  │
 │                  │ 3. pull request│                                     │
 │ main ◀───────────┼────────────────┼─ YOURPID                            │
 └──────────────────┘                └─────────────────────────────────────┘
       4. the editors review and merge
```

A fork is your own copy of this repository under your GitHub account. The pull request is how you ask for your folder to be copied from your fork into this repository.

> [!IMPORTANT]
> **The three rules**
>
> 1. **Work in your own fork, and open the pull request from it.** Don't push branches
>    to this repository or ask for write access to it; you don't need it. A check on
>    every pull request fails if it doesn't come from a fork.
> 2. **Change only your own folder, `papers/<PID>/`.** Nothing outside it: not the
>    README, not `.github/`, not anyone else's paper, not the `Makefile`, style files
>    or scripts inside your folder.
> 3. **One paper per pull request.** If you are first author on two papers, open two
>    pull requests, each from its own branch.
>
> A pull request that breaks these rules will be sent back to you to fix.

Throughout these instructions, `YOURPID` stands for **your** PID and `your-username`
for **your** GitHub username: type yours wherever they appear.

### Contents

- [Before you start](#before-you-start)
- [Route A: with git on your computer (recommended)](#route-a-with-git-on-your-computer-recommended)
- [Route B: in the browser only, no git](#route-b-in-the-browser-only-no-git)
- [Optional: writing your paper in Overleaf](#optional-writing-your-paper-in-overleaf)
- [After you open the pull request](#after-you-open-the-pull-request)
- [What to put in your folder](#what-to-put-in-your-folder)
- [Fixing common mistakes](#fixing-common-mistakes)

### Before you start

You need:

- a [GitHub account](https://github.com/signup);
- your PID, from the [list of papers](#papers) below;
- for route A, [git](https://git-scm.com/downloads) and a TeX Live installation
  (`pdflatex`, `bibtex`, `make` and `python3`). If you'd rather not install LaTeX, you
  can [write the paper in Overleaf](#optional-writing-your-paper-in-overleaf) and use
  route B to submit it.

Start with [`docs/README_2026.md`](docs/README_2026.md); that is the README for the ADASS author template, and explains the `make` targets, index entries,
PaperCheck and what is in your folder.

If necessary, the complete formatting rules are in [`docs/ManuscriptInstructions.pdf`](docs/ManuscriptInstructions.pdf) (the ADASS guidelines). [`docs/ADASS_template.pdf`](docs/ADASS_template.pdf) shows what the starting template looks like once built.

### Route A: with git on your computer (recommended)

#### A1. Fork this repository

1. Sign in to GitHub.
2. At the top right of this page, click **Fork**.
3. Leave the owner as your own account and the repository name as it is. Leave
   **Copy the `main` branch only** ticked.
4. Click **Create fork**.

You now have your own copy at `https://github.com/your-username/<this repository's name>`.
Everything you do from here on happens in your fork; this repository is only touched
when the editors merge your pull request.

#### A2. Clone your fork

On **your fork's** page (check that the top left says `your-username/...`, not the
ADASS organisation), click the green **Code** button and copy the URL. Then:

```
git clone <the URL you copied>
cd <this repository's name>
```

#### A3. Create a branch for your paper

Don't work on `main`. Make a branch named after your PID:

```
git switch -c C101
```

(With git older than 2.23, use `git checkout -b C101`.)

#### A4. Write your paper

Everything you need is already in `papers/YOURPID/`, and it builds as it is. Edit only
the files listed in [What to put in your folder](#what-to-put-in-your-folder).

#### A5. Build and check it

```
cd papers/YOURPID
make pdf      # builds YOURPID.pdf
make check    # runs the ADASS PaperCheck
make fix      # replaces non-ASCII characters with LaTeX
              # (keeps the original as YOURPID.tex_1)
cd ../..
```

Fix any LaTeX errors and anything PaperCheck reports, except its warning about the
copyright form: that form goes to the editors, not into the repository. Then check
`YOURPID.pdf` against the page limit: **10 pages** for an invited talk, **4 pages** for
everything else, references included.

#### A6. Check what you changed, then commit

From the top of the repository:

```
git status
```

**Every** path listed must start with `papers/YOURPID/`. If anything else is listed, see
[Fixing common mistakes](#fixing-common-mistakes) before going on. Then add your folder,
and only your folder:

```
git add papers/YOURPID/
git status      # check again: under "Changes to be committed",
                # only papers/YOURPID/ is listed
git commit -m "YOURPID: first draft"
```

Don't use `git add .` or `git add -A` from the top of the repository: they pick up
anything else you touched. Build output (the PDF, `.aux`, `.log` and so on) is ignored
by `.gitignore`, so it isn't added.

#### A7. Push the branch to your fork

```
git push -u origin YOURPID
```

`origin` is your fork. You don't need, and won't have, permission to push to this
repository.

#### A8. Open the pull request

1. Go to **your fork** on GitHub. A yellow banner says *YOURPID had recent pushes*;
   click **Compare & pull request**. (No banner? Click **Contribute** → **Open pull
   request**.)
2. Check the four boxes at the top of the page read:
   - **base repository**: this repository (the ADASS one, not your fork)
   - **base**: `main`
   - **head repository**: `your-username/...` (your fork)
   - **compare**: `YOURPID` (your branch)
3. Title it with your PID and your paper's title: `YOURPID: Your paper title`.
4. Fill in the checklist that appears in the description.
5. Leave **Allow edits and access to secrets by maintainers** ticked, so the editors can
   make small fixes for you.
6. Click the **Files changed** tab before you submit, or right after: every file must
   be inside `papers/YOURPID/`.
7. Click **Create pull request**.

Then go to [After you open the pull request](#after-you-open-the-pull-request).

### Route B: in the browser only, no git

Use this if you don't want to use git. If you're writing in Overleaf, follow
[Optional: writing your paper in Overleaf](#optional-writing-your-paper-in-overleaf)
first; it brings you back here to submit.

#### B1. Fork this repository

As in [A1](#a1-fork-this-repository): **Fork** at the top right of this page, then
**Create fork**.

#### B2. Upload your files into your folder

1. On **your fork**, click into `papers`, then into **your** folder, `YOURPID`. Check
   the path above the file list reads `<repository>/papers/YOURPID/`.
2. Click **Add file** → **Upload files**.
3. Drag in your `YOURPID.tex`, `YOURPID.bib`, figures and `makedefs`. Files with the
   same name replace the template's ones. Upload only the files listed in [What to put
   in your folder](#what-to-put-in-your-folder).
4. To delete a template file you no longer use (such as the `example.*` figures), open
   it, click **⋯** at the top right → **Delete file**.
5. Under **Commit changes**, choose **Create a new branch for this commit and start a
   pull request**, and name the branch `YOURPID`. Click **Propose changes**.

   (If you've already made the `YOURPID` branch, switch to it with the branch menu at
   the top left before uploading, and commit to it directly.)

#### B3. Open the pull request

GitHub takes you to the *Open a pull request* page. Follow
[A8](#a8-open-the-pull-request) from step 2.

### Optional: writing your paper in Overleaf

Your folder compiles in Overleaf as it is, so you can write and collaborate on the
paper there, and submit it with route B (or route A) at the end. The three rules still
apply: the pull request comes from your fork and changes only `papers/YOURPID/`.

> [!NOTE]
> Don't use Overleaf's **GitHub Sync** or **Import from GitHub** with this repository.
> They copy the whole repository, which has more files than an Overleaf project allows,
> and they only work with the `main` branch. Copying your one folder across, as below,
> is simpler.

#### O1. Put your folder into Overleaf

1. On this page, click the green **Code** button → **Download ZIP**, and unzip it.
2. Find your folder, `papers/YOURPID/`, in the unzipped files, and make a zip of just
   that folder (on macOS, right-click → **Compress "YOURPID"**; on Windows, right-click
   → **Send to** → **Compressed (zipped) folder**).
3. In Overleaf, click **New Project** → **Upload Project**, and choose that zip.

#### O2. Set up the project

Open the project's **Menu** (top left) and set:

- **Compiler**: `pdfLaTeX`
- **TeX Live version**: the newest one offered, which is closest to what the checks use
- **Main document**: `YOURPID.tex`

Click **Recompile**. You should see the ADASS template, as in
[`docs/ADASS_template.pdf`](docs/ADASS_template.pdf).

#### O3. Write the paper

Edit `YOURPID.tex` and `YOURPID.bib`, upload your figures as `YOURPID_f1.png`,
`YOURPID_f2.pdf` and so on, delete the `example.*` figures, and check your surname and
email in `makedefs`. See [What to put in your folder](#what-to-put-in-your-folder).

- Leave the other files (`Makefile`, `asp2023.sty`, the `.bst`, the Python scripts)
  where they are and unchanged. Overleaf needs the style files to compile your paper;
  the rest is harmless.
- Don't add other `.sty` or `.cls` files, or extra packages, without asking the editors:
  the book is built with the ADASS style only.
- Overleaf can't run `make check` or `make fix`. The PaperCheck and *Unprintable
  characters* checks run on your pull request instead, so expect to fix a few things
  there. Watch out for non-ASCII characters pasted into the text (accented letters,
  curly quotes, en dashes, `µ`): write them in LaTeX (`\'e`, ``` `` '' ```, `--`, `$\mu$`).
- Keep an eye on the page count in Overleaf's PDF: **10 pages** for an invited talk,
  **4 pages** for everything else, references included.

#### O4. Get your files out of Overleaf

In Overleaf, open **Menu** → **Download** → **Source**. You get a zip of the project's
files (without the PDF); unzip it.

#### O5. Submit

- **Without git**: follow [route B](#route-b-in-the-browser-only-no-git), and in
  [B2](#b2-upload-your-files-into-your-folder) upload only your `YOURPID.tex`,
  `YOURPID.bib`, figures and `makedefs` from the unzipped download, and delete the
  `example.*` figures.
- **With git**: follow [route A](#route-a-with-git-on-your-computer-recommended) to
  A3, copy the same files from the download into `papers/YOURPID/`, delete the
  `example.*` figures, and carry on from [A5](#a5-build-and-check-it).

#### Changes after you've opened the pull request

Keep editing in Overleaf. When you're ready, download the source again (O4) and upload
the changed files to the **same** `YOURPID` branch of your fork: on your fork, switch to
the `YOURPID` branch with the branch menu at the top left, go to `papers/YOURPID/`, then
**Add file** → **Upload files**, and choose **Commit directly to the `YOURPID` branch**.
The pull request updates by itself. Don't open a new one.

If someone (an editor, or a fix from the *Unprintable characters* check) changes your
files in the pull request, make the same change in Overleaf too. Otherwise your next
upload undoes it.

### After you open the pull request

Within a few minutes, four checks run on your paper, each with its own status at the
bottom of the pull request:

| Check | What it does | When it fails |
|---|---|---|
| *From a fork* | checks the pull request comes from your fork | it comes from a branch in this repository; see [Fixing common mistakes](#fixing-common-mistakes) |
| *Build papers* | builds the PDF with [latex-action](https://github.com/xu-cheng/latex-action) (latexmk with a full TeX Live) | a LaTeX error; the error lines are in the job log |
| *PaperCheck* | the ADASS PaperCheck, as `make check`, including its TexScanner parse of the `.tex` file | PaperCheck reports problems; the job log lists them |
| *Unprintable characters* | FixUnprintable, as `make fix` | non-ASCII characters; the log shows the replacements, and the fixed `.tex` is in the run's artifacts |

Click **Details** next to a check to see its log. A comment on the pull request links the
built PDF: check it looks the way you expect.

The checks on a first pull request may wait for an editor to approve them; that's
normal.

**To make changes**, whether to fix a check or to answer the editors: change the files
in the **same branch** of your fork, and push again (route A: commit, then `git push`;
route B: upload to the `YOURPID` branch). The pull request updates by itself and the
checks run again. **Don't open a new pull request**, and don't close the old one.

When the editors are happy, they merge your pull request. You're done; you can delete
your fork afterwards if you like.

### What to put in your folder

Change these, in `papers/YOURPID/`:

| File | What to do |
|---|---|
| `YOURPID.tex` | your paper. It starts as the standard ADASS template, which also explains the formatting rules; replace its example content with your paper |
| `YOURPID.bib` | your references. It starts as the template's example references; replace them with only the ones your paper cites |
| figures | name them `YOURPID_f1.eps`, `YOURPID_f2.png`, and so on |
| `example.*` | delete the template's example figures once your paper no longer uses them |
| `makedefs` | check your surname and email |

Don't change or add anything else: not the `Makefile`, the style files
(`asp20*.sty`, `.bst`), the Python scripts or the other template files. Don't commit
the PDF or other build output, and **don't commit your signed copyright form**: it
carries your signature, so send it to the editors instead.

### Fixing common mistakes

**`git status` or *Files changed* shows files outside `papers/YOURPID/`.** Put each one
back as it is in this repository. With git, first add this repository as a remote called
`upstream` (once; use the URL from the green **Code** button on *this* page, not your
fork's):

```
git remote add upstream <this repository's URL>
git fetch upstream
```

Then, for each file that shouldn't have changed:

```
git restore --source=upstream/main --staged --worktree path/to/the/file
```

A file you added by mistake, which isn't in this repository, is removed with
`git rm --cached path/to/the/file` (add it to your own `.git/info/exclude` if you want
to keep it locally). Commit and push; the pull request updates.

In the browser, open each wrong file on your branch and delete it, or ask the editors in
the pull request to tidy it for you.

**The *From a fork* check fails.** Your pull request comes from a branch in this
repository, not from your fork. Fork the repository ([A1](#a1-fork-this-repository)),
push your branch to the fork (with git: `git remote add fork <your fork's URL>`, then
`git push -u fork YOURPID`), and open a new pull request from it as in
[A8](#a8-open-the-pull-request). Then close the old pull request, with a link to the new
one.

**I committed to `main` instead of a branch.** That's fine as long as only your folder
changed: open the pull request from your fork's `main` (in [A8](#a8-open-the-pull-request),
**compare** is then `main`). Use a separate branch for any second paper.

**My pull request shows other people's papers, or hundreds of changes.** Your fork is
out of date with this repository, or the pull request is the wrong way round. Check the
four boxes in [A8](#a8-open-the-pull-request) step 2. To bring your fork up to date, on
your fork's page click **Sync fork** → **Update branch**; then, with git,
`git switch YOURPID && git pull origin main && git push`.

**A check warns *This PR touches more than one paper*.** You changed files in two
`papers/` folders. Undo the changes to the folder that isn't yours, as above.

**I have two papers.** Make a separate branch for each, named after each PID
(`git switch main`, then `git switch -c` and your second PID), and open a separate pull
request from each.

**Something else.** Ask in your pull request, or contact the editors. Don't worry about
breaking anything: nothing reaches this repository until an editor merges it.

## For editors

- `bash ci/build_papers.sh C101 P203` builds specific papers locally with `make`. With no
  arguments it builds every paper. GitHub Actions uses latex-action instead; it runs the
  same `pdflatex`/`bibtex` passes through latexmk.
- Running any of the three workflows manually runs it on the whole set. They share the
  `find-papers.yml` workflow, which picks the papers a PR changed.
- This repo was generated by `make_author_templates.py` in the main
  ADASSProceedings2026 repo. When all PRs are merged, copy `papers/` back there:
  ```
  git clean -fdX papers/      # drop ignored build products first
  rsync -av papers/ ../ADASSProceedings2026/papers/
  ```
  Then continue with `pmake inc rsync` and `make asp1` / `make book0` as described in its `INGESTION.md`.

## Papers

<!-- papers-table:start -->
### 1. AI as a tool for data discovery and data management

| Authors | Type | Title | PID |
|---------|------|-------|-----|
| Example, Ben; Carla Coauthor | Contributed Talk | Test contributed talk with two speakers | [C101](papers/C101/) |
| Sample, Dana Van Der | Contributed Talk | Test second contributed talk in the same track | [C102](papers/C102/) |
| Testperson, Ada | Invited Talk | Test invited talk | [I101](papers/I101/) |

### 2. AI as tool for scientific discovery

| Authors | Type | Title | PID |
|---------|------|-------|-----|
| Müller-Testa, Eve | Contributed Talk | Test contributed talk with an accented hyphenated name | [C201](papers/C201/) |

### 3. AI as tool for software engineering

| Authors | Type | Title | PID |
|---------|------|-------|-----|
| Placeholder, Finn | Poster | Test poster that was never formally accepted | [P301](papers/P301/) |

### 4. Building and operating science platforms and workflows in the Petabyte Era

| Authors | Type | Title | PID |
|---------|------|-------|-----|
| Dummy, Gita | Featured Poster | Test featured poster | [P401](papers/P401/) |

### 5. Usability, accessibility and security in astronomy software

| Authors | Type | Title | PID |
|---------|------|-------|-----|
| Mock, Hugo | Focus Demo | Test focus demo | [F501](papers/F501/) |

### 6. The art of collaboration in astronomy software development

| Authors | Type | Title | PID |
|---------|------|-------|-----|
| Fixture, Iris | BoF | Test BoF | [B601](papers/B601/) |

### 7. Global data management and lifecycle in the exascale era

| Authors | Type | Title | PID |
|---------|------|-------|-----|
| Stub, Jon | Tutorial | Test tutorial | [T701](papers/T701/) |

### 8. Topical Computing, Software and Algorithms

| Authors | Type | Title | PID |
|---------|------|-------|-----|
| Sandbox, Lee | Poster | Test poster in the last track | [P802](papers/P802/) |
| Trial, Kim | Featured Poster | Test featured poster in the last track | [P801](papers/P801/) |
<!-- papers-table:end -->
