---

Name: image-text-extraction-merge

Description: Extract Chinese text from one or more pictures, screenshots, posters, social media long pictures or chat records, and automatically identify duplicate content, combine the same paragraphs, repair broken sentences and sequences, and finally organise them into a continuous, complete and directly useable Chinese copy.

---

# Image Text Extraction & Merge

## 1. Purpose

It is used to process one or more pictures containing Chinese characters.

Core tasks:

1. Extract text accurately from pictures.

2. Retain the meaning and expression of the original text.

3. Automatically recognise duplicate content between different pictures.

4. De-weight the duplicate content.

5. Merge sentences or paragraphs truncated by different pictures.

6. Restore the reasonable reading order.

7. Delete obvious OCR errors, garbled codes and meaningless symbols.

8. Finally output a continuous, complete, directly copied and useable Chinese copy.

---

## 2. Supported Inputs

Support:

- Screenshot of mobile phone

- Screenshot of Little Red Book

- Screenshot of WeChat chat

- Screenshot of Weibo

- TikTok screenshot

- Screenshots of social media such as Instagram / Facebook

- Long picture

- Poster

- Propaganda picture

- PPT screenshot

- Screenshot of PDF page

- Multiple continuous pictures

- Multiple pictures with duplicate content

---

## 3. Core Workflow

### Step 1 — Inspect All Images

Check all the pictures first, don't just deal with the first one.

Identification:

- Number of pictures

- Is there a continuous relationship between pictures?

- Whether there are duplicates in the picture

- Is there a contextual relationship?

- Is there an obvious order of pictures?

If the picture file name contains the number, for example:

`1.png`

`2.png`

`3.png`

By default, it is processed in the order of numbering.

If there is no number, according to:

- Content continuity

- Sentence context

- The relationship between the title and the body

- Paragraph logic

Infer a reasonable order.

---

### Step 2 — OCR Extraction

Extract text from each picture.

Keep as much as possible:

- Original text

- Title

- Paragraph

- punctuation

- emoji

- Number

- English

- Proper noun

- Hash label

Don't take the initiative to rewrite the copy in the OCR stage.

For example, it appears in the picture:

> The application for the German Conservatory of Music is really not as simple as you think.

It should be kept as:

> The application for the German Conservatory of Music is really not as simple as you think.

Instead of rewriting it as:

> The application for the German Conservatory of Music is actually not simple.

---

### Step 3 — OCR Error Correction

Identify obvious OCR errors.

Key inspection:

- homophones

- Shape-close characters

- Typos

- punctuation error

- Extra spaces

- Characters are garbled

- Chinese and English confusion

- Digital identification error

- Proper noun error

For example:

`College of Music`

Revised as:

`Conservatory of Music`

For example:

"Deyu"

Revised as:

"Germany"

But if you can't determine the correct text, don't modify it without permission.

You can keep the original text and mark it:

`[Suspected OCR error: xxx]`

---

## 4. Duplicate Detection

This is the core function of this Skill.

Compare the text extracted from all pictures across pictures.

Identification:

### 4.1 Completely repeated

For example:

Picture 1:

> Applications for the German Conservatory of Music need to be prepared in advance.

Picture 2:

> Applications for the German Conservatory of Music need to be prepared in advance.

In the end, only keep it once:

> Applications for the German Conservatory of Music need to be prepared in advance.

---

### 4.2 Partial repetition

For example:

Picture 1:

> The application of the German Conservatory of Music needs to prepare materials in advance, including language scores.

Picture 2:

> Including language scores, tracks and resumes.

It should be combined into:

> To apply for the German Conservatory of Music, you need to prepare materials in advance, including language scores, tracks and resumes.

---

### 4.3 Overlapping paragraphs

For example:

Picture 1:

> When choosing a school, don't just look at the school ranking.

Picture 2:

> Don't just look at the school ranking, but also consider the professor, city and examination requirements.

Merged into:

> When choosing a school, don't just look at the ranking of the school, but also consider the professor, the city and the examination requirements.

---

### 4.4 Similar but not repeated

Don't delete it directly because the two sentences are similar.

For example:

> Applications for the German Conservatory of Music need to be prepared in advance.

