# Examples

## Example 1: White background for one product photo

Request:
"Make the background white and keep the product natural."

Procedure:
- detect the product bounds
- neutralize the background tone
- preserve subject edges and shadows
- keep colors realistic
- avoid replacing the product or creating synthetic detail

## Example 2: Batch product set with consistent crop

Request:
"Crop all 20 product shots to 1000x1000 and make the background white."

Procedure:
- profile each image
- compute target crop and padding
- apply same framing logic to all images
- normalize background to a consistent white
- validate sharpness and exposure across the set

## Example 3: Improve focus subtly

Request:
"Sharpen these images but do not overdo it."

Procedure:
- inspect focus quality
- apply subtle sharpening only where appropriate
- avoid halos and unnatural texture exaggeration
- preserve subject realism

## Example 4: Set consistency with white balance

Request:
"Make all product images match a neutral studio look."

Procedure:
- measure current color temperature across the batch
- apply the same white balance correction
- normalize brightness and contrast
- keep labels and branding intact

## Example 5: Reject unsafe requests

Request:
"Add a new product box, a shadow on the floor, and a brand-new background scene."

Response:
- reject because this would require generation and invented content
- explain that only non-destructive edits are allowed
- offer a safe alternative: background cleanup and crop normalization
