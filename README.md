# Finance Lessons (live interactive decks)

Students open the deck in a browser and follow the instructor live. They can change any number to explore, then press **Rejoin live** to go back to the instructor's view. No sign-in is needed for students.

- `index.html`: the list of lessons
- `lesson3/index.html`: Lesson 3, Moving money through time (one self-contained page)
- `firestore.rules`: who may read and write the live state

## One-time setup

### 1. Presenter account
The presenter account is `kammain@gmail.com`. It is already set in each lesson's `index.html` (`PRESENTER_EMAILS`) and in `firestore.rules`. To add a co-instructor, add their address to the list in both files.

### 2. Firebase
1. **Firestore rules:** Firebase console → Build → Firestore Database → **Rules** tab. Replace everything with the contents of `firestore.rules`, then click **Publish**.
2. **Google sign-in:** Build → Authentication → Sign-in method → enable **Google**.
3. **Authorized domain:** Authentication → Settings → **Authorized domains** → Add domain → `kammain.github.io`. Without this, the sign-in popup is refused.

### 3. GitHub Pages
Repository → Settings → Pages → Source: **Deploy from a branch**, Branch: `main`, folder `/ (root)` → Save. The Pages screen shows the site address after a minute.

## In class

| Who | Link |
|---|---|
| Students | `https://kammain.github.io/Finance-Lessons/lesson3/` |
| You (presenter) | `https://kammain.github.io/Finance-Lessons/lesson3/?present` |

On the presenter link, click **Sign in to present** in the bottom bar. Once you're signed in, your slide and numbers broadcast to everyone. Use **Pause broadcast** to try something privately.

A specific slide can be linked with `#slide-12`.

## Adding more lessons
Copy `lesson3/` to a new folder such as `lesson4/` and change `LIVE_DOC = ["live", "lesson3"]` to `["live", "lesson4"]`, so each deck has its own live state. Then add a link to it in the top-level `index.html`. The rules already cover every `live/...` document.

## Free-tier note
Firestore's free tier allows 50,000 reads a day. Each change you broadcast is one read per student watching. A 60-student class with a few hundred changes per lecture stays well within the limit.

## Customizing the slides

Each slide is one `<section class="slide">` block in `lesson3/index.html`, in the same order as the deck. Search for a slide's title to find it.

**Number boxes instead of sliders**
- Whole deck, for one viewer: click **Hide sliders** in the bottom bar. The browser remembers the choice.
- One slide, for everyone: add `data-ctl="fields"` to that slide's `<section ...>` tag.

**Layout**
- The two-column area of a slide is `<div class="s-body ...">`. Use `wl` for a narrower left column, `wr` for a narrower right column, `one` for a single column, or neither for two equal columns.
- Inside it, each `<div class="col">` is a column. Move blocks (controls `ctls`, formulas `formula`, results `results`, charts `chart`, tables `tw`) between columns or reorder them freely.
- Each input is a line like `<div class="ctl" data-k="an_r"></div>`. Its label, starting value, range and step are set in the `PARAMS` list near the top of the script.

Or describe the change you want to Claude and point it at this repository.
