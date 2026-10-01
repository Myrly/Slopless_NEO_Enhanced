# Slopless
Just getting rid of all the ai features because I dislike them. For my personal use initially but if anyone wants to use it, feel free to do so.

# NEO Enhanced

justsomerandomshit's own version of [NEO](https://github.com/hughhowey/neo), the writing app by Hugh Howey. The rest of this README is his, with a few bits changed to fit this version. All the credit for NEO goes to him.

## What's different here

- **Text formatting.** Underline, strikethrough, headings, block quotes, and bulleted or numbered lists, on top of the bold and italic NEO already had. They're all in the Format menu with shortcuts, and Markdown works as you type. More on that under Formatting below.
- **Paste keeps formatting.** Paste from Google Docs, Word or a web page and headings, lists, quotes, bold, italic, underline and strikethrough come along. Paste Markdown (from a notes app, a code editor, or a chatbot) and it gets turned into the same formatting instead of showing the asterisks and hashes.
- **Copying a chapter copies its heading.** Select from the top of a chapter (or just press Cmd+A in it) and copy, and "Chapter 3 — Title" comes along above the text. Edit → Copy Chapter Headings turns this off.
- **Save cover as image.** Right-click a book on the shelf and pick Save cover as image… to get its cover as a full-size JPEG (1600×2560), title and author included, just like it looks on the shelf. If you gave the book your own cover image, you get that image back as it is.
- **Zooming keeps your place.** Pinching, Ctrl+scrolling, the zoom buttons and the text size shortcuts no longer throw you to a different part of the chapter. Also sent to the original as [hughhowey/neo#132](https://github.com/hughhowey/neo/pull/132).
- **No automatic updates.** This version never checks for new releases or installs them, so an official NEO update can't replace it. The Check for Update menu item is gone too.
- **Shelf fix.** After the NEO Pocket commit (285c081), the desktop app opened to an empty window with no shelf. That's fixed here, and the same fix is now in the original too ([hughhowey/neo#130](https://github.com/hughhowey/neo/pull/130)).

It uses the same `~/Documents/NEO Library` folder as the original NEO, so your books show up in both. Just don't run the two at once.

---

**A distraction-free word processor for authors, by a wannabe author.**

NEO understands from the moment you install it that you are writing *books* and nothing else. No bloat, no distractions, with manuscripts that look like books as you write them.

NEO runs locally. WIPs are saved in plain files on your disk. No accounts or subscriptions. And it's free!

## Download

There are no ready-made installers for this version, so you build it yourself. On a Mac with Apple silicon it takes a few commands (you need [Node.js](https://nodejs.org)):

```
git clone https://github.com/justsomerandomshit/NEO_Enhanced.git
cd NEO_Enhanced
npm install
npx electron-builder --mac dir --arm64 -c.mac.notarize=false -c.mac.identity=null
codesign --force --deep --sign - dist/mac-arm64/NEO.app
```

Then drag `dist/mac-arm64/NEO.app` into Applications. On an Intel Mac, swap `--arm64` for `--x64` and `mac-arm64` for `mac`.

If you want the official NEO with installers for Mac, Windows and Linux, get it from the [original Releases page](https://github.com/hughhowey/neo/releases). Your library lives in `~/Documents/NEO Library`; File → Library Folder… moves it anywhere you like.

## Why NEO?

**The bookshelf** 

Your library looks like a bookshelf, not a file list. Labeled shelves you organize however you like — by series, by status, by pen name. Progress bars on the covers show how far you are from your word goals. You can drag-and-drop books anywhere. You can also drag shelves around and put cover art on your titles.

**Just a blank page** 

There's a white page by default or a dark mode (which I now prefer!). Controls fade until you mouse over them. Chapters number and renumber themselves automatically. Drop caps mark chapter openings, because I'm a sucker for drop-caps. Em dashes, true ellipses, and curly quotes sort themselves out as you type. Spellcheck exists only when you invoke it — no more red squiggles mid-sentence triggering your imposter syndrome.

**Enter, Enter, Enter** 

One Enter: new paragraph. Two: a `***` section break. Three: a new chapter. The goal is to KEEP WRITING.

**Formatting** 

Bold, italic, underline and strikethrough, plus headings, block quotes, and bulleted or numbered lists — all under **Format**, all with keyboard shortcuts. Markdown habits work as you type: `*italic*`, `**bold**`, `~~struck~~`, and at the start of a line `# `, `## `, `> `, `- ` or `1. `. Everything carries through to every export.

**Darlings** 

The writing advice is "kill your darlings" — but I say: *keep the bodies*. Drag any beautiful-but-in-the-way passage onto the Darlings tab. It leaves your manuscript but isn't lost. Darlings restore to the exact spot it came from. More like zombies than darlings.

**Placeholders** 

Mid-flow and need a name, a fact, a date? ⌘⇧X drops a mark and a sticky note. The left panel shows a red dot on every chapter that you need to get back to. The right panel will list all these to-do items.

**Outlining for plotters** 

Outline chapters and sections in the Outline tab; section notes appear in the manuscript as gray ghost paragraphs, ready to be overwritten. Pantsers can ignore all of it or learn to draw a freakin' map for the first time. Try it. You might like it!

**Cover Art** 

Every book gets a cover! New books are dressed in a seeded abstract (six art styles, six type templates, typefaces bundled with NEO) so no two stories on the shelf look alike. Once a story passes 1,000 words, NEO can read it and paint an abstract cover from the text. This is a bit more work but totally worth it. Get an OpenAI API key from their website and paste it into **File → Cover Art…**. The art is generated in the background for about a penny a picture. (These are not meant for publication, just writing inspiration!) The API key is stored encrypted in NEO's own settings, never in your library folder. The title and author are always set in real type on top, so the lettering is never left to a gen-AI model. The ↻ on any book re-rolls its type and colors, or paints it again. And you can always switch back and forth from the seeded modern look to the painted variety.

**Goals and momentum** 

Daily word goals, word sprints, and a NaNoWriMo-style progress chart. Needs more testing, but I think it works okay!

**Exports** 

EPUB 3 with a proper table of contents built to KDP's guidelines, Word .docx, PDF, HTML, markdown, and plain text. Email a timestamped PDF snapshot to yourself with a SHA-256 fingerprint of the text in the body. Might come in handy someday.

**Import** 

Bring in existing .docx, .txt, and .md manuscripts; chapters and scene breaks are detected automatically. This is still a bit rough and might require you to tweak things. It will try to grab your title and remove that from the body, and it seems to be working okay.

**Backups** 

Continuous autosave, daily zip backups kept for two weeks, everything stored as plain files. Set up your NEO library folder on your iCloud if you want for extra safety. You can also email copies of your WIP to yourself with a keystroke: ⌘E.

## Your files

Everything lives in `~/Documents/NEO Library` — one folder per book, chapters as readable HTML, metadata as JSON. Open them in your favorite text editor.

## Languages

NEO speaks English, French, Spanish, Portuguese, German, Italian, Dutch and Polish. Pick one under **View → Language**; on first launch NEO follows your system language when it has it. Adding a language is a single file, no programming needed: see [TRANSLATING.md](TRANSLATING.md).

## Building from source (for the eggheads):

Requires [Node.js](https://nodejs.org).

```
git clone https://github.com/justsomerandomshit/NEO_Enhanced.git
cd NEO_Enhanced
npm install
npm start
```

**View → Keyboard Shortcuts…** opens the shortcut reference. You can also press `Cmd+/` on macOS or `Ctrl+/` on Windows and Linux, or use **Help → NEO Shortcuts**.

To build installers: `npm install electron-builder --save-dev`, then `npm run package` (macOS), `npm run package:win` (Windows), or `npm run package:all`. Output lands in `dist/`.

The app is very simple: an Electron shell (`main.js`), a preload bridge (`preload.js`), and a renderer (`app.js` + `styles.css` + `index.html`). If you know JavaScript, you can change NEO. Have at it.

## Roadmap (things I'm dreaming up but may never get to):

Chapter version history · manuscript format for agent submissions (Times New Roman, double-spaced, address block, just to make Kristin Nelson happy) · global end matter that updates every book at once (same for copyright pages, bios, etc).

## Contributing

Issues and pull requests are welcome — see [CONTRIBUTING.md](CONTRIBUTING.md). Fair warning: NEO is opinionated by design, and bloat killed every writing app I've ever tried. If you want complex, try Scrivener. It really is a great application beloved by many! There are so many wonderful writing apps out there! Nobody needs to use this but me.

## License

[MIT](LICENSE) — free to use, free to modify, free to share.

## Philosophy

If you didn't know, I opened up the Silo universe to fan fiction years ago. And not just to put on fan fiction sites, but you can charge money for the things you write and keep every penny of the income! Lots of incredible Silo Stories out there. But readers are forever looking for more.
