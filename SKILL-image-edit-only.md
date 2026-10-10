---
name: image-edit-only
description: Non-destructive image editing for product photos and image sets. Apply safe edits only: background cleanup to white, consistent cropping, focus/sharpness improvement, and uniform styling across a set. Never regenerate or invent content.
---

# Image Edit Only

## Mission

Edit the provided image(s) without generating new visual content. Make them cleaner, more consistent, and presentation-ready while preserving the original subject, composition, and intent.

Use only non-destructive edits that modify the existing pixels:
- crop and pad to consistent framing
- remove or neutralize background color differences
- adjust white balance, exposure, contrast, and saturation
- improve sharpness/focus within the original image
- normalize brightness and color across a set
- resize or reposition consistently across images

Do not create, invent, or replace subjects, objects, people, text, patterns, or backgrounds beyond the requested edit.

## Core operating principles

1. Preserve the source image as much as possible.
2. Make only the edits explicitly requested.
3. Keep subject identity and proportions intact.
4. Maintain realistic lighting, shadows, texture, and perspective.
5. When a background is changed, make it clean, consistent, and believable.
6. When a batch is edited, keep all images visually aligned in a single style.
7. Do not regenerate or repaint content that is not already in the source image.

## Allowed edit operations

Use only these operations when appropriate:
- crop to a consistent frame
- resize or pad to match target dimensions
- white background replacement for solid or near-solid backgrounds
- background cleanup that removes only distractive noise or uneven color
- exposure correction
- contrast and brightness balancing
- color temperature / white balance correction
- saturation normalization
- sharpening and deblurring within reasonable limits
- denoise when needed
- consistency edits across a set of images

## Strict forbidden operations

Never do any of the following:
- do not generate new objects
- do not add people, animals, props, or scenery
- do not replace the subject with a different one
- do not invent new text, logos, labels, packaging, or signs
- do not extend the canvas with invented background content
- do not use generative inpainting to "fill" areas
- do not create new shadows, reflections, or surfaces that were not in the source
- do not change identity, face, product shape, branding, or layout unless specifically requested
- do not over-sharpen into halos or artifacts
- do not change the image style beyond the requested edits
- do not make a set inconsistent by applying different treatments to different files unless the user asked for variance

## Background normalization rules

When the task is to make the background white or uniform:
- maintain the subject's true shape and edge detail
- remove only the surrounding color difference
- keep realistic separation between subject and background
- preserve natural lighting and cast shadows where present
- avoid hard-edged cutouts that look pasted on
- do not alter the product or subject beyond cleanup of the background

If the original background is highly complex, do not "hallucinate" a clean background. Instead:
- clean what is possible
- keep the result realistic
- avoid converting a natural scene into a fake studio shot unless explicitly requested

## Crop and uniformity rules

When cropping a set of images:
- use a consistent crop ratio and alignment
- keep the primary subject in a similar position across all files
- preserve important product detail and visual hierarchy
- do not crop so aggressively that the subject is cut off
- maintain consistent padding and margins across the set

Use a single visual standard for the batch:
- same crop ratio
- same framing logic
- same edge padding
- same subject placement
- same output resolution if requested

## Sharpness and focus rules

When improving focus:
- enhance clarity without creating artificial halos
- preserve natural textures
- avoid over-sharpening on faces, fabric, edges, or packaging
- do not fabricate detail that is not present in the source
- keep the edit subtle and realistic

## Batch consistency rules

For multiple images:
- match exposure, white balance, and contrast across the set
- normalize color and brightness with same target values
- keep crop style consistent
- maintain similar background treatment
- keep finished outputs cohesive without making any one image look "generated"

## Decision flow

Before editing, determine:
1. What is the subject?
2. What exactly is being requested?
3. Which parts are allowed to change?
4. What should remain untouched?
5. What are the target dimensions and visual consistency requirements?
6. Is the request safe and non-generative?

If any requested operation would require generation or invention of missing content, do not proceed.

## Required output format

Return only the edited image(s) or the final processed files. If a summary is required, keep it brief and factual:
- what was corrected
- what was preserved
- any assumptions made
- whether the edit was non-destructive and within the original image

## Final hard constraint

This workflow is strictly "edit existing pixels only."

Never:
- generate a new scene
- invent content
- replace a subject
- fake missing details
- create a background from nothing
- make the image look synthetic or AI-generated

The result must look like a clean, consistent, well-processed version of the original, not a different image created from scratch.
