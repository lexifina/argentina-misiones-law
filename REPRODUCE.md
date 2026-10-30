# How this repository was made (Misiones)

This file is written by the build on 2026-10-30, the day the source data was retrieved.

## Sources

| Source | Address | Retrieved | Licence |
| --- | --- | --- | --- |
| Cámara de Representantes de la Provincia de Misiones (www.diputadosmisiones.gov.ar) | <https://www.diputadosmisiones.gov.ar/nuevo/documentos> | 2026-10-30 | Official legal texts of the province, published by its government for public consultation. Argentina's copyright law (Ley 11.723) has no express exclusion for them; laws are public acts of government, binding on everyone once officially published (Código Civil y Comercial, art. 5). The source states no restriction on reuse. Reproduced with attribution, following the official text. |

Every word of law in this repository comes from these sources. Lexifina reads them and records each act's dated versions, and the laws that made each change, in one corpus file. This repository is built from that file.

## What is in it

| Act | Title | Versions | Span |
| --- | --- | ---: | --- |
| `constitucion` | Constitución de la Provincia de Misiones | 1 | 2022-03-11 to 2022-03-11 |

The build made 1 commits:

| Commits | Kind |
| ---: | --- |
| 1 | first version of an act |
| 0 | one law on its in-force day |
| 0 | changes no amendment note explains, credited to the publisher |

Other counts:
- 0 commits on the branch `futuro`: laws not yet in force on 2026-10-30.
- 0 commits dated 1 January 1970: in force before 1970, with the real day in their `In-force` trailer.
- 1 laws in the record.
- 1 tags.

## Dates

Each commit is dated at noon (America/Argentina/Cordoba) on the day the change took effect. The other dates, enacted and published, are trailers.

When a law gives no date of its own, the default rule applies: Código Civil y Comercial de la Nación, art. 5: "Las leyes rigen después del octavo día de su publicación oficial, o desde el día que ellas determinen", counted under art. 6 (the day of publication is excluded), so a law without its own vigencia clause is in force from the ninth day after its publication in the provincial Boletín Oficial (before 1 August 2015, Código Civil art. 2 as replaced by Ley 16.504, to the same effect). A law's own vigencia clause overrides the rule. https://servicios.infoleg.gob.ar/infolegInternet/anexos/235000-239999/235975/texact.htm

## How the history is built

`tools/build.py` turns the corpus into this history in one pass: one commit per law, on the day it took effect. The same corpus always gives the same commit hashes. `tools/check_repo.py` reads every version back from git and compares it with the corpus. `tools/on.py` shows the law as it stood on any date. The corpus format is described in `tools/SCHEMA.md`.

- Corpus: sha256 `96c406d5bfd755ef868999aa97ee4f8b19e966ce235c490afaa6a8269a6192f2` (131177 bytes).
- Builder blob hashes (`git hash-object`): `build.py` `a97ff7ea62c3c7595c5668a297d533da0b74373c`, `check.py` `3e59cb6f05eccb94a9ec14431a7f6781221e83ef`, `on.py` `644a6c0857fbcc72562032b58d57aa113fee0641`.
- Python 3.12.10; git version 2.46.0.windows.1.

## Checks

1 versions of 1 acts read back from git on the day each took effect and on the day before: 0 mismatches. Trailers: 0 commits whose trailers git cannot parse. Health: 0 merge commits on main, 0 commit dates that go backwards, 0 commits dated after the build.

No second build of this corpus has been compared yet.

## Decisions made by hand

- The constitution is the text the Cámara publishes: the 1958 Constitución with its amendments in place (Ley 254, Ley 2604, Ley 3651, Ley IV - Nº 60; the source's footnotes give each replaced wording). Earlier consolidated wordings are not published as texts, so it is shown as its current text only (the oldest version available), dated by the Cámara's edition, 11 March 2022 (the PDF's creation date). The norm's record dates the constitution 21 April 1958, the day of its sanción, from which its own transitional art. 11 makes it rule; the source gives no Boletín Oficial date.
- Units: the heading (encabezado: the edition's title pages, the list of the Convención's members, the enacting formula and the headings before Artículo 1) and one file per article, holding the article and everything printed after it up to the next article (section headings, the source's footnotes with the replaced wording, the running heads and page numbers). The Cláusulas transitorias are numbered from Artículo 1 again and are filed as art-001-dup2 and so on; the Reglamento of 1810 inserted by the Convención follows the last of them. "Artículo. 50.-" (so printed) is filed as article 50. Nothing is dropped. One paragraph per line, spacing normalised.
- The PDF is read in its content order (PyMuPDF), and its letters and digits are checked against poppler's pdftotext -raw, which reads the same order.

## What AI did and did not do

The scripts that read the sources and build this repository were written by Claude Code running Claude Opus 5.5 (`claude-opus-5-5`) under Lexifina's direction.

No model wrote, translated or corrected legal text. No model runs at build time. Every word of law in this repository comes from the official sources above.

The commit messages are written by `build.py` from the source data.

Model use at data-build time:
- A model (Claude) wrote the fetch and parse code and chose which norms to include; it wrote no law text. Every word of law comes from the provincial source's own texts.
