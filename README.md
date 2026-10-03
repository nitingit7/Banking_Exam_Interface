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
      "groups": [
        {
          "id": "p1",
          "passage": "<b>Directions (Q. 1-2):</b> Eight persons A to H sit around a circular table facing the centre. B sits second to the right of C."
        }
      ],
      "questions": [
        {
          "id": 1,
          "groupId": "p1",
          "question": "Who sits third to the left of B?",
          "options": ["A", "D", "E", "F", "G"],
          "correct": 2,
          "explanation": "Clockwise order: B, D, C, E, G, A, F, H. D is third to the left of B.<br><b>Full solution:</b> Reasoning_Day3.pdf, pages 13-14"
        },
        {
          "id": 2,
          "question": "Which number comes next? 2, 4, 8, 16, ?",
          "options": ["24", "30", "32", "36"],
          "correct": 3,
          "explanation": "Each term doubles: 16 x 2 = 32.<br><b>Full solution:</b> Reasoning_Day3.pdf, page 15"
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
        { "id": 1, "question": "He is ___ honest man.", "options": ["a", "an", "the", "no article"], "correct": 2,
          "explanation": "'Honest' starts with a vowel sound, so 'an'.<br><b>Full solution:</b> English_Mock01.pdf, page 4" }
      ]
    },
    {
      "name": "Quantitative Aptitude",
      "durationMinutes": 20,
      "cutoff": 30,
      "groups": [
        { "id": "di1", "passage": "<b>Directions (Q. 1-2):</b> Study the bar chart and answer the questions.", "image": "quant1-di1-bar.png" }
      ],
      "questions": [
        { "id": 1, "groupId": "di1", "question": "Total sales in 2022 and 2023?", "options": ["210", "230", "250", "270", "290"], "correct": 3,
          "explanation": "120 + 130 = 250.<br><b>Full solution:</b> Quant_Mock01.pdf, pages 22-23" }
      ]
    },
    {
      "name": "Reasoning Ability",
      "durationMinutes": 20,
      "cutoff": 33,
      "questions": [
        { "id": 1, "question": "Which is the odd one out?", "options": ["Cat", "Dog", "Car", "Cow"], "correct": 3,
          "explanation": "Car is not an animal.<br><b>Full solution:</b> Reasoning_Mock01.pdf, page 40" }
      ]
    }
  ]
}
```
## Field reference

| Field         | Notes                                                                                                                             |
|---------------|-----------------------------------------------------------------------------------------------------------------------------------|
| `explanation` | Optional. Short solution text and, if you want, your reference line. Shown only in Analyse and Re-attempt, never during the exam. |
| `groups`      | Optional. Directions, table or chart written once per set (`id`, `passage`, `image`). Questions only say `"groupId"`.             |
| `image`       | The file name of an image you attach with the "Add images" button.                                                               |
| `correct`     | 1-based option number.                                                                                                           |

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
