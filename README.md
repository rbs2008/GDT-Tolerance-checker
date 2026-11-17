# Tolerance Desk

A local-first prototype for reviewing dimensioned mechanical designs. It calculates one-dimensional worst-case and RSS tolerance stacks, checks explicit pin/hole fits, and runs a small set of transparent GD&T syntax sanity checks against manually entered feature-control frames.

## Run it

Open `index.html` in a current desktop browser. No server, account, or uploaded-file service is required. Project data is kept in the browser until you export a project JSON file.

## Supported inputs

- **Project JSON:** import or export `tolerance-spellcheck/1` projects, including features, feature-control frames, and stack terms.
- **DXF:** reads basic ASCII DXF structure and reports title/entity counts. It does not interpret dimensions, blocks, geometric tolerances, or drawing intent.
- **STEP (`.step`/`.stp`):** reads text headers and reports schema and solid-body counts. It also lists component occurrences and parent/component links when the file uses recognized `NEXT_ASSEMBLY_USAGE_OCCURRENCE` or `ASSEMBLY_COMPONENT_USAGE` records. It does not analyze placements, geometry, PMI, assembly constraints, or mating fits.

CAD files are read locally in the browser. Binary DWG, native CAD documents, and image/PDF drawings are not supported. STEP assembly structure is a record-level inventory, not a geometric assembly validation.

## Calculation conventions

- Dimensions use the project-selected unit. Switching between millimeters and inches converts entered dimensions and tolerances using 25.4 mm per inch; CAD-file units are not inferred.
- Pin/hole clearance is hole size minus pin size. A negative worst-case minimum indicates possible interference.
- Stack terms are signed along one linear direction. Worst-case sums the limits at their adverse extremes. RSS combines positive and negative deviations separately as root-sum-square magnitudes. RSS is an estimate, not a guaranteed boundary; independence and distribution assumptions must be checked by the engineer.
- GD&T checks are limited heuristics on the entered frame data. They are not an ASME Y14.5 conformance determination. The applicable edition, full feature-control-frame semantics, datum reference frames, material-condition modifiers, geometric boundary conditions, drawing context, and model-based definition are not fully interpreted.

Use the results as an engineering review aid, not as a substitute for the applicable licensed standard, qualified engineering judgment, or manufacturing validation.
