---
title: "{{ replace .Name "-" " " | title }}"
slug: "{{ replace .Name " " "-"}}" # Auto-generated slug from filename
date: {{ .Date }} # Auto-filled with current date/time
draft: true # Start as draft, set to 'false' to publish

# --- Language & Topic ---
language_name: "" # e.g., "Gujarati", "English", "Sanskrit" - IMPORTANT: Fill this in!
language_code: "" # Optional: e.g., "gu", "en", "sa" (ISO 639-1 or 639-2 codes)
topic: "" # e.g., "Vowel Sounds", "Consonant Clusters", "Intonation Patterns", "Script Introduction"

# --- Categories (Broader Grouping) ---
# Choose 1-2 primary categories. Delete the rest for this post.
# You can define these categories as you see fit.
# categories:
  # - "Phonetics & Pronunciation"
  # - "Grammar Basics"
  # - "Vocabulary Building"
  # - "Script & Orthography"
  # - "Language History"

# --- Tags (Specific Keywords) ---
# Add specific keywords relevant to the post.
tags:
  # - "common mistakes"
  # - "Gujarati alphabet"
  # - "language"
  # - "phonetics"
  # - "pronunciation"
  # - "transliteration"


# --- Optional Fields ---
# proficiency_level: "Beginner" # e.g., Beginner, Intermediate, Advanced
# audio_sample: "/audio/language/filename.mp3" # Path to an audio sample, if relevant for the whole post
# related_lessons: # Links to other lessons or posts
#   - "/language/another-lesson/"

cover:
  image: "" # Place 'cover.jpg' (or your image name) in this post's folder (if a Page Bundle)
  alt: ""   # Alt text for the cover image
#   caption: "Optional caption for the image"
  relative: true # Keep true for Page Bundles, false if image is in /static/
---

<!--
Quick Reminders for Language Posts:
- Fill in 'language_name' and 'topic' in the front matter.
- Choose appropriate 'categories' and 'tags'.
- Add a cover image if desired.
- Use ## (H2) for main sections (e.g., Introduction, Key Sounds, IPA Breakdown, Examples).
- Use ### (H3) for sub-sections.
- Use the {{< abbr "term" "definition" >}} shortcode for glossary terms.
- Consider embedding audio samples for pronunciation.
- Set 'draft: false' when ready to publish.
-->

## Introduction

Briefly introduce the language aspect or pronunciation topic covered in this post.

## [Specific Section, e.g., Key Vowel Sounds]

Explain the concept here.

### [Sub-point, e.g., The ' અ ' (a) Sound]

- **IPA:** /ə/
- **Description:** ...
- **Examples:**
  - શબ્દ (shabd) - word
  - {{< abbr "નભ" "Sky" >}} (nabh) - sky

## Audio Examples (Optional)

<!-- You might use a shortcode for an audio player here -->
<!-- Example: {{< audio src="/audio/language/gujarati_a_sound.mp3" >}} -->

## Common Mistakes

...

## Further Reading / Practice

...