And:

> Many people fail to apply for the German Conservatory of Music, not because of insufficient ability, but because the preparation time is too late.

The meaning of these two sentences is related, but it is not a repetition.

All should be reserved.

---

## 5. Merge Rules

Follow the following priorities when merging text:

### Priority 1 — Preserve Original Meaning

The core point of view of the original author shall not be changed.

### Priority 2 — Preserve Original Wording

Unless there is an obvious OCR error, try to keep the original expression.

### Priority 3 — Remove Repetition

Only delete the really duplicate content.

### Priority 4 — Restore Continuity

If a sentence is truncated by a different picture, it should be automatically connected.

### Priority 5 — Improve Formatting

Yes:

- Merge and break lines

- Repair the paragraph

- Add the necessary spaces

- Restore the title hierarchy

- Unify clearly wrong punctuation

But don't make a literary rewriting.

---

## 6. Ordering

If there is a sequential relationship between the content of multiple pictures, it should be restored to a reasonable order.

Prioritise use:

1. Picture number

2. The original order of the pictures

3. Text context

4. Paragraph logic

5. Title → Text → Summary Structure

If you can't determine the order, don't force it to guess.

Can output:

> [There is uncertainty in the order]

And give the most reasonable arrangement.

---

## 7. Preserve Important Elements

In principle, the following contents must be retained:

- Title

- Subheading

- Number

- Date

- Amount

- Name

- Place name

- The name of the school

- Professional name

- Proper noun

-URL

- @Username

- #Topic Tag

- emoji

- Special symbols

- The content of quotation marks

If there are obvious UI elements such as watermark, account name, number of likes, number of comments, etc. in the picture:

If they belong to the text, keep them.

If it obviously belongs to the platform UI:

For example:

`Like 1234`

`Favourite 567`

`Share`

Delete by default.

---

## 8. Social media content

If the content of the picture comes from Xiaohongshu, Weibo, Moments, Instagram and other social media:

Prioritise extraction:

- Title

- Text

- Segmented content

- emoji

-Hashtag

-CTA

- @ content in the author's text

Ignore by default:

- Number of likes

- Number of favourites

- Number of comments

- Release time

- Platform navigation bar

- Power

-Wi-Fi

- Time

- Mobile phone status bar

Unless the user explicitly requires all withdrawals.

---

## 9. Output Modes

Default output:

# The complete copy after the merger

Then provide the organised full text directly.

Do not output the original OCR text of each picture by default.

---

### Optional Debug Mode

If the user requests to view the extraction process, it can output:

## Picture 1

The original extracted text...

## Picture 2

The original extracted text...

## Repeated content

...

## Merge results

...

---

## 10. Formatting

The final copy should:

- coherent

- Easy to read

- Clear paragraphs

- Keep the original tone

- Delete duplicates

- Fix obvious OCR errors

Don't add too much:

- emoji

- Title

- Subheading

- Summarise

- Comment

- Analyse

Unless required by the user.

---

## 11. Important principle

### Extract first, edit second.

Text extraction must be completed first, and then:

- De-weight

- Merge

- Sort

- OCR correction

- Formatting

Do not rewrite the original text directly at the identification stage.

---

## 12. Do not hallucinate

If there is no text in the picture, do not rewrite it by yourself.

If the text is vague:

Don't force it according to common sense.

For example, it appears in the picture:

> The application of the German Conservatory of Music needs to be advanced...

If the subsequent text cannot be recognised, it shall not be written by itself:

> The application of the German Conservatory of Music needs to be prepared one year in advance.

Unless this sentence does exist in the picture.

---

## 13. Handling Ambiguous Text

For words that cannot be recognised:

Use:

`[Unable to recognise]`

Or:

`[Suspected: XXXX]`

Don't take guessing as certainty.

---

## 14. Deduplication Algorithm

Conceptual processing process:

```text

Images

↓

OCR

↓

Text segmentation

↓

Paragraph Detection

↓

Similarity detection

↓

Exact Duplicate Removal

↓

Partial Overlap Detection

↓

Sentence Merging

↓

Order Reconstruction

↓

OCR Error Correction

↓

Formatting

↓

Final Unified Copy
