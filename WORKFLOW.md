# Workflow Overview

## 1. Goal

Create clean, consistent, presentation-ready image edits without generating new visual content. The workflow is intentionally limited to non-destructive edits applied to existing pixel data.

## 2. Core workflow

1. Analyze the image or image set
2. Identify what is explicitly requested
3. Decide which edits are allowed
4. Apply only the requested changes
5. Verify consistency and preservation of the subject
6. Log edits and output a summary

## 3. Safe edit categories

- crop and pad to consistent framing
- adjust exposure and contrast
- correct white balance and color temperature
- normalize background color
- improve sharpness subtly
- standardize batch style

## 4. Unsafe actions to reject

- generation of new content
- inpainting missing subjects or props
- changing identity or branding
- fake shadows, reflections, or backgrounds
- over-sharpening into artifacts
- making the result look synthetic

## 5. Batch process rules

- standardize crop dimensions and framing
- align exposure and white balance
- normalize background treatment
- keep the same visual language across the set
- track every change in a manifest

## 6. Outcome

The final output should be a cleaner, more consistent, more presentation-ready version of the original image, not a new image created from scratch.
