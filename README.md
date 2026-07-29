# Padikam - Content Repository

Padikam is a completely free offline app with all the features you need to prepare for KEAM. This repository serves as the cloud backend for the app, hosting all the Past Year Question papers (PYQs) and other public assets. The app dynamically syncs these files so students can get the latest papers without needing an app update.

---

## 🤝 Contribution

We welcome contributions from the community! If you have recent or missing question papers, you can add them to this repository. You can generate the JSON file manually, or use an AI tool (like ChatGPT, Gemini, or Claude) to convert raw text into our JSON structure. **The final result must be accurate and strictly follow the format below.**

### How to Contribute

**Best Practice:** It is highly recommended that you add the new paper **AND** update the `index.json` file in the same Pull Request. This ensures your contribution is complete and ready to be delivered to students immediately upon merging. As a repository maintainer, this saves a lot of time!

1. **Fork the repository** to your GitHub account.
2. **Create the folder structure** for the new paper. Papers are organized by year and date:
   `pyq/{Year}/{MonthDay}/paper.json`
   *(Example: `pyq/2026/April17/paper.json`)*
3. **Create the `paper.json`** file.
4. **Update `index.json`** in the root directory to include your new paper.
5. **Submit a Pull Request (PR)** to this repository.

### File Formats

#### 1. `paper.json` (The Question Paper)
This file goes inside the specific folder for the date (e.g., `pyq/2026/April17/paper.json`). Ensure that `correct_option` is **0-indexed** (i.e., Option A = 0, Option B = 1, Option C = 2, Option D = 3, etc.).

```json
{
  "id": "paper_2026_april_17",
  "title": "2026 April 17",
  "version": 1,
  "questions": [
    {
      "id": 1,
      "subject": "Mathematics",
      "text": "Let A and B be two subsets of a universal set U. If n(U) = 116, n(A ∪ B) = 99, n(B) = 61 and n(A ∩ B) = 28, then n(A') is equal to",
      "has_image": false,
      "image_path": "",
      "options": [
        "47",
        "45",
        "53",
        "48",
        "50"
      ],
      "correct_option": 4
    },
    {
      "id": 2,
      "subject": "Mathematics",
      "text": "Let f(x) = sin⁻¹x and g(x) = x - 2. To define the composite function f ∘ g, the largest domain of g(x) has to be",
      "has_image": false,
      "image_path": "",
      "options": [
        "[2,5]",
        "[1,3]",
        "[0,2]",
        "[-1,3]",
        "[-3,3]"
      ],
      "correct_option": 1
    },
    {
      "id": 3,
      "subject": "Mathematics",
      "text": "Let f(x) = 10/(7 + 4sin x + 3cos x), x ∈ R. Then the range of the function f is",
      "has_image": false,
      "image_path": "",
      "options": [
        "[1,5]",
        "[5,10]",
        "[1,10]",
        "[1,2]",
        "[5,10]"
      ],
      "correct_option": 0
    }
  ]
}
```

#### 2. `index.json` (The Paper Directory)
After creating your `paper.json`, add an entry to the `papers` array inside `index.json` located at the root of the repository.

```json
{
  "min_required_version": 1,
  "banner_message": "",
  "papers": [
    {
      "id": "paper_2026_april_17",
      "title": "2026 April 17",
      "year": 2026,
      "version": 1,
      "url": "pyq/2026/April17/paper.json"
    },
    {
      "id": "paper_2026_april_18",
      "title": "2026 April 18",
      "year": 2026,
      "version": 1,
      "url": "pyq/2026/April18/paper.json"
    }
  ]
}
```

### Tips for AI Generation
If you use an AI to generate the JSON from a PDF or image:
- **Prompt:** "Convert these questions into a JSON array matching this format: `{ "id": 1, "subject": "Mathematics", "text": "...", "has_image": false, "image_path": "", "options": ["A", "B", "C", "D"], "correct_option": 0 }`. The correct_option must be the 0-based index of the right answer."
- Always **verify** that the equations and symbols (like `sin⁻¹x` or `∪`) were correctly parsed by the AI before submitting your pull request.
- Ensure the `id` of each question is sequential and unique within the paper.

Thank you for contributing and helping students prepare better!