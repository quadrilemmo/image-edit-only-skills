# API Reference

## Skill: image-edit-only

### Purpose
General-purpose edit-only skill for one or more images.

### Allowed operations
- crop
- pad
- resize
- white background neutralization
- color correction
- exposure adjustment
- contrast adjustment
- sharpness enhancement
- batch consistency normalization

### Forbidden operations
- generating new content
- inventing subjects or objects
- replacing text or labels
- changing identity or branding
- fake background creation
- inpainting with new details

## Skill: product-photo-edit-only

### Purpose
Strict product-photo workflow for ecommerce and catalogs.

### Allowed operations
- product framing
- cleanup of distracting background noise
- white or neutral background adjustment
- focus and contrast improvement
- labeling and branding preservation

### Forbidden operations
- changing product identity
- adding props or scenes
- altering packaging beyond requested cleanup
- synthetic background generation

## Skill: batch-image-edit-only

### Purpose
Multi-image processing with batch standardization.

### Allowed operations
- analyze and profile a set
- standardize crop and padding
- normalize background color
- equalize exposure and white balance
- apply uniform sharpness adjustments
- generate a manifest and validation report

### Forbidden operations
- any form of generation or invented visual content
- per-image style drift without approval
- inconsistent treatment across the set without a justified exception
