# Dictation dictionary and spoken formatting

Issue #26 builds on the existing persistent personal dictionary. Manage explicit
mishearing → spelling pairs in Settings → Dictation. Matching uses Unicode word
boundaries, longest overlapping phrases first, and a single replacement pass.
German compounds are not split. URLs (including custom schemes), email addresses,
backtick code, relative/absolute and Windows paths are protected. No fuzzy,
phonetic matching or ASR boosting is enabled.

Spoken formatting is opt-in and needs an explicit English or German selection;
it does not guess from the ASR automatic-language setting. Punctuation and number
formatting can be enabled separately. Without a selected language, neither runs.

| English command | German command | Result |
|---|---|---|
| insert comma | Komma einfügen | `,` |
| insert full stop | Punkt einfügen | `.` |
| insert question mark | Fragezeichen einfügen | `?` |
| insert exclamation mark | Ausrufezeichen einfügen | `!` |
| insert new line | Zeilenumbruch einfügen | newline |
| insert new paragraph | Absatz einfügen | blank line |
| number zero … number twelve | Zahl null … Zahl zwölf | `0` … `12` |

Bare “comma”, “billing period”, “Punkt”, “a new line of products”, and ordinary
number words stay literal. Compound numbers, currency compaction and ambiguous
shorthand are deliberately unsupported. Quote command mentions or introduce them
with “the phrase”, “the word”, “der Befehl”, “das Wort” or “wörtlich” to keep them
literal. Preferred dictionary spellings are protected even when they are commands.

For each final transcript the order is dictionary → spoken formatting → optional
local AI cleanup. Preview text is unchanged. Options and dictionary entries are
captured at recording start; both note and external dictation use this path. The
controller invokes it once per final raw transcript. Dictionary rules do not
cascade in that pass; do not feed processed output back into the dictionary
(conflicting pairs such as A → B and B → C intentionally remain one-step rules).
Formatting commands themselves are idempotent. Cleanup checks compare against
formatted text and preserve preferred dictionary spellings on accepted output;
failure keeps the deterministic result. No formatting model download is needed.

Regression coverage includes saved preferences, Unicode/compounds, command and
literal cases, language isolation, protected paths/addresses, repeat formatting,
dictionary target protection and cleanup disabled. Native settings tests cover
language selection and the punctuation switch in English and German.
