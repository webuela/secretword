# Hidden Words

Find real words hidden inside the letters of any text — a poem, a song, a quote, a letter, or a plain paragraph. Collect one word from each text and turn your collection into a proverb.

A single self-contained HTML file. No build step, no dependencies, no backend. Works offline (falls back to system fonts).

## How it works

1. Paste any text and press **Analyze text**.
2. The app gathers all letters of the text — ignoring spaces, punctuation and case — and shows them as letter tiles with counts.
3. It then checks its built-in dictionary and lists every real word that can be built from those letters. Hover a word to light up the tiles it uses.
4. Add a word to your **Collection**: it is stored with the number of the current text (Text №1, №2, …).
5. When you have two or more words in one language, press **Make a proverb** to turn the collection into a saying ("Where there is LOVE, there is DREAM").

### Modes

- **Free** — a word only needs each of its letters to *appear* in the text.
- **Strict** — letter counts matter (classic anagram rule): the word `letter` needs two `t`s and two `e`s in the text.

### Languages

- **Word languages:** English, Russian, Spanish (priority), plus French, German, Italian, Portuguese.
- **Interface languages:** English (default), Russian, Spanish.
- **Cross-script:** Cyrillic ⇄ Latin transliteration is automatic, so a Russian poem can yield Spanish words and vice versa.
- **Translations** are shown only when the word language differs from the interface language (useful for language learners, invisible for native use).

## Run locally

Just open `index.html` in a browser. That's it.

## Deploy on GitHub Pages

1. Create a repository and upload `index.html` (and this `README.md`).
2. Go to **Settings → Pages**.
3. Under *Build and deployment*, choose **Deploy from a branch**, select the `main` branch and the `/ (root)` folder, then **Save**.
4. Your app will be live at `https://<username>.github.io/<repository>/`.

## Extending the dictionaries

All dictionaries live at the top of the `<script>` block in `index.html` as plain arrays of `["word", "gloss"]` pairs:

```js
const DICT_ES = [
  ["amor", "love / любовь"],
  ["vida", "life / жизнь"],
  // add yours here
];
```

Rules of thumb:

- Words are lowercase; accents are allowed (they are folded for matching but shown as written).
- Gloss format is `"english / русский"` for most languages; English words are glossed in Russian and Russian words in English. A gloss may be omitted (`["word", ""]`).
- The gloss is only displayed when the word language differs from the interface language.

## Adding a whole new language

1. Create a dictionary array, e.g. `const DICT_NL = [ ["liefde", "love / любовь"], … ];`
2. Register it in the `LANGS` object: `nl:{name:"Nederlands", dict:DICT_NL}`.
3. Add an `<option value="nl">Nederlands</option>` to the word-language `<select>`.
4. (Optional) Add proverb templates for it in the `TEMPLATES` object.

If the language uses extra Latin letters, check the `foldChar` function — by default diacritics are folded to their base letters (Spanish `ñ` is kept as a distinct letter as an example of how to preserve one).

## License

This project is licensed under the **GNU General Public License v3.0**.

The easiest way to add the official license text to your repository: on GitHub click **Add file → Create new file**, name it `LICENSE`, then click **Choose a license template**, pick **GNU General Public License v3.0** and commit. GitHub inserts the exact official text and will show the license badge on the repo page.

This program is distributed WITHOUT ANY WARRANTY; see the license for details.
