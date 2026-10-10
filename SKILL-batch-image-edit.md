---
name: batch-image-edit-only
description: Advanced non-destructive batch image editing. Process multiple product images with consistency rules, metadata tracking, and uniform style application. Edit only; never generate.
requires: image-processing-tools, batch-manifest
---

# Batch Image Edit Only

## Mission

Process a collection of product images with consistent non-destructive edits. Apply the same visual standard across all files while respecting individual image characteristics. Generate a manifest tracking all changes for quality assurance and batch uniformity.

## Workflow overview

```
INPUT: Image set + editing instructions
  ↓
[Phase 1] Analyze & Plan
  → profile each image
  → detect background type
  → measure crop/size variance
  → create edit plan per image
  ↓
[Phase 2] Apply Uniform Rules
  → standardize crop dimensions
  → normalize white balance
  → align exposure / contrast
  → apply batch color grading
  ↓
[Phase 3] Track & Validate
  → log all edits per image
  → verify non-destructive compliance
  → create before/after metadata
  → output manifest
  ↓
OUTPUT: Edited images + batch report
```

## Phase 1: Analysis & Planning

Before editing any image, perform a full batch analysis:

### 1.1 Image profiling
For each image in the set, collect:
- filename and original dimensions
- dominant background color(s)
- subject bounding box (estimated)
- current white balance color temperature
- exposure histogram (bright/normal/dark)
- presence of text, labels, branding
- estimated crop ratio and framing
- focus quality (sharp/acceptable/soft)
- surface material (matte/glossy/fabric/metal/ceramic)

### 1.2 Set-level variance detection
Analyze the batch as a group:
- report dimension variance
- list unique background colors
- group images by lighting condition
- detect outlier images
- note any inconsistent product placement across the set

### 1.3 Edit plan generation
Create a structured plan with:

```yaml
batch_id: "product-set-2026-10-10"
total_images: N
target_dimensions: "1000x1000"
target_background: "white"
target_color_temp: "6500K"
target_exposure: "normal"

per_image_plan:
  - filename: "image_001.jpg"
    current_dims: "800x600"
    action_crop_to: "1000x1000"
    crop_gravity: "center"
    bg_color_detected: "#f5f5f5"
    bg_action: "normalize_to_white"
    exposure_adjustment: "+0.3 EV"
    contrast_target: "medium"
    sharpness_action: "subtle_sharpen"
    preserve_label: true
    preserve_shadow: true
    notes: "Centered product, remove left margin"
```

This plan is reviewed and approved before execution. Do not proceed without explicit confirmation of the plan.

## Phase 2: Uniform Edit Application

### 2.1 Crop & Pad Consistency

Apply the same crop ratio and gravity to all images.

For a set:
1. Agree on target dimensions
2. Choose a gravity/anchor point
3. For each image:
   - Detect the subject bounding box
   - Apply crop with consistent padding from subject
   - Pad or letterbox to target dimensions if needed
   - Ensure product is in same relative position across all files

### 2.2 Background Normalization

Make backgrounds consistent without inventing new content.

For each image:
1. Detect background color and texture
2. If background is solid or near-solid:
   - neutralize color variance
   - preserve subject edges with anti-aliasing
   - keep realistic shadow/grounding
3. If background is complex:
   - do not invent a studio background
   - gently neutralize existing colors
   - blur background slightly while keeping subject sharp
4. Apply consistently across all images

### 2.3 White Balance & Color Temperature Consistency

Apply the same color temperature across the batch.

- measure white balance in reference regions
- choose a target temperature
- shift all images toward the target temperature
- verify neutral surfaces look consistent

### 2.4 Exposure & Brightness Alignment

Align brightness and contrast across the batch.

- measure each image histogram
- compute consistent target brightness
- apply exposure correction uniformly
- adjust contrast consistently
- ensure no image is blown out or underexposed

### 2.5 Saturation & Color Grading

Apply the same color intensity and tone curve across the batch.

- choose a target saturation level
- apply the same color adjustments to all images
- preserve branding and label colors

### 2.6 Focus & Sharpness Uniformity

- measure focus quality per image
- apply subtle sharpening only where needed
- avoid halos, noise amplification, or fake detail
- keep background and product textures believable

### 2.7 Batch Denoising (Optional)

If images show noise or grain:
- detect noise level per image
- apply mild denoising uniformly
- preserve texture on product surfaces
- keep labels legible

## Phase 3: Tracking & Validation

### 3.1 Edit Log Creation

For every image, record:

```yaml
image: "product_001.jpg"
timestamp: "2026-10-10T14:30:00Z"
edits_applied:
  - crop:
      from: "800x600"
      to: "1000x1000"
      gravity: "center"
      padding: "50px"
  - background:
      action: "normalize_to_white"
      original_color: "#f5f5f5"
      result_color: "#ffffff"
      method: "color_replacement_with_edge_preservation"
  - white_balance:
      from_temp: "5800K"
      to_temp: "6500K"
      adjustment: "+700K"
  - exposure:
      from_ev: "-0.2"
      to_ev: "0.0"
      adjustment: "+0.2 EV"
  - contrast:
      adjustment: "+20%"
  - saturation:
      adjustment: "neutral (no change)"
  - sharpness:
      method: "unsharp_mask"
      radius: "1.2px"
      amount: "0.8"
  - denoise: "none"

edit_safety_checks:
  - no_generation: true
  - subject_preserved: true
  - branding_intact: true
  - labels_readable: true
  - dimensions_match_target: true
  - non_destructive: true

output_file: "product_001_edited.jpg"
quality_score: "9.2/10"
notes: "Centered subject, white background consistent with batch standard"
```

### 3.2 Compliance Validation

Before finalizing, verify every image:
- crop dimensions match target
- subject is recognizable and undistorted
- labels and branding are intact and readable
- background treatment is consistent with other images
- no generated or invented content
- no over-processing artifacts
- sharpness is realistic
- colors are consistent with batch
- metadata preserved

### 3.3 Batch Manifest Report

Generate and return a report with:
- total files processed
- images successful and flagged
- crop ratio used
- background color standard
- color temperature target
- exposure standard
- compliance checks
- quality summary

## Advanced options

### Outlier handling
If one image is significantly different:
1. Flag it for manual review
2. Apply the same edits with adjusted parameters if needed
3. Do not regenerate missing parts

### Reference image approach
Use one approved image as the visual standard for color and exposure across the set.

### Batch split for divergent sets
If a batch has different lighting or styles, split it into separate sub-batches and report them separately.

### Dry-run mode
Before finishing edits:
1. Generate the edit plan
2. Preview on a temporary copy
3. Show a comparison
4. Seek approval
5. Save the final result

## Forbidden operations (batch context)

Never:
- regenerate any image or part of an image
- invent background for multiple images
- use generative fill to complete a set
- apply wildly different treatments without consent
- create a pasted-on, obviously AI-edited look
- change product identity, dimensions, or branding across the batch
- over-process into visible halos, noise, or artifacts
- cut and paste between images

## Core promise

This workflow edits images only. It does not generate, invent, or replace any part of the original photos. The result is a cleaned-up, standardized version of your source images, ready for professional use.

All changes are logged, tracked, and reversible by policy.
