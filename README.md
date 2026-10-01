# Banking_Exam_Interface
## For Sectional Test
```json
{
  "meta": {
    "examName": "SBI Clerk Prelims",
    "testName": "Reasoning Sectional 01",
    "testType": "sectional",
    "durationMinutes": 20,
    "marksPerQuestion": 1,
    "negativeMarking": 0.25,
    "allowReattempt": true
  },
  "sections": [
    {
      "name": "Reasoning Ability",
      "durationMinutes": 20,
      "cutoff": 24,
      "questions": [
        {
          "id": 1,
          "question": "Which number comes next? 2, 4, 8, 16, ?",
          "options": ["24", "30", "32", "36"],
          "correct": 3,
          "explanation": "Each number is doubled: 16 x 2 = 32."
        },
        {
          "id": 2,
          "question": "If A &gt; B and B &gt; C, then which is definitely true?",
          "options": ["C &gt; A", "A &gt; C", "A = C", "B &gt; A", "None of these"],
          "correct": 2,
          "explanation": "A &gt; B &gt; C, so A &gt; C."
        }
      ]
    }
  ]
}
```
## For the Full Test
```json
{
  "meta": {
    "examName": "IBPS PO Prelims",
    "testName": "Full Mock 01",
    "testType": "full",
    "durationMinutes": 60,
    "marksPerQuestion": 1,
    "negativeMarking": 0.25,
    "sectionTimed": true,
    "allowReattempt": true
  },
  "sections": [
    {
      "name": "English Language",
      "durationMinutes": 20,
      "cutoff": 27,
      "questions": [
        {
          "id": 1,
          "question": "Choose the correct word: He is ___ honest man.",
          "options": ["a", "an", "the", "no article"],
          "correct": 2,
          "explanation": "'Honest' starts with a vowel sound, so 'an' is used."
        }
      ]
    },
    {
      "name": "Quantitative Aptitude",
      "durationMinutes": 20,
      "cutoff": 30,
      "questions": [
        {
          "id": 1,
          "question": "What is 15% of 200?",
          "options": ["20", "25", "30", "35"],
          "correct": 3,
          "explanation": "200 x 15/100 = 30."
        }
      ]
    },
    {
      "name": "Reasoning Ability",
      "durationMinutes": 20,
      "cutoff": 33,
      "questions": [
        {
          "id": 1,
          "question": "<b>Directions:</b> see the information above and answer.<br>Who sits to the left of A?",
          "options": ["B", "C", "D", "E"],
          "correct": 1,
          "passage": "Four persons A, B, C and D sit in a row facing north. B sits at the extreme left. A sits second from the right.",
          "groupId": "row1"
        },
        {
          "id": 2,
          "question": "Who sits at the extreme right?",
          "options": ["A", "B", "C", "D"],
          "correct": 4,
          "passage": "Four persons A, B, C and D sit in a row facing north. B sits at the extreme left. A sits second from the right.",
          "groupId": "row1"
        }
      ]
    }
  ]
}
```
## Field reference

| Field | Required | Notes |
| :--- | :--- | :--- |
| `meta.testType` | yes | `"sectional"` or `"full"` |
| `meta.durationMinutes` | no | Defaults to 20 for sectional and 60 for full |
| `meta.negativeMarking` | no | Defaults to 0.25 |
| `meta.sectionTimed` | no | Full tests only: locks each section when its time ends |
| `section.cutoff` | no | Defaults to Quant 30, Reasoning 33, English 27 |
| `question.id` | yes | Unique within the section, starting from 1 |
| `question.options` | yes | 4 or 5 strings |
| `question.correct` | yes | 1-based option number (1 = first option) |
| `explanation` | no | Shown in Analyse mode |
| `passage` and `groupId` | no | Questions with the same groupId share one passage, shown on the left. The passage text must be repeated on each question in the group |
| `marks` and `negative` | no | Override the marking for a single question |

## Rules that avoid errors

- Write `<` and `>` as `&lt;` and `&gt;` inside text. Write `&` as `&amp;`. Raw `<` can be treated as an HTML tag.
- Allowed tags are `<b>`, `<i>`, `<u>`, `<sub>`, `<sup>`, `<br>` and tables.
- JSON has no trailing commas and uses straight double quotes only. Curly quotes (“ ”) are fine inside the text, but not around keys or values.
- If you paste into the textarea and get an error, copy it to jsonlint.com first. It points to the exact line.

## Fast testing tricks

- **Timer and auto-submit:** set `durationMinutes` to 1 on a section and let it run out.
- **Section lock:** use the full test above with `sectionTimed: true` and click Save & Next on each section's last question.
- **Scoring:** answer exactly 1 right and 1 wrong in the sectional sample. The score should be 1 − 0.25 = 0.75.
