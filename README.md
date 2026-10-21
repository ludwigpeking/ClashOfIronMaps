# Clash of Iron Maps

Animated track maps of four naval battles of the steam-and-steel age, reconstructed from the official track charts and reports:

| Battle | Date | Link |
|---|---|---|
| Yalu (Battle of the Yellow Sea) | 17 September 1894 | `#yalu` |
| Tsushima | 27–28 May 1905 | `#tsushima` |
| Jutland | 31 May – 1 June 1916 | `#jutland` |
| Guadalcanal (battleship night action) | 14–15 November 1942 | `#guadalcanal` |

Every ship sails her reconstructed track minute by minute, with gunfire, torpedoes, hits, sinkings and the story of the battle beside the map. Where the charts survive, the original scans can be laid underneath the tracks so you can compare the reconstruction against them.

**Open it:** https://ludwigpeking.github.io/ClashOfIronMaps/ (pick a battle in the menu, or add `#tsushima` etc. to the address).

The maps come from a game and documentary project about these battles. They are published here so anyone can check, reuse or correct them.

## Using the map

- **Play** runs the battle clock. Drag the time bar to jump, and use **Speed** to change the pace.
- Drag to pan, and use the wheel or a pinch to zoom. Hulls are drawn to scale when you zoom in.
- Click a ship to see her track, her marks on the official charts and how far she sits from them.
- **Chart** lays a scanned track chart under the map, and **Opacity** fades it.
- **Chart marks** are positions read off the official charts. **Clashes** lists any places where two hulls touch. **Action** shows gunfire and torpedoes.
- **Trail** sets how much of each track is drawn behind the ship. **Names** shows ship names in English or Chinese.
- **Edit pins** and the **Story editor** (the <kbd>`</kbd> key) are the project's editing tools. Your changes are saved in your own browser only.

## Running it locally

It is a single static page with no build step. The browser will not load the data files from `file://`, so serve the folder:

```
python -m http.server
```

Then open http://127.0.0.1:8000/. VS Code's Live Server also works.

## Layout

```
index.html            the whole app (plain HTML, CSS and JavaScript, no dependencies)
data/<battle>/        jutland, tsushima, yalu, guadalcanal
  battle.json         clock, days, sides, first view, weapon reaches of the period
  tracks.json         every ship's track at half-minute steps
  story.json          the story events (+ story_i18n.json, translations)
  events.json         hits and fires from the charts
  clashes.json        hull contacts
  coast.json          land, shoal water, depth line, place names
  marks.json          positions read off the official charts
  charts.json         chart scans and how they lie on the map
  charts/             the chart scans
  traced.json         night tracks traced from the charts (Jutland)
```

## Sources and credits

- **Tsushima:** track charts No.1–48 of the Japanese Navy General Staff's secret official history 『極秘 明治三十七・八年海戦史』 (第二部 戦紀 巻二 付表付図). These are held by the National Institute for Defense Studies, Ministry of Defense, Japan, and provided by JACAR (Japan Center for Asian Historical Records), Ref. C05110095600. The scans are in `data/tsushima/charts/`, with file names that give the JACAR reference codes.
- **Jutland:**
  - The Admiralty's *Battle of Jutland: Official Despatches* (1920), plates 1–12, from the Library of Congress, *Plans of the Battle of Jutland* (https://www.loc.gov/item/2015588079/).
  - The Harper Record track charts (1919) and the Groos charts from *Der Krieg in der Nordsee*, vol. V (1925), from the scans at jutland1916.com.
- **Guadalcanal:** S. E. Morison, *History of United States Naval Operations in World War II*, vol. V, the "Battleship Night Action 14–15 Nov 1942" chart. This is supplemented by the US action reports and the Japanese battle reports held by JACAR.
- **Coastlines:** Natural Earth 1:10m land (public domain). The Jutland depth lines are from EMODnet Bathymetry (CC BY 4.0).

The 1894–1925 charts and the 1940s US government material are in the public domain in the United States. Please credit the holding archives when you reuse the scans.

## Licence

- The code (`index.html`) is under the MIT License (see `LICENSE`).
- The reconstructed tracks, marks, clash lists and story texts in `data/` are © Qian Li and licensed under CC BY 4.0 (https://creativecommons.org/licenses/by/4.0/). Please credit "Clash of Iron Maps".
- The third-party material listed above keeps its own terms.

Corrections are welcome: open an issue with the ship, the minute and your source.
