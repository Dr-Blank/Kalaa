# Kala | Dr. Blank's Art Corner - Hugo Site

This repository contains the source code and content for the Kala website ([https://kala.drblank.dev/](https://kala.drblank.dev/)), a personal collection focusing on Gujarati lyrics (especially Garba), discussions, and potentially film reviews in the future.

Built with [Hugo](https://gohugo.io/) and the [PaperMod](https://github.com/adityatelange/hugo-PaperMod) theme.

## Quick Start / Local Development

1. **Clone the repository:**

    ```bash
    git clone <your-repo-url>
    cd <your-repo-folder>
    ```

2. **Initialize/Update Theme Submodule:**

    ```bash
    git submodule update --init --recursive
    ```

3. **Run Hugo Server:**

    ```bash
    hugo server -D
    ```

    * `-D` includes draft posts.
    * Open your browser to `http://localhost:1313/` (or the address Hugo indicates).

## Creating New Content

### Adding New Lyrics Post

Use the Hugo CLI and the `lyrics` archetype to ensure structure and necessary front matter. **Always use `/index.md` at the end to create a Page Bundle folder.**

1. **Run the command:**

    ```bash
    hugo new lyrics/your-song-title-here/index.md
    ```

    * Replace `your-song-title-here` with a descriptive slug (use hyphens).
    * This creates `content/lyrics/your-song-title-here/index.md`.

2. **Edit the new file (`content/lyrics/your-song-title-here/index.md`):**
    * **Front Matter:**
        * Fill in `authors: ["Lyricist Name"]`.
        * Adjust `genres: ["Garba"]` if needed.
        * Add relevant `tags: ["Tag1", "Tag2"]`.
        * Set `draft: false` when ready to publish.
    * **Content:** Fill in the sections (`## Lyrics`, `## Explanation`, etc.) as prompted by the comments in the archetype template.
    * **Word Meanings:** Use the `<abbr title="Your definition here">GujaratiWord</abbr>` tag for hover definitions (see below).

### Adding a Cover Image

1. Generate or find your image (e.g., `cover.jpg`, `my-image.png`).
2. Place the image file **inside the same folder** as the `index.md` file (e.g., `content/lyrics/your-song-title-here/cover.jpg`).
3. In the `index.md` front matter, **uncomment and edit** the `cover:` section:

    ```yaml
    cover:
      image: "cover.jpg" # Or your image filename
      alt: "Description of the image"
      caption: "Optional caption"
      relative: true # Important!
    ```

### Adding Author/Genre Information (Taxonomies)

* Hugo automatically creates lists based on the `authors` and `genres` arrays in your front matter.
* You can browse all authors at `/authors/` and all genres at `/genres/`.
* Clicking a specific author/genre link (e.g., from the menu or on a post) takes you to `/authors/author-name/` or `/genres/genre-name/`, listing all associated posts.

### (Future) Adding New Reviews

1. **Run the command:**

    ```bash
    hugo new reviews/film-or-book-title/index.md
    ```

    * (Assuming you created `archetypes/reviews.md` and want Page Bundles for reviews too. If not, use `.md` instead of `/index.md`).
2. **Edit the new file:** Fill in front matter and content sections.

## Taxonomy: Genres & Tags

To maintain consistency, please try to use the genres and tags listed below when creating new content. Choose 1-2 genres and multiple relevant tags per post.

The `archetypes/lyrics.md` file includes these lists as comments for easy selection when running `hugo new lyrics/...`.

**Note on Emojis:** Emojis are included for visual appeal in the list. Using them *within* the tag/genre value in the front matter (e.g., `tags: ["💕 Love / Romance"]`) is possible but will affect the generated URL (e.g., `/tags/💕-love-romance/`). You can choose to omit the emoji from the value if you prefer cleaner URLs.

### Preferred Genres

* `💃 Garba`
* `🕺 Raas`
* `🙏 Bhajan / Devotional`
* `🌾 Folk Song / Lok Geet`
* `🎶 Sugam Sangeet`
* `🎬 Film Song / Filmi Geet`
* `👶 Children's Song / Bal Geet`
* `🌙 Lullaby / Halardu`

### Preferred Tags

* **Garba Specific:**
  * `2️⃣ 2-Taali Garba`
  * `3️⃣ 3-Taali Garba`
  * `👏 Taali Raas`
  * `🪵 Dandiya Raas`
  * `☀️ Prabhatiya`
  * `✨ Navratri Special`
* **Themes/Moods:**
  * `💕 Love / Romance`
  * `💔 Heartbreak / Sadness`
  * `🌱 Life / Philosophy`
  * `😊 Joyful / Celebratory`
  * `🤔 Reflective / Thoughtful`
  * `💪 Inspirational / Motivational`
  * `😂 Humorous / Playful`
* **Occasions:**
  * `🎉 Wedding / Lagna Geet`
  * `🎊 Festival Special`
  * `🌧️ Monsoon / Rainy Season`
* **Other:**
  * `📜 Traditional / Paramparik`
  * `🗣️ Narrative / Story Song`
  * `🙏 Prayer / Prarthana`
  * `🏞️ Nature Themed`

If you feel a new genre or tag is essential and will be reused, consider adding it to this list in the README and potentially updating the archetype. Try to avoid creating too many unique tags for one-off posts.
****

## Updating the Site & Theme

* **Update Content:** Pull latest changes if collaborating or using multiple machines: `git pull`.
* **Update PaperMod Theme:**

    ```bash
    cd themes/PaperMod
    git pull origin master # Or the branch you're using
    cd ../..
    ```

* **Update Hugo:** Check the [Hugo Releases](https://github.com/gohugoio/hugo/releases) page and follow instructions for your OS. Check for breaking changes before updating.

### Important: Custom Layouts

Remember that we have created a custom layout override to enable the automatic Glossary generation feature:

* **File:** `layouts/_default/single.html`
* **Purpose:** Copied from the PaperMod theme and modified to include code that renders a glossary based on the `{{< abbr "Term" "Definition" >}}` shortcode used in content files.

**When switching themes, this custom `single.html` file will likely need attention:**

1. The new theme will have its own `layouts/_default/single.html` (or equivalent) structure.
2. Our custom glossary code (the part added *after* `{{ .Content }}`) needs to be **re-integrated** into the *new* theme's template structure.
3. **Action:** You will need to copy the `single.html` from the *new* theme into your `layouts/_default/` folder and carefully add the glossary generation code block again in the appropriate place (usually after the main content rendering).

### Switching to a Different Theme

If you decide to change the Hugo theme in the future, follow these general steps:

1. **Choose a New Theme:** Browse the official [Hugo Themes](https://themes.gohugo.io/) site.
2. **Read Theme Documentation:** **Crucially, read the documentation for the *new* theme.** Pay close attention to:
    * Installation instructions (usually involves Git submodules or Go modules).
    * Required configuration settings (in `hugo.yaml`).
    * Available theme parameters (`params:` block in `hugo.yaml`).
    * Any specific content structures or front matter fields it expects.
3. **Add the New Theme:**
    * **Using Git Submodule (Common):**

        ```bash
        # Example for a theme named 'NewTheme'
        git submodule add https://github.com/user/NewTheme.git themes/NewTheme
        git submodule update --init --recursive
        ```

    * **Using Go Modules (Modern):** Follow the theme's instructions for adding it to your `go.mod` file and running `hugo mod get ...`.
    * **Manual Download:** Download the theme files and place them in the `themes/` directory (e.g., `themes/NewTheme/`).
4. **Update `hugo.yaml`:** Change the `theme:` line to the name of the new theme's directory:

    ```yaml
    # In hugo.yaml
    theme: "NewTheme" # Replace PaperMod with the folder name of the new theme
    ```

5. **Adapt Configuration (`hugo.yaml`):**
    * **Review `params:`:** Go through the `params:` section in your `hugo.yaml`. Most of these are specific to PaperMod (e.g., `ShowReadingTime`, `homeInfoParams`). The new theme will have *different* parameters. **Remove or comment out old PaperMod params** and add the params required/supported by the new theme, according to its documentation.
    * **Review Base Config:** Check if the new theme requires any other specific top-level configuration settings.
    * **Menus (`menu:`):** Your main menu structure should generally work, but check if the new theme styles or uses menus differently.
    * **Taxonomies (`taxonomies:`):** These are core Hugo features and should work fine.
6. **Adapt Custom Layouts:** As mentioned above, **re-apply the glossary logic** to the new theme's `single.html` template copied into your `layouts/_default/single.html`. Check if the new theme uses different CSS classes or structure that might affect the glossary's appearance.
7. **Test Thoroughly:** Run `hugo server -D` and check multiple pages (homepage, list pages, single posts) to ensure everything looks and works as expected. Check browser developer tools for errors.

### Handling Theme-Specific Parameters (Alternative Configuration Structure)

While keeping all params in `hugo.yaml` works, a more organized approach, especially if you experiment with themes, is to use Hugo's [Configuration Directory](https://gohugo.io/getting-started/configuration/#configuration-directory).

You could split your configuration like this:

* `config/_default/config.yaml`: Core settings (baseURL, languageCode, title, theme, taxonomies, outputs, etc.)
* `config/_default/params.yaml`: **Site-wide** parameters not specific to any theme.
* `config/_default/menus.yaml`: Menu definitions.
* `config/_default/markup.yaml`: Markup settings.
* `config/<ThemeName>/params.yaml`: **Theme-specific** parameters. For example:
  * `config/PaperMod/params.yaml`: Contains only params specific to PaperMod.
  * `config/NewTheme/params.yaml`: Contains only params specific to NewTheme.

When you switch themes by changing `theme: "NewTheme"` in `config/_default/config.yaml`, Hugo automatically merges the settings, prioritizing the theme-specific params file (`config/NewTheme/params.yaml`) over the default one (`config/_default/params.yaml`) if there are overlaps.

This keeps theme-specific settings cleanly separated. To implement this:

1. Create the `config/_default/` directory.
2. Move relevant sections from your main `hugo.yaml` into `config/_default/config.yaml`, `config/_default/params.yaml`, `config/_default/menus.yaml`.
3. Create `config/PaperMod/` and move PaperMod-specific params into `config/PaperMod/params.yaml`.
4. Your root `hugo.yaml` might become empty or only contain settings for different *environments* (like development vs. production).

This is a more advanced setup but offers better organization if you anticipate managing multiple themes or complex configurations. Start with the single `hugo.yaml` and consider splitting later if needed.

## Deployment

Deployment depends on your hosting provider (e.g., Netlify, Vercel, GitHub Pages, Cloudflare Pages). Typically:

1. Commit and push your changes to your Git repository.
2. The hosting service automatically detects the push, builds the Hugo site (`hugo` command), and deploys the output from the `public/` folder.

## Notes & Future Ideas

* **Author Linking:** Taxonomies listed on posts *should* be links. If not, check theme config/updates (see point 4 below).
* **Word Hover:** Using `<abbr title="Definition">Word</abbr>` tag in Markdown for simple hover definitions.
* **Script Toggle:** Postponed due to complexity. Revisit later if needed.
* **Author Bios:** Consider a separate `content/author-bios/` section and link manually from relevant posts or create custom taxonomy term layouts later.
