# NKPI 9.1.4 — continuous cornea and verified C audit

Release identifier: **9.1.4-continuous-c-audit**

This is the complete calculator plus the continuous bilateral viewer. The clinical
score model has NOT been retrained or changed. The viewer is a research visualization,
not a validated anatomical replica, progression rule, or surgical-planning tool.

## Upload the five files

Extract **NKPI_v914_GitHub_Upload.zip** once. Upload these at the repository root:

- `kcn_dual_calculator_app.py`
- `nkpi_runtime.zip` — **leave this inner ZIP zipped**
- `requirements.txt`
- `README.md`
- `.streamlit/config.toml` — keep it in the `.streamlit` folder

The four root files must be together, not inside an extra enclosing folder. Replace
the matching files. Select `kcn_dual_calculator_app.py` as Streamlit's main file and
Python **3.12** as the deployment runtime. Reboot, refresh the browser and confirm
**9.1.4-continuous-c-audit** in the calculator footer. Re-import the original report
ZIPs, check the measurements for each eye and visit, and calculate again.

The launcher verifies the matching runtime archive and installs its complete folder
structure automatically. Upload launcher and archive together; an older launcher
will correctly reject this archive. Do not unpack the inner ZIP into GitHub.

## Why the 3D minimum can differ from C

**Verified C** means the thinnest pachymetry value the user confirmed in the calculator
for the selected eye and visit. It is a scalar in micrometres, not an ABCD stage.
Verification is user input confirmation; it is not a new automated validation of the
Pentacam report. Check that the source examination, eye, visit and units are correct.

**Reconstructed minimum** is the lowest accepted thickness in the existing spatial
reconstruction. Its report-image values are decoded from color bins, spatially sampled,
and locally fitted. Obscured regions and discretization can change both the minimum
and its apparent location. The result can be higher OR lower than C. It is not a second
clinical measurement, and a mismatch is not proof of progression or a reason to edit C.

The old large reconstructed-minimum annotation could be mistaken for report C. The
new viewer displays C prominently, shows the original grid minimum separately, and
reports their difference. It does not rescale or warp the surface to make them agree.

Where verified thinnest-point XY coordinates are supplied in the correct scan frame,
the default marker uses them. Without coordinates, the marker uses the original grid
minimum and says that C's exact location is unavailable. A scalar C cannot establish
an XY location. Unscoped baseline landmarks are not reused on paired visits.

## Continuous display without new measurements

Whole surface, Map review and Slice through point share one OD/OS workspace. The
natural-eye appearance and linked cameras are retained. The section is now an intact
eye with a slice line and a profile underneath, rather than a wedge removed from tissue.

Display-only completion keeps a continuous corneal envelope and continuous color field
where that map has source data. The original arrays, measured points, C and NKPI are
unchanged. The support overlay distinguishes supported from completed/uncertain areas.
Small supported map estimates are labeled. Broad visual completion has **no numerical
reading**. An entirely unavailable map remains unavailable, not fabricated.

All five selected-point fields stay available together: thickness, anterior curvature,
posterior curvature magnitude, anterior elevation and posterior elevation. Report
C at supplied XY and reconstructed thickness at that XY remain separate. Map changes
do not move the point or deform the geometry. Original report opens only linked browser
source pages. Save both eyes includes visit, C, minima, support caveat and map scales.

## Accuracy and data limitations

The equal physical axes prevent deliberate cone exaggeration. They do not establish
an accurate 1:1 patient replica. Report-image geometry is approximate. The posterior
boundary is thickness-derived unless valid independent numerical posterior coordinates
were supplied. Iris, globe and unmeasured periphery are reference anatomy. Native
exports retain the existing validated import contract; this release is not a universal
Pentacam CSV/DICOM/proprietary file decoder.

Completion can conceal missing features if treated as anatomy. It is for viewing only.
Verify findings against the original report. A numerical device surface export and
same-scan comparison are required to assess anatomical reconstruction error.

## Retained application

Bilateral calculator, verified import review, input/impact audit, model files, scalar
inputs, regional methods and source processing are retained. The demo-eye selector and
Observed change & evidence panel remain absent. No patient reports or patient test
fixtures are included in this ZIP. Bundled OCR assets retain their existing licenses.

Python declarations remain `streamlit==1.50.0`, `reportlab==4.4.9`,
`numpy>=1.26.4,<3`. They are preserved for compatibility, not claimed as the newest
published library versions.

## Verification scope

The source regression suites, continuous-surface/C tests, browser interaction checks,
archive integrity and launcher extraction were checked. See `docs/V914_VERIFICATION.md`
inside the runtime for precise scope. A prepared example from the earlier supplied
report was used for browser checks, not a fresh end-to-end OCR run and not the patient
in the latest photographs. This environment could not install Streamlit, so this
release was NOT freshly launched inside a live Streamlit server or cloud deployment.
Software tests do not establish clinical accuracy. Check the first imported case against
its original report before using the display in a clinic workflow.

Technical details: `docs/CONTINUOUS_REVIEW.md`, `docs/SURFACE_DATA.md`,
`docs/NUMERICAL_IMPORT.md` inside `nkpi_runtime.zip`.

## Privacy

Use de-identified inputs on public hosting. Do not commit patient reports, screenshots,
exports, secrets, or local test cases to GitHub. Clinical hosting must follow your
institution's approved privacy and security requirements. See `PRIVACY.md`.
