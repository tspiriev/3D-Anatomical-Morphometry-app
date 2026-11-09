# 3D Anatomical Morphometry

*3D model measurement, anatomical analysis, and neurosurgical corridor evaluation*

> **Research use only.** This app is intended for research purposes only and is not for clinical use. Do not use it for patient diagnosis, treatment, surgical planning, or other clinical decisions.

Use 3D Anatomical Morphometry to measure distances, perimeters, and areas on a calibrated photogrammetry 3D model. To compare neurosurgical corridors, mark the proximal exposure and distal target boundaries. The app uses those points to estimate each corridor’s dimensions, volume, and angles of attack.

## Install on macOS

1. Unzip `3D Anatomical Morphometry.zip`.
2. Drag **3D Anatomical Morphometry.app** into **Applications**.
3. Open **3D Anatomical Morphometry** from Applications. Earlier builds appear under the former name, **Surgical 3D Corridor Viewer**.

The app targets macOS 12 or later and supports Apple silicon and Intel Macs. The current build is ad hoc signed and has not been notarized. If macOS blocks the first launch, follow [Apple’s instructions for opening an unnotarized app](https://support.apple.com/en-us/102445).

In the Mac menu bar, open **Help → User Guide** to read this guide in the app, or **Help → Authors, Citation, and License** for credits and citation instructions. **Help → 3D Atlas of Neurological Surgery Website** opens the [project website](https://3datlasofneurologicalsurgery.org/index.php).

Use **Help → Research References** to jump to the bibliography in the app.

## Measure a corridor

1. **Open a model.** Drop an STL, OBJ, GLB, or GLTF file into **3D Model**, or click the drop area to choose a file. Use a self-contained GLB or GLTF. The app blocks external model resources, including remote textures.
2. **Orient the model.** Use **Orbit / View** to inspect the scan and the X, Y, and Z controls under **Orientation** to rotate the model itself. Set the orientation before placing points, since existing annotations stay at their original positions when the model rotates.
3. **Calibrate the scale.** Choose a unit under **Scale Calibration**. Select **Set Point A**, then click both ends of a known distance on the model. Enter that distance in **Reference length** and click **Apply Calibration**. For example, use `40` with **mm** selected if the reference is 40 mm long. Calibrate before interpreting lengths, areas, or volumes as physical measurements.
4. **Mark the exposure and target.** Select **Annotate Area of Exposure**, click at least three points around the proximal working window, and choose **Finish Area of Exposure**. Repeat for **Target Area**. Use **undo** to remove the last point or **clear** to start that boundary again.
5. **Review the results.** The **Measurements** panel shows the corridor metrics. Open **Diagram** to inspect the geometry from different views.

## Read the results

| Metric | What it represents |
| --- | --- |
| Calibration | The conversion from model units to physical units, set with two points a known distance apart. |
| Area of Exposure | Area of the proximal working window, using the terminology of Schwartz, Delashaw, and colleagues (1999). The app projects the picked boundary points onto a best-fit plane and measures their convex hull. |
| Target area (distal exposure) | Area of the annotated region exposed at the deep end, calculated using the same projected-hull method. |
| Target distance | Distance between the centers of the entry and target regions. |
| VOM corridor | The displayed tapered geometry between the fitted entry and target regions. VOM (Volume of Operative Maneuverability) estimates its volume from the two areas and an effective corridor height. |
| VSF corridor |VSF (Volume of surgical freedom) estimates how much room an instrument has to pivot while its tip stays on one specific target point. Its boundary comes from the instrument’s measured extremes of movement.|
| Horizontal angle of attack | The side-to-side angular span in degrees. From the target center, take the difference between the farthest left and right directions to the Area of Exposure in the corridor’s horizontal plane. |
| Vertical angle of attack | The up-and-down angular span in degrees. From the target center, take the difference between the highest and lowest directions to the Area of Exposure in the corridor’s vertical plane. |
| AoA (major / minor) | The original estimates from the long and short axes of the fitted entry ellipse. These are separate from the horizontal and vertical values. |
| Measure tool | Point-to-point distance, open path length, or closed polygon perimeter and projected area, depending on the selected tool. |

The **Horizontal AoA** and **Vertical AoA** readouts are beneath the color legend. Open **Measurement definitions** directly below them for explanations. Orient the model before annotating. The direction from the target center to the center of the Area of Exposure defines the corridor axis. Viewer **+Y** sets the up reference, with **+Z** used when the corridor is nearly parallel to **Y**. Orbiting the camera does not change the reported angles. A dash means there are too few annotations, the centers coincide, or a picked exposure point is at or behind the target plane perpendicular to the corridor axis.


These values are estimates derived from the selected points and fitted geometry. The model, calibration reference, and point placement all affect the results. The **Units** selector changes how values are displayed.

## Make quick measurements

Use **Measure**, just below **Orbit / View** and above the exposure and target tools, for measurements outside the corridor workflow.

- **Line** measures the straight-line distance between two points.
- **Open** adds the lengths of successive segments. Click **Finish** after placing the last point.
- **Closed** reports the area and perimeter of a closed polygon. Place at least three points and click **Finish**.

Open **Measure Style** in the upper-left viewer toolbar to adjust dot size, line width, and the color of both. Dots and lines stay the same on-screen size as you zoom. **Reset** restores the defaults. Click normally to place a point where you clicked, or hold **Shift** while clicking to snap to a nearby existing point.

After a result is complete, enter an optional name and select **Save measurement**. This records the result and clears the active points for the next measurement. Saved results remain in the list for the current app session, even if you load another model. Use **×** to remove a row, then select **Export measurements CSV** to export all remaining rows in one file. The CSV identifies the model, measurement type, point count, and units. Calibrated values are exported in mm and mm². Uncalibrated values are labeled as model units. Export before quitting.

## Adjust the lighting

The **Light** slider appears beside **Model** when the model is visible. Drag it left to dim the model or right to brighten it. The range is **25–400%**, and **Reset** returns it to **150%**. The control also adjusts scans with baked-in lighting. It changes only the model’s appearance and leaves calibration, annotations, and measurements intact.

## Compare and export

- Select **Save Current & Start New Approach** to name the current corridor and clear its active annotations for the next one. Saved approaches can be compared in the same session.
- Use **Export CSV** to save the corridor measurement table, including horizontal and vertical AoA.
- In **Diagram**, use the PNG export button to save an image or the GLB export in the 3D corridor view to save the visible corridor geometry by approach.

Models are processed locally. Saved approaches are kept in the current session, so export your results before quitting the app.

## Data and privacy

The Mac app has no account, upload service, or app telemetry. Model processing and measurement take place on the Mac. Website and DOI links open in your browser only when you choose them. Measurement CSVs can contain the model’s filename and labels you entered. Check those fields and remove identifying information before sharing results or models.

<a id="research-references"></a>

## Research References

These papers were used the development of 3D Anatomical Morphometry.

### Corridor measurement and 3D modeling

- Houlihan LM, Naughton D, Preul MC. Volume of surgical freedom: the most applicable anatomical measurement for surgical assessment and 3-dimensional modeling. *Front Bioeng Biotechnol.* 2021;9:628797. [DOI](https://doi.org/10.3389/fbioe.2021.628797)
- Piazza A, Bauman MMJ, Bellomo J, et al. A novel and cost-effective technique for quantitative measurement of endoscopic photogrammetric model. *Oper Neurosurg.* 2026;30:454–462. [DOI](https://doi.org/10.1227/ons.0000000000001678)
- Piazza A, Bellomo J, Corvino S, et al. Quantitative neuroanatomical measurement on photogrammetric model: validation study. *World Neurosurg.* 2025;194:123574. [DOI](https://doi.org/10.1016/j.wneu.2024.123574)
- Sinosi FA, Rodriguez Rubio R. An open source tool to conduct 3-dimensional morphometric analysis of microneurosurgical corridors: technical note and anatomical validation study using surface scanning techniques. *World Neurosurg.* 2025;202:124378. [DOI](https://doi.org/10.1016/j.wneu.2025.124378)
- Tariciotti L, Rodas A, Patel B, et al. Volume of operative maneuverability as a new measurement in neuroanatomical research: a methodological quantitative study and translational use in the operating room. *World Neurosurg.* 2025;196:123761. [DOI](https://doi.org/10.1016/j.wneu.2025.123761)

### Quantitative studies of surgical approaches

- Agazzi S, Youssef AS, van Loveren HR. The anterolateral approach for the transcranial resection of pituitary adenomas: technical note. *Skull Base.* 2010;20:143–148. [DOI](https://doi.org/10.1055/s-0029-1246227)
- Andaluz N, van Loveren HR, et al. Anatomic and clinical study of the orbitopterional approach to anterior communicating artery aneurysms. *Neurosurgery.* 2003;52:1140–1149. [DOI](https://doi.org/10.1227/01.NEU.0000057834.83222.9F)
- Cavalcanti DD, García-González U, et al. Quantitative anatomic study of the transciliary supraorbital approach: benefits of additional orbital osteotomy? *Neurosurgery.* 2010;66:ons205–ons210. [DOI](https://doi.org/10.1227/01.NEU.0000369948.37233.70)
- Cheng CM, Noguchi A, Dogan A, et al. Quantitative verification of the keyhole concept: a comparison of area of exposure in the parasellar region via supraorbital keyhole, frontotemporal pterional, and supraorbital approaches. *J Neurosurg.* 2013;118(2):264–269. [DOI](https://doi.org/10.3171/2012.9.JNS09186)
- Corrivetti F, de Notaris M, Porto E, Donofrio C, Corvino S, Spiriev T, Kong DS. Endoscopic transorbital approach to the infratemporal fossa: a quantitative anatomical comparison and clinical validation. *Manuscript, undated.*
- D’Ambrosio AL, Mocco J, et al. Quantification of the frontotemporal orbitozygomatic approach using a three-dimensional visualization and modeling application. *Neurosurgery.* 2008;62:ONS251–ONS261. [DOI](https://doi.org/10.1227/01.NEU.0000297018.65963.9B)
- Dayoub H, Schueler WB, et al. The relationship between the zygomatic arch and the floor of the middle cranial fossa: a radiographic study. *Neurosurgery.* 2010;66:ons363–ons369. [DOI](https://doi.org/10.1227/01.NEU.0000369656.20730.29)
- Figueiredo EG, Deshmukh V, et al. An anatomical evaluation of the mini-supraorbital approach and comparison with standard craniotomies. *Neurosurgery.* 2006;59:ONS212–ONS220. [DOI](https://doi.org/10.1227/01.NEU.0000223365.55701.F2)
- Gonzalez LF, Crawford NR, Horgan MA, Deshmukh P, Zabramski JM, Spetzler RF. Working area and angle of attack in three cranial base approaches: pterional, orbitozygomatic, and maxillary extension of the orbitozygomatic approach. *Neurosurgery.* 2002;50(3):550–557. [DOI](https://doi.org/10.1097/00006123-200203000-00023)
- Horgan MA, Anderson GJ, Kellogg JX, Schwartz MS, Spektor S, McMenomey SO, Delashaw JB. Classification and quantification of the petrosal approach to the petroclival region. *J Neurosurg.* 2000;93(1):108–112. [DOI](https://doi.org/10.3171/jns.2000.93.1.0108)
- Schwartz MS, Anderson GJ, Horgan MA, Kellogg JX, McMenomey SO, Delashaw JB Jr. Quantification of increased exposure resulting from orbital rim and orbitozygomatic osteotomy via the frontotemporal transsylvian approach. *J Neurosurg.* 1999;91(6):1020–1026. [DOI](https://doi.org/10.3171/jns.1999.91.6.1020)
- Spektor S, Anderson GJ, McMenomey SO, Horgan MA, Kellogg JX, Delashaw JB Jr. Quantitative description of the far-lateral transcondylar transtubercular approach to the foramen magnum and clivus. *J Neurosurg.* 2000;92(5):824–831. [DOI](https://doi.org/10.3171/jns.2000.92.5.0824)
