# ADASS 2026 Proceedings — paper submissions

Every accepted contribution has a ready-made folder in `papers/<PID>/`, named after its
paper ID (for example `papers/C101/`). Your PID is in your acceptance email. The PID
format is `XNNN`: `X` is the presentation type (I, C, P, F, B, T), the first digit is the
track number, and the last two digits number the papers within that track.

## For authors

1. Fork this repository, or create a branch if you have write access.
2. Edit **only** your own folder, `papers/<PID>/`:
   - `<PID>.tex`: your paper. Your name and PID are already filled in.
   - `<PID>.bib`: your references. Uncomment `\bibliography{<PID>}` in the `.tex` file once you cite something.
   - figures: name them `<PID>_f1.eps`, `<PID>_f2.png`, and so on.
   - `makedefs`: check your surname and email.
3. Build and check it locally with a TeX Live installation:
   ```
   cd papers/<PID>
   make pdf      # builds <PID>.pdf
   make check    # runs the ADASS PaperCheck
   ```
4. Commit your `.tex`, `.bib`, figures and `makedefs`. Don't commit the PDF or other build
   output; `.gitignore` takes care of that.
5. Open a pull request titled `<PID>: <your paper title>`.

The CI builds your paper on every push to the PR, in its own `papers/<PID>/` directory,
using [latex-action](https://github.com/xu-cheng/latex-action) (latexmk with a full TeX
Live). A LaTeX error fails the check, and the error lines are shown in the job log.
PaperCheck problems show up as warnings for the editors to look at. You can download the
built PDF from the run's artifacts (one per paper), and the editors review the paper in
the PR.

If you'd rather use Overleaf, upload the contents of your `papers/<PID>/` folder as a new
project. It compiles there as it is. Copy your changes back into the folder for the PR.

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
