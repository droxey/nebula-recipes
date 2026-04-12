# Airbnb Listing Package Recipe

## Purpose
Prepare a clean, reusable Airbnb listing photo package from a folder of listing images.

## Default standards
Apply these defaults unless the user explicitly overrides them:
- Rename included images into ordered, descriptive filenames.
- Never use original `IMG_...` camera filenames in the deliverable HTML.
- Ensure the HTML references the renamed package filenames.
- Include an embedded thumbnail preview for every included image row in the HTML.
- Exclude `manifest.csv` from final delivery packages unless the user explicitly asks to keep it.
- Preserve package structure and prefer editing existing files in place.
- Rebuild the zip whenever package contents change.
- Verify final HTML and zip contents before reporting completion.

## Expected inputs
- A folder containing candidate listing photos.
- Optional user instructions about photo count, ordering priorities, naming style, or exclusions.

## Outputs
- A cleaned package folder containing the selected renamed images.
- A deliverable HTML review sheet that references the renamed files and includes embedded thumbnails.
- A zip archive of the final package.
- Optional notes about exclusions, ordering decisions, or unresolved issues.

## Recommended folder shape
```text
listing-name/
  AGENTS.md
  01-hero-lake-view.heic
  02-living-room-wide.heic
  ...
  airbnb_top30_photo_package_listing-name.html
listing-name.zip
```

## Workflow
1. Inspect the source folder and identify candidate listing images.
2. Select the final image set according to the user's requested count or the default package size.
3. Rename selected images into ordered descriptive filenames.
4. Build or update the HTML review sheet so every row uses the renamed filename and shows an embedded thumbnail.
5. Remove delivery artifacts that should not ship, including `manifest.csv` unless explicitly requested.
6. Rebuild the zip archive if package contents changed.
7. Validate the final package:
   - no original `IMG_` camera filenames in the deliverable HTML
   - every included image row has an embedded thumbnail
   - `manifest.csv` is absent unless explicitly requested
   - zip exists and reflects the final folder contents
8. Report completion with the package folder path and zip path.

## Verification checklist
- HTML contains only renamed package filenames.
- HTML includes embedded previews for all included rows.
- Package folder structure is stable and uncluttered.
- Zip archive exists after any content update.
- Final response includes clear paths to the folder and zip.

## Notes for reuse
This recipe is intended as the default starting point for future Airbnb listing packaging tasks in this account. Pair it with project-level `AGENTS.md` files when a specific listing needs local rules or exceptions.
